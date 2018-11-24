Module 2: Initial Configuration
---
**This lab is expected to last a maximum of 40 minutes including lab launch.**

# Lab 3.1: Connecting virtual infrastructure servers

Add a vSphere host and a Hyper-V host to Veeam Backup & Replication.

## Step 1: Add vSphere Server or standalone ESXi

1. [] Launch the **Veeam Backup & Replication console** from the desktop.
2. [] Click the **Connect** button.
3. [] Navigate to the **Backup Infrastructure** view.
4. [] Click the **Add Server** button.
5. [] Select **VMware vSphere**.
6. [] Enter DNS name: +++VEEAM-ESX+++
7. [] Click the **Next** button.
8. [] Click the **Add...*** button next to the **Credentials** drop down menu.
9. [] Enter:
 1. Username: +++root+++
 2. Password: +++Pa$$w0rd+++
 3. Description: +++VEEAM-ESX+++

10. [] Click the **OK** button.
11. [] Click the **Next** button.
12. [] Click the **Connect**.
> Note: When you add a vCenter Server or ESX(i) host, Veeam Backup & Replication saves a thumbprint of the SSL certificate installed on the vCenter Server or ESX(i) host to the Veeam Backup & Replication database. During every subsequent connection to the server, Veeam Backup & Replication uses the saved thumbprint to verify the identity of the server and avoid the man-in-the-middle attack.

13. [] Click the **Finish** button.

===

## Step 2: Add a standalone Hyper-V Server

1. [] Click the **Add Server** button.
2. [] Select the **Microsoft Hyper-V server (standalone)** radio button.
3. [] Enter DNS name: +++VEEAM-HYPERV+++
4. [] Click the **Next** button.
5. [] Click the **Add...*** button next to the **Credentials** drop down menu.
6. [] Enter:
 1. Username: +++VEEAMINFRA\Administrator+++
 2. Password: +++Pa$$w0rd+++
 3. Description: +++VEEAMINFRA domain administrator+++

7. [] Click the **OK** button.
> Note: Generally, you would need to select credentials for the account that has local administrator permissions on the added Hyper-V Server. In our case, the Hyper-V server is domain joined, so we’re using a domain credential.

8. [] Click the **Next** button.
9. [] Click the **Apply** button.
10. [] Click the **Next** button.
11. [] Click the **Finish** button.
12. [] Select **Microsoft Hyper-V** in the **Managed Servers** section of the **Backup Infrastructure** view.
> Note: The VEEAM-HYPERV host is now added to the Veeam Backup & Replication user interface.

---

# Congratulations!

You have completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
