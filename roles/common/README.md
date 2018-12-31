All plays will run on CentOS 7 or Ubuntu 18.04. They require the sudo password to be set. This can be done at runtime with -K, or by setting the variable "ansible_become_pass".

This role performs the following tasks:

1. It fully updates the host to the latest packages.
1. It cleans out any orphaned dependencies and the like with autoremove.
1. It installs some useful utilities: wget, nano, ntpd, and open-vm-tools.
1. It starts the firewall of the host, allows SSH, and sets the firewall to start on boot.
1. It installs your public SSH keys to the root account and a user of your choice.
1. It hardens the security settings for SSHD to only allow known secure cipher suites and MACs.
1. It forces root logins over SSH to use key-based auth.
1. It disables TCP timestamps.
1. Finally, it reboots the host to apply the changes and latest kernel.