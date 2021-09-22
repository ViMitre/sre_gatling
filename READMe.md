# Performance testing
![](img/diagram.png)
## Types of testing
- Load testing<br>
Checking performance under a large number of virtual users
- Stress testing<br>
Testing how the system behaves with extreme loads
- Soak testing<br>
Testing with a large load over a long period of time
- Spike testing<br>
Testing with a sudden increase and decrease in load

## What Should be Monitored for an Internet Facing Application
- Resource Monitoring (CPU, Network, Memory, etc.)
- Network Monitoring (in and out)
- Application Performance Monitoring
- Third-party resources/components


# Steps
- Launch the app template
- Make sure auto-scaling is in place
- Record activity on the webpage with the browser
- Tick `Preserve log`
- Save activity (Export HAR)
![](img/1.png)
- Convert `HAR` to `.scala` using `recorder.bat` or `recorder.sh`
![](img/2.png)
- The recorded activity is now added as a test
- Run the test using `gatling.bat` or `gatling.sh` (choose the appropriate one)
- To increase the number of requests, increase the number in the last line: `setUp(scn.inject(atOnceUsers(1))).protocols(httpProtocol)` and run the test again

## Create event(s) to trigger ASG
- Select an ASG 
- On `Automatic Scaling` tab, click on `Create dynamic scaling policy`
### Example:
![](img/3.png)

### Create a dynamic scaling policy to scale in
![](img/6.png)

### Create an alarm for each policy (scale out and scale in)
- Select metric<br>
EC2 -> By Auto Scaling Group -> Select metric
- Set metric options and conditions
![](img/4.png)
![](img/5.png)
- Add notification
![](img/9.png)
- Click on `Create a new topic` if there isn't one yet
- Name it and add an email address
- Add appropriate Auto Scaling Action
![](img/10.png)
- Name it and finish creation of alarm

![](img/diagram2.png)

