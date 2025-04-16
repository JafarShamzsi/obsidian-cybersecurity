Simple Mail Transfer Protocol is a standard protocol for mail transmission. It can be enumerated on port 25 with netcat. We can ask for known users or bruteforce the server for gaining information.

```shell
nc -nv <target> 25
> VRFY username
...
> EXPN username
```

With `VRFY` (verify) we ask to the server if the username is present and with `EXPN` (expand) if which mailing lists the user is subscribed to. On a Windows system we can use

```powershell
Test-NetConnection -Port 25 <target>
```

Or `telnet`.

### SWAKS

Swaks is a good tool for interacting with SMTP servers. It offers also an easy way to attach files. This is a good alternative to netcat for email sending.

```shell
swaks --to receiver@mail.com --from sender@mail.com --auth LOGIN --auth-user sender@mail.com --header-X-Test "Header" --server <TARGET-IP> --attach file.txt
```