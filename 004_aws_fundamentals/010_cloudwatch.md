# Cloud Watch
It is a support service used by almost all other AWS services. 

It performs three main jobs:
1. It collects and manages operational data on your behalf.  
2. Any data about an environment by detailing how it performs, how it normally runs.
3. Or any logging data that it generates.

## Three products in one
1. Metrics: it allows the collection of metrics, monitoring of metrics and actions based on metrics
    * Metrics are simply data relating to AWS Products, Apps, and on-premises systems.  For example, CPU uses of EC2 instances, disc space useage for on-premises servers, or maybe the number of visiters per second to a website.
    * CW is a public service so it can be used for metric gathering, either inside AWS, within on-premises environments, or even within other cloud platforms. If you have a public Inet connection and permissions to add data to CW, it can be used from almost anywhere. 
    * One aspect of CW that you'll need to learn pretty quickly is that some metrics are gathered natively by the product. So generally, anything running in AWS, anything which is visible from within a product can be handled natively. For example, looking at CPU utilization on an EC2 instance, that's done by default. Also monintoring other things inside products which aren't exposed to AWS needs the AWS Agent. For example, if you want to monitor which processes are running on an EC2 instance, or the memory untilization of those processes, you'll need to install the CloudWatch Agent.