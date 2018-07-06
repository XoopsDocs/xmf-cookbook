# Changing Table Data

## delete\(_$table_, _$criteria_\)

Create DELETE statement and add to queue. Criteria specified in _$criteria_ can be a CriteriaElement object, or a string to use as the where clause.

Returns _true_ on success, or _false_ on error. Additional information may be available using getLastError\(\) and getLastErrNo\(\).

## insert\(_$table_, _$columns_, _$quoteValue_\)

Adds an INSERT SQL statement for the table named _$table_ to the work queue. The data to insert is supplied in _$columns_ as an array. Each element in the array is in the form `array('column' => 'value')`.

By default, the value portion of the supplied _$columns_ entries is quoted in the resulting SQL. To supply your own quoting, supply _false_ for _$quoteValue_. This is especially useful if you are using expressions in the values.

Returns _true_ on success, or _false_ on error. Additional information may be available using getLastError\(\) and getLastErrNo\(\).

## update\(_$table_, _$columns_, _$criteria_, _$quoteValue_\)

Adds an UPDATE SQL statement for the table named _$table_ to the work queue. The data to updated is supplied in _$columns_ as an array. Each element in the array is in the form `array('column' => 'value')`. Criteria specified in _$criteria_ to limit which rows are updated can be a CriteriaElement object, or a string to use as the where clause.

By default, the value portion of the supplied _$columns_ entries is quoted in the resulting SQL. To supply your own quoting, supply _false_ for _$quoteValue_. This is especially useful if you are using expressions in the values.

Returns _true_ on success, or _false_ on error. Additional information may be available using getLastError\(\) and getLastErrNo\(\).

## truncate\(_$table_\)

Add statement to empty the table named _$table_ to the work queue.

Returns _true_ on success, or _false_ on error. Additional information may be available using getLastError\(\) and getLastErrNo\(\).

