Leaving a backdoor in a system can easily let us come back later and gain immediatly control over the machine. The simplest "root" backdoor on Linux can be done with bash. Just using

```shell
sudo chmod +s /bin/bash
```

Will set the SUID over the bash binary. That means that using

```shell
/bin/bash -p
```

A **root** shell will be gained. The "-p" option preserve the SUID bit. In this way the bash program is called with the owner privileges (root) and if It is not called with "-p" It remains a normal bash shell. Many programs like linpeas.sh or some privesc checker will anyway find this backdoor and report it.