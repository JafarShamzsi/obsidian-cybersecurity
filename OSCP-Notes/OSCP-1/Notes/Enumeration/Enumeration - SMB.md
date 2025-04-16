Server Message Block is a protocol used in Microsoft systems to exhange file or messages. It has been attacked over the years and this led to an implementation to a better software: **Netbios**. Netbios is a session layer protocol that lets computers in the same network communicate and listens on port TCP 139. SMB is on port TCP 445. NBT (Netbios over TCP is often required to run among SMB for compatibility). There are many useful tools to scan Netbios, like **NMAP** or **nbtscan**. The following scenario uses `-r` that indicates nbtscan to use port UDP 137, the Netbios Name service port.

```shell
sudo nbtscan -r <target-range>
```

Enum4Linux can also be used to enumerate SMB/NetBIOS
```shell
sudo enum4linux <host>
```

To scan for SMB shares it can be used the tool `enum4linux` and then the connection can be tested with

```shell
smbclient -L //<IP>
```

With -L for share listing and then

```shell
smbclient //<IP> -U <USER>
```

To connect to a specific share (in this case without password protection)

NMAP offers too many scripts for enumeration or information gathering on Windows Host with Netbios enabled (eg: `--script smb-os-discovery`). From Windows the smb connections can be tested with

```powershell
net view \\<host> /all
```

With `/all` we can list Administrators shares ending with `$`

SMB can be exploited if the `signing is disabled`, with a [NTLM Relay attack](https://hackdefense.com/publications/het-belang-van-smb-signing/) we will cover in the next sections. Systems are susceptible to an NTLM relay attack because the recipient does not verify the content and origin of the message.

We can use this to query the NetBIOS name service for valid NetBIOS names, specifying the originating UDP port as 137 with the **-r** option.

```shell
sudo nbtscan -r 192.168.50.0/24
```
