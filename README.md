# DHCP

<h2>Description</h2>
Configure DHCP server on R2 and client on R1. Verify results.

<h2>Environments Used </h2>

- <b>Cisco Packet Tracer</b> (2.2.43) <br />

- <b>Cisco IOS C2900 Software Version 15.1(4)M5<br />

<h2>Diagram </h2>
<img src="https://i.imgur.com/HU6IKen.png" height="80%" width="80%" />

<h2>Walk-through:</h2>
Configure R2 with DHCP server: reserved IP address ranges and 3 pools for 3 network areas.<br />
R2(config)#ip dhcp excluded-address 192.168.1.1 192.168.1.10<br />
R2(config)#ip dhcp excluded-address 192.168.2.1 192.168.2.10<br />
R2(config)#ip dhcp excluded-address 203.0.113.1<br />
R2(config)#ip dhcp pool POOL1<br />
R2(dhcp-config)#network 192.168.1.0 255.255.255.0<br />
R2(dhcp-config)#dns-server 8.8.8.8<br />
R2(dhcp-config)#domain-name corpdormain.com<br />
R2(dhcp-config)#default-router 192.168.1.1<br />
R2(dhcp-config)#ip dhcp pool POOL2<br />
R2(dhcp-config)#network 192.168.2.0 255.255.255.0<br />
R2(dhcp-config)#dns-server 8.8.8.8<br />
R2(dhcp-config)#domain-name corpdomain.com<br />
R2(dhcp-config)#default-router 192.168.2.1<br />
R2(dhcp-config)#ip dhcp pool POOL3<br />
R2(dhcp-config)#network 203.0.113.0 255.255.255.252<br />
R2(dhcp-config)#dns-server 8.8.8.8<br />
R2(dhcp-config)#domain-name corpdomain.com<br />
<img src="https://i.imgur.com/BNJfP2O.png" height="80%" width="80%" /> <br />
<br />
<br />
Configure R1 with a DHCP client interface POOL3 and as a DHCP relay agent for POOL1. <br />
R1(config)#int g0/0<br />
R1(config-if)#ip address dhcp<br />
R1(config)#int g0/1<br />
R1(config-if)#ip helper-address 203.0.113.1<br />
<img src="https://i.imgur.com/tSJKHgo.png" height="80%" width="80%" /> <br />
<img src="https://i.imgur.com/4WSFS6S.png" height="80%" width="80%" /> <br />
<img src="https://i.imgur.com/btuHQ2Y.png" height="80%" width="80%" /> <br />

