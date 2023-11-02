Title: Setting up F1TENTH Gym Environment with ROS2 Communication Bridge

Description: This guide provides step-by-step instructions on how to set up the F1TENTH Gym environment with a ROS2 communication bridge on different systems including Ubuntu. By following this guide, you'll have a containerized ROS communication bridge for the F1TENTH gym environment turning it into a simulation in ROS2.

## Table of Contents
1. [Prerequisites](#prerequisites)
2. [Installation on Ubuntu 20.04 (Native)](#native-ubuntu)

<a name="prerequisites"></a>
## 1. Prerequisites
- Ubuntu 20.04 (for native installation)

<a name="native-ubuntu"></a>
## 2. Installation on Ubuntu 20.04 
### Dependencies Installation:
1. Install ROS 2 Foxy by following the instructions [here](https://index.ros.org/doc/ros2/Installation/Foxy/Linux-Install-Debians/).
2. Set up the F1TENTH Gym:
   ```bash
   git clone https://github.com/f1tenth/f1tenth_gym
   cd f1tenth_gym && pip3 install -e .
   ```

### Simulation Installation:
1. Create a workspace:
   ```bash
   cd $HOME && mkdir -p sim_ws/src
   ```
2. Clone the repository into the workspace:
   ```bash
   cd $HOME/sim_ws/src
   git clone https://github.com/f1tenth/f1tenth_gym_ros
   ```
3. Update the map file path in `sim.yaml`:
   - Navigate to [sim.yaml](https://github.com/f1tenth/f1tenth_gym_ros/blob/main/config/sim.yaml) in your cloned repository.
   - Change the `map_path` parameter to `<your_home_dir>/sim_ws/src/f1tenth_gym_ros/maps/levine`.
4. Install dependencies with rosdep:
   ```bash
   source /opt/ros/foxy/setup.bash
   cd ..
   rosdep install -i --from-path src --rosdistro foxy -y
   ```
5. Build the workspace:
   ```bash
   colcon build
   ```
Ensure to test the setup to confirm the simulation runs successfully in the ROS2 environment.
