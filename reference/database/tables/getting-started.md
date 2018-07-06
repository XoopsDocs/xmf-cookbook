# Getting Started

## $tables = new Tables\(\)

There are no arguments used to instantiate this class.

## addTable\(_$table_\)

Load schema for _$table_ from database, or starts new empty schema if table does not exist.

Returns _true_ on success, or _false_ on error. Additional information may be available using getLastError\(\) and getLastErrNo\(\).

## useTable\(_$table_\)

Like addTable\(\) but only succeeds if the _$table_ already exists.

Returns _true_ on success, or _false_ on error. Additional information may be available using getLastError\(\) and getLastErrNo\(\).

