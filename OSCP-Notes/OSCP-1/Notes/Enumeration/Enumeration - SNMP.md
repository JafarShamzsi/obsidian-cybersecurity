Simple Network Management Protocol or SNMP is a UDP based protocol, implemented at the beginning in not a very safe way. It has a database (MIB) with information related to network. The default SNMP port is 161 UDP. Until the third version of this protocol, SNMPv3 this protocol was poorly secured. There are many tools to use here because SNMP can tell us many things about an organization, based on the response of the server. We can use `onesixtyone` for basic bruteforce and enumeration and `snmpwalk` to access data in MIB database. The “SNMP community string” is like a user ID or password that allows access to a router's or other device's statistics. SNMP community strings are used only by devices which support the SNMPv1 and SNMPv2c protocol. SNMPv3 uses username/password authentication, along with an encryption key. By convention, most SNMPv1-v2c equipment ships from the factory with a read-only community string set to “public”. It is standard practice for network managers to change all the community strings to customized values in the device setup.

```shell
snmpwalk -c public -v1 -t 5 <target>
```

In this way we enumerate all the MIB tree of a SNMPv1 version with a timeout of 5 seconds, on the target IP.

```
# MIB Value                    Microsoft Windows SNMP parameters
1.3.6.1.2.1.25.1.6.0           System Processes
1.3.6.1.2.1.25.4.2.1.2         Running Programs
1.3.6.1.2.1.25.4.2.1.4         Processes Path
1.3.6.1.2.1.25.2.3.1.4         Storage Units
1.3.6.1.2.1.25.6.3.1.2         Software Name
1.3.6.1.4.1.77.1.2.25          User Accounts
1.3.6.1.2.1.6.13.1.3           TCP Local Ports
```

To search deeper use the extend functionality of SNMP. As suggested in [HackTricks](https://book.hacktricks.xyz/network-services-pentesting/pentesting-snmp/snmp-rce)

```shell
apt-get install snmp-mibs-downloader
snmpwalk -v2c -c public <IP> NET-SNMP-EXTEND-MIB::nsExtendOutputFull
```

For basic enumeration

```shell
echo public > community
echo private >> community
echo manager >> community
for ip in $(seq 1 254); do echo 192.168.50.$ip; done > ips
onesixtyone -c community -i ips
```