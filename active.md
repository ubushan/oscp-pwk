# Active Information Gathering

## DNS Enum
NS - Nameserver records contain the name of the authoritative servers hosting the DNS records for a domain.  
A - Also known as a host record, the "a record" contains the IP address of a hostname (such as www.megacorpone.com).  
MX - Mail Exchange records contain the names of the servers responsible for handling email for the domain. A domain can contain multiple MX records.  
PTR - Pointer Records are used in reverse lookup zones and are used to find the records associated with an IP address.  
CNAME - Canonical Name Records are used to create aliases for other host records.  
TXT - Text records can contain any arbitrary data and can be used for various purposes, such as domain ownership verification.  


### Forward lookup Brute force
```
$ cat list.txt
www
ftp
mail
owa
proxy
router

$ for ip in $(cat list.txt); do host $ip.megacorpone.com; done
```

### Reverse Lookup Brute force
```
$ for ip in $(seq  50 100); do host 38.100.193.$ip; done | grep -v "not found"
```
  
## DNS Zone Transfer
```
$ host -t ns <domain name>
$ host -l <domain name> <dns server address>
```

Util - https://github.com/mandatoryprogrammer/TLDR
### Kali linux utils
DNSRecon - https://github.com/darkoperator/dnsrecon
DNSEnum

## Port Scanning
Nmap  
Masscan  


## SMB Enum
Ports: 139, 445  
Nmap  
NSE Scripts: smb-os-discovery, smb-vuln-ms08-067  
nmap -v -p 139, 445 --script=smb-os-discovery 10.11.1.227

## NFS Enum
Ports: 111  
nmap -v -p 111 10.11.1.1-254  
NSE Scripts: rpcinfo, nfs*  
nmap -sV -p 111 --script=rpcinfo 10.11.1.1-254  

## SMTP Enum
## SNMP Enum
