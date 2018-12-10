Module 4: Protect

---
**This lab is expected to last a maximum of 60 minutes including lab launch.**

# Module 4: Protect

## Step 1: Create and schedule a backup job for VEEAM-ORCL and Tiny-Veeam

1. [] Launch the **Veeam Backup & Replication console** from the desktop.
2. [] Click the **Connect** button.
3. [] Click the **Backup Job** button on the **Home** ribbon.
4. [] Select **Virtual machine**.
5. [] Select **VMware vSphere...**.
6. [] Enter name: +++Backup Oracle+++.
7. [] Click the **Next** button on the **Name** step.
8. [] Click the **Add...** button.
9. [] Expand the **VEEAM-ESX** host.
10. [] Expand the **Production** resource pool.
11. [] Hold the **CTRL** keyboard button and select both the **VEEAM-ORCL** and **Tiny-Veeam** virtual machines.
12. [] Click the **Add** button.
13. [] Click the **Next** button on the **Virtual Machines** step.
14. [] Lower **Restore points to keep on disk** to: +++2+++.
15. [] Click the **Advanced** button.
16. [] Untick the **Create synthetic full backups periodically** check box.
17. [] Click the **OK** button.
18. [] Click the **Next** button on the **Storage** step.
19. [] Tick the **Enable application-aware processing** check box.
> Note: Veeam Backup Enterprise Manager does not require guest file system indexing to be enabled to perform file-level recovery, however, it is required to search for files across restore points.

20. [] Click the **Applications...** button.
21. [] Select **Tiny-Veeam**.
22. [] Click the **Edit...** button.
23. [] Select the **Disable application processing** radio button.
> Note: Tiny-Veeam is a DOS-based virtual machine and does not support the Microsoft VSS framework, because of this we disable application-aware processing for this virtual machine.

24. [] Click the **OK** button in Tiny-Veeam Processing Settings.
25. [] Select **VEEAM-ORCL**.
26. [] Click the **Edit...** button.
27. [] Click the **Oracle** tab.
> Note: At this step, you may also specify file exclusions within the File Exclusions tab.

28. [] Review the **Oracle** tab then click the **Add...** button.
29. [] Enter:
 1. Username: +++oracle+++
 2. Password: +++Pa$$w0rd+++
 3. Description: +++sysdba account for VEEAM-ORCL+++

30. [] Click the **OK** button.
31. [] Tick the **Backup logs every** check box.
> Note: With this option selected, Veeam Backup & Replication will periodically ship transaction logs to the backup repository and store them with the Oracle Server VM backup in the Veeam backup repository. Log truncation will still occur during the normal job run

32. [] Click the **OK** button in the VEEAM-ORCL Processing Settings.
33. [] Click the **OK** button in the Application-Aware Processing Options window.
34. [] Click the **Add...** button in the **Guest OS credentials** section.
35. [] Select **Linux account** as **VEEAM-ORCL** is Linux-based.
36. [] Enter:
 1. Username: +++oracle+++
 2. Password: +++Pa$$w0rd+++

37. [] Tick the **Elevate specified account to root** check box.
38. [] Tick the **Add account to the sudoers file automatically** check box.
> Note: In a production environment, the Oracle administrator could also configure the same permissions directly on the virtual machine.

39. [] Enter root password: +++Pa$$w0rd+++
40. [] Click the **OK** button.
41. [] Click the **Test Now** button.
> Note: Disregard the notice that the testing failed for Tiny-Veeam — we have disabled the application-aware processing for this VM.
>
> Important: If the test fails for VEEAM-ORCL, it is likely that the username or password has a typo - please go back, check the username and re-enter the password OR ask your trainer for assistance in resolving the issue.

42. [] Click the **Close** button.
43. [] Click the **Next** button on the **Guest Processing** step.
44. [] Tick the **Run the job automatically** check box.
> Important: If you do not schedule a job, you must be aware of two limitations: 
>
> 1. Even if transaction log backups are enabled in the job, the transaction logs will not be backed up.
> 2. There is no option to schedule the automatic retry for jobs configured to start only manually.

45. [] Click the **Apply** button on the **Schedule** step.
46. [] Tick the **Run the job when I click Finish** check box.
47. [] Click the **Finish** button on the **Summary** step.
> Note: If you forgot to select Run the job when I click Finish, start the backup job manually.
>
> **Important: Do not wait for this job to finish before moving to the next step.**

===

## Step 2: Create and schedule a backup job for VEEAM-DC01

1. [] Click the **Backup Job** button on the **Home** ribbon.
2. [] Select  **Virtual machine**.
3. [] Select **VMware vSphere...**.
4. [] Enter name: +++Backup Active Directory+++
5. [] Click the **Next** button on the **Name** step.
6. [] Click the **Add...** button.
7. [] Expand the **VEEAM-ESX** host.
8. [] Expand the **Production** resource pool.
9. [] elect the **VEEAM-DC01** virtual machine.
10. [] Click the **Add** button.
11. [] Click the **Next** button on the **Virtual Machines** step.
12. [] Lower **Restore points to keep on disk** to +++2+++.
13. [] Click the **Advanced** button.
14. [] Select the **Reverse incremental (slower)** radio button.
15. [] Click the **OK** button.
16. [] Click the **Next** button on the **Guest processing** step.
17. [] Tick the **Enable application-aware processing** check box.
> Note: Enable application-aware image processing is used to freeze the VMs when the snapshot is created. This leads to the creation of a transactionally consistent backup that ensures successful recovery of VM applications without any data loss.

18. [] Tick the **Enable guest file system indexing** check box.
> Note: Guest file indexing allows you to search for VM guest OS files inside VM backups using Veeam Backup Enterprise Manager.

20. [] Click the **Add...** button in the **Guest OS credentials** section.
21. [] Select **Standard account...**.
22. [] Enter:
 1. Username: +++VEEAMLAB\Administrator+++
 2. Password: +++Pa$$w0rd+++

23. [] Click the **OK** button.
24. [] Click the **Test Now** button.
25. [] Wait for the **Status** of the **VEEAM-DC01** virtual machine to change to **Success** then click the **Close** button.
26. [] Click the **Next** button on the **Guest Processing** step.
27. [] Tick the **Run the job automatically** check box.
28. [] Click the **Apply** button on the **Schedule** step.
29. [] Tick the **Run the job when I click Finish** check box.
> **Important: It is very important this backup job is launched on the first day of the class. Do not wait for the jobs to finish before moving to the next step.**

30. [] Click the **Finish** button on the **Summary** step.

===

## Step 3: Create and schedule a backup job for VEEAM-EX01 and VEEAM-SP01

1. [] Click the **Backup Job** button on the **Home** ribbon.
2. [] Select  **Virtual machine**.
3. [] Select **VMware vSphere...**.
4. [] Enter name: +++Backup Exchange & SharePoint+++
5. [] Click the **Next** button on the **Name** step.
6. [] Click the **Add...** button.
7. [] Expand the **VEEAM-ESX** host.
8. [] Expand the **Production** resource pool.
9. [] Hold the **CTRL** button and select the **VEEAM-EX01** and **VEEAM-SP01** virtual machines.
10. [] Click the **Add** button.
11. [] Click the **Next** button on the **Virtual Machines** step.
12. [] Lower **Restore points to keep on disk** to +++2+++.
13. [] Click the **Advanced** button.
14. [] Select the **Reverse incremental (slower)** radio button.
15. [] Click the **OK** button.
16. [] Click the **Next** button on the **Guest processing** step.
17. [] Tick the **Enable application-aware processing** check box.
> Note: Enable application-aware image processing is used to freeze the VMs when the snapshot is created. This leads to the creation of a transactionally consistent backup that ensures successful recovery of VM applications without any data loss.

18. [] Click the **Applications...** button
19. [] Select **VEEAM-SP01**
> Note: The VEEAM-SP01 virtual machine contains Microsoft SQL Server.

20. [] Click the **Edit...** button.
21. [] Click the **SQL** tab.
22. [] Select the **Backup logs periodically** radio button.
23. [] Increase **Backup logs every** to +++60+++ minutes.
> Note: For this setting to take effect, you should ensure that the full or bulk-logged recovery model is turned on for the required databases on the SQL Server VM. If the recovery model is set to Simple, Veeam Backup & Replication does not detect or process the SQL Server VM’s logs. If Full model is enabled, but neither the Backup nor Truncate logs option is selected, logs will increase in size and occupy disk space.

24. [] Click the **OK** button in the VEEAM-SP01 Processing Settings.
25. [] Click the **OK** button in the Application-Aware Processing Options.
26. [] Click the **Guest OS credentials** drop down menu.
27. [] Select the **VEEAMLAB\Administrator** account.
28. [] Click the **Test Now** button.
29. [] Wait for the **Status** of all virtual machines to change to **Success** then click the **Close** button.
30. [] Click the **Next** button on the **Guest Processing** step.
31. [] Tick the **Run the job automatically** check box.
32. [] Click the **Apply** button on the **Schedule** step.
33. [] Tick the **Run the job when I click Finish** check box.
> **Important: It is very important this backup job is launched on the first day of the class. Do not wait for the jobs to finish before moving to the next step.**

34. [] Click the **Finish** button on the **Summary** step.

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
12. [] Review the **Backup Proxy** window options then click the **Cancel** button.
> Note: As we don’t have a configured off-host backup proxy at the moment, the backup will be made in on-host mode.

13. [] Lower **Restore points to keep on disk** to +++2+++
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
> Note: As Tiny-Veeam2 is a DOS-based server we decided to not enable application-aware processing.

25. [] Tick the **Run this job automatically** check box.
26. [] Select the **Monthly at this time** radio button.
27. [] Click the **Apply** button on the **Schedule** step.
28. [] Tick the **Run the job when I click Finish** check box.
29. [] Click the **Finish** button on the **Summary** step.
> **Important: Do not wait for the jobs to finish before moving to the next step.**

===

# Lab 4.2: Creating backups with VeeamZIP

1. [] Navigate to the **Inventory** view.
2. [] Select the **VEEAM-ESX** host in the **VMware vSphere** section of the **Inventory** view.
3. [] Select the **Tiny-Veeam** virtual machine.
4. [] Click the **VeeamZIP** button on the **Virtual Machine** ribbon.
5. [] Select **VeeamZIP...**.
6. [] Click the **More >>** button.
> Note: Since we did not select a password, Veeam Backup & Replication will produce an unencrypted VeeamZIP file. By default, Veeam Backup & Replication uses application-aware image processing to create a transactionally consistent backup of VMs running applications with VSS support. If you were backing up VMs that run something other than Windows OS or applications without VSS support, you could enable this option by clearing the Disable guest quiescence check box.

7. [] Tick the **Disable guest quiescence (perform crash consistent backup)** check box.
8. [] Click the **OK** button to start the job.
9. [] Click the **OK** button to dismiss the **Tiny-Veeam** job window.
> Important: Do **NOT** wait for the job to finish before moving on to the next step.

10. [] Launch **File Explorer** from the **Windows taskbar**.
11. [] Navigate to the +++X:\\Backup+++ folder.
> Note: Because of the way Scale-out Backup Repository works, your VeeamZIP backup could have been stored in the E:\Backups folder.

12. [] Verify the **Tiny-Veeam** VBK full backup file is present then close the **File Explorer** window.
> Note: If you need to quickly create a restore point for the selected VM, VeeamZIP (full backup) or quick backup (incremental backup) can be used. Quick backup is an incremental backup task and can be run only for VMs that have been successfully backed up at least once and have a full restore point.

===

# Lab 4.3: Creating an off-site backup copy job

## Step 1: Install "remote" WAN accelerator

1. [] Navigate to the **Backup infrastructure** view.
2. [] Select **WAN Accelerators** in the **Backup Infrastructure** view.
3. [] Click the **Add WAN Accelerator** button on the **WAN Accelerator** ribbon.
4. [] Click the **Choose server** drop down menu.
5. [] Select **VEEAM-Remote**.
6. [] Click the **Next** button on the **Server** step.
7. [] Verify the **Folder** is set to **X:\VeeamWAN** then lower the **Cache size** to +++10+++ GB.
> Important: **WARNING! Do NOT use the default cache size of 100 GB. Leaving the default cache size in place will result in the lab running out of space and ultimately the job will fail**. We’re using 10 GB for demonstration only. Please check the User Guide for sizing recommendations.

8. [] Click the **Next** on the **Cache** step.
9. [] Keep the default settings and click the **Apply** button on the **Review** step.
10. [] Keep the default settings and click the **Next** button on the **Apply** step.
11. [] Click the **Finish** button on the **Summary** step.

===

## Step 2: Install a local WAN accelerator

1. [] Click the **Add WAN Accelerator** button on the **WAN Accelerator** ribbon.
2. [] Verify **Choose server** already has **VEEAM-VBR.veeaminfra.local** selected then click the **Next** button on the **Server** step.
3. [] Verify the **Folder** is set to **X:\VeeamWAN** then lower the **Cache size** to +++10+++ GB.
> Important: **WARNING! Do NOT use the default cache size of 100 GB. Leaving the default cache size**

4. [] Click the **Next** on the **Cache** step.
5. [] Click the **Apply** button on the **Review** step.
6. [] Click the **Next** button on the **Apply** step.
7. [] Click the **Finish** button on the **Summary** step.
8. [] Verify both WAN accelerators are present then navigate to the **Home** view.

===

## Step 3: Create a backup copy job

1. [] Click the **Backup Copy** button on the **Home** ribbon.
2. [] Select **Virtual Machine**.
3. [] Select **VMware vSphere backup...**.
4. [] Enter name: +++Backup Copy via WAN accelerators+++
5. [] Modify **Copy every** to +++2+++ day.
6. [] Click the **Next** button on the **Job** step.
7. [] Click the **Add...** button.
8. [] Select **From backups...**.
9. [] Expand the **Backup Oracle** backup job.
10. [] Select **Tiny-Veeam**.
11. [] Click the **Add** button.
12. [] Click the **Next** button on the **Objects** step.
13. [] Click the **Backup repository** drop down menu.
14. [] Select **Remote Repository**.
15. [] Lower **Restore points to keep** to +++3+++.
16. [] Click the **Advanced** button.
17. [] Tick the **Defragment and compact full backup file** check box.
> Note: This setting will periodically compact the full backup, however, this option can only be enabled if GFS settins are disabled.

18. [] Click the **OK** button.
19. [] Click the **Next** button on the **Target** step.
20. [] Click the **Yes** button to ignore the data sovereignty violation warning.
21. [] Select the **Through built-in WAN accelerators** radio button.
22. [] Click the **Source WAN accelerator** drop down menu.
23. [] Select **VEEAM-VBR**.
24. [] Click the **Target WAN accelerator** drop down menu.
25. [] Select **VEEAM-Remote**.
26. [] Click the **Next** button on the **Data Transfer** step.
27. [] Click the **OK** button to safely ignore that the target WAN accelerator cache is empty.
28. [] Keep the default setting and click the **Apply** button on the **Schedule** step.
29. [] Keep the default setting and click the **Finish** button on the **Summary** step.
> **Important: Do not wait for the jobs to finish before moving to the next step.**
>
> Note: The Backup Copy job starts automatically copying the last restore point for Tiny-Veeam and will be transported from the source repository to the second Backup Target since it was created within the sync interval.

===

# Lab 4.4: Creating replicas

## Step 1: Seed replication job for Tiny-Veeam

1. [] Click the **Replication Job** button on the **Home** ribbon.
2. [] Select **Virtual machine**.
3. [] Select **VMware vSphere...**.
4. [] Enter name: +++Replication Tiny-Veeam+++
5. [] Tick the **Low connection bandwidth (enable replica seeding)** check box.
6. [] Click the **Next** button on the **Name** step.
7. [] Click the **Add...** button.
8. [] Expand the **VEEAM-ESX** host.
9. [] Expand the **Production** resource pool.
10. [] Select **Tiny-Veeam**.
11. [] Click the **Add** button.
12. [] Click the **Next** button on the **Virtual Machines** step.
13. [] Click the **Choose...** button in the **Host or cluster** section.
14. [] Select **VEEAM-ESX**.
15. [] Click the **OK** button.
16. [] Click the **Choose...** button in the **Resource pool** section.
17. [] Select the **Replicas** resource pool.
18. [] Click the **OK** button.
19. [] Click the **Next** button on the **Destination** step.
20. [] Lower **Restore points to keep** to +++3+++.
> Note: It is generally recommended to store replica metadata in a repository that is close to the source proxy, however, Scale-out Backup Repositories are not a supported target for replication job metadata.

21. [] Click the **Next** button on the **Job Settings** step.
22. [] Keep the default settings and click the **Next** button on the  **Data Transfer** step.
23. [] Tick the **Get seed from the following backup repository** check box.
> Note: This will make the replication job use the Backup Jopy job placed in the Remote Repository as a source for the first run of this replication job. All subsequent runs will use the production environment as the source.

24. [] Click the **Next** button on the **Seeding** step.
25. [] Keep the default settings and click the **Next** button on the **Guest processing** step.
26. [] Tick the **Run the job automatically** check box.
27. [] Keep the default schedule and click the **Apply** button on the **Schedule** step.
28. [] Tick the **Run the job when I click Finish** check box.
29. [] Click the **Finish** button on the **Summary** step.
> **Important: Do not wait for the jobs to finish before moving to the next step.**

===

## Step 2: Create a replica for VEEAM-DC01

1. [] Click the **Replication Job** button on the **Home** ribbon.
2. [] Select **Virtual machine**.
3. [] Select **VMware vSphere...**.
4. [] Enter name: +++Replication Active Directory+++.
5. [] Click the **Next** button on the **Name** step.
6. [] Click the **Add...** button.
7. [] Expand the **VEEAM-ESX** host.
8. [] Expand the **Production** resource pool.
9. [] Select **VEEAM-DC01**.
10. [] Click the **Add** button.
11. [] Click the **Next** button on the **Virtual Machines** step.
12. [] Click the **Choose...** button in the **Host or cluster** section.
13. [] Select **VEEAM-ESX**.
14. [] Click the **OK** button.
15. [] Click the **Choose...** button in the **Resource pool** section.
16. [] Expand the **VEEAM-ESX** host.
17. [] Select **Replicas**.
18. [] Click the **OK** button.
19. [] Click the **Next** button on the **Destination** step.
20. [] Lower **Restore points to keep** to +++3+++.
> Note: It is generally recommended to store replica metadata in a repository that is close to the source proxy.

21. [] Click the **Next** button on the **Job Settings** step.
22. [] Keep the default settings and click the **Next** button on the **Data Transfer** step.
23. [] Tick the **Enable application-aware processing** check box.
24. [] Click the **Guest OS credentials** drop down menu.
25. [] Select **VEEAMLAB\\Administrator**.
26. [] Click the **Test Now** button.
> Note: Select the VM and review the stages of the process on the right.

27. [] Wait for all tests have reached status **Success** then click the **Close** button.
28. [] Click the **Next** button on the **Guest Processing** step.
29. [] Tick the **Run the job automatically** check box.
30. [] Keep the default schedule and click the **Apply** button on the **Schedule** step.
31. [] Tick the **Run the job when I click Finish** check box.
32. [] Click the **Finish** button on the **Summary** step.
> **Important: Do not wait for the jobs to finish before moving to the next step.**

===

## Step 3: Create a "remote" replica from backup for Tiny-Veeam2


1. [] Click the **Replication Job** button on the **Home** ribbon.
2. [] Select **Virtual machine**.
3. [] Select **Microsoft Hyper-V...**.
4. [] Enter name: +++Replication Tiny-Veeam2 from backup+++.
5. [] Click the **Next** button on the **Name** step.
6. [] Click the **Add...** button.
7. [] Expand the **VEEAM-HYPERV** host.
8. [] Select **Tiny-Veeam2**.
9. [] Click the **Add** button.
10. [] Click the **Source...** button.
11. [] Select the **From backup files (latest VM state available in backups)** radio button.
12. [] Tick the **Scale-out Backup Repository** check box.
13. [] Click the **OK** button.
14. [] Click the **Next** button on the **Virtual Machines** step.
15. [] Click the **Choose...** button in the **Host or cluster** section.
16. [] Select **VEEAM-HYPERV**.
17. [] Click the **OK** button.
18. [] Click the **Next** button on the **Destination** step.
19. [] Lower **Restore points to keep** to +++2+++.
> Note: It is generally recommended to store replica metadata in a repository that is close to the source proxy.

20. [] Click the **Next** button on the **Job Settings** step.
21. [] Keep the default settings and click the **Next** button on the **Data Transfer** step.
22. [] Tick the **Run the job automatically** check box.
23. [] Select the **Monthly at this time** radio button.
24. [] Click the **Apply** button on the **Schedule** step.
25. [] Tick the **Run the job when I click Finish** check box.
26. [] Click the **Finish** button on the **Summary** step.
> **Important: Do not wait for the replication jobs to complete.**
>
> Note: When the backup repository is the only source of data, the replication job is often referred to as remote replica from backup. It will always capture only the most recent restore point data from the repository that was created since the remote replica was running last time.

27. [] Close the **Veeam Backup and Replication console** window.

---

# Congratulations!

You have completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
