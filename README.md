# Vagrant Midterm 1 - Provisioning a machine with a Flask service and their connection with a Postgres database

![alt tag](https://github.com/yorjaggy/VagrantParcial1Sisdistri/blob/master/images/1.png)

In this exercise we use vagrant for provide a environment like the showed in the imagen 1: A centos machine with a microframework and a database in postgres. 

The version of vagrant used for this exercise is (1.7.2), the version of centos used was the (6.4) and the host machine was a ubuntu 14.04 with the next specifications. 
- 8GB of RAM 
- Intel Core i7

We implement 2 cookbooks: 
- **flask**: in this cookbook, we install the microframework Flask, we configure the machines to execute a service in the port 5432. This microservice has 3 URL's:
    1. http://192.168.56.101:5000/ -> this url show all the information storage in the table "word" in the postgres database.
    2. http://192.168.56.101:5000/test -> this url add information to the database, in this case added a static text "Mi Primera Palabra".
    3. http://192.168.56.101:5000/parametro -> this url added the text inserted in the url, for example "http://192.168.56.101:5000/hola" added the text "hola" in the database.
    
- **postgres**: in this, we install the postgres database, we configure the schema, the iptables permissions, we indicated which clients are allowed to authenticated to the database and we configure the start of the services.

To run this exercise, clone this repository and realize the "vagrant up" command, remember to use an image of CentOs6.4. If the process end succesfully you will be able to connect via ssh to some of the virtual machines created. In other cases you have to check in your configurations allow you to created this environment.

Video:
https://www.youtube.com/watch?v=7oRs6xQBtwA&feature=youtu.be

developed by:
*yorjaggy
