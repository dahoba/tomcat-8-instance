# Tomcat 8.0.x instance

## Configuration

Edit `tomcat-instance-common-config` to specify JAVA_HOME and CATALINA_HOME (the Apache Tomcat distribution folder)

i.e.:

```sh
export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_77.jdk/Contents/Home
export JRE_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_77.jdk/Contents/Home
export CATALINA_HOME=$HOME/apps/apache-tomcat-8.0.44
```

Java options can put in `startup.sh`

```sh
export JAVA_OPTS="-noverify -server -Xms128m -Xmx1G -XX:MaxPermSize=256m"
```

## Change Tomcat listener ports

If you want to start an instance of Tomcat in the same machine just copy this folder
 to another folder and change its port. 

Open file `conf/server.xml` find these port then change it to another port. 

i.e.: 8080 -> 8090

```xml
...
<Server port="8005" shutdown="SHUTDOWN">
...
```

```xml
...
 <Connector port="8080" protocol="HTTP/1.1" ... />
 ...
```

```xml
...
<Connector port="8009" protocol="AJP/1.3" .. />
...
```



## Running

At the Terminal app

Before execute them, change the permission of these `.sh` files by execute command

```sh
$ chmod +x *.sh
```

To start:

 `tomcat-8-instance$ ./startup.sh`

To stop:

`tomcat-8-instance$ ./shutdown.sh`

Watch Tomcat console logs:

`tomcat-8-instance$ tail -200f logs/catalina.out`

