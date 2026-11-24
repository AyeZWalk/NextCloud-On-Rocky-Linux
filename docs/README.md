# Implementation and validation notes

## Deployment

I hosted Nextcloud, Apache, PHP, and MariaDB on a Rocky Linux VM. A separate Windows VM acted as the client. I configured the Apache virtual host, set up a dedicated application database account, and checked access to the directories Nextcloud needed. Separating the client from the server let me verify the deployment from the perspective of someone connecting over the network.

## What I checked

- **Application access** · Opened the dashboard from Windows and confirmed the user menu loaded.
- **File and database behavior** · The original project notes record a successful upload and persistence after a reboot. The surviving captures show the dashboard, administration page, and filesystem configuration.
- **Security posture** · The administration page flagged HTTP during initial validation. The SELinux configuration recorded permissive mode. A hardened deployment would need a trusted HTTPS connection and a repeat of the application checks with SELinux enforcing.

## Follow-up validation

| Area | Suggested evidence |
| --- | --- |
| HTTPS | A trusted certificate from the lab client and a clean HTTPS check in the administration page |
| SELinux | Enforcing status and successful login, upload, and download with the intended policy |
| Persistence | Upload a harmless test file, reboot the application VM, and retrieve the same file |
| Recovery | Restore the database, configuration and file data into an isolated VM, then verify that a test account can retrieve its files |

When collecting new screenshots, capture the application or terminal window with synthetic accounts and neutral hostnames.

- [Nextcloud installation on Linux](https://docs.nextcloud.com/server/stable/admin_manual/installation/source_installation.html)
- [Nextcloud SELinux configuration](https://docs.nextcloud.com/server/stable/admin_manual/installation/selinux_configuration.html)
