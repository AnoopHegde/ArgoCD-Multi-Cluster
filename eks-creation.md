# EKS Setup

## EKS Clusters Creation

eksctl create cluster --name hub-cluster --region us-east-2

eksctl create cluster --name spoke-cluster-1 --region us-east-2

eksctl create cluster --name spoke-cluster-2 --region us-east-2

## EKS Clusters Deletion

eksctl delete cluster --name hub-cluster --region us-east-2

eksctl delete cluster --name spoke-cluster-1 --region us-east-2

eksctl delete cluster --name spoke-cluster-2 --region us-east-2
