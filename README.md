# bezier_examples
This package contains example usage of the [bezier](https://github.com/ros-industrial-consortium/bezier/) project.

# Compiling

## wstool
Install [wstool](http://wiki.ros.org/wstool).

## rosdep
Install, initialize and update [rosdep](http://wiki.ros.org/rosdep).

## Compiling
Create a catkin workspace and clone the project:

```bash
mkdir -p catkin_workspace/src
cd catkin_workspace/src
git clone https://github.com/ros-industrial-consortium/bezier_examples.git
cd ..
wstool init src src/bezier_examples/bezier_examples.rosinstall
```

## Resolve ROS dependencies
```bash
rosdep install --from-paths src --ignore-src --rosdistro $ROS_DISTRO -y
```

## Fix `fanuc` package compilation
The `fanuc` package will not compile on melodic due to old IKFast MoveIt configuration packages, see issue https://github.com/ros-industrial/fanuc/issues/241.
You can fix them (help provided in the issue) or delete them as we won't use them:

```bash
rm -rf src/fanuc/*_moveit_config src/fanuc/*_moveit_plugins
```

## Compile
Use `catkin` to compile
```bash
catkin_make
```

# Launch
Source the catkin workspace in which you compiled the package, then launch:
```bash
roslaunch bezier_examples fanuc_m10ia_surfacing.launch surfacing_mode:=true mesh_cad:=plane/plane_defect.ply
```
Use the following command for the painting application:
```bash
roslaunch bezier_examples fanuc_m10ia_painting.launch mesh_cad:=ocean/ocean.ply
```

In this example, `bezier_examples` will be launched with `plane_defect.ply` as the CAD mesh and the grinding will be done in surface mode, meaning that we only pass on the surface of the mesh to smooth it.

```bash
roslaunch bezier_examples fanuc_m10ia_surfacing.launch mesh_cad:=plane/plane.ply mesh_defect:=plane/plane_defect.ply
```

In this example, `bezier_examples` will be launched with `plane.ply` as the CAD mesh and `plane_defect.ply` as defect mesh.

Others examples of meshes are available in:
```bash
$(catkin_workspace)/src/bezier_examples/bezier_examples/meshes
```
