# Mongodb
* [Mongodb official docs](https://www.mongodb.com/docs/manual/)
* Starting Mongodb server
```sh
./mongod --dbpath [folder path where db will be saved]
```
use this commands in the directory where mongod is present.

## Mongosh commands
* ``` show dbs ```
* ``` use [db name] ```
* ``` show collections ``` : used after selecting a db.


## CURD Operations
* note : in mondosh ``` db ``` refers to the database that you select using ``` use [db name] ``` command.

<hr>

### C - Create
* ``` db.[collection name].insertOne({}) ```
* ``` db.[collection name].insertMany([{},{},{}]) ```
     
<hr>

### U - Update

<hr>

### R - Read
* ``` db.[collection name].find() ``` : fetch all docs in collections in a db
  * output will be an array of json objects ( documents )
* ``` db.[collection name].findOne() ```
* ``` db.[collection name].find({ [selector] }) ``` : fetch all docs matching the keyword used in selector
  * selector is a key-value pair that exist in any doc that you want to find
  * ex. : ``` db.sde.find({"department":"development"}) ```
  * this will select all the SDE present in development department

* #### Operators
  * sample data ( documents )
    ```js
    // document 1
    {
      "_id": {
        "$oid": "64944474a3b36d9fcd6b2b6b"
      },
      "class": "newone",
      "tags": [
        "red",
        "blue"
      ],
      "num":45
    }

    // document 2
    {
      "_id": {
        "$oid": "64944474a3b36d9fcd6b2b6b"
      },
      "class": "newone",
      "tags": [
        "red",
        "green"
      ],
      "num": 96
    }

    // document 3
    {
      "_id": {
        "$oid": "64944474a3b36d9fcd6b2b6b"
      },
      "class": "newone",
      "tags": [
        "yellow",
        "green"
      ],
      "num": 54
    }

    // document 4
    {
      "_id": {
        "$oid": "64944474a3b36d9fcd6b2b6b"
      },
      "class": "newone",
      "tags": [
        "yellow",
        "black"
      ],
      "num": 78
    }
    ```
   * #### ``` $in ``` operator
      ```sh
      # command
      db.mycollection.find( { "tags" : { $in : ["red", "green"] } } )
      ```
      ```js
      // output
      [
        {
          _id: ObjectId("64944474a3b36d9fcd6b2b6b"),
          class: 'newone',
          tags: [ 'red', 'blue' ]
        },
        {
          _id: ObjectId("64944487a3b36d9fcd6b2b6c"),
          class: 'newone',
          tags: [ 'red', 'green' ]
        },
        {
          _id: ObjectId("64944493a3b36d9fcd6b2b6d"),
          class: 'newone',
          tags: [ 'yellow', 'green' ]
        }
      ]
      ```
   * #### ``` $lt ``` operator : less than
      ```sh
      # command
      db.mycoll2.find( {"num": { $lt:60  } } )
      ```
      ```js
      // output
      [
        {
          _id: ObjectId("64944474a3b36d9fcd6b2b6b"),
          class: 'newone',
          tags: [ 'red', 'blue' ],
          num: 45
        },
        {
          _id: ObjectId("64944493a3b36d9fcd6b2b6d"),
          class: 'newone',
          tags: [ 'yellow', 'green' ],
          num: 54
        }
      ]
      ```
   * #### AND operator : less than
      ```sh
      # command
      db.mycollection.find( {"tags":"red", "num": {$lt: 60} } )
      ```
      ```js
      // output
      [
        {
          _id: ObjectId("64944474a3b36d9fcd6b2b6b"),
          class: 'newone',
          tags: [ 'red', 'blue' ],
          num: 45
        }
      ]
      ```
   * #### ``` $or ``` operator : less than
      ```sh
      # command
      db.mycollection.find( { $or : [ {"tags":"red"}, { "num": {$lt:60} } ] } )
      ```
      ```js
      // output
      [
        {
          _id: ObjectId("64944474a3b36d9fcd6b2b6b"),
          class: 'newone',
          tags: [ 'red', 'blue' ],
          num: 45
        },
        {
          _id: ObjectId("64944487a3b36d9fcd6b2b6c"),
          class: 'newone',
          tags: [ 'red', 'green' ],
          num: 96
        },
        {
          _id: ObjectId("64944493a3b36d9fcd6b2b6d"),
          class: 'newone',
          tags: [ 'yellow', 'green' ],
          num: 54
        }
      ]
      ```
* ``` findOne() ``` :
  ```sh
  db.mycoll2.findOne( { $or : [{"tags":"red"}, {"num": {$lt:60} }] } )
  ```
  ```js
  // output - output will be a json object ( document )
  {
    _id: ObjectId("64944474a3b36d9fcd6b2b6b"),
    class: 'newone',
    tags: [ 'red', 'blue' ],
    num: 45
  }
  ```


<hr>

### D - Delete
