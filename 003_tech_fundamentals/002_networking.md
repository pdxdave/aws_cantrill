# Networking

## OSI 7 layer model
|                  |
| ---------------  |
| 7 - Application  |
| ---------------  |
| 6 - Presentation |
| ---------------  |
| 5 - Session      |
| ---------------  |
| 4 - Transport    | 
| ---------------  |

|                  |
| ---------------  | 
| 3 - Networking   |
| ---------------  |
| 2 - Data Link    |
| ---------------  |
| 1 - Physical     |
| ---------------  |

1. Layers 1 - 3 are the ```media layers```. This is how data moves from point A to point B.
2. Layers 4 - 7 are the ```host layers```. This is how data is chopped up, readied for transport, and reassembled.
    * At the top you may have a web browser connected to a server
    * At the bottom you'll have network cards

## Layers
### 1 Physical
1. This is about voltage levels, distances, modulation and connectors. Imagine two computers connected with a LAN line, the physical shared medium.
2. This is how two NICs (that share the same standards) communicate at layer 1.
3. The problem with layer 1: errors and collisions. Why? Because the traffic is broadcasted. It would be like several people yelling at the same time.  There's no device addressing. 

### 2. Data Link
1. This runs over layer 1. 
2. Layer 2 introduces frames. A framework for sending data over a layer 2 network.
3. Every device on a network as a MAC address.  These are specific to the hardware (NIC), and are globally unique. 
4. A layer 2 frame can be transmitted onto the shared physical medium in layer 1.  It's converted into voltage, RF, or light wave across the medium and received by other devices.

| ---------------  | --------- |
| Preamble         | destination Mac Address |
| ---------------  | ----------- |
5. Frames - multiple parts
    * the first is the preamble. it lets other devices know it's the start of the frames. 
    * next is the destination MAC address and source MAC address.