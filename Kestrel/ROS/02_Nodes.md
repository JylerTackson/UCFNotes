A node within ROS is responsible for a single, modular purpose:
- Controlling motors
- Publishing Sensor Data
- etc...
Each Node can **send and receive data** from other nodes using:
- [[03_Topics]]
- [[04_Services]]
- [[05_Parameters]]
- [[06_Actions]]
![[Nodes-TopicandService.gif]]

In a full robotic system; there are many nodes working on concert, while in ROS 2 a single executable file can contain one or more nodes.

### Create a Node:
``