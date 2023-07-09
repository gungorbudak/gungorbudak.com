---
author: Güngör Budak
date: '2018-09-11T11:00:00+03:00'
slug: mongodb-listing-database-collections-tables-with-number-of-records-rows
tags:
- mongo
- mongodb
- nosql
- database
title: MongoDB Listing Database Collections/Tables with Number of Records/Rows
year: '2018'
---

Use following script and command to quickly get the number of records/rows in the collections/tables in a database.

`mongo-ls.js` script:

```javascript
var collections = db.getCollectionNames();
for (var i = 0; i < collections.length; ++i) {
  print(collections[i] + ' - ' + db[collections[i]].count() + ' records');
}
```

So, copy-paste this script in to text file and save as `mongo-ls.js`.

Finally, use the following command to query the database. Make sure you change `HOSTNAME`, `DBNAME`, `USERNAME` and `PASSWORD` with your own.

```bash
mongo --host HOSTNAME -u USERNAME -p PASSWORD DBNAME < /path/to/mongo-ls.js
```

The output should look like this:

```
MongoDB shell version v3.4.15
connecting to: mongodb://HOSTNAME:PORT/DBNAME
MongoDB server version: 3.4.15
exons - 2204650 records
genes - 57820 records
transcripts - 196520 records
```
