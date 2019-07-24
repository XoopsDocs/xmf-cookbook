# Uuid

`Xmf\Uuid` can be used to generate UUIDs \(Universally Unique IDentifiers\)

A [UUID](https://en.wikipedia.org/wiki/Universally_unique_identifier) is a 128-bit number that serves as a unique identifier.

## Uuid::generate\(\)

Returns a version 4 \(random\) UUID

## Uuid::packAsBinary\($uuid\)

Returns a packed version of the supplied UUID. The return is a 16 byte binary string, a compact form that may be more suitable for database storage. 

## Uuid::unpackBinary\($packedUuid\)

Returns a full human readable UUID from the supplied packed form 16 byte binary string.