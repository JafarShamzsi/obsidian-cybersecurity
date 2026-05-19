This tools works like a VPN and routes our traffic through the SSH listener we spin on a server. First we have to set up `SOCAT` to listen in the , then we can scan the network simply using a normal NMAP.

```shell
socat TCP-LISTEN:<LOCAL-PORT>,fork TCP:<REMOTE-IP>:<REMOTE-PORT>
```

Next we run sshuttle specifying the subnets we want to be forwarded through the ssh connection

```shell
sshuttle -r database_admin@<REMOTE-IP>:<LOCAL-PORT> <SUBNET-1> <SUBNET-2>
```

Now, an NMAP on SUBNET-1 will work as we were in the same network.