This lets us forward all ports to the **KALI** machine through the connection forwarded from **TARGET** to **IP-A**. It is useful when we want to perform a network scan and in the IP-A machine there isn't the NMAP binary.

```shell
ssh -N -D 0.0.0.0:<LOCAL-PORT> user@<IP-B>
```

```
     
KALI ----- TARGET ----- IP-A ----- IP-B [ALL PORTS]
 |________________________||__________|

```

To use commands we must pass through the SOCKS5 protocol, with the `proxychains` client. This client will forward all traffic to the proxy on the ssh listening port. In this way all the traffic will go through this connection. An example of the usage of proxychains for an nmap scan of the victim's subnet is the following:

```shell
proxychains nmap -sV -A -O 192.168.1.0/24
```

Proxychain configuration at `/etc/proxychains.conf` must be configured

```shell
[ProxyList]
socks5 <IP-B> <LOCAL-PORT>
```