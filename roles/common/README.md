All plays will run on CentOS 7 or Ubuntu 16.04. They require the sudo password to be set. This can be done at runtime with -K, or by setting the variable "ansible_become_pass".

This role performs the following tasks:

1. It fully updates the host to the latest packages.
2. It cleans out any orphaned dependencies and the like with autoremove.
3. It installs some useful utilities: wget, nano, ntpd, and open-vm-tools.
4. It starts the firewall of the host, allows SSH, and sets the firewall to start on boot.
5. It installs your public SSH keys to the root account and a user of your choice.
6. It removes the host's default NTP servers and sets ntpd to use Google's NTP servers. (Warning: Google's NTP smears leap seconds)
7. It configures rsyslogd to log everything to a remote server over UDP. The server and port are configures as variables.
8. It hardens the security settings for SSHD to only allow known secure cipher suites and MACs.
9. It forces root logins over SSH to use key-based auth.
10. It disables TCP timestamps.
11. Finally, it reboots the host to apply the changes and latest kernel.