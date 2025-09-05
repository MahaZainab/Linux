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
## 📂 3. Transferring Files

To run scripts or access results, transfer files using scp:

### Upload a file to the cluster:
```bash
scp myscript.py your_username@easley.hpc.auburn.edu:/home/your_username/
```

### Download a file from the cluster:
```bash
scp your_username@easley.hpc.auburn.edu:/home/your_username/results.txt .
```

For larger datasets, use **rsync** for faster transfers.

---

## 🖥️ 4. Working on the Cluster

The HPC system runs on Linux. Some useful commands:

```bash
ls        # list files
cd dir    # change directory
pwd       # print working directory
```

### Requesting Interactive Resources

You must request resources through the job scheduler:

```bash
srun --partition=gpu --gres=gpu:1 --mem=16G --time=02:00:00 --pty bash
```

This gives you **1 GPU, 16 GB RAM, for 2 hours.**

---

## 📜 5. Submitting Batch Jobs

Most jobs are submitted with a batch script (`job.slurm`):

```bash
#!/bin/bash
#SBATCH --job-name=test_job
#SBATCH --output=output.txt
#SBATCH --partition=gpu
#SBATCH --gres=gpu:1
#SBATCH --mem=16G
#SBATCH --time=04:00:00

module load python/3.9
python myscript.py
```

### Submit the job:
```bash
sbatch job.slurm
```

### Check its status:
```bash
squeue -u your_username
```

### Cancel a job:
```bash
scancel job_id
```

---

## ⚡ 6. Best Practices

- Do not run heavy computations on the login node — always use `srun` or `sbatch`.
- Request only the resources you need (GPUs, memory, time).
- Run large workloads from `/scratch` instead of `/home`.
- Use `module avail` and `module load <package>` to manage software environments.
- Use `screen` or `tmux` for long interactive sessions.
- Clean up files in `/scratch` regularly (purged after 30 days of inactivity).
