# Question 1 - Environment Verification

## Task 1: User Identity

so first i need to check who i am on the system and what groups im part of

```bash
root@Assignment:~# whoami
root
root@Assignment:~# id
uid=0(root) gid=0(root) groups=0(root)
root@Assignment:~# groups
root
```

basically `whoami` shows my username which is root (administrator). `id` shows my user id (0 means root) and group ids. im in the root group which has full system access
https://cdn.discordapp.com/attachments/1438130151748665369/1457465715693977763/image.png?ex=695c1a39&is=695ac8b9&hm=031312dc4bd254c38b1b0617363172a0ec1e5c1f0bf2c5a1b906bc6ad7415ca7&

---

## Task 2: Workspace Validation

```bash
root@Assignment:~# pwd
/root
root@Assignment:~# ls -la
total 20
drwx------  3 root root 4096 Aug  9 19:39 .
drwxr-xr-x 18 root root 4096 Jan  4 20:00 ..
-rw-r--r--  1 root root  607 May 12  2025 .bashrc
-rw-r--r--  1 root root  132 May 12  2025 .profile
drwx------  2 root root 4096 Jan  4 19:48 .ssh
root@Assignment:~# 
```

`pwd` shows im in /root which is root users home directory. `ls -la` shows all files including hidden ones with permissions, owner, size etc

---

## Task 3: Environment Confirmation File

```bash
root@Assignment:~# echo "Linux user environment verified" > user_info.txt
root@Assignment:~# cat user_info.txt
Linux user environment verified
```

created user_info.txt with echo and output redirection. cat confirms the content is there

---

## Task 4: File Integrity Check

```bash
root@Assignment:~# wc -c user_info.txt
35 user_info.txt
```

wc -c counts characters. file has 35 chars including the newline

---

## Task 5: Learning the Tools

```bash
root@Assignment:~# mkdir --help
Usage: mkdir [OPTION]... DIRECTORY...
Create the DIRECTORY(ies), if they do not already exist.

Mandatory arguments to long options are mandatory for short options too.
  -m, --mode=MODE   set file mode (as in chmod), not a=rwx - umask
  -p, --parents     no error if existing, make parent directories as needed,
                    with their file modes unaffected by any -m option
  -v, --verbose     print a message for each created directory
  -Z                   set SELinux security context of each created directory
                         to the default type
      --context[=CTX]  like -Z, or if CTX is specified then set the SELinux
                         or SMACK security context to CTX
      --help        display this help and exit
      --version     output version information and exit

GNU coreutils online help: <https://www.gnu.org/software/coreutils/>
Full documentation <https://www.gnu.org/software/coreutils/mkdir>
or available locally via: info '(coreutils) mkdir invocation'
root@Assignment:~# 
```

used --help instead of man since man wasnt installed. the `-p` option is useful - it creates parent directories as needed. like `mkdir -p a/b/c` makes all 3 folders at once even if a and b dont exist yet

---

## Task 6: Home Directory (sorted)

```bash
root@Assignment:~# ls ~ | sort
user_info.txt
```

listed home directory and sorted alphabetically

---

## Task 7: Log Investigation

```bash
root@Assignment:~# grep "admin" log.txt
2026-01-05 08:01:15 - User admin logged in at 10:00 AM
2026-01-05 08:10:45 - Admin permissions granted to user
2026-01-05 08:25:12 - System admin performed backup
```

grep finds lines containing "admin" in the log file. found 3 matching lines

---

## Task 8: System Information

```bash
root@Assignment:~# uname -r
6.12.38+deb13-amd64
```

shows kernel version. this is ubuntu with kernel 5.15

---

## Task 9: Network Test

```bash
PING www.google.com (142.250.207.228) 56(84) bytes of data.
64 bytes from del12s11-in-f4.1e100.net (142.250.207.228): icmp_seq=1 ttl=110 time=1.89 ms
64 bytes from del12s11-in-f4.1e100.net (142.250.207.228): icmp_seq=2 ttl=110 time=1.93 ms
64 bytes from del12s11-in-f4.1e100.net (142.250.207.228): icmp_seq=3 ttl=110 time=1.91 ms
64 bytes from del12s11-in-f4.1e100.net (142.250.207.228): icmp_seq=4 ttl=110 time=1.90 ms

--- www.google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3005ms
rtt min/avg/max/mdev = 1.891/1.907/1.926/0.012 ms
```

sent 4 icmp packets to google. all came back so network is working fine

---

## Task 10: System Health

```bash
root@Assignment:~# uptime
 21:41:20 up  1:40,  2 users,  load average: 0.00, 0.00, 0.00
```

shows:
- current time 21:41
- system running for 1 hour 40 minutes
- 2 users logged in  
- load averages for 1, 5, 15 mins - numbers below 1 means system isnt stressed

---

**files created:** user_info.txt, log.txt
