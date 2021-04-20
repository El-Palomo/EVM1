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




















