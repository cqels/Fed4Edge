# Fed4Edge
Federation for Edge Devices

## Contents
* [1. Requirements](#requirements)
   * [1.1. Hardware](#hardware)
   * [1.2. Software](#software)
* [2. Setup](#setup)
* [3. Run Experiment](#run-experiment)

## 1. Requirement
### 1.1. Hardware
  - Raspbery pi 3 B+.
  - Ethernet switch.

### 1.2. Software
  - OS: raspbian latest version.
  - JDK 8.
  - python2.7.
  
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
 ### Step 1. Prepare
 ### Step 2. Run
    
   
