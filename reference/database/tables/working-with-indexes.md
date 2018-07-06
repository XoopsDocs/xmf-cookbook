# Working with Indexes

## getTableIndexes\(_$table_\)

Get an array of indexes defined on _$table_

Each array entry is in the form:

```php
    'indexname' => array(
        'columns' => 'column1, column2',
        'unique' => false
    )
```

Returns an array of indexes on success, or _false_ on error. Additional information may be available using getLastError\(\) and getLastErrNo\(\).

## addPrimaryKey\(_$table_, _$column_\)

Queue instruction needed to add new primary key definition \(_$column_\) for _$table_ to the work queue. The _$column_ string may be a single column name or a comma separated list of column names. A [primary key](https://en.wikipedia.org/wiki/Unique_key#Defining_primary_keys_in_SQL) must be unique.

Returns _true_ on success, or _false_ on error. Additional information may be available using getLastError\(\) and getLastErrNo\(\).

## addIndex\(_$name_, _$table_, _$column_, _$unique_\)

Queue instruction needed to create a new index named _$name_ to _$table_ with definition _$column_ to the work queue. The _$column_ string may be a single column name or a comma separated list of column names. If _$unique_ is specified as _true_, the index will be specified as unique.

Returns _true_ on success, or _false_ on error. Additional information may be available using getLastError\(\) and getLastErrNo\(\).

## dropIndex\(_$name_, _$table_\)

Queue instruction needed to drop the index named _$name_ on _$table_ to the work queue.

Returns _true_ on success, or _false_ on error. Additional information may be available using getLastError\(\) and getLastErrNo\(\).

## dropIndexes\(_$table_\)

Add drop index for all \(non-PRIMARY\) keys for a _$table_ to the work queue. This can be used to clean up indexes with automatically generated names.

Returns _true_ on success, or _false_ on error. Additional information may be available using getLastError\(\) and getLastErrNo\(\).

## dropPrimaryKey\(_$table_\)

Queue instruction needed to drop the primary key definition on _$table_ to the work queue.

Returns _true_ on success, or _false_ on error. Additional information may be available using getLastError\(\) and getLastErrNo\(\).

