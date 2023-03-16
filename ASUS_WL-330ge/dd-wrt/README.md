# uses DD-WRT firmware

### download firmwares
https://dd-wrt.com/support/router-database/?model=WL-330gE_-

### uses this firmware for testing  
note, version info displayed was wrong with "vpn"
https://download1.dd-wrt.com/dd-wrtv2/downloads/betas/2020/11-03-2020-r44715/broadcom/dd-wrt.v24_std_generic.bin


ok, netgear orbi router is not supporting bcm wifi card, real slow, this old router is better performance, but why ?  
![firmware_download_2023-03-16/2023-03-16_upgrade_ok.JPG](firmware_download_2023-03-16/2023-03-16_upgrade_ok.JPG)
![firmware_download_2023-03-16/speedtest.JPG](firmware_download_2023-03-16/speedtest.JPG)


### how to make it work to connect to internet
https://forum.dd-wrt.com/phpBB2/viewtopic.php?p=410825  
https://www.medo64.com/2012/02/ddwrt-on-wl330ge/  

Once the WL330gE is running dd-wrt, you might notice that you are unable to find the wireless network 'dd-wrt'. dd-wrt has some slight issues with the asus WL-330gE's 1 ethernet port. dd-wrt's default settings will cause the wireless interface to be the router's WAN-port. This will cause problems.

1. Go to Setup > Networking > Port Setup and set WAN Port Assignment to 'Disabled'. Once these settings are applied you will find the wireless network 'dd-wrt'.
2. Setup your wireless netwerk. Set a ssid, and protect your network.

If you wish to use the ethernet port as a WAN-port:
3. Connect to this wireless netwerk and go to 
Setup > Networking > Port Setup and set WAN Port Assignment to 'eth0'. Once these settings are applied you may continue to configure your router using the wireless netwerk. The ethernet port was become the router's WAN-port.

### this made it works, ISP assign static IP, no uses PPPoE  
login router, click tabs,  
```
Setup > Networking > Port Setup and set WAN Port Assignment to 'eth0'  
```

Administration > Command start-up script then save /run, reboot device  
```
nvram set wan_ifname=eth0
brctl delif br0 eth0
startservice wan
```

### try some test
```
nvram get lan_hwaddr
nvram get wan_hwaddr
nvram get wl0_hwaddr
```
only last command gives response with MAC wl0_hwaddr 48:5B:39:E7:1D:B0, same as eth1


### version used DD-WRT v3.0-r44715 vpn (11/03/20)
```
DD-WRT v3.0-r44715 vpn (11/03/20)

There are several different distributions of the DD-WRT firmware. 
The mini contains all the features of the standard distribution,with the exception of chillispot, nocat, rflow, kaid, CIFS client, SNMP, IPv6, and MMC/SD card support. 

The standard (std) distribution includes all features, with the exception of VOIP. 

The standard-nokaid (std-nokaid) distribution includes all features of standard, with kaid removed to free some flash space.

The VOIP distribution includes all features, with kaid removed to make room for Milkfish.

The VPN edition includes OpenVPN but does not include IPv6, CIFS client, or kaid.

The micro edition is a stripped down version designed for the WRT54G v5 and other 2MB router models.
```
