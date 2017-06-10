All plays will run on CentOS 7 or Ubuntu 16.04. They require the sudo password to be set. This can be done at runtime with -K, or by setting the variable "ansible_become_pass".

The Nextcloud role installs Nextcloud with Apache 2, PHP 7.0, and MariaDB/MySQL. It sets up self-signed HTTPS certs.
A Nextcloud instance installed with this play returns a 0/10 on OpenVAS.

DB name is "nextcloud". DB user is "nextcloud"

To remove the memcache warning on the Nextcloud Admin page, just add the line "'memcache.local' => '\OC\Memcache\APCu'," to /var/www/html/config/config.php.

