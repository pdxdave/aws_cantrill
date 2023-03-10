# CloudWatch Test
![cw_04](../assets/cw_04.png)
![cw_05](../assets/cw_05.png)
![cw_06](../assets/cw_06.png)
![cw_07](../assets/cw_07.png)
### Advanced Settings
1. Detailed CloudWatch monitoring set to enable.  Additional charges apply.
![cw_08](../assets/cw_08.png)
2. When done with settings scroll to bottom and select launch instance.  It will take a few minutes to run.
3. Select view all instances
![cw_09](../assets/cw_09.png)
4. When status check is 2/2, run a search for CloudWatch
![cw_10](../assets/cw_10.png)
5. CloudWatch Dashboard > Alarms 
![cw_11](../assets/cw_11.png)
6. All alarms > Create alarm
![cw_12](../assets/cw_12.png)
7. Select metric
![cw_13](../assets/cw_13.png)
8. Now look for EC2.  The CPU Utilize metric is inside the EC2 name space.
![cw_14](../assets/cw_14.png)
9. Per-Instance Metrics
![cw_15](../assets/cw_15.png)
10. This will show all of the pre-instance metrics we currently have.  Scroll until you find CPUUtilization. Check the box, then select metric button
![cw_16](../assets/cw_16.png)
11. Specify metric and conditions
![cw_17](../assets/cw_17.png)
12. Scroll down to Conditions.  Keep static b/c you want the alarm to go into an alarm state when something happens to the CPUUtilization. When the CPUUtilization is greater/equal than 15%, then the alarm will go off.  Click next.
![cw_18](../assets/cw_18.png)
13. Now we can choose to have SNS notification.  This would be good for production, but in this practice case, not really.  Just take the Remove button. Select Next.
![cw_19](../assets/cw_19.png)
14. Now give it an alarm name, then next, then create alarm.
![cw_20](../assets/cw_20.png)
15. It'll take you back to Alarms.  The state will be insufficient since it doesn't really have any data.