# docker-oracle
docker-oracle


## Run with 1521 port opened:
````
docker run -d -p 1521:1521 wachira90/oracle:xe-11g.11.2.0.2.0
````

## Run this, if you want the database to be connected remotely:
````
docker run -d -p 1521:1521 -e ORACLE_ALLOW_REMOTE=true wachira90/oracle:xe-11g.11.2.0.2.0
````

## For performance concern, you may want to disable the disk asynch IO:
````
docker run -d -p 1521:1521 -e ORACLE_DISABLE_ASYNCH_IO=true wachira90/oracle:xe-11g.11.2.0.2.0
````

##  Enable XDB user with default password: xdb, run this:
````
docker run -d -p 1521:1521 -e ORACLE_ENABLE_XDB=true wachira90/oracle:xe-11g.11.2.0.2.0
````

##  Login `http://localhost:8080/apex/apex_admin` with following credential:
````
username: ADMIN
password: Oracle_11g
````

## connection
````
hostname: localhost
port: 1521
sid: xe
username: system
password: oracle
````

##  login sqlplus
````
sqlplus / AS SYSDBA
````

## login docker with user oracle
````
docker exec -it -u oracle oracle_oracle-db_1 bash
````

## docker-compose.yml
````
version: '3'

services:
  oracle-db:
    image: wachira90/oracle:xe-11g.11.2.0.2.0
    environment:
      - ORACLE_ALLOW_REMOTE=true
      - ORACLE_DISABLE_ASYNCH_IO=true
    ports:
      - 1521:1521
      - 5500:5500
      - 8088:8080
````

## variable
````
ORACLE_ALLOW_REMOTE=true

ORACLE_DISABLE_ASYNCH_IO=true

ORACLE_ENABLE_XDB=true
````
