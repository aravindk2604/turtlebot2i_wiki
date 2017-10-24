.. _chapter_softwareSetup:

Software Setup (Includes ROS instructions)
==========================================

Setup your sources.list
~~~~~~~~~~~~~~~~~~~~~~~

::

    sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

Set up your keys
~~~~~~~~~~~~~~~~

::

    sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 421C365BD9FF1F717815A3895523BAEEB01FA116
    sudo apt update && sudo apt upgrade

Optional
~~~~~~~~

::

    sudo apt remove libreoffice*
    
VNC/remote ssh Setup
~~~~~~~~~~~~~~~~~~~~

::

    sudo apt install vino ssh gedit
    vino-preferences

Check
~~~~~

- Allow other users to view your desktop
- Allow other users to control your desktop

Uncheck
~~~~~~~

- You must confirm each access to this machine.

.. Note:: Disable require-encryption if your VNC client does not support it.

Ubuntu
~~~~~~

::

    gsettings set org.gnome.Vino require-encryption false

Ubuntu Mate
~~~~~~~~~~~

**Add to startup group on Mate:**

- System > Control Center > Startup Applications
- Click "Add" Button
- Name: Remote Desktop
- Command Path: /usr/lib/vino/vino-server

ROS Kinetic Dependencies & Install
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

::

    sudo apt install git build-essential ros-kinetic-desktop
    sudo rosdep init
    rosdep update
    apt-cache search ros-kinetic (not actual dependency)

RealSense ROS Package Install
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`Check Prerequisites <http://wiki.ros.org/librealsense#Installation_Prerequisites>`_

::

    wget -O enable_kernel_sources.sh http://bit.ly/en_krnl_src
    bash ./enable_kernel_sources.sh

**Sensor package**

::

    sudo apt install ros-kinetic-librealsense ros-kinetic-realsense-camera

**Kernel 4.10 installation work-around**

::

    sudo apt-get install libglfw3-dev
    cd ~
    git clone https://github.com/IntelRealSense/librealsense.git
    cd librealsense
    mkdir build && cd build
    cmake ../
    make && sudo make install
    cd ..
    sudo cp config/99-realsense-libusb.rules /etc/udev/rules.d/
    sudo udevadm control --reload-rules && udevadm trigger
    ./scripts/patch-realsense-ubuntu-xenial.sh


TurtleBot 2i ROS Package Install
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

::

    sudo apt install ros-kinetic-turtlebot* libudev-dev ros-kinetic-find-object-2d ros-kinetic-rtabmap-ros ros-kinetic-moveit ros-kinetic-octomap-ros ros-kinetic-manipulation-msgs ros-kinetic-controller-manager python-wxgtk3.0

Setup TurtleBot2i Source Code & Catkin Environment
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

::

    source /opt/ros/kinetic/setup.bash
    cd ~
    mkdir -p ~/turtlebot2i/src
    cd ~/turtlebot2i/src
    git clone https://github.com/Interbotix/turtlebot2i.git .
    git clone https://github.com/Interbotix/arbotix_ros.git -b turtlebot2i
    git clone https://github.com/Interbotix/phantomx_pincher_arm.git
    git clone https://github.com/Interbotix/ros_astra_camera -b filterlibrary
    git clone https://github.com/Interbotix/ros_astra_launch
    cd ~/turtlebot2i
    catkin_make
    
bashrc setup
~~~~~~~~~~~~

- You will need to place the following at the bottom of your ~/.bashrc file
- Edit .bashrc with your choice of editor ( gedit, nano, vi )
- Be sure to replace example.hostname with your computer's hostname

::

    source /opt/ros/kinetic/setup.bash
    alias goros='source devel/setup.sh'
    export ROS_HOSTNAME=example.hostname
    export TURTLEBOT_3D_SENSOR=astra
    export TURTLEBOT_3D_SENSOR2=sr300
    export TURTLEBOT_BATTERY=None
    export TURTLEBOT_STACKS=interbotix
    export TURTLEBOT_ARM=pincher

dialout permission
~~~~~~~~~~~~~~~~~~

::

    sudo usermod -a -G dialout turtlebot

udev rules
~~~~~~~~~~

::

    cd ~/turtlebot2i/
    goros
    rosrun kobuki_ftdi create_udev_rules
    rosrun astra_camera create_udev_rules
    cd ~/turtlebot2i/src/turtlebot2i_misc
    gedit 99-turtlebot2i.rules

- At this point we need to execute a couple commands that will return the serial number for the ArbotiX and the Kobuki. Remove and/or Re-plug both the Arbotix and the Kobuki USB cables and ensure they are powered on before running these commands:

::

    udevadm info -a -n /dev/ttyUSB0 | grep '{serial}' | head -n1

    udevadm info -a -n /dev/ttyUSB1 | grep '{serial}' | head -n1

- The output from these commands are the serial numbers used to fill in the blanks of lines 6 and 7 of the 99-turtlebot2i.rules file.

::

    sudo cp ./99-turtlebot2i.rules /etc/udev/rules.d/

References
~~~~~~~~~~

- `<http://wiki.ros.org/kinetic/Installation/Ubuntu>`_
- `<http://ubuntuhandbook.org/index.php/2016/07/remote-access-ubuntu-16-04/>`_