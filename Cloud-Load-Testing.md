Cloud-Based Load Testing:
=========================
With more than 300,000 applications available for the iPhone and another million for Android mobile devices, 
there is an urgent market need to ensure network-connected applications scale for the number of users accessing it concurrently. 
Additionally, social media usage in the mobile environment has skyrocketed and the applications available typically use APIs to communicate across various platforms. Current offerings for cloud-based load testing are enterprise tools, designed for testing static websites and enterprise applications, and are not affordable for developers of mobile applications or APIs. In fact, in many cases the testing cannot be performed because of the time and cost involved. We take away these objections with a self-service and affordable solution that any software development team can use.


The solution is built upon the open source load test framework Apache JMeter. 
The JMeter is – next to The Grinder – one of the most popular open source load tools. 
As most serious load tools JMeter implements an Agent/Controller Architecture. 


Within the JMeter framework the Controller is called “Master”. 
The master coordinates several agent (aka “slave”) machines. 
Each slave machine controls several worker threads. 
In order to generate load master and slave processes run on different machines in the network. 


The number of slave machines – and thereby the number of machines necessary to run the tests 
– increases with the amount of load specified for the tests. Master and slave machines are implemented as Amazon Machine Images. 
A Starter Kit has been added that implements the transparent start-up of as many slaves as necessary. 
According to JMeter logic the Starter Kit first starts up the slave machines. 
Once they are operational it writes a proper JMeter. 


## Architectural Overview

The overall Architecture of the JMeter in the Cloud solution is shown below.
![Cloud Testing](/images/JmeterCloud.png)


The tester talks from his machine to an instance of the Starter Kit amazon machine image (AMI) containing all the necessary software (Starter Kit, JMeter). 

The Starter Kit machine is accessed using a linux based remote desktop application (NX client, available for unix and windows).
The Starter Kit instance starts up as many slaves as requested. 


The slaves are implemented as AMIs and live in the cloud. Once the slaves are operational the Starter Kit starts the JMeter master.
From here on the tests can be executed as described in the standard JMeter documentation. 
If required the slaves can be accessed using commonly available secure shell (ssh) tools. 
The slaves inject the load into the system under test (SuT).
