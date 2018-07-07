# zoidberg_nav
navigation for zoidberg

Install
-------

This package is installed using catkin_make. Clone this repository into the

    catkin_workspace/src/

directory (fill in catkin_workspace with your specific catkin workspace
directory). The basic instructions for making the workspace are found in the
[Ros tutorial][RosT1]. Permanently source your local catkin workspace in the home .bashrc file. For instance, if you are in you catkin_workspace home folder,
```
cd devel
pwd
```
copy the pwd output, and type
```
echo "source <pwd output>/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

Once the zoiderg_nav package is in place, move to the base catkin_workspace
and run catkin_make

```
cd catkin_workspace
catkin_make
```

Once installed, this package defines a number of ROS messages related to
 navigation and a few ROS nodes. A launch file is used to set up navigation.

```
roslaunch zoidberg_nav zoidberg_nav.launch
```

This sets up a node "helm" that sits around and waits for commands. This command
will raise a fatal error if there is no Pixhawk attached to the computer.

Currently the script
```
rosrun zoidberg_nav navigation_client.py
```

is used to send commands. The current mission is meant to turn to a heading. If
there is a Pixhawk attached, the compass is used to construct proportional RC
commands. These commands can be seen to change on the rc rostopic as the pixhawk
is moved.
```
rostopic echo /apm/rc/out
```
The command will exit when the desired and current heading are within a
 tolerance, or if the timeout is reached.

[RosT1]: http://wiki.ros.org/ROS/Tutorials/InstallingandConfiguringROSEnvironment


