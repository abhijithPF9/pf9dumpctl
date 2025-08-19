# 📦 Collecting Platform9 Cluster Dump for Troubleshooting

This guide explains how to **collect a cluster dump** from your Platform9 **Management Cluster**.  
The dump captures cluster resources and logs, which can be shared with Platform9 Support for troubleshooting.

---

## ✅ Prerequisites

- Access to a **Management Cluster node**  
- **Cluster admin privileges** on the node  
- **Kubeconfig** for the Management Cluster exported and working  

---

## 📝 Steps to Collect Cluster Dump

### 📥 Step 1: Download the Collection Script

On a **node**, download the `pcd-dumpctl.sh` script:

```bash
curl -o pcd-dumpctl.sh https://platform9.com/tools/pcd-dumpctl.sh
chmod +x pcd-dumpctl.sh
```

---

### ⚙️ Step 2: Run the Script

Execute the script to start the dump collection:

```bash
./pcd-dumpctl.sh
```

The script will automatically collect:  
- Namespaced and cluster-wide Kubernetes resources (`yaml` + `describe`)  
- Pod logs (including failed/non-running pods)  
- Node and pod resource usage metrics  
- Cluster version details  
- Checksums for validation  

---

### 📂 Step 3: Locate the Dump

Once finished, the dump will be stored in `/tmp/` as a timestamped `.tar.gz` file. Example:

```bash
/tmp/cluster-dump-2025-08-19_14-30-10.tar.gz
```

---

### 🚀 Step 4: Share with Support

Send the generated `.tar.gz` file to **Platform9 Support** for analysis.  
If the file is large, compress further or upload to the secure share link provided by the Support team.

---

## 💡 Notes

- You can re-run the script anytime; each run generates a new dump folder with timestamp  
- Ensure sufficient disk space is available in `/tmp/` before running the script  
- For very large clusters, the collection may take several minutes  

---
