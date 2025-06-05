1. Create Genesis cluster and install ArgoCD manually:
`kind delete cluster --name genesis && kind create cluster --name genesis && kc ns argocd && kns argocd && helm install argocd argo/argo-cd --version 8.0.14`

2. Bootstrap the Genesis cluster:
`helm install --set cluster=genesis --set enableClusters=true --set excludeSelf=false bootstrap apps/bootstrap`

3. Install the Opsteady cluster:
```
kubectl apply -f opsteady/project.yaml
kubectl apply -f clusters/opsteady.yaml
```

4. Switch context to Opsteady cluster and install Opsteady-wl cluster:
```
kubectl apply -f opsteady-wl/project.yaml
kubectl apply -f clusters/opsteady-wl.yaml
```
```
