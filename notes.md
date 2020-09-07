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


