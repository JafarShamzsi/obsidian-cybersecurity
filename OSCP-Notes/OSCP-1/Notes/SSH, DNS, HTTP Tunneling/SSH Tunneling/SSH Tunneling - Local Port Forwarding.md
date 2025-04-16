In this case we run the command on the **TARGET** that becames the "forwarder" between **KALI** and the **IP-B**. This is useful to directly connect **KALI** to the **IP-B** machine, through the connection forwarded from **TARGET** to **IP-A**. The

```shell
ssh -N -L 0.0.0.0:<LOCAL-PORT>:<IP-B>:<REMOTE-PORT> user@<IP-A>
```

```

KALI ----- TARGET ----- IP-A ----- IP-B [REMOTE-PORT]
|________________________||__________|

```
