# Networking - Layer Three

## Two Separate LANs

1. L3 needs one or more operational L2 networks to function.
2. Its role is to get data from one location to another.
![network_04](../assets/network_04.png)
3. We have separate LANs. One on the east coast, one on the west coast, and some inbetween.
4. They use ```different layer 2 protocols```.  LANs often use ethernet, but long distance points may use PPP/MPLS/ATM.
5. The importance of L2 -> ```Layer 2 moves frames from a local source to a local destination```
6. The importances of L3 -> ```Layer 3 is a common protocal that span multiple different layer 2 networks.``` 
![network_05](../assets/network_05.png)
7. L3 can be added to one or more L2 networks.
8. L3 adds the Internet Protocol: IP addresses you can assign to devices for communicating across networks using routing.
9. IP packets are moved from source to destination across the Internet through many intermediate networks. 
10. Routers (L3 devices) move packets of data across different networks.  They ecapsulate a packet inside of an ethernet frame for that part of the journey over that local network.
11. Ecapsulation just means that an IP packet is put inside an ethernet frame for that part of the journey.  When it needs to be moved into an new network that particular frame is removed and a new one is added around the same packet and it's moved onto the next local network.


## Packets - The data unit used within the IP
1. Packets are similar to frames. They contain some data to be moved and they have a source/destination address.
2. The diff is that packet source/destination addresses could be on the opposite sides of the planet, not local.
3. Packets remain the same during their journey. As they move along layer 2 networks they are placed inside frames (encapsulation).
4. The frame is specific to the local network the packet is moving through and changes everytime the packet moves between networks.  The packet itself doesn't normally change.

## Two versions of the Internet Protocol. Packet Structure

 ![network_06](../assets/network_06.png)
 1. v4
 * The v4 protocol. The IP is L3 and it contains data provided by a L4 protocol. It stores which protocol is used.  Examples would be like ICMP (value 1), TCP (value 6), UDP (value 17). This L3 layer will know which L4 protocol to pass the data into.
 * The data is provided by a L4 protocol.
 * TTL or Time To Live. This defines the max number of hops a packet can take to get to its destination.  If it exceeds them, it can be discarded. 
 * A single packet may exist in several frames throughout its route to get to its destination.  One for every L2 point to point link.    

 2. v6
 * Hop Limit is like Time To Live


 ## IP Addressing - v4
 ![network_07](../assets/network_07.png)
 * If the network component of the two IP addresses match, the devices are local.  If not, they are remote.


 ## Subnet Mask
 * It's the subnet mask which allows a HOST to determine if an IP address it needs to commicate with is local or remote - which influences if it needs to use a gateway or can communicate locally.
 * They are configured on L3 interfaces along with IP addresses. 
 * A default gateway is also configured on most interfaces.  This is an IP address on the local network which packets are forwarded to generally if the intended destination is not a local IP address.
 * Subnet masks are what allow an IP to know if an IP address it needs to communicate with is on the same network or not. This influences if a device attempts to communicate directly on the local network or if it needs to use the default gateway.
 * Default Gateway Example: My Internet router is my default gateway.  When I go to Netflex or interact with AWS, because the IP addresses I'm interacting with are not local, then packets from my computer are passed to the router/default gateway.

 | IP address | 133.33.3.7 |
 | ---------  | ---------- |
 | binary | 10000101 00100001 00000011 00000111 |

 | Subnet ---   | 255.255.0.0 |
 | ---------    | ---------- |
 | binary | 11111111 11111111 00000000 00000000 |    

 * /16 is the same as saying sixteen 1's.  It means the first two octets are the network.
 * When the subnet mask is in binary, anything with 1 represents the network, anything with 0's is the host computer. 
 
* In this example the ```start``` of the network is ```133.33.0.0```.  Why? The first two octets of the subnet are all 1's. The last two octects are all 0's. 
* The end is 133.33.255.255.  Why? The last two subnet octets don't have 1s in it. This leaves the ranges for the last to octets to have ranges up to 255.  So the range is from 133.33.0.0 to 133.33.255.255

## Route Tables & Routes

![network_08](../assets/network_08.png)

* The route that is selected, the top one, has a next route or target field.  It has the IP address the packet is to be forwarded to.  The packet is forwarded to 52.217.13.0/24. Routing is the process by which packets hop across the internet from source to destination.  Route tables enable this.
* !important. When the ISP router is forwarding the packet through to the AWS router, it is forwarding it at L2. It wraps the packet in a frame. It doesn't change.  The frame though as the AWS Mac Address as its destination.  That's how the packet gets to the AWS router.  How do we determine the Mac Address of the AWS router? That would be through the ```address resolution protocol```.

## Address Resolution Protocol

1. This is generally used when you have a L3 packet and you want to encapsolate it inside a frame and then send that frame to a Mac Address.  You don't initially know the Mac Address and you need a protocol that can find the Mac Address for a given IP address. 
2. ARP will give you the Mac Address for a given IP address.
![network_09](../assets/network_09.png)

### An example NOT using a local network
1. D2 uses the subnet mask to compare its IP address to the destination address to learn that D3 is not on the same network.
    * It then creates a packet P2, which has the D3 destination IP address. It wraps it up in a frame called F2. Because D3 is remote, it knows that it has to use the default gateway as a router.  So for the destination mac address of F2, it uses the ARP to get the mac address of the local router R1.
    * So the packet P2 is addressed to the laptop D3.  The frame F2 is now addressed to the router R1.
    * R1 will see that the mac address is addressed to itself, so it will strip away the frame just leaving the packet P2.
    * R1 reviews the destination of packet P2, it sees that it's destined for laptop D3. R1 has a route for D3 in its route table. It knows anything for the pink network, router R2 should be the next hop.
    * It takes packet P2 and encapsulates it in a new frame F3.  The destination mac address of this frame is the router R2, and gets it using ARP.
    * It now sends it off as the next hop to router R2.  R2 accepts the frame and removes the frame around P2.
    * R2 confirms the destination IP address of P2 is on the same network and uses ARP to get the mac address of D3. It then encapsulates the packet P2 in a new frame F4, whose destination mac address is that of D3.
    * D3 receives the frame, it sees it is the intended destination of the frame (the mac addresses match), it strips off the frame, it strips off the packet and the data inside is available. 
    
![network_13](../assets/network_13.png)

## L3 review
![network_10](../assets/network_10.png)