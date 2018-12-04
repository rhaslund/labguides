 Module P: Preparation for day 2

---
**This lab is expected to last a maximum of 70 minutes including lab launch.**

# Lab P.1: Deploying a second Veeam backup server

## Step 1: Disable the Backup Copy Job WAN job

1. [] Launch the **Veeam Backup & Replication Console** from the desktop.
2. [] Click the **Connect** button.
3. [] Select **Backup Copy** in the **Jobs** section of the **Home** view.
4. [] Select the **Backup Copy Job WAN** job.
5. [] Click the **Disable** button on the **Backup Copy** ribbon.
> **Important: Do NOT continue until the job status is Stopped.**

===

## Step 2: Install Veeam Backup & Replication at VEEAM-VBR2

1. [] Launch the **Remote Desktop Connection client** from the Windows task bar.
2. [] Enter computer: +++VEEAM-VBR2+++.
3. [] Click the **Connect** button.
4. [] Enter password: +++Pa$$w0rd+++.
5. [] Click the **OK** button.
6. [] Launch the **File Explorer** from the Windows task bar.
7. [] Navigate to +++\\\\VEEAM-VBR\\Install+++.
8. [] Double click the **VeeamBackup&Replication** ISO Disc Image File.
9. [] Launch the **Setup.exe** file.
10. [] Click the **Install** button on the left hand side.
> **Important: Do not click the Install text links on the right hand side.**

11. [] Select the **Select the I accept the terms in the license agreement** radio button.
12. [] Click the **Next** button on the **License Agreement** step.
13. [] Click the **Browse...** button.
14. [] Enter file name: +++\\\\VEEAM-VBR\\Install\\+++.
15. [] Click the **Open** button.
16. [] Select the **veeam_availability_suite_nfr_2_2.lic** file.
17. [] Click the **Open** button.
18. [] Click the **Next** button on the **Provide License** step.
19. [] Keep the default settings and click the **Next** button on the **Program features** step.
20. [] Tick the **Let me specify different settings** check box.
21. [] Click the **Next** button on the **Default Configuration** step.
22. [] Keep the default settings and click the **Next** button on the **Service Account** step.
23. [] Keep the default settings and click the **Next** button on the **SQL Server Instance** step.
24. [] Keep the default settings and click the **Next** button on the **Port Configuration** step.
25. [] Keep the default settings and click the **Next** button on the **Data Locations** step.
26. [] Keep the default settings and click the **Install** button on the **Ready to install** step.
> **Important: The installation will take about 30 minutes. Please continue with the next lab exercises, you will come back to complete it in a later step.**

27. [] Minimize the **Remote Desktop Connection** window.

===

# Lab P.2: Day 1 overview

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

1. [] Launch the **Hyper-V Manager** from the Microsoft Windows task bar.
2. [] Select **Hyper-V Manager** in the navigation pane on the left side.
3. [] Click the **Connect to Server...** text link in the **Actions** pane.
4. [] Enter another computer: +++VEEAM-HYPERV+++.
> Note: VEEAM-HYPERV will get added as VEEAM-DCInfra because this is actually the real server name of VEEAM-HYPERV host.

5. [] Select the **Tiny-Veeam2_replica** virtual machine.
> Note: Review the Snapshots section. For each new incremental run of the replication job, Veeam Backup & Replication triggers a regular snapshot of the replica.

===

# Lab P.3: Deleting VMs

1. [] Launch the **Hyper-V Manager** from the Windows task bar.
2. [] Select the **Tiny-Veeam2** virtual machine.
3. [] Click the **Turn Off...** text link in the **Actions** pane.
4. [] Click the **Turn Off** button.
5. [] Wait for the **Tiny-Veeam2** virtual machine to reach a powered off state then click the **Delete...** text link in the **Actions** pane.
6. [] Click the **Delete** button.
7. [] Close the **Hyper-V Manager** window.

===

# Lab P.4: Deleting SQL table

## Step 1: Deleting SQL table

1. [] Launch a second **Remote Desktop Connection client** from the Windows task bar.
> Note: Hold the SHIFT keyboard button while clicking the icon to launch a second instance of the remote desktop connection client

2. [] Enter computer: +++VEEAM-SP01+++.
3. [] Click the **Connect** button.
4. [] Enter password: +++Pa$$w0rd+++.
5. [] Click the **OK** button.
6. [] Launch **SQL Server Management Studio** from the desktop.
7. [] Verify that the server name is set to +++VEEAMSP01\SQLEXPRESS+++ and click the **Connect** button.
8. [] Expand the **Databases** node.
9. [] Expand the **testdb** database.
10. [] Expand **Tables**.
11. [] Select **dbo.BuildVersion**.
12. [] Click the **Edit** menu.
13. [] Select **Delete**.
14. [] Click the **OK** button to delete the object.
15. [] Close the **Microsoft SQL Server Management Studio** window.
16. [] Close the **Remote Desktop Connection VEEAM-SP01** window.

===

## Step 2: Complete installation of Veeam Backup & Replication at VEEAM-VBR2

1. [] Switch back to the **Remote Desktop Connection VEEAM-VBR** using the Windows task bar.
2. [] Click the **Finish** button.
3. [] Close the **Veeam Backup & Replication installer** window.
4. [] Close the **Remote Desktop Connection** window.
5. [] Click the **Disable** button on the **Backup Copy** ribbon.
> **Important: Do NOT continue until the job status is Idle.**

6. [] Close the **Veeam Backup & Replication Console** window.

---

# Congratulations!

You have completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
