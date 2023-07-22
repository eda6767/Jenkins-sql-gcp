# Jenkins-sql-gcp

<sub> 
In this scenario we are gonna use Jenkins to automatize creating backup of SQL database and copy this file to Cloud Storage on GCP.

</br>
</br>

<img width="657" alt="Zrzut ekranu 2023-07-22 o 16 28 28" src="https://github.com/eda6767/Jenkins-sql-gcp/assets/102791467/2afbd02d-1010-4330-8976-774b8da3d10c">

</br>
A a first step we have to create container with SQL Database. For this purpose let's create the docker-compose file.
</br>


<img width="650" alt="Zrzut ekranu 2023-07-22 o 18 05 07" src="https://github.com/eda6767/Jenkins-sql-gcp/assets/102791467/416959c1-87ff-47d5-ab9c-8c7f67b1689d">

```
docker-compose up -d
docker images
docker ps
docker logs -f db
```

</br>
In our location w folder db_data has been created. Now, let's connest to new container, and then to database

```
docker exec ti- db bash
mysql -u root -p
show databases;
```

</br>
Next step we need to install SQL and GCP clients, so we need to edit Dockerfile
  
</br>

<img width="650" alt="Zrzut ekranu 2023-07-22 o 21 09 21" src="https://github.com/eda6767/Jenkins-sql-gcp/assets/102791467/e298ca17-efc9-4031-86ec-04928d437902">


</br>

```
docker-compose build
docker-compose up -d remote_host 
```

Now:

```
docker exec -ti remote-host bash
mysql
```

Now from remote-host we are gonna conect to mysql container, create database, table and insert some data into the table.

```
mysql -u root -h db_host -p
show databases;
create database testdb;
use testdb;
create table info (name varchar(20), lastname varchar(20), age int(2));
show tables;
desc info;
insert into info values ('tom', 'links', 21);
select * from info;
```

To create backup of database:

```
mysqldump -u root -h db_host -p testdb > /tmp/db.sql
```

Now, let's automate creating of this backup:

```
touch /tmp/script.sh
cd tmp
vi script.sh
```
<img width="637" alt="Zrzut ekranu 2023-07-22 o 22 57 41" src="https://github.com/eda6767/Jenkins-sql-gcp/assets/102791467/181c0fe2-2410-4636-8aa7-01ad6b4a05c1">


```
chmod +x script.sh
./script.sh db_host 1234 testdb
```
