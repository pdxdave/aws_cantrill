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
3. Every device on a network has a MAC address.  These are specific to the hardware (NIC), and are globally unique. 
4. A layer 2 frame can be transmitted onto the shared physical medium in layer 1.  It's converted into voltage, RF, or light wave across the medium and received by other devices.

     
| 1 Preamble | 2 destination Mac Address | 3 source Mac Address | 4 ET 16 bits | 5 Payload 46 - 15000 bytes | // | check |

5. Frames - multiple parts
    * 1 is the preamble. It lets other devices know it's the start of the frames. 
    * 2 & 3 are the destination/source MAC address. the packet can be sent to a specific MAC address, or ff:ff:ff if for a global destination. 
    * 4 is the EtherType. This is SUPER FUCKING important. The EtherType decides which layer 3 protocal (e.g., IP) is putting its data inside a frame.
    * parts 2, 3 and 4 are the ```Mac Header```. They indicate the destination, source, and ET. 
    * part 5 is the payload. The ET (EtherType) defines which L3 protocal it uses (e.g., IP). This process is called encapsulation.  The payload is put into the Eathernet frame & delivered to a different layer 2 destination (e.g., another computer), analyized, the layer 3 packet is extracted and given back to layer 3 at the destination side.
    * At the end is the check sequence to make sure no errors occured.

### Data Like Part Two
1. Assume we have two computers with known NIC addresses between them  
2. Comp A packages up a frame of data. Before sending it checks for a carrier signal on the network, via CSMA (Carrier Sense Multiple Access). If none is detected, it passes the frame to layer 1.
![network_01](../assets/network_01.png)
3. The raw data is converted to 1s and 0s in layer 1 and then goes to Comp B where it reviews the destination mac address
4. What if Comp B wants to send at the same time?  To avoid a collision it looks for ```carrier dectected```. If one is, it waits.
![network_02](../assets/network_02.png)
5. What if both sides don't detect traffic then send at the same time? A collision could accure and that's what collision detection is for. This is part of layer 2.  A collision is detected, a jam signal is sent by all the devices that detect it, and a ```random backoff``` occurs. No device will attempt a transmission.
![network_03](../assets/network_03.png)
6. Hubs behave like layer 1. They don't detect collisions. A switch is a layer 2 device, so should help. They understand MAC addresses and have a MAC address table which starts off empty.  It learns which devices are connected and populates the Mac address table.
    