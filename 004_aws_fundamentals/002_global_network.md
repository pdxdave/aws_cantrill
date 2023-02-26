# AWS Global Network

## Regions & Edge Locations
### Regions
1. A region to AWS doesn't map on to a continent or a country.  A region is ```a creation``` of AWS.  It's an area of the world they have selected and inside this region is a full deployment of AWS infrastructure.
    * Computers, storage, DB, AI, Analytics and more
    * AWS adds regions all the time.
    * Regions are geographically spread, so the network can withstand global area disasters.
    * When interacting with AWS you're actually interacting with a specific region.
    * Regions have three main benefits.
        1. Geographic separation - isolated fault domain
        2. Geopolitical Separation - governed by laws of that region. a side note, you have to explicitly tell AWS if you want your data to move between regions.
        3. Location control - tune for performance
    * When referring to a region you do it one of two ways. 
        1. Region code ap-southeast-2  - cli or api
        2. Region name Asian Pacific (Sydney) - console ui
    * Resiliance
        1. If you have infrastructure in Sydney and a mirror in Northern VA, if Sydney blows up, N.VA will be OK.
            * Globally Resilient Services: A service operates globally with a single database.  Only a few services do this. IAM, Route53
            * Region Resilient: Services that operate in a single region with one set of data. They operate as separate services in each region. They generally replicate data from multiple AZ's in that region.  In an AZ fails, the service can continue.  If the Region as a whole fails, then the service fails.
            * AZ Resilient Services: These are services that are run from a single AZ. The the service in that AZ fails, then the service will fail. As a SAA we need to know about AWS services whether it's global, region, or AZ resilient.


### Edge Locations
1. Edge locations are much smaller than regions and they generally only have content distribution services as well as some type of edge computing. 
    * They are located in many more places than regions.
    * Edge locations are useful for clients who have to store their info as close as possible to their customers; for instance, Netflix.  This allows low latency and high speed distribution.  The further the distance, the slower speed, the higher the latency.
    * Example: Australia has a region location in Sydney, but an edge location in Melbourne to better handle all of the Melbourne demand. This results in lower latency and better delivery.
    * There are fewer regions than edge locations.
    * !! With EC2 you have to pick a region. Some services like IAM and Route53 are Global.

### Availability Zones
1. A lower level architecture available within AWS 
2. Take Sydney as an eample: ap-southeast-2. Inside every Region AWS provides multiple AZ's.  It could be 2 or up to 6
    * Sydney has ap-southeast-2a, ap-southeast-2b, ap-southeast-2c
    * With AZ's you are given isolated infrastructures within a region
    * isloated storage, networking, computing, power and facilities
    * in this case if 2a were taken out, 2b and 2c could still offer services provided they are setup that way (e.g., EC2's set up there).
    * As a SA you can design solutions that span across many AZ's.
    * AZ's are not data centers. It could be one of many. 
    * Services can be put across multiple AZ's. 