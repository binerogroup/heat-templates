# [Percona Server for MongoDB 6.0](https://docs.percona.com/percona-server-for-mongodb/6.0/index.html) on Ubuntu 22.04

Creates a replication set with authorization on the desired amount of nodes, optionally with incremental backups stored
on S3. Only odd numbers of nodes are allowed (this ensures that failover works as expected.

Use the connection string given in the output named `rs_conn_string` to connect to the replication set.
A root user is created with a random password (available through the output `mongo_root_password`).

If backups are enabled, they will be managed by
[Percona Backup for MongoDB](https://docs.percona.com/percona-backup-mongodb/index.html)
and stored in an S3 bucket (which you have to create by yourself - see
[our documentation](https://docs.binero.com/storage/object-storage/s3.html)).

Backups are scheduled by crontabs defined in `/etc/cron.d/pbm` on the first
database instance. The default crontabs do the following:
- Base incremental backup at 02:30 CET every Sunday.
- Incremental backups following the last base backup on 02:30 CET every other day.
- After backups are taken, the retention time will be enforced (old backups deleted).
