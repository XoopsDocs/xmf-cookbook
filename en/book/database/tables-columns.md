## Working with Columns

### addColumn(*$table*, *$column*, *$attributes*)

Add to the work queue instruction needed to add a column, named *$column*, with specified *$attributes* to *$table*.

The attributes as specified as a string, i.e. "VARCHAR(32) NOT NULL DEFAULT ''".

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### alterColumn(*$table*, *$column*, *$attributes*, *$newName* = '')

Add to the work queue instruction needed to alter an existing column, named *$column*, on *$table* with
specified *$attributes*. If *$newName* is supplied, the column will be renamed as specified in *$newName*.

The attributes as specified as a string, i.e. "VARCHAR(32) NOT NULL DEFAULT ''".

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### getColumnAttributes(*$table*, *$column*)

Get the current attributes an existing column, named *$column*, on *$table*.

Returns an attribute string on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### dropColumn(*$table*, *$column*)

Add to the work queue instruction needed to drop an existing column, named *$column*, on *$table*.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().
