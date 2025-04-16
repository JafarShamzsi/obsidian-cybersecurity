If we find a SSH Key password protected we can use

```shell
ssh2john id_rsa > id_rsa.hash
```

We remove the filename at the beginning of the hash, as in the KeePass section and we use JohnTheRipper to crack the hash, but first we add our hashcat rules to the John configuration rules (if we want to use custom rules)

```shell
cat /home/kali/passwordattacks/my-rule.rule >> /etc/john/john.conf
```

And then the attack is run with

```shell
john --wordlist=ssh.passwords --rules=sshRules id_rsa.hash
```

Now we can login with the SSH key and we can use the cracked passphrase.