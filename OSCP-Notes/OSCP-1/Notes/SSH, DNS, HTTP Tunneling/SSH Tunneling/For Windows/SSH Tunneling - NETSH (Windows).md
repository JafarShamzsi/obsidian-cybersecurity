From the Microsoft documentation: "Netsh is a command-line scripting utility that allows you to display or modify the network configuration of a computer that is currently running. Netsh commands can be run by typing commands at the netsh shell and be used in batch files or scripts. Remote computers and the local computer can be configured by using netsh commands. First we must add the interface proxy with

```powershell
netsh interface portproxy add v4tov4 listenport=<LOCA-PORT> listenaddress=<LOCAL-IP> connectport=<REMOTE-PORT> connectaddress=<REMOTE-IP>
```

To show the status of the proxy

```powershell
netsh interface portproxy show all
```

We must allow the firewall rule to open a port in order to use the proxy. For this reason netsh requires Administrator privileges.

```powershell
netsh advfirewall firewall add rule name="port_forward_ssh_PORT" protocol=TCP dir=in localip=<LOCAL-IP> localport=<LOCAL-PORT> action=allow
```

Now, querying the LOCAL-IP with a connection, will connect the Kali machine to the REMOTE-IP on the REMOTE-PORT. At the end of the attack we should restore the firewall rules with

```powershell
netsh advfirewall firewall delete rule name="port_forward_ssh_PORT"
netsh interface portproxy del v4tov4 listenport=<LOCAL-IP> listenaddress=<LOCAL-IP>
```
