# Performance testing
## Gatling

### Steps
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