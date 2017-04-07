FROM ubuntu

MAINTAINER y0hny

WORKDIR /opt
RUN apt update && apt -y upgrade && apt -y install openjdk-8-jdk openjdk-8-jre wget python3

RUN  wget --quiet https://www.apache.org/dist/spark/spark-2.1.0/spark-2.1.0-bin-hadoop2.7.tgz \
     && wget --quiet http://tux.rainside.sk/apache/hadoop/common/hadoop-2.7.3/hadoop-2.7.3.tar.gz \
     && tar xfz spark-2.1.0-bin-hadoop2.7.tgz \
     && ln -s /opt/spark-2.1.0-bin-hadoop2.7 /opt/spark \
     && tar xfz hadoop-2.7.3.tar.gz \ 
     && ln -s /opt/hadoop-2.7.3 /opt/hadoop

ENV SPARK_HOME /opt/spark
ENV SPARK_NO_DAEMONIZE true
ENV JAVA_HOME /usr
ENV HADOOP_INSTALL /opt/hadoop
ENV HADOOP_OPTS "-Djava.library.path=$HADOOP_INSTALL/lib/native"
ENV LD_LIBRARY_PATH=/opt/hadoop/lib/native

EXPOSE 8080 7077
CMD /opt/spark/sbin/start-master.sh
