### Zabbix 4 installer for CentOS 7
Fully automated bash script for install Zabbix server and agent on the CentOS host.

### Features
* Install Zabbix 4.0
* Install php 7.2
* Configure php.ini
* Configure zabbix config
* Configure SELinux
* Configure Firewalld
* Secure zabbix agent

### Install-zabbix
Script for install fully working Zabbix Server + Zabbix Agent. This script deploy SELinux policy from setemplate/zabbix_server_add.te.

After install script show info:
```bash
Now you can install and configure Zabbix!

Link to Zabbix server - http://<server_IP>/zabbix
DB Password - <zabbix_DBPassword>
Default login - Admin
Default password - zabbix

```

This info also caved to script folder in the zabbix-creds.txt file.

### Install-zabbix-agent-only
Install only Zabbix-agent to endpoint. This script also can secure Zabbix agent with pre-shared key (PSK).

```bash
./install-zabbix-agent-only.sh <server_IP>
```

### Secure-agent-psk
Setup psk on the already installed Zabbix agent, after workingthis script show info:
```bash
PSK - <psk_key>
PSKIdentity - <identity>
```

### Zabbix updater
On source server:
* Stop zabbix service
* Export zabbix database
```
mysqldump -uroot -p<password> --database <Db_name> > <backup_name>.sql
```
* Compress your arhive and put to new installed server

On new installed server:
* Change archive name and slq backup name in the update-zabbix.sh file
* Run update script

## Links
* https://www.zabbix.com/documentation/4.0/manual/installation/install_from_packages/rhel_centos
* https://www.zabbix.com/forum/zabbix-help/22576-copying-duplicating-zabbix-configuration
* https://www.zabbix.com/forum/zabbix-help/50603-export-configuration-to-a-new-installation
* https://zabbix.org/wiki/Docs/howto/upgrade/Upgrade_Zabbix_1.8_to_2.0_and_Migrate_Mysql_to_Postgresql
* http://bertvv.github.io/notes-to-self/2015/11/16/automating-mysql_secure_installation/
* https://www.zabbix.com/documentation/3.0/manual/encryption/using_pre_shared_keys