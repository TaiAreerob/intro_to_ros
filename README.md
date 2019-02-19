# Lab 1c: Intro to ROS
The objective of the following exercises is to help you practice the most commonly used concepts in ROS. We provide a quick reference document and pointers to relevant documentations. Feel free to use all the resources available to you to learn the concepts as thoroughly as possible and complete the exercises as efficiently as possible. 

Although you're encouraged to collaborate with others if you are stuck, the lab should be completed individually so you can get practice with skills that will be essential later on in the course when you are in teams. If you have general questions, please post on [Piazza](https://piazza.com/class/jrql7urlkqn189) so other students can benefit from the answer. If you have a question about your individual submission, please make a private post. 

## Grading
You're meant to complete this lab by testing your code and verifying the results on your own, as you would do in real life. Once you are confident in your answers, your lab will be graded against our automated tests, which will be released on Friday at 1pm. Please refer to Automated Tests (below) for instructions on how to run these tests.
           
This lab is due on **Wednesday, February 20th at 1:00PM EST**.

## Automated Tests 

The test suite we have made runs on entirely on it's own and tests to make sure you have completed all problems as defined. You can download the test binary by going to the [releases page of this repo](https://github.com/mit-rss/intro_to_ros/releases) and downloading the ```run_tests``` binary. **Make sure you place the binary in your ```ros_exercises``` folder.**:

    mv run_tests ~/catkin_ws/ros_exercises/
    
Then make the binary executable with ```chmod```

    chmod +x run_tests

First, kill all running ROS processes. Then start ```roscore```.

Finally, run the following in a new terminal to begin testing:

     cd ~/catkin_ws/ros_exercises/
    ./run_tests

You should be graded on the completion of 6 Tests. This will generate a log.npz file which you will upload on Gradescope. Your submission will not get graded properly if you don't put the files in the right format as defined in this handout.

If you have successfully completed all parts, you should receive a score of 3.0/4.0 on Gradescope. The rest of your score (1.0 points) will be a manual grading of your package ``ros_exercises`` by the staff of your git repository, which should be avaliable on your mit github account.

## References
The following are selected chapters from the ROS Wiki [Documentation](http://wiki.ros.org/) and [Tutorials](http://wiki.ros.org/ROS/Tutorials). If you understand all the concepts covered in these exercises, you should be ready for the following exercises and for most of the ROS related tasks you will be performing throughout the first few labs. For more on ROS, visit the [ROS Wiki](http://wiki.ros.org/) section and follow the links to learn more.

Additionally, reference this amazing ROS cheatsheet to get an overview of all the keywords [here!](https://github.com/ros/cheatsheet/releases/download/0.0.1/ROScheatsheet_catkin.pdf).

1. [Catkin](http://wiki.ros.org/catkin/conceptual_overview)   
2. Catkin Workspace   
	a. [Catkin workspaces](http://wiki.ros.org/catkin/workspaces)   
	b. [Creating Catkin workspace](http://wiki.ros.org/catkin/Tutorials/create_a_workspace)   
3. Packages   
	a. [ROS package](http://wiki.ros.org/Packages)   
	b. [Creating ROS package](http://wiki.ros.org/catkin/Tutorials/CreatingPackage)   
4. Messages   
	a. [ROS Messages](http://wiki.ros.org/Messages)   
	b. [Creating custom messages](http://wiki.ros.org/ROS/Tutorials/CreatingMsgAndSrv)   
	c. [The rosmsg command-line tools](http://wiki.ros.org/rosmsg)   
	d. [Common ros message categories](http://wiki.ros.org/common_msgs)   
5. Topics    
	a. [ROS Topics](http://wiki.ros.org/Topics)   
	b. [Rostopic Command-Line tool](http://wiki.ros.org/rostopic)   
6. Nodes   
	a. [ROS Nodes](http://wiki.ros.org/Nodes)   
	b. [The rosnode command-line tools](http://wiki.ros.org/rosnode)   
	c. [Writing Publisher and Subscriber(Python)](http://wiki.ros.org/ROS/Tutorials/WritingPublisherSubscriber%28python%29)   
7. Launch Files    
	a. [ROS Launch](http://wiki.ros.org/roslaunch)   
	b. [Command-line Tools](http://wiki.ros.org/roslaunch/Commandline%20Tools)   
	c. [XML Format](http://wiki.ros.org/roslaunch/XML)   
	d. [Tips for Large Projects](http://wiki.ros.org/roslaunch/Tutorials/Roslaunch%20tips%20for%20larger%20projects)   
8. Parameter server   
	a. [Parameter server](http://wiki.ros.org/Parameter%20Server)   
	b. [rosparam](http://wiki.ros.org/rosparam)   
9. Visualization Tools   
	a. RQT   
		- [RQT](http://wiki.ros.org/ROS/Tutorials/UnderstandingTopics)   
		- [RQT_GRAPH](http://wiki.ros.org/rqt_graph)   
	b. RVIZ   
		- [User Guide](http://wiki.ros.org/rviz/UserGuide)   
		- [Interactive Markers](http://wiki.ros.org/rviz/Tutorials/Interactive%20Markers%3A%20Getting%20Started)   
		- [Tutorials](http://wiki.ros.org/rviz/Tutorials)   
10. [TF](http://wiki.ros.org/tf)   
11. Rosbag   
	a. [Rosbag](http://wiki.ros.org/Bags)    
	b. [Command-Line Tools](http://wiki.ros.org/rosbag/Commandline)   


## ROS Exercises
### Create a package and build it
By following the instructions from the reference or instructions of your finding, create a catkin workspace and package named `catkin_ws/` and `ros_exercises/` respectively, and make sure that your workspace is built (using [catkin_make](http://wiki.ros.org/catkin/commands/catkin_make)) before and after the package was added. Your package (ros_exercises) should live in the `/src/` directory, where you add other packages (such as other labs later on). Make your "ros_exercises" a git repo. After creating the workspace and the package, you should have the following directory layout. 

* /catkin_ws[your catkin workspace] 
	* /src 
		* /ros_exercises[Your catkin package]
		* [other ros related files and packages if any]
	* /devel[automatically generated by catkin_make]
	* /build[automatically generated by catkin_make]

**Note**: Push your `ros_exercises/` package. 

Additionally, everytime you make an edit to your files, make sure to run `catkin_make` and source your `setup.bash` file.

## Question 1: Create Simple Publisher (Python)
Your task in this exercise is to create a simple ROS node that publishes a random number between 0 and 10.0. Before you start the following exercise, please make sure that your package is built properly. Note that this file will reside inside of the /ros_exercises folder of your newly created package. 

### Node Specification    
**Description:** Publishes a random number between 0 and 10.    
**File name:** simple_publisher.py    
**Node Name:** simple_publisher    
**Published topic names:** my_random_float    
**Message type:** Float32    
**Subscription topic names:** None    
**Publish rate:** 20hz    
### Commit Specification    
1. When your node works properly, take a screenshot of ***rqt_graph*** visualization of your node(s) and topic(s). Name your screenshot `simple_publisher_rqt.jpeg` and save it in `ros_exercises/rqt` (create the `rqt/` directory). Note: `ros_exercises/` is the ros package you created at the beginning of this section.
2. Push your code, the screenshot, and any supporting files with an appropriate commit message.

## Question 2: Create Simple Subscriber (Python)
In this exercise, you will write a listener (subscriber) that listens to the topic ***my_random_float***, which is published on to by the previous node. The node takes the natural log of the message on ***my_random_float*** and publishes it to ***random_float_log***.  

### Node Specification    
**Description:** Subscribes to the topic published on by the simple_publisher and publishes the natural log of the received messages.     
**File name:** simple_subscriber.py             
**Node Name:** simple_subscriber       
**Published topic names:** random_float_log    
**Message type:** Float32    
**Subscription topic names:** my_random_float   
### Commit Specification    
1. Again, take a screenshot of ***rqt_graph*** showing your nodes running, name it `simple_subscriber_rqt.jpeg`, and save it in the same folder as the previous exercise.
2. Again, push your code, the screenshot, and any supporting files with a appropriate commit message.

## Question 3: Create more Complex Publisher (Python)
In this exercise, you will write a node that publishes fake laser scan data as specified below.   
### Node Specification    
**Description:** Publish a [LaserScan](http://docs.ros.org/api/sensor_msgs/html/msg/LaserScan.html) message with random ranges between 1 and 10.     
**File name:** fake_scan_publisher.py             
**Node Name:** fake_scan_publisher       
**Published topic names:** fake_scan    
**Message type:** LaserScan    
**Subscription topic names:** None     
**Publish Rate:** 20hz   
### LaserScan Parameter Specifications
**Header:**       
	- **Timestamp:** Current ros time     
	- **Frame_id:** “base_link”     
**Angle_min:** (-2/3)*pi*     
**Angle_max:** (2/3)*pi*     
**Angle_increment:** (1/300)*pi*     
**Time_increment:** Leave it unset if you wish     
**Scan_time:** The time difference in seconds between consecutive scans.

**Range_min:** 1.0        
**Range_max:** 10.0       
**Ranges:** One dimensional array with elements of random floats between range_min and range_max, Use angle_min, angle_max,  and angle_increment to determine the length. Be careful of an off by 1 error! There should be an element **at** ```angle_min``` and ```angle_max```.
**Intensities:** Leave it unset if you wish      
### Commit Specification    
1. When your node works properly, visualize the published laser scan data using rviz. Take a screenshot of your visualized laser scan data and name it `fake_scan_rviz.jpeg`. Save the image in `ros_exercises/rviz`
2. Record a bag file of your laser scan data and call the file `fake_scan_bag.bag`, save it in `ros_exercises/rosbag`.
3. Again, push your code, bag file, screenshot, and any supporting files with a appropriate commit message.

**If you are failing this test make sure you have these files in your ```ros_exercises``` directory**:

- ```rviz/fake_scan_rviz.jpeg```
- ```rosbag/fake_scan_bag.bag```

## Question 4: Create a more complex Subscriber(Python)
Create a node that subscribes to the fake laser scan data and outputs the longest range from the laser scan ranges and its corresponding angle.    
### Node Specification    
**Description:** Subscribes to the fake_scan topic published on by the fake_scan_publisher from the previous exercises, and finds the longest return (the range element with the greatest value) and publishes the corresponding angle and return value or distance.    
**File name:** open_space_publisher.py    
**Node Name:** open_space_publisher    
**Published topic names:** open_space/distance and open_space/angle    
**Message type:** Float32    
**Subscription topic names:** fake_scan    
**Publish rate:** 20hz    
### Commit Specification    
1. Again, take a screenshot of ***rqt_graph*** showing your nodes running, named it `open_space_rqt.jpeg`, and save it in `ros_exercises/rqt`.
2. Again, push your code, the screenshot, and any supporting files with a appropriate commit message.

**If you are failing this test make sure you have these files in your ```ros_exercises``` directory**:

- ```rqt/open_space_rqt.jpeg```

## Question 5: Create a custom Message and Publish it
The publisher from the previous exercise was publishing two related pieces of data on two separate topics (***open_space/distance*** and ***open_space/angle***). In this exercise, we ask you to create a custom message that encapsulates the two pieces of data, the same way the LaserScan message type combines multiple pieces of data, and name your custom message file `OpenSpace.msg`. After creating and compiling your custom message, modify the publisher from the previous exercise to publish this message type on the topic ***open_space***. Hint: Don't forget to modify your `CMakeLists.txt` and `package.xml` files. 
### Commit Specification    
1. Commit your modified code, config/meta files, and your custom message file as well any supporting files.

## Question 6: Using launch files
If you have been running your publisher(s), subscriber(s), and roscore separately using the rosrun command, there’s a more organized way to run multiple nodes at same time with one command. 

In this exercise, we ask you to write a single launch file called `my_first_launch.launch` containing all 4 python files that you have written thus far.

### Commit Specification    
1. Commit your launch files. They should be inside a folder called `launch` inside your package.

## Question 7: Use ROS parameters
When writing the last publisher (***fake_scan_publisher***), you had a couple of variables with default values including angle_min, angle_max, range_min, range_max, etc. With the current setup, if you want to change the value of one of those variables you will have to edit the Python code. For hundreds of lines of code, finding where each of such variables is defined can be tedious. The rosparam server provides a way to set those parameters on the terminal when running your program and in launch or config files. You task here is to parameterize the following variables from the last two nodes.     
1. Fake Scan Publisher     
	* Publish topic      
	* Publish rate      
	* Angle_min     
	* Angle_max     
	* Range_min      
	* Range_max     
	* Angle_increment      
2. Open Space Publisher     
	* Subscriber topic     
	* Publisher topic     

### Commit Specification
1. Commit your modified nodes along with any other important changes.

## Question 8: Playing with bag files
In question 3, we asked you to visualize your laserscan data on rviz and record a bag file. The rviz visualization was probably meaningless and ugly because you’re publishing random data. Don’t be alarmed, real laserscan data is a lot prettier and informative. Download these [bagfiles](https://www.dropbox.com/sh/lvbtzph8qba3y8e/AAA2mTp0VxY-9DyJXcyA0GoHa), follow the instructions [here](http://wiki.ros.org/ROS/Tutorials/Recording%20and%20playing%20back%20data), and visualize the laser scan data on rviz. Try it with multiple coordinate frames.     
     
**Note**: the provided bag files are from our cars driving around in the basement of Stata center, where you will be using later.

## Debugging Hints
Here are some helpful tools to use when trying to debugging your code.

Helpful debugging tools (once a node is running):
1. `rostopic list`
A running node should be publishing or subscribing to different topics. To check that these topics are being listened/talked to, the command `rostopic list`, which will list all topics that are currently active (either being subscribed to, published to, or both).

2. `rostopic echo /topic_name`
Once you know that a command is being published/subscribed to, you can echo its contents, which can show whether or not any information is being passed across this topic or if you are not sending what you expect.

3. `rostopic hz /topic_name`
This command can tell you the rate at which messages are being published. This tool is helpful to verify if you are publishing messages at a certain frequency.

This page, http://wiki.ros.org/rostopic, from the ROS documentation can provide many other tools to debug your ROS node setup. 

4. ``rqt graph``: This is a tool to display graphs of running ROS nodes with connecting topics and package dependencies. Allows you to visualize your entire framework! Another helpful technique is to look at the RQT_GRAPH (http://wiki.ros.org/rqt_graph) which shows the interactions between nodes for your system.

5.  ``rviz``: This is a 3D visualizer tool for displaying sensor data and state information from ROS. You will be using it more extensively in future labs. 
