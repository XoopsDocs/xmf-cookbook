# Interacting with the Work Queue

## executeQueue\(_$force_\)

Executes the current work queue. If _$force_ is specified as _true_, the changes specified in the queue will be processed even if the current request should be considered [idempotent](https://en.wikipedia.org/wiki/Idempotence#Computer_science_meaning) or safe, such as a HTTP 'GET'.

Returns _true_ on success, or _false_ on error. Additional information may be available using getLastError\(\) and getLastErrNo\(\).

## resetQueue\(\)

Clears the work queue without processing.

## addToQueue\(_$sql_\)

Adds an SQL/DDL statement to the work queue. This can be useful in special circumstances. Be aware that no processing is performed on the SQL -- it is used as supplied. No attempt is made to insure portability or compatibility among different database platforms.

