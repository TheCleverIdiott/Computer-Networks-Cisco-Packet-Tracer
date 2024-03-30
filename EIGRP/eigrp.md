<img width="753" alt="image" src="https://github.com/TheCleverIdiott/Computer-Networks-Cisco-Packet-Tracer/assets/95587262/7ffc86dc-2238-42e6-bf75-2bc5f2a42462">


## IP Congiguration:
```
PC0 - 192.168.10.2 | 10.0.0.0
PC1 - 192.168.10.3 | 10.0.0.0
PC2 - 192.168.11.2 | 10.0.0.0
PC3 - 192.168.11.3 | 10.0.0.0
```

## Router0 Configuration Code (DTE):
```
Router>
Router>en
Router#config terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#int gi 0/0
Router(config-if)#ip add 192.168.10.1 255.255.255.0
Router(config-if)#no shutdown

Router(config-if)#
%LINK-5-CHANGED: Interface GigabitEthernet0/0, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0, changed state to up

Router(config-if)#ex
Router(config)#int se 0/1/0
Router(config-if)#ip add 10.0.0.1 255.0.0.0
Router(config-if)#no shut

%LINK-5-CHANGED: Interface Serial0/1/0, changed state to down
Router(config-if)#
Router(config-if)#ex
Router(config)#
%LINK-5-CHANGED: Interface Serial0/1/0, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface Serial0/1/0, changed state to up

Router(config)#
Router(config)#router eigrp 3
Router(config-router)#network 192.168.10.0
Router(config-router)#network 10.0.0.0
Router(config-router)#ex
Router(config)#
%DUAL-5-NBRCHANGE: IP-EIGRP 3: Neighbor 10.0.0.2 (Serial0/1/0) is up: new adjacency

Router(config)#
```

## Router1 Configuration Code (DCE):
```
Router>
Router>en
Router#config t
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#int gi 0/0
Router(config-if)#ip add 192.168.11.1 255.255.255.0
Router(config-if)#no shut

Router(config-if)#
%LINK-5-CHANGED: Interface GigabitEthernet0/0, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0, changed state to up

Router(config-if)#ex
Router(config)#int se 0/1/0
Router(config-if)#ip add 10.0.0.2 255.0.0.0
Router(config-if)#clock rate 64000
Router(config-if)#no shut

Router(config-if)#
%LINK-5-CHANGED: Interface Serial0/1/0, changed state to up

Router(config-if)#ex
Router(config)#
Router(config)#
%LINEPROTO-5-UPDOWN: Line protocol on Interface Serial0/1/0, changed state to up

Router(config)#
Router(config)#router eigrp 3
Router(config-router)#network 192.168.11.0
Router(config-router)#network 10.0.0.0
Router(config-router)#
%DUAL-5-NBRCHANGE: IP-EIGRP 3: Neighbor 10.0.0.1 (Serial0/1/0) is up: new adjacency

Router(config-router)#
Router(config-router)#ex
Router(config)#
```
