# OpenFOAM-HPC

# Background

This repository is intended to be shared with the HPC committee of OpenFOAM as an upstream contribution to the community.

# Case

The case here is the 3D turbulent flow over a cylinder. Unsteady time-marching Large Eddy Simulation is performed.

The domain size is as followed:
  - 38D in radial direction (13D are employed for the non-reflective zone)
  - pi*D in span-wise direction
  
# Case setup

The case consists of a cylinder of unit diameter at the center of the computational domain. The inlet Mach number is 0.2, and the flow properties are such that the Reynolds number is 3900. Three different mesh sizes are provided:
  - Small (S): around 1 million total cells
  - Medium (M): around 12.5 million total cells
  - Large (L): around 80 million total cells  
  
Because of the large size of some of the mesh files, git-lfs was used to store some of the generated polyMesh files.
  
 # Solver
 
- The case is setup to run with the solver caaFOAM developed by Prof. Valerio d'Alessandro (Universita Politecnica delle Marche). The link of the solver used with this test case is found [here](https://github.com/vdalessa/caafoam/tree/master/caafoam-m2_gradU-OF_v2112).
- The solver uses an implementation of dynamic Smagorinsky SGS model, that can be found [here](https://github.com/vdalessa/caafoam/tree/master/dynamicSmagorinsky-OF_v2112)

# Run the cases

Each mesh size contains a run.sh script that untar the heavy mesh files, perform the domain decomposition, renumbering of the mesh, and run of the test case. Just run the script as:
```
./run.sh X
```
where X is the desired number of processes.

# Results and reference data

Data are compared with experimental data of [Parnaudeau et. al](https://aip.scitation.org/doi/abs/10.1063/1.2957018)

