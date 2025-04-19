# Mars_Navigation_Sim

A high-level simulation framework for autonomous planetary rover navigation using Unity and ROS2.

This wrapper repository links two coordinated submodules:
- **Unity Simulation** (`mars_rover_unity_sim/`): 3D Martian terrain, simulated LiDAR, rover prefab, and ROS–Unity integration via ROS–TCP Connector.
- **ROS2 Stack** (`mars_rover_ros2_ws/`): LiDAR mapping with OctoMap, 2D slope-aware costmap projection, and a custom A* navigation planner.

---

## 🛠️ Prerequisites

- Unity 2022 or later (preferably Unity 2022.3 LTS)
- ROS 2 Humble (or compatible version)
- Colcon and ROS2 development environment
- Git and Python 3.10+

---

## 🚀 Getting Started

### 1. Clone this wrapper with submodules:

```bash
git clone --recurse-submodules https://github.com/Maxwell44772029/Mars_Navigation_Sim.git
cd Mars_Navigation_Sim

🔧 Unity Setup
Install Unity using Unity Hub.

Recommended version: Unity 2022.3 LTS

Open Unity Hub and add the project:

Click Add → Navigate to mars_rover_unity_sim/ and open it.

Install the ROS–TCP Connector package:

Go to Window → Package Manager → Add package from Git URL

Paste:
https://github.com/Unity-Technologies/ROS-TCP-Connector.git
Build the Unity project and press Play to start the simulation.


🤖 ROS2 Setup
Once the Unity project is loaded and running:
cd mars_rover_ros2_ws
colcon build
source install/setup.bash

Connecting Unity ↔ ROS2
Terminal 1: Run the ROS TCP Endpoint
source install/setup.bash
ros2 run ros_tcp_endpoint default_server_endpoint

Terminal 2: Launch the full simulation stack
source install/setup.bash
ros2 launch mars_rover_navigation bringup.launch.py

This starts:
-OctoMap 3D occupancy mapping
-2D costmap projection node
-A* path planner
-RViz for LiDAR, map, and path visualization

Repositories Overview
-> Folder	Description
- mars_rover_unity_sim	Unity simulation: terrain, LiDAR, rover, and ROS bridge
- mars_rover_ros2_ws	ROS2 workspace: OctoMap mapping, planning, and control

 Features
-Real Martian terrain using heightmaps and PBR textures
-3D LiDAR simulation via raycasting and point cloud generation
-Rolling slope-aware 2D costmap from OctoMap
-A* planner that avoids steep and hazardous terrain
-Real-time integration between Unity and ROS2 using the ROS–TCP Connector

 Project Goals
-Simulate autonomous planetary navigation with realistic terrain interaction
-Enable testing of terrain-aware perception and navigation algorithms
-Provide a modular foundation for hybrid Unity + ROS2 simulations
