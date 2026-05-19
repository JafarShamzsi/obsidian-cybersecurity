It is more common for firewalls and network administration rules to have only filtering in the inbound traffic, but less filtering on the outbound connections. We can use Remote Port Forwarding to mitigate this defense. The following command is a Remote Port Forwarding from the Kali machine serving the SSH on port LOCAL-PORT and forwarding all the connections to the IP-B on the REMOTE-PORT

```shell
ssh -N -R 127.0.0.1:<LOCAL-PORT>:<IP-B>:<REMOTE-PORT> kali@<KALI-IP>
```

```
    RECEIVED AS OUTBOUND
 |¯¯¯¯¯¯¯¯¯¯¯>¯¯¯¯¯¯¯¯¯¯¯¯¯|      
KALI ----- TARGET ----- IP-A ----- IP-B [REMOTE PORT]
 |___________<____________||_________|
          OUTBOUND
```