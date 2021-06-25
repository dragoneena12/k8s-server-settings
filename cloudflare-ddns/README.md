## set api-secret
```
kubectl create secret generic api-secret -n cloudflare-ddns --dry-run=client --from-literal=API_KEY=xxxxxxxxxxx -o yaml > api-secret-plain.yaml
kubeseal --controller-name=sealed-secrets < api-secret-plain.yaml -o yaml > api-secret.yaml
```
