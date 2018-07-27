# Introduction to Linux Commands / DNS

The commands, for the most part, are really nothing more than small programs built into the operating system. Technically, the only thing that differentiates the commands from the programs (or the scripts) is that the commands are always in very specific folders (/ bin, / usr / bin, and in the case of having logged in as superuser, / sbin) , so it is not necessary to specify where they are.Therefore, all the syntax rules applicable to the commands are applicable to any Bash program or script, with one change: instead of typing the name of the command, you must specify exactly where the program or script is (the program path) or script).

### Types of records:

* A Address record that resolves a name of a host to an IPv4 address.

* AAA Address record that resolves a name of a host to an IPv6 address.

* MX Mail server registry used to define a list of mail servers for a domain, as well as the priority, the one with the lowest number of mail servers is the one with the highest priority.

* PTR Registry of pointers that resolves IPv4 addresses to the host name. That is, it does the opposite of register A. It is used in areas of Reverse Resolution.

* NS Name server registry used to define a list of nameservers with authority for a domain.

* SOA Authority start record that specifies the Master (or Primary) DNS Server that will provide authoritative information about an Internet domain, administrator's email address, domain serial number, and time parameters for the zone.

* SRV Service record that specifies information about services available through the domain.

* CNAME Canonical name record that makes one name alias another.

#### Commands

#### nslookup
is a command-line administrative tool to test and troubleshoot DNS servers (Domain Name Server). It is also used to query records of specific DNS (RR) resources. Most operating systems come with the built-in nslookup function.

* Discover the "A" record (IP address) of the domain
````bash
$ nslookup yahoo.com
Server:		127.0.1.1
Address:	127.0.1.1#53
Non-authoritative answer:
Name:	yahoo.com
Address: 72.30.35.9
Name:	yahoo.com
Address: 98.137.246.7
Name:	yahoo.com
Address: 98.138.219.232
Name:	yahoo.com
Address: 98.137.246.8
Name:	yahoo.com
Address: 72.30.35.10
Name:	yahoo.com
Address: 98.138.219.231

````
* Discover the reverse domain search
````bash
$ nslookup 98.138.219.231
Server:		127.0.1.1
Address:	127.0.1.1#53

Non-authoritative answer:
231.219.138.98.in-addr.arpa	name = media-router-fp1.prod1.media.vip.ne1.yahoo.com.

Authoritative answers can be found from:
219.138.98.in-addr.arpa	nameserver = ns5.yahoo.com.
219.138.98.in-addr.arpa	nameserver = ns4.yahoo.com.
219.138.98.in-addr.arpa	nameserver = ns1.yahoo.com.
219.138.98.in-addr.arpa	nameserver = ns3.yahoo.com.
219.138.98.in-addr.arpa	nameserver = ns2.yahoo.com.
ns1.yahoo.com	internet address = 68.180.131.16
ns2.yahoo.com	internet address = 68.142.255.16
ns3.yahoo.com	internet address = 203.84.221.53
ns4.yahoo.com	internet address = 98.138.11.157
ns5.yahoo.com	internet address = 119.160.253.83
ns1.yahoo.com	has AAAA address 2001:4998:130::1001
ns2.yahoo.com	has AAAA address 2001:4998:140::1002
ns3.yahoo.com	has AAAA address 2406:8600:b8:fe03::1003

````
* To consult the MX record (Mail Exchange).
````bash
$ nslookup -query=mx www.yahoo.com
Server:		127.0.1.1
Address:	127.0.1.1#53

Non-authoritative answer:
www.yahoo.com	canonical name = atsv2-fp.wg1.b.yahoo.com.

Authoritative answers can be found from:
wg1.b.yahoo.com
	origin = yf1.yahoo.com
	mail addr = hostmaster.yahoo-inc.com
	serial = 1532701538
	refresh = 30
	retry = 30
	expire = 86400
	minimum = 300
  ````
* To consult the NS record (Name server)
````bash
$ nslookup -query=ns www.yahoo.com
Server:		127.0.1.1
Address:	127.0.1.1#53

Non-authoritative answer:
www.yahoo.com	canonical name = atsv2-fp.wg1.b.yahoo.com.

Authoritative answers can be found from:
wg1.b.yahoo.com
	origin = yf1.yahoo.com
	mail addr = hostmaster.yahoo-inc.com
	serial = 1532702096
	refresh = 30
	retry = 30
	expire = 86400
	minimum = 300
````
* To check the SOA record (start of authority)

````bash
$ nslookup -type=soa www.yahoo.com
Server:		127.0.1.1
Address:	127.0.1.1#53

Non-authoritative answer:
www.yahoo.com	canonical name = atsv2-fp.wg1.b.yahoo.com.

Authoritative answers can be found from:
wg1.b.yahoo.com
	origin = yf1.yahoo.com
	mail addr = hostmaster.yahoo-inc.com
	serial = 1532702572
	refresh = 30
	retry = 30
	expire = 86400
	minimum = 300
````
* To consult all available DNS records
````bash
$ nslookup -query=any yahoo.com
Server:		127.0.1.1
Address:	127.0.1.1#53

Non-authoritative answer:
yahoo.com	has AAAA address 2001:4998:44:41d::4
yahoo.com	has AAAA address 2001:4998:44:41d::3
yahoo.com	has AAAA address 2001:4998:c:1023::4
yahoo.com	has AAAA address 2001:4998:58:1836::10
yahoo.com	has AAAA address 2001:4998:c:1023::5
yahoo.com	has AAAA address 2001:4998:58:1836::11
Name:	yahoo.com
Address: 98.137.246.7
Name:	yahoo.com
Address: 98.138.219.231
Name:	yahoo.com
Address: 98.137.246.8
Name:	yahoo.com
Address: 72.30.35.9
Name:	yahoo.com
Address: 72.30.35.10
Name:	yahoo.com
Address: 98.138.219.232
yahoo.com	nameserver = ns1.yahoo.com.
yahoo.com	nameserver = ns2.yahoo.com.
yahoo.com	nameserver = ns4.yahoo.com.
yahoo.com	nameserver = ns3.yahoo.com.
yahoo.com	nameserver = ns5.yahoo.com.

Authoritative answers can be found from:
yahoo.com	nameserver = ns5.yahoo.com.
yahoo.com	nameserver = ns4.yahoo.com.
yahoo.com	nameserver = ns3.yahoo.com.
yahoo.com	nameserver = ns1.yahoo.com.
yahoo.com	nameserver = ns2.yahoo.com.
ns1.yahoo.com	internet address = 68.180.131.16
ns2.yahoo.com	internet address = 68.142.255.16
ns3.yahoo.com	internet address = 203.84.221.53
````
* Enable debug mode
````bash
$ nslookup -debug yahoo.com
Server:		127.0.1.1
Address:	127.0.1.1#53

------------
    QUESTIONS:
	yahoo.com, type = A, class = IN
    ANSWERS:
    ->  yahoo.com
	internet address = 98.137.246.8
	ttl = 529
    ->  yahoo.com
	internet address = 72.30.35.9
	ttl = 529
    ->  yahoo.com
	internet address = 98.137.246.7
	ttl = 529
    ->  yahoo.com
	internet address = 72.30.35.10
	ttl = 529
    ->  yahoo.com
	internet address = 98.138.219.232
	ttl = 529
    ->  yahoo.com
	internet address = 98.138.219.231
	ttl = 529
    AUTHORITY RECORDS:
    ->  yahoo.com
	nameserver = ns1.yahoo.com.
	ttl = 12449
    ->  yahoo.com
	nameserver = ns4.yahoo.com.
	ttl = 12449
    ->  yahoo.com
	nameserver = ns3.yahoo.com.
	ttl = 12449
    ->  yahoo.com
	nameserver = ns2.yahoo.com.
	ttl = 12449
    ->  yahoo.com
	nameserver = ns5.yahoo.com.
	ttl = 12449
    ADDITIONAL RECORDS:
    ->  ns1.yahoo.com
	internet address = 68.180.131.16
	ttl = 531375
    ->  ns2.yahoo.com
	internet address = 68.142.255.16
	ttl = 531375
    ->  ns3.yahoo.com
	internet address = 203.84.221.53
	ttl = 534490
    ->  ns4.yahoo.com
	internet address = 98.138.11.157
	ttl = 530850
    ->  ns5.yahoo.com
	internet address = 119.160.253.83
	ttl = 530850
    ->  ns1.yahoo.com
	has AAAA address 2001:4998:130::1001
	ttl = 18764
    ->  ns2.yahoo.com
	has AAAA address 2001:4998:140::1002
	ttl = 18764
    ->  ns3.yahoo.com
	has AAAA address 2406:8600:b8:fe03::1003
	ttl = 18764
------------
Non-authoritative answer:
Name:	yahoo.com
Address: 98.137.246.8
Name:	yahoo.com
Address: 72.30.35.9
Name:	yahoo.com
Address: 98.137.246.7
Name:	yahoo.com
Address: 72.30.35.10
Name:	yahoo.com
Address: 98.138.219.232
Name:	yahoo.com
Address: 98.138.219.231
````

#### dig
Dig (Domain Information Groper) is a very useful command for querying DNS records. It is used a lot - among other things - for diagnosis

* The most basic example is:
````bash
$ dig google.com

; <<>> DiG 9.10.3-P4-Ubuntu <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 61584
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 4, ADDITIONAL: 9

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;google.com.			IN	A

;; ANSWER SECTION:
google.com.		67	IN	A	172.217.30.238

;; AUTHORITY SECTION:
google.com.		9954	IN	NS	ns1.google.com.
google.com.		9954	IN	NS	ns4.google.com.
google.com.		9954	IN	NS	ns3.google.com.
google.com.		9954	IN	NS	ns2.google.com.

;; ADDITIONAL SECTION:
ns1.google.com.		10969	IN	A	216.239.32.10
ns2.google.com.		10981	IN	A	216.239.34.10
ns3.google.com.		10973	IN	A	216.239.36.10
ns4.google.com.		10970	IN	A	216.239.38.10
ns1.google.com.		19260	IN	AAAA	2001:4860:4802:32::a
ns2.google.com.		274404	IN	AAAA	2001:4860:4802:34::a
ns3.google.com.		203558	IN	AAAA	2001:4860:4802:36::a
ns4.google.com.		257188	IN	AAAA	2001:4860:4802:38::a

;; Query time: 23 msec
;; SERVER: 127.0.1.1#53(127.0.1.1)
;; WHEN: Fri Jul 27 12:24:13 ADT 2018
;; MSG SIZE  rcvd: 303
````
* Obtain different types of DNS records
````bash
$ dig @208.67.222.222 google.com A

; <<>> DiG 9.10.3-P4-Ubuntu <<>> @208.67.222.222 google.com A
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 23542
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;google.com.			IN	A

;; ANSWER SECTION:
google.com.		300	IN	A	216.58.222.46

;; Query time: 109 msec
;; SERVER: 208.67.222.222#53(208.67.222.222)
;; WHEN: Fri Jul 27 12:25:36 ADT 2018
;; MSG SIZE  rcvd: 55

````
* Get name servers
````bash
$ dig @208.67.222.222 google.com NS

; <<>> DiG 9.10.3-P4-Ubuntu <<>> @208.67.222.222 google.com NS
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 28429
;; flags: qr rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;google.com.			IN	NS

;; ANSWER SECTION:
google.com.		345600	IN	NS	ns4.google.com.
google.com.		345600	IN	NS	ns3.google.com.
google.com.		345600	IN	NS	ns2.google.com.
google.com.		345600	IN	NS	ns1.google.com.

;; Query time: 168 msec
;; SERVER: 208.67.222.222#53(208.67.222.222)
;; WHEN: Fri Jul 27 12:31:24 ADT 2018
;; MSG SIZE  rcvd: 111

````

* Obtain MX records (From mail)
````bash
$ dig @208.67.222.222 google.com MX

; <<>> DiG 9.10.3-P4-Ubuntu <<>> @208.67.222.222 google.com MX
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 38989
;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;google.com.			IN	MX

;; ANSWER SECTION:
google.com.		600	IN	MX	40 alt3.aspmx.l.google.com.
google.com.		600	IN	MX	10 aspmx.l.google.com.
google.com.		600	IN	MX	20 alt1.aspmx.l.google.com.
google.com.		600	IN	MX	30 alt2.aspmx.l.google.com.
google.com.		600	IN	MX	50 alt4.aspmx.l.google.com.

;; Query time: 100 msec
;; SERVER: 208.67.222.222#53(208.67.222.222)
;; WHEN: Fri Jul 27 12:32:44 ADT 2018
;; MSG SIZE  rcvd: 147

````

* Get TXT records
````bash
$ dig @208.67.222.222 google.com TXT

; <<>> DiG 9.10.3-P4-Ubuntu <<>> @208.67.222.222 google.com TXT
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 45638
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;google.com.			IN	TXT

;; ANSWER SECTION:
google.com.		300	IN	TXT	"docusign=05958488-4752-4ef2-95eb-aa7ba8a3bd0e"
google.com.		3600	IN	TXT	"v=spf1 include:_spf.google.com ~all"
google.com.		3600	IN	TXT	"facebook-domain-verification=22rm551cu4k0ab0bxsw536tlds4h95"

;; Query time: 167 msec
;; SERVER: 208.67.222.222#53(208.67.222.222)
;; WHEN: Fri Jul 27 12:33:34 ADT 2018
;; MSG SIZE  rcvd: 217

````

* Get all types of records in the same query
````bash
$ dig any google.com

; <<>> DiG 9.10.3-P4-Ubuntu <<>> any google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 30925
;; flags: qr rd ra; QUERY: 1, ANSWER: 6, AUTHORITY: 4, ADDITIONAL: 9

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;google.com.			IN	ANY

;; ANSWER SECTION:
google.com.		101	IN	AAAA	2800:3f0:4002:809::200e
google.com.		32	IN	A	216.58.202.46
google.com.		9515	IN	NS	ns4.google.com.
google.com.		9515	IN	NS	ns1.google.com.
google.com.		9515	IN	NS	ns3.google.com.
google.com.		9515	IN	NS	ns2.google.com.

;; AUTHORITY SECTION:
google.com.		9515	IN	NS	ns1.google.com.
google.com.		9515	IN	NS	ns2.google.com.
google.com.		9515	IN	NS	ns4.google.com.
google.com.		9515	IN	NS	ns3.google.com.

;; ADDITIONAL SECTION:
ns1.google.com.		30317	IN	AAAA	2001:4860:4802:32::a
ns2.google.com.		343618	IN	AAAA	2001:4860:4802:34::a
ns3.google.com.		343618	IN	AAAA	2001:4860:4802:36::a
ns4.google.com.		343618	IN	AAAA	2001:4860:4802:38::a
ns1.google.com.		14605	IN	A	216.239.32.10
ns2.google.com.		14605	IN	A	216.239.34.10
ns3.google.com.		14605	IN	A	216.239.36.10
ns4.google.com.		52293	IN	A	216.239.38.10

;; Query time: 20 msec
;; SERVER: 127.0.1.1#53(127.0.1.1)
;; WHEN: Fri Jul 27 12:34:31 ADT 2018
;; MSG SIZE  rcvd: 387

````

* Conduct a reverse query
````bash
$ dig -x 173.194.34.233

; <<>> DiG 9.10.3-P4-Ubuntu <<>> -x 173.194.34.233
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 40168
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 4, ADDITIONAL: 9

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;233.34.194.173.in-addr.arpa.	IN	PTR

;; ANSWER SECTION:
233.34.194.173.in-addr.arpa. 86400 IN	PTR	mad01s09-in-f9.1e100.net.

;; AUTHORITY SECTION:
194.173.in-addr.arpa.	12194	IN	NS	ns2.google.com.
194.173.in-addr.arpa.	12194	IN	NS	ns4.google.com.
194.173.in-addr.arpa.	12194	IN	NS	ns1.google.com.
194.173.in-addr.arpa.	12194	IN	NS	ns3.google.com.

;; ADDITIONAL SECTION:
ns1.google.com.		18582	IN	AAAA	2001:4860:4802:32::a
ns2.google.com.		273726	IN	AAAA	2001:4860:4802:34::a
ns3.google.com.		202880	IN	AAAA	2001:4860:4802:36::a
ns4.google.com.		256510	IN	AAAA	2001:4860:4802:38::a
ns1.google.com.		10291	IN	A	216.239.32.10
ns2.google.com.		10303	IN	A	216.239.34.10
ns3.google.com.		10295	IN	A	216.239.36.10
ns4.google.com.		10292	IN	A	216.239.38.10

;; Query time: 40 msec
;; SERVER: 127.0.1.1#53(127.0.1.1)
;; WHEN: Fri Jul 27 12:35:32 ADT 2018
;; MSG SIZE  rcvd: 352
````

#### host 
The Host command is a minimal and easy-to-use CLI utility to perform DNS lookups that translate domain names into IP addresses and vice versa. It can also be used to list and verify various types of DNS records such as NS and MX, test and validate the ISP's DNS server and Internet connectivity, spam and blacklist records, DNS server troubleshooting and troubleshooting, among others.

* Find the IP address of the domain
This is the simplest host command that you can run, just provide a domain name like google.com to get the associated IP addresses.
````bash
$ host google.com
google.com has address 172.217.30.142
google.com has IPv6 address 2800:3f0:4002:806::200e
google.com mail is handled by 40 alt3.aspmx.l.google.com.
google.com mail is handled by 20 alt1.aspmx.l.google.com.
google.com mail is handled by 30 alt2.aspmx.l.google.com.
google.com mail is handled by 10 aspmx.l.google.com.
google.com mail is handled by 50 alt4.aspmx.l.google.com.

* Find domain name servers
To find out the domain name servers, use the -t option.
````bash
$ host -t ns google.com
google.com name server ns2.google.com.
google.com name server ns3.google.com.
google.com name server ns1.google.com.
google.com name server ns4.google.com.
````
* Search domain CNAME record
To find out the CNAME domain, run.
````bash
$ host -t cname mail.google.com
mail.google.com is an alias for googlemail.l.google.com.
````
* Find the MX record of the domain
To discover the MX records of a domain.
````bash
$ host -n -t mx google.com
google.com mail is handled by 40 alt3.aspmx.l.google.com.
google.com mail is handled by 50 alt4.aspmx.l.google.com.
google.com mail is handled by 10 aspmx.l.google.com.
google.com mail is handled by 20 alt1.aspmx.l.google.com.
google.com mail is handled by 30 alt2.aspmx.l.google.com.
````
* Find the TXT record of the domain
To find the TXT records of a domain.
````bash
$ host -t txt google.com
google.com descriptive text "docusign=05958488-4752-4ef2-95eb-aa7ba8a3bd0e"
google.com descriptive text "v=spf1 include:_spf.google.com ~all"
google.com descriptive text "facebook-domain-verification=22rm551cu4k0ab0bxsw536tlds4h95"
````
* Find SOA Record domain
You can have the host attempt to display the SOA records for the specified zone, of all authorized name servers authorized for that zone with the -C flag.
````bash
$ host -C google.com
Nameserver 216.239.32.10:
	google.com has SOA record ns1.google.com. dns-admin.google.com. 206305962 900 900 1800 60
Nameserver 2001:4860:4802:32::a:
	google.com has SOA record ns1.google.com. dns-admin.google.com. 206305962 900 900 1800 60
Nameserver 216.239.38.10:
	google.com has SOA record ns1.google.com. dns-admin.google.com. 206286683 900 900 1800 60
Nameserver 2001:4860:4802:36::a:
	google.com has SOA record ns1.google.com. dns-admin.google.com. 206305962 900 900 1800 60
Nameserver 2001:4860:4802:38::a:
	google.com has SOA record ns1.google.com. dns-admin.google.com. 206305962 900 900 1800 60
Nameserver 216.239.34.10:
	google.com has SOA record ns1.google.com. dns-admin.google.com. 206286683 900 900 1800 60
Nameserver 216.239.36.10:
	google.com has SOA record ns1.google.com. dns-admin.google.com. 206286683 900 900 1800 60
Nameserver 2001:4860:4802:34::a:
	google.com has SOA record ns1.google.com. dns-admin.google.com. 206305962 900 900 1800 60
````
* Query particular name server
To consult the server of domain names particual.
````bash
$ host google.com ns4.google.com
Using domain server:
Name: ns4.google.com
Address: 2001:4860:4802:38::a#53
Aliases: 
google.com has address 216.58.222.46
google.com has IPv6 address 2800:3f0:4002:804::200e
google.com mail is handled by 10 aspmx.l.google.com.
google.com mail is handled by 30 alt2.aspmx.l.google.com.
google.com mail is handled by 40 alt3.aspmx.l.google.com.
google.com mail is handled by 50 alt4.aspmx.l.google.com.
google.com mail is handled by 20 alt1.aspmx.l.google.com.
````
* Find all the information of domain registrations and zones
To perform an ANY type query, use the -a (all) option, which is equivalent to setting the -v option.
````bash
$ host -a google.com
Trying "google.com"
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 59887
;; flags: qr rd ra; QUERY: 1, ANSWER: 11, AUTHORITY: 4, ADDITIONAL: 10

;; QUESTION SECTION:
;google.com.			IN	ANY

;; ANSWER SECTION:
google.com.		231	IN	MX	10 aspmx.l.google.com.
google.com.		231	IN	MX	20 alt1.aspmx.l.google.com.
google.com.		231	IN	MX	40 alt3.aspmx.l.google.com.
google.com.		231	IN	MX	50 alt4.aspmx.l.google.com.
google.com.		231	IN	MX	30 alt2.aspmx.l.google.com.
google.com.		90	IN	AAAA	2800:3f0:4002:808::200e
google.com.		39	IN	A	172.217.30.238
google.com.		11126	IN	NS	ns2.google.com.
google.com.		11126	IN	NS	ns1.google.com.
google.com.		11126	IN	NS	ns4.google.com.
google.com.		11126	IN	NS	ns3.google.com.

;; AUTHORITY SECTION:
google.com.		11126	IN	NS	ns4.google.com.
google.com.		11126	IN	NS	ns1.google.com.
google.com.		11126	IN	NS	ns2.google.com.
google.com.		11126	IN	NS	ns3.google.com.

;; ADDITIONAL SECTION:
aspmx.l.google.com.	281	IN	A	64.233.186.27
ALT1.aspmx.l.google.com. 219	IN	A	173.194.76.26
alt2.aspmx.l.google.com. 19	IN	A	74.125.128.26
alt4.aspmx.l.google.com. 19	IN	A	74.125.68.26
ns1.google.com.		12141	IN	A	216.239.32.10
ns2.google.com.		12153	IN	A	216.239.34.10
ns3.google.com.		12145	IN	A	216.239.36.10
ns4.google.com.		12142	IN	A	216.239.38.10
ns1.google.com.		20432	IN	AAAA	2001:4860:4802:32::a
ns2.google.com.		275576	IN	AAAA	2001:4860:4802:34::a
Received 497 bytes from 127.0.1.1#53 in 52 ms
````
* Get TTL domain information
To find out the TTL domain information.
````bash
$ host -a google.com
Trying "google.com"
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 59887
;; flags: qr rd ra; QUERY: 1, ANSWER: 11, AUTHORITY: 4, ADDITIONAL: 10

;; QUESTION SECTION:
;google.com.			IN	ANY

;; ANSWER SECTION:
google.com.		231	IN	MX	10 aspmx.l.google.com.
google.com.		231	IN	MX	20 alt1.aspmx.l.google.com.
google.com.		231	IN	MX	40 alt3.aspmx.l.google.com.
google.com.		231	IN	MX	50 alt4.aspmx.l.google.com.
google.com.		231	IN	MX	30 alt2.aspmx.l.google.com.
google.com.		90	IN	AAAA	2800:3f0:4002:808::200e
google.com.		39	IN	A	172.217.30.238
google.com.		11126	IN	NS	ns2.google.com.
google.com.		11126	IN	NS	ns1.google.com.
google.com.		11126	IN	NS	ns4.google.com.
google.com.		11126	IN	NS	ns3.google.com.

;; AUTHORITY SECTION:
google.com.		11126	IN	NS	ns4.google.com.
google.com.		11126	IN	NS	ns1.google.com.
google.com.		11126	IN	NS	ns2.google.com.
google.com.		11126	IN	NS	ns3.google.com.

;; ADDITIONAL SECTION:
aspmx.l.google.com.	281	IN	A	64.233.186.27
ALT1.aspmx.l.google.com. 219	IN	A	173.194.76.26
alt2.aspmx.l.google.com. 19	IN	A	74.125.128.26
alt4.aspmx.l.google.com. 19	IN	A	74.125.68.26
ns1.google.com.		12141	IN	A	216.239.32.10
ns2.google.com.		12153	IN	A	216.239.34.10
ns3.google.com.		12145	IN	A	216.239.36.10
ns4.google.com.		12142	IN	A	216.239.38.10
ns1.google.com.		20432	IN	AAAA	2001:4860:4802:32::a
ns2.google.com.		275576	IN	AAAA	2001:4860:4802:34::a

Received 497 bytes from 127.0.1.1#53 in 52 ms
antonio@venz:~/devel/dns$ host -v -ta google.com
Trying "google.com"
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 58743
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 4, ADDITIONAL: 8

;; QUESTION SECTION:
;google.com.			IN	A

;; ANSWER SECTION:
google.com.		207	IN	A	216.58.202.46

;; AUTHORITY SECTION:
google.com.		11190	IN	NS	ns1.google.com.
google.com.		11190	IN	NS	ns4.google.com.
google.com.		11190	IN	NS	ns3.google.com.
google.com.		11190	IN	NS	ns2.google.com.

;; ADDITIONAL SECTION:
ns1.google.com.		31992	IN	AAAA	2001:4860:4802:32::a
ns2.google.com.		345293	IN	AAAA	2001:4860:4802:34::a
ns3.google.com.		345293	IN	AAAA	2001:4860:4802:36::a
ns4.google.com.		345293	IN	AAAA	2001:4860:4802:38::a
ns1.google.com.		16280	IN	A	216.239.32.10
ns2.google.com.		16280	IN	A	216.239.34.10
ns3.google.com.		16280	IN	A	216.239.36.10
ns4.google.com.		53968	IN	A	216.239.38.10

Received 292 bytes from 127.0.1.1#53 in 28 ms
````
* Use IPv4 or IPv6 well
Option -4 or -6 forces the host to use only IPv4 queries transport or only IPV6, respectively.
````bash
$ host -4 google.com
google.com has address 172.217.30.174
google.com has IPv6 address 2800:3f0:4002:808::200e
google.com mail is handled by 10 aspmx.l.google.com.
google.com mail is handled by 20 alt1.aspmx.l.google.com.
google.com mail is handled by 30 alt2.aspmx.l.google.com.
google.com mail is handled by 40 alt3.aspmx.l.google.com.
google.com mail is handled by 50 alt4.aspmx.l.google.com.
````
* Perform non-recursive queries
The -r option performs non-recursive queries, keep in mind that setting this option deletes the RD (desired recursion), the bit in the query made by the host.
````bash
$ host -rR 5 google.com
google.com has address 172.217.30.238
google.com has IPv6 address 2800:3f0:4002:808::200e
````
* Set UDP retries for a search
By default, the number of UDP attempts is 1, to change it, use the -R flag.
````bash
$ host -R 5 google.com
google.com has address 172.217.30.238
google.com has IPv6 address 2800:3f0:4002:807::200e
google.com mail is handled by 30 alt2.aspmx.l.google.com.
google.com mail is handled by 10 aspmx.l.google.com.
google.com mail is handled by 20 alt1.aspmx.l.google.com.
google.com mail is handled by 40 alt3.aspmx.l.google.com.
google.com mail is handled by 50 alt4.aspmx.l.google.com.
````
* Set query time Wait answer
By using the -W, you can tell the host to wait for a response for the time specified in seconds and, if the -w is used, it causes the host to always wait for a response:
````bash
$ host -T -W 10 google.com
google.com has address 172.217.30.238
google.com has IPv6 address 2800:3f0:4002:807::200e
google.com mail is handled by 10 aspmx.l.google.com.
google.com mail is handled by 20 alt1.aspmx.l.google.com.
google.com mail is handled by 50 alt4.aspmx.l.google.com.
google.com mail is handled by 30 alt2.aspmx.l.google.com.
google.com mail is handled by 40 alt3.aspmx.l.google.com.
````

