## Interacting with the Work Queue

### queueExecute(*$force* = false)

Executes the current work queue. If *$force* is specified as *true*, the changes specified in the queue
will be processed even if the current request should be considered
[idempotent](https://en.wikipedia.org/wiki/Idempotence#Computer_science_meaning) or safe,
such as a HTTP 'GET'.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### queueReset()
Clears the work queue without processing.

### renderTableCreate(*$table*, *$prefixed* = false)

Creates the SQL needed to create the table named *$table* and returns that string. If *$prefixed* is
specified as *true*, the table name in the SQL returned will include the system defined prefix.

This method does not directly influence the work queue, but provides access to the modified table
definitions that were created while building the queue. This direct access to the TABLE CREATE DDL
may be useful in some situations.

Returns SQL to create the *$table* as a string on success, or *false* on error. Additional information
may be available using getLastError() and getLastErrNo().

