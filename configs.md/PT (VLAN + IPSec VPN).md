VLAN setup in main

\-- to demonstrate interVLAN connection with router-on-a-stick first four departments are made: Mgmt, HR, IT, and Sales, with a PC to represent each department

\-- in the switch, interfaces fa0/1-fa0/5 are changed to state up using **no shutdown command**

\-- VLANs 10, 20, 30, and 40 are created and named for the four departments listed, respectively

\-- assign the appropriate port to each VLAN with the following commands: **interface \_\_, switchport mode access, switchport access for VLAN \_\_**

\-- on the switch set the switchport mode to trunk for the interface that's connected to the router

\-- configure router on a stick by first, bringing up the interface, then using creating the subinterfaces with the command **interface \_\_, encapsulation dot1Q \_\_,** and **ip address (IP) (Subnet Mask)**

\-- configure PCs by assigning IP, subnet, and gateway

\-- test connectivity 





IPsec VPN tunnel

\-- determine if the router supports encrypted communication

\-- use the **show version** command to check if security is enabled

\-- since disabled in this case, for the router to support IPsec, a license activation command to enable the security k9 feature will need to be implemented

\-- with **license boot module c2900 technology-package securityk9** command

\-- save the config with **copy run start**

\-- **reload** router

\-- **show version** after reload and it results in security k9 being enabled under evaluation (just means features are available for testing without permanent license)

\-- configure static routes in R1 (Main Router) and R3 (Remote Router) pointing towards R2 (ISP Router) with command **ip route 0.0.0.0 0.0.0.0 209.165.200.2** and **ip route 0.0.0.0 0.0.0.0 209.165.200.5**, respectively

\-- implement ACL in main site router with **access-list \_\_ permit ip (inside local IP + wildcard mask at main site) (inside local IP + wildcard mask at remote site)**

\-- implement ACL in remote site router with **access-list \_\_ permit ip (inside local IP + wildcard mask at remote site) (inside local IP + wildcard mask at main site)**

\-- phase 1 on both routers to set ISAKMP policy with commands **crypto isakmp policy 10, encryption aes 256, authentication pre-share, group 5** so that encryption type, methos of authentication, and key exchange groups match

\-- to implement the authentication that pairs with ISAKMP policy, on the main router insert command **crypto isakmp key \_\_ address (outside local IP of remote site router)**

\-- on the remote router insert command **crypto isakmp key \_\_ address (outside local IP of main site router)**

\-- moving onto phase 2 where we decide how data will be encrypted and identified with command **crypto ipsec transform-set \_\_ esp-aes 256 esp-sha-hmac** on both routers

\-- in the next sequence of code cryto map will be set to establish an entry, define peer, enable pfs, the transform set, tunnel lifetime, and matching ACL that was created 

\-- the commands are **crypto map \_\_ \_\_ ipsec-isakmp, set peer \_\_, set pfs group5, set security-association lifetime seconds 86400, set transform-set \_\_, match address \_\_** to be set on both the main and remote routers

\-- attach the crypto map to both outside local interfaces with the command **interface (outside local interface of main/remote site), crypto map \_\_**

\-- test connectivity





