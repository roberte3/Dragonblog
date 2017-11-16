
#Installing Dragonchain: 

To get started using Dragonchain, we are going use Docker to setup a simple Dragonchain node on Docker. 

If you have Docker already installed on your computer this is going to take only a few minutes to get up and running. If you don't know what Docker is, it is a system that enables you build and run containerized versions of applications. Basically all of the "stuff" to run an application is inside a couple of files, and those files can run on just about any computer. 

##Installing Docker 
To install Docker go to [Docker.com](www.docker.com) and click "Get Docker" and select the version for the computer that you have and follow the directions on that page.  
Mac Version [Link](https://www.docker.com/docker-mac)
Windows Version [Link](https://www.docker.com/docker-windows)

##Installing Git
To install Git on your computer, go to the following [link](https://git-scm.com/downloads) and download the appropriate client for your machine. 

##Installing Dragonchain via a Docker Image 
The best way to install Dragonchain to Docker is run the following commands from your terminal in the directory you want to have Dragonchain installed. 
````
$ git clone https://github.com/dragonchain/dragonchain.git
$ cd dragonchain/docker 
$ docker-compose build
$ docker-compose up 
````

After a few moments you should see some messages about the query and transaction services being up. 

To verify that everything is up and running correctly run a Docker PS command: 
```
$ docker ps --format "table {{.Names}}\t{{.Ports}}" 

```

You should get a result that looks like this: 
```
NAMES                  PORTS
docker_query_svc_1     0.0.0.0:80->80/tcp
docker_txn_service_1   0.0.0.0:81->81/tcp
docker_processor_1     0.0.0.0:8080->8080/tcp
docker_db_1            0.0.0.0:5432->5432/tcp
```

This shows the Dragonchain Query service is running on port 80 on your local machine. 
The Transaction Service is running on Port 81
The Processor is running on Port 8080
And the Database (Postgres) is running on port 5432



URL with instructions to install minkKube 
https://kubernetes.io/docs/tutorials/stateless-application/hello-minikube/#objectives

