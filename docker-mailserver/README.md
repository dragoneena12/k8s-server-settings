## Add mail-account
```
$ ./setup.sh -i mailserver/docker-mailserver email add lapi@lapi.tokyo
```
or
```
$ openssl passwd -6 -salt $(openssl rand -base64 16) PASSWORD
```

### convert to sealed secret
```
$ kubectl create secret generic postfix-accounts -n docker-mailserver --dry-run=client --from-file=config -o yaml > postfix-accounts-plain.yaml
$ kubeseal --controller-name=sealed-secrets < postfix-accounts-plain.yaml -o yaml > postfix-accounts.yaml
```

## Gen DKIM
```
$ ./setup.sh -i mailserver/docker-mailserver config dkim
```

### convert to sealed secret
```
$ kubectl create secret generic opendkim-keys-lapi-gq -n docker-mailserver --dry-run=client --from-file=config/opendkim/keys/lapi.tokyo -o yaml > opendkim-keys-lapi-gq-plain.yaml
$ kubeseal --controller-name=sealed-secrets < opendkim-keys-lapi-gq-plain.yaml -o yaml > opendkim-keys-lapi-gq.yaml
```
