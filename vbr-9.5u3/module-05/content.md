Module 05: Entire VM Recovery

---
**This lab is expected to last a maximum of 60 minutes including lab launch.**


# Lab 5.1: Instant VM Recovery

1. [] Launch the **Veeam Backup & Replication console** from the desktop.
2. [] Click the **Connect** button.
3. [] Click the **Restore** button on the **Home** ribbon.
4. [] Select **Microsoft Hyper-V backup...**.
5. [] Select **Instant VM recovery**.
6. [] Click the **Next** button on the **Restore Type** step.
7. [] Click the **Add VM** button.
8. [] Select **From backup...**.
9. [] Expand the **Backup Tiny-Veeam2** job.
10. [] Select **Tiny-Veeam2**.
11. [] Click the **Add** button.
12. [] Click the **Next** button on the **Virtual Machines** step.
13. [] Keep the default settings and click the **Next** button on the **Recovery Mode** step.
14. [] Keep the default settings and click the **Next** button on the **Reason** step.
15. [] Click the **Show objects** text link.
16. [] Click the **OK** button.
17. [] Click the **Finish** button on the **Summary** step.
> Note: When you perform restore operations on the same Veeam backup server where it was backed up, the storage keys and metakeys required to unlock an encrypted file are still stored in the Veeam Backup & Replication database. Veeam Backup & Replication uses these keys to unlock the backup file, and you do not have to enter a password.

18. [] Watch the restore process until you see the **Waiting for user action...** text then click the **Close** button.
19. [] Launch the **Hyper-V Manager** from the Windows task bar.
20. [] Select the **VEEAM-DCINFRA** host.
21. [] Select the **Tiny-Veeam2** virtual machine.
23. [] Verify the **Snapshots** pane containts **Veeam Instant VM Recovery snapshot** then close the **Hyper-V Manager** window.
24. [] Select **Instant Recovery (1)** in the **Home** view.
25. [] Select the **Tiny-Veeam2** virtual machine.
26. [] Click the **Migrate to production...** button on the **Instant VM Recovery** ribbon.
> Note: As soon as the migrate to production is completed the Instant Recovery (1) section will disappear. If you no longer see Instant VM Recovery (1) it means the migration to production has completed.

===

# Lab 5.2: Full VM recovery

1. [] Expand **Backups** in the **Home** view.
2. [] Select **Disk**.
3. [] Expand the **Backup ORCL** backup job.
4. [] Verify the **Tiny-Veeam** virtual machine has at least 1 (one) restore point then launch the **VMware vSphere Client** from the Windows task bar.
5. [] Enter:
 1. Name: +++VEEAM-ESX+++
 2. User name: +++root+++
 3. Password: +++Pa$$w0rd+++

6. [] Click the **Login** button.
7. [] Expand the **VEEAM-ESX** host.
8. [] Expand the **Production** resource pool.
9. [] Select **Tiny-Veeam** and review the configuration.
10. [] Switch back to the **Veeam Backup & Replication console** using the Windows task bar.
11. [] Click the **Restore** button on the **Home** ribbon.
12. [] Select **VMware vSphere...**.
13. [] Keep the default setting and click the **Next** button on the **Restore Options** step.
14. [] Click the **Add VM** button.
15. [] Select **From backup...**.
16. [] Expand the **Backup ORCL** job.
17. [] Select **Tiny-Veeam**.
18. [] Click the **Add** button.

14. [] Click the **Next** button on the **Virtual Machines** step.
16. [] Tick the **Quick rollback (restore changed block only)** check box.
> Note: That means that the VMware CBT technology will be leveraged to enable incremental restore.
> In the previous scenario, we assumed that the hard drives of the VM were lost because of a hardware or a storage issue. In this one, we will assume that the VM to be restored has a software problem itself – so the incremental restore option (quick rollback) will be used.
> Instead of restoring an entire VM or VM disk from a backup file, Veeam Backup & Replication recovers only those data blocks that are necessary to revert the VM or VM disk to an earlier point in time. Incremental restore significantly reduces the recovery time and has little impact on the production environment.

17. [] Click the **Next** button on the **Restore Mode** step.
18. [] Leave the **reason** empty and click the **Next** button on the **Reason** step.
19. [] Click the **Show VM(s)** text link to verify it is only **Tiny-Veeam** that will be powered off during the restore.
20. [] Click the **OK** button.
21. [] Click the **OK** button to confirm the original virtual machine will be deleted from the infrastructure.
22. [] Tick the **Power on target VM after restoring** check box.
23. [] Click the **Finish** button on the **Summary** step.
24. [] Wait for the log to display **Restore completed successfully** then click the **Close** button.
> Note: To use incremental restore, make sure that the following requirements are met:
>
>- The VM or VM disk is restored to its original location.
> - CBT is enabled for the VM disk or all disks of a VM you plan to restore.
> - The backup file from which you plan to restore a VM or a VM disk is created with the Use Changed Block Tracking option enabled.

25. [] Switch back to the **VMware vSphere Client** using the Windows task bar.
26. [] Review the **Recent Tasks** pane to better understand the restore process then minimize the **VMware vSphere Client** window.

===

# Lab 5.3: Using extract utility

1. [] Launch the **File Explorer** from the Windows task bar.
2. [] Navigate to the +++C:\Program Files\Veeam\Backup and Replication\Backup+++ folder.
3. [] Launch the **Veeam.Backup.Extractor.exe** file.
> Note: If you plan to start the extract utility on a machine other than the Veeam backup server, make sure that you copy the Veeam.Backup.Extractor.exe file together with the extract.exe file from the %PROGRAMFILES%\Veeam\Backup and Replication\Backup folder and store these files to the same folder on the destination machine. Otherwise, the extract utility will fail to start.

4. [] Click the **Browse...** button in the **VBK file** section.
5. [] Enter file name: +++X:\Backup\Backup_ORCL+++
6. [] Click the **Open** button.
7. [] Select the **Tiny-Veeam** VBK full backup file.
8. [] Click the **Open** button.

9. [] Click the **Browse...** button in the **Extract folder** section.
10. [] Expand **Computer**.
11. [] Expand the **Local Drive (X:)** drive.
12. [] Select the **VMs** folder.
13. [] Click the **OK** button.
14. [] Tick the **Tiny-Veeam** check box.
15. [] Click the **Extract** button.
> Note: Note: The VM files will be extracted to the specified folder.

16. [] Click the **OK** button.
17. [] Close the **Veeam Extract Utility** window.
18. [] Close the **File Explorer** window.

===

# Lab 5.4: Bringing a replica back

## Step 1: Perform a failover to the replicated VM

1. [] Switch back to the  **VMware vSphere Client** using the Windows task bar.
6. [] Select **Tiny-Veeam**.
7. [] Click the **Power off** button in the **Commands** pane.
8. [] Click the **Yes** button to confirm powering off the virtual machine.
9. [] Minimize the **VMware vSphere Client**.
10. [] Expand **Replicas** in the **Home** view.
11. [] Select **Ready**.
12. [] Select **Tiny-Veeam**.
13. [] Click the **Failover Now** button on the **Replica** ribbon.
14. [] Keep the default settings and click the **Next** button on the **Virtual Machines** step.
15. [] Keep the default settings and click the **Next** button on the **Reason** step.
16. [] Click the **Finish** button on the **Summary** step.
17. [] Watch the failover process until the log displays the **Failover completed successfully** text then click the **Close** button.
18. [] Switch back to the **VMware vSphere Client** using the Windows task bar.
19. [] Expand the **Replicas** resource pool.
20. [] Select the **Tiny-Veeam_replica** virtual machine.
21. [] Review the configuration of the **Tiny-Veeam_replica** virtual machine then minimize the **VMware vSphere Client**.

===

## Step 2: Undo Failover

1. [] Select **Active (1)** under **Replicas** in the **Home** view.
2. [] Select **Tiny-Veeam**.
3. [] Click the **Undo Failover** button on the **Replica** ribbon.
4. [] Click the **Yes** button to confirm you are aware that undo failover resets the replica VM to the latest state.
5. [] Click the **Close** button.
6. [] Switch back to the **VMware vSphere Client** using the Windows task bar.
7. [] Wait until the **Tiny-Veeam_replica** virtual machine is powered off.
> Note: Tiny-Veeam_replica is automatically powered off as a part of the undo failover process.

7. [] Select the **Tiny-Veeam** virtual machine in the **Production** resource pool.
8. [] Click the **Power On** button in the **Commands** pane.
9. [] Minimize the **VMware vSphere Client** window.

===

## Step 3: Failover a replicated VM again

1. [] Launch the **Hyper-V Manager** from the Windows task bar.
2. [] Select **Tiny-Veeam2**.
3. [] Click the **Turn Off** text link in the **Actions** pane.
4. [] Click the **Turn Off** button to confirm turning off the **Tiny-Veeam2** virtual machine.
5. [] Minimize the **Hyper-V Manager** window.
6. [] Select **Tiny-Veeam2**.
7. [] Click the **Failover Now** button on the **Replica** ribbon.
8. [] Keep the default settings and click the **Next** button on the **Virtual Machines** step.
9. [] Keep the default settings and click the **Next** button on the **Reason** step.
10. [] Click the **Finish** button on the **Summary** step.
11. [] Click the **Close** button.

===

## Step 4: Failback a VM

1. [] Verify the **Tiny-Veeam2** virtual machine is still selected then click the **Failback to Production** button on the **Replica** ribbon.
2. [] Keep the default setting and click the **Next** button on the **Replicas** step.
3. [] Keep the default settings and click the **Next** button on the **Destination** step.
4. [] Tick the **Power on target VM after restoring** check box.
5. [] Click the **Finish** button on the **Summary** step.
6. [] Watch the failback process until the log displays the **Failback completed** text then click the **Close** button.

===

## Step 5: Commit failback

1. [] Verify the **Tiny-Veeam2** virtual machine is still selected then click the **Commit Failback** button on the **Replica** ribbon.
> Note: When you commit failback, you confirm that you want to get back to the production VM. Veeam Backup & Replication resumes replication activities for the VM to which you failed back.

2. [] Click the **Yes** button to confirm the commit failback.
> Note: Make sure to observe what’s happening in the Hyper-V Manager as well. The failback protective snapshot that saves the pre-failback state of a VM replica is not deleted – Veeam Backup & Replication uses this snapshot as an additional restore point for the VM replica. With the pre-failback snapshot, Veeam Backup & Replication needs to transfer fewer changes and, therefore, puts less load on the network when replication activities are resumed

3. [] Watch the failback process until the log displays the **Failback commit operation stopped** text then click the **Close** button.
4. [] Switch to the **Hyper-V Manager** window using the Windows task bar.
5. [] Review the current state of the **Tiny-Veeam2** virtual machine then close the **Hyper-V Manager** window.

===

# Lab 5.5: Failover Plan

## Step 1: Create a failover plan

1. [] Click the **Home** ribbon.
2. [] Click the **Failover Plan** button.
3. [] Select **VMware vSphere...**.
4. [] Enter:
 1. Name: +++Failover plan+++
 2. Description: +++Tiny-Veeam and VEEAM-DC01+++

5. [] Click the **Next** button on the **General** step.
6. [] Click the **Add VM** button.
7. [] Select **From infrastructure...**.
8. [] Expand the **VEEAM-ESX** host.
9. [] Expand the **Production** resource pool.
10. [] Hold the **CTRL** button and select the **VEEAM-DC01** and **Tiny-Veeam** virtual machines.
11. [] Click the **Add** button.
12. [] Select **Tiny-Veeam**.
13. [] Click the **Set Delay...** button.
14. [] Lower the **boot delay** to: +++30+++ seconds.
15. [] Click the **OK** button.
16. [] Select **VEEAM-DC01**.
17. [] Click the **Set Delay...** button.
18. [] Increase the **boot delay** to: +++120+++ seconds.
> Note: Since VEEAM-DC01 is the last virtual machine in the failover plan, this change will only have an effect if additional virtual machines are added in the future.

19. [] Click the **OK** button.
20. [] Click the **Apply** button on the **Virtual Machines** step.
21. [] Click the **Finish** button on the **Summary** step.

=== 

## Step 2: Perform failover by failover plan

1. [] Switch back to the **VMware vSphere Client** using the Windows task bar.
2. [] Select **VEEAM-DC01**
3. [] Select the **Shut Down Guest** text link in the **Commands** pane.
4. [] Click the **Yes** button to confirm shut down of the guest operating system.
5. [] Select **Tiny-Veeam**.
6. [] Select the **Power Off** text link in the **Commands** pane.
7. [] Click the **Yes** button to confirm powering off the virtual machine.
8. [] Minimize the **VMware vSphere Client** window.
9. [] Select **Failover Plans** in the **Replicas** section of the **Home** view.
10. [] Select the **Failover plan** failover plan.
11. [] Click the **Start** button on the **Failover Plan** ribbon.
12. [] Watch the failover process until the log displays the **Failover plan executed** text then click the **Close** button.

===

## Step 3: Undo a failover by the failover plan

1. [] Click the **Undo** button on the **Failover Plan** ribbon.
2. [] Click the **Yes** button to confirm that undo failover plan will reset all replica VMs in the plan to the latest state.
3. [] Click the **Close** button.
4. [] Switch back to the **VMware vSphere Client** window using the Windows task bar.
5. [] Wait until both the **Tiny-Veeam_replica** and **VEEAM-DC01_replica** virtual machines have been powered off then click the **Power On** text link in the **Commands** pane.
6. [] Select **VEEAM-DC01**.
7. [] Click the **Power On** text link in the **Commands** pane.
> Note: Please verify that both the Tiny-Veeam and VEEAM-DC01 virtual machines are in a powered on state before continuing.

8. [] Close the **VMware vSphere Client** window.
> Note: Undo of a failover plan has been completed.

===

# Lab 5.6: Perform planned failover

1. [] Select **Tiny-Veeam2**.
2. [] Click the **Planned Failover** button on the **Replica** ribbon.
3. [] Click the **Next** button on the **Virtual Machines** step.
4. [] Keep the default settings and click the **Next** button on the **Reason** step.
5. [] Click the **Finish** button on the **Summary** step.
> Note: When you start the planned failover, Veeam Backup & Replication performs the following steps:
>
> 1. The failover process triggers the replication job to perform an incremental backup and copy the un-replicated changes to the replica.
> 2. The VM is powered off.
> 3. The failover process triggers the replication job to perform another incremental backup run and copy a portion of the lastminute changes to the replica. The replica becomes fully synchronized with the source VM.
> 4. The VM is failed over to its replica.

5. [] Watch the planned failover process until the log displays the **Failover completed successfully** text then click the **Close** button. This process may take up to 10 minutes, please have some patience. While waiting, you can navigate to the **Running** section of the **Home** view to better observe the process.

6. [] After the failover completes successfully, go to the **Active** section of the **Home** view.
7. [] Select **Tiny-Veeam2**.
8. [] Click the **Permanent Failover** button on the **Replica** ribbon.
9. [] Click the **Yes** button.
10. [] Watch the permanent failover process until the log displays the **Permanent failover is completed** text then click the **Close** button.

---

# Congratulations!

You have completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
