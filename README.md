## CI

Changes to GitLab can be applied by manually starting jobs. Always make sure you have SSH access for a roll-back.

### Apply a change

Start the "run" task.

### Update GitLab

Start the "update" task.

### Roll-Back

1. Create the following symbolic link:
```bash
$ ls -s /opt/config/.env.gitlab /opt/gitlab/.env
```
TODO

### Back up

TODO

## Redis Warnings:

* WARNING: The TCP backlog setting of 511 cannot be enforced because /proc/sys/net/core/somaxconn is set to the lower value of 128.
    * This warning is solved setting `net.core.somaxconn=1024` in `docker-compose.yaml`
* WARNING overcommit_memory is set to 0! Background save may fail under low memory condition. To fix this issue add 'vm.overcommit_memory = 1' to /etc/sysctl.conf and then reboot or run the command 'sysctl vm.overcommit_memory=1' for this to take effect.
    * 0: heuristic overcommit; 1: always overcommit, never check; 2: always check, never overcommit
    * The default sounds sane; we do not want to overcommit without constraints.
    * This Warning remains.
* WARNING you have Transparent Huge Pages (THP) support enabled in your kernel. This will create latency and memory usage issues with Redis. To fix this issue run the command 'echo never > /sys/kernel/mm/transparent_hugepage/enabled' as root, and add it to your /etc/rc.local in order to retain the setting after a reboot. Redis must be restarted after THP is disabled.
    * THPs are now disabled.
    * /etc/default/grub: GRUB_CMDLINE_LINUX_DEFAULT="transparent_hugepage=never quiet splash"

