# Version control

Keeping your software up to date is important because software updates improve existing features, patch security flaws, add new security features and fix bugs. Using outdated software can lead to security vulnerabilities, which cybercriminals and hackers can exploit to gain unauthorized access to your accounts, data and device.

**Before upgrading**

1. Review release notes and check if anything changed that could potentially cause issues.

2. Review if there is enough disk space for the upgrade

- SSH into VM
- Review system information that is shown, or run df -h
  
3. Make a backup of the VM
   
- Go to the VM in Azure > Backup + disaster recovery > Backup > Backup now
  
4. If an external database is used: make a backup of the database
   
- Go to the database in Azure > Settings > Backup and restore > Backup now
  
5. Review if the current PHP version of the system is compatible with the EspoCRM version you're going to upgrade to
   
- In your EspoCRM instance, go to Administration > System requirements > Check your PHP version
  
- Compare to PHP version supported by version you want to upgrade to; the PHP version required by the latest EspoCRM release can be found [here](https://docs.espocrm.com/administration/server-configuration/)
  
- If necessary, upgrade PHP:
  - SSH into the VM
  - Run sudo apt-get update && sudo apt-get upgrade
    
6. Enable maintenance mode in EspoCRM: Administration > Settings > Maintenance Mode
   
7. Disable cron in EspoCRM: Administration > Settings > Disable Cron

**Upgrade**

1. SSH into the VM
   
2. Run sudo /var/www/espocrm/command.sh upgrade

**After upgrading**

- Disable maintenance mode in EspoCRM
- Enable cron in EspoCRM
- Review if everything still works as expected
