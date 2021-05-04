---
layout: post
title: Introductory Networking
description: >
  The aim of this room is to provide a beginner's introduction to the basic principles of networking. Networking is a massive topic, so this really will just be a brief overview; however, it will hopefully give you some foundational knowledge of the topic, which you can build upon for yourself
---

# Introductory Networking


# Task 2 [ The OSI Model: An Overview]


### Which layer would choose to send data over TCP or UDP?

```bash

4

```

### Which layer checks received packets to make sure that they haven't been corrupted?

```bash

2

```

### In which layer would data be formatted in preparation for transmission?

```bash

2

```

### Which layer transmits and receives data?

```bash

1

```

### Which layer encrypts, compresses, or otherwise transforms the initial data to give it a standardised format?
 
```bash

6

```

### Which layer tracks communications between the host and receiving computers?

```bash

5

```

### Which layer accepts communication requests from applications?

```bash

7

```

### Which layer handles logical addressing?

```bash

3

```

### When sending data over TCP, what would you call the "bite-sized" pieces of data?

```bash

Segments

```

### [Research] Which layer would the FTP protocol communicate with?

```bash

7

```

### Which transport layer protocol would be best suited to transmit a live video?

```bash

UDP

```


# Task 3 [ Encapsulation ]


### How would you refer to data at layer 2 of the encapsulation process (with the OSI model)?

```bash

Frames

```

### How would you refer to data at layer 4 of the encapsulation process (with the OSI model), if the UDP protocol has been selected?

```bash

Datagrams

```

### What process would a computer perform on a received message?

```bash

De-encapsulation

```

### Which is the only layer of the OSI model to add a trailer during encapsulation?

```bash

Data Link

```

### Does encapsulation provide an extra layer of security (Aye/Nay)?

```bash

Aye

```


# Task 4 [ The TCP/IP Model ]


### Which model was introduced first, OSI or TCP/IP?

```bash

TCP/IP

```

### Which layer of the TCP/IP model covers the functionality of the Transport layer of the OSI model (Full Name)?

```bash

Transport

```

### Which layer of the TCP/IP model covers the functionality of the Session layer of the OSI model (Full Name)?

```bash

Application

```

### The Network Interface layer of the TCP/IP model covers the functionality of two layers in the OSI model. These layers are Data Link, and?.. (Full Name)?

```bash

Physical

```

### Which layer of the TCP/IP model handles the functionality of the OSI network layer?

```bash

Internet

```

### What kind of protocol is TCP?

```bash

Connection-based

```
 
### What is SYN short for?

```bash

Synchronise

```

### What is the second step of the three way handshake?

```bash

SYN/ACK

```

### What is the short name for the "Acknowledgement" segment in the three-way handshake?

```bash

ACK

```


# Task 5 [ Networking Tools _Ping_ ]


### What command would you use to ping the bbc.co.uk website?

```bash

ping bbc.co.uk

```


### Ping muirlandoracle.co.uk , What is the IPv4 address?

```bash

217.160.0.152

```

### What switch lets you change the interval of sent ping requests?

```bash

-i

```

###  What switch would allow you to restrict requests to IPv4?

```bash

-4

```

### What switch would give you a more verbose output?

```bash

-v

```

# Task 6 [ Networking Tools _Traceroute_ ]

### What switch would you use to specify an interface when using Traceroute?

```bash

-i

```

### What switch would you use if you wanted to use TCP SYN requests when tracing the route?

```bash

-T

```

### [Lateral Thinking] Which layer of the TCP/IP model will traceroute run on by default (Windows)?

```bash

Internet

```


# Task 7 [ Networking Tools _Whois_ ]


### What is the registrant postal code for facebook.com?

```bash

94025


```


### When was the facebook.com domain first registered?
 
```bash

29/03/1997

```


### Which city is the registrant based in?

```bash

Redmond

```

### [OSINT] What is the name of the golf course that is near the registrant address for microsoft.com?

```bash

Bellevue Golf Course

```


### What is the registered Tech Email for microsoft.com?

```bash

msnhst@microsoft.com

```


# Task 8 [ Networking Tools _Dig_ ]

### What is DNS short for?

```bash

Domain Name System

```

### What is the first type of DNS server your computer would query when you search for a domain?

```bash

Recursive

```


### What type of DNS server contains records specific to domain extensions (i.e. .com, .co.uk*, etc)*? Use the long version of the name.

```bash

Top-Level Domain

```

### Where is the very first place your computer would look to find the IP address of a domain?

```bash

Local Cache

```

### [Research] Google runs two public DNS servers. One of them can be queried with the IP 8.8.8.8, what is the IP address of the other one?

```bash

8.8.4.4

```


### If a DNS query has a TTL of 24 hours, what number would the dig query show?

```bash

86400

```


