





## Create your EKS Cluster with eksctl



`eksctl` is a CLI for Amazon EKS that helps you easily create Amazon EKS cluster!

eksctl website:  https://eksctl.io/

You may follow the Amazon EKS official document - [Getting Started with eksctl](https://docs.aws.amazon.com/eks/latest/userguide/getting-started-eksctl.html) to complete the cluster creation with `eksctl` or just follow the steps below.



## Steps

1. Spin up your [Cloud9 IDE](https://us-west-2.console.aws.amazon.com/cloud9/home?region=us-west-2) from AWS console.

![0-c9-0](../images/00-c9-01.png)



2. Create and name your environment

![0-c9-0](../images/00-c9-02.png)

3. Leave everythong as default and click **Next Step**
4. Click **Create environment**

(It would typically take 30-60s to create your Cloud9 IDE)

![0-c9-0](../images/00-c9-03.png)

5. We need to turn off the Cloud9 temporarily provided IAM credentials. 

![0-c9-0](../images/00-c9-04.png)



6. When you turn off the temporary credentials, you should not be able to un AWS CLI now.

![0-c9-0](../images/00-c9-05.png)



7. execute `aws configure` to configure the credentials for your IAM user. Make sure this IAM User has **AdministratorAccess** and run `aws sts get-caller-identity` - you should be able to see the returned JSON output like this.

![0-c9-0](../images/00-c9-06.png)





8. Download the `kubectl` and save to `~/bin`. Check the Amazon EKS User Guide for [Installing kubectl](https://docs.aws.amazon.com/eks/latest/userguide/install-kubectl.html). 

   ```
   $ mkdir ~/bin
   
   $ wget https://amazon-eks.s3-us-west-2.amazonaws.com/1.12.7/2019-03-27/bin/linux/amd64/kubectl -O ~/bin/kubectl
   $ chmod +x $_
   ```

9. Download the `eksctl` from `eksctl.io`(actually it will download from GitHub)

   ```
   $ curl --silent --location "https://github.com/weaveworks/eksctl/releases/download/latest_release/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
   sudo mv /tmp/eksctl /usr/local/bin
   ```


10. run `eksctl help`, you should be able to see the `help` messages

![0-c9-0](../images/00-c9-07.png)


## create cluster with eksctl


11. Create your Amazon EKS cluster witn `eksctl` and spin up a nodegroup with `2 nodes`

```
$ eksctl create cluster --name=<CLUSTER_NAME> --nodes 2 --auto-kubeconfig --ssh-public-key <EXISTING_SSH_KEY_NAME>
```

![0-c9-0](../images/00-c9-08.png)

Or like this
```
eksctl create cluster \
  --name=eksdemo \
  --region=us-west-2 \
  --nodes=2 \
  --tags environment=develop \
  --node-type=m5.large \
  --ssh-access \
  --ssh-public-key=your_key_name \
  --node-private-networking \
  --vpc-private-subnets=subnet-ed2b93c3,subnet-e6c38eac \
  --vpc-public-subnets=subnet-36368e18,subnet-aec68be4
```

Alternatively, you may also create your cluster with cluster config file.

```
cat << EOF > cluster.yaml
apiVersion: eksctl.io/v1alpha4
kind: ClusterConfig

metadata:
  name: eksdemo
  region: us-west-2

nodeGroups:
  - name: ng0
    instanceType: m5.large
    desiredCapacity: 2
EOF
```

And then, just 
```
eksctl create cluster -f cluster.yaml
```
check more config samples from `eksctl` [github](https://github.com/weaveworks/eksctl/tree/master/examples)



## Generate kubeconfig with aws eks update-kubeconfig


And create/update your `$HOME/.kube/config` with `aws eks update-kubeconfig`

```
aws eks update-kubeconfig --name eksdemo
```

(Ensure your aws-cli version is at least **1.16.18**, or follow [this gist](https://gist.github.com/pahud/b748f726515d3b073b997d92b595b526) to upgrade your aws-cli in Cloud9 )

After executing `aws eks update-kubeconfig`, a new context will be generated in `$HOME/.kube/config` and you can execute `kubectl get no` to list all nodes in the nodegroup.



![0-c9-0](../images/00-c9-09.png)



Get the `cluster-info` or `get all` resources.

![0-c9-0](../images/00-c9-11.png)



Now your Amazon EKS cluster is ready!  You may proceed to [customize your nodegroup](../01-nodegroup/customize-nodegroup.md) now.

If you need to delete this clusrer, run `eksctl delete cluster —name=<CLUSTER_NAME>` to trigger the deletion of the stack.

