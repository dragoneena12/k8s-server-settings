## make app secrets
```
kubectl create secret generic app-secret -n lapi-hotel-system --dry-run=client --from-file=config.ini -o yaml > app-secret-plain.yaml
kubeseal --controller-name=sealed-secrets < app-secret-plain.yaml -o yaml > app-secret.yaml
```

## make db password
```
kubectl create secret generic db-secret -n lapi-hotel-system --dry-run=client --from-literal=MARIADB_ROOT_PASSWORD=password -o yaml > db-secret-plain.yaml
kubeseal --controller-name=sealed-secrets < db-secret-plain.yaml -o yaml > db-secret.yaml
```

## access adminer
```
kubectl port-forward svc/adminer -n lapi-hotel-system 8080:8080 --address 0.0.0.0
```
