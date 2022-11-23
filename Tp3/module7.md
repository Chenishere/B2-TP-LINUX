## Module 7 : Fail2ban

### Installations 
```
[ynce@db ~]$ sudo dnf install epel-release -y
Package epel-release-9-4.el9.noarch is already installed.
Dependencies resolved.
Nothing to do.
Complete!

[ynce@db ~]$ sudo dnf install fail2ban -y
Installed:
  esmtp-1.2-19.el9.x86_64                        fail2ban-1.0.1-2.el9.noarch
  fail2ban-firewalld-1.0.1-2.el9.noarch          fail2ban-sendmail-1.0.1-2.el9.noarch
  fail2ban-server-1.0.1-2.el9.noarch             libesmtp-1.0.6-24.el9.x86_64
  liblockfile-1.14-9.el9.x86_64                  python3-systemd-234-18.el9.x86_64

Complete!
``` 

### Configuration de Fail2ban

```
[ynce@db ~]$ sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
``` 

```
[ynce@db ~]$ sudo mv /etc/fail2ban/jail.d/00-firewalld.conf /etc/fail2ban/jail.d/00-firewalld.local

[ynce@db ~]$ sudo nano /etc/fail2ban/jail.d/sshd.local   
[sshd]
enabled = true
bantime = 1d
findtime = 1m
