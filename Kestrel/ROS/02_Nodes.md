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

In a full robotic system; there are many nodes working in concert, while in ROS 2 a single executable file can contain one or more nodes.

### Execute a Node:
To begin the execution of a node with a package that is housed within a workspace; first make sure you are within that workspace. Secondly run the command:
- `ros2 run <package_name> <executable_name>`
This will begin the execution of the `<executable_name>` within the `<package_name>` package.

### View all Nodes:
To view all the nodes that are currently running within your package, run the command:
- `ros2 node list` 
This will return you a list of all the nodes that are currently active within your current package.

### Remapping:
Remapping is a concept that allows you to **reassign default node properties** such as:
- node names
- topic names
- service names
- etc...
`ros2 run <package_name> <executable_name> --ros-args --remap __node:=new_exec_name`

Now that you have remapped `<exec_name>` $\rightarrow$ `new_exec_name` when you run `ros2 node list` you will see both instances within the node list.

### Node Info:
Running the command:
- `ros2 node info <node_name>`
Will report info on the node such as:
- Subscribers
- Publishers
- Service Servers
- Service Clients
- Action Servers
- Action Clients
A.K.A the ROS graph connections that interact with that node so you can better understand what the node is responsible for.