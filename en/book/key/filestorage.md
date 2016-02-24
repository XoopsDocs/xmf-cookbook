## FileStorage

The `Xmf\Key\FileStorage` class implements [Xmf\Key\StorageInterface](storageinterface.md) using files
in *XOOPS_VAR_PATH/data/* directory to persist keys.

### save(*$name*, *$data*)

Save key data *$data* under the name *$name*.

Returns true if successful, otherwise false.

### fetch(*$name*)

Fetch key data stored under the name *$name*.

Returns the stored key data if successful, otherwise false.

### exists(*$name*)

Check for the existence of a key under the name *$name*.

Returns true if a key named *$name* exists, otherwise false.

### delete(*$name*)

Delete a any key stored under the name  *$name*.

Returns true if successful, otherwise false.

