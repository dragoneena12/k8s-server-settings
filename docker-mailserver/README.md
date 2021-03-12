## Add mail-account
```
$ ./setup.sh -i mailserver/docker-mailserver email add lapi@lapi.gq
```
or
```
$ openssl passwd -6 -salt $(openssl rand -base64 16) PASSWORD
```

## Gen DKIM
```
$ ./setup.sh -i mailserver/docker-mailserver config dkim
```
