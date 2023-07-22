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
docker ps
docker logs -f db
```
