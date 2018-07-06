# Table Operations

## renameTable\(_$table_, _$newName_\)

Queue instruction needed to rename a table named _$table_ to _$newName_ to the work queue.

Returns _true_ on success, or _false_ on error. Additional information may be available using getLastError\(\) and getLastErrNo\(\).

## setTableOptions\(_$table_, _$options_\)

Queue instruction needed to alter the table named _$table_ with attributes specified in _$options_ to the work queue.

An example of _$options_ is `"ENGINE=MyISAM DEFAULT CHARSET=utf8")`.

Returns _true_ on success, or _false_ on error. Additional information may be available using getLastError\(\) and getLastErrNo\(\).

## dropTable\(_$table_\)

Queue instruction needed to drop the table named _$table_ to the work queue.

Returns _true_ on success, or _false_ on error. Additional information may be available using getLastError\(\) and getLastErrNo\(\).

## copyTable\(_$table_, _$newTable_, _$withData_\)

Loads schema for a table named _$table_ from database, and adds a new table named _$newTable_ with that same schema to the queue.

If _$withData_ is specified as true, the table will be copied with data, otherwise only the structure will be duplicated.

Returns _true_ on success, or _false_ on error. Additional information may be available using getLastError\(\) and getLastErrNo\(\).

