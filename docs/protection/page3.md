# Version control

**Keeping your software up to date is important because software updates improve existing features, patch security flaws, add new security features and fix bugs. Using outdated software can lead to security vulnerabilities, which cybercriminals and hackers can exploit to gain unauthorized access to your accounts, data and device.**

You can download the needed upgrade packages from the website: https://www.espocrm.com/download/upgrades/ or just click on a hyperlink in Select Upgrade Package section in EspoCRM. Before upgrading it’s better to make the backup of EspoCRM files and data, just to be sure that they will be saved if something goes wrong. (To find out more information on creating a Backup, see [here](https://docs.espocrm.com/administration/backup-and-restore/)).

 
![image](https://github.com/user-attachments/assets/381ee860-55d2-4bfc-bd69-0df73138a8d7)


If you’ve downloaded the upgrade package, the last thing to do is upload and install it into a system. Go to Administration > Upgrade > click Choose File to select the package and press Upload button and wait until all the upgrades will be installed.


![image](https://github.com/user-attachments/assets/c940f82c-9032-4b7a-a714-ea59eb45d3fa)


 
You can also check whether you have the latest version at Menu > About.
 

![image](https://github.com/user-attachments/assets/f9d77525-f57f-42ca-85c8-e0e614bcdf62)


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
