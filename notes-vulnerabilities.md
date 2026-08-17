# Common vulnerabilities
## Command injection
-Injected command inherits process privileges which called system()/shell_exec()
-When using binary SUID with root privileges, may run injected command as root

### Separators
; - always run next command
&& - run next command only when first was ok
| - input of the second command is output of the first one
|| - run next command when first wasn't ok

### SUID
if /bin/sh calls bash then bash checks euid != ruid and drops euid (effective user id) to ruid (real user id) and run injected command as the user
if /bin/sh calls dash then dash doesn't check if SUID runs command and let you run your command with SUID privileges 
