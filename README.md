Spark docker containers
==============

Very simple way how to deploy and tryout Spark 2.1 

Spark master container
--------------

**Image Build**

    cd spark-master
    docker build -t y0hny/spark-master:latest .

**Container run**

    docker run -d --rm -p 8080:8080 --name spark-master -h spark-master y0hny/spark-master

Running worker container
--------------

**Image Build**

    cd spark-worker
    docker build -t y0hny/spark-worker:latest .

**Container run**

    docker run -d --rm --link spark-master --name spark-worker-1 -h spark-worker-1 -p 8081:8081 y0hny/spark-worker   
