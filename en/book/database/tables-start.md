## Getting Started

### $tables = new Tables()

There are no arguments used to instantiate this class.

### addTable(string *$table*)
Load schema for a table from database, or starts new empty schema if table does not exist.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### useTable(string *$table*)

Like addTable() but only succeeds if the table already exists.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().
