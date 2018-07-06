# filestorage

The `Xmf\Key\FileStorage` class implements [Xmf\Key\StorageInterface](storageinterface.md) using files in _XOOPS\_VAR\_PATH/data/_ directory to persist keys.

## save\(_$name_, _$data_\)

Save key data _$data_ under the name _$name_.

Returns true if successful, otherwise false.

## fetch\(_$name_\)

Fetch key data stored under the name _$name_.

Returns the stored key data if successful, otherwise false.

## exists\(_$name_\)

Check for the existence of a key under the name _$name_.

Returns true if a key named _$name_ exists, otherwise false.

## delete\(_$name_\)

Delete a any key stored under the name _$name_.

Returns true if successful, otherwise false.

