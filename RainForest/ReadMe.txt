**Table of contents**

Test Tool
Pre-requisites
Repository folder structure
Scenario/Test Plan Config
Test Script Name
Data Driven
Transaction
Correlation Rules
Sanity Test Execution Results
Known Issues
Assumptions

**Test Tools**

The Apache JMeter application is open source software, a 100% pure Java application designed to load test functional behavior and measure performance.

JMeter 4.0 is compatible with Java 8 or Java 9. It is highly advise you to install latest minor version of those major versions for security and performance reasons.

User Manual located here: -
[https://jmeter.apache.org/usermanual/index.html](https://jmeter.apache.org/usermanual/index.html)

**Pre-requisites**

To get started in testing fuse portal please download the latest JMeter application located here: -[https://jmeter.apache.org/download\_jmeter.cgi](https://jmeter.apache.org/download_jmeter.cgi)

This project was developed using JMeter 5.1.1r1855137

**Repository folder structure**

[01 Scenario]
[02 Test Scripts]
[03 Capture]
[04 Data]

01 - Contains configured scenario to emulate a goal-oriented tests. i.e. soak, load etc
02 - Contains the latest version of test scripts and if updates/changes require the scenario to be updates with the latest changes to the test scripts
03 - Raw capture of the business process
04 - Maintenance and usage of test data such as username and password that would be shared with scenario execution. Data consideration are, Unique, Random, Once, Sequential and thought on data states with any burnt data after execution.

**Scenario/Test Plan Config:**

Scenario/Test Plan Name: 	Fusion
RampUp: 					1000 vuser every 0.033 second.
RampUp Time: 				30secs
Target Txns:  				TPH SignIn page, Login, Sign-out.
Duration:					30sec after rampup
Debug/logging:	 			OFF
Think Time:					NONE
Pacing:						NONE
If Error:	  				Continue

Test Script Name:
Test Script Steps: Login, Landing page displayed, logout

**Data Driven:**

Attribute: 	CSV Host
Element: 	Protocal,URL,Port
File Name: 	Host.csv

Attribute: 	CSV Credentials
Element: 	username,password
File Name: 	Users.csv

_Please note the absolute path of the .CSV files will need to be pointed correctly or converted into a relative path._

**Transaction:**

Measurable transaction time and TPH

Business Process Txns:
000 - Business Process Login

Parent Txns:
100 – SignInPage
200 – Login
300 - SignOut

Verification Points:

Verification  point are place to ensure the page is loaded correctly and does not error.

120-home
164-login
192 logoff

**Correlation Rules:**

csrf-token
service\_sid
clientId

**Sanity Test Execution Results:**

2019/07/16 - Validate with single and multiple iteration sequentially but no concurrent threads. Passed.
Data for user creditable will need to be populated with further rows.
Vuser multiple iteration
Vuser serial threads

**Known Issues:**

Verify that session is being closed in application logs
Widget Disabled as was throwing error from 170 - 185 requests.  Required further debugging

**Assumptions:**

The widget loading is Asynchronous calls.