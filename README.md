All plays will run on CentOS 7 or Ubuntu 16.04. They require the sudo password to be set. This can be done at runtime with -K, or by setting the variable "ansible_become_pass".

The Apache role installs an Apache 2 server with self-signed HTTPS and a strict TLS configuration.

The common role performs the following tasks:

1. It fully updates the host to the latest packages.
2. It cleans out any orphaned dependencies and the like with autoremove.
3. It installs some useful utilities: wget, nano, ntpd, and open-vm-tools.
4. It starts the firewall of the host, allows SSH, and sets the firewall to start on boot.
5. It installs your public SSH keys to the root account and a user of your choice.
6. It removes the host's default NTP servers and sets ntpd to use Google's NTP servers. (Warning: Google's NTP smears leap seconds)
7. It hardens the security settings for SSHD to only allow known secure cipher suites and MACs.
8. It forces root logins over SSH to use key-based auth.
9. It disables TCP timestamps.
10. Finally, it reboots the host to apply the changes and latest kernel.

The GitLab role installs a GitLab server. It is designed to be used with an external SMTP relay.

The MySQL role installs MariaDB/MySQL and completes mysql_secure_installation.

The Nextcloud role installs Nextcloud with Apache 2, PHP 7.0, and MariaDB/MySQL. It sets up self-signed HTTPS certs by default.
A Nextcloud instance installed with this play returns a 0/10 on OpenVAS.
DB name is "nextcloud". DB user is "nextcloud"
To remove the memcache warning on the Nextcloud Admin page, just add the line "'memcache.local' => '\OC\Memcache\APCu'," to /var/www/html/config/config.php.

The NGINX web server role installs an NGINX web server with self-signed HTTPS and a strict TLS configuration.

The PHP role installs PHP 7.

The reboot role reboots the host and, by default, waits up to 60 seconds for it to come back online, checking every 15 seconds. These values are relatively short, and geared mostly towards virtual machines. For physical hosts, higher values are recommended.

The update play is self explanatory. It autoremoves unneeded dependencies by default.

The WordPress role installs WordPress with Apache 2, PHP 7.0, and MariaDB/MySQL. It sets up self-signed HTTPS certs.
A WordPress instance installed with this play returns a 0/10 on OpenVAS.
DB name is "wordpress". DB user is "wordpress"

The LAMP play installs the Apache, MySQL, and PHP roles and then reboots the host.

The LEMP play installs the NGINX web server, MySQL, and PHP roles and then reboots the host.