## Working with Indexes

### getTableIndexes(*$table*)
Get an array of indexes defined on *$table*

Each array entry is in the form:

```PHP
    'indexname' => array(
        'columns' => 'column1, column2',
        'unique' => false
    )
```

Returns an array of indexes on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### addPrimaryKey(*$table*, *$column*)

Queue instruction needed to add new primary key definition (*$column*) for *$table* to the work queue.
The *$column* string may be a single column name or a comma separated list of column names.
A [primary key](https://en.wikipedia.org/wiki/Unique_key#Defining_primary_keys_in_SQL) must be unique.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### createIndex(*$name*, *$table*, *$column*, *$unique* = false)

Queue instruction needed to create a new index named *$name* to *$table* with definition *$column* to the work queue.
The *$column* string may be a single column name or a comma separated list of column names.
If *$unique* is specified as *true*, the index will be specified as unique.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### dropIndex(*$name*, *$table*)

Queue instruction needed to drop the index named *$name* on *$table* to the work queue.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### dropIndexes(*$table*)

Add drop index for all (non-PRIMARY) keys for a *$table* to the work queue. This can be used to clean up indexes
with automaticly generated names.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### dropPrimaryKey(*$table*)

Queue instruction needed to drop the primary key definition on *$table* to the work queue.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().
