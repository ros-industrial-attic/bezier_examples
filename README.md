# bezier_examples

# Launch
Source the catkin workspace in which you compiled the package, then launch:
```bash
roslaunch bezier_application fanuc_m20ia_surfacing.launch surfacing_mode:=true mesh_cad:=plane/plane_defect.ply
```
Use the following command for the painting application:
```bash
roslaunch bezier_application fanuc_m20ia_painting.launch mesh_cad:=ocean/ocean.ply
```

In this example, `bezier_application` will be launched with `plane_defect.ply` as the CAD mesh and the grinding will be done in surface mode, meaning that we only pass on the surface of the mesh to smooth it.

```bash
roslaunch bezier_application fanuc_m20ia_surfacing.launch mesh_cad:=plane/plane.ply mesh_defect:=plane/plane_defect.ply
```

In this example, `bezier_application` will be launched with `plane.ply` as the CAD mesh and `plane_defect.ply` as defect mesh.

Others examples of meshes are available in:
```bash
$(catkin_workspace)/src/bezier/bezier_application/meshes
```
