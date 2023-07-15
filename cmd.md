# CloudNativePG
https://github.com/cloudnative-pg/cloudnative-pg/blob/main/docs/src/quickstart.md
https://github.com/ruslanvs/cloudnative-pg-charts
## Install CloudNativePG
```
kubectl apply -f \
  https://raw.githubusercontent.com/cloudnative-pg/cloudnative-pg/release-1.20/releases/cnpg-1.20.1.yaml
```
## Deploy a PostgreSQL cluster
```
kubectl apply -f cluster.yaml -n production
```
## Uninstallation
```
kubectl delete -f cluster.yaml -n production
```
## Local Testing
```
kubectl -n production port-forward service/cnpg-cluster-rw 5432:5432
psql -U app -d app -W
```
## Secrets
```
kubectl get secret -n production "cnpg-cluster-app" -o jsonpath='{.data}' | json_pp
kubectl get secret -n production "cnpg-cluster-app" -o jsonpath='{.data.username}' | base64 --decode && echo
kubectl get secret -n production "cnpg-cluster-app" -o jsonpath='{.data.password}' | base64 --decode && echo
kubectl get secret -n production "cnpg-cluster-app" -o jsonpath='{.data.pgpass}' | base64 --decode  && echo

kubectl get secret -n production "cnpg-cluster-ca" -o jsonpath='{.data}' | json_pp
```