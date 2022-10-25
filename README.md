# week-4-Smart-Mobility


First of all, make sure your system is up-to-date
```
sudo apt update
```

Install the turtlesim library
```
elbek@elbek-virtual-machine:~$ sudo apt install ros-rolling-turtlesim
Reading package lists... Done
Building dependency tree       
Reading state information... Done
....

```

To start turtlesim, enter the following command in your terminal

```
elbek@elbek-virtual-machine:~$ ros2 run turtlesim turtlesim_node
[INFO] [1663638092.636082943] [turtlesim]: Starting turtlesim with node name /turtlesim
[INFO] [1663638092.645975073] [turtlesim]: Spawning turtle [turtle1] at x=[5.544445], y=[5.544445], theta=[0.000000]
```

![image](https://user-images.githubusercontent.com/65524183/197665832-d37c9a93-3219-478b-bf8d-fbf6feac7289.png)




To control the turtle type the following command:

```
elbek@elbek-virtual-machine:~$ ros2 run turtlesim turtle_teleop_key
Reading from keyboard
---------------------------
Use arrow keys to move the turtle.
Use G|B|V|C|D|E|R|T keys to rotate to absolute orientations. 'F' to cancel a rotation.
'Q' to quit.

```
RQT: installation

```
#  MAKE SURE YOUR SYSTEM IS UP-TO-DATE
elbek@elbek-virtual-machine:~$ sudo apt update

# INSTALL THE RQT LIBRARY AND ITS PLUGINS
elbek@elbek-virtual-machine:~$ sudo apt install ~nros-rolling-rqt*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  pybind11-dev ros-rolling-class-loader
  ...
# To run rqt by just typing command "rqt"
elbek@elbek-virtual-machine:~$ rqt
```


RQT: running rqt_console

```
elbek@elbek-virtual-machine:~$ ros2 run rqt_console rqt_console
```

Turtlesim simulation

```
# RUN THE TURTLESIM_NODE IN A NEW TAB
elbek@elbek-virtual-machine:~$:~$ ros2 run turtlesim turtlesim_node
[INFO] [1664067181.891114659] [turtlesim]: Starting turtlesim with node name /turtlesim
[INFO] [1664067181.940055496] [turtlesim]: Spawning turtle [turtle1] at x=[5.544445], y=[5.544445], theta=[0.000000]
# RUN THE TURTLE_TELEOP_KEY TO MOVE THE TURTLE IN A NEW TAB
elbek@elbek-virtual-machine:~$:~$ ros2 run turtlesim turtle_teleop_key
Reading from keyboard
---------------------------
Use arrow keys to move the turtle.
Use G|B|V|C|D|E|R|T keys to rotate to absolute orientations. 'F' to cancel a rotation.
'Q' to quit.
#RUN THE rqt in your terminal
elbek@elbek-virtual-machine:~$:~$ rqt
#CHANGE THE /SPAWN SERVICE PARAMETERS TO RUN TURTLE2
#TO RUN THE TURTLE TO RUN THIS COMMAND
elbek@elbek-virtual-machine:~$:~$ ros2 run turtlesim turtle_teleop_key --ros-args --remap turtle1/cmd_vel:=turtle2/cmd_vel
Reading from keyboard
---------------------------
Use arrow keys to move the turtle.
Use G|B|V|C|D|E|R|T keys to rotate to absolute orientations. 'F' to cancel a rotation.
'Q' to quit.


```


TURTLE simulation 

![image](https://user-images.githubusercontent.com/65524183/197666521-801fbdfd-62df-4df4-81d5-0042369dfa06.png)

ROS2 Colcon
```
# INSTALLING Colcon
elbek@elbek-virtual-machine:~$:~$ sudo apt install python3-colcon-common-extensions
[sudo] password for ulugbekmirzabakhromov: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python3-colcon-common-extensions is already the newest version (0.3.0-1).
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

-----------------------------------
 # ROS2 Colcon: Create a workspace
 ----------------------------------
elbek@elbek-virtual-machine:~$:~$ echo "source /usr/share/colcon_cd/function/colcon_cd.sh" >> ~/.bashrc
elbek@elbek-virtual-machine:~$:~$ echo "export _colcon_cd_root=/opt/ros/rolling/" >> ~/.bashrc
elbek@elbek-virtual-machine:~$:~$ source /opt/ros/rolling/setup.bash
elbek@elbek-virtual-machine:~$:~$ mkdir -p ~/ros2_ws/src
elbek@elbek-virtual-machine:~$:~$ cd ~/ros2_ws
elbek@elbek-virtual-machine:~$:~/ros2_ws$ git clone https://github.com/ros/ros_tutorials.git -b rolling-devel
Cloning into 'ros_tutorials'...
remote: Enumerating objects: 2841, done.
remote: Counting objects: 100% (161/161), done.
remote: Compressing objects: 100% (88/88), done.
remote: Total 2841 (delta 93), reused 131 (delta 71), pack-reused 2680
Receiving objects: 100% (2841/2841), 617.66 KiB | 7.72 MiB/s, done.
Resolving deltas: 100% (1710/1710), done.
# RESOLVE DEPENDENCIES
elbek@elbek-virtual-machine:~$:~/ros2_ws$ rosdep install -i --from-path src --rosdistro rolling -y
All required rosdeps installed successfully

# BUILD THE WORKSPACE WITH Colcon
elbek@elbek-virtual-machine:~$:~/ros2_ws$ colcon build
[1.070s] WARNING:colcon.colcon_core.package_selection:Some selected packages are already built in one or more underlay workspaces:
	'turtlesim' is in: /opt/ros/rolling, /opt/ros/foxy
If a package in a merged underlay workspace is overridden and i
...
This may be promoted to an error in a future release of colcon-override-check.
Starting >>> turtlesim
[Processing: turtlesim]                             
[Processing: turtlesim] 
....
# SOURCE THE OVERLAY
elbek@elbek-virtual-machine:~$:~$ source /opt/ros/rolling/setup.bash
elbek@elbek-virtual-machine:~$:~$ cd ~/ros2_ws
elbek@elbek-virtual-machine:~$:~/ros2_ws$ . install/local_setup.bash
# MODIFY THE OVERLAY
elbek@elbek-virtual-machine:~$:~/ros2_ws$ cd src
elbek@elbek-virtual-machine:~$:~/ros2_ws/src$ ls
elbek@elbek-virtual-machine:~$:~/ros2_ws/src$ git clone https://github.com/ros/ros_tutorials
Cloning into 'ros_tutorials'...
remote: Enumerating objects: 2841, done.
remote: Counting objects: 100% (161/161), done.
remote: Compressing objects: 100% (88/88), done.
remote: Total 2841 (delta 93), reused 131 (delta 71), pack-reused 2680
Receiving objects: 100% (2841/2841), 617.66 KiB | 855.00 KiB/s, done.
Resolving deltas: 100% (1710/1710), done.
elbek@elbek-virtual-machine:~$:~/ros2_ws/src$ ls
ros_tutorials
elbek@elbek-virtual-machine:~$:~/ros2_ws/src$ cd ros_tutorials
elbek@elbek-virtual-machine:~$:~/ros2_ws/src/ros_tutorials$ ls
roscpp_tutorials  rospy_tutorials  ros_tutorials  turtlesim
elbek@elbek-virtual-machine:~$:~/ros2_ws/src/ros_tutorials$ cd turtlesim/src
elbek@elbek-virtual-machine:~$:~/ros2_ws/src/ros_tutorials/turtlesim/src$ ls
turtle.cpp  turtle_frame.cpp  turtlesim  turtlesim.cpp
elbek@elbek-virtual-machine:~$:~/ros2_ws/src/ros_tutorials/turtlesim/src$ nano turtle_frame.cpp

```

Create a package

```
elbek@elbek-virtual-machine:~$:~/ros2_ws/src$ ros2 pkg create --build-type ament_python --node-name my_node my_package
going to create a new package
package name: my_package
destination directory: /home/ulugbekmirzabakhromov/ros2_ws/src
package format: 3
version: 0.0.0
...
elbek@elbek-virtual-machine:~$:~/ros2_ws/src$ cd ..

# BUILDING PACKAGES
elbek@elbek-virtual-machine:~$:~/ros2_ws$ colcon build            
Summary: 3 packages finished [4.08s]
elbek@elbek-virtual-machine:~$:~/ros2_ws$ colcon build --packages-select my_package
Starting >>> my_package
Finished <<< my_package [1.14s]          
Summary: 1 package finished [1.37s]

#SOURCE THE SETUP FILE
elbek@elbek-virtual-machine:~$:~/ros2_ws$ . install/setup.bash
elbek@elbek-virtual-machine:~$:~/ros2_ws$ ros2 run my_package my_node
Hi from my_package.

```

Writing a publisher and subscriber(Python)

```
#MAKE SURE YOU ARE IN THE src FOLDER AND ENTER THE COMMAND FOR CREATING THE PY_PACKAGE
elbek@elbek-virtual-machine:~$:~$ cd ~/ros2_ws
elbek@elbek-virtual-machine:~$:~/ros2_ws/src$ ros2 pkg create --build-type ament_python py_pubsub
going to create a new package
package name: py_pubsub
destination directory: /home/ulugbekmirzabakhromov/ros2_ws/src
package format: 3
version: 0.0.0
...
elbek@elbek-virtual-machine:~$:~/ros2_ws/src$ ls
my_package  my_pkg  py_pubsub  ros_tutorials
elbek@elbek-virtual-machine:~$:~/ros2_ws/src$ wget https://raw.githubusercontent.com/ros2/examples/foxy/rclpy/topics/minimal_publisher/examples_rclpy_minimal_publisher/publisher_member_function.py
--2022-09-27 21:42:13--  https://raw.githubusercontent.com/ros2/examples/foxy/rclpy/topics/minimal_publisher/examples_rclpy_minimal_publisher/publisher_member_function.py
...
2022-09-27 21:42:14 (11.5 MB/s) - ‘publisher_member_function.py’ saved [1576/1576]

#DOWNLOAD THE publisher_member_function.py TO ros2_ws/src/py_pubsub/py_pubsub DIRECTORY

elbek@elbek-virtual-machine:~$:~/ros2_ws/src/py_pubsub/py_pubsub$ wget https://raw.githubusercontent.com/ros2/examples/foxy/rclpy/topics/minimal_publisher/examples_rclpy_minimal_publisher/publisher_member_function.py
--2022-09-27 22:19:36--  https://raw.githubusercontent.com/ros2/examples/foxy/rclpy/topics/minimal_publisher/examples_rclpy_minimal_publisher/publisher_member_function.py
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.111.133, 185.199.108.133, 185.199.109.133, ...
...
2022-09-27 22:19:37 (31.7 MB/s) - ‘publisher_member_function.py’ saved [1576/1576]

#ALSO DOWNLOAD THE subscriber_member_function.py 
elbek@elbek-virtual-machine:~$:~/ros2_ws/src/py_pubsub/py_pubsub$ wget https://raw.githubusercontent.com/ros2/examples/foxy/rclpy/topics/minimal_subscriber/examples_rclpy_minimal_subscriber/subscriber_member_function.py
...
2022-09-27 21:54:36 (18.1 MB/s) - ‘subscriber_member_function.py’ saved [1469/1469]



```


Build and run

```
elbek@elbek-virtual-machine:~$:~/ros2_ws$ rosdep install -i --from-path src --rosdistro foxy -y
#All required rosdeps installed successfully
elbek@elbek-virtual-machine:~$:~/ros2_ws$ colcon build --packages-select py_pubsub
Starting >>> py_pubsub
Finished <<< py_pubsub [2.89s]          

Summary: 1 package finished [4.10s]
elbek@elbek-virtual-machine:~$:~/ros2_ws$ rosdep install -i --from-path src --rosdistro foxy -y
#All required rosdeps installed successfully
elbek@elbek-virtual-machine:~$:~/ros2_ws$ colcon build --packages-select py_pubsub
Starting >>> py_pubsub
Finished <<< py_pubsub [1.41s]          

Summary: 1 package finished [1.66s]

---------------------------------------
# TESTING THE NODES
---------------------------------------
elbek@elbek-virtual-machine:~$:~/ros2_ws$ . install/setup.bash
elbek@elbek-virtual-machine:~$:~/ros2_ws$ ros2 run py_pubsub talker
[INFO] [1664342591.577268871] [minimal_publisher]: Publishing: "Hello World: 0"
[INFO] [1664342592.061454408] [minimal_publisher]: Publishing: "Hello World: 1"
[INFO] [1664342592.562140724] [minimal_publisher]: Publishing: "Hello World: 2"
[INFO] [1664342593.062828040] [minimal_publisher]: Publishing: "Hello World: 3"
elbek@elbek-virtual-machine:~$:~/ros2_ws$ . install/setup.bash
elbek@elbek-virtual-machine:~$:~/ros2_ws$ ros2 run py_pubsub talker
[INFO] [1664342591.577268871] [minimal_publisher]: Publishing: "Hello World: 0"
[INFO] [1664342592.061454408] [minimal_publisher]: Publishing: "Hello World: 1"
[INFO] [1664342592.562140724] [minimal_publisher]: Publishing: "Hello World: 2"
[INFO] [1664342593.062828040] [minimal_publisher]: Publishing: "Hello World: 3"

```

Writing a simple service and client(Python)

```

#Firstly, create the package into the ros2_ws/src directory
------------------------------------------------------------
elbek@elbek-virtual-machine:~$:~$ cd ros2_ws
elbek@elbek-virtual-machine:~$:~/ros2_ws$ cd src
elbek@elbek-virtual-machine:~$:~/ros2_ws/src$ ros2 pkg create --build-type ament_python py_srvcli --dependencies rclpy example_interfaces
going to create a new package
package name: py_srvcli
....

# Write the service node inside the ros2_ws/src/py_srvcli/py_srvcli directory:
------------------------------------------------------------------------------
elbek@elbek-virtual-machine:~$:~/ros2_ws/src/py_srvcli$ nano service_member_function.py
elbek@elbek-virtual-machine:~$:~/ros2_ws/src/py_srvcli$ nano client_member_function.py

# Add an entry points into the setup.py to be able to run the servic&client nodes.
----------------------------------------------------------------------------------
elbek@elbek-virtual-machine:~$:~/ros2_ws/src/py_srvcli$ nano setup.py

```


# BUILD AND RUN


```
# BUILD AND RUN
----------------
elbek@elbek-virtual-machine:~$:~/ros2_ws$ rosdep install -i --from-path src --rosdistro foxy -y
#All required rosdeps installed successfully
elbek@elbek-virtual-machine:~$:~/ros2_ws$ colcon build --packages-select py_srvcli
Starting >>> py_srvcli
Finished <<< py_srvcli [2.13s]          
Summary: 1 package finished [2.48s]

# Open a new terminal, navigate to ros2_ws, and source the setup files
----------------------------------------------------------------------
elbek@elbek-virtual-machine:~$:~/ros2_ws$ . install/setup.bash
elbek@elbek-virtual-machine:~$:~/ros2_ws$ ros2 run py_srvcli service
[INFO] [1664849371.615817085] [minimal_service]: Incoming request
a: 2 b: 3
# Do the same thing for the client node
elbek@elbek-virtual-machine:~$:~/ros2_ws$ . install/setup.bash
elbek@elbek-virtual-machine:~$:~/ros2_ws$ ros2 run py_srvcli client 2 3
[INFO] [1664849371.665846561] [minimal_client_async]: Result of add_two_ints: for 2 + 3 = 5

```
#Writing an action server and client(Python)
```
#Writing an action server
-------------------------
elbek@elbek-virtual-machine:~$ nano fibonacci_action_server.py

#You can get the action_server code from this link:
---------------------------------------------------

```

