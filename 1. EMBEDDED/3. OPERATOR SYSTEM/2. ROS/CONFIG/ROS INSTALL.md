Guía de Instalación ROS Noetic, adjunta en la wiki [^1] .

```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

sudo apt install curl

curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -

sudo apt update

sudo apt install ros-noetic-desktop-full
```

Para sourcear por defecto el setup.bash general

```
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
	source ~/.bashrc
```

[^1]: https://wiki.ros.org/noetic/Installation/Ubuntu
