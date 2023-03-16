# uses DD-WRT firmware

### download


### 
https://forum.dd-wrt.com/phpBB2/viewtopic.php?p=410825
https://www.medo64.com/2012/02/ddwrt-on-wl330ge/

Once the WL330gE is running dd-wrt, you might notice that you are unable to find the wireless network 'dd-wrt'. dd-wrt has some slight issues with the asus WL-330gE's 1 ethernet port. dd-wrt's default settings will cause the wireless interface to be the router's WAN-port. This will cause problems.

1. Go to Setup > Networking > Port Setup and set WAN Port Assignment to 'Disabled'. Once these settings are applied you will find the wireless network 'dd-wrt'.
2. Setup your wireless netwerk. Set a ssid, and protect your network.

If you wish to use the ethernet port as a WAN-port:
3. Connect to this wireless netwerk and go to 
Setup > Networking > Port Setup and set WAN Port Assignment to 'eth0'. Once these settings are applied you may continue to configure your router using the wireless netwerk. The ethernet port was become the router's WAN-port.

```
nvram set wan_ifname=eth0
brctl delif br0 eth0
startservice wan
```

###
```
nvram get lan_hwaddr
nvram get wan_hwaddr
nvram get wl0_hwaddr
```
only last command gives response with MAC wl0_hwaddr 48:5B:39:E7:1D:B0, same as eth1
