## Tables

`Xmf\Database\Tables` is a class to simplify creating and modifying database tables. When a module is first
installed, there is an automatic mechanism to create the module related tables. For migrations, changes to
the schema after installations, there has been no standard solution.

This class is used to build and execute a work queue of [DDL](https://en.wikipedia.org/wiki/Data_definition_language) 
statements to modify database tables. The current schema is loaded for each referenced table, and creation 
of the work queue considers that current state while determining the work to be done (i.e. it will not attempt 
a CREATE of an existing table.)

## Getting Started

### $migrate = new Tables()

There are no arguments used to instantiate this class.

### $migrate->addTable(string *$table* )
Load schema for a table from database, or starts new empty schema if table does not exist

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### $migrate->useTable(string *$table* )

Like addTable() but only succeeds if the table already exists.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

## Working with Columns 

### $migrate->addColumn(string *$table*, string *$column*, array *$attributes*)

Add to the work queue instruction needed to add a column, named *$column*, with specified *$attributes* to *$table*.

The attributes as specified as a string, i.e. "VARCHAR(32) NOT NULL DEFAULT ''".

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### $migrate->alterColumn(string *$table*, string *$column*, array $attributes, string $newName = '', mixed $position = null )

Add to the work queue instruction needed to alter an existing column, named *$column*, on *$table* with 
specified *$attributes*.

The attributes as specified as a string, i.e. "VARCHAR(32) NOT NULL DEFAULT ''".

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### $migrate->getColumnAttributes(string *$table*, string *$column* )

Get the current attributes an existing column, named *$column*, on *$table*. 

Returns an attribute string on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### $migrate->dropColumn(string *$table*, string *$column* )

Add to the work queue instruction needed to drop an existing column, named *$column*, on *$table*.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

## Working with Indexes

### $migrate->getTableIndexes(string *$table* )
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

### $migrate->addPrimaryKey(string *$table*, string *$column* )

Queue instruction needed to add new primary key definition (*$column*) for *$table* to the work queue.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### createIndex(string *$name*, string *$table*, string *$column*, boolean *$unique* = false )

Queue instruction needed to create a new index named *$name* to *$table* with definition *$column* to the work queue.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### $migrate->dropIndex(string *$name*, string *$table*)

Queue instruction needed to drop the index named *$name* on *$table* to the work queue.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### $migrate->dropIndexes(string *$table* )

Add drop index for all (non-PRIMARY) keys for a *$table* to the work queue. This can be used to clean up indexes 
with automaticly generated names.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### $migrate->dropPrimaryKey(string *$table* )

Queue instruction needed to drop the primary key definition on *$table* to the work queue.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

## Table Operations

### $migrate->copyTable(string *$table*, string $newTable, boolean $withData = false )

Loads schema for *$table* from database, and adds *$newTable* with that same schema to the queue.

If *$withData* is true, the table will be copied with data, otherwise only the structure will be copied.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### $migrate->dropTable(string *$table* )

Queue instruction needed to drop *$table* to the work queue.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### $migrate->renameTable(string *$table*, string $newName )

Queue instruction needed to rename *$table* to *$newName* to the work queue.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### $migrate->setTableOptions(string *$table*, array $options )

Queue instruction needed to alter *$table* with *$options* to the work queue.

An example of *$options* is `array("ENGINE=MyISAM", "DEFAULT CHARSET=utf8")`.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

## Changing Table Data

### $migrate->delete(string *$table*, mixed *$criteria* )
Create DELETE statement and add to queue. Criteria can be a CriteriaElement object, or a string to use
in the where clause.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### $migrate->insert(string *$table*, array *$columns*)
Create an INSERT SQL statement and add to queue. The data to insert is supplied in *$columns* as an array.
Each element in the array is in the form `array('column' => 'value')`.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### $migrate->update(string *$table*, array *$columns*, mixed $criteria )
Creates and executes an UPDATE SQL statement. The data to updated is supplied in *$columns* as an array.
Each element in the array is in the form `array('column' => 'value')`. The *$criteria* to limit which
rows are updated can be a CriteriaElement object, or a string to use in the where clause.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### $migrate->truncate(string *$table*)
Add statement to empty *$table* to the queue

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

public string|null	
### $migrate->renderTableCreate(string *$table*, boolean *$prefixed* = false)
return SQL to create the table
Returns SQL to create the *$table* as a string on success, or *false* on error. Additional information 
may be available using getLastError() and getLastErrNo().

## Interacting with the Work Queue

### $migrate->queueExecute( boolean $force = false )
Execute the work queue

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### $migrate->queueReset( )
Clear the work queue

## Error Information

public string	
### $migrate->getLastError()
Return message from last error encountered

public integer	
### $migrate->getLastErrNo()
Return code from last error encountered

## Debugging methods

These methods expose internal data and may be useful in debugging. However, the internal mechanisms they expose
**will** change over time. Do not depend on these methods in your finished module.

### $migrate->dumpTables( )

Development function that returns the raw tables array

### $migrate->dumpQueue( )

Development only function the returns the raw work queue
