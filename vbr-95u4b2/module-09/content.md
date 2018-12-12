Module 9: Advanced Data Protection

---
**This lab is expected to last a maximum of 150 minutes including lab launch**.

# Lab 9.1: Working with SAN storage snapshots

## Step 1: Add HPE StoreVirtual VSA

1. [] Launch the **Veeam Backup & Replication console** from the desktop.
2. [] Click the **Connect** button.
3. [] Navigate to the **Storage Infrastructure** view.
4. [] Click the **Add Storage** button.
5. [] Select **Hewlett Packard Enterprise**.
6. [] Select **StoreVirtual**.
7. [] Enter Management server DNS name: +++VEEAM-VSA+++.
8. [] Click the **Next** button on the **Name** step.
9. [] Click the **Add...** button
10. [] Enter:
 1. Username: +++veeam+++ (case sensitive).
 2. Password: +++veeam+++ (case sensitive).
 3. Description: +++HPE VSA admin account+++

11. [] Click the **OK** button.
12. [] Click the **Next** button on the **Credentials** step.
13. [] Click the **Yes** button to confirm trust of the remote storage system. 
> Note: Veeam Backup & Replication saves a fingerprint of the SSH key of the storage system to the Veeam Backup & Replication database. During every subsequent connection to the server, Veeam Backup & Replication uses the saved fingerprint to verify the identity of the storage system and avoid the man-in-the-middle attack.

14. [] Keep the default settings and click the **Next** button on the **Access Options** step.
15. [] Click the **Finish** button on the **Summary** step.
16. []  Wait until the storage discovery reaches status **Success** then click the **Close** button.

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
2. [] Select **SureBackup** in the **Backup Infrastructure** view.
3. [] Click the **Add App Group** button on the **SureBackup** ribbon.
4. [] Select **VMware...**.
5. [] Enter name:  +++SharePoint from storage snapshot+++.
6. [] Click the **Next** button on the **Name** step.
7. [] Click the **Add VM** button.
8. [] Select **From storage snapshots...**.
9. [] Expand **datastore1 (datastore1)**.
10. [] Hold the **CTRL** keyboard button and select the **VEEAM-DC01** and **VEEAM-SP01** virtual machines.
11. [] Click the **Add** button.
12. [] Select **VEEAM-DC01**.
13. [] Click the **Move Up** button.
14. [] Click the **Next** button on the **Virtual Machines** step.
15. [] Click the **Finish** button on the **Summary** step.
16. [] Navigate to the **Home** view.
17. [] Click the **SureBackup Job** button on the **Home** ribbon.
18. [] Select **VMware...**.
19. [] Enter
 1. Name: +++On-Demand Sandbox SharePoint+++ into the **Name** field.
 2. Description: +++VEEAM-SP01+++. 

20. [] Click the **Next** button on the **Name** step..
11. [] Keep the default settings and click the **Next** button on the **Virtual Lab** step.
22. [] Click the **Application group** drop-down menu.
23. [] Select the **SharePoint from storage snapshot** application group.
24. [] Tick the **Keep the application group running after the job completes** check box.
> Note:  If the Keep the application group running after the job completes check box is ticked the lab will not be powered off when the SureBackup job completes and you could use On-Demand Sandbox for testing, troubleshooting or training.

25. [] Click the **Next** button on the **Application Group** step.
26. [] Keep the default settings and click the **Next** button on the **Linked Jobs** step.
27. [] Keep the default settings and click the **Next** button on the **Settings** step.
28. [] Tick the **Run the job automatically** check box.
29. [] Select the **Monthly at this time** radio button.

30. [] Click the **Apply** button on the **Schedule** step.
21. [] Tick the **Run the job when I click Finish** check box.
32. [] Click the **Finish** button on the **Summary** step.
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
11. [] Click the **OK** button.
12. [] Click the **Next** button on the **Location** step.
13. [] Click the **Finish** button on the **Summary** step.
> Note: The Backup Browser will launch after a short wait, please have some patience.

14. [] Expand the **(C:)** drive.
15. [] Expand the **inetpub** folder.
16. [] Select the **wwwroot** folder in the **Navigation** pane.
17. [] Select the **iis-8.png** file.
18. [] Click the **Restore** button on the **File** ribbon.
19. [] Select **Keep**.
20. [] Click the **Credentials** drop down menu.
21. [] Select **VEEAMLAB\\Administrator**.
22. [] Click the **OK** button.
23. [] Wait for the restore to display the **Restore completed successfully** text then click the **Close** button.
24. [] Close the **Backup Browser** window.
25. [] Launch the **File Explorer** from the Windows task bar.
26. [] Navigate to the +++\\\\veeam-sp01\\c$\\inetpub\\wwwroot+++ folder.
> Important: It is not possible to browse to this path, you need to click the address bar inside the File Explorer and then manually input the path and finally press the Enter button.

27. [] Verify both the **iis-8.png** and **RESTORED-iis-8.png** files are present then close the **File Explorer** window.

===

## Step 5: Backup from Storage Snapshots

1. [] Select **Backup** in the **Jobs** section of the **Home** view.
2. [] Select the **Backup ORCL** job.
3. [] Click the **Start** button on the **Job** ribbon.
4. [] Select the **VEEAM-ORCL** virtual machine in the **Statistics** pane at the bottom of the screen.
5. [] Wait until the text **Using backup proxy** is displayed and confirm the line ends with **from storage snapshot**.
> **Important: Do NOT wait for this job to complete before continuing until the next lab.

===

# Lab 9.2. Using backup to tape

## Step 1: Add a tape server

1. [] Navigate to the **Tape Infrastructure** view.
2. [] There are no Tape Drives or Libraries available yet. In the lab environment, the tape library is connected to the **VEEAM-Remote** server. Click the **Add Tape Server** button on the **Tape** ribbon.
3. [] Click the **Choose server:** drop down menu.
4. [] Select **VEEAM-Remote**.
5. [] Click the **Next** button on the **Server** step.
6. [] Keep the default settings and click the **Next** button on the **Traffic** step.
7. [] Click the **Apply** button on the **Review** step.
8. [] Click the **Next** button on the **Apply** step.
9. [] Click the **Finish** button on the **Summary** step.

===

## Step 2: Add new devices

1. [] Expand **Libraries** in the **Tape Infrastructure** view.
2. [] Expand **HP MSL G3 Series 1068**.
> **Important: If the HP MSL G3 Series 1068 tape library is missing, ask your instructor for assistance. The VEEAM-REMOTE server needs to be rebooted.**

3. [] Select **Drives**.
> Note: There are currently no tape drives available due to missing drivers on the **VEEAM-Remote** server.

4. [] Launch the **Remote Desktop Connection client** from the Windows task bar.
5. [] Enter computer: +++VEEAM-Remote+++.
6. [] Click the **Connect** button.
7. [] Enter password: +++Pa$$w0rd+++
8. [] Click the **OK** button.
9. [] Click the **Start** menu (move the mouse cursor all the way to the edge of the bottom left hand corner to make the start menu button appear).
10. [] Enter: +++devmgmt.msc+++ and press the **Enter** keyboard button.
11. [] Expand **Medium Changer devices**.
12. [] Double click the **Unknown Medium Changer** device.
13. [] Click the **Driver** tab.
14. [] Click the **Update driver...** button.
15. [] Select **Browse my computer for driver software**.
16. [] Enter path +++C:\install\HP Tape Drivers+++
17. [] Click the **Next** button.
18. [] Click the **Close** button.
19. [] Verify the driver has been installed then click the **Close** button.
20. [] Expand **Other devices**.
21. [] Right click the first **HP Ultrium 5-SCSI SCSI Sequential** device.
22. [] Select **Update Driver Software...**.
23. [] Select **Browse my computer for driver software**.
24. [] Keep the default path and click the **Next** button.
25. [] Click the **Close** button.
26. [] Right click the remaining **HP Ultrium 5-SCSI SCSI Sequential** device.
27. [] Select **Update Driver Software...**.
28. [] Select **Browse my computer for driver software**.
29. [] Keep the default path and click the **Next** button.
30. [] Click the **Close** button.
31. [] Close the **Device Manager** window.
32. [] Close the **Remote Desktop Connection** window.
33. [] Select the **HP MSL G3 Series 1068** tape library.
34. [] Click the **Rescan Library** button on the **Tape Library** ribbon.
35. [] Click the **Close** button.
36. [] Select **Drives** in the **Libraries** section of the **Home** view.

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

8. [] Click the **Yes** button to confirm moving the unrecognized tapes to the **Free Media Pool**.
9. [] Wait for the status to reach **Success** then click the **Close** button.
9. [] Verify the **Media Pool** column changes to **Free** for all tapes with the exception of the cleaning tape then navigate to the **Home** view.

===

## Step 4: Create a tape backup job

1. [] Click the **Tape Job** button on the **Home** ribbon.
2. [] Select **Backups...**
3. [] Keep the default settings and click the **Next** button on the **Name** step.
4. [] Click the **Add...** button.
5. [] Select **Backup Jobs...**.
6. [] Select the **Backup Oracle** job.
7. [] Click the **OK** button.
8. [] Click the **Next** button on the **Backups** step.
9. [] Click the **Add New...** button.
10. [] Select **Simple Media Pool**.
11. [] Enter name: +++Media Pool Full+++.
12. [] Click the **Next** button on the **Name** step.
13. [] Click the **Add...** button.
14. [] Select the first seven tapes from the **Free Media Pool**.
15. [] Click the **OK** button.
16. [] Click the **Next** button on the **Tapes** step.
17. [] Select the **Create new media set for every backup session** radio button.
> Note: Media set is a set of tapes used for continuously writing backup data. Media set is one of parameters in media pool configuration.
>
> A new media set always starts with a free tape. Within one media set, the new data block is appended to a previous one on a tape. Veeam Backup & Replication stores information about all tapes that belong to each media set. You can view the list of names or barcodes of tapes that are associated with a particular media set.

18. [] Click the **Next** button on the **Media Set** step.
19. [] Select the **Protect data for** radio button.
20. [] Increase the weeks to protect data to +++4+++ Weeks.
21. [] Click the **Next** button on the **Retention** step.
22. [] Keep the default settings and click the **Apply** button on the **Options** step.
23. [] Click the **Finish** button on the **Summary** step.
24. [] Verify the media pool for full backups has changed to **Media Pool Full (HP MSL G3 Series 1068)** then click the **Next** button on the **Media Pool** step.
25. [] Verify the media pool for incremental backups is set to **Media Pool Full (HP MSL G3 Series 1068)** then click the **Next** button on the **Incremental Backup** step.
26. [] Keep the default settings and click the **Next** button on the **Options** step.
27. [] Tick the **Run the job automatically** check box.
28. [] Select the **As new backup files appear** radio button.
29. [] Click the **Apply** button on the **Schedule** step.
30. [] Click the **Finish** button on the **Summary** step.
31. [] Select **Tape** in the **Jobs** section of the **Home** view.
32. [] Select the **Backup to Tape Job 1** and confirm the job has started.
> **Important: Do not wait for this job to finish before moving to the next step.**

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
8. [] Keep the default path and click the **Next** button on the **Choose Destination Location** step.
9. [] Keep the default port and click the **Next** button on the **Enter Text** step.
11. [] Click the **Install** button on the **Ready to Install the Program** step.
12. [] Read the notification and click **Next**.
13. [] Click **Finish** to exit the installation wizard.
14. [] Close the **File Explorer** window.
15. [] Click the **Start menu** button (move the mouse cursor to the bottom left edge of the screen to make the start menu button appear).
16. [] Launch the **Authentication Console**.
17. [] Click the **OK** button to dismiss the notification about credentials.
18. [] Click the **New Management Group Credentials** text link in the **Actions** pane.
> **Important!** The management group name is **Case Sensitive**.

19. [] Enter:
 1. Management group: +++Veeam-VSA-MGMTG+++ (case sensitive)
 2. User name: +++veeam+++ (case sensitive)
 2. Password: +++veeam+++ (case sensitive)
 3. Confirm password: +++veeam+++ (case sensitive)
> Note: Pay attention to the management group name as it is case sensitive. Otherwise, the test will fail.

20. [] Click the **Test** button.
21. [] Enter IP address: +++10.0.2.240+++.
22. [] Click the **OK** button.
23. [] Verify the **Test succeeded. The credentials are valid.** text is displayed then click the **OK** button.
24. [] Close the **Authentication Console** window.
25. [] Navigate to the **Backup Infrastructure** view.
26. [] Select **Microsoft Hyper-V** in the **Managed Servers** section of the **Home** view.
27. [] Select the  **VEEAM-HYPERV** host.
28. [] Click the **Manage Volumes** button on the **Server** ribbon.
29. [] Verify that **G:\\** mount point provider is **LeftHand Networks VSS Provider** then click the **Cancel** button.

===

## Step 2: Add a Hyper-V off-host backup proxy

1. [] Select **Backup Proxies** in the **Backup Infrastructure** view.
2. [] Click the **Add Proxy** button on the **Backup Proxy** ribbon.
3. [] Select **Hyper-V...**.
4. [] Keep the default settings and click the **Next** button on the **Server** step.
> Note: The Hyper-V role must be enabled on the server, otherwise it is not possible to add it as an off-host backup proxy.

5. [] Keep the default settings and click the **Next** button on the **Traffic Rules** step.
6. [] Keep the default settings and click the **Apply** button on the **Review** step.
7. [] Wait for the required components to be installed and configued then click the **Next** button on the **Apply** step.
> Note: Checking for updates from Windows Update could take up to 4 minutes.

8. [] Click the **Finish** button on the **Summary** step.

===

## Step 3: Edit a Hyper-V backup job and run it in the off-host mode

1. [] Navigate to the **Home** view.
2. [] Select **Backup** in the **Jobs** section of the **Home** view.
3. [] Select the **Backup Tiny-Veeam2** job.
4. [] Click the **Edit** button on the **Job** ribbon.
5. [] Keep the existing settings and click the **Next** button on the **Name** step.
6. [] Select the **Tiny-Veeam2** virtual machine.
> Note:  We are re-adding the VM because the virtual machine was deleted then restored in a previous lab exercise.

7. [] Click the **Remove** button.
8. [] Click the **Add...** button.
9. [] Expand the **VEEAM-HYPERV** host.
10. [] Select **Tiny-Veeam2**.
11. [] Click the **Add** button.
12. [] Click the **Next** button on the **Virtual Machines** step.
13. [] Click the **Choose...** button in the **Backup proxy** section.
14. [] Verify the **Hyper-V Off-Host Backup Proxy** is visible in the **Name** column then click the **Cancel** button.
15. [] Click the **Finish** button on the **Storage** step.
16. [] Click the **Start** button on the **Job** ribbon.
17. [] Select the **Tiny-Veeam2** virtual machine in the **Statistics** view at the bottom of the screen.
18. [] Verify the **Creating snapshot LeftHand Networks VSS Provider on Hyper-V Off-Host Backup Proxy** text is displayed then minimize the **Veeam Backup & Replication console** window.
> **Important: The backup job will take a maximum of 2 minutes to complete, but please do not wait for the job to complete before continuing to the next lab exercise.**

===

# Lab 9.4. Working with Veeam Backup Enterprise Manager

## Step 1. Review the server's management

1. [] Launch **Veeam Backup Enterprise Manager** from the **desktop**.
2. [] Click the **Configuration** button in the top right corner.
3. [] Click the **Add...** button.
4. [] Enter: 
 1. DNS name: +++VEEAM-VBR2+++ 
 2. User name: +++VEEAMINFRA\Administrator+++ 
 3. Password: +++Pa$$w0rd+++ 

5. [] Click the **OK** button.
> Note: Now, both Veeam backup servers are visible to **Veeam Backup Enterprise Manager**. Data about backup and replication jobs from the SQL databases used by VEEAM-VBR and VEEAM-VBR2 will be collected and stored. Veeam Backup Enterprise Manager enables you to modify the settings of jobs that have been previously configured on managed backup servers.

6. [] Click the **Jobs** tab.
7. [] Select the **Backup Copy Job WAN** job.
> Important: Do **NOT** click the **Backup Copy Job WAN** text link, instead make sure you select the row - for example by clicking right next to the text link.

8. [] Click the **Job** button.
> Important: If the screen resolution is less than 1440 × 900 the Job button will not be visible, please increase your resolution.

9. [] Select **Disable**.
10. [] Wait for the **Backup Copy Job WAN** job status changes to either **Warning** or **Success**. Switch to the **Veeam Backup and Replication console** window using the Windows task bar. 
11. [] Select **Backup Copy** in the **Jobs** section of the **Home** view.
12. [] Verify the **Backup Copy Job WAN** next run is **Disabled** then switch to the **Veeam Backup Enterprise Manager** window using the Windows task bar.

===

## Step 2: Restore guest OS files

1. [] Click the **Configuration** button in the top right corner.
2. [] Select the **veeam-vbr.veeaminfra.local** backup server.
3. [] Click the **Start Collecting** button.
> Note: To automatically run catalog replication after every backup job, click **Schedule** on the toolbar. In the displayed window, select Automatic after any backup job finishes and specify other options as necessary. This is actually not required in this specific lab environment since Veeam Backup & Replication and Veeam Backup Enterprise Manager are installed on the same machine and use the same catalog. However, this would be required for performing a file-level restore if Veeam Backup & Replication and Veeam Backup Enterprise Manager were installed on different machines.

4. [] Click the **Files** tab.
5. [] Enter machine name: +++VEEAM-DC01+++.
6. [] Select the **VEEAM-DC01** virtual machine.
7. [] Click the **Mount** button.
8. [] Enter file name: +++\*.txt+++.
9. [] Click the **Search** button.
10. [] Select the **first file**.
11. [] Click the **Restore** button.
12. [] Select **Overwrite**.
13. [] Click the **Yes** button.
> Note:  The restore session will start, and you can view its progress in the session log.

14. [] Minimize the **Veeam Backup Enterprise Manager** window.

===

## Step 3: Delegate restore privileges

1. [] Launch **Outlook Web Access** from the Windows task bar.
2. [] Enter:
 1. User name +++testmail@veeamlab.local+++ 
 2. Password +++Pa$$w0rd+++ 

3. [] Click the **Sign In** button.
4. [] Click the **Delete** text link to delete the most recent email from the **Inbox** folder.
5. [] Switch to the **Veeam Backup Enterprise Manager** window using the Windows task bar.
6. [] Click the **Configuration** button in the top right corner.
7. [] Navigate to the **Roles** view.
> Note:  To provide for the recoverability of Exchange items, you will need an application-consistent backup (with VSS enabled) of the Exchange server VM. To check corresponding job settings, you can go to the **Jobs** tab in Veeam Backup **Enterprise Manager**, select the backup job that contains the Exchange server and choose to **Edit** it.

8. [] Click the **Add...** button.
9. [] Enter account: +++VEEAMINFRA\restoreoperator+++
10. [] Click the **Role** drop down menu.
11. [] Select **Restore Operator**.
12. [] Tick the **Microsoft Exchange items** check box.
13. [] Click the **OK** button.
14. [] Navigate to the **Settings** view.
15. [] Enter:
 1. Username: +++VEEAMLAB\Administrator+++
 2. Password: +++Pa$$w0rd+++
 
16. [] Click the **Save** button.
> Note:  This user account requires corresponding permissions to access Microsoft Active Directory and the mailbox. It needs Exchange Administrator rights and administrator's rights for all mailboxes. If you miss this step, the later Exchange restore exercise will fail.

17. [] Click the **VEEAMINFRA\Administrator** text link in the top right corner.
18. [] Select **Log Out**.
19. [] Enter:
 1. User name: +++VEEAMINFRA\restoreoperator+++
 2. Password +++Pa$$w0rd+++
 
20. [] Click the **Login** button.
21. [] Enter username: +++testmail+++
22. [] Press the **Enter** keyboard button.
> Note: If the testmail user cannot be found, the username and password set in Configuration\\Setting was incorrect. Click the Configuration button in the top right corner, Navigate to the Sessions view and enter username VEEAMLAB\\Administrator and password Pa$$w0rd.

23. [] Select the **testmail** user.
24. [] Tick the **Mail** check box.
25. [] Click the **Restore** button.
> Note:  Restore to another domain is supported within the same forest only.

26. [] Wait until **Status** reaches **Success** then click the **Sign out** text link in the top right corner.
27. [] Switch to the **Outlook Web Access** window using the Windows task bar.
28. [] Verify that the previously deleted item has been restored and close the **Outlook Web Access** window.

===

## Step 4: Manage public keys and encryption keys

1. [] In the **Veeam Backup Enterprise Manager** window, enter:
 1. User name: +++VEEAMINFRA\\Administrator+++
 2. Password: +++Pa$$w0rd+++

2. [] Click the **Login** button.
3. [] Click the **Configuration** button in the top right corner.
4. [] Navigate to the **Key Management** view.
5. [] Click the **Generate** button.
> Note: For security, it is recommended to periodically generate new Veeam Backup Enterprise Manager keys that should be used in the encryption process.

6. [] Enter hint: +++Veeam Training+++
> Note: Veeam Backup Enterprise Manager keys are created in the inactive state. To make the keys active and use them for encryption and decryption, you need to activate the keys.

7. [] Click the **Generate** button.

8. [] Select the **Veeam Training** key set.
9. [] Click the **Activate** button.
10. [] Tick the **Key retention period** check box.
11. [] Tick the **Auto-generate new keys** check box.
> Note: After the current keyset expires, **Veeam Backup Enterprise Manager** will automatically generate a new keyset and mark it as active.

12. [] Click the **Save** button.
> Important: It is important to regularly back up your Veeam Backup Enterprise Manager keys or save their copies in a safe place.

13. [] Click the **Export** button.
14. [] Click the **X** button in the bottom right corner of the window.

===

## Step 5: Decrypt data without a password

1. [] Launch the **Remote Desktop Connection client** from the Windows task bar.
2. [] Enter computer: +++VEEAM-VBR2+++.
3. [] Click the **Connect** button.
4. [] Enter password: +++Pa$$w0rd+++
5. [] Click the **OK** button.
6. [] Launch the **Veeam Backup & Replication console** from the desktop.
7. [] Click the **Connect** button.
8. [] Select **Backup Repositories** in the **Backup Infrastructure** view.
9. [] Click the **Add Repository** button on the **Backup Repository** ribbon.
10. [] Select **Direct attached storage**.
11. [] Select **Microsoft Windows**.
12. [] Enter name: +++Remote Repository+++.
13. [] Click the **Next** button on the **Name** step.
14. [] Click **Add new...** button.
15. [] Enter DNs name: +++VEEAM-VBR+++.
16. [] Click the **Next** button on the **Name** step.
17. [] Click the **Add...** button.
18. [] Enter:
 1. Username: +++VEEAMINFRA\Administrator+++
 2. Password: +++Pa$$w0rd+++
 
19. [] Click the **OK** button.
20. [] Click the **Next** button on the **Credentials** step.
21. [] Click the **Apply** button on the **Review** step.
22. [] Click the **Next** button on the **Apply** step.
23. [] Click the **Finish** button on the **Summary** step.
24. [] Verify that the repository server is set to VEEAM-VBR then click the **Next** button on the **Server** step.
25. [] Enter path to folder: +++X:\Backup+++.
26. [] Click the **Next** button on the **Repository** step
27. [] Untick the **Enable vPower NFS service on the mount server**.
> Note: In a production environment it usually not be recommended to disable the vPower NFS service on the mount server.

28. [] Click the **Next** button on the **Mount Server** step.
29. [] Tick the **Import existing backups automatically** check box.
30. [] Click the **Apply** button on the **Review** step.
31. [] Click the **Finish** button on the **Apply** step.
32. [] Click the **No** button to keep the current configuration backup location.
33. [] Navigate to the **Home** view.
34. [] Select **Disk (encrypted)** in the **Backups** section of the **Home** view.
35. [] Select **Backup Tiny-Veeam2**.
36. [] Click the **Specify password** button on the **Encrypted Backup** ribbon.
37. [] Click the **I have lost the password** text link.
38. [] Click the **Copy to clipboard** button.
39. [] Click the **Next** button on the **Request** step.
> Note: At this step, the copied request will be sent by email or passed in another way to the Veeam Backup Enterprise Manager administrator. For our lab purposes, we will just keep it copied in the clipboard.

40. [] Minimize the **Remote Desktop Connection** window.
41. [] Navigate to the **Backup Servers** view.
42. [] Click the **Refresh** button.
43. [] Navigate to the **Key Management** view.
44. [] Click the **Password Recovery** button.
45. [] Press the **CTRL + V** keyboard buttons to paste the challange request..
46. [] Click the **Next** button on the **Challenge Request** step.
47. [] Verify the **Request verified successfully** text is displayed then click the **Next** button on the **Verify request** step.
48. [] Press the **CTRL + C** keyboard buttons together to copy the response.
49. [] Switch back to the **Remote Desktop Connection client** window.
50. [] Press the **CTRL + V** keyboard buttons together to paste the request.
51. [] Click the **Next** button on the **Response** step.
> Note: Wait for the backup to be decrypted using the Veeam Backup Enterprise Manager key sets. This will take a maximum of 2 minutes.

52. [] Click the **Finish** button on the **Summary** step.
53. [] Expand the **Backup Tiny-Veeam2** backup job.
54. [] Verify that the **Tiny-Veeam2** virtual machine is now visible then minimize the **Remote Desktop Connection client** window.
55. [] Click the **Finish** button on the **Response** step of the **Password Recovery** wizard in the **Veeam Backup Enterprise Manager**.
56. [] Close the **Veeam Backup Enterprise Manager** window.

===

# Lab 9.5: Veeam configuration backup and restore

## Step 1: Schedule configuration backups

1. [] Select **Jobs** in the **Home** view.
2. [] Select the **On-Demand Sandbox SharePoint** job.
3. [] Click the **Stop** button on the **SureBackup** ribbon.
4. [] Click the **Yes** button to confirm stopping the job.
5. [] Press the **CTRL+A** keyboard buttons to select all jobs.
6. [] Click the **Disable** button on the **Job** ribbon.
> **Important:  Do NOT proceed until the job status is Stopped for all jobs.**

7. [] Click the **≡** button in the top left corner in **Veeam Backup and Replication**.
8. [] Select **Configuration Backup**.
9. [] Tick the **Enable configuration backup to the following repository** check box.
10. [] Tick the **Encrypt configuration backup** check box.
11. [] Click the **Password** drop down menu.
12. [] Select **Technical course that provides extensive information on Veeam solutions**.
13. [] Click the **Backup now** button.
14. [] Wait for the configuration backup to complete then click the **OK** button.

===

## Step 2: Restoring a configuration backup to another Veeam server

1. [] Switch back to the **Remote Desktop Connection client** window using the Windows task bar.
2. [] Click the **≡** button in the top left corner in **Veeam Backup and Replication**.
3. [] Select **Configuration Backup**.
4. [] Click the **Restore...** button.
5. [] Select the **Migrate** radio button.
6. [] Click the **Next** on the **Restore Mode** step.
7. [] Click the **Browse...** button.
8. [] Enter file name: +++X:\\Backups\\VeeamConfigBackup\\VEEAM-VBR+++.
9. [] Click the **Open** button.
10. [] Select the newest **VEEAM-VBR** configuration backup file.
> Note: The configuration backup file is named in the following way: ServerName\_YYYY-MM- DD\_HH-MM-SS.bco

11. [] Click the **Open** button.
12. [] Click the **Analyze** button on the **Configuration Backup** step.
13. [] Click the **Next** button on the **Backup Contents** step.
14. [] Enter **Password**: +++vmce+++
15. [] Click the **Validate** button on the **Password** step.
16. [] Click the **Connect** button on the **Target Database** step.
17. [] Click the **Yes** button to confirm that the current configuration database will be lost.
18. [] Click the **Restore** button on the **Restore Options** step.
19. [] Click the **Yes** button to confirm closing the **Veeam Backup and Replication Console** and stop all running jobs.

21. [] Wait for the restore process to complete then click the **Next** button on the **Restore** step.
22. [] Click the **Start** button on the **Credentials** step.
> Note:  Because the Configuration Backup is encrypted, both usernames and passwords are included. If the Configuration Backup is not encrypted, you would have to enter all the passwords here.

23. [] Untick the **Launch the Backup & Replication user interface** check box.
24. [] Click the **Finish** button on the **Summary** step.
25. [] Close the Remote Desktop Connection to **VEEAM-VBR2**.
26. [] Select the **Backup Oracle** job.
27. [] Press the **CTRL+A** keyboard buttons to select all jobs.
28. [] Click the **Disable** button on the **Job** ribbon.

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
14. [] Close the **Veeam Backup & Replication console** window.
> **Note:**  If you want to configure a specific PowerShell script to be run as a post-job activity, you can create a .ps1 file out of it and type the following in job settings (**Storage** tab → **Advanced** → **Script** → **Post job activity**): C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\powershell.exe -Noninteractive -File "\[PathToScript\]\\\[scriptname\].ps1"
>
> **Note:** If you want to configure a specific PowerShell script to be run as a post-job activity, you can create a .ps1 file out of it and type the following in job settings (**Storage** tab → **Advanced** → **Script** → **Post job activity**): C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\powershell.exe -Noninteractive -File "\[PathToScript\]\\\[scriptname\].ps1"
>
> **Note:** If you want to configure a specific PowerShell script to be run as a task in the Windows Scheduler, you would also want to save this kind of script as a .ps1 file (e.g., the content of the file can be the following): Add-PSSnapin VeeamPSSnapin Get-VBRJob --name "Backup Tiny-Veeam2" | Start- VBRJob --FullBackup And then to set up a new task created via Windows Scheduler to run: PowerShell -file "\[PathToScript\]\\\[scriptname\].ps1"

---

# Congratulations!

You have successfully completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
