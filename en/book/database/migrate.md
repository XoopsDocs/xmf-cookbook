# migrate

## Migrate

`Xmf\Database\Migrate` is a class to simplify synchronizing database changes between versions of a module. It builds on the [Tables](tables.md) class, and adds support for building a module schema directly from the database, saving that schema, and generating the DDL to convert the current database for a module into a saved schema definition.

## Basic Usage

### $migrate = new Migrate\(_$dirname_\)

Creates a new Migrate object that considers the tables specified in the module definition for the module identified by _$dirname_.

### synchronizeSchema\(\)

Compare the current database tables to the target schema and execute any DDl/SLQ needed to synchronize the database with the target schema.

The synchronizeSchema\(\) method should normally be called during the modules onUpdate processing. In most cases this should be invoked in the xoops_module\_pre\_update$dirname_ function.

### getSynchronizeDDL\(\)

Gets an array of DDL/SQL statements that when executed sequentially will synchronize the existing database to match the taget schema. This may be useful if extensive changes to a large database need to be run as batches or from the command line.

### preSyncActions\(\)

Simple schema changes, such a changing the length of a VARCHAR column, can be handled automatically. Some changes, such as renaming a table or a column need to be performed explicitly before synchronizing, or data loss will result. \(A renamed entity looks like a dropped entity under the old name and a new entity of the new name.\)

The intended pattern is for a module to extend the Migrate class for use in its own module update process, and perform any needed conversion logic, such a renames in the preSyncActions\(\) method.

## Utility methods

### getCurrentSchema\(\)

Builds a schema representation from the current database that includes all tables declared for the module specified when the object was instantiated.

### getTargetDefinitions\(\)

Loads a saved schema definition corresponding to the current version of the module specified when the object was instantiated.

### saveCurrentSchema\(\)

Saves the schema definition obtained from the current state of the database as the schema target for the current module version.

**This method is intended for use by module developers/publishers.** The format of the saved schema is subject to change. Editing the generated file may cause inconsistencies in the synchronization process. Changes should be made to the current database, and then saveCurrentSchema\(\) invoked to capture any updates.

## Error Information

### getLastError\(\)

Return message from last error encountered

### getLastErrNo\(\)

Return code from last error encountered

