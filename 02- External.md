# External Network Penetration Testing

## Reconnaissance
### Passive External Network Reconnaissance
- Google Dorks (GHDB), bing dorks
- Pastebin
https://github.com/carlospolop/Pastos
https://github.com/leapsecurity/Pastepwnd
https://github.com/CIRCL/AIL-framework
https://github.com/cvandeplas/pystemon
https://github.com/xme/pastemon
- crt.sh
- https://certstream.calidog.io/
- spiderfoot
https://github.com/smicallef/spiderfoot
- Exposed credentials and leaks (Flare, dehashed, breach-parse)
- Social networks (linkedIn, hunter.io, clearbit, phonebook.cz, Facebook, Company twitter/instagram)
- DNS history
- ASN
https://bgp.he.net/dns/aecon.com#_ipinfo

- Wayback machine, google cache

### Active External Network Reconnaissance
- masscan
- censys
- shodan
- scans.io
- nmap
- DNS brute force (aiodnsbrute, subLocal)
- Aquatone, Eyewitness, Shutter
- DNS zone transfer
- subdomain takeover

### User account enumeration
On web app portal







## Exposed services - Protocols
### HTTP/HTTPS

### SMTP

### DKIM / DMARC / SPF misconfiguration

### SNMP
- snmpget
- onesixtyone

```
for i in $(cat onesixtyone/dict.txt); do echo -n "$i : "; snmpget -v 3 -u $i udp6:[IPv6] MIB_TO_FETCH; done
```

### FTP

### SSH

### Databases (MySQL, MSSQL, Oracle, DB2, Postgre, MongoDB...)

### Exposed storages
- AWS S3 buckets
- Azure blob storage
- GCP storage

### Scanning external target
- Nessus, Burp Enterprise, Qualys, nuclei, wpscan, joomscan...
http://www.melcara.com/wp-content/uploads/2017/09/parse_nessus_xml.v24.pl_.zip








## Exploitation
### RCE
RCE-as-a-feature (Jenkins, Serv-U, etc).
- https://github.com/p0dalirius/Awesome-RCE-techniques

### Exposed source code or credentials
- .git folder
- Access key, token, secret on github, gitlab, mercurial, code repo solutions...
Git / Repo secret parsers

    gitleaks (https://github.com/zricethezav/gitleaks)
    trufflehog (https://github.com/trufflesecurity/truffleHog)
    git-secrets (https://github.com/awslabs/git-secrets)
    shhgit (https://github.com/eth0izzle/shhgit)
    gitrob (https://github.com/michenriksen/gitrob)

### SAP
- https://book.hacktricks.xyz/network-services-pentesting/pentesting-sap
  
### Lync
- https://www.mdsec.co.uk/2017/04/penetration-testing-skype-for-business-exploiting-the-missing-lync/
- https://www.trustedsec.com/blog/attacking-self-hosted-skype-businessmicrosoft-lync-installations/
- https://github.com/mdsecresearch/LyncSniper

### IIS specific checks

### Web vulnerabilities
- serialization/deserialization

### Default Credentials in use


### Open SMTP Relay
- https://www.blackhillsinfosec.com/how-to-test-for-open-mail-relays/

### DNS Zone Transfer


### VPN - IKE Aggressive Mode

## Password spray
(o365, Azure, Citrix, RDP, VPN, OWA, etc)

#### General tool
- https://github.com/knavesec/CredMaster
The following plugins are currently supported:
- OWA - Outlook Web Access
- EWS - Exchange Web Services
- O365 - Office365
- O365Enum - Office365 User Enum (No Authentication Request)
- MSOL - Microsoft Online
- Okta - Okta Authentication Portal
- FortinetVPN - Fortinet VPN Client
- HTTPBrute - Generic HTTP Brute Methods (Basic/Digest/NTLM)
- ADFS - Active Directory Federation Services
- AzureSSO - Azure AD Seamless SSO Endpoint
- GmailEnum - Gmail User Enumeration (No Authentication Request)

#### CheckPoint SSL VPN 
- https://github.com/lutzenfried/checkpointSpray

#### O365
- https://github.com/blacklanternsecurity/TREVORspray

```
 ./trevorspray.py -e emails.txt --passwords "Winter2021!"  --delay 15 --no-current-ip --ssh ubuntu@<IP> ubuntu2@<IP2> -k privkey.pem
 ```

#### OWA
Metasploit module : ```scanner/http/owa_login```

#### Azure
- https://github.com/dafthack/MSOLSpray
- https://github.com/blacklanternsecurity/TREVORspray

### IP rotation
Sometimes during password spraying or brute force attack attacker will need to rotate IP and geolocation to avoid being blocked.

- Burp Extension: IPRotate
- RhinoSecurity Blog : https://rhinosecuritylabs.com/aws/bypassing-ip-based-blocking-aws/
- AWS Keys Setup : https://www.youtube.com/watch?v=_YQLao6p9GM
- Proxycannon https://www.blackhillsinfosec.com/using-burp-proxycannon/
- BHIS blog (https://www.blackhillsinfosec.com/how-to-rotate-your-source-ip-address/)
- Amazon Lambda
- Fireprox

### 2FA/MFA implementation issues
​
[MFASweep](https://github.com/dafthack/MFASweep): Detect MFA for various Microsoft Servers
Credsniper
Re-using valid credentials on alternate services
Mailsniper

### SSL/TLS
- heartbleed
- Shellshock

