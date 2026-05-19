As always, enumerate all the possible things, login to SMB/SSH/Other services with default userames ad passwords or perform a _null login_ as the following

For rpcclient

```shell
rpcclient 10.10.10.192 -U""
```

For for smbclient

```shell
smbclient -L 10.10.10.192 -U""
```
