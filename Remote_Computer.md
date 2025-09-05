# Auburn University Remote Cluster Tutorial

This guide walks you through the process of connecting to Auburn University’s High-Performance Computing (HPC) cluster.  
The cluster provides **powerful GPUs, CPUs, and large memory** resources to run heavy computations, simulations, and deep learning tasks.

---

## 🚀 1. Request Access
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
