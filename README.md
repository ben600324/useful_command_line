install apache:
sudo apt-get update sudo apt-get install apache2

How to Find your Server's IP address
ifconfig eth0 | grep inet | awk '{ print $2 }'

sudo gedit /etc/apache2/httpd.conf /*edit httpd.conf

404 Error:
AllowOverride All Allow from all </Directory

Create Virtual Hosts
https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-12-04-lts

install Mysql
sudo apt-get install mysql-server libapache2-mod-auth-mysql php5-mysql sudo mysql_install_db sudo /usr/bin/mysql_secure_installation

Install PHP
sudo apt-get install php5 libapache2-mod-php5 php5-mcrypt apt-cache search php5-

https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu

drush commands
drush variable-set site_name "Change site name" drush pm-list --type=Module drush user-create newuser --mail="person@example.com" --password="letmein" drush user-add-role "power user" 5,user3 --uid=2,3 --name=someguy,somegal --mail=[email protected]

drush dl drupal --drupal-project-rename=example cd example drush site-install standard --db-url='mysql://[db_user]:[db_pass]@localhost/[db_name]' --site-name=Example

User Name: admin Password: PmnQbrYW9d

drush upwd --password="givememypasswordback" "admin"

drush Export/Import database
Export
drush cc drush sql-dump > ~/my-sql-dump-file-name.sql

Import
drush sql-connect

drush sql-drop drush sql-cli < ~/my-sql-dump-file-name.sql

update core
drush pm-update projects drupal-7.x

drush updb /*run update.php

Drush restore by backup and magrit
drush bam-restore db manual "TeachFirst-2015-11-19T16-44-42.mysql.gz"

drush unlink permission denied filesystem.inc
sudo drush @ -------

Git
http://git-scm.com/docs/gittutorial

Git Clone from branch
git clone -b drupal736 http://git.devbox.local/kdskels/DRUPAL7.git ./

git
git add . git commit -m "comment" git push /to master git chechout -b branch-name /create branch in local git push /* to master git push origin branch-name

git pull /* to master git pull origin branch-name /* pull from branch

git checkout branch-name /switch branch

git checkout -b branch-name /* create a branch

git reset --merge /* fix merge issue

rm -f ./.git/index.lock

git rm /path to file name /

git branch -d the_local_branch /* delete branch

git delecte file
git commit -a -m "A file was deleted"

git rm -r --cached some-directory git commit -m 'Remove the now ignored directory "some-directory"' git push origin master

git commit -a -m "A file was deleted"

git push

Git list of commits in the project
git log --pretty=format:"%h - %an, %ar : %s"

Git removes commits when not being pushed
git reset

git clean untracked file
git clean -fd

git discard files
git checkout /profiles/teachfirst/modules/contrib/filename

git diff
git diff profiles/teachfirst/modules/contrib/filename

save username and password
git config credential.helper store git push http://example.com/repo.git Username: Password:

Dealing with non-fast-forward errors
git fetch origin git merge origin YOUR_BRANCH_NAME git pull origin YOUR_BRANCH_NAME

git log --oneline /* 01b9f13

git revert
git checkout 01b9f13 file-name

git commit -m "comment"

git push

git add -A

git commit

git push -u origin master

git ignore file
$ git rm -f db/.sqlite3 $ echo '.sqlite3' >> .gitignore $ git add .gitignore $ git commit -m "ignored sqlite databases"

Git pull aborts itself, local file changes will be overwritten by merge

git add filename git commit //enter your commit message and save git pull

Git CONFLICT (MODIFY/DELETE)

git add and git commit

linux find string in file
sudo find / -type f -exec grep -H 'drupal8' {} \;

contral + c exit

Check database size in phpmyadmin
SELECT table_schema "jeroboams_drupal", SUM( data_length + index_length ) /1024 /1024 "Data Base Size in MB" FROM information_schema.TABLES GROUP BY table_schema LIMIT 0 , 30

PHPUnit Install

https://phpunit.de/getting-started.html

Memcache install
http://andrewdunkle.com/2012/how-to-install-memcached-for-drupal-7.html

vagrant php.ini
sudo nano /etc/php5/apache2/php.ini

vargratn host file
sudo nano /etc/hosts

add sql to mysql
use database

source /var/www/jeroboams/jeroboams_drupal_light.sql

Mysql export to gzip
mysqldump -u {$db_user} -p{$db_pass} {$db_name} | gzip -9 > {$this->remote_tmp_dir}/database.bkup.sql.gz

mysqldump -u root -p database_name | gzip -9 > DATABASE/database.sql.gz

Mysql import from sql
mysql -u root -p testingmaster_vdd < dtatbase.sql

mysql 2006
mysqladmin variables -u user -p

mysql> SET GLOBAL max_allowed_packet=1072731894

wordpress
http://wpgothemes.com/wp-content/uploads/2014/08/Template_Hierarchy.png

Drupal
Drupal go-live checklist

https://microserve.io/blogs/drupal-go-live-checklist-revisited

sudo nano /etc/php5/apache2/conf.d/20-xdebug.ini xdebug.max_nesting_level = 250

Teach First
Find ssh key: /var/aegir/.ssh vim id_rsa.pub

Check all service in ubuntu
sudo service --status-all sudo service mysql status

ubuntu check fold size
du -h foldername/

Search in files in unbuntu
if you want search drupal_add_js and settings do below

grep -R "drupal_add_js" * | grep "settings"

command line check os
uname -a

Check users logged in
w

How to find out CPU utilization in Linux?
top (stop by q)

ubuntu kill user by pid
sudo kill pid

aegir drush change user sudo su aegir
drush @andy.community.dev.teachfirst.org.uk cc all

drush show all sites
drush sa

change drush alias
.drush nano sites name

Aegir deploy to community.dev.teachfirst.org.uk
git push to github
run jenkins build now to generat a version number
go to community.dev.teachfirst.org.uk run Migrate and select a version that was build by jenkins
Deploy the community.dev.teachfirst.org.uk to Acquia
need git clone from Acquia get url to a fold like "acquia" in Aegir
diff the files between "acquia" and "teachfirst" in Aegir and then update fold of "acquia"
git push "acquia" fold changes to acquia server.
Fatal error: Allowed memory size of X bytes exhausted (tried to allocate Y bytes)...
ini_set('memory_limit', '250M'); in settings.php

curl -L https://get.rvm.io | bash -s stable source ~/.rvm/scripts/rvm echo "source ~/.rvm/scripts/rvm" >> ~/.bashrc rvm install 2.1.2 rvm use 2.1.2 --default ruby -v gem install compass

Ubuntu list all users
compgen -g /list group compgen -u /list users

Ubuntu check user in group
getent group groupname

Ubuntu set user sudo
sudo usermod -a -G sudo

Ubuntu change user to root
sudo -i

Ubuntu create ssh key
mkdir ~/.ssh chmod 700 ~/.ssh ssh-keygen -t rsa

Generating public/private rsa key pair. Enter file in which to save the key (/home/b/.ssh/id_rsa): Enter passphrase (empty for no passphrase): Enter same passphrase again: Your identification has been saved in /home/b/.ssh/id_rsa. Your public key has been saved in /home/b/.ssh/id_rsa.pub.

Set up sandbox aegir
Create platforms naming (Names's Sandbox) in platform and then clone from community.dev.teachfirst.org.uk

Information
[‎27/‎11/‎2015 12:01] Jon Moss: Private key is only used on the local system, public key is used on the remote service. So if you wanted to connect from Server A to Server B you would need the private key on Server A and the Public key on Server B [‎27/‎11/‎2015 12:02] Jon Moss: eg PuTTY on windows would have Private Key >>> Aegir server would need public key or Aegir server would have private key >>> Git hub would have public key

Restart Jenkins

sudo /etc/init.d/jenkins restart

Git revert local and remote
Local reset:
git reset --hard fj5789sufj

Remote reset:
git push -f origin fj5789sufj:master

install apache:
sudo apt-get update sudo apt-get install apache2

How to Find your Server's IP address
ifconfig eth0 | grep inet | awk '{ print $2 }'

sudo gedit /etc/apache2/httpd.conf /*edit httpd.conf

404 Error:
AllowOverride All Allow from all </Directory

Create Virtual Hosts
https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-12-04-lts

install Mysql
sudo apt-get install mysql-server libapache2-mod-auth-mysql php5-mysql sudo mysql_install_db sudo /usr/bin/mysql_secure_installation

Install PHP
sudo apt-get install php5 libapache2-mod-php5 php5-mcrypt apt-cache search php5-

https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu

drush commands
drush variable-set site_name "Change site name" drush pm-list --type=Module drush user-create newuser --mail="person@example.com" --password="letmein" drush user-add-role "power user" 5,user3 --uid=2,3 --name=someguy,somegal --mail=[email protected]

drush dl drupal --drupal-project-rename=example cd example drush site-install standard --db-url='mysql://[db_user]:[db_pass]@localhost/[db_name]' --site-name=Example

User Name: admin Password: PmnQbrYW9d

drush upwd --password="givememypasswordback" "admin"

drush Export/Import database
Export
drush cc drush sql-dump > ~/my-sql-dump-file-name.sql

Import
drush sql-connect

drush sql-drop drush sql-cli < ~/my-sql-dump-file-name.sql

update core
drush pm-update projects drupal-7.x

drush updb /*run update.php

Drush restore by backup and magrit
drush bam-restore db manual "TeachFirst-2015-11-19T16-44-42.mysql.gz"

drush unlink permission denied filesystem.inc
sudo drush @ -------

Git
http://git-scm.com/docs/gittutorial

Git Clone from branch
git clone -b drupal736 http://git.devbox.local/kdskels/DRUPAL7.git ./

git
git add . git commit -m "comment" git push /to master git chechout -b branch-name /create branch in local git push /* to master git push origin branch-name

git pull /* to master git pull origin branch-name /* pull from branch

git checkout branch-name /switch branch

git checkout -b branch-name /* create a branch

git reset --merge /* fix merge issue

rm -f ./.git/index.lock

git rm /path to file name /

git branch -d the_local_branch /* delete branch

git delecte file
git commit -a -m "A file was deleted"

git rm -r --cached some-directory git commit -m 'Remove the now ignored directory "some-directory"' git push origin master

git commit -a -m "A file was deleted"

git push

git clean untracked file
git clean -fd

git discard files
git checkout /profiles/teachfirst/modules/contrib/filename

git diff
git diff profiles/teachfirst/modules/contrib/filename

save username and password
git config credential.helper store git push http://example.com/repo.git Username: Password:

Dealing with non-fast-forward errors
git fetch origin git merge origin YOUR_BRANCH_NAME git pull origin YOUR_BRANCH_NAME

git log --oneline /* 01b9f13

git revert
git checkout 01b9f13 file-name

git commit -m "comment"

git push

git add -A

git commit

git push -u origin master

git ignore file
$ git rm -f db/.sqlite3 $ echo '.sqlite3' >> .gitignore $ git add .gitignore $ git commit -m "ignored sqlite databases"

Git pull aborts itself, local file changes will be overwritten by merge

git add filename git commit //enter your commit message and save git pull

Git CONFLICT (MODIFY/DELETE)

git add and git commit

linux find string in file
sudo find / -type f -exec grep -H 'drupal8' {} \;

contral + c exit

Check database size in phpmyadmin
SELECT table_schema "jeroboams_drupal", SUM( data_length + index_length ) /1024 /1024 "Data Base Size in MB" FROM information_schema.TABLES GROUP BY table_schema LIMIT 0 , 30

PHPUnit Install

https://phpunit.de/getting-started.html

Memcache install
http://andrewdunkle.com/2012/how-to-install-memcached-for-drupal-7.html

vagrant php.ini
sudo nano /etc/php5/apache2/php.ini

vargratn host file
sudo nano /etc/hosts

add sql to mysql
use database

source /var/www/jeroboams/jeroboams_drupal_light.sql

Mysql export to gzip
mysqldump -u {$db_user} -p{$db_pass} {$db_name} | gzip -9 > {$this->remote_tmp_dir}/database.bkup.sql.gz

mysqldump -u root -p database_name | gzip -9 > DATABASE/database.sql.gz

Mysql import from sql
mysql -u root -p testingmaster_vdd < dtatbase.sql

mysql 2006
mysqladmin variables -u user -p

mysql> SET GLOBAL max_allowed_packet=1072731894

wordpress
http://wpgothemes.com/wp-content/uploads/2014/08/Template_Hierarchy.png

Drupal
Drupal go-live checklist

https://microserve.io/blogs/drupal-go-live-checklist-revisited

sudo nano /etc/php5/apache2/conf.d/20-xdebug.ini xdebug.max_nesting_level = 250

Teach First
Find ssh key: /var/aegir/.ssh vim id_rsa.pub

Check all service in ubuntu
sudo service --status-all sudo service mysql status

ubuntu check fold size
du -h foldername/

Search in files in unbuntu
if you want search drupal_add_js and settings do below

grep -R "drupal_add_js" * | grep "settings"

command line check os
uname -a

Check users logged in
w

How to find out CPU utilization in Linux?
top (stop by q)

ubuntu kill user by pid
sudo kill pid

aegir drush change user sudo su aegir
drush @andy.community.dev.teachfirst.org.uk cc all

drush show all sites
drush sa

change drush alias
.drush nano sites name

Aegir deploy to community.dev.teachfirst.org.uk
git push to github
run jenkins build now to generat a version number
go to community.dev.teachfirst.org.uk run Migrate and select a version that was build by jenkins
Deploy the community.dev.teachfirst.org.uk to Acquia
need git clone from Acquia get url to a fold like "acquia" in Aegir
diff the files between "acquia" and "teachfirst" in Aegir and then update fold of "acquia"
git push "acquia" fold changes to acquia server.
Fatal error: Allowed memory size of X bytes exhausted (tried to allocate Y bytes)...
ini_set('memory_limit', '250M'); in settings.php

curl -L https://get.rvm.io | bash -s stable source ~/.rvm/scripts/rvm echo "source ~/.rvm/scripts/rvm" >> ~/.bashrc rvm install 2.1.2 rvm use 2.1.2 --default ruby -v gem install compass

Ubuntu list all users
compgen -g /list group compgen -u /list users

Ubuntu check user in group
getent group groupname

Ubuntu set user sudo
sudo usermod -a -G sudo

Ubuntu change user to root
sudo -i

Ubuntu create ssh key
mkdir ~/.ssh chmod 700 ~/.ssh ssh-keygen -t rsa

Generating public/private rsa key pair. Enter file in which to save the key (/home/b/.ssh/id_rsa): Enter passphrase (empty for no passphrase): Enter same passphrase again: Your identification has been saved in /home/b/.ssh/id_rsa. Your public key has been saved in /home/b/.ssh/id_rsa.pub.

Set up sandbox aegir
Create platforms naming (Names's Sandbox) in platform and then clone from community.dev.teachfirst.org.uk

Restart Jenkins

sudo /etc/init.d/jenkins restart

Git revert local and remote
Local reset:
git reset --hard fj5789sufj

Remote reset:
git push -f origin fj5789sufj:master

Clean up Aegir
1.sudo chown -R aegir:aegir "number folder"

2.Delete platforms use Operations

3.Delete each version is status is Enabled

4.Delete folder from Putty sudo rm -r "number folder"

5.Delete content from Aegir


# remvoe each commit from repository

git rebase --onto commit-id^ commit-id

git push origin +master

#Acquia drush 

ssh teachfirst.prod@web-8155.prod.hosting.acquia.com
cd /var/www/html/teachfirst.prod/docroot/sites/community.teachfirst.org.uk
drush rr
drush cc all
drush updb

Fatal error: Allowed memory size of 536870912 bytes exhausted (tried to allocate 72 bytes) in /mnt/www/html/teachfirstdev/docroot/modules/filter/filter.module on line 1520

#Git workflow without losing work
When starting a new ticket make sure you have a clean and up to date site:

is it clean?
git status
if not clean it up!

get the latest changes
git pull

Import and new config from your colleagues
sudo -H -u aegir bash -c 'drush @$USER.dtp.dev.teachfirst.org.uk cim'

NOW START YOUR WORK!

Once you are happy that your work is ready to deploy you should follow the next steps in order:

Export any configuration changes you have made


Create the branch on your local machine and switch in this branch :

$ git checkout -b [name_of_your_new_branch]
Change working branch :

$ git checkout [name_of_your_new_branch]
$ git push origin [name_of_your_new_branch]
When you want to commit something in your branch, be sure to be in your branch.

You can see all branches created by using :

$ git branch
Which will show :

* approval_messages
  master
  master_clean
Add a new remote for your branch :

$ git remote add [name_of_your_remote] 
Push changes from your commit into your branch :

$ git push [name_of_your_new_remote] [name_of_your_branch]
Update your branch when the original branch from official repository has been updated :

$ git fetch [name_of_your_remote]
Then you need to apply to merge changes, if your branch is derivated from develop you need to do :

$ git merge [name_of_your_remote]/develop
Delete a branch on your local filesystem :

$ git branch -d [name_of_your_new_branch]
To force the deletion of local branch on your filesystem :

$ git branch -D [name_of_your_new_branch]
Delete the branch on github :

$ git push origin :[name_of_your_new_branch]

#copy database from live to stage,
reroute,
stage proxy,
shield,
configure reroute to smoral@teachfirst.org.uk
(i have a rule in my mail to delete all those emails)
or your email,
in salesforce change the authorize data

cp /var/aegir/platforms/jon/drupal8/docroot/sites/jon.dtp.dev.teachfirst.org.uk/services.yml /var/aegir/platforms/sofia/drupal8/docroot/sites/sofia.dtp.dev.teachfirst.org.uk/ 
sudo su
----------------
sudo chown aegir:www-data services.yml 



Export:
sudo -H -u aegir bash -c 'drush @jon.dtp.dev.teachfirst.org.uk cex'
Import:
git pull
sudo -H -u aegir bash -c 'drush @$USER.dtp.dev.teachfirst.org.uk cim'


#add ip address to server

#access dev serve via Jon's server
ssh aegir.dev.aog.io -p 32100
ssh aegir.dev.teachfirst.org.uk

sudo iptables -I INPUT 10 -s 94.196.236.101 -j ACCEPT

scp homepage_header_image_-_option_3.jpg teachfirstd8.dev@staging-4778.prod.hosting.acquia.com:/mnt/gfs/teachfirstd8.dev/sites/default/files/2017-09

# acquia prod file path:
/mnt/www/html/teachfirst/docroot/sites/community.teachfirst.org.uk/files/messaging/cache$ 

# D8 migrate

sudo -H -u aegir bash -c 'drush @andy.login.dev.teachfirst.org.uk ms'
sudo -H -u aegir bash -c 'drush @andy.login.dev.teachfirst.org.uk mim salesforce_connect_migration'
sudo -H -u aegir bash -c 'drush @andy.login.dev.teachfirst.org.uk mim salesforce_connect_migration --update'

sudo -H -u aegir bash -c 'drush @andy.login.dev.teachfirst.org.uk migrate-reset-status salesforce_connect_migration'

# ssh to acquia from aegir dev
sudo -H -u aegir bash -c 'drush @teachfirstd8.prod cim'

# acquia ssh 
ssh teachfirstd8.dev@teachfirstd8dev.ssh.prod.acquia-sites.com 


# fixed dtp site 
I think Aegir tried to roll back and lost the database, it happens sometimes, once every few months, due to a bug in drush. I can probably fix it faster than explaining the process but next week I will go through it with you so you know for the future. I will basically create a new site from the backup, manually remove the old site and then clone the new site to the current URL. It should take about 5 to 10 mins. 

Delete the backup of test and copy last known good backup of dtp to the same file name. 
cd /var/aegir/backups 
cp dtp.dev.teachfirst.org.uk-20180213.170539.tar.gz test.dtp.dev.teachfirst.org.uk-20180214.121733.tar.gz 
then restore test.dtp 

# Drush import/export database
export:

drush cr

drush sql-dump > ~/my-sql-dump-file-name.sql

Import:

drush sql-drop

drush sql-cli < ~/my-sql-dump-file-name.sql
 

# degrade database
sudo -H -u aegir bash -c 'drush @connect.dev.teachfirst.org.uk ev "drupal_set_installed_schema_version('system', 8301)"'

# drupal 8 basic http
// return isset($username) && isset($password);
+
+    if (isset($username) && isset($password)) {
+      return (bool) $this->entityManager->getStorage('user')->loadByProperties(['name' => $username, 'status' => 1]);
+    }
+
+    return FALSE;

Final version - deployment to DEV 
(crossed out above in case I missed something)

# For Schools Portal
Copy profile from release branch to Acquia Profiles folder   --
Copy config/schools/sync to config folder  -- 

# For Connect
Copy profile from your branch branch to Acquia Profiles folder --
Copy config/connect/sync to config folder --
If your site needs any libraries that are not currently in Vendors folder you will need to add these using composer after you have replace composer below.
composer require drupal/new_module

# For Charity no further steps are needed - unless there are changes to be deployed
Copy profile from release branch to Acquia Profiles folder --
Copy config/charity/sync to config folder --
 
# Copy composer.json to Acquia Repo from drupal8/coreWithEntity85  /docroot/composer.json --
cp ~/platforms/drupal8/docroot/composer.json ~/platforms/acquiad8/teachfirstd8/docroot/

- This is the new composer that you can add your libraries to if needed.

# Remove vendors and composer.lock
rm -rf ~/platforms/acquiad8/teachfirstd8/docroot/vendors
rm -rf ~/platforms/acquiad8/teachfirstd8/docroot/composer.lock

# Run composer update
cd ~/platforms/acquiad8/teachfirstd8/docroot
composer update --no-dev --with-dependencies

# deploy code to Acquia Dev by pushing changes to master

# Clear caches on each site and run Database Updates 'updb' and Entity update 'entup'
sudo -H -u aegir bash -c 'drush @teachfirstd8.dev cr
sudo -H -u aegir bash -c 'drush @teachfirstd8.dev updb'
sudo -H -u aegir bash -c 'drush @teachfirstd8.dev entup'
sudo -H -u aegir bash -c 'drush @teachfirstd8.dev cr
'
# Import the configuration on each site
sudo -H -u aegir bash -c 'drush @teachfirstd8.dev cim'


# Schools cache clear example
sudo -H -u aegir bash -c 'drush @teachfirstd8.dev --uri=http://dev.schools.teachfirst.org.uk cr'
# Charity config import example
sudo -H -u aegir bash -c 'drush @teachfirstd8.dev cim'

#drupal 8
INSERT INTO andyconnectdevte.user__field_push_password_to_sf (bundle,deleted,entity_id,revision_id,langcode,delta,field_push_password_to_sf_value)
SELECT 'user', '0', uid, uid,'en', '0', pass 
FROM andyconnectdevte.users_field_data where pass != '';

#drupal 7

INSERT INTO teachfirststg.field_data_field_push_password_to_sf (entity_type,bundle,deleted,entity_id,revision_id,language,delta,field_push_password_to_sf_value,field_push_password_to_sf_format)
SELECT 'user','user', '0', uid, uid,'und', '0', pass, NULL
FROM teachfirststg.users where pass != '';

#Git push error: Unable to unlink old (Permission denied)

sudo chmod -R ug+w .;

# compare pack
sudo -H -u aegir bash -c 'drush @connect.dev.teachfirst.org.uk ev "drupal_set_installed_schema_version('file', 8000)"'
xrxb@.com/1555/2


#drupal 7 database update

UPDATE tf_profiles 
LEFT JOIN users ON users.uid = tf_profiles.uid 
SET tf_profiles.password_sync = users.pass 
where users.uid = tf_profiles.uid;
