## Interacting with the Work Queue

### executeQueue(*$force*)

Executes the current work queue. If *$force* is specified as *true*, the changes specified in the queue
will be processed even if the current request should be considered
[idempotent](https://en.wikipedia.org/wiki/Idempotence#Computer_science_meaning) or safe,
such as a HTTP 'GET'.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### resetQueue()

Clears the work queue without processing.

### addToQueue(*$sql*)

Adds an SQL/DDL statement to the work queue. This can be useful in special circumstances. 
Be aware that no processing is performed on the SQL -- it is used as supplied. No attempt 
is made to insure portability or compatibility among different database platforms. 
