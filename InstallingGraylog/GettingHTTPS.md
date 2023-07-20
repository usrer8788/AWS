ubuntu@ip-172-31-8-57:~$ sudo apt install nginx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nginx is already the newest version (1.18.0-0ubuntu1.4).
nginx set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 82 not upgraded.
ubuntu@ip-172-31-8-57:~$ cd /etc/nginx
ubuntu@ip-172-31-8-57:/etc/nginx$ ls
conf.d        fastcgi_params  koi-win     modules-available  nginx.conf    scgi_params      sites-enabled  uwsgi_params
fastcgi.conf  koi-utf         mime.types  modules-enabled    proxy_params  sites-available  snippets       win-utf
ubuntu@ip-172-31-8-57:/etc/nginx$ cd sites-available/
ubuntu@ip-172-31-8-57:/etc/nginx/sites-available$ ls
default
ubuntu@ip-172-31-8-57:/etc/nginx/sites-available$ sudo nano graylog-lab.conf
ubuntu@ip-172-31-8-57:/etc/nginx/sites-available$ ls 
default  graylog-lab.conf
ubuntu@ip-172-31-8-57:/etc/nginx/sites-available$ sudo rm default 
ubuntu@ip-172-31-8-57:/etc/nginx/sites-available$ sudo rm /etc/
Display all 195 possibilities? (y or n)
ubuntu@ip-172-31-8-57:/etc/nginx/sites-available$ sudo rm /etc/nginx/
conf.d/            fastcgi_params     koi-win            modules-available/ nginx.conf         scgi_params        sites-enabled/     uwsgi_params
fastcgi.conf       koi-utf            mime.types         modules-enabled/   proxy_params       sites-available/   snippets/          win-utf
ubuntu@ip-172-31-8-57:/etc/nginx/sites-available$ sudo rm /etc/nginx/sites-enabled/default 
ubuntu@ip-172-31-8-57:/etc/nginx/sites-available$ ls
graylog-lab.conf
ubuntu@ip-172-31-8-57:/etc/nginx/sites-available$ sudo ln -s /etc/nginx/sites-available/graylog-lab.conf /etc/nginx/sites-enabled/
ubuntu@ip-172-31-8-57:/etc/nginx/sites-available$ ls /etc/nginx/sites-enabled
graylog-lab.conf
ubuntu@ip-172-31-8-57:/etc/nginx/sites-available$ ls -la /etc/nginx/sites-enabled
total 8
drwxr-xr-x 2 root root 4096 Jul 18 09:01 .
drwxr-xr-x 8 root root 4096 Jul 18 08:48 ..
lrwxrwxrwx 1 root root   43 Jul 18 09:01 graylog-lab.conf -> /etc/nginx/sites-available/graylog-lab.conf
ubuntu@ip-172-31-8-57:/etc/nginx/sites-available$ sudo nginx -t
nginx: [emerg] unknown directive "    listen" in /etc/nginx/sites-enabled/graylog-lab.conf:3
nginx: configuration file /etc/nginx/nginx.conf test failed
ubuntu@ip-172-31-8-57:/etc/nginx/sites-available$ sudo nano graylog-lab.conf
ubuntu@ip-172-31-8-57:/etc/nginx/sites-available$ sudo nano graylog-lab.conf


Use "fg" to return to nano.

[1]+  Stopped                 sudo nano graylog-lab.conf
ubuntu@ip-172-31-8-57:/etc/nginx/sites-available$ sudo nano graylog-lab.conf
ubuntu@ip-172-31-8-57:/etc/nginx/sites-available$ sudo nano graylog-lab.conf
ubuntu@ip-172-31-8-57:/etc/nginx/sites-available$ fg
sudo nano graylog-lab.conf
ubuntu@ip-172-31-8-57:/etc/nginx/sites-available$ sudo nano graylog-lab.conf
ubuntu@ip-172-31-8-57:/etc/nginx/sites-available$ nginx -t
nginx: [alert] could not open error log file: open() "/var/log/nginx/error.log" failed (13: Permission denied)
2023/07/18 09:06:29 [warn] 20745#20745: the "user" directive makes sense only if the master process runs with super-user privileges, ignored in /etc/nginx/nginx.conf:1
2023/07/18 09:06:29 [emerg] 20745#20745: unknown directive "    listen" in /etc/nginx/sites-enabled/graylog-lab.conf:3
nginx: configuration file /etc/nginx/nginx.conf test failed
ubuntu@ip-172-31-8-57:/etc/nginx/sites-available$ cd 
ubuntu@ip-172-31-8-57:~$ sudo nano /etc/nginx/sites-enabled/graylog-lab.conf
ubuntu@ip-172-31-8-57:~$ certbot
The following error was encountered:
[Errno 13] Permission denied: '/var/log/letsencrypt'
Either run as root, or set --config-dir, --work-dir, and --logs-dir to writeable paths.
ubuntu@ip-172-31-8-57:~$ sudo python3
python3             python3-futurize    python3-pasteurize  python3-pbr         python3.8           
ubuntu@ip-172-31-8-57:~$ sudo certbot 
.bash_logout                       .cache/                            .ssh/                              .wget-hsts
.bashrc                            .profile                           .sudo_as_admin_successful          graylog-4.3-repository_latest.deb
ubuntu@ip-172-31-8-57:~$ sudo certbot 
.bash_logout                       .cache/                            .ssh/                              .wget-hsts
.bashrc                            .profile                           .sudo_as_admin_successful          graylog-4.3-repository_latest.deb
ubuntu@ip-172-31-8-57:~$ sudo certbot 
.bash_logout                       .cache/                            .ssh/                              .wget-hsts
.bashrc                            .profile                           .sudo_as_admin_successful          graylog-4.3-repository_latest.deb
ubuntu@ip-172-31-8-57:~$ sudo certbot 
.bash_logout                       .cache/                            .ssh/                              .wget-hsts
.bashrc                            .profile                           .sudo_as_admin_successful          graylog-4.3-repository_latest.deb
ubuntu@ip-172-31-8-57:~$ sudo certbot 
.bash_logout                       .cache/                            .ssh/                              .wget-hsts
.bashrc                            .profile                           .sudo_as_admin_successful          graylog-4.3-repository_latest.deb
ubuntu@ip-172-31-8-57:~$ sudo certbot 
.bash_logout                       .cache/                            .ssh/                              .wget-hsts
.bashrc                            .profile                           .sudo_as_admin_successful          graylog-4.3-repository_latest.deb
ubuntu@ip-172-31-8-57:~$ sudo certbot --help

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

  certbot [SUBCOMMAND] [options] [-d DOMAIN] [-d DOMAIN] ...

Certbot can obtain and install HTTPS/TLS/SSL certificates.  By default,
it will attempt to use a webserver both for obtaining and installing the
certificate. The most common SUBCOMMANDS and flags are:

obtain, install, and renew certificates:
    (default) run   Obtain & install a certificate in your current webserver
    certonly        Obtain or renew a certificate, but do not install it
    renew           Renew all previously obtained certificates that are near
expiry
    enhance         Add security enhancements to your existing configuration
   -d DOMAINS       Comma-separated list of domains to obtain a certificate for

  (the certbot apache plugin is not installed)
  --standalone      Run a standalone webserver for authentication
  --nginx           Use the Nginx plugin for authentication & installation
  --webroot         Place files in a server's webroot folder for authentication
  --manual          Obtain certificates interactively, or using shell script
hooks

   -n               Run non-interactively
  --test-cert       Obtain a test certificate from a staging server
  --dry-run         Test "renew" or "certonly" without saving any certificates
to disk

manage certificates:
    certificates    Display information about certificates you have from Certbot
    revoke          Revoke a certificate (supply --cert-path or --cert-name)
    delete          Delete a certificate

manage your account:
    register        Create an ACME account
    unregister      Deactivate an ACME account
    update_account  Update an ACME account
  --agree-tos       Agree to the ACME server's Subscriber Agreement
   -m EMAIL         Email address for important account notifications

More detailed help:

  -h, --help [TOPIC]    print this message, or detailed help on a topic;
                        the available TOPICS are:

   all, automation, commands, paths, security, testing, or any of the
   subcommands or plugins (certonly, renew, install, register, nginx,
   apache, standalone, webroot, etc.)
  -h all                print a detailed help page including all topics
  --version             print the version number
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
ubuntu@ip-172-31-8-57:~$ sudo certbot -d siem.lab.defencelogic.io --nginx
Saving debug log to /var/log/letsencrypt/letsencrypt.log
Error while running nginx -c /etc/nginx/nginx.conf -t.

nginx: [emerg] unknown directive "    listen" in /etc/nginx/sites-enabled/graylog-lab.conf:3
nginx: configuration file /etc/nginx/nginx.conf test failed

The nginx plugin is not working; there may be problems with your existing configuration.
The error was: MisconfigurationError('Error while running nginx -c /etc/nginx/nginx.conf -t.\n\nnginx: [emerg] unknown directive "\xa0\xa0\xa0\xa0listen" in /etc/nginx/sites-enabled/graylog-lab.conf:3\nnginx: configuration file /etc/nginx/nginx.conf test failed\n')
ubuntu@ip-172-31-8-57:~$ nginx -t
nginx: [alert] could not open error log file: open() "/var/log/nginx/error.log" failed (13: Permission denied)
2023/07/18 09:13:14 [warn] 20796#20796: the "user" directive makes sense only if the master process runs with super-user privileges, ignored in /etc/nginx/nginx.conf:1
2023/07/18 09:13:14 [emerg] 20796#20796: unknown directive "    listen" in /etc/nginx/sites-enabled/graylog-lab.conf:3
nginx: configuration file /etc/nginx/nginx.conf test failed
ubuntu@ip-172-31-8-57:~$ sudo nano /etc/nginx/sites-enabled/graylog-lab.conf
ubuntu@ip-172-31-8-57:~$ sudo nano /etc/nginx/sites-avaiable/graylog-lab.conf
ubuntu@ip-172-31-8-57:~$ sudo nano /etc/nginx/sites-available/graylog-lab.conf
ubuntu@ip-172-31-8-57:~$ sudo nano /etc/nginx/sites-available/graylog-lab.conf
ubuntu@ip-172-31-8-57:~$ nginx -t
nginx: [alert] could not open error log file: open() "/var/log/nginx/error.log" failed (13: Permission denied)
2023/07/18 09:21:13 [warn] 20832#20832: the "user" directive makes sense only if the master process runs with super-user privileges, ignored in /etc/nginx/nginx.conf:1
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
2023/07/18 09:21:13 [emerg] 20832#20832: open() "/run/nginx.pid" failed (13: Permission denied)
nginx: configuration file /etc/nginx/nginx.conf test failed
ubuntu@ip-172-31-8-57:~$ sudo nginx -t
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
ubuntu@ip-172-31-8-57:~$ sudo certbot -d siem.lab.defencelogic.io --nginx
Saving debug log to /var/log/letsencrypt/letsencrypt.log
Plugins selected: Authenticator nginx, Installer nginx
Enter email address (used for urgent renewal and security notices) (Enter 'c' to
cancel): soc@defencelogic.io

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Please read the Terms of Service at
https://letsencrypt.org/documents/LE-SA-v1.3-September-21-2022.pdf. You must
agree in order to register with the ACME server at
https://acme-v02.api.letsencrypt.org/directory
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
(A)gree/(C)ancel: A

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Would you be willing to share your email address with the Electronic Frontier
Foundation, a founding partner of the Let's Encrypt project and the non-profit
organization that develops Certbot? We'd like to send you email about our work
encrypting the web, EFF news, campaigns, and ways to support digital freedom.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
(Y)es/(N)o: Y
Obtaining a new certificate
Performing the following challenges:
http-01 challenge for siem.lab.defencelogic.io
Waiting for verification...
Cleaning up challenges
Deploying Certificate to VirtualHost /etc/nginx/sites-enabled/graylog-lab.conf

Please choose whether or not to redirect HTTP traffic to HTTPS, removing HTTP access.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
1: No redirect - Make no further changes to the webserver configuration.
2: Redirect - Make all requests redirect to secure HTTPS access. Choose this for
new sites, or if you're confident your site works on HTTPS. You can undo this
change by editing your web server's configuration.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Select the appropriate number [1-2] then [enter] (press 'c' to cancel): 2
Redirecting all traffic on port 80 to ssl in /etc/nginx/sites-enabled/graylog-lab.conf

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Congratulations! You have successfully enabled https://siem.lab.defencelogic.io

You should test your configuration at:
https://www.ssllabs.com/ssltest/analyze.html?d=siem.lab.defencelogic.io
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

IMPORTANT NOTES:
 - Congratulations! Your certificate and chain have been saved at:
   /etc/letsencrypt/live/siem.lab.defencelogic.io/fullchain.pem
   Your key file has been saved at:
   /etc/letsencrypt/live/siem.lab.defencelogic.io/privkey.pem
   Your cert will expire on 2023-10-16. To obtain a new or tweaked
   version of this certificate in the future, simply run certbot again
   with the "certonly" option. To non-interactively renew *all* of
   your certificates, run "certbot renew"
 - Your account credentials have been saved in your Certbot
   configuration directory at /etc/letsencrypt. You should make a
   secure backup of this folder now. This configuration directory will
   also contain certificates and private keys obtained by Certbot so
   making regular backups of this folder is ideal.
 - If you like Certbot, please consider supporting our work by:

   Donating to ISRG / Let's Encrypt:   https://letsencrypt.org/donate
   Donating to EFF:                    https://eff.org/donate-le

ubuntu@ip-172-31-8-57:~$ sudo nano /etc/nginx/sites-available/graylog-lab.conf
ubuntu@ip-172-31-8-57:~$ sudo systemctl restart nginx
ubuntu@ip-172-31-8-57:~$ sudo systemctl --type=service --state=active | grep nginx
  nginx.service                                  loaded active running A high performance web server and a reverse proxy server                     
ubuntu@ip-172-31-8-57:~$ 