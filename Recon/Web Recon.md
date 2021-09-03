---
tags: 🔻 🔻/Recon
aliases: Hacking Notes
---

# Web Recon Tools

# Gobuster

#gobuster

`gobuster dir -w /usr/share/dirbuster/wordlists/directory-list-2.3-medium.txt -o gobuster.txt -u http://`

Gobuster requires a mode, host and wordlist to search

*Global Flags*
-z, –noprogress Don’t display progress  
-o, –output string Output file to write results to (defaults to stdout)  
-q, –quiet Don’t print the banner and other noise  
-t, –threads int Number of concurrent threads (default 10)  
–delay duration Time each thread waits between requests (e.g. 1500ms)  
-v, –verbose Verbose output (errors)  
-w, –wordlist string Path to the wordlist

## Modes

-   dir – the classic directory brute-forcing mode
-   dns – DNS subdomain brute-forcing mode
-   vhost – virtual host brute-forcing mode (not the same as DNS!)

### Dir Mode *most used*

**Flags:**  
-u, –url string The target URL  
-U, –username string Username for Basic Auth  
-P, –password string Password for Basic Auth  

-f, –addslash Append / to each request  
-c, –cookies string Cookies to use for the requests  
-e, –expanded Expanded mode, print full URLs  
-x, –extensions string File extension(s) to search for  
-r, –followredirect Follow redirects  
-H, –headers stringArray Specify HTTP headers, -H ‘Header1: val1’ -H ‘Header2: val2’  
-l, –includelength Include the length of the body in the output  
-k, –insecuressl Skip SSL certificate verification  
-n, –nostatus Don’t print status codes  
-p, –proxy string Proxy to use for requests \[http(s)://host:port\]  
-s, –statuscodes string Positive status codes (will be overwritten with statuscodesblacklist if set) (default “200,204,301,302,307,401,403”)  
-b, –statuscodesblacklist string Negative status codes (will override statuscodes if set)  
–timeout duration HTTP Timeout (default 10s)  
-a, –useragent string Set the User-Agent string (default “gobuster/3.0.1”)  
–wildcard Force continued operation when wildcard found

### DNS mode

**Flags:**
-d, –domain string The target domain  
-h, –help help for dns  
-r, –resolver string Use custom DNS server (format server.com or server.com:port)  
-c, –showcname Show CNAME records (cannot be used with ‘-i’ option)  
-i, –showips Show IP addresses  
–timeout duration DNS resolver timeout (default 1s)  
–wildcard Force continued operation when wildcard found

### Vhosts

**Flags:**
-c, –cookies string Cookies to use for the requests  
-r, –followredirect Follow redirects  
-H, –headers stringArray Specify HTTP headers, -H ‘Header1: val1’ -H ‘Header2: val2’  
-h, –help help for vhost  
-k, –insecuressl Skip SSL certificate verification  
-P, –password string Password for Basic Auth  
-p, –proxy string Proxy to use for requests \[http(s)://host:port\]  
–timeout duration HTTP Timeout (default 10s)  
-u, –url string The target URL  
-a, –useragent string Set the User-Agent string (default “gobuster/3.0.1”)  
-U, –username string Username for Basic Auth


# Nikto

#nikto #Enumeration 

-h		Provide the Host name

-port	to provide a specific port if required

-ssl		force ssl
-nossl		disable ssl

-dbcheck	Database check

Nikto -h *Hostname/IP* -Display *Option*  
1 Show redirects  
2 Show Cookies  
3 Show 200/OK responses  
4 Show URL requiring authentication  
D Show debug output  
E HTTP Errors  
P Print progress to STDOUT  
S Scrub output of IP and Hostname  
V Verbose output

Nikto -h *Hostname/IP*  -evasion *Option*  
1 Random URI Encoding  
2 Directory Self-Reference /./  
3 Premature URL ending  
4 Prepend long random string  
5 Fake parameter  
6 TAB as request spacer  
7 Change the case of the URL  
8 Used windows directory separator \\  
A Use a carriage return (0x0d) as a request spacer  
B  Use binary value (0x0b) as a request spacer
	
Nikto -h *Hostname/IP*  -Tuning *Option* 
1   Interesting file  
2   Misconfiguration  
3   Information Disclosure  
4   Injection (XSS/Script/HTML)  
5   Remote File Retrieval – Inside Web Root  
6   Denial of Service  
7   Remote File Retrieval – Server Wide  
8   Command Execution – Remote Shell  
9   SQL Injection  
0   File Upload  
a   Authentication Bypass  
b   Software Identification  
c   Remote Source Inclusion  
x   Reverse Tuning Option

# Curl
	
#curl
	
curl -v -X OPTIONS *http://Hostname/IP* /test/
curl --upload-file *file name* -v --url *Hostname/IP*  -0 --http1.0

	
# Dirsearch

#dirsearch
dirsearch -u http://x.x.x.x
dirsearch -u http://x.x.x.x
dirsearch -u http://x.x.x.x
dirsearch -u http://x.x.x.x
dirsearch -u http://x.x.x.x
python3 dirsearch.py -f -e html,php,tar.gz,txt,xml,zip -u http://x.x.x.x

	
# Dirb	

#Dirb
dirb http://localhost:5000 ./docs/common.txt
dirb http://webscantest.com /usr/share/dirb/wordlists/vulns/apache.txt
dirb http://x.x.x.x
dirb http://x.x.x.x
dirb http://x.x.x.x
dirb http://x.x.x.x
dirb http://x.x.x.x
dirb http://x.x.x.x
dirb http://target.com -a "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/51.0.2704.x.x.x.x

	
# Wfuzz

#WFUZZ
	
wfuzz -c -w /usr/share/seclists/Discovery/Web_Content/common.txt --hc 404 $ip/FUZZ

wfuzz -c -w /usr/share/seclists/Discovery/Web_Content/common.txt -R 3 --sc 200 $ip/FUZZ

wfuzz -c -z file,/root/.ZAP/fuzzers/dirbuster/directory-list-2.3-big.txt --sc 200 http://pegasus.dev:8088/FUZZ.php

wfuzz --hw=1 --hh=3076 -w seclist_common_wordlist.txt http://ip/FUZZ

wfuzz -c -z file,/root/Desktop/tools/SecLists/Usernames/Names/names.txt --hs "Try again" -d "username=FUZZ&password=anything" *http://ip*

# CMS


#CMS
	
cmsmap http://IP_ADDR -f (D,J…)

droopescan scan drupal -u http://IP_ADDR


wpscan --url http://IP_ADDR --enumerate u,p,t

wpscan --url //dc-2 --enumerate p --enumerate t --enumerate u

# Wordpress
#wordpress
	
wpscan --url http://.... --log
wpscan --url http://... --enumerate u --log
wpscan --url http://*targetip* --wordlist wordlist.txt --username example_username
http://....../wp-admin
http://...../wp-content/uploads/2017/x.x.x.x

# Other
	
joomscan -u http://x.x.x.x

	
#portknock
	
for x in 7000 8000 9000; do nmap -Pn –host_timeout 201 –max-retries 0 -p $x server_ip_address; done

# ASN Enumeration

Autonomous system numbers are given to alarge enough networks.
These asn's will help track down some semblance of an entities IT Infrastructure.
The most reliable way to get these is manually through;

http://bpg.he.net


Because of cloud infrastructure ASNs arent always a complete picture of a network. Rouge assets could exist on cloud environments like AWS and Azure


### Automatic lookup
#asnlookup
ASNlookup & metabigor are both automatic ASN scraper tools

!!Caution May scrap more than expected to need to verify targets




### Amass
#amass
amass intel -asn ####

Amass can return seed domains from the ASN to parse through the certificates to find seed domains owned by that ASN


# Reverse Whois

#reversewhois
Every website has some reg info on file with registrars. 

2 key pieces of data we canuse are organisation name and any emails in the WHOIS data.

http://www.whoxy.com is one such domain

automatic tool to do this is DOMLink

# Subdomain Enumeration
#subdomainenumeration

Main tool used Amass

## linked and JS discovery

Can be done on Burp Suite Pro easiest

Another way to widen our scope is to examine all the links of the main target.
We can visit a see/root and recursively spider all the links for a term with regex, examining those links, and their links and so on until well have found all sites that could be in scope
1. turn off passive scanning
2. set forms auto to submit
3. set scope to advanced control and use "keyword" of atarget name (not a nomral FQDN)
4. Walk+browse main site, then spider all hosts recursively


GoSpider or hakrawler or subscraper
both work in terminal rather than using burp pro


### Subdomainizer

Tool used to find subdomains referenced in JS files, Find cloud services referenced in JS files and use the Shannon Entropy formula to find potentially sensitivie items in JS files


## sub domain scraping


manual Google scraping (example twitch) 

site:twitch.tv -www.twitch.tv -watch.twitch.tv -dev.twitch.tv

keep on minus'ing out domains until google doesnt know any more subdomains

### Auto scraping

Amass & Subfinder auto scrap

amass has the most sources extensivle output bruteforcing permutationscanning and a ton of other modes to do additional analysis


python file called github-subdomains.py
queiries github api for references to a root and spiders our subdomains


#### Cloud ranges

bufferover.run api by sam erb
needs setting up and bash scripting not live data - most of the data from this will be found by amass

## Subdomain bruteforce

Amass does this with a -rf flag added to the command to give it a resolvers.txt 

amass enum -brute -d twitch.tv -src


use a bruteforce list (jhaddix has an all.txt list avaliable)

