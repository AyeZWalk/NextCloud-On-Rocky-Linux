# Nextcloud on Rocky Linux
Goal: deploy nextcloud, configure apache/php/mariadb, set permissions, and validate from a windows workstation.

Top outcomes
- login works from browser
- uploads succeed
- database persists across reboots

Environment
- Rocky Linux version
- Apache version, PHP version, MariaDB version
- VM specs

Steps I took
1) set selinux to permissive for install
2) install apache php php-extensions mariadb
3) create db and user with least privilege
4) configure apache vhost and restart
5) run nextcloud web installer
6) set ownership/permissions and confirm

Validation
- screenshots and command outputs

Security notes
- tls, firewall, regular updates, backups

What I’d improve next
- move from permissive to enforcing with proper rules
