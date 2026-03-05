Overview

Fail2Ban is a tool that monitors server logs and blocks IP addresses showing suspicious activity. In this lab, it is used to protect the Ubuntu server from SSH brute-force attacks.

Installation

Fail2Ban was installed on the server using:

sudo apt update
sudo apt install fail2ban -y
sudo systemctl status fail2ban

The service started automatically.

SSH Configuration

The SSH jail was configured in /etc/fail2ban/jail.local:

[sshd]
enabled = true
port = ssh
maxretry = 3
findtime = 10m
bantime = 10m

enabled = true activates monitoring

maxretry = 3 blocks IP after three failed attempts

bantime = 10 sets the ban time to 10 minutes

After editing, the service was restarted:

sudo systemctl restart fail2ban
sudo fail2ban-client status sshd
Testing

A simulated SSH brute-force attack was performed from the Kali Linux machine. Fail2Ban blocked the attacking IP after three failed login attempts.

Banned IPs and logs were verified with:

sudo fail2ban-client status sshd
tail -f /var/log/fail2ban.log
Screenshots

Screenshots include:

Fail2Ban service status

SSH jail status

Logs showing banned IPs

All screenshots are saved in the screenshots/ folder.
