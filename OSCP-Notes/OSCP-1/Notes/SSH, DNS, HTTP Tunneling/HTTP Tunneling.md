### CHISEL

[Chisel](https://github.com/jpillora/chisel) is an HTTP tunnel that forwards all the network connection through the HTTP protocol. It can be used combined with SSH to provide a good way to bypass firewalls that allows only Web traffic. Chisel uses a client/server model and binds the connection to the SOCKS port on the kali machine.

First we start chisel `SERVER` executable. It can happen that the target doesn't have the chisel executable. In this case we must provide it first.

```shell
chisel server --port <LOCAL-PORT> --reverse
```

On the `CLIENT` we must bind the connection with the server. The R specifies SOCKS reverse tunneling that bounds on port 1080 on the kali machine by default (`ss -ntplu` to check the bind status)

```shell
/tmp/chisel client <KALI-IP>:<LOCAL-PORT> R:socks > /dev/null 2>&1 &
```

Now, on the server we can navigate through the chisel tunnel with HTTP connection. We specify the ProxyCommand option that is the SSH option to specify a SOCKS5 connection and we use ncat, a modified version of netcat that accepts a SOCKS5 connection.

```shell
ssh -o ProxyCommand='ncat --proxy-type socks5 --proxy 127.0.0.1:1080 %h %p' user@<REMOTE-IP>
```

Alternately we can use proxychains bound on `127.0.0.1` on port `1080`. This is an example with smbclient.

```shell
proxychains smbclient -L \\<REMOTE-IP>
```