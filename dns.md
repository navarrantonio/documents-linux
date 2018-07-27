#### DNS Concept (Domain Name System):

It is a system that associates domain names with ip addresses. It is hierarchical with tree structure.

Its main function is to translate or resolve ip addresses to domain names

#### Process:
When we access a specific site, the traffic begins to originate from your computer, passes through your ISP (Internet provider), and then through a series of intermediate routers, until you reach the web server in question. That is, a user's computer has its DNS client that generates the requests in order to know the IP address that corresponds to the domain that is trying to access, if you type in the browser "google.com", your browser requests the IP to a server. The DNS servers answer these requests and tell the computer the IP of the site, resolving the address.

#### Domain name resolution types

There are three types of queries that a client can make to a DNS server:

Recursive: In recursive queries, they consist of the best answer that the name server can give. The name server queries your local data (including its cache)
looking for the requested data.

Iterative: The iterative queries, or iterative resolution, the server does not have the information in its local data, so it looks for a root server and repeats the same basic process (consult a remote server and follow the next reference) until it obtains the answer to the question.
Reverse Resolution: Reverse resolution is the process of finding out the domain name associated with an IP address (instead of the normal resolution that the ip associated with a domain finds out).

#### Authority areas
They are portions of the rare domain namespace that store the data. Each zone of authority covers at least one domain and possibly its subdomains, if the latter are not delegated to other areas of authority.

#### Types of DNS servers

Primary or master: they save the data of a namespace in their files.

Secondary or slave: obtain the data from the primary servers through a zone transfer.

Local or cache: they do not contain databases for the resolution of names. When a query is made, these in turn consult the corresponding DNS servers, storing the response in their cache to expedite the requests in the future.

Forwarding: They do not have authority over the areas they resolve.
They respond to requests by forwarding them to the servers they have configured, and await their response.

#### Root Server

Root Servers are the main DNS servers around the world, these are responsible for resolving DNS requests for the highest level domains. There are 13 Root Server distributed in several points of the planet, mainly in the United States. These servers are under the domain: root-servers.org. All Root Servers use BIND (Berkeley Internet Name Domain) as a DNS server, except the H, L and K servers they use. Root Distributed Servers use anycast to improve and balance the load, giving a decentralized service.
#### BIND (Berkeley Internet Name Domain)
It is the most commonly used DNS server on the Internet, especially on Unix systems, in which it is a standard.

#### NSD (Name Server Daemon)

It is an open source Domain Name System (DNS) server. It was created as authorized name server (that is, it does not implement the recursive function of caching by design). The intention of this development is to add the variance to the "gene set" of the DNS implementations used by top-level name servers and, therefore, increase the recovery capacity of the DNS in the face of software failures or vulnerabilities.

#### Anycast

It is a form of addressing, routing or routing in which the information is routed or routed to the best destination from the point of view of the topology of the network. In the internet network, an IP address can be announced from several different points. The intermediate routers route the packet to the nearest destination.

#### Top-level domain (TLD)

Refers to the last segment of a domain name, or the part that follows immediately after the "dot" symbol. TLDs are mainly classified into two categories: generic TLDs and country-specific TLDs. Examples of some of the popular TLDs include .com, .org, .net, .gov, .biz and .edu.
