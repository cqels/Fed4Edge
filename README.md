# Fed4Edge
Federation for Edge Devices

## 1. Hardware & Software Requirement
   
The engine can run on any device that is equipped with JRE 8.

## 2. Setup
 * On **root node** and **leaf processing nodes**:
   - Install jdk 8 (recommend open jdk 8): 
     ```
      sudo apt-get update
      sudo apt-get install openjdk-8-jdk
     ```
   - Upload file **Fed4Edge.jar** from folder bin to devices.
    
 ## 3. Run Experiment
 ### Prepare
- A query to query data from **root node**.
- For each nodes which have childs is a **leaf processing nodes**:
 - Create a text file contain the IP list of the childs of that node with its port on separate lines.
   Format: _{ip}:{port}_
   E.g.
   ```
      192.168.1.88:2500
   ```
 - Create a text file contain a **CONSTRUCT** query that will query data from its child nodes, to get result in N-triples

- For the nodes which its child node is **streamer nodes**:
 - Create a text file contain the list of Websocket URI of **streamer nodes** on separate lines.
      
 ### Usage
 ```
   java -jar Fed4Edge.jar port output_file_name node_type uri_list query_file_name
 ```
 - Arguments:
   - ***port***: port for current node,
   - ***output_file_name***: name for the output file.
   - ***node_type***: **root** for root node and **leaf** for leaf nodes.
   - ***uri_list***: file name of list uri.
   - ***query_file_name***: file name of the construct query, leave it empty if the node have childs is a **streamer nodes**.
   

   
