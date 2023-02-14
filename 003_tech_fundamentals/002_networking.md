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
1. Two computers using NICs, connected by a shared physical medium (copper cable). This is a broadcast use case as there are no IP addresses. !Problem. If two devices transmit at the same time there could be a collision. There's no way to control access control, so collisions happen. Terrible scaling in layer 1 networks.    

### 2. Data Link
1. This runs over a functional layer 1. 
2. Layer 2 uses MAC addresses and sends data in frames. Frames can be addressed to specific locations or broadcast.