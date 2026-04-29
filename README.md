**All-atom Molecular Dynamics Simulations (AAMD)**

This repository contains essential input parameter files and a helper script required to set up and run all-atom molecular dynamics (AAMD) simulations using GROMACS.

📁 **Repository Contents**

The following files are included to guide a standard MD simulation workflow:

**🔹 1. ions.mdp**

Defines parameters for ion addition to neutralize the system and achieve the desired ionic concentration. Typically used during the preprocessing step before equilibration.

**🔹 2. minim.mdp**

Contains settings for energy minimization, ensuring removal of steric clashes and unfavorable contacts in the system before starting dynamics.

**🔹 3. nvt.mdp**

Used for NVT equilibration (constant Number, Volume, Temperature). Stabilizes the system temperature while keeping volume fixed.

**🔹 4. npt.mdp**

Defines parameters for NPT equilibration (constant Number, Pressure, Temperature). Allows the system density and pressure to equilibrate.

**🔹 5. md.mdp**

Contains parameters for the production molecular dynamics run, where actual simulation data is collected for analysis.

**🔹 6. prod.sh**

A shell script to automate the simulation workflow, typically including preprocessing, equilibration, and production MD steps.

**⚙️ Simulation Workflow**

The files are organized to follow a standard GROMACS MD pipeline:

Energy Minimization → minim.mdp
Ion Addition → ions.mdp
NVT Equilibration → nvt.mdp
NPT Equilibration → npt.mdp
Production Run → md.mdp
Execution Script → prod.sh

**🚀 Usage**

Make sure you have **GROMACS** installed and properly configured.

**Example execution:**
````markdown
bash prod.sh
````
Or run steps manually using:

gmx grompp -f minim.mdp -c input.gro -p topol.top -o em.tpr
gmx mdrun -deffnm em

(Repeat similarly for NVT, NPT, and MD steps)

🧪 Requirements
GROMACS (version 2020 or later recommended)
Linux/Unix environment
Input structure files (.gro, .top, .itp)
📌 Notes
These .mdp files are generic templates and may need modification depending on:
Force field used
System type (protein, membrane, complex, etc.)
Simulation time scale
Ensure proper validation of parameters before running long simulations.
````markdown
## Test Code Block

```bash
echo "Hello MD Simulation"
