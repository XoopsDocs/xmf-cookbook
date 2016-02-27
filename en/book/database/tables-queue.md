## Interacting with the Work Queue

### queueExecute(*$force*)

Executes the current work queue. If *$force* is specified as *true*, the changes specified in the queue
will be processed even if the current request should be considered
[idempotent](https://en.wikipedia.org/wiki/Idempotence#Computer_science_meaning) or safe,
such as a HTTP 'GET'.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### queueReset()
Clears the work queue without processing.
