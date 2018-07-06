# Tables

`Xmf\Database\Tables` is a class to simplify creating and modifying database tables. When a module is first installed, there is an automatic mechanism to create the module related tables. For migrations, changes to the schema after installations, there has been no standard solution.

This class is used to build and execute a work queue of [DDL](https://en.wikipedia.org/wiki/Data_definition_language) statements to modify database tables. The current schema is loaded for each referenced table, and creation of the work queue considers that current state while determining the work to be done \(i.e. it will not attempt a CREATE of an existing table.\)

All methods with create or alter tables, columns, indexes or data require a table that is already established using `addTable()` or `useTable()`.

No alterations are made to the database until the work queue is executed by invoking `executeQueue()`.

* [Getting Started](getting-started.md)
* [Table Operations](table-operations.md)
* [Working with Columns](working-with-columns.md)
* [Working with Indexes](working-with-indexes.md)
* [Changing Table Data](changing-table-data.md)
* [Interacting with the Work Queue](interacting-with-the-work-queue.md)
* [Error Info and Debugging](error-info-and-debugging.md)

