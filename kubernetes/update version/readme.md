# Kubernetes Cluster Upgrade Using kubeadm

## Cluster Details

Initial Version:
v1.30.14

Target Version:
v1.31.14

Cluster Nodes:
- master (control-plane)
- worker1
- worker2

Upgrade Order:
1. Control Plane
2. Worker Nodes (one-by-one)

---

# Upgrade Control Plane

## Step 1: Update Kubernetes Repository to v1.31

echo "deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.31/deb/ /" | sudo tee /etc/apt/sources.list.d/kubernetes.list
sudo apt-get update

## Step 2: Upgrade kubeadm

sudo apt-mark unhold kubeadm
sudo apt-get install -y kubeadm=1.31.14-1.1
sudo apt-mark hold kubeadm

## Step 3: Check Upgrade Plan

sudo kubeadm upgrade plan

## Step 4: Apply Upgrade

sudo kubeadm upgrade apply v1.31.14

## Step 5: Drain Control Plane

kubectl drain master --ignore-daemonsets --delete-emptydir-data

## Step 6: Upgrade kubelet and kubectl

sudo apt-mark unhold kubelet kubectl
sudo apt-get install -y kubelet=1.31.14-1.1 kubectl=1.31.14-1.1
sudo apt-mark hold kubelet kubectl

sudo systemctl daemon-reload
sudo systemctl restart kubelet

## Step 7: Uncordon Master

kubectl uncordon master

---

# Upgrade Worker Nodes

Repeat the following steps for worker1 and worker2.

## Step 1: Drain Worker (Run on Master)

kubectl drain worker1 --ignore-daemonsets --delete-emptydir-data --force

## Step 2: Update Repo (Run on Worker)

echo "deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.31/deb/ /" | sudo tee /etc/apt/sources.list.d/kubernetes.list
sudo apt-get update

## Step 3: Upgrade kubeadm (Worker)

sudo apt-mark unhold kubeadm
sudo apt-get install -y kubeadm=1.31.14-1.1
sudo apt-mark hold kubeadm

## Step 4: Upgrade Node

sudo kubeadm upgrade node

## Step 5: Upgrade kubelet and kubectl

sudo apt-mark unhold kubelet kubectl
sudo apt-get install -y kubelet=1.31.14-1.1 kubectl=1.31.14-1.1
sudo apt-mark hold kubelet kubectl

sudo systemctl daemon-reload
sudo systemctl restart kubelet

## Step 6: Uncordon Worker (Run on Master)

kubectl uncordon worker1

---

# Final Verification

kubectl get nodes

Expected Output:

master    v1.31.14
worker1   v1.31.14
worker2   v1.31.14

---

# Health Check

kubectl get --raw='/readyz?verbose'
kubectl get po -n kube-system

All components must be Running.

TERMINAL 1 → MASTER
✅ STEP 1 — Drain worker2

Run:

kubectl drain worker2 --ignore-daemonsets --delete-emptydir-data --force

Wait until you see:

node/worker2 drained

STOP here on master.

🖥 TERMINAL 2 → WORKER2

SSH into worker2:

ssh ubuntu@worker2

Now follow exactly these steps.

✅ STEP 2 — Change Repo to 1.31
echo "deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.31/deb/ /" | sudo tee /etc/apt/sources.list.d/kubernetes.list

Update:

sudo apt-get update
✅ STEP 3 — Upgrade kubeadm
sudo apt-mark unhold kubeadm
sudo apt-get install -y kubeadm=1.31.14-1.1
sudo apt-mark hold kubeadm

Check version:

kubeadm version

It must show:

v1.31.14
✅ STEP 4 — Run kubeadm upgrade node
sudo kubeadm upgrade node

Wait until it completes.

✅ STEP 5 — Upgrade kubelet & kubectl
sudo apt-mark unhold kubelet kubectl
sudo apt-get install -y kubelet=1.31.14-1.1 kubectl=1.31.14-1.1
sudo apt-mark hold kubelet kubectl

Restart kubelet:

sudo systemctl daemon-reload
sudo systemctl restart kubelet

When done, type:

DONE WORKER2
🖥 Back to MASTER

After worker2 steps complete:

kubectl uncordon worker2
kubectl get nodes
🎯 Final Expected Output
master    v1.31.14
worker1   v1.31.14
worker2   v1.31.14
