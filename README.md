# postgres-backup-restore

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



