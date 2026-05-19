This, similar to the Local Dynamic port forwarding lets through the usage of `proxychains` to connect to the on all ports, based redirecting the traffic from the IP-A to the Kali machine on the

```shell
ssh -N -R <LOCAL-PORT> kali@<KALI-IP>
```

```
    RECEIVED AS OUTBOUND
 |¯¯¯¯¯¯¯¯¯¯¯>¯¯¯¯¯¯¯¯¯¯¯¯¯|      
KALI ----- TARGET ----- IP-A ----- IP-B [ALL PORTS]
 |___________<____________||_________|
          OUTBOUND
```