# ROS2 

Learning the basics of ROS through a crash course

Tutorial Youtube link - https://www.youtube.com/watch?v=Gg25GfA456o

## turtle controller 

After installing **Ubunutu 22.04 and ROS2 humble**
### run
```
source .bashrc
colcon build --symlink-install
ros2 run my_robot_controller turtle_controller 
ros2 run turtlesim turtlesim_node
```
in different terminal windows to see the magic happen.


ROS Basics
==========

1. ROS is a Middleware that will handle the message passing & comm

	+ Event based communication channel

2. Pakage management 

	ROS1 -> Catkin vs  ROS2 -> colcon
	* Design - Make it modular enough so that you can work on packages in isolation.

3. Harware abstraction

	+ Use ROS as a API wrapper for your specific hardware


messages (Async communication)
-------------
It is a Topic - topic of interest for both all the parties interested in the topic

Publisher - talks about this Topic
subscriber - subs to the topic

Services
-----------
Battery status -> ask actuation through the service
Service client ask whenever it wants to WHATEVER it wants. Specify "Motor" for eg.
Who wants the info initiates the action. But once asked it cannot cancel this request.
 Something is always sent here. In ROS2 service is not blocking as in ros 1
 
 Actions
 ----------
 Move the robot to x,y,z postion.
 Will provide real time feedback of where it is.
 There is always an option to cancel an action while beiing implemented
 
 
 ## ROS1											
 1. Own middleware				
 2. Has a ROS MASTER - The system fails if the MASTER fails Communicate directly
 3. No shared codebase. Different thread.
 4. Cannot create multiple ros nodes in 1 Process
 5. Action service ( whatever that is not availbale in 1 but there in 2)
 6. Windows not supported
 7. Change in launch infrastructure - Ros2 has Python based ROS files as well
 8. Limited Updates for future

## ROS2

1. 3rd party middleware(DDS)
2. There is no ROS MASTER 
3. Shared codebase in Python and cpp 
4. In ROS2 you can do that
5. Promised updates for the future 

ROS Bridge helps in migeration
Ros2 building tool - colcon

We will write nodes inside packages - It will help organize the code and dependencies in a better way.

```
ros2 pkg create my_robot_controller --build-type ament_python --dependencies rclpy
```


# Service & Topics
when a client server interaction is required

## When to use a topic & Service?
Topics are used to send data streams, without feedback

When you need to compute something and expect some answer you need Services