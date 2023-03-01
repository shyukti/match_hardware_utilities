#Automatic launch at the boot

##Commands for install:
'''
sudo apt-get install ros-noetic-robot-upstart
'''
'''
rosrun robot_upstart install ps4_controller/launch/single_mir_ps4_drive.launch --job start_ps4 --symlink --master http://mir:11311 --setup /home/rosmatch/catkin_ws_yukti/devel/setup.bash --rosdistro noetic  --user rosmatch
'''

--setup add path to the workspace

##Create a new file named “local.rules” in /etc/udev/rules.d/.

'''
cd /etc/udev/rules.d/
sudo touch local.rules
'''

##Test:

Connect ps4 by pressing both shoulder buttons at the same time and releasing at the same time. Blue light will be visible on the controller.

'''
sudo systemctl daemon-reload

sudo systemctl start start_ps4.service

export ROS_MASTER_URI=http://mir:11311

rostopic echo  rostopic echo /ps4_input

sudo systemctl stop start_ps4.service

rostopic echo  rostopic echo /ps4_input
'''

##Documentation:

http://docs.ros.org/en/jade/api/robot_upstart/html/