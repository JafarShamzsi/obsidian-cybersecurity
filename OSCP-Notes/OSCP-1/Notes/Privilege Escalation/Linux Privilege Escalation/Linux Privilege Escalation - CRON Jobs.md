The Linux-based job scheduler is known as cron. Scheduled tasks are listed under the
/etc/cron.* directories, where * represents the frequency at which the task will run. For example,
tasks that will be run daily can be found under /etc/cron.daily. Each script is listed in its own
sub-directory.

```shell
ls -lah /etc/cron*
```

It is worth noting that system administrators often add their own scheduled tasks in the
/etc/crontab file. These tasks should be inspected carefully for insecure file permissions, since
most jobs in this particular file will run as root. To view the current user’s scheduled jobs, we can
run crontab followed by the -l parameter.

```shell
crontab -l
```
