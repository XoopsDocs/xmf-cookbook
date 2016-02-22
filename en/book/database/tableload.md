## TableLoad

`Xmf\Database\TableLoad` is a class to simplify loading initial data to a new table. All methods take a table
name as an argument, and that table name will automatically be prefixed as appropriate to the XOOPS system.

### TableLoad::loadTableFromArray(string *$table*, array *$data*)

Loads a table from an array. Each top level element of the array is a single row. Each row consists of an
associative array of *'column' => 'value'* pairs for each included column.

Returns the count of rows inserted.

### TableLoad::loadTableFromYamlFile(string *$table*, string *$yamlFile*)

Similar to `TableLoad::loadTableFromArray()`, but reads the array from the specified YAML file.

This method can accept YAML exported from [phpMyAdmin](https://www.phpmyadmin.net/).

Returns the count of rows inserted.

### TableLoad::truncateTable(string *$table*)

Empties the specified database table

Returns the number of affected rows.

### TableLoad::rowCount(string *$table*, CriteriaElement *$criteria* = null)

Returns the count of rows in a table matching the optional Criteria (all rows in the table if not specified.)
