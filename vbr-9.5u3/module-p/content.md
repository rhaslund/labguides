 Module P: Preparation for day 2

---
**This lab is expected to last a maximum of 70 minutes including lab launch.**

# Lab P.1: Day 1 overview

## Step 1: Review created VMware replicas

1. [] Launch **VMware vSphere Client** from the Windows task bar.
2. [] Enter:
 1. User name: +++root+++.
 2. Password: +++Pa$$w0rd+++.

3. [] Click the **Login** button.
4. [] Expand the **VEEAM-ESX** host.
5. [] Expand the **Replicas** resource pool.
6. [] Select the **VEEAM-DC01_replica** virtual machine.
7. [] Click the **Snapshot Manager** button on the toolbar (icon looks like a clock with a wrench).
> Note: For each new incremental run of the replication job, Veeam Backup & Replication triggers a regular snapshot of the replica.

8. [] Click the **Close** button.
> Note: It is recommended to do failovers in the Veeam Backup & Replication software. But, in an emergency situation, you can also use vSphere Client to select a snapshot / restore point.
9. [] Close the **VMware vSphere Client** window.

===

## Step 2: Review created Hyper-V replicas



---

# Congratulations!

You have completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
