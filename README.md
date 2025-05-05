# SDN Ryu-Controller -- Load-Balancing with Dynamic-Routing
Ryu controller which performs DIJKSTRA algorithm to find best paths, based on traffic flowing through links.

## OpenFlow version used: 
OpenFlow 1.3 

## Description:
Ryu controller which performs DIJKSTRA algorithm to find best paths, based on traffic flowing through links. Optimal path is being choosen from possible paths. The costs are being calculated in the background (action performed by thread and the path cost is calculated via network bandwidth calculation.) and optimal path is being updated every second based on the gathered stats. Discover of topology is done automatically so we don't have to have specially prepared topology. 

## Commands AND Requirements
```bash
ryu-manager --observe-links multipath.py (for initializing the RYU controller)
```
```bash
sudo mn -c
```
```bash
sudo python topology.py (For initializing the topology of the network)
```
- Virtual Machine
- Mininet 2.3.0
- RYU controller


## DIJKSTRA ALOGRITHM USED:

We have used Dijkstra algorithm to find the shortest available path from H1 to H2. The algorithm uses min heap functionality to calculate the smallest path cost. Following is the screenshot of the code.

![Screenshot](https://github.com/Sotejaswini/SDN-based-Load-Balancing/blob/main/SDN-based-Load-Balancing/Algorithms/dijkstra.png?raw=true)

## TOPOLOGY USED:

We have created 2 controllers, one controller is for backup. We have created 9 switches for the connection part. All the links are connected as shown in the screenshot. There are 2 hosts in the network topology.

![Screenshot](https://github.com/Sotejaswini/SDN-based-Load-Balancing/blob/main/SDN-based-Load-Balancing/Algorithms/topology.png?raw=true)

## Protocols Configured:

Our Code is configured to use 4 types of protocol. The type of protocol can be found using the header values. The protocols are ``TCP`` , ``UDP`` , ``ICMP`` , ``ARP``. Tcp is used for normal connection. UDP will be used for service packets for buffering. ICMP will be used when the link gets terminated to send a ping regarding link destruction. ARP is used when the host IP is known but MAC is not known.

![Screenshot](https://github.com/Sotejaswini/SDN-based-Load-Balancing/blob/main/SDN-based-Load-Balancing/Algorithms/protocols.png?raw=true)


## Screenshots of Running Code:
As you can see in the screenshot the possible paths are calculated and the path will minimum cost is the final cost of the packet transmission.
![Screenshot](https://github.com/Sotejaswini/SDN-based-Load-Balancing/blob/main/SDN-based-Load-Balancing/Mininet-basictools/screenshot1.jpg?raw=true)
![Screenshot](https://github.com/Sotejaswini/SDN-based-Load-Balancing/blob/main/SDN-based-Load-Balancing/Mininet-basictools/screenshot2.jpg?raw=true)
![Screenshot](https://github.com/Sotejaswini/SDN-based-Load-Balancing/blob/main/SDN-based-Load-Balancing/Mininet-basictools/screenshot3.jpg?raw=true)
![Screenshot](https://github.com/Sotejaswini/SDN-based-Load-Balancing/blob/main/SN-based-Load-Balancing/Mininet-basictools/screenshot4.jpg?raw=true)
![Screenshot](https://github.com/Sotejaswini/SDN-based-Load-Balancing/blob/main/SDN-based-Load-Balancing/Mininet-basictools/screenshot5.jpg?raw=true)

