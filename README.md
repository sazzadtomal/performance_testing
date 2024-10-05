# Performance-Testing
# Introduction
Welcome to the performance testing repository for the [restful-booker API ](https://restful-booker.herokuapp.com) using Apache JMeter. This document explains how to run a performance test with JMeter.

Dear,

I’ve completed a performance test on frequently used API for the test App [restful-booker API](https://restful-booker.herokuapp.com)

Test executed for the below-mentioned scenario in server [restful-booker API](https://restful-booker.herokuapp.com)

* 100 Concurrent Request with 10; Ramp-up Speed 10s; Avg TPS for Total Samples is ~ 8 And Total Concurrent API requested: 500.
* 500 Concurrent Request with 10;Ramp-up Speed 10s; Avg TPS for Total Samples is ~ 42 And Total Concurrent API requested: 2500.
* 1000 Concurrent Request with 10; Ramp-up Speed 10s; Avg TPS for Total Samples is ~ 84 And Total Concurrent API requested: 5000.
* 2000 Concurrent Request with 10; Ramp-up Speed 10s; Avg TPS for Total Samples is ~ 168 And Total Concurrent API requested: 10000.
* 3000 Concurrent Request with 10; Ramp-up Speed 10s; Avg TPS for Total Samples is ~ 250 And Total Concurrent API requested: 15000.
* 4000 Concurrent Request with 10; Ramp-up Speed 10s; Avg TPS for Total Samples is ~ 302 And Total Concurrent API requested: 20000.
* 4500 Concurrent Request with 10; Ramp-up Speed 10s; Avg TPS for Total Samples is ~ 209 And Total Concurrent API requested: 22500.
* 5000 Concurrent Request with 10; Ramp-up Speed 10s; Avg TPS for Total Samples is ~ 336 And Total Concurrent API requested: 25000.

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
  
    The root element of every test plan. Simulates the (concurrent) users and then run all requests. Each thread simulates a single user.
  
* HTTP Request Default (Configuration Element)
* HTTP Request (Sampler)
* Summary Report (Listener)

# Test Plan
* Testplan > Add > Threads (Users) > Thread Group (this might vary depending on the JMeter version you are using)
* Name: RestfulBooker Users
* Number of Threads (users): 100 to 5000
* Ramp-Up Period (in seconds): 10
* Loop Count: 1

  1) The general setting for the tests execution, such as whether Thread Groups will run simultaneously or sequentially, is specified in the item called Test Plan.

  2) All HTTP Requests will use some default settings from the HTTP Request, such as the Server IP, Port Number, and Content-Encoding.

  3) Each Thread Group specifies how the HTTP Requests should be carried out. To determine how many concurrent "users" will be simulated, one must first know the number of threads. The number of actions each "user" will perform is determined by the loop count.

  4) The HTTP Header Manager, which allows you to provide the Request Headers that will be utilized by the upcoming HTTP Requests, is the first item in Thread Groups.


# Collection of API
## Load the JMeter Script
* File > Open (CTRL + O)
* Locate the "RestfulBooker_TC100.jmx" file contained on this repo
* Continue open "RestfulBooker_TC100.jmx" to "RestfulBooker_TC5000.jmx"
* Open those file
* The Test Plan will be loaded
  
![Jmeter_GUI](https://github.com/user-attachments/assets/7620d50d-00ff-4c88-a8ff-dc181503d547)


# Test execution (from the Terminal)
* JMeter should be initialized in non-GUI mode.
* Make a report folder in the bin folder.
* Run Command in jmeter\bin folder.

### Make jtl file
```bash
  jmeter -n -t RestfulBooker_TC100.jmx    -l RestfulBooker_TC100.jtl
```      
  - **n**: non GUI mode
  - **t**: test plan to execute
  - **l**: output file with results

Then continue to upgrade Threads(100 to 5000) by keeping Ramp-up Same.     

After completing this command  

### Make html file
```bash
  jmeter -g report\RestfulBooker_TC100.jmx -o RestfulBooker_TC100.html
```
  - **g**: jtl results file
  - **o**: path to output folder  

# Result Summary 


I’ve completed a performance test on frequently used API for the test App [restful-booker API ](https://restful-booker.herokuapp.com).

Test executed for the below-mentioned scenario in server [restful-booker API ](https://restful-booker.herokuapp.com).

* 100 Concurrent Request with 10; Ramp-up Speed 10s; Avg TPS for Total Samples is ~ 8 And Total Concurrent API requested: 500.
* 500 Concurrent Request with 10; Ramp-up Speed 10s; Avg TPS for Total Samples is ~ 42 And Total Concurrent API requested: 2500.
* 1000 Concurrent Request with 10; Ramp-up Speed 10s; Avg TPS for Total Samples is ~ 84 And Total Concurrent API requested: 5000.
* 2000 Concurrent Request with 10; Ramp-up Speed 10s; Avg TPS for Total Samples is ~ 168 And Total Concurrent API requested: 10000.
* 3000 Concurrent Request with 10; Ramp-up Speed 10s; Avg TPS for Total Samples is ~ 250 And Total Concurrent API requested: 15000.
* 4000 Concurrent Request with 10; Ramp-up Speed 10s; Avg TPS for Total Samples is ~ 302 And Total Concurrent API requested: 20000.
* 4500 Concurrent Request with 10; Ramp-up Speed 10s; Avg TPS for Total Samples is ~ 209 And Total Concurrent API requested: 22500.
* 5000 Concurrent Request with 10; Ramp-up Speed 10s; Avg TPS for Total Samples is ~ 336 And Total Concurrent API requested: 25000.

# HTML Report

**Number of Threads 100 ; Ramp-Up Period 10s**

![Number of Threads 100 ; Ramp-Up Period 10s](https://github.com/user-attachments/assets/6b5d32b0-8a83-4622-91ee-1ff5e80aa951)

![Number of Threads 100 ; Ramp-Up Period 10s](https://github.com/user-attachments/assets/b861f2c3-8996-411a-93d3-5ba0207fb33e)

**Number of Threads 500 ; Ramp-Up Period 10s**

![Number of Threads 500 ; Ramp-Up Period 10s](https://github.com/user-attachments/assets/ac02467b-691a-4a84-ba76-11fdae9f6564)

![Number of Threads 500 ; Ramp-Up Period 10s](https://github.com/user-attachments/assets/a01a37ea-4617-468f-8a75-bdccb2c4be8d)


**Number of Threads 1000 ; Ramp-Up Period 10s**

![Number of Threads 1000 ; Ramp-Up Period 10s](https://github.com/user-attachments/assets/2c172092-3861-4fb7-8c64-50da55be7f96)

![Number of Threads 1000 ; Ramp-Up Period 10s](https://github.com/user-attachments/assets/6dc77efc-fa08-4e97-8c1b-f3bc19e8c9cc)


**Number of Threads 2000 ; Ramp-Up Period 10s**

![Number of Threads 2000 ; Ramp-Up Period 10s](https://github.com/user-attachments/assets/0cbd77e4-2fbe-493f-a551-e74fcf26606e)

![Number of Threads 2000 ; Ramp-Up Period 10s](https://github.com/user-attachments/assets/5e85542a-52a8-47ac-a50e-ebf27be4135b)


**Number of Threads 3000 ; Ramp-Up Period 10s**

![Number of Threads 3000 ; Ramp-Up Period 10s](https://github.com/user-attachments/assets/791fb9cb-6b23-47f7-8b8d-4feec196a5b5)

![Number of Threads 3000 ; Ramp-Up Period 10s](https://github.com/user-attachments/assets/c0e2002b-80b5-4e9a-8f1f-38a5c0d4ca1f)

**Number of Threads 4000 ; Ramp-Up Period 10s**

![Number of Threads 4000 ; Ramp-Up Period 10s](https://github.com/user-attachments/assets/e02d5414-83c6-4872-b464-8f2c580dfcb4)

![Number of Threads 4000 ; Ramp-Up Period 10s](https://github.com/user-attachments/assets/b93a1304-bdc4-437e-9707-37bb60ed8bd7)

**Number of Threads 4500 ; Ramp-Up Period 10s**

![Number of Threads 4500 ; Ramp-Up Period 10s](https://github.com/user-attachments/assets/b43f34f9-853a-4b86-9f68-c92fb62ecc52)

![Number of Threads 4500 ; Ramp-Up Period 10s](https://github.com/user-attachments/assets/82252559-c1c8-4457-9a2f-35e16119c935)

**Number of Threads 5000 ; Ramp-Up Period 10s**

![Number of Threads 5000 ; Ramp-Up Period 10s](https://github.com/user-attachments/assets/9f3a4d18-cff6-48ff-8ae6-c06a2efdc4cc)

![Number of Threads 5000 ; Ramp-Up Period 10s](https://github.com/user-attachments/assets/59888856-a603-4b1b-a570-b0bd133fd820)