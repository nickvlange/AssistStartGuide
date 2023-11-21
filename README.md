Start by downloading vmWare https://www.vmware.com/nl/products/workstation-player/workstation-player-evaluation.html

Open the premade virtual machine. 
Password: magicleap10

Some of the options of the virtual machine might have to be changed,
make sure that network adapter is host only when connecting to unity, this option can be changed to nat while the vm is running if you require internet. 

To start up the ros side open a terminal 
go to the ws

```shell
cd catkin_ws
```

first we have to make sure we can communicate through the local host, we might have to adjust the ip settings in unity.  Make sure that that the network adapter is set to localhost then, to find out what the right ip settings are run:

```shell
ifconfig
```

You should get something like:
![[Pasted image 20231110102449.png]]
In this case the right ip is 192.168.247.128 Check if you can communicate to it by opening a terminal on your host machine and running
```
ping <your_ip>
```

Then in Unity set this ip at two places:
in the robotics tab ROS settings ROS IP address
and in the scene find the RosConnection object and set the ROS IP Addres

to start the tcp connection run:
```shell
source devel/setup.bash
roslaunch ros_tcp_connection endpoint.launch
```
This also starts a roscore

To start the haptic feedback controller run in a different shell:
```shell
source devel/setup.bash
roslaunch omega_x haptic_feedback.launch
```

Open magic leap hub and connect the magic leap2 with the usb c cable to your pc, be sure that the device connects to your machine and not the vm. Start the application Simulator in magic leap hub. Due to the connection being made over the simulation the global dimming needs to be set in the device settings of the magic leap. 

finally on the unity side play the scene. In the tcp connection terminal it should show that unity made connection, you should see the scene in unity. 
