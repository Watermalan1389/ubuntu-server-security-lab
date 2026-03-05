This experiment demonstrates a brute-force attack against an SSH server using the password cracking tool Hydra.

The goal of this test is to simulate a real-world attack where an attacker attempts to gain unauthorized access to a server by trying many passwords from a common password list.

This attack was performed in a controlled home lab environment.

Target System

Target machine:

User: watermalan

IP Address: 192.168.100.141

Service: SSH

Port: 22

Attacker machine:

Kali Linux

Wordlist Used

The attack uses the rockyou.txt password wordlist, which contains millions of commonly used passwords.

Location of the wordlist:

/usr/share/wordlists/rockyou.txt
Hydra Command

The following command was used to perform the brute-force attack:

sudo hydra -l watermalan -P /usr/share/wordlists/rockyou.txt -t 4 ssh://192.168.100.141
Command Explanation

-l specifies the target username

-P specifies the password wordlist

-t 4 runs 4 parallel attack threads

ssh:// specifies the protocol being attacked

192.168.100.141 is the target server IP address

Attack Result

Hydra attempted multiple login attempts using passwords from the wordlist.

The login attempts generated failed authentication logs on the Ubuntu server, which can later be detected and mitigated using security tools such as Fail2Ban.

Screenshots of the attack and server logs are available in the screenshots folder.

Security Implications

This test demonstrates how servers that allow unlimited login attempts are vulnerable to brute-force attacks.

In the next phase of this project, defensive tools such as:

Firewall rules

Fail2Ban intrusion prevention

will be implemented to automatically detect and block these attacks.
