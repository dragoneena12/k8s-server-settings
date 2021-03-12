# k8s-server-settings
## 既存の永続ディスクを PersistentVolume として使用する
https://cloud.google.com/kubernetes-engine/docs/how-to/persistent-volumes/preexisting-pd

## kubeseal
```
kubectl -n docker-mailserver create secret generic test-secret --dry-run --from-literal=password=password -o yaml > test-secret.yaml
kubeseal --controller-name=sealed-secrets < test-secret.yaml -o yaml > sealed-test-secret.yaml
```