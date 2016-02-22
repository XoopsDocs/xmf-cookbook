## Changing Table Data

### delete(*$table*, *$criteria*)
Create DELETE statement and add to queue. Criteria specified in *$criteria* can be a CriteriaElement object,
or a string to use in the where clause.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### insert(*$table*, *$columns*)
Adds an INSERT SQL statement for the table named *$table* to the work queue. The data to insert is
supplied in *$columns* as an array. Each element in the array is in the form `array('column' => 'value')`.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### update(*$table*, *$columns*, *$criteria*)
Adds an UPDATE SQL statement for the table named *$table* to the work queue. The data to updated is
supplied in *$columns* as an array. Each element in the array is in the form `array('column' => 'value')`.
Criteria specified in *$criteria* to limit which rows are updated can be a CriteriaElement object,
or a string to use in the where clause.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

### truncate(*$table*)
Add statement to empty the table named *$table* to the work queue.

Returns *true* on success, or *false* on error. Additional information may be available using getLastError()
and getLastErrNo().

