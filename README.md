# RT-Assignment2-Lidia-Loubar
## Description:

This package contains three ROS nodes that collectively enable a robot to receive user-defined goals, navigate to the targets, and provide information about its position and velocity.

## Nodes

### 1. Action Client Node: `action_client_node.py`

- This node acts as an action client to the `/reaching_goal` action server.
- Users can set new target positions or cancel the current goal through user input.
- The node subscribes to the `/odom` topic to receive Odometry messages, extracts relevant information, and publishes a `CustomMessage` on the `/custom_topic` topic.
- Progress feedback is displayed during goal execution.

### 2. Last Target Service Node: `last_target_service.py`

- Implements a service client to retrieve the last target coordinates from the `/get_last_target_coordinates` service.
- Allows users to set new target positions or cancel the current goal through user input.
- Subscribes to the `/odom` topic, processes Odometry messages, and publishes a `CustomMessage` on the `/custom_topic` (or `/odom`) topic.

### 3. Robot Position and Velocity Service Node: `robot_pos_vel_service_node.py`

- Provides a service (`/get_robot_pos_vel`) that responds with information about the robot's position and velocity.
- Subscribes to the `/custom_topic` topic, processes `CustomMessage` data, and updates the robot's position and speed.
- Calculates the distance to the last target and the average speed since the last request.

## Usage

1. **Run the ROS Nodes using the Launch File:**

   Execute the following command to launch the nodes (excluding `action_client_node.py`) in separate terminals:

   ```bash
   roslaunch <your_package_name> <your_launch_file_name>.launch
  
2. **Run action_client_node.py in a Separate Terminal::**

