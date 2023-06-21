# Mongodb

* Starting Mongodb server
```sh
./mongod --dbpath [folder path where db will be saved]
```
use this commands in the directory where mongod is present.

## Mongosh commands
* show dbs
* use [db name]
* show collections ( used after selecting a db )


## CURD Operations
### C - Create
* db.[collection name].insertOne({})
* db.[collection name].insertMany([{},{},{}])

### U - Update

### R - Read
* db.[collection name].find() : fetch all docs in collections in a db
* db.[collection name].find({ [selector] }) : fetch all docs matching the keyword used in selector

### D - Delete
