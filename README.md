## kubectlコマンド
*create sealed-secret from file*
```
$ kubectl create secret generic <secret_name> -n <namespace> --dry-run=client --from-file=config -o yaml > <secret_filename>.yaml
$ kubeseal --controller-name=sealed-secrets < <secretfilename>.yaml -o yaml > <sealed_secret_filename>.yaml
```

*create sealed-secret from literal*
```
$ kubectl create secret generic <secret_name> -n <namespace> --dry-run=client --from-literal=<key>=<value> -o yaml > <secret_filename>.yaml
$ kubeseal --controller-name=sealed-secrets < <secretfilename>.yaml -o yaml > <sealed_secret_filename>.yaml
```
