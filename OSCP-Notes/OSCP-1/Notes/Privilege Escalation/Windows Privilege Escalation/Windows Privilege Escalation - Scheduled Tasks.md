If a task is executed periodically, we can exploit the called program if we have write permissions on it. To seek for scheduled tasks we can run.

```powershell
schtasks /query /fo LIST /v
```

Eventually we can use `findstr` if we want to search for something specific. After that we can replace the program with a simple .exe that creates a new admin user.
