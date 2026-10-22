# Backupctl

This repository contains the `backupctl` CLI tool that is used to backup up database dumps and files.

## Requirements

Some packages are required, to allow `backupctl` to communicate with the S3 storage.

```bash
apt install -y yq restic
```

## Configuration

The configuration file `/etc/backupctl/backupctl.yml` is used to apply the entire `backupctl` configuration.
You can find an example configuration below.

```yml
profiles:
  file_test:
    # Type 'dir' uses 'path' to specify the target. 'container' is optional.
    type: dir
    path: /opt/otobo/otobo-docker

  postgres_test:
    # Type 'postgres' uses 'database' to specify the target database name. 'container' is optional if DB is inside docker.
    type: postgres
    container: otobo-web-1
    database: otobo

  mariadb_test:
    # Type 'mariadb' uses 'database' to specitfy the target database name. 'container' is optional if DB is inside docker.
    type: mariadb
    database: otobo

credentials:
  encryption_secret: Test123
  # These credentials need to be configured on the S3 storage
  s3_username: testuser
  s3_password: MySecurePW!
```
