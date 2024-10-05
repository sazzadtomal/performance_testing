# Performance-Testing using Apache JMeter.

## Introduction

This performance test was conducted on the website [https://restful-booker.herokuapp.com](https://restful-booker.herokuapp.com) to evaluate its behavior under varying levels of concurrent API requests. The test aimed to assess the system's stability, throughput, and its ability to handle high traffic loads efficiently. 

Using **Apache JMeter**, the test simulated concurrent user threads, starting from 100 and increasing to 5000, with a ramp-up period of 10 seconds for each test. Key performance metrics such as **Average Transactions Per Second (TPS)** and the total number of API requests successfully processed were recorded to identify potential bottlenecks and measure the system's performance under different load conditions. 

The results provide insights into the system's capacity to handle concurrent users and will help guide optimizations for future scalability and performance improvements.


## Instructions

### Install

#### Java

https://www.oracle.com/java/technologies/downloads/

#### JMeter

https://jmeter.apache.org/download_jmeter.cgi

Click =>Binaries
=>apache-jmeter-5.5.zip

## Prerequisites

As of JMeter 4.0, Java 8 and above are supported.
* We suggest multicore CPUs with 4 or more cores.
* Memory 16GB RAM is a good value.

## Elements of a minimal test plan

* Thread Group
  
    The root element of every test plan. Simulates the (concurrent) users and then run all requests. Each thread simulates a single user.
  
* HTTP Request Default (Configuration Element)
* HTTP Request (Sampler)
* Summary Report (Listener)

## Test Plan
* Testplan > Add > Threads (Users) > Thread Group (this might vary depending on the JMeter version you are using)
* Name: RestfulBooker Users
* Number of Threads (users): 100 to 5000
* Ramp-Up Period (in seconds): 10
* Loop Count: 1

  1) The general setting for the tests execution, such as whether Thread Groups will run simultaneously or sequentially, is specified in the item called Test Plan.

  2) All HTTP Requests will use some default settings from the HTTP Request, such as the Server IP, Port Number, and Content-Encoding.

  3) Each Thread Group specifies how the HTTP Requests should be carried out. To determine how many concurrent "users" will be simulated, one must first know the number of threads. The number of actions each "user" will perform is determined by the loop count.

  4) The HTTP Header Manager, which allows you to provide the Request Headers that will be utilized by the upcoming HTTP Requests, is the first item in Thread Groups.


## Test Plan
### Load the JMeter Script
* File > Open (CTRL + O)
* Locate the "RestfulBooker_TC100.jmx" file contained on this repo
* Continue opening from "RestfulBooker_TC100.jmx" to "RestfulBooker_TC5000.jmx"
* Open those file
* The Test Plan will be loaded
  
![Jmeter_GUI](https://github.com/user-attachments/assets/7620d50d-00ff-4c88-a8ff-dc181503d547)

---

## Test execution

### From the Terminal
* JMeter should be initialized in non-GUI mode.
* Make a report folder in the bin folder.
* Run Command Prompt jmeter\bin folder.

### Run Test and Generate Logs
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


## Summary

### Test Results Overview

| Concurrent Requests | Ramp-up Period | Average TPS | Total API Requests | Observations                |
|---------------------|----------------|-------------|--------------------|-----------------------------|
| 100                 | 10s            | ~8          | 500                | Stable                      |
| 500                 | 10s            | ~42         | 2500               | Stable                      |
| 1000                | 10s            | ~84         | 5000               | Stable                      |
| 2000                | 10s            | ~168        | 10000              | Stable                      |
| 3000                | 10s            | ~250        | 15000              | Stable                      |
| 4000                | 10s            | ~302        | 20000              | Stable                      |
| 4500                | 10s            | ~209        | 22500              | Stable but lower throughput |
| 5000                | 10s            | ~336        | 25000              | Errors Noticed              |

---

### Key Observations

1. **Stable Performance**
   - The system performed stably up to **4500 concurrent requests**. The Average TPS steadily increased with the number of concurrent requests, reaching up to **302 TPS** with 4000 concurrent requests.

2. **4500 Concurrent Requests**
   - With **4500 concurrent requests**, the system remained stable but the throughput decreased. The Average TPS was **209**, lower than the expected progression from previous tests. This indicates the system could handle the load, but with reduced efficiency.

3. **Performance Degradation at 5000 Concurrent Requests**
   - When the number of concurrent requests reached **5000**, performance dropped significantly. The Average TPS increased to **336**, but errors were noticed during execution, indicating that the system struggled to handle this level of concurrency.

---

### HTML Reports

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



### Conclusion

The system demonstrated solid performance up to **4500 concurrent requests**, handling high traffic efficiently but with reduced throughput at this level. Beyond this threshold, particularly at **5000 concurrent requests**, errors emerged, suggesting a need for optimization or infrastructure scaling to maintain performance under extreme load conditions.

---

### Recommendations

1. **System Tuning**
   - Investigate potential bottlenecks in the system (e.g., database connections, server limits) and tune them to handle more than 4500 concurrent users. Special attention should be paid to throughput optimization for **4500 concurrent requests**.

2. **Infrastructure Scaling**
   - Consider scaling the infrastructure vertically or horizontally to accommodate higher concurrency levels.

3. **Further Testing**
   - Conduct additional testing at a range between **4500 and 5000** concurrent requests to pinpoint the system’s capacity limit more accurately.

---






