# Version control

Keeping your software up to date is important because software updates improve existing features, patch security flaws, add new security features and fix bugs. Using outdated software can lead to security vulnerabilities, which cybercriminals and hackers can exploit to gain unauthorized access to your accounts, data and device.

**Before upgrading**

Review release notes and check if anything changed that could potentially cause issues.
Review if there is enough disk space for the upgrade
SSH into VM
Review system information that is shown, or run df -h
Make a backup of the VM
Go to the VM in Azure > Backup + disaster recovery > Backup > Backup now
If an external database is used: make a backup of the database
Go to the database in Azure > Settings > Backup and restore > Backup now
Review if the current PHP version of the system is compatible with the EspoCRM version you're going to upgrade to
In your EspoCRM instance, go to Administration > System requirements > Check your PHP version
Compare to PHP version supported by version you want to upgrade to; the PHP version required by the latest EspoCRM release can be found here
If necessary, upgrade PHP:
SSH into the VM
Run sudo apt-get update && sudo apt-get upgrade
Enable maintenance mode in EspoCRM: Administration > Settings > Maintenance Mode
Disable cron in EspoCRM: Administration > Settings > Disable Cron

**Upgrade**

SSH into the VM
Run sudo /var/www/espocrm/command.sh upgrade

**After upgrading**

Disable maintenance mode in EspoCRM
Enable cron in EspoCRM
Review if everything still works as expected
