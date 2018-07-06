# TableLoad

`Xmf\Database\TableLoad` is a class to simplify loading initial data to a new table. All methods take a table name as an argument, and that table name will automatically be prefixed as appropriate to the XOOPS system.

These methods are intended for use will small sets of data, as all data will be held in memory during processing.

## TableLoad::loadTableFromArray\(_$table_, _$data_\)

Loads a table from an array. Each top level element of the array is a single row. Each row consists of an associative array of _'column' =&gt; 'value'_ pairs for each included column.

Returns the count of rows inserted.

## TableLoad::loadTableFromYamlFile\(_$table_, _$yamlFile_\)

Similar to `TableLoad::loadTableFromArray()`, but reads the array from the specified YAML file.

This method can accept a YAML export from [phpMyAdmin](https://www.phpmyadmin.net/).

Returns the count of rows inserted.

## TableLoad::truncateTable\(_$table_\)

Empties the specified database table.

Returns the number of affected rows.

## TableLoad::countRows\(_$table_, _$criteria_\)

Returns the count of rows in a table matching the optional Criteria \(all rows in the table if not specified.\)

## TableLoad::extractRows\(_$table_, _$criteria_, _$skipColumns_\)

Returns an array of rows from _$table_ matching the optional Criteria \(all rows in the table if not specified.\)

An array of column names that should _not_ be included in the extracted data can be specified in _$skipColumns_. If not specified, all columns will be included.

## TableLoad::saveTableToYamlFile\(_$table_, _$yamlFile_, _$criteria_, _$skipColumns_\)

Extracts table data from _$table_ matching the optional _$criteria_ \(all rows in the table if not specified\) and saves it in the YAML file _$yamlFile_.

An array of column names that should _not_ be included in the extracted data can be specified in _$skipColumns_. If not specified, all columns will be included.

Returns true on success, false on error.

