# wpl-staging


On RedHat:

Install software and set timezone (an example for Prague):

```
yum install puppet
yum install git
yum install wget

gem install librarian-puppet

cd /etc/puppet
librarian-puppet init
wget https://github.com/fhrbek/wpl-staging/raw/master/Puppetfile
librarian-puppet install

puppet apply -e "class {'wpl': backups => true, sendBackups => true, backupEmailFrom => '<from>', backupEmailPassword => '<passwd>', backupEmailRecipient => '<to>', tzRegion => 'Europe', tzLocality => 'Prague'}"
```

Reboot now so that all services apply the time zone change (if changed).
