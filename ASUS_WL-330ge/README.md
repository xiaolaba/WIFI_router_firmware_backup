

ASUS official firmware  
WL-330gE 韌體版本2.0.2.0（英語/繁體中文/簡體中文/德語/日語/土耳其語）  
Version 2.0.2.0 2.97 MB  
2011/04/21  
新增支援土耳其語  
[WL-330gE_2.0.2.0_EN_TW_CN_DE_JP_TR.trx](WL-330gE_2.0.2.0_EN_TW_CN_DE_JP_TR.trx)  

enter resecue mode
1. hold the button
2. power up
3. power LED flash about 1sec interval

download [tftp64](https://pjo2.github.io/tftpd64/), uses [client] mode to [put] firmware to the wl-330ge
or uses ASUS tool, UT_WL330GE_1421. go to ASUS webpage downlod, or here local [UT_WL330GE_1421.zip](UT_WL330GE_1421.zip)  


following burn firmware
openwrt-15.05.1-brcm47xx-legacy-asus-wl-330ge-squashfs.trx, ok
lede-17.01.7-brcm47xx-legacy-asus-wl-330ge-squashfs.trx, ok
openwrt-18.06.4-brcm47xx-legacy-asus-wl-330ge-squashfs.trx, NG
openwrt-22.03.2-bcm47xx-legacy-asus_wl-330ge-squashfs.trx, NG
openwrt-22.03.3-bcm47xx-legacy-asus_wl-330ge-squashfs.trx, NG
openwrt-bcm47xx-legacy-asus_wl-330ge-squashfs.trx, NG




if uses UART dump terminal, will see tftp
```
CFE version 1.0.37 for BCM947XX (32bit,SP,LE)
Build Date: Fri Apr 11 15:23:32 CST 2008 (root@localhost.localdomain)
Copyright (C) 2000,2001,2002,2003 Broadcom Corporation.

Initializing Arena
Initializing Devices.
Boot partition size = 131072(0x20000)
et0: Broadcom BCM47xx 10/100 Mbps Ethernet Controller 4.130.31.0
CPU type 0x29029: 240MHz
Total memory: 16384 KBytes

Total memory used by CFE:  0x80400000 - 0x80497DD0 (622032)
Initialized Data:          0x8042F150 - 0x80431610 (9408)
BSS Area:                  0x80431610 - 0x80431DD0 (1984)
Local Heap:                0x80431DD0 - 0x80495DD0 (409600)
Stack Area:                0x80495DD0 - 0x80497DD0 (8192)
Text (code) segment:       0x80400000 - 0x8042F150 (192848)
Boot area (physical):      0x00498000 - 0x004D8000
Relocation Factor:         I:00000000 - D:00000000

Device eth0:  hwaddr xx-xx-xx-xx-xx-xx, ipaddr 192.168.1.220, mask 255.255.255.0
        gateway not set, nameserver not set
Null Rescue Flag.
Hello!! Enter Rescue Mode: (by Force)

Reading :: TFTP Server.
Failed.: Timeout occured

```




boot log

```
root@OpenWrt:~# dmesg
[    0.000000] Linux version 3.18.23 (buildbot@builder1) (gcc version 4.8.3 (OpenWrt/Linaro GCC 4.8-2014.04 r48532) ) #1 Tue Mar 1 09:18:44 CET 2016
[    0.000000] CPU0 revision is: 00029029 (Broadcom BMIPS3300)
[    0.000000] bcm47xx: Using ssb bus
[    0.000000] ssb: Found chip with id 0x5354, rev 0x03 and package 0x00
[    0.000000] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x14, vendor 0x4243)
[    0.000000] ssb: Core 1 found: Fast Ethernet (cc 0x806, rev 0x09, vendor 0x4243)
[    0.000000] ssb: Core 2 found: MIPS 3302 (cc 0x816, rev 0x08, vendor 0x4243)
[    0.000000] ssb: Core 3 found: USB 2.0 Host (cc 0x819, rev 0x02, vendor 0x4243)
[    0.000000] ssb: Core 4 found: MEMC SDRAM (cc 0x80F, rev 0x04, vendor 0x4243)
[    0.000000] ssb: Core 5 found: IEEE 802.11 (cc 0x812, rev 0x0D, vendor 0x4243)
[    0.000000] ssb: Core 6 found: Roboswitch (cc 0x81C, rev 0x02, vendor 0x4243)
[    0.000000] ssb: chipcommon status is 0x0
[    0.000000] ssb: Found rev 0 PMU (capabilities 0x04A63400)
[    0.000000] ssb: Initializing MIPS core...
[    0.000000] ssb: set_irq: core 0x0806, irq 4 => 4
[    0.000000] ssb: set_irq: core 0x0816, irq 5 => 2
[    0.000000] ssb: set_irq: core 0x0812, irq 2 => 5
[    0.000000] ssb: after irq reconfiguration
[    0.000000] ssb: core 0x0800, irq : 2(S)  3* 4  5  6  D  I
[    0.000000] ssb: core 0x0806, irq : 2(S)  3  4* 5  6  D  I
[    0.000000] ssb: core 0x0816, irq : 2(S)* 3  4  5  6  D  I
[    0.000000] ssb: core 0x0819, irq : 2(S)  3  4  5  6* D  I
[    0.000000] ssb: core 0x080f, irq : 2(S)  3  4  5  6  D  I*
[    0.000000] ssb: core 0x0812, irq : 2(S)  3  4  5* 6  D  I
[    0.000000] ssb: core 0x081c, irq : 2(S)  3  4  5  6  D  I*
[    0.000000] ssb: Sonics Silicon Backplane found at address 0x18000000
[    0.000000] Determined physical RAM map:
[    0.000000]  memory: 01000000 @ 00000000 (usable)
[    0.000000] Initrd not found or empty - disabling initrd
[    0.000000] Zone ranges:
[    0.000000]   Normal   [mem 0x00000000-0x00ffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00000000-0x00ffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x00ffffff]
[    0.000000] On node 0 totalpages: 4096
[    0.000000] free_area_init_node: node 0, pgdat 802e42f0, node_mem_map 80364000
[    0.000000]   Normal zone: 32 pages used for memmap
[    0.000000]   Normal zone: 0 pages reserved
[    0.000000]   Normal zone: 4096 pages, LIFO batch:0
[    0.000000] Primary instruction cache 16kB, VIPT, 4-way, linesize 16 bytes.
[    0.000000] Primary data cache 16kB, 2-way, VIPT, cache aliases, linesize 16 bytes
[    0.000000] pcpu-alloc: s0 r0 d32768 u32768 alloc=1*32768
[    0.000000] pcpu-alloc: [0] 0
[    0.000000] Built 1 zonelists in Zone order, mobility grouping off.  Total pages: 4064
[    0.000000] Kernel command line:  noinitrd console=ttyS0,115200
[    0.000000] PID hash table entries: 64 (order: -4, 256 bytes)
[    0.000000] Dentry cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Inode-cache hash table entries: 1024 (order: 0, 4096 bytes)
[    0.000000] Memory: 12712K/16384K available (2605K kernel code, 103K rwdata, 316K rodata, 164K init, 267K bss, 3672K reserved)
[    0.000000] NR_IRQS:128
[    0.000000] MIPS: machine is Asus WL330GE
[    0.060000] Calibrating delay loop... 239.61 BogoMIPS (lpj=1198080)
[    0.070000] pid_max: default: 32768 minimum: 301
[    0.070000] Mount-cache hash table entries: 1024 (order: 0, 4096 bytes)
[    0.070000] Mountpoint-cache hash table entries: 1024 (order: 0, 4096 bytes)
[    0.080000] NET: Registered protocol family 16
[    0.100000] Switched to clocksource MIPS
[    0.110000] NET: Registered protocol family 2
[    0.110000] TCP established hash table entries: 1024 (order: 0, 4096 bytes)
[    0.110000] TCP bind hash table entries: 1024 (order: 0, 4096 bytes)
[    0.110000] TCP: Hash tables configured (established 1024 bind 1024)
[    0.110000] TCP: reno registered
[    0.110000] UDP hash table entries: 256 (order: 0, 4096 bytes)
[    0.110000] UDP-Lite hash table entries: 256 (order: 0, 4096 bytes)
[    0.110000] NET: Registered protocol family 1
[    0.110000] PCI: CLS 0 bytes, default 16
[    0.120000] futex hash table entries: 256 (order: -1, 3072 bytes)
[    0.120000] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[    0.120000] jffs2: version 2.2 (NAND) (SUMMARY) (LZMA) (RTIME) (CMODE_PRIORITY) (c) 2001-2006 Red Hat, Inc.
[    0.120000] msgmni has been set to 24
[    0.120000] io scheduler noop registered
[    0.120000] io scheduler deadline registered (default)
[    0.130000] Serial: 8250/16550 driver, 16 ports, IRQ sharing enabled
[    0.140000] console [ttyS0] disabled
[    0.160000] serial8250.0: ttyS0 at MMIO 0xb8000300 (irq = 3, base_baud = 1562500) is a U6_16550A
[    0.440000] console [ttyS0] enabled
[    0.470000] serial8250.0: ttyS1 at MMIO 0xb8000400 (irq = 3, base_baud = 1562500) is a U6_16550A
[    0.480000] physmap platform flash device: 02000001 at 1c000000
[    0.490000] physmap-flash.0: Found 1 x16 devices at 0x0 in 16-bit bank. Manufacturer ID 0x0000c2 Chip ID 0x0022a8
[    0.500000] physmap-flash.0: Found an alias at 0x400000 for the chip at 0x0
[    0.500000] physmap-flash.0: Found an alias at 0x800000 for the chip at 0x0
[    0.500000] physmap-flash.0: Found an alias at 0xc00000 for the chip at 0x0
[    0.500000] physmap-flash.0: Found an alias at 0x1000000 for the chip at 0x0
[    0.500000] physmap-flash.0: Found an alias at 0x1400000 for the chip at 0x0
[    0.500000] physmap-flash.0: Found an alias at 0x1800000 for the chip at 0x0
[    0.500000] physmap-flash.0: Found an alias at 0x1c00000 for the chip at 0x0
[    0.500000] Amd/Fujitsu Extended Query Table at 0x0040
[    0.500000]   Amd/Fujitsu Extended Query version 1.1.
[    0.510000] number of CFI chips: 1
[    0.530000] 6 bcm47xxpart partitions found on MTD device physmap-flash.0
[    0.530000] Creating 6 MTD partitions on "physmap-flash.0":
[    0.540000] 0x000000000000-0x000000020000 : "boot"
[    0.550000] 0x000000020000-0x0000003f0000 : "firmware"
[    0.560000] 0x00000002001c-0x00000002090c : "loader"
[    0.560000] 0x00000002090c-0x000000126000 : "linux"
[    0.570000] 0x000000126000-0x0000003f0000 : "rootfs"
[    0.580000] mtd: device 4 (rootfs) set to be root filesystem
[    0.590000] 1 squashfs-split partitions found on MTD device rootfs
[    0.600000] 0x000000380000-0x0000003f0000 : "rootfs_data"
[    0.600000] 0x0000003f0000-0x000000400000 : "nvram"
[    0.720000] libphy: Fixed MDIO Bus: probed
[    0.730000] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
[    0.750000] libphy: b44_eth_mii: probed
[    0.850000] b53_common: found switch: BCM5325, rev 0
[    0.860000] b44 ssb0:0: attached PHY driver [Broadcom B53 (1)] (mii_bus:phy_addr=1:1e)
[    0.870000] b44 ssb0:0 eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 48:5b:39:e7:1d:ae
[    0.880000] bcm47xx-wdt bcm47xx-wdt.0: BCM47xx Watchdog Timer enabled (30 seconds, Software Timer)
[    0.890000] GPIO_WDT: failed to register misc device
[    0.890000] TCP: cubic registered
[    0.900000] NET: Registered protocol family 17
[    0.900000] bridge: automatic filtering via arp/ip/ip6tables has been deprecated. Update your scripts to load br_netfilter if you need this.
[    0.920000] Bridge firewalling registered
[    0.920000] 8021q: 802.1Q VLAN Support v1.8
[    0.940000] VFS: Mounted root (squashfs filesystem) readonly on device 31:4.
[    0.960000] Freeing unused kernel memory: 164K (802f7000 - 80320000)
[    2.490000] init: Console is alive
[    2.500000] init: - watchdog -
[    4.560000] init: - preinit -
[    5.060000] b44 ssb0:0 eth0: Link is up at 100 Mbps, half duplex
[    5.060000] b44 ssb0:0 eth0: Flow control is off for TX and off for RX
[    5.240000] random: procd urandom read with 8 bits of entropy available
[    6.990000] b44 ssb0:0 eth0: Link is Up - 100Mbps/Full - flow control off
[    8.910000] jffs2: notice: (228) jffs2_build_xattr_subsystem: complete building xattr subsystem, 0 of xdatum (0 unchecked, 0 orphan) and 0 of xref (0 dead, 0 orphan) found.
[    8.930000] mount_root: switching to jffs2 overlay
[    9.000000] b44 ssb0:0 eth0: powering down PHY
[    9.030000] procd: - early -
[    9.040000] procd: - watchdog -
[    9.970000] procd: - ubus -
[    9.990000] b44 ssb0:0 eth0: Link is Down
[   11.000000] procd: - init -
[   14.610000] NET: Registered protocol family 10
[   14.640000] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   14.680000] Loading modules backported from Linux version master-2015-03-09-0-g141f155
[   14.690000] Backport generated by backports.git backports-20150129-0-gdd4a670
[   14.710000] ip_tables: (C) 2000-2006 Netfilter Core Team
[   14.750000] nf_conntrack version 0.5.0 (201 buckets, 804 max)
[   14.870000] xt_time: kernel timezone is -0000
[   14.940000] cfg80211: Calling CRDA to update world regulatory domain
[   14.940000] cfg80211: World regulatory domain updated:
[   14.950000] cfg80211:  DFS Master region: unset
[   14.950000] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   14.960000] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   14.970000] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz, 92000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[   14.980000] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[   14.990000] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[   15.000000] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[   15.010000] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[   15.020000] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[   15.030000] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[   15.440000] PPP generic driver version 2.4.2
[   15.460000] NET: Registered protocol family 24
[   15.630000] b43-phy0: Broadcom 5354 WLAN found (core revision 13)
[   15.660000] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 0
[   15.670000] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2062, Revision 1, Version 0
[   15.690000] Broadcom 43xx driver loaded [ Features: PNL ]
[   15.780000] Broadcom 43xx-legacy driver loaded [ Features: PLD ]
[   15.820000] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   22.110000] b44 ssb0:0 eth0: Link is up at 100 Mbps, full duplex
[   22.110000] b44 ssb0:0 eth0: Flow control is off for TX and off for RX
[   23.200000] b44 ssb0:0 eth0: Link is Up - 100Mbps/Full - flow control off
[   34.780000] b44 ssb0:0 eth0: powering down PHY
[   34.820000] b44 ssb0:0 eth0: Link is up at 100 Mbps, full duplex
[   34.830000] b44 ssb0:0 eth0: Flow control is off for TX and off for RX
[   34.870000] device eth0.1 entered promiscuous mode
[   34.880000] device eth0 entered promiscuous mode
[   34.900000] br-lan: port 1(eth0.1) entered forwarding state
[   34.910000] br-lan: port 1(eth0.1) entered forwarding state
[   36.910000] br-lan: port 1(eth0.1) entered forwarding state
[   69.670000] random: nonblocking pool is initialized
root@OpenWrt:~#

```
