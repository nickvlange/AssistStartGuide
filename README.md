markdown

# Virtual Reality Robotics Setup Guide

## Prerequisites
1. Download and install [VMware Workstation Player](https://www.vmware.com/nl/products/workstation-player/workstation-player-evaluation.html).
2. Open the premade virtual machine.
   - **Virtual Machine Password:** magicleap10
   - Ensure the network adapter is set to "Host Only" when connecting to Unity. Change to "NAT" if internet access is required.

## ROS Setup
1. Open a terminal and navigate to the workspace:
   ```shell
   cd catkin_ws

    Configure network settings:
        Confirm the network adapter is set to localhost.
        Run the following command to find the IP address:

        shell

    ifconfig

    Identify the IP address (e.g., 192.168.247.128).

Test communication:

    On the host machine, open a terminal and run:

    shell

    ping <your_ip>

In Unity, set the IP address:

    In the Robotics tab, under ROS Settings, set the ROS IP address.
    In the scene, find the RosConnection object and set the ROS IP address.

Start TCP connection in a terminal:

shell

source devel/setup.bash
roslaunch ros_tcp_connection endpoint.launch

Start haptic feedback controller in a different shell:

shell

    source devel/setup.bash
    roslaunch omega_x haptic_feedback.launch

Magic Leap Setup

    Open Magic Leap Hub and connect the Magic Leap2 device to your PC using a USB-C cable.
        Ensure the device connects to your machine, not the VM.

    Start the Simulator application in Magic Leap Hub.

    Set global dimming in Magic Leap device settings.

Unity Setup

    Play the scene in Unity.
    In the TCP connection terminal, confirm Unity establishes a connection.
    The Unity scene should display, confirming successful setup.

Note: The provided IP address is an example; replace it with the actual IP obtained from ifconfig.

This guide assumes a working knowledge of ROS, Unity, and Magic Leap development environments. For detailed troubleshooting, refer to respective documentation.

csharp


Copy and paste this content into your README.md file.
