Mariadb on Ubuntu22 with the option for database dumps and replication

Replication - You get the option to select replication, this will deploy a secondary Mariadb instance that will act as secondary and read from the primary.

Database dump -  This option will dump all your databases daily on the primary instance at 06.25 into folder /home/ubuntu/sql_dump. The dumps get removed after 30 days.
