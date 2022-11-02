# postgres-backup-restore

Ref links

https://medium.com/@mijlalawan/complete-guide-to-backup-and-restore-postgresql-database-e6f7e99d53eb

https://rajanmandanka.medium.com/postgres-backup-and-restore-7d5c5b463fd3

https://www.w3resource.com/PostgreSQL/postgresql-backup-restore.php

https://medium.com/srp-labs/tutorial-3-postgresql-database-setup-backup-and-restore-f633e7a85d02


# Backup the data

Before taking backup check the database size

#### Connect to source postgres server
```
psql -U postgres -h source-postgres-server-url  postgres 
```
### Check the database size
```
\l+
```

### Disconnect the postgres server
```
exit

or 

\q

```

### Backup the postgres data to sql file

```
pg_dump -x --no-owner -U postgres -h source-postgres-server-url  databasename > backup.sql
```

### Backup the postgres data to dump file

```
pg_dump -x -Fc -U postgres -h source-postgres-server-url  databasename > db.dump
```

# Restore the data

#### Connect to destination postgres server

```
psql -U postgres -h destination-postgres-server-url  postgres 
```

### Delete database if already exist

```
drop database databasename;
```

### Create database

```
create database databasename;
```
### Disconnect the postgres server
```
exit

or 

\q

```

### Restore the data using psql

```
psql -h destination-postgres-server-url -U postgres  -d databasename < backup.sql
```

### Restore the data using pg_restore
```
pg_restore -h destination-postgres-server-url -U postgres -C -d databasename db.dump
```

#### Connect to destination postgres server

```
psql -U postgres -h destination-postgres-server-url  postgres 
```
### Check the database size
```
\l+
```

### Disconnect the postgres server
```
exit

or 

\q

```



# Without password prompt

Ref link

https://stackoverflow.com/questions/2893954/how-to-pass-in-password-to-pg-dump

```
pg_dump postgresql://username:password@127.0.0.1:5432/mydatabase  > mydatabase.sql
```

