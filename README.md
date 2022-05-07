# docker-mysql
Docker MySQL

### Make two directories on host machine/server to map the MySQL data and configuration with the Docker container

```
mkdir -p /root/mysql/conf.d && mkdir -p /root/mysql/mysql-data
```

### Now, pull the MySQL image from docker hub and run the container mapped with host on 6603 port

```
docker run \
--detach \
--name=mysql_docker \
--env="MYSQL_ROOT_PASSWORD=Str@ngP#&&W@!D" \
--publish 6603:3306 \
--volume=/root/mysql/conf.d:/etc/mysql/conf.d \
--volume=/root/mysql/mysql-data:/var/lib/mysql \
mysql
```

### Run below command to check MySQL DB from the running container

```
docker exec -it mysql_docker bash

echo $MYSQL_ROOT_PASSWORD

mysql -u root -p

show databases;

use mysql;

exit
```
### Also, we can run sql query directly from the host machine/server, without entering the mysql container

```
mysql -u root -p Str@ngP#&&W@!D -h 127.0.0.1 -P 6603 -e 'show global variables like "max_connections"';
```

