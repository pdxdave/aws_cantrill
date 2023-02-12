# Cloud Computing Fundamentals

## The parts of cloud computing
1. On-demand self-service. Meaning, can provision capabilities (e.g., virtual machines, databases, storage, networking) as needed w/o having to notify anyone.  You can use a CLI or API for access.
2. Broad network access.  Meaning, capabilities are availble over the network and accessed through standard mechanisms (http, https, ssh, remote desktop, or maybe a VPN).  If you have to go to a vendor facility, it's probably not cloud.
3. Resource pooling. A sense of location independence. No control or knowledge of the exact location of the resources. Resources are pooled (memory, storage, cpu's) to server multiple consumers using a multi-tenant model.
4. Rapid elasticity. Capabilities can be elastically provisioned and released to scale rapidly outward and inward with demand.  To consumers, the capabilities available for provisioning often appear to be unlimited.
5. Measured service. Resources usage can be monitored, controlled, reported and billed.


## Public vs Private vs Hybrid vs Multi Cloud
1. AWS, Azure and Google all offer public clouds.  They meet the five above requirements.
2. You can combine cloud platforms, known as ```multi-cloud```.
3. You could mirror the platforms.  If one fails the other takes over.
    * Will require a 3rd party tool, and it's possible two plaforms don't offer exactly the same services. A problem.
    * Better to have each platform handle different aspects rather than try to mirror them.
4. ```AWS Outposts``` a Private Cloude On-Premisses.  Dedicated to a business and run on business premisses. 
    * A private cloud still needs to meet the 5 characteristics. 
5. Hybrid cloud is a public and private cloud working together.  Meets the 5 requirements.
    * It's not hybrid if you use AWS public with your on-site equipment.
6. A hybrid environment is AWS public with your on-site equipment.     

| Public Cloud | Private Cloud| Multi Cloud | Hybrid Cloud |
| ------------ | ------------ | ------------| ------------ |