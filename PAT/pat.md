## Functional Ports:
```
PC0 - 
192.168.10.2 (ipv4)
255.255.255.0 (subnet)
10.0.0.0 (default gateway)

PC1 - 
192.168.10.3 (ipv4)
255.255.255.0 (subnet)
10.0.0.0 (default gateway)

Server0 - 
192.168.11.2 (ipv4)
255.255.255.0 (subnet)
10.0.0.0 (default gateway)
```
## Router0 Configuration Code (DTE) [Left Side with More Devices]: 
```
Router>
Router>en
Router#config terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#interface gi 0/0
Router(config-if)#ip address 192.168.10.1 255.255.255.0
Router(config-if)#no shutdown
Router(config-if)#
%LINK-5-CHANGED: Interface GigabitEthernet0/0, changed state to up
%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0, changed state to up
Router(config-if)#exit
Router(config)#
Router(config)#interface se 0/1/0
Router(config-if)#ip address 10.0.0.1 255.0.0.0
Router(config-if)#no shutdown
%LINK-5-CHANGED: Interface Serial0/1/0, changed state to down
Router(config-if)#
Router(config-if)#exit
Router(config)#
Router(config)#
Router(config)#
%LINK-5-CHANGED: Interface Serial0/1/0, changed state to up
%LINEPROTO-5-UPDOWN: Line protocol on Interface Serial0/1/0, changed state to up
Router(config)#
Router(config)#
Router(config)#router eigrp 3
Router(config-router)#network 192.168.10.0
Router(config-router)#network 10.0.0.0
Router(config-router)#exit
Router(config)#
Router(config)#
%DUAL-5-NBRCHANGE: IP-EIGRP 3: Neighbor 10.0.0.2 (Serial0/1/0) is up: new adjacency
Router(config)#
Router(config)#
Router(config)#
Router(config)#access-list 2 permit 192.168.10.0 0.0.0.255
Router(config)#
Router(config)#
Router(config)#
Router(config)#
Router(config)#
Router(config)#ip nat inside source list 2 interface se0/1/0 overload
Router(config)#
Router(config)#
Router(config)#
Router(config)#interface gi 0/0
Router(config-if)#ip nat inside
Router(config-if)#exit
Router(config)#
Router(config)#
Router(config)#interface se 0/1/0
Router(config-if)#ip nat outside
Router(config-if)#
Router(config-if)#exit
Router(config)#exit
Router#
%SYS-5-CONFIG_I: Configured from console by console
Router#
Router#show ip nat translations
Router#
Router#
Router#show ip nat translations
Pro  Inside global     Inside local       Outside local      Outside global
icmp 10.0.0.1:14       192.168.10.2:14    192.168.11.2:14    192.168.11.2:14
icmp 10.0.0.1:15       192.168.10.2:15    192.168.11.2:15    192.168.11.2:15
icmp 10.0.0.1:16       192.168.10.2:16    192.168.11.2:16    192.168.11.2:16
icmp 10.0.0.1:17       192.168.10.2:17    192.168.11.2:17    192.168.11.2:17
Router#
Router#
Router#
Router#show ip nat translations
Pro  Inside global     Inside local       Outside local      Outside global
tcp 10.0.0.1:1025      192.168.10.2:1025  192.168.11.2:80    192.168.11.2:80
Router#
```
## Router1 Configuration Code (DCE):
```
Router>
Router>en
Router#config terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#interface gi 0/0
Router(config-if)#ip address 192.168.11.1 255.0.0.0
Router(config-if)#no shutdown
Router(config-if)#
%LINK-5-CHANGED: Interface GigabitEthernet0/0, changed state to up
%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0, changed state to up
Router(config-if)#exit
Router(config)#
Router(config)#interface se 0/1/0
Router(config-if)#ip address 10.0.0.2 255.0.0.0
Router(config-if)#clock rate 64000
Router(config-if)#no shutdown
Router(config-if)#
%LINK-5-CHANGED: Interface Serial0/1/0, changed state to up
Router(config-if)#
Router(config-if)#exit
Router(config)#
%LINEPROTO-5-UPDOWN: Line protocol on Interface Serial0/1/0, changed state to up
Router(config)#
Router(config)#
Router(config)#
Router(config)#router eigrp 3
Router(config-router)#network 192.168.11.0
Router(config-router)#network 10.0.0.0
Router(config-router)#
%DUAL-5-NBRCHANGE: IP-EIGRP 3: Neighbor 10.0.0.1 (Serial0/1/0) is up: new adjacency
Router(config-router)#exit
Router(config)#
Router(config)#
```
