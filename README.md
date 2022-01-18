# MariaDB-replication-docker-stack
Mariadb automated master-master, master-slave docker compose replication


[![GitHub license](https://img.shields.io/github/license/hosein-yousefii/Mariadb-replication-docker-stack)](https://github.com/hosein-yousefii/Mariadb-replication-docker-stack/blob/master/LICENSE)
![LinkedIn](https://shields.io/badge/style-hoseinyousefii-black?logo=linkedin&label=LinkedIn&link=https://www.linkedin.com/in/hoseinyousefi)


Implementing a master-master or master-slave mariadb replication is always a challenge. I Automated this process by using docker containers.

## What is MariaDB?

MariaDB Database Service is a fully managed database service to deploy cloud-native applications.

### What is master-slave replication?

MariaDB replication is the process by which a single data set, stored in a MySQL database, will be live-copied to a second server. This configuration, called “master-slave” replication, is a typical setup.

### What is master-master replication?

MariaDB master-master replication allows data to be copied from either server to the other one. This subtle but important difference allows us to perform mariadb read or writes from either server. This configuration adds redundancy and increases efficiency when dealing with accessing the data.

# Get started with master-slave:

There are several variables which is your replication configuration, and all of them have a default value, so if you don't specify any variable it will work correctly but, it would be a good idea to chnage some of them, for instance your root password or replication user and password. To do that you can export specified below variables:

(For test environment it's not necessary to set any variables, it works with default values.)

```bash
# First DB container name.
export MARIADB_FIRST_DB_NAME='db-master'

# Second DB container name.
export MARIADB_SECOND_DB_NAME='db-slave'

# User on master container for repliation.
export MARIADB_FIRST_REPLICATION_USER='repl'

# Password for replica user on master container.
export MARIADB_FIRST_REPLICATION_PASSWORD='qazwsx'

# Root password for master DB.
export MARIADB_FIRST_ROOT_PASS='qazwsx'

# Root password for slave DB.
export MARIADB_SECOND_ROOT_PASS='qazwsx'

# Master container address (it depends on the container name "MARIADB_FIRST_DB_NAME" and should be same. You can specify IP addr instead "NOT RECOMMENDED").
export MARIADB_FIRST_HOST='db-master'

# Slave container address (it depends on the container name "MARIADB_SECOND_DB_NAME" and should be same. You can specify IP addr instead "NOT RECOMMENDED").
export MARIADB_SECOND_HOST='db-slave'

# Your docker bridge IP addr on host.
export DOCKER0_IP='172.17.0.1'

```

# Get started with master-master:

First of all You should set a variable to benefit from master-master replication "REPLICATION_METHOD=master-master".

```bash
export REPLICATION_METHOD=master-master
```

The default value of "REPLICATION_METHOD" is master-slave.

Like master-slave replication, several variables exist for master-master replication too. all of them have a default value, so if you don't specify any variable it will work correctly but, it would be a good idea to chnage some of them for instance, your root password or replication user and password. To do that you can export specified below variables:

(For test environment it's not necessary to set any variables, it works with default values.)

```bash
# First DB container name.
export MARIADB_FIRST_DB_NAME='db-master1'

# Second DB container name.
export MARIADB_SECOND_DB_NAME='db-master2'

# User on master1 container for repliation.
export MARIADB_FIRST_REPLICATION_USER='repl-master1'

# User on master2 container for repliation.
export MARIADB_SECOND_REPLICATION_USER='repl-master2'

# Password for replica user on master1 container.
export MARIADB_FIRST_REPLICATION_PASSWORD='qazwsx'

# Password for replica user on master2 container.
export MARIADB_SECOND_REPLICATION_PASSWORD='qazwsx'

# Root password for master1 DB.
export MARIADB_FIRST_ROOT_PASS='qazwsx'

# Root password for master2 DB.
export MARIADB_SECOND_ROOT_PASS='qazwsx'

# Master1 container address (it depends on the container name "MARIADB_FIRST_DB_NAME" and should be same. You can specify IP addr instead "NOT RECOMMENDED").
export MARIADB_FIRST_HOST='db-master1'

# Master2 container address (it depends on the container name "MARIADB_SECOND_DB_NAME" and should be same. You can specify IP addr instead "NOT RECOMMENDED").
export MARIADB_SECOND_HOST='db-master2'

# Your docker bridge IP addr on host.
export DOCKER0_IP='172.17.0.1'

```
## Usage:

You can deploy your mariadb replication by just executing these commands:

```bash
export REPLICATION_METHOD=master-master
or 
export REPLICATION_METHOD=master-slave

./mariadb-deployment.sh
```


# How to contribute:

You are able to add other features related to this stack or expand it, it would be great to implement a replication for running instances.
Copyright 2021 Hosein Yousefi <yousefi.hosein.o@gmail.com>

