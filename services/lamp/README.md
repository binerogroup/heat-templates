This template will leave you with the following,

Right now this can only be deployed in europe-se-1a not europe-se-1b

Webserver with PHP and Apache2 
NFS server with NFS sharing paths with the webservers
DB server with MariaDB
Loadbalancer in Binerocloud that round-robin traffic from port 80 and 443 to the webservers

You need an ssh-key / key pair and a private network on your account to run this template
You can use the Private network template to set up a private network if you haven't created one yet.

The backup option will take backup on NFS and MariaDB volumes, and not on the web volume.
This is because all web instance files will be stored and shared from NFS so they will already be backed up.
