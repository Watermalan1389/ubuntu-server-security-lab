Overview

A firewall was configured on the Ubuntu server to control network access and block unauthorized traffic. The firewall used is UFW (Uncomplicated Firewall), which is the default firewall tool on Ubuntu.

1. Install and Enable UFW

UFW is installed and enabled with the following commands:

sudo apt update
sudo apt install ufw -y
sudo ufw enable
sudo ufw status

After enabling, the firewall is active and monitoring all incoming connections.

2. Configure Rules

The firewall was configured to allow only SSH connections on port 22. All other incoming connections were blocked by default.

sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow ssh
sudo ufw status numbered

Explanation of commands:

default deny incoming → blocks all incoming connections by default

default allow outgoing → allows outgoing connections

allow ssh → permits SSH connections to the server

status numbered → shows the list of rules with numbers

3. Testing the Firewall

After configuring, connectivity was tested:

SSH access from the Kali attacker machine was allowed.

Other ports were blocked, ensuring no unauthorized access.

Screenshot examples are saved in the screenshots/ folder:

UFW status showing allowed ports

Firewall rules list
