# ResearchData
Research data of the linked journal article, is composed of input and output files of the LIGGGHTS simulations (Project folders) and an Excel data sheet (Results_Excel) which includes calculated data.

## Folder and file structure
There are two main folders with names `Project_2005341` and `Project_2006017`, which contain the input and output files from 80 cases described in article: .

Here the project numbers correspond to the HPC center project number.

All of the first replicas are run on `Project_2005341`, while majority of the second replicas are run on `Project_2006017`(excluding cases 75X Mesh, 75X Primitive transition fraction 0.005, 75X Primitive transition fraction 0.100, which are run on `Project_2005341`but reported in folder `Project_2006017`).

Each project folder include 40 folders that are named according to rule: `size_mult_sizemultiplier_walltype_walls_transitionfraction`. (`sizemultiplier:` 30, 45, 60, 75 `wall_type:` mesh, primitive `transitionfraction:` none (mesh case), 0.001, 0.005, 0,025, 0,050, 0.075, 0.100, 0.150, 0.200, 0.250)

Each of these 40 subfolders include the below list of files:

### Input files
#### In. file (Script of LIGGGHTS commands, more information on how they are generated:)
- in.cent_walltype_walls_sizemultiplierX_transitionfraction (walltype: mesh, primitive; size_multiplier: 30, 45, 60, 75; transitionfraction: none (mesh case), 0.001, 0.005, 0,025, 0,050, 0.075, 0.100, 0.150, 0.200, 0.250)

#### Mesh files (For representing geometries, more information on how they are generated: )
- **bottom_disk.stl** 
- **bot_cyl.stl**
- **cone.stl**
- **dem_walls_*sizemultiplier*X_14micronpore_mod_mesh.stl** (*sizemultiplier:* 30, 45, 60, 75)(only in mesh type of filter mesh wall)
- **in_cyl.stl**
- **top_cyl.stl**
- **top_disk.stl**

#### Dump file (Initial no_overlap packing of particles, more information on how it is generated:)
- **dump.atom_info_1**

#### LIGGGHTS executable file (Compiled on the supercomputer)
- **lmp_puhti**

#### Batch file (For batch job submission to supercomputer, more information on how it is generated:)
- **b.*walltype*_*sizemultiplier*X_*transitionfraction*** (*walltype:* mesh, prim *size_multiplier:* 30, 45, 60, 75 *transitionfraction:* none (mesh case), 0.001, 0.005, 0,025, 0,050, 0.075, 0.100, 0.150, 0.200, 0.250)

### Output files
#### LIGGGHTS forced restart file (Generated by LIGGGHTS due to killing the job earlier than its completion)
- **restart_forced_ligghts_*simulationtimestep*.data**
        
#### LIGGGHTS log file (Generated by LIGGGHTS)
- **log.liggghts**
        
#### Slurm file (Generated by supercomputer for each batch job sent)
- **slurm.*jobID*.out**

#### Text file reporting number of atoms each 25 steps (Generated by LIGGGHTS as defined in the in.file)
- **numatoms.txt**
        
#### Dump files (Atom positions, velocities and properties, generated by LIGGGHTS as defined in the .in file)
- **dump.atom_info_ac_*simulationtimestep***

## Results_Excel sheet structure
### Results_time red.+part. loss
Here you can find information about how long the simulations took and how much particles are left at the final step (timestep correscponding to 1 second). You can also see the derived quantities such as time reduction and particle loss %.

### Case properties
Here you can find information about the case set-up (such as: mesh size, number of steps it will take to reach one second, number of horizontal and vertical pores, number of particles added, number of mesh elements, etc.). You can also see the comparison of different size multipliers in terms of number of elements vs computation time.

### Mesh quality
Here you can find the metrics that are related to mesh quality.