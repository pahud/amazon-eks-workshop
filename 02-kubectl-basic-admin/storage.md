# Storage Concepts - PV, PVC and StatefulSet



Let's define `gp2`  as the default `StorageClass`

```
$ kubectl apply -f gp2-storage-class.yaml
```

#### get all `StorageClass`

```
$ kubectl get sc
NAME            PROVISIONER             AGE
gp2 (default)   kubernetes.io/aws-ebs   28m
```

### create nginx with PVC and Dynamic PV

```
$ kubectl apply -f nginx-with-pvc.yaml
persistentvolumeclaim "nginx-with-pvc" created
deployment.extensions "nginx-with-pvc" created
```

### watch the pod creation and running

```
$ kubectl get po -l app=nginx -w
NAME                             READY     STATUS              RESTARTS   AGE
nginx-with-pvc-95d96c4fd-ddsqw   0/1       ContainerCreating   0          12s
nginx-with-pvc-95d96c4fd-ddsqw   1/1       Running   0         20s
```

### get the PVC info

```
$ kubectl get pvc -l name=nginx-with-pvc
NAME             STATUS    VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS   AGE
nginx-with-pvc   Bound     pvc-c4c89320-9479-11e8-81a0-0aeef4411be2   6Gi        RWO            gp2            3m
```

### delete `nginx-with-pvc`

```
$ kubectl delete -f nginx-with-pvc.yaml
persistentvolumeclaim "nginx-with-pvc" deleted
deployment.extensions "nginx-with-pvc" deleted
```

### create nginx `StatefulSets`

```
$ kubectl apply -f nginx-with-ss.yaml
service "nginx" created
statefulset.apps "web" created
$ kubectl get po -w -l app=nginx
NAME      READY     STATUS              RESTARTS   AGE
web-0     1/1       Running             0          8s
web-1     0/1       ContainerCreating   0          3s
web-1     1/1       Running   0         10s
(Ctrl-c to escape)
$ kubectl get po  -l app=nginx
NAME      READY     STATUS    RESTARTS   AGE
web-0     1/1       Running   0          4m
web-1     1/1       Running   0          4m

# scale out to 6
$ kubectl scale statefulset/web --replicas 6
statefulset.apps "web" scaled

# watch the pod creation and running
$ kubectl get po  -w -l app=nginx
NAME      READY     STATUS              RESTARTS   AGE
web-0     1/1       Running             0          6m
web-1     1/1       Running             0          6m
web-2     0/1       ContainerCreating   0          13s
web-2     1/1       Running   0         18s
web-3     0/1       Pending   0         0s
web-3     0/1       Pending   0         0s
web-3     0/1       ContainerCreating   0         0s
web-3     1/1       Running   0         19s
web-4     0/1       Pending   0         0s
web-4     0/1       Pending   0         0s
web-4     0/1       ContainerCreating   0         0s
web-4     1/1       Running   0         9s
web-5     0/1       Pending   0         0s
web-5     0/1       Pending   0         0s
web-5     0/1       ContainerCreating   0         0s
web-5     1/1       Running   0         19s
web-6     0/1       Pending   0         1s
web-6     0/1       Pending   0         1s
web-6     0/1       Pending   0         4s
web-6     0/1       ContainerCreating   0         4s
web-6     1/1       Running   0         14s

$ kubectl get statefulset/web
NAME      DESIRED   CURRENT   AGE
web       6         6         8m

$ kubectl get po -l app=nginx
NAME      READY     STATUS    RESTARTS   AGE
web-0     1/1       Running   0          8m
web-1     1/1       Running   0          8m
web-2     1/1       Running   0          2m
web-3     1/1       Running   0          2m
web-4     1/1       Running   0          2m
web-5     1/1       Running   0          1m

```



### Delete all StatefulSet

```
$ kubectl delete -f nginx-with-ss.yaml
service "nginx" deleted
statefulset.apps "web" deleted
```



### Delete all PV and PVC

```
$ kubectl delete --all pv,pvc
```

