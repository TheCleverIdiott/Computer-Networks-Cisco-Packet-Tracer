<img width="633" alt="image" src="https://github.com/TheCleverIdiott/CN-Lab/assets/95587262/8badf2c1-4f5a-4f46-8952-4cfcee687919">


## IP Congihuration:
```
PC0 - 192.168.10.2 | 10.0.0.0
PC1 - 192.168.10.3 | 10.0.0.0
Server0 - 192.168.11.2 | 10.0.0.0
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
Router(config)#interface se 0/1/0
Router(config-if)#ip address 10.0.0.1 255.0.0.0
Router(config-if)#no shutdown

%LINK-5-CHANGED: Interface Serial0/1/0, changed state to down
Router(config-if)#exit
Router(config)#
%LINK-5-CHANGED: Interface Serial0/1/0, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface Serial0/1/0, changed state to up

Router(config)#
Router(config)#router eigrp 3
Router(config-router)#network 192.168.10.0
Router(config-router)#network 10.0.0.0
Router(config-router)#exit
Router(config)#
Router(config)#
%DUAL-5-NBRCHANGE: IP-EIGRP 3: Neighbor 10.0.0.2 (Serial0/1/0) is up: new adjacency

Router(config)#
Router(config)#ip nat inside source static 192.168.11.2 10.0.0.1	
Router(config)#interface gi 0/0
Router(config-if)#ip nat inside
Router(config-if)#exit
Router(config)#interface se 0/1/0
Router(config-if)#ip nat outside
Router(config-if)#exit
Router(config)#
Router(config)#
Router(config)#
Router(config)#exit
Router#
%SYS-5-CONFIG_I: Configured from console by console

Router#
Router#show ip nat translations
Pro  Inside global     Inside local       Outside local      Outside global
---  10.0.0.1          192.168.11.2       ---                ---

Router#
```
## Router1 Configuration Code:
```
Router>
Router>en
Router#config terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#interface gi 0/0
Router(config-if)#ip address 192.168.11.1 255.255.255.0
Router(config-if)#no shutdown

Router(config-if)#
%LINK-5-CHANGED: Interface GigabitEthernet0/0, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0, changed state to up

Router(config-if)#exit
Router(config)#interface se 0/1/0
Router(config-if)#ip address 10.0.0.2 255.0.0.0
Router(config-if)#clock rate 64000
Router(config-if)#no shutdown

Router(config-if)#
%LINK-5-CHANGED: Interface Serial0/1/0, changed state to up

Router(config-if)#exit
Router(config)#
%LINEPROTO-5-UPDOWN: Line protocol on Interface Serial0/1/0, changed state to up

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

