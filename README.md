# openfoam-rayleigh_taylor
Rayleigh-Taylor instability case for openFOAM

![](anim.gif)

## Instructions
1. Navigate to the directory, in the terminal, use the command 
```
> blockMesh
```
to create the mesh data (found in the `polyMesh` directory) according to the specifications in the `blockMeshDict` file. There is no harm in checking that the mesh generation process is successful using the command 
```
> checkMesh
```

2. To initialize the region of the two fluids where the denser fluid is sitting on top of the less dense fluid, use the command
```
> setFields
``` 
The specifications is contained in the `setFieldsDict` file. Within it, the we can find that it uses the `initialVolSurface.stl` file (which is just a 3D model) to determine the field value. i.e. If the cell is located inside the 3D model, the field value is set to 1, and 0 if the cell is located outside the 3D model.

3. Next, we decompose the work into four chunks, and solve it in parallel. This is done by running the command 
```
> decomposePar
```
and then
```
> mpirun -np 4 interFoam -parallel
```
to run it on four cores using the interFoam solver. 

