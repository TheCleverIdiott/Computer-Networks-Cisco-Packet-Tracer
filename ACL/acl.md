<img width="758" alt="image" src="https://github.com/TheCleverIdiott/CN-Lab/assets/95587262/8eeaa9d7-88fa-4227-aeb2-2722032f6f6a">




## IP Configuration:
```
PC0 - 192.168.10.2 | 10.0.0.0
PC1 - 192.168.10.3 | 10.0.0.0
PC2 - 192.168.11.2 | 10.0.0.0
PC3 - 192.168.10.3 | 10.0.0.0
Server0 - 192.168.12.2 | 10.0.0.0
```

## Router0 Configuration Code:
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
Router(config)#interface gi 0/1
Router(config-if)#ip address 192.168.11.1 255.255.255.0
Router(config-if)#no shutdown

Router(config-if)#
%LINK-5-CHANGED: Interface GigabitEthernet0/1, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/1, changed state to up

Router(config-if)#exit
Router(config)#
Router(config)#interface se 0/1/0
Router(config-if)#ip address 10.0.0.1 255.0.0.0
Router(config-if)#clock rate 64000
Router(config-if)#no shutdown

%LINK-5-CHANGED: Interface Serial0/1/0, changed state to down
Router(config-if)#exit
Router(config)#
Router(config)#
%LINK-5-CHANGED: Interface Serial0/1/0, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface Serial0/1/0, changed state to up

Router(config)#
Router(config)#router eigrp 3
Router(config-router)#network 192.168.10.0
Router(config-router)#network 10.0.0.0
Router(config-router)#exit
Router(config)#
Router(config)#router eigrp 3
Router(config-router)#network 192.168.11.0
Router(config-router)#network 10.0.0.0
Router(config-router)#exit
Router(config)#
Router(config)#
%DUAL-5-NBRCHANGE: IP-EIGRP 3: Neighbor 10.0.0.2 (Serial0/1/0) is up: new adjacency

Router(config)#
Router(config)#
Router(config)#
Router(config)#config terminal
%Invalid hex value
Router(config)#exit
Router#
%SYS-5-CONFIG_I: Configured from console by console

Router#
Router#config terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#access-list 2 deny 192.168.10.0 0.0.0.255
Router(config)#access-list 2 permit any
Router(config)#interface se 0/1/0
Router(config-if)#ip access-group 2 out
Router(config-if)#
```
## Router1 Configuration Code:
```
Router>
Router>en
Router#config terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#interface gi 0/0
Router(config-if)#ip address 192.168.12.1 255.255.255.0
Router(config-if)#no shutdown

Router(config-if)#
%LINK-5-CHANGED: Interface GigabitEthernet0/0, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0, changed state to up

Router(config-if)#
Router(config-if)#exit
Router(config)#
Router(config)#interface se 0/1/0
Router(config-if)#ip address 10.0.0.2 255.0.0.0
Router(config-if)#no shutdown

Router(config-if)#
%LINK-5-CHANGED: Interface Serial0/1/0, changed state to up

Router(config-if)#
Router(config-if)#exit
Router(config)#
Router(config)#
%LINEPROTO-5-UPDOWN: Line protocol on Interface Serial0/1/0, changed state to up

Router(config)#
Router(config)#
Router(config)#router eigrp 3
Router(config-router)#network 192.168.12.0
Router(config-router)#network 10.0.0.0
Router(config-router)#
%DUAL-5-NBRCHANGE: IP-EIGRP 3: Neighbor 10.0.0.1 (Serial0/1/0) is up: new adjacency

Router(config-router)#exit
Router(config)#
Router(config)#access-list 112 deny tcp 192.168.10.0 0.0.0.255 192.168.12.2 0.0.0.0 eq 80
Router(config)#access-list 112 permit ip any any
Router(config)#interface gi 0/0
Router(config-if)#ip access-group 112 out
Router(config-if)#
```

## Result:
<img width="1556" alt="image" src="https://github.com/TheCleverIdiott/CN-Lab/assets/95587262/e389d73c-d2e7-4632-a1ac-a44caf749dc8">
