# learnPostgreSQL

Learning more about how to work with database, here I will cover some concepts based on PostgreSQL. 

# Getting Started
```shell
# Still in progress ...
```
# Whats a database? 
Database is a organized collection of data stored. There so many context about it, but you can image a database like a folder and inside of that there so many tables listed. Here in this project, template0 and template1 are our folders.

# Version
I'm using postgreSQL 14, I really recommend you to use the same version, because I don't know what kind of features change between the other version.
### Docker image
[complete-intro-to-SQL](https://sql.holt.courses/lessons/welcome/docker)
[postgres](https://hub.docker.com/_/postgres/)
### Useful commands
```shell
# After get the docker images, run the command to see if its working
$ docker run -e POSTGRES_PASSWORD=lol --name=pg --rm -d -p 5432:5432 postgres:14

# To execute the postgres inside the container, it should return the postgres cli
docker exec -u postgres -it pg psql
```
### PSQL commands
```shell
# List all databases
$ \l

# Run some bash commands, maybe you want to use a cat to see files or pwd to find the current directory
$ \! pwd 

# Show all the tables and sequences and relations
$ \d

# Connect to a database
\c recipeguru #\c + database name
```

# Reference
[doc](https://gist.github.com/coproduto/5e8cec614a86f1d5668e5322a8b2e67c)
