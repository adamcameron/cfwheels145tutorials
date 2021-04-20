# Docker environment for CFWheels tutorials

This is a quick repo to strum up minimum containers for working through the https://guides.cfwheels.org/v1.4/docs/beginner-tutorial-hello-world tutorials. It's not very flashy.

Note: most of the _code_ is from the CFWheels download
at https://guides.cfwheels.org/page/download. It's not my code, and I am not claiming it is. 
Obviously CFWheels licensing applies to all that stuff.

My stuff here is just the stuff around Docker (that `/docker` directory).


## Installation

```
cd /var/www
git clone git@github.com:adamcameron/cfwheels145tutorials.git
cd cfwheels145tutorials/docker
DATABASE_ROOT_PASSWORD=123 MYSQL_PASSWORD=1234 LUCEE_PASSWORD=12345 docker-compose up --build --detach --force-recreate
```

Make sure to add `hosts` entries thus on your host PC:

```
127.0.0.1 cfwheels145tutorials.frontend
127.0.0.1 cfwheels145tutorials.lucee
```

## Installation tests

Not implemented yet sorry :-(

## Access

### Site
http://cfwheels145tutorials.frontend/

### Lucee admin
http://cfwheels145tutorials.lucee:8888/lucee/admin.cfm

### Containers

#### Lucee

```
cd /var/www/cfwheels145tutorials/docker
docker exec --interactive --tty cfwheels145tutorials_lucee_1 /bin/bash
curl -I http://localhost:8888/index.cfm
```

```
HTTP/1.1 200
# etc
```

#### Nginx

```
cd /var/www/cfwheels145tutorials/docker
docker exec --interactive --tty cfwheels145tutorials_nginx_1 /bin/ash
curl -I http://localhost/index.cfm
```

```
HTTP/1.1 200
# etc
```

#### MySQL

```
cd /var/www/cfwheels145tutorials/docker
docker exec --interactive --tty cfwheels145tutorials_mysql_1 /bin/bash
mysql --database=cfwheels145tutorials --user=cfwheels145tutorials --password=1234
SELECT @@VERSION; 
```

```
+-----------+
| @@VERSION |
+-----------+
| 8.0.24    |
+-----------+
1 row in set (0.00 sec)
```
