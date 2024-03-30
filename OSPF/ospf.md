<img width="568" alt="image" src="https://github.com/TheCleverIdiott/Computer-Networks-Cisco-Packet-Tracer/assets/95587262/5bc4d415-513b-4054-a530-a1bf0a920793">


## Configuration Codes for Router 0 (DTE):

```
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
Router(config)#interface se 0/1/0
Router(config-if)#ip address 10.0.0.1 255.0.0.0
Router(config-if)#no shutdown

%LINK-5-CHANGED: Interface Serial0/1/0, changed state to down
Router(config-if)#exit
Router(config)#
%LINK-5-CHANGED: Interface Serial0/1/0, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface Serial0/1/0, changed state to up

Router(config)#
Router(config)#router ospf 2
Router(config-router)#network 192.168.10.0 0.0.0.255 area 1
Router(config-router)#network 10.0.0.0 255.255.255.255 area 1
Router(config-router)#exit
Router(config)#
00:06:19: %OSPF-5-ADJCHG: Process 2, Nbr 192.168.11.1 on Serial0/1/0 from LOADING to FULL, Loading Done
```


## Configuration Codes for Router 1 (DCE):
```
Router>en
Router#config terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#ip address 192.168.11.1 255.255.255.0
                   ^
% Invalid input detected at '^' marker.
	
Router(config)#interface gi 0/0
Router(config-if)#ip address 192.168.11.1 255.255.255.0
Router(config-if)#no shutdown

Router(config-if)#
%LINK-5-CHANGED: Interface GigabitEthernet0/0, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0, changed state to up

Router(config-if)#exit
Router(config)#interface se 0/1/0
Router(config-if)#ip address 10.0.0.2 255.0.0.0
Router(config-if)#no shutdown

Router(config-if)#
%LINK-5-CHANGED: Interface Serial0/1/0, changed state to up

Router(config-if)#exit
Router(config)#interfac
%LINEPROTO-5-UPDOWN: Line protocol on Interface Serial0/1/0, changed state to up
% Incomplete command.
Router(config)#
Router(config)#interface se 0/1/0
Router(config-if)#clock rate 64000
Router(config-if)#exit
Router(config)#
Router(config)#router ospf 3
Router(config-router)#network 192.168.11.0 0.0.0.255 area 1
Router(config-router)#network 10.0.0.0 255.255.255.255 area 1
Router(config-router)#
Router(config-router)#exit
Router(config)#
Router(config)#
00:06:14: %OSPF-5-ADJCHG: Process 3, Nbr 192.168.10.1 on Serial0/1/0 from LOADING to FULL, Loading Done
```
