To get all capabilities on file in the system we can use the following commands, also grepping for a specific capability.

```shell
/usr/sbin/getcap -r / 2>/dev/null
/usr/sbin/getcap -r / 2>/dev/null | grep -i setuid
```
