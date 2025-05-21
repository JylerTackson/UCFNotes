A **Workspace** is a directory that will house your [[01_Packages]]. There are two types of Workspaces within ROS:
## Types of Workspaces:
### Underlay
The underlay workspace is the **Base Workspace**; this workspace will contain packages and dependencies you want to build **on top of & NOT modify.**

### Overlay
The overlay workspace is the **Secondary (top) Workspace**; this workspace is where you **import your own packages** that you want to modify.

The **Underlay** is sourced prior to the **Overlay** therefore the base workspace is able to find all the dependencies within the Overlay workspace and Custom packages.
**NOTE:** If a package in the Overlay has the same name as one in the Underlay it will **OVERWRIGHT** the one in the Underlay.

---
## Creating the Workspaces:

### Underlay:
We are going to use the **ROS 2 Humble** distribution for our underlay; this is just a prebuild ROS 2 distribution using and official binary version of ROS 2 (Humble).

Install ROS 2 Humble (Underlay):
- Linux `sudo apt install ros-humble-desktop`
The command above installs the underlay $\therefore$ it already exists, the next step is to source the **Underlay** so that the ROS tools **know where to locate the underlay**:
- **Linux**: `source /opt/ros/humble/setup.bash`

### Overlay:
#### 1) Create Workspace:
When creating an underlay workspace, the next step should be **creating a directory within the workspace that will house ALL overlay workspaces.**
- **Linux**: `mkdir -p ~/ros2_ws/src`
	- `ros2_ws` - This folder is the overlay workspace.
	- `src` - This folder will house the custom packages.

#### 2) Build Workspace:
cd into the overlay workspace folder and run the following line in your terminal:
- `colcon build` - Builds only the packages within the `src` folder and lets them depend on the previously sourced underlay workspace.

#### 3) Source Overlay:
Finally, after building you should source the overlay's `setup.bash` file so that it overrides the Underlay:
- `source ~/ros2_ws/install/setup.bash`