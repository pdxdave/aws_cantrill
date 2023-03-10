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
4. ```AWS Outposts``` a Private Cloude On-Premises.  Dedicated to a business and run on business premises. 
    * A private cloud still needs to meet the 5 characteristics. 
5. Hybrid cloud is a public and private cloud working together.  Meets the 5 requirements.
    * It's not hybrid if you use AWS public with your on-site equipment.
6. A hybrid environment is AWS public with your on-site equipment.     

| Public Cloud | Private Cloud| Multi Cloud | Hybrid Cloud | Hybrid Environment |
| ------------ | ------------ | ------------| ------------ | ------------------ |
|  1 public    | on-premises  |  using more |  public and  | public cloud w/    |
|   cloud      |  real cloud  |    than 1   | private cloud| legacy on-premises |
|              |              | public cloud| not public w |
|              |              |             |legacy on-site|


## Service Models
1. Infrastructure stack (IS). The IS is a collection of things that an application needs that stack on top of each other.

| 9 Application    | the application itself            |
| -----------      | --------------------------------- |
| 8 Data           | creates or consumes               |
| -----------      | --------------------------------- |
| 7 Runtime        | Python, Java, JS, C, C++, etc     |
| -----------      | --------------------------------- |
| 6 Container      | Docker                            |
| -----------      | --------------------------------- |
| 5 OS             | Linux, Windows                    |
| -----------      | --------------------------------- |
| 4 Virtualization | severs running vm's               |
| -----------      | --------------------------------- |
| 3 Servers        | 1 or more servers                 |
| -----------      | ----------------------------------|
| 2 Infrastructure | storage, networking               |
| -----------      | --------------------------------- |
| 1 Facilities     | bulding, power, physical security |
| -----------      | --------------------------------- |

2. Unit of consumption. It's what you use and pay for. From that point in the stack upward, you are responsible for management. This is what makes each service different.

| On-Premises  | DC Hosted    | IaaS        | PaaS         | SaaS               |
| ------------ | ------------ | ------------| ------------ | ------------------ |
| Responsible  | rent sever   | vender mgns |  vender mgns | vender mgns it.    |
| for all if it|  in data     |   1 to 4.   |   1 to 6.    |    you consume 9   |
|              |  center.     | you consume | you consume  |                    |
|              | consumption  |  and mng 5  |  and mgn 7   |                    |
|              | is 1         |    and up   |  and up      |                    |