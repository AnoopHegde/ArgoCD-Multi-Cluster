# Argo CD Setup

## Install Argo CD

```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

## Run Argo CD in HTTP Mode(Insecure)

https://github.com/argoproj/argo-cd/blob/54f1572d46d8d611018f4854cf2f24a24a3ac088/docs/operator-manual/argocd-cmd-params-cm.yaml#L82

kubectl get cm -n argocd

kubectl edit cm argocd-cmd-params-cm -n argocd

data:

    server.insecure: "true"

 kubectl describe deployment/argocd-server -n argocd

 kubectl edit deployment/argocd-server -n argocd

## Expose Argo CD Server Service in NodePort Mode

```
kubectl edit svc argocd-server -n argocd
```

and change the type to NodePort from ClusterIP

## ARGOCD Credentials

admin

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 --decode ; echo

## Connect ArgoCD from Hub Cluster to mutli s3.139.90.129:31132poke clusters

argocd login  3.139.90.129:31132

argocd cluster add prdk8admin@spoke-cluster-1.us-east-2.eksctl.io --server 3.139.90.129:31132

argocd cluster add prdk8admin@spoke-cluster-2.us-east-2.eksctl.io --server 3.139.90.129:31132


