# IPAddress

`Xmf\IPAddress` is an IP address object. To the extent possible, all methods are IP version agnostic -- the
method will perform the same function for either a IPv4 or IPv6 address.

### new IPAddress(*$ip*)

Creates a new IPAddress object using the specified string as the IP address. The address may be any valid
presentation form for IPv4 or IPv6 addresses.

### IPAddress::fromRequest()

Use the IP address specified in the server request data to instantiate a IPAddress object.

### asReadable()

Returns the presentation (human readable) form of address. The address will be returned in canonical textual
representation -- dotted quad for IPv4, and [RFC5952](http://tools.ietf.org/html/rfc5952) for IPv6.

If the IP address provided at instantiation was invalid, **false** will be returned.

### asBinary()

Returns the IP address as a binary string (network form.) The returned string is 4 bytes in length for IPv4
addresses, and 16 bytes long for IPv6.

If the IP address provided at instantiation was invalid, **false** will be returned.

### ipVersion()

Return the version of the IP address as a integer, either 4 or 6.

If the IP address provided at instantiation was invalid, **false** will be returned.

### sameSubnet(*$matchIp*, *$netMask4*, *$netMask6*)
Returns as a boolean the answer to this question,
"Is this IP address in the same subnet as address supplied in $matchIp?"

The subnet masks are the number of bits of the address to be considered as the subnet. For IPv4, this can
be an integer from 0 to 32, and for IPv6 the range is 0 to 128.

The method takes separate net masks for both [IPv4](https://en.wikipedia.org/wiki/IPv4_subnetting_reference)
and [IPv6](https://en.wikipedia.org/wiki/IPv6_subnetting_reference) and will select the appropriate one to
allow checking a policy against request input with minimal method calls.

In addition to a differing subnet, a *false* return can indicate that the IP addresses being compared are
different versions or that one or both of the addresses are invalid.

NB - Subnet matching has been used historically to verify that a consistent IP address was associated with
each transaction for a session. As the Internet has evolved, this type of technique becomes less and less
useful, and can be quite unfriendly to visitors.  Developments such as the proliferation of mobile devices,
NAT and Proxy networks, and privacy techniques such as TOR, all make it very likely to see large changes in
the reported client IP address from a single user session in a short amount of time. Use with caution for
well defined purposes.
