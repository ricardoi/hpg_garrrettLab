## SLURM: Scheduler for HiperGator


```bash
#!/bin/bash
#SBATCH --account=epi
#SBATCH --qos=epi
#SBATCH --job-name=INA  #Job name
#SBATCH --mail-type=ALL   # Mail events (NONE, BEGIN, END, FAIL, ALL)
#SBATCH --mail-user=gatorlink@ufl.edu  # Where to send mail
#SBATCH --ntasks=1
#SBATCH --cpus-per-task=1
#SBATCH --mem=64gb   # Per processor memory
#SBATCH --time=100:00:00   # Walltime
#SBATCH --output=ina_%j.out   # Name output file
# Displya date host and directory
date; hostname; pwd

# loading modules
module load ufrc
module load R

#load files
Rscript --vanilla INA_exe.R
```
