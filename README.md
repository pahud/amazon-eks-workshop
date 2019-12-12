# amazon-eks-workshop
Amazon EKS workshop walkthrough repository. 

This is a collection of Amazon EKS popular topics and assets aimed to help you successfully build your Amazon EKS workload.



## Getting Started - create cluster

Options to create your own Amazon EKS environment:


1. [Create your EKS Cluster with eksctl](./00-getting-started/create-eks-with-eksctl.md) - A super powerful Amazon EKS CLI.

2. [aws-samples/amazon-eks-refarch-cloudformation](https://github.com/aws-samples/amazon-eks-refarch-cloudformation) -  Reference architecture of Amazon EKS with modern cloudformation templates. Create the `cluster` and `nodegroup` of `mixed instance types` and `purchase options` by simply `make create-eks-cluster`.

3. 💥 [Create EKS cluster and nodegroups with AWS CDK](https://github.com/aws-samples/amazon-eks-refarch-cloudformation/blob/master/cdk/README.md
) by aws-samples/amazon-eks-refarch-cloudformation   


## Basic Administration

[Working with kubectl for basic administrations](./02-kubectl-basic-admin/kubectl-basic-admin.md)

## Amazon EKS with AWS Fargate

 💥 [Amazon EKS and AWS Fargate with alb-ingress-controller](./eks-fargate/README.md)
 
 💥 [(Youtube)AWS re:Invent 2019: [NEW LAUNCH!] Running Kubernetes Applications on AWS Fargate (CON326-R1)](https://www.youtube.com/watch?v=m-3tMXmWWQw&feature=youtu.be)

## Creating Services

[ClusterIP, NodePort and LoadBalancer](https://github.com/pahud/amazon-eks-workshop/tree/master/03-creating-services)

## Ingress Options

ALB Ingress Controller([GitHub](https://github.com/kubernetes-sigs/aws-alb-ingress-controller)) 

 - [Installing alb-ingress-controller with Helm](https://github.com/pahud/aws-containers-workshop/tree/master/lab2#put-extra-role-policy-on-the-eks-nodegroup)
 
Traefik Ingress([official doc](https://docs.traefik.io/user-guide/kubernetes/)|[walkthrough](./03-creating-services/ingress/traefik-ingress/README.md))

Nginx Ingress([github](https://github.com/kubernetes/ingress-nginx))

NLB+Nginx Ingress([AWS blogpost](https://aws.amazon.com/blogs/opensource/network-load-balancer-nginx-ingress-controller-eks/))

HAProxy Kubernetes Ingress([official doc](https://www.haproxy.com/blog/haproxy-2-0-and-beyond/#kubernetes-ingress-controller)|[github](https://github.com/haproxytech/kubernetes-ingress))

Kong Ingress([github](https://github.com/Kong/kubernetes-ingress-controller))



   

## Development with Amazon EKS

[Create your 1st app from scratch and deploy into Amazon EKS](https://github.com/pahud/greeting)


## AWS CDK with Amazon EKS

💥 [CDK samples](https://github.com/aws-samples/amazon-eks-refarch-cloudformation/blob/master/cdk/README.md
) from aws-samples/amazon-eks-refarch-cloudformation


## Helm and Charts

[Installing Helm](./00-getting-started/installing-helm.md)



## Spot and Lambda Integration

💥 [awslabs/amazon-eks-serverless-drainer](https://github.com/awslabs/amazon-eks-serverless-drainer) - Amazon EKS node drainer with AWS Lambda

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

[https://github.com/atlassian/escalator](atlassian/escalator) - a batch or job optimized horizontal autoscaler for Kubernetes



## Log Consolidation

Fluentd integration



## CI/CD

[Amazon EKS with AWS CodeBuild integration](https://github.com/pahud/eks-kubectl-docker#codebuild-support) 

💥[Amazon EKS Canary Deployment with AWS App Mesh and AWS Step Function](https://github.com/aws-samples/eks-canary-deployment-stepfunction)

[Amazon EKS Continuous Deployment Sample using AWS CodePipeline](https://github.com/chankh/eksutil/tree/master/lambda/codepipeline)

[Automate Kubernetes deployment on Amazon EKS with buddy.works](https://buddy.works/blog/amazon-eks-kubernetes)

[Blog - Continuous Delivery with Amazon EKS and Jenkins X](https://amzn.to/2JM2luY) 

💥 Create 12 EKS clusters in parallel one for each in different regions with `Codepipeline` cross region capabilities([demo tweet](https://twitter.com/pahudnet/status/1098597986165239811) and [cfn template](https://github.com/pahud/eks-templates/blob/master/cloudformation/codepipeline.yml))



## Service Discovery

[ExternalDNS and Route53 Auto Naming API](https://dev.classmethod.jp/cloud/aws/external-dns-eks/)



## Service Mesh

💥[Amazon EKS Canary Deployment with AWS App Mesh and AWS Step Function](https://github.com/aws-samples/eks-canary-deployment-stepfunction)

[Installing Istio 1.x on Amazon EKS](https://github.com/pahud/amazon-eks-workshop/tree/master/06-service-mesh/Istio)

Blog - Getting Started with Istio on Amazon EKS - https://amzn.to/2wo3inY

How to integrate AWS ALB with istio v1.0 by *Chuan-Yen Chiang* - https://medium.com/@cy.chiang/how-to-integrate-aws-alb-with-istio-v1-0-b17e07cae156




## CloudWatch Events Integration

[CloudWatch Events scheduled kubectl execution from within AWS Fargate](https://github.com/pahud/eks-kubectl-docker#aws-fargate-with-cloudwatch-event-scheduled-events)([Tweet](https://twitter.com/pahudnet/status/1047166317042618368))



## Amazon EKS and AWS Lambda Integration

💥 [aws-samples/lambda-layer-kubectl](https://github.com/aws-samples/aws-lambda-layer-kubectl) - AWS Lambda layer for kubectl - Run `kubectl` command in AWS Lambda 



## Amazon EKS and CloudWatch Integration

[K8s Cloudwatch Adapter](https://github.com/chankh/k8s-cloudwatch-adapter) - and subscribe this [issue](https://github.com/aws/containers-roadmap/issues/120) in AWS container public roadmap.

[Cloudwatch Container Insights](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/ContainerInsights.html) - monitoring kubernetes resources



## Multi-tenancy

Multiple EKS clusters sharing single VPC and ALB - ([tweet](https://twitter.com/pahudnet/status/1044988111694876672)|[architecture](https://pbs.twimg.com/media/DoCLDjfUwAA4s2_.jpg))

## Public References
**SkyScanner: Building Highly-Available, Multi-Region Kubernetes Clusters on 100% Amazon EC2 Spot**([Youtube](https://www.youtube.com/watch?v=99nNHsbwBpg))

