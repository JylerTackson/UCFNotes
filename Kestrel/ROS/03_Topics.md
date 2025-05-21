**Topics** act as a bus for nodes to exchange messages. **A node may publish and subscribe to any number of topics simultaneously**. Topics are one of the main ways in which data is moved between nodes and different parts of the system.
![[Topic-MultiplePublisherandMultipleSubscriber.gif]]

### Visualization tool:
To visualize the changing nodes and topics you can use a tool known as `rqt_graph`. To install on, enter the following line within you command line:
- `sudo apt install '~nros-humble-rqt*'`
Then run by using the following in the command line:
- `rqt`

When running rqt for the first time go to: $\text{Plugins} \rightarrow\text{Services} \rightarrow\text{Service Caller}$ in the ribbon at the top.
**NOTE:** If you do not see any services within the Plugins options, close rqt and run:
- `rqt --force-discover`

To run `rqt_graph` for visualization of changing nodes and topics, in your command terminal run:
- `rqt_graph`
![[rqt_graph.png]]


### List:
To return a list of all the currently running topics that are active within the system, in a new command terminal run:
- `ros2 topic list`
If you would like to see the topic type as well as the topic you can run:
- `ros2 topic list -t`
This will return the same list of topics however it will append the type attribute to within a bracket to the end of each topic.

If you want to generate a list of all topics of a certian type you can enter the command:
- `ros2 topic find <type>`

### Topic Echo:
If you would like to see the data being published on a topic you can use the command:
- `ros2 topic echo <topic_name>`
This command will return the data that is being published to that specific topic. This is good to see what is being sent in real time.

### Topic Info:
As shown in the picture at the top; topics can be:
- One to one
- One to many
- Many to One
- Many to Many
It really doesn't matter they just have to be configured correctly. If you run the command:
- `ros2 topic info <topic_name>` 
The following information will be reported:
- Type
- Publisher count
- Subscription count

### Interface Show:
Nodes send data over topics using **messages**.
A **publisher** is a node that sends a message to a topic meanwhile a **subscriber** is a node that receives data from a topic. In order for these nodes to communicate properly their publishers and subscribers must be sending and receiving the **same type of message.**

Running the command:
- `ros2 interface show <package_name>/msg/<msg_name>`
Will return you the information that the `<msg_name>` is expected to carry. 

### Topic Publish:
Assuming you have properly structured the message you are ready to transmit from the node to the topic, you can run the following command line prompt to:
- `ros2 topic pub <topic_name> <msg_type> '<args>'`
	- Where `'<args>'` is the actual data you'll pass to the topic.

### Topic hz:
To view the rate at which data is being published you can run the following command:
- `ros2 topic hz <topic_name>`

### Topic Bandwidth:
To view the bandwidth used by the topic you can run the following command:
- `ros2 topic bw <topic_name>`