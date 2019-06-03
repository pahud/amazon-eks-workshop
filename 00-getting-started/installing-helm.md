## Installing Helm



You may follow [Using Helm with Amazon EKS](https://docs.aws.amazon.com/eks/latest/userguide/helm.html) from the Amazon EKS official document or just follow the steps below:



```bash
# install helm cli 
$ curl -L https://git.io/get_helm.sh | bash
# create 'tiller' namespace
$ kubectl create namespace tiller
# open a new terminal and run tiller client mode
$ export TILLER_NAMESPACE=tiller
$ tiller -listen=localhost:44134 -storage=secret -logtostderr
# open a new terminal
$ export HELM_HOST=:44134
$ helm init --client-only
$ helm repo update
```

That's all!



