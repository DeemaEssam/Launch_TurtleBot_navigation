# 4th_Ai_Launch_TurtleBot_navigation


Great! Since you have ROS Noetic installed, we'll proceed with the steps to set up the TurtleBot packages, the simulation package, create a map, and launch the navigation. Follow these steps carefully:

### Step 2: Install TurtleBot Packages

1. **Install the TurtleBot3 packages:**
   ```bash
   sudo apt update
   sudo apt install ros-noetic-turtlebot3 ros-noetic-turtlebot3-simulations
   ```

2. **Install dependencies:**
   ```bash
   sudo apt install ros-noetic-navigation ros-noetic-slam-gmapping
   ```

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

### Step 5: Create a Map Using SLAM

1. **Launch the SLAM node:**
   ```bash
   roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
   ```

2. **Control the TurtleBot using the keyboard:**
   Open a new terminal and run:
   ```bash
   roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
   ```

3. **Save the map:**
   Once you have explored the environment and built a map, save the map by running the following command in a new terminal:
   ```bash
   rosrun map_server map_saver -f ~/map
   ```

### Step 6: Launch Navigation

1. **Launch the TurtleBot3 navigation:**
   ```bash
   roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=$HOME/map.yaml
   ```

### Step-by-Step Explanation

1. **Install TurtleBot Packages:**
   - We installed the TurtleBot3 and TurtleBot3 simulation packages along with their dependencies to ensure we have all necessary tools for navigation and SLAM.

2. **Set Up the Environment:**
   - The `TURTLEBOT3_MODEL` environment variable is set to specify which TurtleBot3 model we are using (`burger` in this case). This helps the launch files configure the simulation accordingly.

3. **Launch the Simulation:**
   - We launched the TurtleBot3 world in Gazebo, which provides a simulated environment where we can test the navigation and SLAM.

4. **Create a Map Using SLAM:**
   - By launching the SLAM node with `gmapping`, we enabled the TurtleBot to create a map of its environment as it navigates.
   - The `teleop` package allows us to control the TurtleBot manually using the keyboard.
   - Once the map is created, we save it to a file using the `map_saver` node.

5. **Launch Navigation:**
   - With the saved map, we launched the TurtleBot3 navigation stack. This allows the TurtleBot to navigate autonomously within the environment using the map we created.

If you encounter any issues or need further clarification, feel free to ask!
