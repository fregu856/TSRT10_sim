# TSRT10_sim

Needed:  

Ubuntu 16.04.1  
ROS Kinetic  
ros-kinetic-turtlebot  
ros-kinetic-turtlebot-apps  
ros-kinetic-turtlebot-interactions  
ros-kinetic-turtlebot-simulator  
catkin

Create a catkin workspace:
- $ cd TSRT10_sim
- $ mkdir catkin_ws
- $ cd catkin_ws
- $ mkdir src
- $ catkin_make

Add "source ~/TSRT10_sim/catkin_ws/devel/setup.bash" to the bottom of ~/.bashrc ($ sudo nano ~/bashrc) for this line to be run everytime you open the terminal (otherwise you have to do it manually).  

Create a package in the workspace:  
$ cd AA203/AA203_project/catkin_ws/src  
$ catkin_create_pkg turtlebot_control std_msgs roscpp rospy  
$ cd AA203/AA203_project/catkin_ws  
$ catkin_make   

Create a scripts directory in the package:  
$ cd AA203/AA203_project/catkin_ws/src/turtlebot_control  
$ mkdir scripts  

Every script that you write must be made executable:  
$ chmod a+x script.py    
You should also build the package:  
$ cd AA203/AA203_project/catkin_ws  
$ catkin_make  

Simulation in Gazebo:  
$ cd AA203/AA203_project/catkin_ws/src  
$ git clone https://github.com/StanfordASL/asl_turtlebot.git  
$ cd AA203/AA203_project/catkin_ws    
$ catkin_make  
Add "export GAZEBO_MODEL_PATH=~/AA203/AA203_project/catkin_ws/src/asl_turtlebot/models" to the bottom of ~/.bashrc ($ sudo nano ~/bashrc) for this line to be run everytime you open the terminal (otherwise you have to do it manually).  

Test the simulation:  
$ roslaunch asl_turtlebot turtlebot_sim.launch  
If this doesn't work, open another terminal and do this FIRST:  
$ rosrun gazebo_ros gzclient  

Run a test controller to check that everything is working:  
Place "test_controller.py" in ~/AA203/AA203_project/catkin_ws/src/turtlebot_control/scripts, make it executable and build the package.  
$ roslaunch asl_turtlebot turtlebot_sim.launch  
$ rosrun turtlebot_control test_controller.py (in another terminal)  
The robot should now move to the coordinate (1, 1).    

*******

Run the AA274 project code:  
Create a directory called "launch" in catkin_ws/src/turtlebot_control  
Place "AA274_project.launch" in catkin_ws/src/turtlebot_control/launch  
$ roslaunch asl_turtlebot turtlebot_project_sim.launch  
$ roslaunch turtlebot_control AA274_project.launch  
$ rosrun turtlebot_control mission_publisher.py  

Tele-op:  
$ roslaunch kobuki_keyop keyop.launch  

*****

Launch the modified maze (maze3.world) and Gmapping:  
$ roslaunch asl_turtlebot turtlebot_maze.launch


