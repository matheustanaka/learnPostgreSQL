# learnPostgreSQL

Learning more about how to work with database, here I will cover some concepts based on PostgreSQL. 

# Getting Started
```shell
# Still in progress ...
```

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

# Reference
[doc](https://gist.github.com/coproduto/5e8cec614a86f1d5668e5322a8b2e67c)
