# Auburn University Remote Cluster Tutorial

This guide walks you through the process of connecting to Auburn University’s(AIAU) cluster.  
The cluster provides **powerful GPUs, CPUs, and large memory** resources to run heavy computations, simulations, and deep learning tasks.

---

## 1. Request Access
Before you begin, you must have an **Auburn AIAU account**.

- Contact your **system administrator** or **HPC support team**.  
- Request access and provide your Auburn username.  
- Credentials (username/password) will be issued.  
- Some systems also require **Duo two-factor authentication**.

---

## 💻 2. Connect to the Cluster (SSH)
You will connect to the cluster using **SSH**.

- On **Windows**:  
  Press `Win + R`, type `cmd`, and press Enter.  

- On **Mac/Linux**:  
  Open the **Terminal**.

Run the following command (replace with your actual username):

```bash
ssh your_username@easley.hpc.auburn.edu

```

---

## 🖥️ 3. Working on the Cluster

The HPC system runs on Linux. Some useful commands:

```bash
ls        # list files
cd dir    # change directory
pwd       # print working directory
```

## 📦 4. Modules
```bash
module avail          # list available modules
module load <module>  # load a module
module list           # show loaded modules
module purge          # unload all modules
```

---

## 🖥️ 5. Job Allocation (Slurm)
```bash
salloc -N1                          # request 1 node
salloc -N1 --nodelist=aiau010        # request a specific node
srun --pty /bin/bash                 # run shell on allocated node
```

---

## 📜 6. Batch Jobs
```bash
sbatch job.slurm     # submit job
squeue -u username   # check job status
scancel job_id       # cancel a job
```

---

## 📂 7. File Transfer
```bash
scp file.py user@aiau.eng.auburn.edu:/home/user/   # upload
scp user@aiau.eng.auburn.edu:/home/user/out.txt .  # download
rsync -avP data/ user@aiau.eng.auburn.edu:/home/user/data/   # sync large datasets
```

---

## 📊 8. GPU Monitoring
```bash
nvidia-smi
```

---



## ✅ 9. Quick Summary of commands
- **Login:** `ssh user@aiau.eng.auburn.edu`
- **Modules:** `module avail`, `module load <pkg>`
- **Jobs:** `salloc`, `sbatch`, `squeue`
- **Cancel:** `scancel job_id`
- **Files:** `scp`, `rsync`
- **GPU:** `nvidia-smi`

---
## ⚡ 6. Best Practices

- Do not run heavy computations on the login node — always use `srun` or `sbatch`.
- Request only the resources you need (GPUs, memory, time).
- Run large workloads from `/scratch` instead of `/home`.
- Use `module avail` and `module load <package>` to manage software environments.
- Use `screen` or `tmux` for long interactive sessions.
- Clean up files in `/scratch` regularly (purged after 30 days of inactivity).
