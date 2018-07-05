# Ansible Plays and Roles
All plays will run on CentOS 7 or Ubuntu 16.04 unless stated otherwise. They require the sudo password to be set. This can be done at runtime with `-K`, or by setting the variable `ansible_become_pass`.

#### Apache
The Apache role installs an Apache 2 server with self-signed HTTPS and a strict TLS configuration.

#### Common
The common role performs the following tasks:

1. It fully updates the host to the latest packages.
2. It cleans out any orphaned dependencies and the like with autoremove.
3. It installs some useful utilities: wget, nano, ntpd, and ovirt-guest-agent.
4. It starts the firewall of the host, allows SSH, and sets the firewall to start on boot.
5. It installs your public SSH keys to the root account and a user of your choice.
6. It removes the host's default NTP servers and sets ntpd to use Google's NTP servers. (Warning: Google's NTP smears leap seconds)
7. It configures rsyslogd to log everything to a remote server over UDP. The server and port are configures as variables.
8. It hardens the security settings for SSHD to only allow known secure cipher suites and MACs.
9. It forces root logins over SSH to use key-based auth.
10. It disables TCP timestamps.
11. Finally, it reboots the host to apply the changes and latest kernel.

#### GitLab
The GitLab role installs a GitLab server. It is designed to be used with an external SMTP relay.

#### LAMP
The LAMP play installs the Apache, MySQL, and PHP roles and then reboots the host.

#### LEMP
The LEMP play installs the NGINX web server, MySQL, and PHP roles and then reboots the host.

#### MySQL
The MySQL role installs MariaDB/MySQL and completes mysql_secure_installation.

#### Nextcloud
The Nextcloud role installs Nextcloud with Apache 2, PHP 7.0, and MariaDB/MySQL. It sets up self-signed HTTPS certs by default.
A Nextcloud instance installed with this play returns a 0/10 on OpenVAS.
DB name is "nextcloud". DB user is "nextcloud"
To remove the memcache warning on the Nextcloud Admin page, just add the line `'memcache.local' => '\OC\Memcache\APCu',` to `/var/www/html/config/config.php`.

#### NGINX
The NGINX web server role installs an NGINX web server with self-signed HTTPS and a strict TLS configuration.

#### PHP
The PHP role installs PHP 7.

#### Reboot
The reboot role reboots the host and, by default, waits up to 60 seconds for it to come back online, checking every 15 seconds. These values are relatively short, and geared towards virtual machines. For physical hosts, higher values are recommended.

#### Register Spacewalk
The register Spacewalk role installs the required pacakges and registers a host with the designated Spacewalk server. For CentOS hosts only.

#### SMB Mount
The SMB mount role sets up an AutoFS mount of an SMB share based on the variables provided.

#### Unregister Spacewalk
The unregister Spacewalk role removes the Spacewalk packages, with the exception of m2crypto and epel-release, and unregisters the host from Spacewalk. For CentOS hosts only.

#### Update
The update play is self explanatory. It autoremoves unneeded dependencies by default.

#### VirtIO Prep
The VirtIO prep role prepares a virtual machine for migration from VMWare to oVirt. It activates any necessary drivers in the kernel, removes VMWare tools, installs and activates the oVirt guest agent, and shuts the host down to be migrated.

#### WordPress
The WordPress role installs WordPress with Apache 2, PHP 7.0, and MariaDB/MySQL. It sets up self-signed HTTPS certs.
A WordPress instance installed with this play returns a 0/10 on OpenVAS.
DB name is "wordpress". DB user is "wordpress"
