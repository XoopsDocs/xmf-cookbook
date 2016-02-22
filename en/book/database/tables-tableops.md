## Table Operations

### copyTable(*$table*, *$newTable*, *$withData* = false)

Loads schema for a table named *$table* from database, and adds a new table named *$newTable* with that
same schema to the queue.

If *$withData* is specified as true, the table will be copied with data, otherwise only the structure
will be duplicated.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### dropTable(*$table*)

Queue instruction needed to drop the table named *$table* to the work queue.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### renameTable(*$table*, *$newName*)

Queue instruction needed to rename a table named *$table* to *$newName* to the work queue.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### setTableOptions(*$table*, array *$options*)

Queue instruction needed to alter the table named *$table* with attributes specified in the array *$options*
to the work queue.

An example of *$options* is `array("ENGINE=MyISAM", "DEFAULT CHARSET=utf8")`.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().
