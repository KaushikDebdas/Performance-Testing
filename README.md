# Performance-Testing
# Introduction
This document explains how to run a performance test with JMeter.

Dear,

I’ve completed a performance test on frequently used API for the test App https://restful-booker.herokuapp.com/.
Test executed for the below-mentioned scenario in server https://restful-booker.herokuapp.com/.

* 100 Concurrent Request with 10 Loop Count; Avg TPS for Total Samples is ~ 10 And Total Concurrent API requested: 600.
* 500 Concurrent Request with 10 Loop Count; Avg TPS for Total Samples is ~ 50 And Total Concurrent API requested: 3000.
* 1000 Concurrent Request with 10 Loop Count; Avg TPS for Total Samples is ~ 100 And Total Concurrent API requested: 6000.
* 5000 Concurrent Request with 10 Loop Count; Avg TPS for Total Samples is ~ 438 And Total Concurrent API requested: 30000.

# Install
# Java
https://www.oracle.com/java/technologies/downloads/

# JMeter
https://jmeter.apache.org/download_jmeter.cgi

Click =>Binaries
=>apache-jmeter-5.5.zip

# Prerequisites
As of JMeter 4.0, Java 8 and above are supported.
* We suggest multicore CPUs with 4 or more cores.
* Memory 16GB RAM is a good value.

# Elements of a minimal test plan
* Thread Group
The root element of every test plan. Simulates the (concurrent) users and then runs all requests. Each thread simulates a single user.
* HTTP Request Default (Configuration Element)
* HTTP Request (Sampler)
* Summary Report (Listener)

# Test Plan
* Testplan > Add > Threads (Users) > Thread Group (this might vary depending on the JMeter version you are using)
* Name: Users
* Number of Threads (users): 1 to 6
* Ramp-Up Period (in seconds): 10
* Loop Count: 1

  1) The general setting for the tests execution, such as whether Thread Groups will run simultaneously or sequentially, is specified in the item called Test Plan.

  2) All HTTP Requests will use some default settings from the HTTP Request, such as the Server IP, Port Number, and Content-Encoding.

  3) Each Thread Group specifies how the HTTP Requests should be carried out. To determine how many concurrent "users" will be simulated, one must first know the number of threads. The number of actions each "user" will perform is determined by the loop count.

  4) The HTTP Header Manager, which allows you to provide the Request Headers that will be utilized by the upcoming HTTP Requests, is the first item in Thread Groups.


# Collection of API
## Load the JMeter Script
* File > Open (CTRL + O)
* Locate the "BasicProject_BookingAPI_TG100.jmx" file contained on this repo
* Continue open BasicProject_BookingAPI_TG100 to BasicProject_BookingAPI_TG5000
* Open those file
* The Test Plan will be loaded
![BasicProject_BookingAPI_TG100](https://github.com/KaushikDebdas/Performance-Testing/assets/67013658/3cec7fd4-1777-4a87-bd88-4706f3600635)

# Test execution (from the Terminal)
* JMeter should be initialized in non-GUI mode.
* Make a report folder in the bin folder.
* Run Command in jmeter\bin folder.

### Make jtl file
```bash
  jmeter -n -t BasicProject_BookingAPI_TG100.jmx -lBasicProject_BookingAPI_TG100.jtl
```      
  - **n**: non GUI mode
  - **t**: test plan to execute
  - **l**: output file with results 
  Then continue to upgrade Threads(100 to 5000) by keeping Ramp-up Same.   
  
After completing this command  
### Make html file
```bash
  jmeter -g report\BasicProject_BookingAPI_TG100.jtl -o BasicProject_BookingAPI_TG100.html
```
  - **g**: jtl results file
  - **o**: path to output folder  

# Result Summary 
Dear,

I’ve completed a performance test on frequently used API for the test App https://restful-booker.herokuapp.com/.
Test executed for the below-mentioned scenario in server https://restful-booker.herokuapp.com/.

* 100 Concurrent Request with 10 Loop Count; Avg TPS for Total Samples is ~ 10 And Total Concurrent API requested: 600.
* 500 Concurrent Request with 10 Loop Count; Avg TPS for Total Samples is ~ 50 And Total Concurrent API requested: 3000.
* 1000 Concurrent Request with 10 Loop Count; Avg TPS for Total Samples is ~ 100 And Total Concurrent API requested: 6000.
* 5000 Concurrent Request with 10 Loop Count; Avg TPS for Total Samples is ~ 438 And Total Concurrent API requested: 30000.

# HTML Report

**Number of Threads 100 ; Ramp-Up Period 10s**

![Number of Threads 100 ; Ramp-Up Period 10s](https://github.com/KaushikDebdas/Performance-Testing/assets/67013658/9df5caaf-ba81-4c58-8d96-ecb6c870c9cb)

**Number of Threads 500 ; Ramp-Up Period 10s**

![Number of Threads 500 ; Ramp-Up Period 10s](https://github.com/KaushikDebdas/Performance-Testing/assets/67013658/c705ba45-7385-4e60-896c-44a5ceb042f4)

**Number of Threads 1000 ; Ramp-Up Period 10s**

![Number of Threads 1000 ; Ramp-Up Period 10s](https://github.com/KaushikDebdas/Performance-Testing/assets/67013658/d7d24090-f5cf-4690-82b9-c695a4db86d6)

**Number of Threads 5000 ; Ramp-Up Period 10s**

![Number of Threads 5000 ; Ramp-Up Period 10s](https://github.com/KaushikDebdas/Performance-Testing/assets/67013658/64668c83-6295-48e1-b8f7-52a708920724)
