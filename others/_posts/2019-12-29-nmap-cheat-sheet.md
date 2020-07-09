---
layout: post
title: Nmap Cheat Sheet
description: >
  **Nmap** is a great tool for hackers and network administrators. Whey you first start playing with these tools it will be a bit difficult.this post all about Namp and how to use these tools.
---

## What is Nmap?

Nmap is an open-source program that is a helpful tool for network administrators which can be used to discover, monitor, and troubleshoot TCP/IP systems.

## What is Port number?

A **port** number is a logical construct that identifies a specific process or type of network service. Ports are identified for each protocol and address combination by a 16-bit unsigned number, commonly known as the port number.

## Port Scan Result
	1. Open
	2. Closed
	3. Filtered
	4. Unfiltered
	5. Open | Filtered
	6. Closed | Filtered


## Scan Options

| Scan Name | Command Syntax  |
|--|--|
| TCP SYN Scan | -sS |
| TCP connect() Scan| -sT |
| ACK Scan | -sA |
| FIN Stealth Scan | -sF |
| Xmas Tree Stealth Scan | -sX |
| Null Stealth Scan | -sN |
| Ping Scan | -sP |
| Version Detection| -sV |
| UDP Scan | -sU |
| IP Protocol Scan | -sO |
| Window Scan | -sW |
| RPC Scan | -sR |
| List Scan | -sL |
| Idle Scan | -sI |
| FTP Bounce Attack| -b |




## Basic Scanning Techniques
### Scan a Single Target
> format: `$ nmap [target-ip/Domain]`

```bash
$ nmap yahoo.com
$ nmap 192.168.0.1
```
### Scan multiple Targets
> format: `$ nmap [target-1] [target-2]`

```bash
$ nmap yahoo.com uber.com
$ nmap 192.168.0.1 192.168.0.100
```


### Scan a list of targets
> format: `$ nmap -iL [target-ip-list]`

```bash
$ nmap -iL ipLixt.txt
```
### Ranger Scan
> format: `$ nmap [ip-range]`

```bash
$ nmap 192.168.0.1-100
$ nmap 192.168.0.1-500
```

### Scan an entire subnet
> format: `$ nmap  [ip-address/cdir]`

```bash
$ nmap 192.168.0.1/24
$ nmap 192.168.0.1/16
$ nmap 192.168.0.1/8
```

### Scan random hosts
> format: `$ nmap  -iR [number]`

```bash
$ nmap -iR 100
$ nmap -iR 10
```

### Excluding targets from a scan
> format: `$ nmap  [targets] –exclude [targets]`

```bash
$ nmap 192.168.0.1-300 -exclude 192.168.0.102
```
### Perform an aggressive scan
> format: `$ nmap -A [target]`

```bash
$ nmap -A 192.168.0.1
$ nmap -A yahoo.com
$ nmap -A scanme.nmap.org
```


## Discovery Options
| Scan Name  | Command Syntax |
|--|--|
| Ping Scan   | ` nmap -sP [target]`  |
| Don't Ping | ` nmap -PN [target]`|
| TCP SYN Ping | ` nmap -PS [target]` |
| TCP ACK Ping | ` nmap -PA [target]` |
| UDP Ping | ` nmap -PU [target]` |
| IP protocol Ping | ` nmap -PO [target]` |
| ARP Ping | ` nmap -PR [target]` |
| Traceroute | ` nmap -traceroute [target]` |
| Create a Host list | ` nmap -sL [targets]` |



### Reverse DNS Scan

```bash
$ nmap facebook.com/24 -sL
```
###  Syn Scan

```bash
$ nmap -iR 100 -PS 22-25,80,113,1050,35000 -v -sn
```
### ACK scan

```bash
$ nmap -iR 100 -PA 22-25,80,113,1050,35000 -v -sn
```

### UDP scan

```bash
$ nmap -iR 100 -PU 53 -sn -vv
```
### IPv6 Scan

```bash
$ nmap -6 fe80::29aa:9db9:4164:d80e
```


###  Example of nmap Scan

```bash
$ nmap 98.137.246.8 -sL --dns-server 8.8.8.8
$ nmap -iR 3 -sn --traceroute
$ nmap 98.137.246.8 -sS -v
$ nmap 98.137.246.8 -sT -v
$ nmap 98.137.246.8 -sA -v
$ nmap 98.137.246.8 -sW -v
$ nmap 98.137.246.8 -p U:53,111,137 T:21-25,80,139 -sS -sU
$ nmap 98.137.246.8 -v --top-port 2000
$ nmap 98.137.246.8 -sV --allports
$ nmap 98.137.246.8 -sV --version-intensity 1 -v
$ nmap 98.137.246.8 -sV --version-all -v
$ nmap 98.137.246.8 -sV --version-trace
```

### OS Detection

```bash
$ nmap 45.33.32.156 -O -Pn -v --osscan-limit
$ nmap 45.33.32.156 -O --fuzzy -max-os-tries 1

```

## Firewall Evasion Techniques

| Scan Name  | Command Syntax |
|--|--|
| Fragment packets |  `nmap -f [target]` |
| Use a decoy |  ` nmap -D RND: [number] [target]` |
| Idle zombie scan |  ` nmap -sI [zombie-ip] [target]` |
| Append random data |  ` nmap -data-length [size] [target]` |
| Randomize target scan order |  ` nmap -randomize-hosts [target]` |
| Spoof MAC Address |  `nmap -spoof-mac [MAC|0|vendor] [target]` |
| Send bad checksums |  ` nmap -badsum [target]` |


> Format `nmap -n -D [decoy-ip],[decoy-ip],[decoy-ip] [target]`

```bash
$ nmap -n -D 98.137.246.8,13.107.21.200,172.217.194.101 45.33.32.156
```
>Format `nmap -S -e eth0 -Pn [spoof_address] [target]`

```bash
$ nmap -S -e eth0 -Pn 172.217.194.101 45.33.32.156
```
>Format `nmap -n -T4 -g 53 [ip]`

```bash
$ nmap -n -T4 -g 53 45.33.32.156
```
>Format `nmap --data-length [number] [target]`

```bash
$ nmap --data-lenght 200 45.33.32.156
```
>Format `nmap --data-string "Some Strings" [target] `

```bash
$ nmap --data-string "A Test Scann" 45.33.32.156
```
>Format `nmap -f -T 0 -n -PN --data-length 200 -D  [decoy-ip],[decoy-ip],[decoy-ip] [target]`

```bash
$ nmap -f -T 0 -n -PN --data-lenght 200 -D 98.137.246.8,13.107.21.200,172.217.194.101 45.33.32.156
```

## Broad Cast Scan

>Format `nmap --script broadcast -v`

```bash
$ nmap --script broadcast -v
```

>Format `nmap --script "broadcasr and not targets*" -v`

```bash
$ nmap --script "broadcast and not targets*" -v
```

>Format ` nmap --script "broadcasr and not targets*" -v --script-trace`

```bash
$ nmap --script "broadcasr and not targets*" -v --script-trace
```

>Format `nmap --script “vuln,exploit” -vv [target] -sV -O`

```bash
$ nmap --script “vuln,exploit” -vv [target] -sV -O
```

>Format `nmap --script whois* [domain / target-ip]`

```bash
$ nmap --script whois* <domain/ip>
```

## Version Detection

| Scan Name | Command Syntax |
|--|--|
| Operating system detection | `nmap -O [target]` |
| Attempt to guess an unknown | `nmap -O –osscan-guess [target]` |
| Service version detection | `nmap -sV [target]` |
| Troubleshooting version scans | ` nmap -sV –version-trace [target] ` |
| Perform a RPC scan | `nmap -sR [target]` |

 

```bash
$ nmap -O 45.33.32.156
```

```bash
$ nmap -O --osscan-guess 45.33.32.156
```
```bash
$ nmap -sV 45.33.32.156
```
```bash
$ nmap -sV -version-trace 45.33.32.156
```

```bash
$ nmap -sR 45.33.32.156
```


## Output Options

| Scan Name | Command Syntax |
|--|--|
| Save output to a text file | `nmap -oN [Output-File] [target]`  |
| Save output to a xml file |  `nmap -oX [Outout-File] [target]`  |
| Output all supported file types |  `nmap -oA [path/Output-file] [target]`  |
| Periodically display statistics |  `nmap -stats-every [time] [target]`  |
| Grepable output |  ` nmap -oG [Output-File] [target]`  |







## Nmap Scripting Engine

| Scan Name | Command Syntax |
|--|--|
| Execute individual scripts | `nmap  --script [script.nse] [target]` |
| Update the script database | `nmap –script-updatedb` |

## Script Scanning

```bash
$ nmap -sC 45.33.32.156 -v 
```

```bash
$ nmap 45.33.32.156 --script default,safe -v -O -sV
```

```bash
$ nmap -vvv --script=banner 45.33.32.156
```

```bash
$ nmap -Pn --script=http-xssed 45.33.32.156
```

```bash
$ nmap -Pn --script=http-sitemap-generator 45.33.32.156
```

```bash
$ nmap -v --script "http-*" 45.33.32.156
```

```bash
$ nmap -n -Pn -p 80 --open -sV -v --script http-method-tramper 45.33.32.156
```

```bash
$ nmap -n -Pn -p 80 --open -sV -vvv --script banner,http-title -iR 1000
```

```bash
$ nmap --script smb-os-discovery -vv 45.33.32.156
```

```bash
$ nmap -n -Pn -vv -O -sV --script smb-enum*,smb-ls,smb-mbenum,smb-os-discovery,smb-vuln*,smbv2* -vv 45.33.32.156
```

```bash
$ nmap -p80 --script http-wordpress-brute --script-args http-wordpress-brute.threads=5 [wordpress-Site-Domain]
```

```bash
$ nmap -p25 --script smtp-brute 45.33.32.156
```

```bash
$ nmap -p80 --script http-waf-detect 45.33.32.156
```

```bash
$ nmap -p80 --script http-unsafe-output-escaping 45.33.32.156
```

```bash
$ nmap -p80 --script http-sql-injection 45.33.32.156
```

```bash
$ nmap -p3306 --script mysql-databases --script-args mysqluser=[username],mysqlpass=[password] 45.33.32.156
```

```bash
$ nmap -sV --script smtp-open-relay -v 45.33.32.156
```

```bash
$ nmap -sV --script smtp-open-relay -v -iR 1000 -p 25 -n -Pn 
```



### Advance Scan

```bash
$ nmap --spoof-mac-Cisco --data-length 24 -T paranoid --max-hostgtoup 1 --max-parallelism 10 -PN -f -D 10.2.20.5,RND:5,ME --v -n -sS -sV -oA output_file -p T:1-1024 -random-hosts 10.1.1.10 10.1.1.15 
```

### Common Scan

```bash
nmap -sV -sC -T4 -A --script vuln -oA scan 192.168.0.100
```



