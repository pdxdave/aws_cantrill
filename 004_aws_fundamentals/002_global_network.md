# AWS Global Network

## Regions & Edge Locations
### Regions
1. A region to AWS doesn't map on to a continent or a country.  A region is ```a creation``` of AWS.  It's an area of the world they have selected and inside this region is a full deployment of AWS infrastructure.
    * Computers, storage, DB, AI, Analytics and more
    * AWS adds regions all the time.
    * Regions are geographically spread, so the network can withstand global area disasters.
    * When interacting with AWS you're actually interacting with a specific region.

### Edge Locations
1. Edge locations are much smaller than regions and they generally only have content distribution services as well as some type of edge computing. 
    * They are located in many more places than regions.
    * Edge locations are useful for clients who have to store their info as close as possible to their customers; for instance, Netflix.  This allows low latency and high speed distribution.  The further the distance, the slower speed, the higher the latency.
    * Example: Australia has a region location in Sydney, but an edge location in Melbourne to better handle all of the Melbourne demand. This results in lower latency and better delivery.