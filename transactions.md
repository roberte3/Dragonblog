#Interacting with Dragonchain. 

Dragonchain as we mentioned in the introduction, uses web technology at its core. And it was designed/developed by people who built the technology behind some of the highest traffic'ed websites on the internet. As a result it uses many of the current web best practicies in its desgin an implmentation, which makes it easy for developers to integrate it into their existing services and sites. 

The main technologies that we are going to be using in this tutorial are JSON and CURL. This also assumes you have the Docker image of Dragonchain up and running that we talked about in the previous post. 

##Getting Started 
I'm going to assume you are running Dragonchain via the Docker Image in the last chapter. And that your docker_query_svc_1 is running on port 80 on your localhost, and your docker_txn_service_1 is running on port 81 on your localhost.  

You can double check your configuration by running the following command: 
``` 
$ docker ps --format "table {{.Names}}\t{{.Ports}}" 
```
and you should see a result like this: 
```
NAMES                  PORTS
docker_query_svc_1     0.0.0.0:80->80/tcp
docker_txn_service_1   0.0.0.0:81->81/tcp
docker_processor_1     0.0.0.0:8080->8080/tcp
docker_db_1            0.0.0.0:5432->5432/tcp
```
If you do you are all set. 

## JSON 
JSON has become a standard tool of the internet developer. It is an abriviation for JavaScript Object Notation. It is a simple way to save data in a text file, that can easily be written and read by not only Javascript but just about every programming language on the planet. 

For this example, we are going to use a very simple JSON file. 
transaction.json 
````
{
  "header": {
    "create_ts": 1475180987,
    "business_unit": "a3e13076-8683-11e6-97a9-3c970e3bee11",
    "family_of_business": "Test Business Family",
    "line_of_business": "My Business",
    "owner": "Test Node",
    "transaction_type": "LOCATION_RECORD",
    "entity": "c78f4526-8683-11e6-b1c6-3c970e3bee11" 
  },
  "payload": {
"Transactions":[
    { "sender":"john@example.org", "numberOfDragons":"10", "receiver": "mike@example.org"},
    { "sender":"bob@example.org", "numberOfDragons":"100", "receiver": "john@example.org"},
    { "sender":"fred@example.org", "numberOfDragons":"5", "receiver": "john@example.org"}
    ]}
  
}
````

If you aren't familar with JSON, this is an array of Transactions, each transaction consists of three key-value pairs, of the sender and their email address, the numberofDragons that your sending and who received the transactions. 

So make a copy of the text above, and save it to a file on your computer. 

##Curl 
Curl is a command line tool for interacting with the Web. It is avaiable on most computers and is installed by default on Macs, Windows and other Unix based computers like Linux.  To get a copy follow this link. [link](https://curl.haxx.se/download.html)

##Posting Transactions
To get started we are going to post the example json posted above, (it was saved with the file name of example.json)

```
 curl -i -H "Accept: application/json" -H "Content-type: application/json" --data @transaction.json http://localhost:81/transaction
```

If everything completed successfully, you should see something like this message on your terminal. 

```
HTTP/1.1 201 Created
Date: Sat, 25 Nov 2017 02:14:38 GMT
Content-Length: 58
Content-Type: application/json
Server: TornadoServer/4.2.1

{"transaction_id": "045dec8f-6e8a-4183-bc77-3287e1dca6e3"
```
(note the string after the transaction_id will be different everytime you post). 

##
