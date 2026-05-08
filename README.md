1) Wi-Fi hacking
   Analysing the .pcap file for SSID and BSSID
   Filter --> eapol --> packet no. 8 --> BSSID:Netgear ('value') --> copy the value --> kali --> aircrack-ng -w /usr/share/wordlists/rockyou.txt wpa.full.cap
   Key Found! [ ]

2) Bluetooth Hacking
   Filter --> ' bthci_evt.bd_addr ' – MAC address --> Packet no. 12 --> BD_ADDR: value -->
   Bluetooth scanning process to identify nearby devices
   --> btle.advertising_header.pdu_type == 0x00 --> Packet no. 31 --> custom-id
   --> btle.advertising_header.pdu_type == 0x03 --> Packet no. 28 --> scanning address : 'value'
   --> btle.advertising_header.pdu_type == 0x04 --> Packet no. 23 --> advertising address : 'value'
