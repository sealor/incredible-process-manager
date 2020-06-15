Incredible Process Manager
==========================

The IPM can be used to manage simple UNIX background processes. The development is not yet finished.

Usage
-----

```
usage: ipm (-s|-e|-d|--self-test|-h) [process-names|group-names]

The Incredible Process Manager starts and stops Unix processes.
It is designed to manage Unix services which depend on each other.
The configuration is read from task.conf.

commands:
-s	start process or group of processes
-e	stop process or group of processes
-d	display processes with their start configuration
-h	show this help

config file example:
# Group  Name      Dependencies  Start command
GroupA   SERVER    -             ./tcp-service-starter  nc -lvp 0
GroupA   ProcessA  SERVER        ./process-starter      sleep 1234
GroupB   ProcessB  SERVER        ./process-starter      sleep 1227

start command requirements:
- must stop after service is fully started and available
- holds exactly one process in background with env variable __IPM_ID
- this process is used for process termination
```