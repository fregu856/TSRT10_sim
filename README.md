# TSRT10_sim

Needed:  

Ubuntu 16.04.1  
ROS Kinetic  
ros-kinetic-turtlebot  
ros-kinetic-turtlebot-apps  
ros-kinetic-turtlebot-interactions  
ros-kinetic-turtlebot-simulator  
catkin

Reset the ROS IP addresses:
- Make sure that the lines with ROS_MASTER_URI and ROS_HOSTNAME in ~/.bashrc looks as below:
```
export ROS_MASTER_URI=http://localhost:11311
export ROS_HOSTNAME=localhost
```
- $ source ~/.bashrc

Create a catkin workspace:
- $ cd TSRT10_sim
- $ mkdir catkin_ws
- $ cd catkin_ws
- $ mkdir src
- $ catkin_make
- Add "source ~/TSRT10_sim/catkin_ws/devel/setup.bash" to the bottom of ~/.bashrc ($ sudo nano ~/.bashrc to edit, we do this for this line to be run everytime we open the terminal, otherwise we'd have to do it manually)  
- $ source ~/TSRT10_sim/catkin_ws/devel/setup.bash

Create a package in the workspace:
- $ cd ~/TSRT10_sim/catkin_ws/src  
- $ catkin_create_pkg Balrog std_msgs roscpp rospy  
- $ cd ~/TSRT10_sim/catkin_ws  
- $ catkin_make   

Create a python_scripts directory in the package:
- $ cd ~/TSRT10_sim/catkin_ws/src/Balrog  
- $ mkdir python_scripts  

Every python script that you write (and place in python_scripts) must be made executable:
- $ chmod a+x test.py    
You should also build the package:
- $ cd ~/TSRT10_sim/catkin_ws  
- $ catkin_make  

Simulation in Gazebo:
- $ cd ~/TSRT10_sim/catkin_ws/src  
- $ git clone https://github.com/StanfordASL/asl_turtlebot.git  
- $ cd ~/TSRT10_sim/catkin_ws    
- $ catkin_make  
- Add "export GAZEBO_MODEL_PATH=~/TSRT10_sim/catkin_ws/src/asl_turtlebot/models" to the bottom of ~/.bashrc ($ sudo nano ~/.bashrc to edit, we do this for this line to be run everytime we open the terminal, otherwise we'd have to do it manually)
- $ export GAZEBO_MODEL_PATH=~/TSRT10_sim/catkin_ws/src/asl_turtlebot/models

Test the simulation:
- $ roslaunch asl_turtlebot turtlebot_sim.launch  

If this doesn't work, open another terminal and do this FIRST:
- $ rosrun gazebo_ros gzclient  

Run a test controller to check that everything is working:  
- Place "test_controller.py" in ~/TSRT10_sim/catkin_ws/src/Balrog/python_scripts, make it executable and build the package.  
- $ roslaunch asl_turtlebot turtlebot_sim.launch  
- $ rosrun Balrog test_controller.py (in another terminal)  
- The robot should now move to the coordinate (1, 1).    

Simulate the robot in the TSRT10 test area:
- Create a launch directory in ~/TSRT10_sim/catkin_ws/src/Balrog.
- Place the file Balrog_launch.launch in the launch directory.



Test area:
- The square is 8x8 meters.
- All obstacles are 1x1 meter squares.


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


