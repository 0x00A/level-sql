
Given the following key/values
```
key1  { a: 0, b: 1 }
key2  { a: 2, b: 3 } 
```

And some boilerplate
```js
var level = require('level');
var sql = require('level-sql');

var db = level('./db', { valueEncoding: 'json' });
sql(db);
```

### Select Any
Given a table T, the query `SELECT * FROM T` will result in all the elements of all the rows of the table being shown.
```js
var stream1 = db.query('SELECT * from table1');
```

```json
{ "key": "key1", "value": { "a": 0, "b": 1 } }
{ "key": "key2", "value": { "a": 2, "b": 3 } }
```

### Select Specific
With the same table, the query `SELECT K FROM T` will result in the elements from the key `K` of all the rows of the table being shown.

```js
var stream1 = db.query('SELECT a from table1');
```

```
{ "key": "key1", "value": { "a": 0 } }
{ "key": "key2", "value": { "a": 2 } }
```
