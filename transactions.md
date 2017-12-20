# Interacting with Dragonchain.

Dragonchain, as we mentioned in the introduction, uses web technology at its core. And it was designed/developed by people who built the technology behind some of the highest trafficked websites on the Internet. As a result it uses many of the current web best practices in its design an implementation, which makes it easy for developers to integrate it into their existing services and sites.

The main technologies that we are going to be using in this tutorial are JSON and CURL. This also assumes you have the Docker image of Dragonchain up and running that we talked about in the previous post.

## Getting Started
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
JSON has become a standard tool of the Internet developer. It is an abbreviation for JavaScript Object Notation. It is a simple way to save data in a text file, that can easily be written and read by not only Javascript but just about every programming language on the planet.

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
    "transaction_type": "TT_PROVISION_TSC",
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

If you aren't familiar with JSON, there are two sections to this file. The first is a header, and the second is the payload (aka the information you want Dragonchain to store.

The header structure is described on the Dragonchain github site, [link](https://github.com/dragonchain/dragonchain/blob/master/docs/transactions.md).

We are more concerned about the payload section which holds an array of Transactions, each transaction consists of three key-value pairs, of the sender and their email address, the numberofDragons that your sending and who received the transactions.

So make a copy of the text above, and save it to a file on your computer.

## Curl
Curl is a command line tool for interacting with the Web. It is available on most computers and is installed by default on Macs, Windows and other Unix based computers like Linux.  To get a copy follow this link. [link](https://curl.haxx.se/download.html)

## Posting Transactions
To get started we are going to post the example json posted above, (it was saved with the file name of transaction.json)

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
(note the string after the transaction_id will be different every time you post).

## Querying A Transaction
Dragonchain in its default configuration from the Docker image posts L1 transactions in 5 seconds. After waiting a few moments lets use curl to query the transaction we just posted.

We are going to use the transaction_id that we received when we posted a transaction in the previous section.

We are also going to use a tool called jq that is a command line tool for querying and manipulating json from the command line. Jq is a highly recommended tool for any web programmers arsenal. In this particular case we are going to use it to "pretty-print" the output from the curl command so it is more human readable. To install jq on your computer go to the following [link](https://stedolan.github.io/jq/download/)
```
curl http://localhost:80/transaction/?transaction_id=8e903340-0a8f-4abe-a24d-87a84271e1f4 | jq '.'
```
Which should return something like this.
```
[
  {
    "header": {
      "status": "new",
      "family_of_business": "Test Business Family",
      "block_id": null,
      "line_of_business": "My Business",
      "entity": "c78f4526-8683-11e6-b1c6-3c970e3bee11",
      "create_ts": 1475180987,
      "owner": "Test Node",
      "creator_id": null,
      "actor": "",
      "transaction_type": "TT_PROVISION_TSC",
      "business_unit": "a3e13076-8683-11e6-97a9-3c970e3bee11",
      "transaction_id": "ff7a1cbd-b2db-4491-9e6b-3dd4d240291e",
      "transaction_ts": 1511734999
    },
    "payload": {
      "Transactions": [
        {
          "numberOfDragons": "10",
          "sender": "john@example.org",
          "receiver": "mike@example.org"
        },
        {
          "numberOfDragons": "100",
          "sender": "bob@example.org",
          "receiver": "john@example.org"
        },
        {
          "numberOfDragons": "5",
          "sender": "fred@example.org",
          "receiver": "john@example.org"
        }
      ]
    },
    "signature": {
      "stripped_hash": "6dee1fb8a3315652d115f82ae31ce6d0320025d4ac60e52666c342827d903288bb54958b1b419517a1b6fcf523278053f9adc5538c8407411821caac92e9d294",
      "hash": "6c320711de9fa84e2a746b5c23a73cbdba0839363e4af892895272647c87f894d9074b8194c7eb45d67d0861d99a2f18551c736a8de4c324142c211e9d722e8a",
      "public_key": "-----BEGIN PUBLIC KEY-----\nMFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAEIIAanocnQbJuDLuNPD09VXUQAei/\nBLlLBHz6WTNcP71MJDYuVz9CHGk6mC46I0slk4ktkTpZ8WlRueavVbktcg==\n-----END PUBLIC KEY-----\n",
      "signature_ts": 1511734999,
      "signatory": "transaction-service",
      "signature": "P8Md/HhYTjgJIhcsI1w+XvDprXQjyV19mh2Fqmrk4T7f67DzsgYSDK4DK1tMAvVH1RUUKXUcBhLP\nrC0bTDHTJg==\n"
    }
  }
]
```

If you don't have the transaction_id you can query on any of the other header fields as well. The block_id, transaction_type, create_ts, transaction_ts, business_unit, family_of_business, line_of_business, status, actor, entity, and owner are all query-able fields.

For example, if you wanted to see all of the transactions created by our owner "Test Node" you would use the following curl command.
```
curl http://localhost:80/transaction/?owner=`Test Node` | jq '.'
```

Likewise if you wanted all of the transactions done by your business. 
```
curl http://localhost:80/transaction/?line_of_business=`My Business` | jq '.'
```
