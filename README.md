All scripts require the sudo password to be set. This can be done at runtime with -K, or by setting the variable "ansible_become_pass".

The Initial Configuration script performs the following tasks on either CentOS 7 Minimal, or Ubuntu 16.04 Server:

1. It fully updates the host to the latest packages.
2. It cleans out any orphaned dependencies and the like with autoremove.
3. It installs some useful utilities: wget, nano, ntpd, and open-vm-tools.
4. It starts the firewall of the host, allows SSH, and sets the firewall to start on boot.
5. It installs your public SSH keys to the root account and a user of your choice. All variables are set in ssh_vars.yml.
6. It removes the host's default NTP servers and instead sets ntpd to use Google's NTP servers. (Warning: Google's NTP smears leap seconds)
7. It hardens the security settings for SSHD to only allow known secure cipher suites.
8. It forces root logins over SSH to use key-based auth.
9. It disables TCP timestamps.
10. Finally, it reboots the host to apply the changes and latest kernel.

The MySQL script installs MariaDB on CentOS 7, and completes mysql_secure_installation. All variables are set in mysql_vars.yml

The Nextcloud script installs Nextcloud on CentOS 7, with Apache 2, PHP 7.0, and MariaDB. It sets up self-signed HTTPS certs by default. All variables are set in nextcloud_vars.yml
DB name is "nextcloud". DB user is "nextcloud"
If the memcache warning bothers you, just add the line "'memcache.local' => '\OC\Memcache\APCu'," to /var/www/html/config/config.php.

The Update script is self explanatory. It autoremoves unneeded dependencies by default.

reboot.yml is also self explanatory.