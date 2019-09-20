# Fed4Edge
Federation for Edge Devices

## 1. Hardware & Software Requirement
   
The engine can run on any device that is equipped with JRE 8.

## 2. Setup
 * Connect all raspberry pi devices to the network (LAN or over internet), then assign a **static IP address** for each devices.
 * On **root node** and **leaf processing nodes** (red node and blue nodes):
   - Install jdk 8 (recommend open jdk 8): 
     ```
      sudo apt-get update
      sudo apt-get install openjdk-8-jdk
     ```
   - Upload file **cqels.jar** from folder bin to devices.
  
 * On **streamer nodes**:
   - Install Python2.7.
   - Install python websocket:
     ```
      sudo pip install websocket_server
     ```
    - Upload file **streamer** from folder bin to devices.
  * On **client node**:
    - Install jdk 8.
    - Upload file **client.jar** from folder bin to device.
    
 ## 3. Run Experiment
 ### Prepare
 **Bellow is an example for setup experiment on Topology with 5 nodes (2 hop, 4-fanout)**
 
 * On **Root node** (red node) (and the **leaf processing nodes** if the topology have more than 2 hop, except the last **leaf processing nodes** level - which is direct connect with the **streamer nodes**):
   1. Create file "stream_list.txt" and add the list  **static IP** of the first level **leaf processing nodes**.
   E.g.
   ```
    192.168.1.30
    192.168.1.31
    192.168.1.32
    192.168.1.33
   ```
   2. Create file "sub_query.txt" and add a **CONSTRUCT** query which **root node** will send to **leaf processing nodes** to get the data from lower level(s)

* On the last level of **Leaf processing nodes** (blue nodes):
  1. Create file "stream_list.txt" and add the list **static IP** of **streamer nodes** that directly connect to that **leaf processing node**. 
  
  E.g.
  ***List of streamer nodes connect to leaf processing node 192.168.1.30***
  ```
    192.168.1.34
    192.168.1.35
    192.168.1.36
    192.168.1.37
  ```
  
  ***List of streamer nodes connect to leaf processing node 192.168.1.31***
  ```
    192.168.1.38
    192.168.1.39
    192.168.1.40
    192.168.1.41
  ```
  ...etc
  
* On **Client node**:
  Create file "query.txt" and add the query which will query the data from **leaf processing nodes** under **root node**.

* On **Streamer node**:
  - Upload data (in N-triple format) to devices and setup data in folder with structure bellow:
    data/{data-id}/
  Example for data tree structure:
    ```
      ---
          |--- streamer
          |--- data
               |--- 720170-63851-2019
                    |---------------- 1.nt
                    |---------------- 2.nt
                    |---------------- 3.nt
                    ...
          
    ```
 
 ### Run
 ***run program by following step in the order:***
 * On **root nodes** run command:
   ```
     java -Xms512M -jar cqels.jar 2500 log 0
   ```
 * On **leaf processing nodes** run command:
   ```
    java -Xms512M -jar cqels.jar 2500 log 1
   ```
 * On **client node** run command:
   ```
    java -jar client.jar
   ```
 * On **stream nodes** run command:
   ```
    ./streamer
   ```
   
