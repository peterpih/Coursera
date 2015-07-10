###Steps to make **DLink DIR615** router to a repeater

Gateway O2 router IP address:
```
192.168.1.254
```
Dlink IP address is at:
```
192.168.1.1
```
###Dlink GUI Menus

###Setup | Basic Setup
- Wireless Setup
  + Connection Type: Disabled
-Router IP
  + Local IP Address: 192.168.1.1
  + Subnet Mask: 255.255.255.0
  + Gateway: 192.168.1.254
- WAN Port
  + Tick Assign WAN To Port Switch

###Wireless
- Basic Setup
  + Wireless Mode: Client Bridge (routed)
  + Default GW Mode: Mixed
  + Channel Width: Full(20Mhz)
  + Wireless Neotwork Name (SSID): \<same as gateway\>
- Virtual Interfaces
  + Wireless Mode: WDS AP
  + Wireless Network Name (SSID): \<name to use this router, not gateway\>
  + Wireless SSID Broadcast: Enabled

###Wireless Security
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
