## TableLoad

`Xmf\Database\TableLoad` is a class to simplify loading initial data to a new table. All methods take a table
name as an argument, and that table name will automatically be prefixed as appropriate to the XOOPS system.

These methods are intended for use will small sets of data, as all data will be held in memory during processing.

### TableLoad::loadTableFromArray(*$table*, *$data*)

Loads a table from an array. Each top level element of the array is a single row. Each row consists of an
associative array of *'column' => 'value'* pairs for each included column.

Returns the count of rows inserted.

### TableLoad::loadTableFromYamlFile(*$table*, *$yamlFile*)

Similar to `TableLoad::loadTableFromArray()`, but reads the array from the specified YAML file.

This method can accept a YAML export from [phpMyAdmin](https://www.phpmyadmin.net/).

Returns the count of rows inserted.

### TableLoad::truncateTable(*$table*)

Empties the specified database table.

Returns the number of affected rows.

### TableLoad::countRows(*$table*, *$criteria*)

Returns the count of rows in a table matching the optional Criteria (all rows in the table if not specified.)

### TableLoad::extractRows(*$table*, *$criteria*, *$skipColumns*)

Returns an array of rows from *$table* matching the optional Criteria (all rows in the table
if not specified.)

An array of column names that should *not* be included in the extracted data can be specified in
*$skipColumns*. If not specified, all columns will be included.

### TableLoad::saveTableToYamlFile(*$table*, *$yamlFile*, *$criteria*, *$skipColumns*)

Extracts table data from *$table* matching the optional *$criteria* (all rows in the table
if not specified) and saves it in the YAML file *$yamlFile*.

An array of column names that should *not* be included in the extracted data can be specified in
*$skipColumns*. If not specified, all columns will be included.

Returns true on success, false on error.
