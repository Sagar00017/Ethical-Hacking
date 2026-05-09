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

3) Cloud Hacking (write up)
   
   Cloud Vulnerabilities
   
   1. IAM Weaknesses
   2. Misconfigured Storage
   3. Insecure API's 
   4. Network Security Misconfigurations
   5. Container & Kubernetes vulnerabilties

      Typical Cloud Attack Flow
      
      1. Reconnaissance - Attackers first identify exposed cloud assets like Public storage buckets, Exposed APIs
      2.  Initial Access - The attacker gains an entry point like Phishing cloud credentials, Stolen API keys
      3.  Credential Access - Cloud attacks heavily focus on identity theft. Goals --> Access keys, CI/CD secrets
      4.  Privilege Escalation - Once inside, attackers try to gain higher privileges. Techniques like Overly permissive IAM roles, Weak RBAC
      5.  Lateral Movement - Attackers move between services and environments. Common Movement Paths -> VM → cloud control plane & Container → Kubernetes cluster
      6.  Persistence - Attackers establish long-term access like Creating hidden IAM users & Adding SSH keys

Link --> https://wiki.wireshark.org/Bluetooth

Bluetooth File --> wifi-bluetooth-advent.pcap

### Bluetooth Low Energy (BLE)

```wireshark
btle
```

or

```wireshark
bluetooth.le
```

### BLE Link Layer

```wireshark
btle.ll
```

### Bluetooth L2CAP

```wireshark
btl2cap
```

### Bluetooth Attribute Protocol (ATT)

```wireshark
btatt
```

### Only ATT Requests

```wireshark
btatt.opcode.method == 0x02
```

### Only ATT Responses

```wireshark
btatt.opcode.method == 0x0b
```

### GATT-related Traffic

```wireshark
btgatt
```

### Show Advertising Packets

```wireshark
btle.advertising_header
```

### Show Data Channel Packets

```wireshark
btle.data_header
```

### Filter by Device MAC Address

Replace with your BLE device address:

```wireshark
bluetooth.addr == aa:bb:cc:dd:ee:ff
```

### Filter Read/Write Attribute Operations

#### Read Requests

```wireshark
btatt.opcode.method == 0x0a
```

#### Write Requests

```wireshark
btatt.opcode.method == 0x12
```

### Show Only Packets with RSSI

```wireshark
btcommon.eir_ad.entry.device_name
```

### Useful Combined Filters

#### BLE ATT Traffic Only

```wireshark
btle && btatt
```

#### L2CAP + ATT

```wireshark
btl2cap && btatt
```

#### Exclude Empty Packets

```wireshark
!(btle.control_opcode)
```
