# GROMACS

[GROMACS](https://www.gromacs.org/) is a molecular dynamics simulation package. For detailed information on using GROMACS, including input files, simulation workflows and command-line options, refer to the [official GROMACS documentation](https://manual.gromacs.org/).

## Available versions

The following version is available on Calder, with both CPU and GPU builds:

| Version | CPU | GPU |
| --- | --- | --- |
| `2026.1` | Yes | Yes |

## Loading GROMACS

Calder provides CPU and GPU builds of GROMACS. Load the appropriate environment and OpenMPI module before loading GROMACS.

### CPU version

```bash
module load calder/cpu openmpi/5.0.10 gromacs/2026.1
```

### GPU version

```bash
module load calder/hopper openmpi/5.0.10 gromacs/2026.1

```

:::{note}
GROMACS on Calder is built with external MPI support through OpenMPI. Use `gmx_mpi` to run GROMACS commands; the `gmx` command will not work with this build.
:::

## Example Slurm jobs

The following examples request one hour of runtime and 16 CPU cores. Adapt the input and output filenames to match your simulation.

### CPU job

Save the following as `gromacs_cpu.sh`:

```bash
#!/bin/bash
#SBATCH --job-name=gromacs-cpu
#SBATCH --time=01:00:00
#SBATCH --ntasks=16
#SBATCH --cpus-per-task=1
#SBATCH --output=gromacs-%j.out
#SBATCH --error=gromacs-%j.err

module load calder/cpu
module load openmpi/5.0.10
module load gromacs/2026.1

export OMP_NUM_THREADS=1

mpirun -np 16 gmx_mpi mdrun -s topol.tpr -deffnm md_cpu
```

Submit the job with:

```bash
sbatch gromacs_cpu.sh
```

### GPU job

Save the following as `gromacs_gpu.sh`:

```bash
#!/bin/bash
#SBATCH --job-name=gromacs-gpu
#SBATCH --time=01:00:00
#SBATCH --ntasks=2
#SBATCH --partition=calder-gpu-hopper
#SBATCH --gres=gpu:nvidia_h200:2
#SBATCH --output=gromacs-%j.out
#SBATCH --error=gromacs-%j.err

module load calder/hopper
module load openmpi/5.0.10
module load gromacs/2026.1

mpirun -np 2 gmx_mpi mdrun -s topol.tpr -deffnm md_gpu -nb gpu -pme gpu -npme 1 -bonded gpu -v
```

Submit the job with:

```bash
sbatch gromacs_gpu.sh
```

:::{note}
These are starting examples, not performance-tuned configurations. The GPU example requests two H200 GPUs and directs non-bonded calculations to the GPU. The optimal CPU and GPU task layout depends on the simulation and should be benchmarked for your workload.
:::
