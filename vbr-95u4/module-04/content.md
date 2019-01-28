Module 4: Creating virtual machine backups
---
**This lab is expected to last a maximum of XX minutes including lab launch.**

# Lab 4.1
In this lab exercise, you will configure storage latency control to avoid overloading the production storage system.

1. [] Launch the **Veeam Backup & Replication console** from the desktop.
2. [] Click the **Connect** button.
3. [] Click the **≡** button in the top left corner.
4. [] Select **General Options**.
6. [] Tick the **Enable storage latency control** check box.
> Note: Storage latency control is also referred to by Veeam as Backup I/O Control.

===

# Lab 4.2
In this lab exercise, you will configure e-mail settings so notifications can be sent out for the jobs created later.

1. [] Click the **E-mail Settings** tab.
2. [] Tick the **Enable e-mail notifications** check box.
3. [] Enter:
 1. SMTP server: +++veeam-ex01.veeamlab.local+++
 2. From: +++VeeamBackup@veeamlab.local+++
 3. To: +++administrator@veeamlab.local+++

4. [] Click the **Apply** button.
5. [] Click the **Test Message** button.
6. [] Click the **OK** button.
> Note: You can find Outlook Web Access (OWA) in the task bar of the VEEAM-VBR server. When you start OWA, you can log in as administrator@veeamlab.local using password: Pa$$w0rd

7. [] Click the **OK** button to close the **Options** window.

===

# Lab 4.3

In this lab exercise, you will create a VeeamZIP backup.

1. [] Navigate to the **Inventory** view.
2. [] Select the **VEEAM-ESX** host in the **VMware vSphere** section of the **Inventory** view.
3. [] Select the **Tiny-Veeam** virtual machine.
4. [] Click the **VeeamZIP** button on the **Virtual Machine** ribbon.
5. [] Select **VeeamZIP...**.
6. [] Click the **Backup Repository** drop down menu.
7. [] Select **Default Backup Repository (Created by Veeam Backup)**.
6. [] Click the **More >>** button.
> Note: Since we did not select a password, Veeam Backup & Replication will produce an unencrypted VeeamZIP file. By default, Veeam Backup & Replication uses application-aware image processing to create a transactionally consistent backup of VMs running applications with VSS support. If you were backing up VMs that run something other than Windows OS or applications without VSS support, you could enable this option by unticking the Disable guest quiescence check box.

7. [] Tick the **Disable guest quiescence (perform crash consistent backup)** check box.
8. [] Click the **OK** button to start the job.
9. [] Click the **OK** button to dismiss the **Tiny-Veeam** job window.
> Important: Do **NOT** wait for the job to finish before moving on to the next action.

10. [] Launch **File Explorer** from the **Windows taskbar**.
11. [] Navigate to the +++X:\\Backup+++ folder.
12. [] Verify the **Tiny-Veeam** VBK full backup file is present then close the **File Explorer** window.
> Note: If you need to quickly create a restore point for the selected VM, VeeamZIP (full backup) or quick backup (incremental backup) can be used. Quick backup is an incremental backup task and can be run only for VMs that have been successfully backed up at least once and have a full restore point.

===

# Lab 4.4

In this lab exercise, you will create backup jobs to protect the virtual machines in the environment.

## Step 1: Create and schedule a backup job for VEEAM-ORCL and Tiny-Veeam

1. [] Navigate to the **Home** view.
3. [] Click the **Backup Job** button on the **Home** ribbon.
4. [] Select **Virtual machine**.
5. [] Select **VMware vSphere...**.
6. [] Enter name: +++Backup Oracle & Tiny-Veeam+++.
7. [] Click the **Next** button on the **Name** step.
8. [] Click the **Add...** button.
9. [] Expand the **VEEAM-ESX** host.
10. [] Expand the **Production** resource pool.
11. [] Hold the **CTRL** keyboard button and select both the **VEEAM-ORCL** and **Tiny-Veeam** virtual machines.
12. [] Click the **Add** button.
13. [] Click the **Next** button on the **Virtual Machines** step.
14. [] Lower **Restore points to keep on disk** to: 2
15. [] Click the **Advanced** button.
16. [] Untick the **Create synthetic full backups periodically** check box.
> Note: Selecting backup mode Incremental (recommended) while both Create synthetic full backups periodically and Create active full backups periodically are unticked will cause Veeam Backup & Replication to use the third backup mode: Forever Forward Incremental.

17. [] Click the **OK** button.
18. [] Click the **Next** button on the **Storage** step.
19. [] Tick the **Enable application-aware processing** check box.
20. [] Click the **Applications...** button.
21. [] Select **Tiny-Veeam**.
22. [] Click the **Edit...** button.
23. [] Select the **Disable application processing** radio button.
> Note: Tiny-Veeam is a Linux virtual machine and does not support the Microsoft VSS framework, because of this we disable application-aware processing for this virtual machine.

24. [] Click the **OK** button in Tiny-Veeam Processing Settings window.
25. [] Select **VEEAM-ORCL**.
26. [] Click the **Edit...** button.
27. [] Click the **Oracle** tab.
> Note: At this step, you may also specify file exclusions within the File Exclusions tab.

28. [] Review the **Oracle** tab then click the **Add...** button.
29. [] Tick the **Backup logs every** check box.
> Note: With this option selected, Veeam Backup & Replication will periodically ship transaction logs to the backup repository and store them with the Oracle Server VM backup in the Veeam backup repository. Log truncation will still occur during the normal job run

30. [] Click the **OK** button in the **VEEAM-ORCL Processing Settings** window.
31. [] Click the **OK** button in the **Application-Aware Processing Options** window.
32. [] Click the **Add...** button in the **Guest OS credentials** section.
33. [] Select **Linux account** as **VEEAM-ORCL** is Linux-based.
34. [] Enter:
 1. Username: +++oracle+++
 2. Password: +++Pa$$w0rd+++

35. [] Tick the **Elevate specified account to root** check box.
36. [] Tick the **Add account to the sudoers file automatically** check box.
> Note: In a production environment, the Oracle administrator could also configure the same permissions directly on the virtual machine.

37. [] Enter
 1. Root password: +++Pa$$w0rd+++
 2. Description: +++sysdba account for VEEAM-ORCL+++

38. [] Click the **OK** button.
39. [] Click the **Test Now** button.
> Note: Disregard the notice that the testing failed for Tiny-Veeam — we have disabled the application-aware processing for this VM.
>
> Important: If the test fails for VEEAM-ORCL, it is likely that the username or password has a typo - please go back, check the username and re-enter the password OR ask your trainer for assistance in resolving the issue.

40. [] Click the **Close** button.
41. [] Click the **Next** button on the **Guest Processing** step.
42. [] Tick the **Run the job automatically** check box.
> Important: If you do not schedule a job, you must be aware of two limitations: 
>
> 1. Even if transaction log backups are enabled in the job, the transaction logs will not be backed up.
> 2. There is no option to schedule the automatic retry for jobs configured to start only manually.

43. [] Click the **Apply** button on the **Schedule** step.
44. [] Tick the **Run the job when I click Finish** check box.
45. [] Click the **Finish** button on the **Summary** step.
> Note: If you forgot to select Run the job when I click Finish, start the backup job manually.
>
> **Important: Do not wait for this job to finish before moving to the next step.**

===

## Step 2: Create and schedule a backup job for VEEAM-DC01, VEEAM-EX01 and VEEAM-SP01

1. [] Click the **Backup Job** button on the **Home** ribbon.
2. [] Select  **Virtual machine**.
3. [] Select **VMware vSphere...**.
4. [] Enter name: +++Backup Active Directory+++
5. [] Click the **Next** button on the **Name** step.
6. [] Click the **Add...** button.
7. [] Expand the **VEEAM-ESX** host.
8. [] Expand the **Production** resource pool.
9. [] Hold the **CTRL** keyboard button and select both the **VEEAM-DC01**, **VEEAM-EX01** and **VEEAM-SP01** virtual machines.
10. [] Click the **Add** button.
11. [] Click the **Next** button on the **Virtual Machines** step.
12. [] Lower **Restore points to keep on disk** to: 2.
13. [] Click the **Backup repository** drop down menu.
14. [] Select **Local Backup Repository**.

13. [] Click the **Advanced** button.
14. [] Select the **Reverse incremental (slower)** radio button.
15. [] Click the **OK** button.
16. [] Click the **Next** button on the **Guest processing** step.
17. [] Tick the **Enable application-aware processing** check box.
> Note: Enable application-aware image processing is used to freeze the VMs when the snapshot is created. This leads to the creation of a transactionally consistent backup that ensures successful recovery of VM applications without any data loss.

18. [] Tick the **Enable guest file system indexing** check box.
> Note: Veeam Backup Enterprise Manager does not require guest file system indexing to be enabled to perform file-level recovery, however, it is required to search for files across restore points.

19. [] Click the **Applications...** button
20. [] Select **VEEAM-SP01**
> Note: The VEEAM-SP01 virtual machine contains Microsoft SQL Server.

20. [] Click the **Edit...** button.
21. [] Click the **SQL** tab.
22. [] Select the **Backup logs periodically** radio button.
> Note: For this setting to take effect, you should ensure that the full or bulk-logged recovery model is turned on for the required databases on the SQL Server VM. If the recovery model is set to Simple, Veeam Backup & Replication does not detect or process the SQL Server VM’s logs. If Full model is enabled, but neither the Backup nor Truncate logs option is selected, logs will increase in size and occupy disk space.

23. [] Click the **OK** button in the **VEEAM-SP01 Processing Settings** window.
24. [] Click the **OK** button in the **Application-Aware Processing Options** window.
25. [] Click the **Add...** button in the **Guest OS credentials** section.
26. [] Select **Standard account...**.
27. [] Enter:
 1. Username: +++VEEAMLAB\Administrator+++
 2. Password: +++Pa$$w0rd+++
 3. Description: +++VEEAMLAB domain administrator+++

28. [] Click the **OK** button.
29. [] Click the **Test Now** button.
30. [] Wait for the **Status** of the virtual machines to change to **Success** then click the **Close** button.
31. [] Click the **Next** button on the **Guest Processing** step.
32. [] Tick the **Run the job automatically** check box.
33. [] Click the **Apply** button on the **Schedule** step.
34. [] Tick the **Run the job when I click Finish** check box.
> **Important: It is very important this backup job is launched on the first day of the class. Do not wait for any jobs to finish before moving to the next step.**

35. [] Click the **Finish** button on the **Summary** step.

===

## Step 4: Create and run an encrypted backup job for Tiny-Veeam2

1. [] Click the **Backup Job** on the **Home** ribbon.
2. [] Select **Virtual machine**.
3. [] Select **Microsoft Hyper-V...**.
4. [] Enter name: +++Backup Tiny-Veeam2+++
5. [] Click the **Next** button on the **Name** step.
6. [] Click the **Add...** button.
7. [] Expand the **VEEAM-HYPERV** host.
8. [] Select **Tiny-Veeam2**
9. [] Click the **Add** button.
10. [] Click the **Next** button on the **Virtual Machines** step.
11. [] Click the **Choose...** button.
> Note: The default settings mean if the off-host backup is misconfigured or not available, the backups will be made in on-host mode. If this behavior is unwanted, simply untick the Failover to on-host backup mode if no suitable off-host proxies available check box.

12. [] Review the **Backup Proxy** window options then click the **Cancel** button.
13. [] Lower **Restore points to keep on disk** to: 2.
14. [] Click the **Advanced** button.
15. [] Untick the **Create synthetic full backups periodically** checkbox.
16. [] Click the **Storage** tab.
17. [] Tick the **Enable backup file encryption** check box.
18. [] Click the **Add...** button in the **Encryption** section.
19. [] Enter:
 1. Hint: +++Technical course that provides extensive information on Veeam solutions+++
 2. Password: +++vmce+++

> Note: It is strongly recommended that you provide a meaningful hint that will help you recall the password. The password hint is displayed when you import an encrypted file to the Veeam backup server and access it.

20. [] Click the **OK** button in the Password window.
21. [] Currently, configuration backup does not have encryption enabled. Because you just enabled encryption for a job, configuration backup has been disabled until you enable the encryption of configuration backup. Click the **OK** button.

22. [] Verify the encryption password hint is displayed then click the **OK** button in the Advanced Settings window.
> Note: If even one job has encryption enabled, configuration backup will not be performed unless it also has encryption enabled. This is due to security risks.

23. [] Click the **Next** button on the **Storage** step.
24. [] Keep the default settings and click the **Next** button on the **Guest Processing** step.
> Note: As Tiny-Veeam2 is a DOS-based server we will not enable application-aware processing.

25. [] Tick the **Run this job automatically** check box.
26. [] Select the **Monthly at this time** radio button.
27. [] Click the **Apply** button on the **Schedule** step.
28. [] Tick the **Run the job when I click Finish** check box.
29. [] Click the **Finish** button on the **Summary** step.
> **Important: Do not wait for any jobs to finish before moving to the next step.**

30. [] Close the **Veeam Backup & Replication** window.

---

# Congratulations!

You have completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
