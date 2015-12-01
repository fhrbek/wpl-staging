# wpl-staging


On RedHat:

Set timezone on an AWS instance (an example for Prague):

```
cd /etc
ln -s ../usr/share/zoneinfo/Europe/Prague localtime 
init 6
```

Install software:

```
yum install puppet
yum install git
git clone https://github.com/fhrbek/wpl.git
cd wpl

puppet module install puppetlabs/java
puppet module install puppetlabs/postgresql
puppet module install puppetlabs/apache
puppet module install puppetlabs/tomcat

puppet apply --modulepath=/root:/etc/puppet/modules -e "class {'wpl': backups => true, sendBackups => true, backupEmailFrom => '<from>', backupEmailPassword => '<passwd>', backupEmailRecipient => '<to>'}"
```
