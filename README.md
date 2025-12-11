# Ethical-hacking-Paro-
A deep dive into nmap and scapy
<img width="1903" height="1031" alt="scap" src="https://github.com/user-attachments/assets/23da0442-599e-41dd-990e-131235b73d85" />
1. Nmap Scanning: Host Discovery
   
 ```bash
nmap -sn 10.6.6.0/24
 ```
 OS Detection
 ```bash
sudo nmap -O 10.6.6.23
 ```

 Service & Version Enumeration
```bash
nmap -p21 -sV -A -T4 10.6.6.23
```

 SMB Port Scan
```bash
nmap -A p139, p445 10.6.6.23
```
<img width="1903" height="1031" alt="scap" src="https://github.com/user-attachments/assets/23da0442-599e-41dd-990e-131235b73d85" />

 SMB Share Enumeration
```bash
nmap --script smb-enum-shares.nse -p445 10.6.6.23
```

 Accessing SMB Share
```bash
smbclient //10.6.6.23/print$ -N
```
Type exit to close

<img width="1874" height="618" alt="smb" src="https://github.com/user-attachments/assets/ab3b1475-77e4-48f1-b08c-09b87450bd66" />

 2. Basic Network Information

```bash
ifconfig
```

```bash
ip route
```

```bash
cat /etc/resolv.conf
```

3. Packet Capture with TCPDump: Start Packet Capture
   
```bash
sudo tcpdump -i eth0 -s 0 -w ladies.pcap
```

Stop with: Ctrl + C

Verify File & Open in Wireshark

```bash
ls ladies.pcap
wireshark
```

 4. Scapy Sniffing & Packet Analysis: Start Scapy
```bash
sudo su
scapy
```

 Basic Sniffing
 ```bash
sniff()
```

In another terminal:

```bash
ping google.com
```

Stop both with Ctrl + C

```bash
paro = _
paro.summary()
```
<img width="888" height="892" alt="scapy" src="https://github.com/user-attachments/assets/9629519d-bade-4fcd-9c18-a73e8633e07b" />

 Web Interface Test
 
```bash
Open browser → http://10.6.6.23
```

 Sniff on Specific Interface
 
```bash
sniff(iface="br-internal")
```

```bash
ping 10.6.6.1/24
```

Stop sniffing: Ctrl + C

```bash
paro2 = _
```

```bash
paro2.summary()
```

Filtered Sniffing (ICMP Only)

```bash
sniff(iface="br-internal", filter="icmp", count=5)
```

In another terminal:
```bash
ping 10.6.6.23
```

<img width="1125" height="913" alt="scapy2" src="https://github.com/user-attachments/assets/8dd02825-7cb5-41ce-90e3-aad4466edbdb" />
Stop with Ctrl + C.

```bash
paro3 = _
paro3.summary()
paro3[3]
```
<img width="1247" height="864" alt="scapy1" src="https://github.com/user-attachments/assets/a23924eb-ae24-4baf-8888-4348b91e6a7c" />
