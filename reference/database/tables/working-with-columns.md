# Working with Columns

## addColumn\(_$table_, _$column_, _$attributes_\)

Add to the work queue instruction needed to add a column, named _$column_, with specified _$attributes_ to _$table_.

The attributes as specified as a string, i.e. "VARCHAR\(32\) NOT NULL DEFAULT ''".

Returns _true_ on success, or _false_ on error. Additional information may be available using getLastError\(\) and getLastErrNo\(\).

## alterColumn\(_$table_, _$column_, _$attributes_, _$newName_\)

Add to the work queue instruction needed to alter an existing column, named _$column_, on _$table_ with specified _$attributes_. If _$newName_ is supplied, the column will be renamed as specified in _$newName_.

The attributes as specified as a string, i.e. "VARCHAR\(32\) NOT NULL DEFAULT ''".

Returns _true_ on success, or _false_ on error. Additional information may be available using getLastError\(\) and getLastErrNo\(\).

## getColumnAttributes\(_$table_, _$column_\)

Get the current attributes an existing column, named _$column_, on _$table_.

Returns an attribute string on success, or _false_ on error. Additional information may be available using getLastError\(\) and getLastErrNo\(\).

## dropColumn\(_$table_, _$column_\)

Add to the work queue instruction needed to drop an existing column, named _$column_, on _$table_.

Returns _true_ on success, or _false_ on error. Additional information may be available using getLastError\(\) and getLastErrNo\(\).

