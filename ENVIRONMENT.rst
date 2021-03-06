Environment Configuration Settings
==================================

- **ETCD_HOST**: the DNS A record pointing to Etcd hosts.
- **ETCD_DISCOVERY_DOMAIN**: the DNS SRV record pointing to Etcd hosts.
- **PGHOME**: filesystem path where to put PostgreSQL home directory (/home/postgres by default)
- **APIPORT**: TCP port to Patroni API connections (8008 by default)
- **BACKUP_SCHEDULE**: cron schedule for doing backups via WAL-E (if WAL-E is enabled, '00 01 * * *' by default)
- **CRONTAB**: anything that you want to run periodically as a cron job (empty by default)
- **PGROOT**: a directory where we put the pgdata (by default /home/postgres/pgroot). One may adjust it to point to the mount point of the persistent volume, such as EBS.
- **WALE_TMPDIR**: directory to store WAL-E temporary files. PGROOT/../tmp by default, make sure it has a few GBs of free space.
- **PGDATA**: location of PostgreSQL data directory, by default PGROOT/pgdata.
- **PGPASSWORD_STANDBY**: a password for the replication user, 'standby' by default.
- **PGPASSWORD_SUPERUSER**: a password for the superuser, 'zalando' by default
- **PGPORT**: port PostgreSQL listens to for client connections, 5432 by default
- **SCOPE**: cluster name, multiple Spilos belonging to the same cluster must have identical scope.
- **SSL_CERTIFICATE_FILE**: path to the SSL certificate file inside the container (by default PGHOME/server.crt), Spilo will generate one if not present.
- **SSL_PRIVATE_KEY_FILE**: path to the SSL private key within the container (by default PGHOME/server.key), Spilo will generate one if not present
- **WALE_BACKUP_THRESHOLD_MEGABYTES**: maximum size of the WAL segments accumulated after the base backup to consider WAL-E restore instead of pg_basebackup.
- **WALE_BACKUP_THRESHOLD_PERCENTAGE**: maximum ratio (in percents) of the accumulated WAL files to the base backup to consider WAL-E restore instead of pg_basebackup.
- **WALE_ENV_DIR**: directory where to store WAL-E environment variables
- **WAL_S3_BUCKET**: path to the S3 bucket used for WAL-E base backups (i.e. s3://foobar). Spilo will add /spilo/scope/wal to that path.
- **WAL_GCS_BUCKET**: ditto for the Google Cloud Storage (WAL-E supports both S3 and GCS).
- **USE_WALE**: whether to consider base backup/restore with WAL-E.
- **GOOGLE_APPLICATION_CREDENTIALS**: credentials for WAL-E when running in Google Cloud.
- **CALLBACK_SCRIPT**: the callback script to run on various cluster actions (on start, on stop, on restart, on role change). The script will receive the cluster name, connection string and the current action. See `Patroni <http://patroni.readthedocs.io/en/latest/SETTINGS.html?highlight=callback#postgresql>`__ documentation for details.
