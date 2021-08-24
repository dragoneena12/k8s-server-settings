## make app secrets
```
kubectl create secret generic app-secret --dry-run=client --from-file=config.ini -o yaml > app-secret-plain.yaml
kubeseal --controller-name=sealed-secrets < app-secret-plain.yaml -o yaml > app-secret.yaml
```

## make db password
```
kubectl create secret generic db-secret --dry-run=client --from-literal=MARIADB_ROOT_PASSWORD=password -o yaml > db-secret-plain.yaml
kubeseal --controller-name=sealed-secrets < db-secret-plain.yaml -o yaml > db-secret.yaml
```

## make front envs
```
kubectl create configmap front-env --dry-run=client --from-file=.env.local -o yaml > front-env.yaml
```

## access adminer
```
kubectl port-forward svc/adminer 8080:8080 --address 0.0.0.0
```
