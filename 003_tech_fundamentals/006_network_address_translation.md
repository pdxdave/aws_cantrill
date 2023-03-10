# Network Address Translation
NAT is a fundamental technology used in computer networking to allow multiple devices to share a single public IP address. This is essential for businesses and individuals who have more devices than available public IP addresses.
![network_17](../assets/network_17.png)
## Static NAT
1. The router or NAT device maintains a NAT table.  It stores a 1:1 table between public and private IPs.    

|private   |public     |
|----------|---------- |
|10.0.0.42 |52.95.36.67|

2. The same works if the server wants to connect to the CatAPI. The server sends a package with its source of 10.0.0.10, goes to the NAT, checks the table, finds a match with 52.95.36.68, and continues to the CatAPI.
3. The CatAPI sends back a package with its source of CATAPI and destination of 52.95.36.68, goes to the NAT, finds a match with 10.0.0.10 in the table, and proceeds to the server.    

![network_18](../assets/network_18.png)
## Dynamic NAT
1. This type of NAT is used when you have less Public IP addresses than Private IP addresses, but when all of those Private  IP's need public access at some time.    
2. In this example we have four private IP addresses and two public. 
3. In the diagram, 10.0.0.42 sends a packet along with its sourse and destination IP addresses.  It goes to the router and sees if it has a current allocation of public addresses from the pool. If it's not currently using one and one is available, one will be dynamically created.  In this case 52.95.36.66.  This is a temporary basis. 
4. When the previous one is done, 10.0.0.44 can go through the same process and use 52.95.36.66 because it was freed up.

![network_19](../assets/network_19.png)

## Port Address Translation PAT
1. This is the type of NAT you use on your home network. PAT is what allows a large number of devices to share one public address. It's how the AWS NAT Gateway functions w/in the AWS environment. It has a many:one mapping architecture.
2. Src port: 32768 is a randomly assigned ephemeral port. Notice how the NAT device changes the Src port number to 1337. It puts that number into a NAT table. 

![network_20](../assets/network_20.png)