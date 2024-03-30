<img width="313" alt="image" src="https://github.com/TheCleverIdiott/Computer-Networks-Cisco-Packet-Tracer/assets/95587262/910c7976-3b56-4665-b399-7966665854ff">



```
Press RETURN to get started!
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
Router(config)#ip dhcp pool a
Router(dhcp-config)#network 192.168.10.0 255.255.255.0
Router(dhcp-config)#default-router 192.168.10.1
Router(dhcp-config)#dns 8.8.8.8
Router(dhcp-config)#exit
Router(config)#


```
