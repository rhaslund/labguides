Module 9: Advanced Data Protection

---
**This lab is expected to last a maximum of 150 minutes including lab launch**.

# Lab 9.1: Working with SAN storage snapshots

## Step 1: Add HPE StoreVirtual VSA

1. [] Launch the **Veeam Backup & Replication console** from the desktop.
2. [] Click the **Connect** button.

1. [] Navigate to the **Storage Infrastructure** view.
2. [] Click the **Add Storage** button.
3. [] Select **Hewlett Packard Enterprise**.
4. [] Select **StoreVirtual**.
5. [] Enter Management server DNS name: +++VEEAM-VSA+++.
6. [] Click the **Next** button on the **Name** step.
6. [] Click the **Add...** button
7. [] Enter:
 1. Username: +++veeam+++ (case sensitive).
 2. Password: +++veeam+++ (case sensitive).
 3. Description: +++HP VSA admin account+++

8. [] Click the **OK** button.

7. [] Click the **Next** button on the **Credentials** step.
8. [] Click the **Yes** button to confirm trust of the remote storage system. 
> Note: Veeam Backup & Replication saves a fingerprint of the SSH key of the storage system to the Veeam Backup & Replication database. During every subsequent connection to the server, Veeam Backup & Replication uses the saved fingerprint to verify the identity of the storage system and avoid the man-in-the-middle attack.

9. [] Keep the default settings and click the **Next** button on the **Access Options** step.
10. [] Click the **Finish** button on the **Summary** step.
11. []  Wait until the storage discovery reaches status **Success** then click the **Close** button.

===

## Step 2: Create a SAN snapshot

1. [] Expand **HPE StoreVirtual** in the **Storage Infrastructure** view.
3. [] Expand **Veeam-VSA-MGMTG**.
4. [] Select **veeam-vsa-cluster**.
5. [] Select **datastore1**.
6. [] Click the **Create Snapshot** button on the **Volume** ribbon.
7. [] Keep the default settings and click the **OK** button.
8. [] Wait until the create storage snapshot reaches status **Success** then click the **Close** button.
> Note: This progress will take a maximum of 2 minutes.

===

## Step 3: Create an On-Demand Sandbox for snapshots

1. [] Navigate to the **Backup Infrastructure** view.
1. [] Select **SureBackup** in the **Backup Infrastructure** view.
2. [] Click the **Add App Group** button on the **SureBackup** ribbon.
3. [] Select **VMware...**.
3. [] Enter name:  +++SharePoint from snapshot+++.
4. [] Click the **Next** button on the **Name** step.
4. [] Click the **Add VM** button.
5. [] Select **From storage snapshots...**.
6. [] Expand **datastore1 (datastore1)**.
7. [] Hold the **CTRL** keyboard button and select the **VEEAM-DC01** and **VEEAM- SP01** virtual machines.
8. [] Click the **Add** button.
> Important: Verify that the boot order is:
>
> VEEAM-DC01
>
> VEEAM-SP01
>
> If necessary, use the **Move Up** and **Move Down** buttons to change the order.

9. [] Click the **Next** button on the **Virtual Machines** step.
10. [] Click the **Finish** button on the **Summary** step.
11. [] Navigate to the **Home** view.
12. [] Click the **SureBackup Job** button on the **Home** ribbon.

11. [] Select **VMware...**.
12. [] Enter
 1. Name: +++SureBackup Job SharePoint+++ into the **Name** field.
 2. Description: +++VEEAM-SP01+++. 

13. [] Click the **Next** button on the **Name** step..

13. [] Keep the default settings and click the **Next** button on the **Virtual Lab** step.
14. [] Click the **Application group** drop-down menu.
15. [] Select the **SharePoint from snapshot** application group.
> Note:  If the Keep the application group running after the job completes check box is ticked the lab will not be powered off when the SureBackup job completes and you could use On-Demand Sandbox for testing, troubleshooting or training. For VMCE training purposes, however, we will leave the check box unticked.

16. [] Click the **Next** button on the **Application Group** step.
17. [] Click the **Yes** button to ignore the data sovereignty warning.
18. [] Keep the default settings and click the **Next** button on the **Linked Jobs** step.
19. [] Keep the default settings and click the **Next** button on the **Settings** step.
20. [] Keep the default settings and click the **Apply** button on the **Schedule** step.
21. [] Tick the **Run the job when I click Finish** check box.
22. [] Click the **Finish** button on the **Summary** step.
> **Important: Do NOT wait for the SureBackup job to complete - please continue to the next lab exercise immediately.**

===

## Step 4: Restore guest files from a SAN snapshot

1. [] Select **Storage Snapshots** in the **Backups** section of the **Home** view.
2. [] Expand **datastore1 (datastore1)**.
3. [] Select **VEEAM-SP01**.
4. [] Click the **Guest Files** button on the **Backup** ribbon.
5. [] Select **Microsoft Windows**.
6. [] Keep the default settings and click the **Next** button on the **Restore Point** step.
7. [] Click the **Customize** text link.
8. [] Click the **Choose...** in the **Host** section.
9. [] Select the **VEEAM-ESX** host.
10. [] Click the **OK** button to confirm the host.
11. [] Click the **Choose...** button in the **Resource pool** section.
12. [] Expand the **VEEAM-ESX** host.
13. [] Select the **Production** resource pool.
14. [] Click the **OK** button to confirm the resource pool.
15. [] Click the **OK** button.
16. [] Click the **Next** button on the **Location** step.
17. [] Keep the default settings and click the **Next** button on the **Restore Reason** step.
18. [] Click the **Finish** button on the **Summary** step.
> Note: The Backup Browser will launch after a short wait, please have some patience.

19. [] Expand the **(C:)** drive.
20. [] Expand the **inetpub** folder.

20. [] Select the **wwwroot** folder in the **Navigation** pane.
21. [] Select the **iis-8.png** file.
22. [] Click the **Restore** button on the **File** ribbon.
23. [] Select **Keep**.
24. [] Click the **Credentials** drop down menu.
25. [] Select **VEEAMLAB\\Administrator**.
26. [] Click the **OK** button.
27. [] Wait for the restore to display the **Restore completed successfully** text then click the **Close** button.
28. [] Close the **Backup Browser** window.
28. [] Launch the **File Explorer** from the Windows task bar.
29. [] Navigate to the +++\\\\veeam-sp01\\c$\\inetpub\\wwwroot+++ folder.
30. [] Verify both the **iis-8.png** and **RESTORED-iis-8.png** files are present then close the **File Explorer** window.
> Important It is not possible to browse to this path, you need to click the address bar inside the File Explorer and then manually input the path and finally press the Enter button.

===

## Step 5: Backup from Storage Snapshots

1. [] Select **Backup** in the **Jobs** section of the **Home** view.
2. [] Select the **Backup ORCL** job.
3. [] Click the **Edit** button on the **Job** ribbon.
4. [] Click the **Storage** text link in the left hand step list.
5. [] Click the **Advanced** button.
6. [] Click the **Integration** tab.
7. [] Untick the **Enable backup from storage snapshots** check box.
8. [] Click the **OK** button.
9. [] Click the **Finish** button on the **Storage** step.
10. [] Click the **Active Full** button on the **Job** ribbon.
11. [] Click the **Yes** button to confirm running the Active Full backup now.
12. [] Launch the **VMware vSphere Client** from the Windows task bar.
13. [] Enter:
 1. User name: +++root+++.
 2. Password: +++Pa$$w0rd+++.
 
14. [] Click the **Login** button.

12. [] In the **Recent Task** pane, locate the **Create vitual machine snapshot** text for the **Tiny-Veeam** virtual machine and note down the **Start Time** then locate the **Remove snapshot** text for the **Tiny-Veeam** virtual machine. Compare the two time stamps and calculate the time difference. Minimize the **VMware vSphere Client**.
> Note:  We choose to launch active full here since Veeam Backup & Replication retrieves data for the whole VM from the source, so backup will take a bit longer, and the difference in time it takes to release the VM snapshot will be more noticeable. 

14. [] Wait for the job **Status** to reach **Stopped** then click the **Edit** button on the **Job** ribbon.
> Important: It will take a maximum of 6 minutes to complete this active full backup.

15. [] Click the **Storage** text link in the left hand step list.
16. [] Click the **Advanced** button.
17. [] Click the **Integration** tab.
18. [] Tick the **Enable backup from storage snapshots** check box.
19. [] Click the **OK** button.
20. [] Click the **Finish** button on the **Storage** step.
21. [] Click the **Active Full** button on the **Job** ribbon.
22. [] Click the **Yes** button to confirm running the Active Full backup now.
23. [] Switch to the **VMware vSphere Client** using the Windows task bar.
25. [] In the **Recent Task** pane, locate the **Create vitual machine snapshot** text for the **Tiny-Veeam** virtual machine and note down the **Start Time** then locate the **Remove snapshot** text for the **Tiny-Veeam** virtual machine. Compare the two time stamps and calculate the time difference, then compare with the result from the active full without storage snapshots enabled. Close the **VMware vSphere Client** window.
> Note: The snapshot is open longer time in this example with backup from storage snapshots enabled. This is because it takes time to orchestrate the storage snapshot and there is no data changes in the virtual machine during the backup. Generally, it makes the most sense to enable backup from storage snapshots for highly transactional servers.

===

# Lab 9.2. Using backup to tape

## Step 1: Add a tape server

1. [] Open **Veeam Backup & Replication**.
2. [] Navigate to the **Tape Infrastructure** view.
3. [] There are no Tape Drives or Libraries available yet. In the lab environment, the tape library is connected to the **VEEAM-Remote** server. Click the **Add Tape Server** button on the **Tape** ribbon.
4. [] Click the **Choose server:** drop down menu.
5. [] Select **VEEAM-Remote**.
6. [] Click the **Next** button on the **Server** step.
7. [] Keep the default settings and click the **Next** button on the **Traffic** step.
8. [] Click the **Apply** button on the **Review** step.
9. [] Click the **Next** button on the **Apply** step.
10. [] Click the **Finish** button on the **Summary** step.

===

## Step 2: Add new devices

1. [] Expand **Libraries** in the **Tape Infrastructure** view.
2. [] Expand **HP MSL G3 Series 1068**.
3. [] Select **Drives**.
> Note: There are currently no tape drives available due to missing drivers on the **VEEAM-Remote** server.

3. [] Launch the **Remote Desktop Connection client** from the Windows task bar.
3. [] Enter computer: +++VEEAM-Remote+++.
4. [] Enter password: +++Pa$$w0rd+++.
5. [] Click the **OK** button.
6. [] Click the **Yes** button to dismiss the certificate warning.
5. [] Click the **Start** menu (move the mouse cursor all the way to the edge of the bottom left hand corner to make the start menu button appear).
6. [] Enter: +++devmgmt.msc+++ and press the **Enter** keyboard button.
7. [] Expand **Medium Changer devices**.
8. [] Double click the **Unknown Medium Changer** device.
9. [] Click the **Driver** tab.
10. [] Click the **Update driver...** button.
11. [] Select **Browse my computer for driver software**.
12. [] Enter path +++C:\install\HP Tape Drivers+++
13. [] Click the **Next** button.

13. [] Click the **Close** button.
14. [] Verify the driver has been installed then click the **Close** button.
15. [] Expand **Other devices**.
16. [] Right click the first **HP Ultrium 5-SCSI SCSI Sequential** device.
17. [] Select **Update driver software...**.
18. [] Select **Browse my computer for driver software**.
19. [] Keep the default path and click the **Next** button.
20. [] Click the **Close** button.
21. [] Right click the remaining **HP Ultrium 5-SCSI SCSI Sequential** device.
22. [] Select **Update Driver Software...**.
23. [] Select **Browse my computer for driver software**.
24. [] Keep the default path and click the **Next** button.
25. [] Click the **Close** button.
26. [] Close the **Remote Desktop Connection** window.

===

## Step 3: Add unrecognized tapes to the free media pool

1. [] Verify the two **HP Ultrium 5-SCSI** drives appear then select the **HP MSL G3 Series 1068** tape library in the **Libraries** section of the **Tape Infrastructure** view.
2. [] Click the **Location** button on the **Tape Library** ribbon.
3. [] Select **Local**.
4. [] Select **Media** in the **Libraries** section of the **Home** view.
5. [] Select the first tape then press the **CTRL** \+ **A** to select **all tapes**.
6. [] Click the **Move To** button on the **Media** ribbon.
7. [] Select **Free**.
> Note: In a production environment, if you are unsure if the tapes are completely new and you want to use them as free media, use Erase Tape → Short to place them in **Media Pool** → **Free**.

9. [] Click the **Yes** button to confirm moving the unrecognized tapes to the **Free Media Pool**.
10. [] Verify the **Media Pool** column changes to **Free** for all tapes with the exception of the cleaning tape then navigate to the **Home** view.

===

## Step 4: Create a tape backup job

1. [] Click the **Tape Job** button on the **Home** ribbon.
2. [] Select **Backups...**
3. [] Keep the default settings and click the **Next** button on the **Name** step.
4. [] Click the **Add...** button.
5. [] Select **Backup Jobs...**.
6. [] Select the **Backup ORCL** job.
7. [] Click the **OK** button.
9. [] Click the **Next** button on the **Backup Files** step.
10. [] Click the **Add New...** button.
11. [] Select **Simple media pool**.
12. [] Enter name: +++Media Pool Full+++.
13. [] Click the **Next** button on the **Name** step.
13. [] Click the **Add...** button.
14. [] Select the first seven tapes from the **Free Media Pool**.
15. [] Click the **OK** button.
16. [] Click the **Next** button on the **Tapes** step.
17. [] Select the **Daily at** radio button.
> Note: Media set is a set of tapes used for continuously writing backup data. Media set is one of parameters in media pool configuration.
>
> A new media set always starts with a free tape. Within one media set, the new data block is appended to a previous one on a tape. Veeam Backup & Replication stores information about all tapes that belong to each media set. You can view the list of names or barcodes of tapes that are associated with a particular media set.

18. [] Click the **Daily at** drop down menu (currently set to **Everyday**).
19. [] Select **On these days**.
20. [] Click the **Days...** button.
21. [] Untick the **Tuesday** check box.
22. [] Untick the **Wednesday** check box.
23. [] Untick the **Thursday** check box.
24. [] Untick the **Friday** check box.

22. [] Click the **OK** button.
23. [] Click the **Next** on the **Media Set** step.
24. [] Select the **Protect data for** radio button.
25. [] Increase the weeks to protect data to +++4+++ Weeks.
26. [] Click the **Next** button on the **Retention** step.

26. [] Keep the default settings and click the **Apply** button on the **Options** step.
27. [] Click the **Finish** button on the **Summary** step.
28. [] Verify the media pool for full backups has changed to **Media Pool Full (HP MSL G3 Series 1068)** then click the **Next** button on the **Full Backup** step.
29. [] Verify the media pool for incremental backups is set to **Media Pool Full (HP MSL G3 Series 1068)** then click the **Next** button on the **Incremental Backup** step.
30. [] Keep the default settings and click the **Next** button on the **Options** step.
31. [] Tick the **Run the job automatically** check box.
32. [] Select the **As new backup files appear** radio button.
33. [] Click the **Apply** button on the **Schedule** step.
34. [] Click the **Finish** button on the **Summary** step.
35. [] Select **Tape** in the **Jobs** section of the **Home** view.
36. [] Select the **Backup to Tape Job 1** and confirm the job has started.

===

# Lab 9.3: Configuring Hyper-V backup to run in off-host mode

## Step 1: Install and configure the hardware VSS provider

1. [] HPE LeftHand P4000 VSS Provider is the hardware provider that supports the Volume Shadow Copy Service on the HPE LeftHand Storage Solution. The hardware VSS provider needs to be installed on both the production Hyper-V host and the off-host proxy. In our case, it's already installed on the Hyper-V host, so let's install it on the **VEEAM-VBR** server. Launch **File Explorer** from the Windows task bar.
2. [] Expand **Local Disk (C:)**.
3. [] Select the **Install** folder.
4. [] Launch the **HPE_StoreVirtual_Application_Aware_Snapshot_Manager_Installer_AT004-10545.exe** installer.
5. [] Click the **Next** button.
6. [] Select the **I accept the terms of the license agreement** radio button. 
7. [] Click the **Next** on the **License Agreement** step.
8. [] Click the **Next** button on the **Choose Destination Location** step.
9. [] Click the **Next** button on the **Enter Text** step.
11. [] Click the **Install** button on the **Ready to Install the Program** step.
12. [] Read the notification and click **Next**.
13. [] Click **Finish** to exit the installation wizard.
14. [] Close the **File Explorer** window.
15. [] Click the **Start menu** button (move the mouse cursor to the bottom left edge of the screen to make the start menu button appear).
16. [] Launch the **Authentication Console**.

16. [] Click the **OK** button to dismiss the notification about credentials.
18. [] Click the **New Management Group Credentials** text link in the **Actions** pane.
> **Important!** The management group name is **Case Sensitive**.

19. [] Enter:
 1. Management group: +++Veeam-VSA-MGMTG+++
 2. User name: +++veeam+++.
 2. Password: +++veeam+++.
 3. Confirm password: +++veeam+++.
> Note: Pay attention to the management group name as it is case sensitive. Otherwise, the test will fail.

20. [] Click the **Test** button.

20. [] Enter IP address: +++10.0.2.240+++.
21. [] Click the **OK** button.
21. [] Verify the **Test succeeded. The credentials are valid.** text is displayed then click the **OK** button.
22. [] Close the **Authentication Console** window.
23. [] Navigate to the **Backup Infrastructure** view.
24. [] Select **Microsoft Hyper-V** in the **Managed Servers** section of the **Home** view.
25. [] Select the  **VEEAM-HYPERV** host.
26. [] Click the **Manage Volumes** button on the **Server** ribbon.
27. [] Verify that **G:\\** mount point provider is **LeftHand Networks VSS Provider** then click the **Cancel** button.

===

## Step 2: Add a Hyper-V off-host backup proxy

1. [] Select **Backup Proxies** in the **Backup Infrastructure** view.
2. [] Click the **Add Proxy** button on the **Backup Proxy** ribbon.
3. [] Select **Hyper-V...**.
4. [] Keep the default settings and click the **Next** button on the **Server** step.
> Note: The Hyper-V role must be enabled on the server, otherwise it is not possible to add it as an off-host backup proxy.

5. [] Keep the default settings and click the **Next** button on the **Traffic Rules** step.
6. [] Review the settings then click the **Apply** button on the **Review** step.
7. [] Wait for the required components to be installed and configued then click the **Next** button on the **Apply** step.
> Note: Checking for updates could take up to 4 minutes.

8. [] Click the **Finish** button on the **Summary** step.

===

## Step 3: Edit a Hyper-V backup job and run it in the off-host mode

1. [] Navigate to the **Home** view.
2. [] Select **Backup** in the **Jobs** section of the **Home** view.
3. [] Select the **Backup Tiny-Veeam2** job.
4. [] Click the **Edit** button on the **Job** ribbon.
5. [] Keep the existing settings and click the **Next** button on the **Name** step.
6. [] Select the **Tiny-Veeam2** virtual machine.
> Note:  We are re-adding the VM since it was deleted and restored from a backup previously. The VM uuid has changed, so we have to re-add it onto the job.

7. [] Click the **Remove** button.
8. [] Click the **Add...** button.
9. [] Expand the **VEEAM-HYPERV** host.
10. [] Select **Tiny-Veeam2**.
11. [] Click the **Add** button.
12. [] Click the **Next** button on the **Virtual Machines** step.
13. [] Click the **Choose...** button in the **Backup proxy** section.
14. [] Select the **Off-host backup** radio button.
15. [] Verify the **Hyper-V Off-Host Backup Proxy** is visible in the **Name** column then click the **OK** button.
16. [] Click the **Finish** button on the **Storage** step.
17. [] Click the **Start** button on the **Job** ribbon.
18. [] Select the **Tiny-Veeam2** virtual machine in the **Statistics** view.
19. [] Verify the **Creating snapshot LeftHand Networks VSS Provider on Hyper-V Off-Host Backup Proxy** text is displayed then minimize the **Veeam Backup & Replication console** window.
> Note: The backup job will take a maximum of 2 minutes to complete, but please do not wait for the job to complete before continuing to the next lab exercise.

===

# Lab 9.4. Working with Veeam Backup Enterprise Manager

## Step 1. Review the server's management

1. [] Launch **Veeam Backup Enterprise Manager** from the **desktop**.
2. [] Click the **Configuration** button in the top right corner.

3. [] Click the **Add...** button.
4. [] Click the **Yes** button to dismiss the warning that Veeam Backup Enterprise Manager will push its license to all connected backup servers.
5. [] Enter: 
 1. DNS name: +++VEEAM-VBR2+++ 
 2. User name: +++VEEAMINFRA\Administrator+++ 
 3. Password: +++Pa$$w0rd+++ 

6. [] Click the **OK** button.
7. [] Now, both Veeam backup servers are visible to **Veeam Backup Enterprise Manager**. Data about backup and replication jobs from the SQL databases used by VEEAM-VBR and VEEAM-VBR2 will be collected and stored. Veeam Backup Enterprise Manager enables you to modify the settings of jobs that have been previously configured on managed backup servers. Click the **Home** button in the top left corner.
8. [] Click the **Jobs** tab.
9. [] Select the **Backup Copy Job WAN** job.
> Important: Do **NOT** click the **Backup Copy Job WAN** text link, instead make sure you select the row - for example by clicking right next to the text link.

10. [] Click the **Job** button.
> Important: If the screen resolution is less than 1440 × 900 the Job button will not be visible, please increase your resolution.

11. [] Select **Disable**.
12. [] Wait for the **Backup Copy Job WAN** job status changes to either **Warning** or **Success**. Switch to the **Veeam Backup and Replication console** window using the Windows task bar. 
13. [] Select **Backup Copy** in the **Jobs** section of the **Home** view.
14. [] Verify the **Backup Copy Job WAN** next run is **Disabled** then switch to the **Veeam Backup Enterprise Manager** window using the Windows task bar.

===

## Step 2: Restore guest OS files

1. [] Click the **Configuration** button in the top right corner.
2. [] Select the **veeam-vbr.veeaminfra.local** backup server.
3. [] Click the **Start Collecting** button.
4. [] Click the **OK** button.
> Note: To automatically run catalog replication after every backup job, click **Schedule** on the toolbar. In the displayed window, select Automatic after any backup job finishes and specify other options as necessary. This is actually not required in this specific lab environment since Veeam Backup & Replication and Veeam Backup Enterprise Manager are installed on the same machine and use the same catalog. However, this would be required for performing a file-level restore if Veeam Backup & Replication and Veeam Backup Enterprise Manager were installed on different machines.

5. [] Click the **Home** button in the top left corner.
6. [] Click the **Files** tab.
7. [] Enter machine name: +++VEEAM-DC01+++.
8. [] Press the **ENTER** keyboard button.

8. [] Click the **Search** tab.
9. [] Enter search: +++\*.txt+++.
10. [] Press the **Enter** keyboard button.
10. [] Click the **Advanced search** button.
12. [] Right the **first file**.
13. [] Select **Restore**.
14. [] Select **Overwrite**.
15. [] Click the **Yes** button.
> Note:  The restore session will start, and you can view its progress in the session log.
16. [] Minimize the **Veeam Backup Enterprise Manager** window.

===

## Step 3: Delegate restore privileges

1. [] Launch **Outlook Web Access** from the Windows task bar.
2. [] Enter:
 1. User name +++testmail@veeamlab.local+++ 
 2. Password +++Pa$$w0rd+++ 

3. [] Click the **Sign In** button.
3. [] Click the **Delete** text link to delete the most recent email from the **Inbox** folder.
4. [] Switch to the **Veeam Backup Enterprise Manager** window using the Windows task bar.
5. [] Click the **Configuration** button in the top right corner.
6. [] Navigate to the **Roles** view.
> Note:  To provide for the recoverability of Exchange items, you will need an application-consistent backup (with VSS enabled) of the Exchange server VM. To check corresponding job settings, you can go to the **Jobs** tab in Veeam Backup **Enterprise Manager**, select the backup job that contains the Exchange server and choose to **Edit** it.

7. [] Click the **Add...** button.
8. [] Enter account: +++VEEAMINFRA\restoreoperator+++
9. [] Click the **Role** drop down menu.

9. [] Select **Restore Operator**.
10. [] Tick the **Microsoft Exchange items** check box.
11. [] Click the **OK** button.
12. [] Navigate to the **Settings** view.
13. [] Enter:
 1. Username: +++VEEAMLAB\Administrator+++.
 2. Password: +++Pa$$w0rd+++.
 
14. [] Click the **Save** button.
> Note:  This user account requires corresponding permissions to access Microsoft Active Directory and the mailbox. It needs Exchange Administrator rights and administrator's rights for all mailboxes. If you miss this step, the later Exchange restore exercise will fail.

14. [] Click the **Sign out** text link in the top right corner.
15. [] Enter:
 1. User name: +++VEEAMINFRA\restoreoperator+++.
 2. Password +++Pa$$w0rd+++
 
16. [] Click the **Login** button.

16. [] Enter username: +++testmail+++
17. [] Press the **Enter** keyboard button.

17. [] Select the **testmail** user.
18. [] Tick the **Mail** check box.
19. [] Click the **Restore** button.
> Note:  Restore to another domain is supported within the same forest only.

20. [] Wait until **Status** reaches **Success** then click the **Sign out** text link in the top right corner.
21. [] Switch to the **Outlook Web Access** window using the Windows task bar.
22. [] Verify that the previously deleted item has been restored and close the **Outlook Web Access** window.

===

## Step 4: Manage public keys and encryption keys

1. [] In the **Veeam Backup Enterprise Manager** window, enter:
 1. User name: +++VEEAMINFRA\\Administrator+++.
 2. Password: +++Pa$$w0rd+++.

2. [] Click the **Login** button.
2. [] Click the **Configuration** button in the top right corner.
3. [] Navigate to the **Key Management** view.
4. [] Click the **Generate...** button.
> Note: For security, it is recommended to periodically generate new Veeam Backup Enterprise Manager keys that should be used in the encryption process.

5. [] Leave the **Hint** empty and click the **Generate** button.
> Note: Veeam Backup Enterprise Manager keys are created in the inactive state. To make the keys active and use them for encryption and decryption, you need to activate the keys.

6. [] Select the **first keyset**.
7. [] Click the **Activate** button.
8. [] Tick the **Key retention period** check box.
9. [] Tick the **Auto-generate new keys** check box.
> Note: After the current keyset expires, **Veeam Backup Enterprise Manager** will automatically generate a new keyset and mark it as active.

10. [] Click the **Save** button.
> Important: It is important to regularly back up your Veeam Backup Enterprise Manager keys or save their copies in a safe place.

11. [] Click the **Export** button.
12. [] Click the **Save** button on the yellow bar in the bottom of the **Internet Explorer** window.
12. [] Click the **X** button on the yellow bar in the bottom of the **Internet Explorer** window.

===

## Step 5: Decrypt data without a password

1. [] Launch the **Remote Desktop Connection client** from the Windows task bar.
2. [] Enter computer: +++VEEAM-VBR2+++.
3. [] Click the **Connect** button.

2. [] Enter password: +++Pa$$w0rd+++.
3. [] Click the **OK** button.
4. [] Click the **Yes** button to dismiss the certificate warning.

3. [] Launch the **Veeam Backup & Replication console** from the desktop.
4. [] Click the **Connect** button.
5. [] Click the **Apply** button on the **Servers** step.
6. [] Click the **Finish** button on the **Update** step.

5. [] Select **Backup Repositories** in the **Backup Infrastructure** view.
6. [] Click the **Add Repository** button on the **Backup Repository** ribbon.
7. [] Enter name: +++Remote Repository+++.
8. [] Click the **Next** button on the **Name** step.

9. [] Click **Add new...** button.
10. [] Enter DNs name: +++VEEAM-VBR+++.
11. [] Click the **Next** button on the **Name** step.

11. [] Click the **Add...** button.
12. [] Enter:
 1. Username: +++VEEAMINFRA\Administrator+++.
 2. Password: +++Pa$$w0rd+++.
 
13. [] Click the **OK** button.
13. [] Click the **Next** button on the **Credentials** step.
14. [] Click the **Apply** button on the **Review** step.
15. [] Click the **Next** button on the **Apply** step.
16. [] Click the **Finish** button on the **Summary** step.
17. [] Verify that the repository server is set to VEEAM-VBR then click the **Next** button on the **Server** step.
18. [] Enter path to folder: +++X:\Backup+++.
23. [] Click the **Next** button on the **Repository** step
24. [] Untick the **Enable vPower NFS service on the mount server**
> Note: In a production environment it usually not be recommended to disable the vPower NFS service on the mount server.

24. [] Click the **Next** button on the **Mount Server** step.
25. [] Click the **Apply** button on the **Review** step.
26. [] Click the **Finish** button on the **Apply** step.
27. [] Click the **No** button to keep the current configuration backup location.
42. [] Click the **Rescan** button on the **Backup Repository** ribbon.
> Note: This process will take a maximum of 3 minutes.

43. [] Click the **Close** button.
44. [] Navigate to the **Home** view.
45. [] Select **Disk (encrypted)** in the **Backups** section of the **Home** view.
46. [] Select **Backup Tiny-Veeam2**.
47. [] Click the **Specify password** button on the **Encrypted Backup** ribbon.
48. [] Click the **I have lost the password** text link.
49. [] Click the **Copy to clipboard** button.
50. [] Click the **Next** button on the **Request** step.
> Note: At this step, the copied request will be sent by email or passed in another way to the Veeam Backup Enterprise Manager administrator. For our lab purposes, we will just keep it copied in the clipboard.

51. [] Minimize the **Remote Desktop Connection** window.
52. [] Click the **Configuration** button in the top right corner.
53. [] Navigate to the **Key Management** view.
54. [] Click the **Password Recovery...** button.
55. [] Press the **CTRL + V** keyboard buttons together to paste the request.
56. [] Click the **Next** button on the **Challenge Request** step.
57. [] Verify the **Request verified successfully** text is displayed then click the **Next** button on the **Verify request** step.
58. [] Press the **CTRL + C** keyboard buttons together to copy the response.

58. [] Switch back to the **Remote Desktop Connection client** window.
59. [] Click the **Next** button on the **Request** step.

59. [] Press the **CTRL + V** keyboard buttons together to paste the request.
60. [] Click the **Next** button on the **Response** step.
> Note: Wait for the backup to be decrypted using the Veeam Backup Enterprise Manager key sets. This will take a maximum of 2 minutes.

61. [] Click the **Finish** button on the **Summary** step.
63. [] Close the **Remote Desktop Connection client** window.
64. [] Close the **Veeam Backup Enterprise Manager** window.
65. [] Click the **Finish** button on the **Response** step of the **Password Recovery** wizard in the **Veeam Backup Enterprise Manager**.
66. [] Close the **Veeam Backup Enterprise Manager** window.

===

# Lab 9.5: Veeam configuration backup and restore

## Step 1: Schedule configuration backups

1. [] Click the **≡** button in the top left corner in **Veeam Backup and Replication**.
2. [] Select **Configuration Backup**.
3. [] Tick the **Enable configuration backup to the following repository** check box.
4. [] Tick the **Encrypt configuration backup** check box.
5. [] Click the **Password** drop down menu.

5. [] Select **Technical course that provides extensive information on Veeam solutions**.
6. [] Click the **Backup now** button.
7. [] Wait for the configuration backup to complete then click the **OK** button.
8. [] Select the **Backup ORCL** job then press the **CTRL+A** keyboard buttons to select all jobs.
9. [] Click the **Disable** button on the **Job** ribbon.
> Important:  Do NOT proceed until the job status is Stopped for all jobs.

===

## Step 2: Restoring a configuration backup to another Veeam server

1. [] Launch the **Remote Desktop Connection client** using the Windows task bar.
1. [] Keep computer as +++VEEAM-VBR+++ and click the **Connect** button.
2. [] Enter password: +++Pa$$w0rd+++
3. [] Click the **Connect** button.
4. [] Click the **Yes** button to ignore the certificate warning.
4. [] Click the **≡** button in the top left corner in **Veeam Backup and Replication**.
5. [] Select **Configuration Backup**.
6. [] Click the **Restore...** button.
7. [] Select the **Migrate** radio button.
8. [] Click the **Next** on the **Restore Mode** step.
9. [] Click the **Browse...** button.
10. [] Enter file name: +++X:\\Backups\\VeeamConfigBackup\\VEEAM-VBR+++.
11. [] Click the **Open** button.
11. [] Select the **VEEAM-VBR** configuration backup file.
> Note: The configuration backup file is named in the following way: ServerName\_YYYY-MM- DD\_HH-MM-SS.bco

12. [] Click the **Open** button.
13. [] Click **Analyze**. button on the **Configuration Backup** step.
14. [] Review the backup contents and click the **Next** button.
15. [] Enter **Password**: +++vmce+++.
16. [] Click the **Validate** button.

16. [] Click the **Connect** button on the **Target Database** step.
17. [] Click the **Yes** button to confirm that the current configuration database will be lost.
18. [] Click the **Restore** button on the **Restore Options** step.
19. [] Click the **Yes** button to confirm closing the **Veeam Backup and Replication Console**.
> Note: Because some jobs are not scheduled, they could not be disabled, which will cause a warning.

20. [] Click the **Yes** button to perform a full configuration restore.
21. [] Wait for the restore process to complete then click the **Next** button on the **Restore** step.
22. [] Click the **Start** button on the **Credentials** step.
> Note:  Because the Configuration Backup is encrypted, both usernames and passwords are included. If the Configuration Backup is not encrypted, you would have to enter all the passwords here.

23. [] Untick the **Launch the Backup & Replication user interface** check box.
24. [] Click the **Finish** button on the **Summary** step.
25. [] Close the Remote Desktop Connection to **VEEAM-VBR2**.

===

# Lab 9.6: Introducing the Veeam PowerShell snap-in

1. [] Click the **≡** button in the top left corner in **Veeam Backup and Replication**.
2. [] Select **Console**.
3. [] Select **PowerShell**.
4. [] Enter: +++Get-VBRCommand+++
5. [] Press the **Enter** keyboard button.
> Note: This will output a full list of all Veeam Backup & Replication cmdlets.

6. [] Enter: +++Get-VBRJob+++
7. [] Press the **Enter** keyboard button.
> Note: This will output a list of all backup, replication and copy jobs configured.

8. [] Working in PowerShell is like working at a conveyor belt. Let's apply a parameter - the name of the job to the output of the previous command. Enter: +++Get-VBRJob -name "Backup Tiny-Veeam2"+++.
9. [] Press the **Enter** keyboard button.
> Note: Only information about the **Backup Tiny-Veeam2** job was returned by running this command.

10. [] Now, we can perform some actions with it. Let's launch this job. Enter: +++Get-VBRJob -name "Backup Tiny-Veeam2" | Start-VBRJob+++.
11. [] Press the **Enter** keyboard button.
> Note: The job progress is displayed at the top of the window.

12. [] Minimize the **PowerShell** window.

13. [] Verify the **Backup Tiny-Veeam2** job has started.

> **Note:**  If you want to configure a specific PowerShell script to be run as a post-job activity, you can create a .ps1 file out of it and type the following in job settings (**Storage** tab → **Advanced** → **Script** → **Post job activity**): C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\powershell.exe -Noninteractive -File "\[PathToScript\]\\\[scriptname\].ps1"
>
> **Note:** If you want to configure a specific PowerShell script to be run as a post-job activity, you can create a .ps1 file out of it and type the following in job settings (**Storage** tab → **Advanced** → **Script** → **Post job activity**): C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\powershell.exe -Noninteractive -File "\[PathToScript\]\\\[scriptname\].ps1"
>
> **Note:** If you want to configure a specific PowerShell script to be run as a task in the Windows Scheduler, you would also want to save this kind of script as a .ps1 file (e.g., the content of the file can be the following): Add-PSSnapin VeeamPSSnapin Get-VBRJob --name "Backup Tiny-Veeam2" | Start- VBRJob --FullBackup And then to set up a new task created via Windows Scheduler to run: PowerShell -file "\[PathToScript\]\\\[scriptname\].ps1"

---

# Congratulations!

You have successfully completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
