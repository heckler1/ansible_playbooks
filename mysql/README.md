All scripts will run on CentOS 7 or Ubuntu 16.04. They require the sudo password to be set. This can be done at runtime with -K, or by setting the variable "ansible_become_pass".

The MySQL script installs MariaDB/MySQL and completes mysql_secure_installation. All variables are defined in mysql_vars.yml