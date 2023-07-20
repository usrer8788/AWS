ubuntu@ip-172-31-8-57:~$ wget -qO - https://www.mongodb.org/static/pgp/server-4.4.asc | sudo apt-key add -
OK
ubuntu@ip-172-31-8-57:~$ echo "deb http://repo.mongodb.org/apt/debian buster/mongodb-org/4.4 main" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.4.list
deb http://repo.mongodb.org/apt/debian buster/mongodb-org/4.4 main
ubuntu@ip-172-31-8-57:~$ sudo apt-get update
Ign:1 http://repo.mongodb.org/apt/debian buster/mongodb-org/4.4 InRelease
Hit:2 http://eu-west-2.ec2.archive.ubuntu.com/ubuntu focal InRelease                                                  
Hit:3 http://eu-west-2.ec2.archive.ubuntu.com/ubuntu focal-updates InRelease                                          
Hit:4 http://eu-west-2.ec2.archive.ubuntu.com/ubuntu focal-backports InRelease                   
Hit:5 http://security.ubuntu.com/ubuntu focal-security InRelease                                 
Get:6 http://repo.mongodb.org/apt/debian buster/mongodb-org/4.4 Release [2032 B]
Get:7 http://repo.mongodb.org/apt/debian buster/mongodb-org/4.4 Release.gpg [866 B]
Get:8 http://repo.mongodb.org/apt/debian buster/mongodb-org/4.4/main amd64 Packages [47.8 kB]
Fetched 50.7 kB in 1s (57.1 kB/s)
Reading package lists... Done
ubuntu@ip-172-31-8-57:~$ sudo apt-get install -y mongodb-org
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  mongodb-database-tools mongodb-org-database-tools-extra mongodb-org-mongos mongodb-org-server mongodb-org-shell mongodb-org-tools
The following NEW packages will be installed:
  mongodb-database-tools mongodb-org mongodb-org-database-tools-extra mongodb-org-mongos mongodb-org-server mongodb-org-shell mongodb-org-tools
0 upgraded, 7 newly installed, 0 to remove and 82 not upgraded.
Need to get 101 MB of archives.
After this operation, 203 MB of additional disk space will be used.
Get:1 http://repo.mongodb.org/apt/debian buster/mongodb-org/4.4/main amd64 mongodb-database-tools amd64 100.7.3 [50.8 MB]
Get:2 http://repo.mongodb.org/apt/debian buster/mongodb-org/4.4/main amd64 mongodb-org-shell amd64 4.4.23 [13.4 MB]
Get:3 http://repo.mongodb.org/apt/debian buster/mongodb-org/4.4/main amd64 mongodb-org-server amd64 4.4.23 [20.8 MB]
Get:4 http://repo.mongodb.org/apt/debian buster/mongodb-org/4.4/main amd64 mongodb-org-mongos amd64 4.4.23 [16.1 MB]
Get:5 http://repo.mongodb.org/apt/debian buster/mongodb-org/4.4/main amd64 mongodb-org-database-tools-extra amd64 4.4.23 [7756 B]
Get:6 http://repo.mongodb.org/apt/debian buster/mongodb-org/4.4/main amd64 mongodb-org-tools amd64 4.4.23 [2896 B]
Get:7 http://repo.mongodb.org/apt/debian buster/mongodb-org/4.4/main amd64 mongodb-org amd64 4.4.23 [3524 B]
Fetched 101 MB in 4s (23.7 MB/s)      
Selecting previously unselected package mongodb-database-tools.
(Reading database ... 62466 files and directories currently installed.)
Preparing to unpack .../0-mongodb-database-tools_100.7.3_amd64.deb ...
Unpacking mongodb-database-tools (100.7.3) ...
Selecting previously unselected package mongodb-org-shell.
Preparing to unpack .../1-mongodb-org-shell_4.4.23_amd64.deb ...
Unpacking mongodb-org-shell (4.4.23) ...
Selecting previously unselected package mongodb-org-server.
Preparing to unpack .../2-mongodb-org-server_4.4.23_amd64.deb ...
Unpacking mongodb-org-server (4.4.23) ...
Selecting previously unselected package mongodb-org-mongos.
Preparing to unpack .../3-mongodb-org-mongos_4.4.23_amd64.deb ...
Unpacking mongodb-org-mongos (4.4.23) ...
Selecting previously unselected package mongodb-org-database-tools-extra.
Preparing to unpack .../4-mongodb-org-database-tools-extra_4.4.23_amd64.deb ...
Unpacking mongodb-org-database-tools-extra (4.4.23) ...
Selecting previously unselected package mongodb-org-tools.
Preparing to unpack .../5-mongodb-org-tools_4.4.23_amd64.deb ...
Unpacking mongodb-org-tools (4.4.23) ...
Selecting previously unselected package mongodb-org.
Preparing to unpack .../6-mongodb-org_4.4.23_amd64.deb ...
Unpacking mongodb-org (4.4.23) ...
Setting up mongodb-org-server (4.4.23) ...
Adding system user `mongodb' (UID 114) ...
Adding new user `mongodb' (UID 114) with group `nogroup' ...
Not creating home directory `/home/mongodb'.
Adding group `mongodb' (GID 120) ...
Done.
Adding user `mongodb' to group `mongodb' ...
Adding user mongodb to group mongodb
Done.
Setting up mongodb-org-shell (4.4.23) ...
Setting up mongodb-database-tools (100.7.3) ...
Setting up mongodb-org-mongos (4.4.23) ...
Setting up mongodb-org-database-tools-extra (4.4.23) ...
Setting up mongodb-org-tools (4.4.23) ...
Setting up mongodb-org (4.4.23) ...
Processing triggers for man-db (2.9.1-1) ...
ubuntu@ip-172-31-8-57:~$ sudo systemctl daemon-reload
ubuntu@ip-172-31-8-57:~$ sudo systemctl enable mongod.service
Created symlink /etc/systemd/system/multi-user.target.wants/mongod.service → /lib/systemd/system/mongod.service.
ubuntu@ip-172-31-8-57:~$ sudo systemctl restart mongod.service
ubuntu@ip-172-31-8-57:~$ sudo systemctl --type=service --state=active | grep mongod
  mongod.service                                 loaded active running MongoDB Database Server                                                      
ubuntu@ip-172-31-8-57:~$ wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
OK
ubuntu@ip-172-31-8-57:~$ echo "deb https://artifacts.elastic.co/packages/oss-7.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list
deb https://artifacts.elastic.co/packages/oss-7.x/apt stable main
ubuntu@ip-172-31-8-57:~$ sudo apt update && sudo apt install elasticsearch-oss
Ign:1 http://repo.mongodb.org/apt/debian buster/mongodb-org/4.4 InRelease
Hit:2 http://eu-west-2.ec2.archive.ubuntu.com/ubuntu focal InRelease                                                                                                      
Hit:3 http://eu-west-2.ec2.archive.ubuntu.com/ubuntu focal-updates InRelease                                                                                              
Hit:4 http://eu-west-2.ec2.archive.ubuntu.com/ubuntu focal-backports InRelease                                                                        
Hit:5 http://repo.mongodb.org/apt/debian buster/mongodb-org/4.4 Release                                                
Hit:6 http://security.ubuntu.com/ubuntu focal-security InRelease                                 
Get:8 https://artifacts.elastic.co/packages/oss-7.x/apt stable InRelease [10.4 kB]
Get:9 https://artifacts.elastic.co/packages/oss-7.x/apt stable/main amd64 Packages [87.3 kB]
Fetched 97.7 kB in 3s (29.8 kB/s)  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
82 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  elasticsearch-oss
0 upgraded, 1 newly installed, 0 to remove and 82 not upgraded.
Need to get 231 MB of archives.
After this operation, 420 MB of additional disk space will be used.
Get:1 https://artifacts.elastic.co/packages/oss-7.x/apt stable/main amd64 elasticsearch-oss amd64 7.10.2 [231 MB]
Fetched 231 MB in 15s (14.9 MB/s)                                                                                                                                         
Selecting previously unselected package elasticsearch-oss.
(Reading database ... 62513 files and directories currently installed.)
Preparing to unpack .../elasticsearch-oss_7.10.2_amd64.deb ...
Creating elasticsearch group... OK
Creating elasticsearch user... OK
Unpacking elasticsearch-oss (7.10.2) ...
Setting up elasticsearch-oss (7.10.2) ...
Created elasticsearch keystore in /etc/elasticsearch/elasticsearch.keystore
Processing triggers for systemd (245.4-4ubuntu3.21) ...
ubuntu@ip-172-31-8-57:~$ sudo tee -a /etc/elasticsearch/elasticsearch.yml > /dev/null << EOT
> cluster.name: graylog
> action.auto_create_index: false
> EOT
ubuntu@ip-172-31-8-57:~$ sudo systemctl daemon-reload
ubuntu@ip-172-31-8-57:~$ sudo systemctl enable elasticsearch.service
Synchronizing state of elasticsearch.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable elasticsearch
Created symlink /etc/systemd/system/multi-user.target.wants/elasticsearch.service → /lib/systemd/system/elasticsearch.service.
ubuntu@ip-172-31-8-57:~$ sudo systemctl restart elasticsearch.service

ubuntu@ip-172-31-8-57:~$ sudo systemctl restart elasticsearch.service
ubuntu@ip-172-31-8-57:~$ wget https://packages.graylog2.org/repo/packages/graylog-4.4-repository_latest.deb
--2023-07-18 08:32:43--  https://packages.graylog2.org/repo/packages/graylog-4.4-repository_latest.deb
Resolving packages.graylog2.org (packages.graylog2.org)... 104.21.88.209, 172.67.153.95, 2606:4700:3036::6815:58d1, ...
Connecting to packages.graylog2.org (packages.graylog2.org)|104.21.88.209|:443... connected.
HTTP request sent, awaiting response... 404 Not Found
2023-07-18 08:32:43 ERROR 404: Not Found.

ubuntu@ip-172-31-8-57:~$ sudo dpkg -i graylog-4.4-repository_latest.deb
dpkg: error: cannot access archive 'graylog-4.4-repository_latest.deb': No such file or directory
ubuntu@ip-172-31-8-57:~$ wget https://packages.graylog2.org/repo/packages/graylog-4.3-repository_latest.deb
--2023-07-18 08:33:00--  https://packages.graylog2.org/repo/packages/graylog-4.3-repository_latest.deb
Resolving packages.graylog2.org (packages.graylog2.org)... 172.67.153.95, 104.21.88.209, 2606:4700:3035::ac43:995f, ...
Connecting to packages.graylog2.org (packages.graylog2.org)|172.67.153.95|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://graylog-package-repository.s3.eu-west-1.amazonaws.com/packages/graylog-4.3-repository_latest.deb?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Date=20230718T083300Z&X-Amz-SignedHeaders=host&X-Amz-Expires=599&X-Amz-Credential=AKIAIJSI6MCSPXFVDPIA%2F20230718%2Feu-west-1%2Fs3%2Faws4_request&X-Amz-Signature=ce8994adc0c9cd00c6495d8d3c132a758d2a6a9b72386db4b6bdf615469e7400 [following]
--2023-07-18 08:33:00--  https://graylog-package-repository.s3.eu-west-1.amazonaws.com/packages/graylog-4.3-repository_latest.deb?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Date=20230718T083300Z&X-Amz-SignedHeaders=host&X-Amz-Expires=599&X-Amz-Credential=AKIAIJSI6MCSPXFVDPIA%2F20230718%2Feu-west-1%2Fs3%2Faws4_request&X-Amz-Signature=ce8994adc0c9cd00c6495d8d3c132a758d2a6a9b72386db4b6bdf615469e7400
Resolving graylog-package-repository.s3.eu-west-1.amazonaws.com (graylog-package-repository.s3.eu-west-1.amazonaws.com)... 3.5.71.147, 52.92.1.58, 3.5.70.106, ...
Connecting to graylog-package-repository.s3.eu-west-1.amazonaws.com (graylog-package-repository.s3.eu-west-1.amazonaws.com)|3.5.71.147|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2078 (2.0K) [application/x-debian-package]
Saving to: ‘graylog-4.3-repository_latest.deb’

graylog-4.3-repository_latest.deb          100%[=======================================================================================>]   2.03K  --.-KB/s    in 0s      

2023-07-18 08:33:00 (35.7 MB/s) - ‘graylog-4.3-repository_latest.deb’ saved [2078/2078]

ubuntu@ip-172-31-8-57:~$ sudo dpkg -i graylog-4.4-repository_latest.deb
dpkg: error: cannot access archive 'graylog-4.4-repository_latest.deb': No such file or directory
ubuntu@ip-172-31-8-57:~$ ls
graylog-4.3-repository_latest.deb
ubuntu@ip-172-31-8-57:~$ sudo dpkg -i graylog-4.3-repository_latest.deb
Selecting previously unselected package graylog-4.3-repository.
(Reading database ... 63236 files and directories currently installed.)
Preparing to unpack graylog-4.3-repository_latest.deb ...
Unpacking graylog-4.3-repository (1-6) ...
Setting up graylog-4.3-repository (1-6) ...
ubuntu@ip-172-31-8-57:~$ sudo apt-get update && sudo apt-get install graylog-server  graylog-integrations-plugins
Ign:1 http://repo.mongodb.org/apt/debian buster/mongodb-org/4.4 InRelease
Hit:2 http://security.ubuntu.com/ubuntu focal-security InRelease                                                                             
Hit:3 http://eu-west-2.ec2.archive.ubuntu.com/ubuntu focal InRelease                                                                         
Hit:4 http://eu-west-2.ec2.archive.ubuntu.com/ubuntu focal-updates InRelease                                                                            
Hit:5 http://eu-west-2.ec2.archive.ubuntu.com/ubuntu focal-backports InRelease                                                                          
Hit:6 https://artifacts.elastic.co/packages/oss-7.x/apt stable InRelease                                                                                
Hit:7 http://repo.mongodb.org/apt/debian buster/mongodb-org/4.4 Release                            
Get:8 https://packages.graylog2.org/repo/debian stable InRelease [58.1 kB]              
Get:10 https://packages.graylog2.org/repo/debian stable/4.3 amd64 Packages [23.2 kB]    
Fetched 81.3 kB in 1s (63.1 kB/s)   
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  graylog-integrations-plugins graylog-server
0 upgraded, 2 newly installed, 0 to remove and 82 not upgraded.
Need to get 235 MB of archives.
After this operation, 260 MB of additional disk space will be used.
Get:1 https://packages.graylog2.org/repo/debian stable/4.3 amd64 graylog-server all 4.3.15-1 [205 MB]
Get:2 https://packages.graylog2.org/repo/debian stable/4.3 amd64 graylog-integrations-plugins all 4.3.15-1 [29.3 MB]                                                      
Fetched 235 MB in 8s (29.6 MB/s)                                                                                                                                          
Selecting previously unselected package graylog-server.
(Reading database ... 63240 files and directories currently installed.)
Preparing to unpack .../graylog-server_4.3.15-1_all.deb ...
Unpacking graylog-server (4.3.15-1) ...
Selecting previously unselected package graylog-integrations-plugins.
Preparing to unpack .../graylog-integrations-plugins_4.3.15-1_all.deb ...
Unpacking graylog-integrations-plugins (4.3.15-1) ...
Setting up graylog-server (4.3.15-1) ...
################################################################################
Graylog does NOT start automatically!

Please run the following commands if you want to start Graylog automatically on system boot:

    sudo systemctl enable graylog-server.service

    sudo systemctl start graylog-server.service

################################################################################
Setting up graylog-integrations-plugins (4.3.15-1) ...
Processing triggers for systemd (245.4-4ubuntu3.21) ...
ubuntu@ip-172-31-8-57:~$ sudo nano /etc/graylog/server/server.conf
ubuntu@ip-172-31-8-57:~$ pwgen -N 1 -s 96
EGjg17objnyTMZedynZuFS4qBZ7s5DUOVsLmbUWYAOGRtxi4vdQqeADhf7ccLH2jtj9obfybdRPbQ2WY81sRBILw7rA4Jmp0
ubuntu@ip-172-31-8-57:~$ sudo nano /etc/graylog/server/server.conf
ubuntu@ip-172-31-8-57:~$ echo -n H@vingAGrand0ldT1me468% | shasum -a 256
0c5f5fc24fddba68e7ceb234b85db615519f80178ff5005ef501efd38e81e18c  -
ubuntu@ip-172-31-8-57:~$ sudo nano /etc/graylog/server/server.conf
ubuntu@ip-172-31-8-57:~$ sudo systemctl daemon-reload
ubuntu@ip-172-31-8-57:~$ sudo systemctl enable graylog-server.service
Synchronizing state of graylog-server.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable graylog-server
Created symlink /etc/systemd/system/multi-user.target.wants/graylog-server.service → /lib/systemd/system/graylog-server.service.
ubuntu@ip-172-31-8-57:~$ sudo systemctl start graylog-server.service
ubuntu@ip-172-31-8-57:~$ sudo systemctl --type=service --state=active | grep graylog
  graylog-server.service                         loaded active running Graylog server                                                               
ubuntu@ip-172-31-8-57:~$ sudo nano /etc/graylog/server/server.conf
ubuntu@ip-172-31-8-57:~$ curl 127.0.0.1:9000
<!DOCTYPE html>
<html>
  <head>
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="robots" content="noindex, nofollow">
    <meta charset="UTF-8">
    <title>Graylog Web Interface</title>
    <link rel="shortcut icon" href="/assets/favicon.png">
    
  </head>
  <body>
    <script src="/config.js"></script>
    
    <script src="/assets/vendor.3b152b3d9c1d8273aa7e.js"></script>
    
    <script src="/assets/polyfill.d3520237f6db697cd0c3.js"></script>
    
    <script src="/assets/plugin/org.graylog.plugins.threatintel.ThreatIntelPlugin/plugin.org.graylog.plugins.threatintel.ThreatIntelPlugin.2f75008bc782853b72ac.js"></script>
    
    <script src="/assets/plugin/org.graylog.plugins.collector.CollectorPlugin/plugin.org.graylog.plugins.collector.CollectorPlugin.013f2d634538d30f0d7b.js"></script>
    
    <script src="/assets/plugin/org.graylog.integrations.IntegrationsPlugin/plugin.org.graylog.integrations.IntegrationsPlugin.563e2556d9397590f5bb.js"></script>
    
    <script src="/assets/plugin/org.graylog.aws.AWSPlugin/plugin.org.graylog.aws.AWSPlugin.609043bf60b2725ea154.js"></script>
    
    <script src="/assets/app.ed21d7ca08cddf6cca31.js"></script>
    
  </body>
</html>
ubuntu@ip-172-31-8-57:~$ sudo nano /etc/graylog/server/server.conf
ubuntu@ip-172-31-8-57:~$ curl siem.defencelogic.io
curl: (6) Could not resolve host: siem.defencelogic.io
ubuntu@ip-172-31-8-57:~$ curl siem.lab.defencelogic.io
curl: (7) Failed to connect to siem.lab.defencelogic.io port 80: Connection refused
ubuntu@ip-172-31-8-57:~$ sudo apt update
Hit:1 http://security.ubuntu.com/ubuntu focal-security InRelease
Hit:2 http://eu-west-2.ec2.archive.ubuntu.com/ubuntu focal InRelease                                                                                    
Get:3 http://eu-west-2.ec2.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]                                                                   
Hit:4 https://artifacts.elastic.co/packages/oss-7.x/apt stable InRelease                                                                                
Get:5 http://eu-west-2.ec2.archive.ubuntu.com/ubuntu focal-backports InRelease [108 kB]                                                                 
Ign:6 http://repo.mongodb.org/apt/debian buster/mongodb-org/4.4 InRelease    
Hit:7 http://repo.mongodb.org/apt/debian buster/mongodb-org/4.4 Release      
Hit:8 https://packages.graylog2.org/repo/debian stable InRelease
Fetched 222 kB in 1s (203 kB/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
82 packages can be upgraded. Run 'apt list --upgradable' to see them.
ubuntu@ip-172-31-8-57:~$ sudo apt install python3-certbot
python3-certbot                   python3-certbot-dns-dnsimple      python3-certbot-dns-linode        python3-certbot-dns-sakuracloud
python3-certbot-apache            python3-certbot-dns-gandi         python3-certbot-dns-ovh           python3-certbot-nginx
python3-certbot-dns-cloudflare    python3-certbot-dns-gehirn        python3-certbot-dns-rfc2136       
python3-certbot-dns-digitalocean  python3-certbot-dns-google        python3-certbot-dns-route53       
ubuntu@ip-172-31-8-57:~$ sudo apt install python3-certbot
python3-certbot                   python3-certbot-dns-dnsimple      python3-certbot-dns-linode        python3-certbot-dns-sakuracloud
python3-certbot-apache            python3-certbot-dns-gandi         python3-certbot-dns-ovh           python3-certbot-nginx
python3-certbot-dns-cloudflare    python3-certbot-dns-gehirn        python3-certbot-dns-rfc2136       
python3-certbot-dns-digitalocean  python3-certbot-dns-google        python3-certbot-dns-route53       
ubuntu@ip-172-31-8-57:~$ sudo apt install python3-certbot-nginx 