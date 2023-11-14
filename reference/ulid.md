# Ulid

`Xmf\Ulid` class provides a unique identifier (ULID) generator for XOOPS modules. 

ULIDs are a type of UUID that are designed to be more ordered and sequential than traditional UUIDs. This makes them well-suited for use in applications where it is important to be able to compare or order identifiers.

## Uuid::generate()	
Generates a new ULID

## Uuid::encodeTime($time)	
Encodes a timestamp into a ULID time component

## Uuid::encodeRandomness()	
Generates random data and encodes it into a ULID randomness component

## Uuid::decode($ulid)	
Decodes a ULID string into a time and randomness component array

## Uuid::decodeTime($ulid)	
Decodes the time component of a ULID string

## Uuid::decodeRandomness($ulid)	
Decodes the randomness component of a ULID string

## Uuid::isValid($ulid)	
Checks if a ULID string is valid

## Uuid::microtimeToUlidTime($microtime)	
Converts a microtime float value to a ULID time integer
