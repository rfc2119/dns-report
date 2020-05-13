The design goals of the DNS influence its structure.  They are:

   - The primary goal is a consistent name space which will be used
     for referring to resources.  In order to avoid the problems
     caused by ad hoc encodings, names should not be required to
     contain network identifiers, addresses, routes, or similar
     information as part of the name.
   - The sheer size of the database and frequency of updates
     suggest that it must be maintained in a distributed manner,
     with local caching to improve performance.  Approaches that attempt to collect a consistent copy of the entire database
     will become more and more expensive and difficult, and hence
     should be avoided.  The same principle holds for the structure
     of the name space, and in particular mechanisms for creating
     and deleting names; these should also be distributed.
   - Where there tradeoffs between the cost of acquiring data, the
     speed of updates, and the accuracy of caches, the source of
     the data should control the tradeoff.
   - The costs of implementing such a facility dictate that it be
     generally useful, and not restricted to a single application.
     We should be able to use names to retrieve host addresses,
     mailbox data, and other as yet undetermined information.  All
     data associated with a name is tagged with a type, and queries
     can be limited to a single type.
   - Because we want the name space to be useful in dissimilar
     networks and applications, we provide the ability to use the
     same name space with different protocol families or
     management.  For example, host address formats differ between
     protocols, though all protocols have the notion of address.
     The DNS tags all data with a class as well as the type, so
     that we can allow parallel use of different formats for data
     of type address.
   - We want name server transactions to be independent of the
     communications system that carries them.  Some systems may
     wish to use datagrams for queries and responses, and only
     establish virtual circuits for transactions that need the
     reliability (e.g., database updates, long transactions); other
     systems will use virtual circuits exclusively.
   - The system should be useful across a wide spectrum of host
     capabilities.  Both personal computers and large timeshared
     hosts should be able to use the system, though perhaps in
     different ways.

## concepts

### anycast routing

### DNS request types

| DNS  Lookup  Type | Description           | Function                                                     |
| ----------------- | --------------------- | ------------------------------------------------------------ |
| **A**             | IPv4 address record   | Returns a 32-bit IPv4 address, which typically maps a domain’s hostname to an IP address |
| **AAAA**          | IPv6 address record   | Returns a 128-bit IP address that maps a domain’s hostname to an IPv6 address |
| **ANY**           | All cached records    | Returns all records of all types known to the name server    |
| **CNAME**         | Canonical name record | Alias of one name to another: the DNS lookup will continue by retrying the lookup with the new name |
| **NS**            | Name server record    | Delegates a DNS zone to use the specified authoritative name servers |
| **PTR**           | Pointer record        | Pointer to a canonical name that returns the name only and is used for implementing reverse DNS lookups |
| **SRV**           | Service locator       | Generalized service location record, used for newer protocols instead of creating protocol-specific records such as MX |

# ref

* [DOMAIN NAMES - CONCEPTS AND FACILITIES](https://tools.ietf.org/html/rfc1034)
* [Common DNS Request Types](https://support.opendns.com/hc/en-us/articles/227986607-Common-DNS-Request-Types) - OpenDNS Knowledge Base
* DNS Server Types - Cloudflare

