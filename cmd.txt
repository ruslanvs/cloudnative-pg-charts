https://github.com/ruslanvs/cloudnative-pg-charts


helm upgrade --install cnpg -n cnpg-system --create-namespace charts/cloudnative-pg

kubectl apply -f cluster.yaml