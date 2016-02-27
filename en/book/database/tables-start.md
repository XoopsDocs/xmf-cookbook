## Getting Started

### $tables = new Tables()

There are no arguments used to instantiate this class.

### addTable(*$table*)
Load schema for *$table* from database, or starts new empty schema if table does not exist.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### useTable(*$table*)

Like addTable() but only succeeds if the *$table* already exists.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().
