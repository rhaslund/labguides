Module 4: Protect

---
**This lab is expected to last a maximum of 60 minutes including lab launch.**

# Module 4: Protect

## Step 1: Create and schedule a backup job for VEEAM-ORCL and Tiny-Veeam

1. [] Launch the **Veeam Backup & Replication console** from the desktop.
2. [] Click the **Connect** button.
3. [] Click the **Backup Job** button on the **Home** ribbon.
4. [] Select **VMware vSphere...**.
5. [] Enter name: +++Backup ORCL+++.
6. [] Click the **Next** button on the **Name** step.
7. [] Click the **Add...** button.
8. [] Expand the **VEEAM-ESX** host.
9. [] Expand the **Production** resource pool.
10. [] Hold the **CTRL** keyboard button and select both the **VEEAM-ORCL** and **Tiny-Veeam** virtual machines.
11. [] Click the **Add** button.
11. [] Click the **Next** button on the **Virtual Machines** step.
12. [] Lower **Restore points to keep on disk** to: +++2+++.
13. [] Click the **Advanced** button.
14. [] Untick the **Create synthetic full backups periodically** check box.
14. [] Click the **OK** button.
15. [] Click the **Next** button on the **Storage** step.
16. [] Tick the **Enable application-aware processing** check box.
> Note: Veeam Backup Enterprise Manager does not require guest file system indexing to be enabled to perform file-level recovery, however, it is required to search for files across restore points.

17. [] Click the **Applications...** button.
18. [] Select **Tiny-Veeam**.
19. [] Click the **Edit...** button.
20. [] Select the **Disable application processing** radio button.
> Note: Tiny-Veeam is a DOS-based virtual machine and does not support the Microsoft VSS framework, because of this we disable application-aware processing for this virtual machine.

21. [] Click the **OK** button.
22. [] Select **VEEAM-ORCL**.
23. [] Click the **Edit...** button.
24. [] Click the **Oracle** tab.
> Note: At this step, you may also specify file exclusions within the File Exclusions tab.

25. [] Review the **Oracle** tab then click the **Add...** button.
26. [] Enter:
 1. Username: +++oracle+++
 2. Password: +++Pa$$w0rd+++
 3. Description: +++sysdba account for VEEAM-ORCL+++

27. [] Click the **OK** button.
28. [] Tick the **Backup logs every** check box.
> Note: With this option selected, Veeam Backup & Replication will periodically ship transaction logs to the backup repository and store them with the Oracle Server VM backup in the Veeam backup repository. Log truncation will still occur during the normal job run


29. [] Click the **OK** button.
30. [] Click the **OK** button.
31. [] Click the **Add...** button in the **Guest OS credentials** section.
32. [] Select **Linux account** as **VEEAM-ORCL** is Linux-based.
33. [] Enter:
 1. Username: +++oracle+++
 2. Password: +++Pa$$w0rd+++

34. [] Tick the **Elevate specified account to root** check box.
35. [] Tick the **Add account to the sudoers file automatically** check box.
> Note: In a production environment, the Oracle administrator could also configure the same permissions directly on the virtual machine.

36. [] Enter root password: +++Pa$$w0rd+++.
37. [] Click the **OK** button.
37. [] Click the **Test Now** button.
> Note: Disregard the notice that the testing failed for Tiny-Veeam — we have disabled the application-aware processing for this VM.
>
> Important: If the test fails for VEEAM-ORCL, it is likely that the username or password has a typo - please go back, check the username and re-enter the password OR ask your trainer for assistance in resolving the issue.

38. [] Click the **Close** button.
39. [] Click the **Next** button on the **Guest Processing** step.
40. [] Tick the **Run the job automatically** check box.
> Important: If you do not schedule a job, you must be aware of two limitations: 
>
> 1. Even if transaction log backups are enabled in the job, the transaction logs will not be backed up.
> 2. There is no option to schedule the automatic retry for jobs configured to start only manually.

42. [] Click the **Apply** button on the **Schedule** step.
43. [] Tick the **Run the job when I click Finish** check box.
44. [] Click the **Finish** button on the **Summary** step.
> Note: If you forgot to select Run the job when I click Finish, start the backup job manually.

45. [] Select the **Backup ORCL** backup job.
46. [] Verify the job has started then select **Jobs** in the **Home** view.
> Important: Do not wait for this job to finish before moving to the next step.

===

## Step 2: Create and schedule a backup job for VEEAM-DC01, VEEAM-EX01 and VEEAM-SP01

1. [] Click the **Backup Job** button on the **Home** ribbon.
2. [] Select **VMware vSphere...**.
3. [] Enter name: +++Backup AD & Exchange & SharePoint+++
4. [] Click the **Next** button on the **Name** step.
5. [] Click the **Add...** button.
6. [] Expand the **VEEAM-ESX** host.
7. [] Expand the **Production** resource pool.
8. [] Hold the **CTRL** button and select the **VEEAM-DC01**, **VEEAM-EX01** and **VEEAM-SP01** virtual machines.
9. [] Click the **Add** button.
10. [] Click the **Next** button on the **Virtual Machines** step.
11. [] Lower **Restore points to keep on disk** to +++2+++.
12. [] Click the **Advanced** button.
13. [] Select the **Reverse incremental (slower)** radio button.
14. [] Click the **OK** button.
15. [] Click the **Next** button on the **Guest processing** step.
16. [] Tick the **Enable application-aware processing** check box.
> Note: Enable application-aware image processing is used to freeze the VMs when the snapshot is created. This leads to the creation of a transactionally consistent backup that ensures successful recovery of VM applications without any data loss.

17. [] Tick the **Enable guest file system indexing** check box.
> Note: Note: Guest file indexing allows you to search for VM guest OS files inside VM backups using Veeam Backup Enterprise Manager.

18. [] Click the **Applications** button
19. [] Select **VEEAM-SP01**
> Note: The VEEAM-SP01 virtual machine contains Microsoft SQL Server.

20. [] Click the **Edit** button.
21. [] Click the **SQL** tab.
22. [] Select the **Backup logs periodically** radio button.
23. [] Increase **Backup logs every** to +++60+++ minutes.
> Note: For this setting to take effect, you should ensure that the full or bulk-logged recovery model is turned on for the required databases on the SQL Server VM. If the recovery model is set to Simple, Veeam Backup & Replication does not detect or process the SQL Server VM’s logs. If Full model is enabled, but neither the Backup nor Truncate logs option is selected, logs will increase in size and occupy disk space.

24. [] Click the **OK** button.
25. [] Click the **OK** button.
26. [] Click the **Add...** button in the **Guest OS credentials** section.
27. [] Select **Standard account...**.
28. [] Enter:
 1. Username: +++VEEAMLAB\Administrator+++
 2. Password: +++Pa$$w0rd+++

29. [] Click the **OK** button.
30. [] Click the **Test Now** button.
31. [] Wait for the **Status** of all virtual machines to change to **Success** then click the **Close** button.
32. [] Click the **Next** button on the **Guest Processing** step.
33. [] Tick the **Run the job automatically** check box.
34. [] Modify the schedule to run daily at **10:00 PM**.
35. [] Click the **Apply** button on the **Schedule** step.
36. [] Tick the **Run the job when I click Finish** check box.
> Important: It is **very important** this backup job is launched on the **first day of the class**. Do not wait for the jobs to finish before moving to the next step.

37. [] Click the **Finish** button

===

## Step 3: Create and run an encrypted backup job for Tiny-Veeam2

1. [] Click the **Backup Job** on the **Home** ribbon.
2. [] Select **Microsoft Hyper-V...**
3. [] Enter name: +++Backup Tiny-Veeam2+++
4. [] Click the **Next** button on the **Name** step.
5. [] Click the **Add...** button.
6. [] Expand the **VEEAM-HYPERV** host.
7. [] Select **Tiny-Veeam2**
8. [] Click the **Add** button.
9. [] Click the **Next** button on the **Virtual Machines** step.
10. [] Click the **Choose** button.
11. [] Review the **Backup Proxy** window options then click the **Cancel** button.
> Note: As we don’t have a configured off-host backup proxy at the moment, the backup will be made in on-host mode.

12. [] Lower **Restore points to keep on disk** to +++2+++
13. [] Click the **Advanced** button.
14. [] Click the **Storage** tab.
15. [] Tick the **Enable backup file encryption** check box.
16. [] Click the **Add...** button in the **Encryption** section.
17. [] Enter:
 1. Hint: +++Technical course that provides extensive information on Veeam solutions+++
 2. Password: +++vmce+++

> Note: It is strongly recommended that you provide a meaningful hint that will help you recall the password. The password hint is displayed when you import an encrypted file to the Veeam backup server and access it.

18. [] Click the **OK** button.
19. [] Currently, configuration backup does not have encryption enabled. Because you just enabled encryption for a job, configuration backup has been disabled until you enable the encryption of configuration backup. Click the **OK** button.
20. [] Verify the encryption password hint is displayed then click the **OK** button.
> Note: If even one job has encryption enabled, configuration backup will not be performed unless it also has encryption enabled. This is due to security risks.

21. [] Click the **Next** button on the **Storage** step.
21. [] Keep the default settings and click the **Next** button on the **Guest Processing** step.
> Note: As Tiny-Veeam2 is a DOS-based server we decided to not enable application-aware processing.

22. [] Do **NOT** schedule the job and click the **Apply** button.
23. [] Tick the **Run the job when I click Finish** check box.
24. [] Click the **Finish** button on the **Summary** step.

===

# Lab 4.2: Creating backups with VeeamZIP

1. [] Navigate to the **Inventory** view.
2. [] Select the **VEEAM-ESX** host.
3. [] Right-click the **Tiny-Veeam** virtual machine.
4. [] Select **VeeamZIP...**.
5. [] Click the **More >>** button.
> Note: Since we did not select a password, Veeam Backup & Replication will produce an unencrypted VeeamZIP file. By default, Veeam Backup & Replication uses application-aware image processing to create a transactionally consistent backup of VMs running applications with VSS support. If you were backing up VMs that run something other than Windows OS or applications without VSS support, you could enable this option by clearing the Disable guest quiescence check box.

6. [] Click the **OK** button.
7. [] Click the **OK** button.
> Important: Do **NOT** wait for the job to finish before moving on to the next step. The job is expected to end with a warning, because the FreeDOS operation system does not have VMware Tools installed.

8. [] Launch **File Explorer** from the **Windows taskbar**.
9. [] Navigate to the **E:\Backups** folder.
> Note: Because of the way Scale-out Backup Repository works, your VeeamZIP backup could have been stored in the X:\Backup folder.

10. [] Verify the **Tiny-Veeam** VBK full backup file is present then close the **File Explorer** window.
> Note: If you need to quickly create a restore point for the selected VM, VeeamZIP (full backup) or quick backup (incremental backup) can be used. Quick backup is an incremental backup task and can be run only for VMs that have been successfully backed up at least once and have a full restore point.

===

# Lab 4.3: Creating an off-site backup copy job

## Step 1: Install "remote" WAN accelerator

1. [] Navigate to the **Backup infrastructure** view.
2. [] Select **WAN Accelerators**.
3. [] Click the **Add WAN Accelerator** button on the **WAN Accelerator** ribbon.
4. [] Click the **Choose server** drop down menu.
5. [] Select **VEEAM-Remote**.
6. [] Click the **Next** button on the **Server** step.
8. [] Verify the **Folder** is set to **X:\VeeamWAN** then lower the **Cache size** to +++10+++ GB.
> Important: **WARNING! Do NOT use the default cache size of 100 GB. Leaving the default cache size in place will result in the lab running out of space and ultimately the job will fail**. We’re using 10 GB for demonstration only. Please check the User Guide for sizing recommendations.

9. [] Click the **Next** on the **Cache** step.
10. [] Click the **Apply** button on the **Review** step.
11. [] Click the **Next** button on the **Apply** step.
12. [] Click the **Finish** button on the **Summary** step.

===

## Step 2: Install a local WAN accelerator

1. [] Click the **Add WAN Accelerator** button on the **WAN Accelerator** ribbon.
2. [] Click the **Choose server** drop down menu.
3. [] Select **VEEAM-VBR.veeaminfra.local**
4. [] Click the **Next** button on the **Server** step.
5. [] Select the **X:\\** drive.
6. [] Verify the **Folder** is set to **X:\VeeamWAN** then lower the **Cache size** to +++10+++ GB.
> Important: **WARNING! Do NOT use the default cache size of 100 GB. Leaving the default cache size**

7. [] Click the **Next** on the **Cache** step.
8. [] Click the **Apply** button on the **Review** step.
9. [] Click the **Next** button on the **Apply** step.
10. [] Click the **Finish** button on the **Summary** step.
11. [] Verify both WAN accelerators are present then navigate to the **Home** view.

===

## Step 3: Create a backup copy job

1. [] Click the **Backup Copy** button on the **Home** ribbon.
2. [] Select **VMware vSphere backup...**.
3. [] Enter name: +++Backup Copy Job WAN+++
4. [] Modify **Copy every** to +++2+++ day.
5. [] Click the **Next** button on the **Job** step.
6. [] Click the **Add...** button.
7. [] Select **From backups...**.
8. [] Expand the **Backup ORCL** backup job.
9. [] Select **VEEAM-ORCL**.
10. [] Click the **Add** button.
11. [] Click the **Next** button on the **Objects** step.
12. [] Click the **Backup repository** drop down menu.
13. [] Select **Remote Repository**.
14. [] Lower **Restore points to keep** to +++3+++.
15. [] Click the **Advanced** button.
16. [] Tick the **Defragment and compact full backup file** check box.
> Note: This setting will periodically compact the full backup, however, this option can only be enabled if GFS settins are disabled.

17. [] Click the **OK** button.
18. [] Click the **Next** button on the **Target** step.
19. [] Click the **Yes** button to ignore the data sovereignty violation warning.
20. [] Select the **Through built-in WAN accelerators** radio button.
21. [] Click the **Source WAN accelerator** drop down menu.
22. [] Select **VEEAM-VBR**.
23. [] Click the **Target WAN accelerator** drop down menu.
24. [] Select **VEEAM-Remote**.
25. [] Click the **Next** button on the **Data Transfer** step.
26. [] Click the **OK** button to safely ignore that the target WAN accelerator cache is empty.
27. [] Keep the default setting and click the **Apply** button on the **Schedule** step.
28. [] Tick the **Enable the job when I click Finish** check box.
29. [] Click the **Finish** button on the **Summary** step.
30. [] Select the **Backup Copy Job WAN** job.
> Note: Backup Copy Job WAN starts automatically copying the last restore point for VEEAM-ORCL and will be transported from Backup Copy Job to the second Backup Target since it was created within the sync interval.

===

# Lab 4.4: Creating replicas

## Step 1: Map replication job for Tiny-Veeam

1. [] Click the **Replication Job** button on the **Home** ribbon.
2. [] Select **VMware vSphere**.
3. [] Enter name: +++Replication Job Tiny-Veeam+++
4. [] Tick the **Low connection bandwidth (enable replica seeding)** check box.
5. [] Click the **Next** button on the **Name** step.
6. [] Click the **Add...** button.
7. [] Expand the **VEEAM-ESX** host.
8. [] Expand the **Production** resource pool.
9. [] Select **Tiny-Veeam**.
10. [] Click the **Add** button.
11. [] Click the **Next** button on the **Virtual Machines** step.
12. [] Click the **Choose...** button in the **Host or cluster** section.
13. [] Select **VEEAM-ESX**.
14. [] Click the **OK** button.
15. [] Click the **Choose...** button in the **Resource pool** section.
16. [] Select the **Replicas** resource pool.
17. [] Click the **OK** button.
18. [] Click the **Next** button on the **Destination** step.
19. [] Verify that **Remote Repository** is selected as the **Repository for replica metadata** then lower **Restore points to keep** to +++3+++.
> Note: It is generally recommended to store replica metadata in a repository that is close to the source proxy, however, Scale-out Backup Repositories are not a supported target for replication job metadata.

20. [] Keep the default settings and click the **Next** button on the  **Data Transfer** step.
21. [] Tick the **Map replicas to existing VMs** check box.
> Note: In the classroom lab, we prepared an existing replica of the Tiny-Veeam VM. You can map it to the newly created replica job to avoid processing a full replica again.

22. [] Select **Tiny-Veeam**.
23. [] Click the **Edit...** button.
24. [] Expand the **VEEAM-ESX** host.
25. [] Expand the **Replicas** resource pool.
26. [] Select **Tiny-Veeam_replica**.
27. [] Click the **OK** button.
28. [] Click the **Next** button on the **Seeding** step.
29. [] Keep the default settings and click the **Next** button on the **Guest processing** step.
30. [] Tick the **Run the job automatically** check box.
31. [] Keep the default schedule and click the **Apply** button on the **Schedule** step.
32. [] Tick the **Run the job when I click Finish** check box.
33. [] Click the **Finish** button on the **Summary** step.
> Important: Do not wait for the jobs to finish before moving to the next step.

===

## Step 2: Create a replica for VEEAM-DC01

1. [] Click the **Replication Job** button on the **Home** ribbon.
2. [] Select **VMware vSphere...**.
3. [] Enter name: +++Replication Job AD+++.
4. [] Click the **Next** button on the **Name** step.
5. [] Click the **Add...** button.
6. [] Expand the **VEEAM-ESX** host.
7. [] Expand the **Production** resource pool.
8. [] Select **VEEAM-DC01**.
9. [] Click the **Add** button.
10. [] Click the **Next** button on the **Virtual Machines** step.
11. [] Click the **Choose...** button in the **Host or cluster** section.
12. [] Select **VEEAM-ESX**.
13. [] Click the **OK** button.
14. [] Click the **Choose...** button in the **Resource pool** section.
15. [] Expand the **VEEAM-ESX** host.
16. [] Select **Replicas**.
17. [] Click the **OK** button.
18. [] Click the **Next** button on the **Destination** step.
19. [] Lower **Restore points to keep** to +++3+++.
> Note: It is generally recommended to store replica metadata in a repository that is close to the source proxy.

20. [] Click the **Next** button on the **Job Settings** step.
21. [] Keep the default settings and click the **Next** button on the **Data Transfer** step.
22. [] Tick the **Enable application-aware processing** check box.
23. [] Click the **Guest OS credentials** drop down menu.
24. [] Select **VEEAMLAB\\Administrator**.
25. [] Click the **Test Now** button.
> Note: Select the VM and review the stages of the process on the right.

26. [] Wait for all tests have reached status **Success** then click the **Close** button.
27. [] Click the **Next** button on the **Guest Processing** step.
28. [] Tick the **Run the job automatically** check box.
29. [] Keep the default schedule and click the **Apply** button on the **Schedule** step.
30. [] Tick the **Run the job when I click Finish** check box.
31. [] Click the **Finish** button on the **Summary** step.
> Important: Do not wait for the jobs to finish before moving to the next step.

===

## Step 3: Create a "remote" replica from backup for Tiny-Veeam2


1. [] Click the **Replication Job** button on the **Home** ribbon.
2. [] Select **Microsoft Hyper-V...**.
3. [] Enter name: +++Replication Job from Tiny-Veeam2 backup+++.
4. [] Click the **Next** button on the **Name** step.
5. [] Click the **Add...** button.
6. [] Expand the **VEEAM-HYPERV** host.
7. [] Select **Tiny-Veeam2**.
8. [] Click the **Add** button.
9. [] Click the **Source...** button.
10. [] Select the **From backup files (latest VM state available in backups)** radio button.
11. [] Tick the **Main Backup Repository** check box.
12. [] Click the **OK** button.
13. [] Click the **Next** button on the **Virtual Machines** step.
14. [] Click the **Choose...** button in the **Host or cluster** section.
15. [] Select **VEEAM-HYPERV**.
16. [] Click the **OK** button.
17. [] Click the **Next** button on the **Destination** step.
18. [] Lower **Restore points to keep** to +++2+++.
> Note: It is generally recommended to store replica metadata in a repository that is close to the source proxy.

19. [] Keep the default settings and click the **Next** button on the **Job Settings** step.
20. [] Keep the default settings and click the **Next** button on the **Data Transfer** step.
21. [] Do **not** schedule this job and click the **Apply** button on the **Schedule** step.
22. [] Tick the **Run the job when I click Finish** check box.
23. [] Click the **Finish** button on the **Summary** step.
> Note: When the backup repository is the only source of data, the replication job is often referred to as remote replica from backup. It will always capture only the most recent restore point data from the repository that was created since the remote replica was running last time. Do not wait for the replication jobs to complete.

---

# Congratulations!

You have completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
