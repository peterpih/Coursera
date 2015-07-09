###Steps tp make **DLink DIR615** router to a repeater

IP address is at:
```
192.168.1.1
``
O2 router IP address:
``
192.168.1.254
```
###Setup | Basic Setup
- Wireless Setup
  + Connection Type: Disabled
-Router IP
  + Local IP Address: 192.168.1.1
  + Subnet Mask: 255.255.255.0
  + Gateway: 192.168.1.254
- WAN Port
  + Tick Assign WAN To Port Switch
  
###Wireless | Wireless Security
- Physical Address
  + Security Mode: WPA2 Personal Mixed
  + WPA Algorithms: TKIP+AES
  + WPA Shared Key: \<same key as the gateway router\>
-Virtual Address (add one)
  + Security Mode: WPA2 Personal Mixed
  + TKIP+AES
  + \<any password for entry to this router point\>
  
###Security | VPN Passthrough
- Disable everything since the Gateway will take care of it
