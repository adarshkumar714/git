# Mongodb

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
### C - Create
* ``` db.[collection name].insertOne({}) ```
* ``` db.[collection name].insertMany([{},{},{}]) ```

### U - Update

### R - Read
* ``` db.[collection name].find() ``` : fetch all docs in collections in a db
* ``` db.[collection name].find({ [selector] }) ``` : fetch all docs matching the keyword used in selector
  * selector is a key-value pair that exist in any doc that you want to find
  * ex. : ``` db.sde.find({"department":"development"}) ```
  * this will select all the SDE present in development department

### D - Delete
