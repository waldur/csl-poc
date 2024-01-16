# csl-poc

## Prerequisite for an application installation

```bash
ARGOCD_SERVER_IP=$(kubectl get service argocd-server -n argocd -o jsonpath={.spec.clusterIP})
ARGOCD_ADMIN_PASSWORD=$(argocd admin initial-password -n argocd | head -n1)
argocd login $ARGOCD_SERVER_IP:80 --username admin --password $ARGOCD_ADMIN_PASSWORD --name default
# validate
argocd account get-user-info
```

## Application installation

### Longhorn

```bash
argocd app create --repo https://github.com/waldur/csl-poc.git --path applications/longhorn
argocd app sync argocd/longhorn
```
