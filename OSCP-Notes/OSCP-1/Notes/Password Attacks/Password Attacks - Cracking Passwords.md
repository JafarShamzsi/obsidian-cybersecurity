With John and Hashcat we can craft customized mutating wordlist that let us modify the original wordlist while executing. In the [Hashcat Wiki](https://hashcat.net/wiki/doku.php?id=rule_based_attack) are shown all possible combinations for password mutation. For example, the following rule capitalizes each first letter and adds `1` and then `!` for each word.

```hashcat-rule
c $1
c $!
```

For a wordlist with the single word `test`, this will create the following mutated wordlist

```password-example
Test1
Test!
```

The attack will be the following

```shell
hashcat --wordlist=/usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/my-rule.rule user.hash
```