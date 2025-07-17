ExplORB-SLAM
============

A package for Active visual SLAM using the structure of the underlying pose-graph.

Code used for the paper "ExplORB-SLAM: Active Visual SLAM Exploiting the Pose-graph Topology", accepted for presentation in the Fifth Iberian Robotics Conference (ROBOT 2022).

Tested by jplaced for Ubuntu 20.04, ROS Noetic.

Contact: jplaced@unizar.es, jjgomez@unizar.es

Citation
------------

Placed, J. A., Gómez-Rodríguez, J. J., Tardós, J. D., & Castellanos, J. A. (2022). ExplORB-SLAM: Active Visual SLAM Exploiting the Pose-graph Topology. In 2022 Fifth Iberian Robotics Conference (ROBOT).

Detected dependencies:
------------
- Eigen
- OpenCV
- Python3
  * Numpy
  * Sklearn
  * Numba
  * OpenCV
- Gazebo
- ROS Noetic
  * rviz
  * turtlebot3_teleop
  * gazebo_ros
  * octomap_ros
  * octomap_rviz_plugins
  * move_base

# Dependency Installation Guide (ROS Noetic, Ubuntu 20.04)

Absolutely! Here is a **step-by-step installation and setup guide** for all the listed dependencies to implement a ROS Noetic project like ExplORB-SLAM or similar.
This assumes you are using **Ubuntu 20.04** (the standard for ROS Noetic).

---

## Step-by-Step Installation Guide

### 1. **Update System**

```bash
sudo apt update
sudo apt upgrade -y
```

---

### 2. **Install ROS Noetic**

* [Official Guide](http://wiki.ros.org/noetic/Installation/Ubuntu)

```bash
# Setup sources
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
sudo apt install curl
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
sudo apt update

# Install ROS Noetic Desktop-Full (includes rviz, turtlebot3_teleop, move_base, etc.)
sudo apt install ros-noetic-desktop-full

# Initialize rosdep
sudo rosdep init
rosdep update

# Add ROS setup to .bashrc
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc

# Install rosinstall tools
sudo apt install python3-rosinstall python3-rosinstall-generator python3-wstool build-essential
```

---

### 3. **Setup Catkin Workspace**

```bash
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws/
catkin_make
echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

---

### 4. **Install Core Libraries**

#### Eigen

```bash
sudo apt install libeigen3-dev
```

#### OpenCV

```bash
sudo apt install libopencv-dev python3-opencv
```

#### Python3

(Ubuntu 20.04 ships with Python3.8 by default)

#### Numpy, Sklearn, Numba (for Python)

```bash
pip3 install numpy scikit-learn numba
```

---

### 5. **Install ROS Packages**

#### rviz, move\_base, gazebo\_ros, octomap\_ros, octomap\_rviz\_plugins, turtlebot3\_teleop

```bash
sudo apt install ros-noetic-rviz \
                 ros-noetic-move-base \
                 ros-noetic-gazebo-ros-pkgs \
                 ros-noetic-octomap-ros \
                 ros-noetic-octomap-rviz-plugins \
                 ros-noetic-turtlebot3-teleop
```

* **Tip:** Some packages like `gazebo_ros` come with `gazebo_ros-pkgs`.

---

### 6. **Install Gazebo Simulator**

```bash
sudo apt install gazebo11
```

* If you need integration with ROS:

```bash
sudo apt install ros-noetic-gazebo-ros-control
```

---

### 7. **Clone/Build Your Project (e.g., ExplORB-SLAM)**

```bash
cd ~/catkin_ws/src
git clone https://github.com/WhiZTiM/ExplORB-SLAM.git   # replace with the actual repo
cd ~/catkin_ws
catkin_make
```

---

### 8. **(Optional) Setup TurtleBot3 Model Environment**

* If using TurtleBot3 for simulation:

```bash
echo "export TURTLEBOT3_MODEL=burger" >> ~/.bashrc
source ~/.bashrc
```

---

### 9. **Check Installations**

```bash
# Check ROS packages
roscd rviz
roscd move_base
roscd octomap_ros
roscd gazebo_ros

# Check Python libraries
python3 -c "import numpy, sklearn, numba, cv2; print('All Python libs imported successfully!')"
```

---

### 10. **Run a Quick Test**

* Test RViz:

```bash
roscore
# In a new terminal:
rviz
```

* Test Turtlebot3 teleop:

```bash
roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```

---

## Markdown Version

```markdown
# Dependency Installation Guide (ROS Noetic, Ubuntu 20.04)

## 1. System Update
sudo apt update && sudo apt upgrade -y

## 2. ROS Noetic Installation
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
sudo apt install curl
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
sudo apt update
sudo apt install ros-noetic-desktop-full
sudo rosdep init
rosdep update
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
sudo apt install python3-rosinstall python3-rosinstall-generator python3-wstool build-essential

## 3. Catkin Workspace
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws/
catkin_make
echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc
source ~/.bashrc

## 4. Core Libraries
sudo apt install libeigen3-dev
sudo apt install libopencv-dev python3-opencv
pip3 install numpy scikit-learn numba

## 5. ROS Packages
sudo apt install ros-noetic-rviz ros-noetic-move-base ros-noetic-gazebo-ros-pkgs ros-noetic-octomap-ros ros-noetic-octomap-rviz-plugins ros-noetic-turtlebot3-teleop

## 6. Gazebo Simulator
sudo apt install gazebo11
sudo apt install ros-noetic-gazebo-ros-control

## 7. Clone and Build Project
cd ~/catkin_ws/src
git clone [https://github.com/WhiZTiM/ExplORB-SLAM.git](https://github.com/Lawaries/ExplORB-SLAM-test.git)
cd ~/catkin_ws
catkin_make

## 8. TurtleBot3 Model (if used)
echo "export TURTLEBOT3_MODEL=burger" >> ~/.bashrc
source ~/.bashrc

## 9. Check Installations
python3 -c "import numpy, sklearn, numba, cv2; print('All Python libs imported successfully!')"
```

---

### **Notes:**

* Always source your workspace before launching nodes:

  ```bash
  source ~/catkin_ws/devel/setup.bash
  ```
* Some dependencies (like `octomap_ros` or `gazebo_ros`) may require additional ROS environment variables if you use a different workspace or multiple ROS versions.
* If you use Ubuntu 22.04 or ROS2, installation steps and package names will be different.

Building
------------
1. Clone repo:
```
git clone [https://github.com/JulioPlaced/ExplORBSLAM.git](https://github.com/Lawaries/ExplORB-SLAM-test.git)
```

2. Build repo:
```
cd ExplORBSLAM/
catkin build
```

3. Remember to source the ExplORBSLAM workspace:

  ```
  source devel/setup.bash
  ```

  If sourcing doesn't work properly, try

  ```
  catkin config --no-install
  catkin clean --all
  ```

  and rebuild.

Running
------------
1. Launch the scenario:

  AWS house environment:
  ```
  roslaunch robot_description single_house.launch
  ```
  Or AWS bookstore environment:
  ```
  roslaunch robot_description single_bookstore.launch
  ```

2. Launch the decision maker
  ```
  roslaunch decision_maker autonomous_agent.launch
  ```
