# amazon-eks-workshop
Amazon EKS workshop walkthrough repository. 

This is a collection of Amazon EKS popular topics and assets aimed to help you successfully build your Amazon EKS workload.



## Getting Started

[Create your EKS Cluster with eksctl](./00-getting-started/create-eks-with-eksctl.md) or check the [8min Youtube walkthrough video](https://www.youtube.com/watch?v=3-OZqA5p1HA) by Arun Gupta

[Customize your nodegroup(worker nodes)](./01-nodegroup/customize-nodegroup.md)

[Working with kubectl for basic administrations](./02-kubectl-basic-admin/kubectl-basic-admin.md)



## Creating Services

[ClusterIP, NodePort and LoadBalancer](https://github.com/pahud/amazon-eks-workshop/tree/master/03-creating-services)

[Ingress Options](./03-creating-services/ingress-options.md)



## Development with Amazon EKS

[Create your 1st app from scratch and deploy into Amazon EKS](https://github.com/pahud/greeting)

## Helm and Charts

[Installing Helm](./00-getting-started/installing-helm.md)



## Spot and Lambda Integration

[pahud/eks-lambda-drainer](https://github.com/pahud/eks-lambda-drainer) - Amazon EKS node drainer with AWS Lambda

[Blog - Interacting with EKS via Lambda
](http://www.nickaws.net/aws/2018/09/03/Interacting-with-EKS-via-Lambda.html) by [@nbrandaleone](https://github.com/nbrandaleone)



## Storage

[Storage(PV, PVC and StatefulSet)](./02-kubectl-basic-admin/storage.md)

[Amazon EKS with Amazon EFS](https://github.com/kubernetes-incubator/external-storage/tree/master/aws/efs)



## Monitoring

Kubernetes Dashboard

## Scheduling

Affinity and Anti-Affinity

Taint and Toleration

Cordon and Uncordon

Drain



## AutoScaling

[HPA(Horizontal Pod Autoscaling)](./04-scaling/hpa/README.md)

[CA(Cluster-Autoscaler](./04-scaling/cluster-autoscaler/README.md))

VPA(Vertical Pod Autoscaling)

Autoscaling Group LifeCycle Hooks with Pod draining





## Log Consolidation

Fluentd integration



## CI/CD

[Amazon EKS with AWS CodeBuild integration](https://github.com/pahud/eks-kubectl-docker#codebuild-support) 

[Amazon EKS Continuous Deployment Sample using AWS CodePipeline](https://github.com/chankh/eksutil/tree/master/lambda/codepipeline)

[Automate Kubernetes deployment on Amazon EKS with buddy.works](https://buddy.works/blog/amazon-eks-kubernetes)

[Blog - Continuous Delivery with Amazon EKS and Jenkins X](https://amzn.to/2JM2luY) 

## Service Discovery

[ExternalDNS and Route53 Auto Naming API](https://dev.classmethod.jp/cloud/aws/external-dns-eks/)

## Service Mesh

[Installing Istio 1.x on Amazon EKS](https://github.com/pahud/amazon-eks-workshop/tree/master/06-service-mesh/Istio)

Blog - Getting Started with Istio on Amazon EKS - https://amzn.to/2wo3inY

How to integrate AWS ALB with istio v1.0 by *Chuan-Yen Chiang* - https://medium.com/@cy.chiang/how-to-integrate-aws-alb-with-istio-v1-0-b17e07cae156


## CloudWatch Events Integration

[CloudWatch Events scheduled kubectl execution from within AWS Fargate](https://github.com/pahud/eks-kubectl-docker#aws-fargate-with-cloudwatch-event-scheduled-events)([Tweet](https://twitter.com/pahudnet/status/1047166317042618368))



## Amazon EKS and Amazon API Gateway Integration

https://twitter.com/pahudnet/status/1030628314044452865

https://twitter.com/pahudnet/status/1030629435664302085

## multi-tenant topology

Multiple EKS clusters sharing single VPC and ALB - ([tweet](https://twitter.com/pahudnet/status/1044988111694876672)|[architecture](https://pbs.twimg.com/media/DoCLDjfUwAA4s2_.jpg))



## Contributors

- [Pahud Hsieh](https://github.com/pahud)([Twitter](https://twitter.com/pahudnet)/[Facebook](https://www.facebook.com/pahudnet)). 
