# 4th_Ai_Launch_TurtleBot_navigation

Great! Since you have ROS Noetic installed, we'll proceed with the steps to set up the TurtleBot packages, the simulation package, create a map, and launch the navigation. Follow these steps carefully:

### Step 2: Install TurtleBot Packages

1. **Install the TurtleBot3 packages:**
   ```bash
   sudo apt update
   sudo apt install ros-noetic-turtlebot3 ros-noetic-turtlebot3-simulations
   ```
   
<img src="https://github.com/user-attachments/assets/ba246d65-c994-4a15-9e2e-f1c93c4e37d1" data-canonical-src="https://gyazo.com/eb5c5741b6a9a16c692170a41a49c858.png" width="500" height="400" />


2. **Install dependencies:**
   ```bash
   sudo apt install ros-noetic-navigation ros-noetic-slam-gmapping
   ```
<img src="https://github.com/user-attachments/assets/56c48525-49b0-414e-ae8b-df6096ef4ec6" data-canonical-src="https://gyazo.com/eb5c5741b6a9a16c692170a41a49c858.png" width="500" height="400" />


### Step 3: Set Up the Environment

1. **Add the TurtleBot3 model to your `.bashrc` file:**
   ```bash
   echo "export TURTLEBOT3_MODEL=burger" >> ~/.bashrc
   source ~/.bashrc
   ```

2. **Source the ROS setup file:**
   ```bash
   source /opt/ros/noetic/setup.bash
   ```

### Step 4: Launch the TurtleBot3 Simulation

1. **Launch the TurtleBot3 world in Gazebo:**
   ```bash
   roslaunch turtlebot3_gazebo turtlebot3_world.launch
   ```
<img src="https://github.com/user-attachments/assets/6e3f7b9c-10ef-471f-8026-61eabb2bc4a8" data-canonical-src="https://gyazo.com/eb5c5741b6a9a16c692170a41a49c858.png" width="500" height="400" />
<img src="https://github.com/user-attachments/assets/d9d499fb-74ad-403b-bd74-7ac86efc8c89" data-canonical-src="https://gyazo.com/eb5c5741b6a9a16c692170a41a49c858.png" width="500" height="400" />
<img src="https://github.com/user-attachments/assets/1952bace-91f9-49d7-aa25-aa13789ef134" data-canonical-src="https://gyazo.com/eb5c5741b6a9a16c692170a41a49c858.png" width="500" height="400" />


### Step 5: Create a Map Using SLAM

1. **Launch the SLAM node:**
   ```bash
   roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
   ```
<img src="https://github.com/user-attachments/assets/303da213-62cd-4433-abbe-36b456c8dde8" data-canonical-src="https://gyazo.com/eb5c5741b6a9a16c692170a41a49c858.png" width="500" height="400" />
<img src="https://github.com/user-attachments/assets/7548f5c4-18d5-420b-9222-b643209ac63b" data-canonical-src="https://gyazo.com/eb5c5741b6a9a16c692170a41a49c858.png" width="500" height="400" />

2. **Control the TurtleBot using the keyboard:**

   ```bash
   roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
   ```
<img src="https://github.com/user-attachments/assets/3851a85b-2315-4c7d-b1dd-1333229f3144" data-canonical-src="https://gyazo.com/eb5c5741b6a9a16c692170a41a49c858.png" width="500" height="400" />
<img src="https://github.com/user-attachments/assets/c0d76aae-4769-4dd5-bbb3-282f4042fc40" data-canonical-src="https://gyazo.com/eb5c5741b6a9a16c692170a41a49c858.png" width="500" height="400" />

![4thtaskAi](https://github.com/user-attachments/assets/9839ce2a-058e-4abb-a162-a5697cb4a385)


4. **Save the map:**
   Once you have explored the environment and built a map, save the map by running the following command in a new terminal:
   ```bash
   rosrun map_server map_saver -f ~/map
   ```

### Step 6: Launch Navigation

1. **Launch the TurtleBot3 navigation:**
   ```bash
   roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=$HOME/map.yaml
   ```

<img src="https://github.com/user-attachments/assets/e0f3bd5c-a26c-467a-b930-72e065294af1" data-canonical-src="https://gyazo.com/eb5c5741b6a9a16c692170a41a49c858.png" width="500" height="400" />
<img src="https://github.com/user-attachments/assets/8c38fdcf-8fee-4634-b63e-54a8ab6a75e2" data-canonical-src="https://gyazo.com/eb5c5741b6a9a16c692170a41a49c858.png" width="500" height="400" />
