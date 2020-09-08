# Computer Networking: A Top Down Approach

## Chapter 2

### 2.5 DNS

#### 2.5.2 Overview of How DNS Works

- clients host needs to translate hostname to IP address

- invoke client side of DNS (on Linux machines most likely
  `gethostbyname()`

- DNS in user's host sends a query message into the network.

- delay

- DNS in user's host receives a DNS reply message with mapping. 

> All DNS query and reply messages sent on UDP datagrams to port 53. 

From a user's machine DNS is a black box, while on the network, DNS is
large and complex, with many servers and querying host communicating. This
is to counteract the design flaws of a simple system:

- A **single point of failure** could cripple the entire internet.

- **Traffic Volume** would be huge if a single server handled all DNS
  queries.

- **Distant Centralized database** would be the case as a single server
  could not be close to all possible clients, possibly leading to
significant delays.

- **Maintenance** A Single server would have to keep records for all
  hosts, which would be huge and have to be updated very frequently.

##### A Distributed, Hierarchical Database

DNS uses a large number of servers to deal with scale. No single server
has all mappings. Classes of DNS servers:

- **Root DNS servers**. 13 of these labled A through M. Each of these
  servers is actually a network of replicated servers.

- **top-level domain(TLD) DNS servers** Resposible for top-level domains
  like com, net, org, edu, gov, and country top-level domains such as uk,
fr, ca, jp.

- **authoritative DNS servers** The servers that contain the publicly
  avaliable DNS records for accessible hosts. The organization can either
host this themselves or pay for another entity to host it. Most
universities and large companies host their own primary and backup
authoritative servers. 

The approximate sequence when a client host requests an ip:

- client contacts root server

- root server returns IP addresses fro TLD servers for the top level
  domain `.com`

- client contacts an individual TLD server

- TLD server returns the IP of the authoritative server

- client contacts the authoritative server

- authoritative server returns the ip address associated with the
  hostname.

Another type is the **local DNS server**. Each ISP has a local DNS server.
When a host connects, the ISP provides the IP of the local DNS server,
usually via DHCP. The local DNS server acts as a proxy, forwarding
requests to DNS server heirarchy. There also can be varying intermediate
DNS servers. 

##### DNS Caching

Used extensively to improve delay performance and reduce number of DNS
messages. When a DNS server receives a reply, it saves the mapping to its
local memory, allowing for an immeadiate return of the correct mapping if
a different(or even the same) host requests it later. Local DNS servers
can also cache the ip of TLD servers, thus allowing them to skip sending
a query to root DNS servers.
