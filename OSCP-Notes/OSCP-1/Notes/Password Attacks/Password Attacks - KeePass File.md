If we dump a KeePass Database (Database.kdbx), we can try to crack it with

```shell
keepass2john Database.kdbx > keepass.hash
```

First we remove the "Database:" string from the hash, then we run our attack. The **13400** is the code for Hashcat to crack KeePass hashes.

```shell
hashcat -m 13400 keepass.hash /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/rockyou-30000.rule --force
```
