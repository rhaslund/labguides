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
11. []  Wait until the storage discovery reaches status **Success* then click the **Close** button.

===

## Step 2: Create a SAN snapshot

1. [] Expand **HPE StoreVirtual** in the **Storage Infrastructure** view.
3. [] Expand **Veeam-VSA-MGMTG**.
4. [] Select **veeam-vsa-cluster**.
5. [] Select **datastore1**.
6. [] Click the **Create Snapshot** button on the **Volume** ribbon.
7. [] Keep the default settings and click the **OK** button.
8. [] Wait until the create storage snapshot reaches status **Success* then click the **Close** button.
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
8. [] Click the **Choose...** in the **Host*' section.
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

19. [] Expand the **(C:)** drive**.
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
> Note: The snapshot is open longer time in this example with backup from storage snapshots. This is because it takes time to orchestrate the storage snapshot and there is no data changes in the virtual machine during the backup. Generally, it makes the most sense to enable backup from storage snapshots for highly transactional servers.

===

# Lab 9.2. Using backup to tape

## Step 1: Add a tape server

1. [] Open **Veeam Backup & Replication**.
2. [] Open **Tape Infrastructure** view.

3. [] There are no Tape Drives or Libraries installed there. In the lab environment, the tape library is connected to the **VEEAM-Remote** server. Click **Add Tape Server** to add it to the infrastructure.
4. [] Click the **Choose server:** drop-down list.
5. [] Select **VEEAM-Remote** from the drop-down list.
6. [] Click **Next**.
7. [] Do not set traffic throttling. Click **Next** to proceed to the **Review** step of the wizard.
8. [] Review the list of components required for the tape server. Click **Apply**.
9. [] The tape server is added to the backup infrastructure. Click **Next** when the process is over.
10. [] Click **Finish** to complete the installation.

===

## Step 2: Add new devices

1. [] Expand **Libraries**.
2. [] Expand **HP MSL G3 Series 1068**.
3. [] Use the **Remote Desktop Connection** to connect to the remote server so that we can install tape drivers.
4. [] Enter +++VEEAM-Remote+++ and click the **Connect** button.
5. [] Open **Start** menu.
6. [] Type **Device Manager** and switch to Setting section in Start menu.
7. [] Expand **Medium Changer devices**.
8. [] Double-click **Unknown Medium Changer**.
9. [] Open the **Driver** tab.
10. [] Click **Update driver...**
11. [] Click **Browse my computer for driver software**.
12. [] Enter path +++C:\install\HP Tape Drivers+++ and click **Next**.
13. [] After the driver software is installed, click **Close**.
14. [] Check the driver version now to see if it's updated. Click **Close**.
15. [] Expand **Other devices**.
16. [] Right-click the first **HP Ultrium** device.
17. [] Select **Update driver software**.
18. [] Click **Browse my computer for driver software**.
19. [] Click **Next**.
20. [] Click **Close**.
21. [] Right-click on the remaining **HP Ultrium** device.
22. [] Click on **Update Driver Software**.
23. [] Select **Browse my computer for driver software**.
24. [] Click **Next**.
25. [] Click **Close**.
26. [] Close the **Remote Desktop Connection** window.

===

## Step 3: Add unrecognized tapes to the free media pool

1. [] Select the **HP MSL G3 Series 1068** tape library.
2. [] Click Location.
3. [] Select Local.
4. [] Select **Media**.
5. [] Select all tapes.
6. [] Right-click anywhere in the selected area.
7. [] Choose **Move to Media Pool**.
8. [] Select the **Free** media pool.
> Note:  If you are not sure if the tapes are completely new and you want to use them as free media, use Erase Tape → Short to place them in **Media Pool** → **Free**.
9. [] Click **Yes** to confirm moving the unrecognized tapes to the **Free Media Pool**.
10. [] You may now see the tapes added to the **Free** Media Pool. Go to the **Home** view.

===

## Step 4: Create a tape backup job

1. [] Click **Tape Job** on the ribbon toolbar.
2. [] Select **Backups...**
3. [] Leave the default value in the **Name** field. Click **Next**.
4. [] On the **Backup Files** page, click **Add...**
5. [] Click **Backup Jobs...**
6. [] Select **Backup ORCL**.
7. [] Click **OK**.
8. [] Click **Latest**.
9. [] Click **Next**.
10. [] On the **Full Backup** page, click **Add New...**
11. []  Select **Simple media pool**.
12. [] Enter the media pool name: +++Media Pool Full+++. Click **Next**.
13. [] Click **Add...**
14. [] Select the first seven tapes from the **Free Media Pool**.
15. [] Click **OK**.
16. [] Click **Next**.
17. [] On the **Media Set** page, click the **Daily at** radio button.
> Note: A media set is a consequent data stream that can span several tapes (for example, a weekly database backup).

18. [] Leave **12 PM** and click the **Everyday** drop-down list.
19. [] Select **On these days** from the drop-down list.
20. [] Click **Days** to set the particular days.
21. [] Select **Monday**.
22. [] Click **OK**.
23. [] Click **Next**.
24. [] On the **Retention** page, select **Protect data for**.
25. [] Click the weeks counter and set it to *4* weeks as the **Data retention policy** for this media pool. Click **Next**.
26. [] Leave the default encryption settings and click **Apply**.
27. [] Click **Finish**.
28. [] Make sure **Media pools** for both full and incremental backups are set to **Media Pool Full (HP MSL G3 Series 1068)**. Media pools are logical groups of tapes.
29. [] Click **Next**.
30. [] On the **Options** page, leave all options at their default values and click **Next**.
31. [] Select the **Run the job automatically** check box.
32. [] Click the **As new backup files appear** radio button.
33. [] Click **Apply**.
34. [] Click **Finish**.
35. [] Go to **Jobs** → **Tape**.
36. [] The **Backup to Tape Job 1** job is now available.

===

# Lab 9.3: Configuring Hyper-V backup to run in off-host mode

## Step 1: Install and configure the hardware VSS provider

1. [] HPE LeftHand P4000 VSS Provider is the hardware provider that supports the Volume Shadow Copy Service on the HPE LeftHand Storage Solution. The hardware VSS provider needs to be installed on both the host and the off-host proxy. In our case, it's already installed on the Hyper-V host, so let's install it on **VEEAM-VBR**. Launch **File Explorer**.
2. [] Select disk C:\
3. [] Click the install folder which contains distributives for the course.
4. [] Launch the HPE\_StoreVirtual\_App\_Aware\_Snapshot\_Mgr\_Installer executable.
5. [] Click **Next**.
6. [] Click the **I accept the terms of the license agreement** radio button.
7. [] Click **Next**.
8. [] Click **Next**.
9. [] Click **Next**.
10. [] Click **Next** to proceed from the Specify CIM connection port step.
11. [] Click **Install**.
12. [] Read the notification and click **Next**.
13. [] Click **Finish** to exit the installation wizard.
14. [] Close **File Explorer**.
15. [] Launch the **Authentication Console** from the **Start Menu**.
16. [] Click **OK** to accept the notification about credentials.
17. [] Right-click **Authentication Console**.
18. [] Select **New Management Group Credentials** from the context menu.
> **Important!** The management group name is **Case Sensitive.**

19. []  Add Veeam-VSA-MGMTG with the following credentials:
 1. Username: +++veeam+++ 
 2. Password: +++veeam+++ 
 3. Click the **Test** button.

20. []  Select to **Test** the configuration and enter +++10.0.2.240+++ as the IP address. Click **OK**.
21. [] After the test is over, press **OK**.
> Note: Pay attention to the management group name as it is case sensitive. Otherwise, the test will fail.

22. [] Close the Authentication Console window.
23. [] To verify that a specific provider is going to be used to back up a particular Hyper-V host, you need to open the **Backup Infrastructure** view.
24. [] Click on **Microsoft Hyper-V** under **Managed Servers**.
25. [] Right-click **VEEAM-HYPERV** in the working area.
26. [] Select **Manage Volumes**.
27. [] Verify that drive G:\\ has **LeftHand Networks VSS Provider** listed instead of the default **Microsoft Software Show Copy** provider, then click **OK** to close the **Manage Volumes** window.

===

## Step 2: Add a Hyper-V off-host backup proxy

1. [] On the **Backup Infrastructure** view, select the **Backup Proxies** node in the inventory pane.
2. [] Click **Add Proxy** on the ribbon.
3. [] Select **Hyper-V\...**
4. [] **VEEAM-VBR** (this server) is going to be used as an off-host backup proxy. Click **Next** to confirm this selection.
The Hyper-V role must be enabled on the machine so that it's possible to add it as an off-host backup proxy.
5. [] Click **Next** to skip configuring the traffic rules and proceed with the installation.
6. [] At this step, Veeam Backup & Replication displays the list of components required for work of the Hyper-V off-host backup proxy. Click **Apply** to proceed with the installation.
7. [] Click **Next** to proceed.
> Note:  Checking for updates could take up to eight minutes.

8. [] Click **Finish** as the process ends.

===

## Step 3: Edit a Hyper-V backup job and run it in the off-host mode**

1. [] Go to the **Home** view.
2. [] Go to **Jobs** → **Backup**.
3. [] Select **Backup Tiny-Veeam2**.
4. [] Click **Edit**.
5. [] Click **Next**.
6. [] Select the **Tiny-Veeam2** VM.
> Note:  We are re-adding the VM since it was deleted and restored from a backup previously. The VM uuid has changed, so we have to re-add it onto the job.

7. [] Select **Remove**.
8. [] Re-add **Tiny-Veeam2** on the **Virtual Machines** step by clicking **Add**.
9. [] Expand the **VEEAM-HYPERV** host.
10. [] Select **Tiny-Veeam2**.
11. [] Click **Add**.
12. [] Click **Next**.
13. [] On the **Storage** page, click **Choose** at the **Backup proxy** selection section.
14. [] Select **Off-host backup**.
15. [] Make sure the newly-added proxy is in the list below. Press **OK** to confirm your changes.
16. [] Click **Finish** to finish editing the job.
17. [] Click the **Start** button on the Job ribbon to launch the Backup Tiny-Veeam2 job.
18. [] Click on **Tiny-Veeam2** in the **Statistics** view and review the information on the right about its processing. Make sure the off-host mode was used.

===

# Lab 9.4. Working with Veeam Backup Enterprise Manager

## Step 1. Review the server's management

1. [] Minimize the **Veeam Backup & Replication** window.
2. [] Launch **Veeam Backup Enterprise Manager** using the shortcut on your screen.
3. [] Click the **Configuration** option.

4. [] Earlier, **VEEAM-VBR** was added to the Veeam Backup Enterprise Manager console. Click Add... to start adding the second backup server **VEEAM-VBR2** in a similar way.

5. [] Click **Yes** to accept the warning that Veeam Backup Enterprise Manager will push its license to all connected backup servers.
6. [] Enter: 
 1. DNS name: +++VEEAM-VBR2+++ 
 2. User name: +++VEEAMINFRA\Administrator+++ 
 3. Password: +++Pa$$w0rd+++ 
 4. Click **OK**.

7. [] Now, both Veeam backup servers are visible to **Veeam Backup Enterprise Manager**. Data about backup and replication jobs from the SQL databases used by VEEAM-VBR and VEEAM-VBR2 will be collected and stored. Veeam Backup Enterprise Manager enables you to modify the settings of VMware and Hyper-V backup and replication jobs that have been previously configured on managed backup servers. You can start and stop these jobs, clone them, and enable and disable backup copy jobs. As an example, let's disable running **Backup Copy Job WAN**. Click **Home**.
8. [] Go to the **Jobs** tab.
9. [] Select **Backup Copy Job WAN**.
10. [] Click the **Job** drop-down menu on the toolbar.
11. [] Select **Disable**.
12. [] After disabling the job, the *Backup Copy Job WAN* job status changes to either **Warning** or **Success**. Open the **Veeam Backup & Replication UI** to verify that the job has been disabled.
13. [] Return to **Veeam Backup Enterprise Manager** by clicking the browser icon in the toolbar.

===

## Step 2: Restore guest OS files

1. [] Open the **Configuration** tab.
2. [] Select the **veeam-vbr.veeaminfra.local server.**
3. [] Click the **Start collecting** button.
4. [] Click **OK** to confirm your selection. To automatically run catalog replication after every backup job, click **Schedule** on the toolbar. In the displayed window, select **Automatic after any backup job finishes** and specify other options as necessary. This is actually not required in this specific lab environment since Veeam Backup & Replication and Veeam Backup Enterprise Manager are installed on the same machine and use the same catalog. However, this would be required for performing a file-level restore if Veeam Backup & Replication and Veeam Backup Enterprise Manager were installed on different machines.
5. [] Click the **Home** button in the top left corner.
6. [] Click the **Files** tab.
7. [] Type in +++VEEAM-DC01+++ and click the search icon on the right.
8. [] Open the **Search** tab.
9. [] In the **Search** field, type in +++*.txt*+++. Click on the **Search** icon.
10. [] Expand the **Advanced search** section and review the advanced search criteria.
11. [] Click the search icon to the right of the **Search** field.
12. [] Right-click one of the found files.
13. [] Select **Restore**.
14. [] Click **Overwrite** in the Restore context menu.
15. [] Click **Yes** to confirm the operation. Use the +++VEEAMLAB\\Administrator+++ account to authenticate if prompted.
> Note:  The restore session will start, and you can view its progress in the session log.

===

## Step 3: Delegate restore privileges

1. [] Open Outlook Web Access.
2. [] Enter:
 1. Username +++testmail@veeamlab.local+++ 
 2. Password +++Pa$$w0rd+++ 

3. [] Click the **Sign In** button.
3. [] Click **Delete** to delete the most recent email from the **testmail@veeamlab.local** user Inbox folder.
4. [] Open **Veeam Backup Enterprise Manager** from the Windows task bar.
5. [] The authorized restore operators at the Help Desk can be granted rights to restore the necessary Exchange items (emails, tasks, etc.) and SQL items. Select the **Configuration** tab in **Veeam Backup Enterprise Manager**.
6. [] Open the **Roles** tab on the left.
> Note:  To provide for the recoverability of Exchange items, you will need an application-consistent backup (with VSS enabled) of the Exchange server VM. To check corresponding job settings, you can go to the **Jobs** tab in Veeam Backup **Enterprise Manager**, select the backup job that contains the Exchange server and choose to **Edit** it.

7. [] Click **Add...** to add a new user.
8. [] Enter account +++VEEAMINFRA\restoreoperator+++, then click on the **Role** drop-down menu.
9. [] Click on **Restore Operator**.
10. [] Select the **Microsoft Exchange items** check box.
11. [] Confirm your choices by clicking **OK**.
12. [] Click on the **Settings** tab.
13. [] Enter +++VEEAMLAB\Administrator+++ and +++Pa$$w0rd+++ in the Account section, then click **Save**.
> Note:  This user account requires corresponding permissions to access Microsoft Active Directory and the mailbox. It needs Exchange Administrator rights and administrator's rights for all mailboxes. If you miss this step, the later Exchange restore exercise will fail.

14. [] Click **Sign out**.
15. [] Log in to Veeam Backup Enterprise Manager by entering the username +++VEEAMINFRA\restoreoperator+++ and the password +++Pa$$w0rd+++, then click **Login**.

16. [] Select the **Items** tab. Enter the account of the Microsoft Active Directory user whose mailbox will be restored: +++testmail+++, then click the **Search** icon.
17. [] Select the user **testmail** in the list of search results.
18. [] Choose a restore point and select what type of item you need to restore. Click the **Mail** tab.
19. [] Click the **Restore** button.
> Note:  Restore to another domain is supported within the same forest only.

20. [] Wait until the restore completes. Click **Sign out**.
21. [] Restore the **Outlook Web Access** window.
22. [] Verify that the previously deleted item has been restored and close the **Outlook Web Access** window.

===

## Step 4: Manage public keys and encryption keys

1. [] Log in to **Veeam Backup Enterprise Manager** using +++VEEAMINFRA\\Administrator+++ | +++Pa$$w0rd+++.
2. [] Click the **Configuration** option.
3. [] Select **Key Management**.
4. [] For security, it is recommended to periodically generate new Veeam Backup Enterprise Manager keys that should be used in the encryption process. Click **Generate\...** on the right of the keyset list.
5. [] In the **Hint**: field, enter a description for the created keyset. Press **Generate**.
6. [] Veeam Backup Enterprise Manager keys are created in the inactive state. To make the keys active and use them for encryption and decryption, you need to activate the keys. In Veeam Backup Enterprise Manager, go to the **Configuration** → **Key Management** section.
Select the inactive keyset in the list.
7. [] Click **Activate** on the right of the list.
8. [] In the **Key retention settings**, select the **Key retention period** check box and specify *4* as the number of weeks for which Veeam Backup Enterprise Manager keys must remain in effect.
9. [] Also, select the **Auto-generate new keys** check box. After the current keyset expires, **Veeam Backup Enterprise Manager** will automatically generate a new keyset and mark it as active.
10. [] Click **Save**.
11. [] You may now see the newly generated keyset. It is important to regularly back up your Veeam Backup Enterprise Manager keys or save their copies in a safe place. To export a keyset, in the keyset list, select a keyset you want to back up and click **Export**.
12. [] Save the resulting PEM file on the local disk.
13. [] To proceed with the following lab, launch **Remote Desktop Connection**.

===

## Step 5: Decrypt data without a password

1. [] Log in to **VEEAM-VBR2** through the Remote Desktop Connection client.
2. [] Type in +++Pa$$w0rd+++ and click **OK**.
3. [] Run **Veeam Backup & Replication** from the desktop.
4. [] Click the **Connect** button.
5. [] In the **Backup Infrastructure** view, click **Backup Repositories**.
6. [] Click the **Add Repository** button on the ribbon.
7. [] Enter the name: +++Remote Repository+++ and click **Next**.
8. [] Keep the default repository type of Microsoft Windows Server and click **Next**.
9. [] Click **Add new...** to add **VEEAM-VBR.**
10. [] Fill in the **DNS or IP address of a server with VEEAM-VBR**. Click **Next**.
11. [] Click **Add...** to input credentials.
12. [] Input the credentials (+++VEEAMINFRA\Administrator+++ | +++Pa$$w0rd+++) and click **OK**.
13. [] Click **Next**.
14. [] Review the information and click **Apply**.
15. [] Wait for the operation to complete and click **Next**.

16. [] Check the Summary and click **Finish**.
17. [] Verify that the repository server is set to VEEAM-VBR and click **Next**.
18. [] Click **Browse...** to set a path to a repository.
19. [] Expand the **VEEAM-VBR** server.
20. [] Expand drive **X:**
21. [] Select the **Backup** folder.
22. [] Click **OK**.
23. [] Click **Next**.
24. [] At the **Mount Server** step of the wizard, click **Next** to proceed.
25. [] Review the settings and click **Apply**.
26. [] Wait for the operation to complete and click **Finish**.
27. [] Click **Yes** to change the configuration backup location.
28. [] Click **Add Repository**.
29. [] Fill in the name +++Local Backup Repository+++ and click **Next**.
30. [] On the **Type** step of the wizard, make sure that the default **Microsoft Windows server** option is selected and click **Next**.
31. [] Click **Next**.
32. [] Click **Browse...** in the **Location** section.
33. [] Expand the **VEEAM-VBR** server.
34. [] Expand the **E:** drive.
35. [] Select the **Backups folder**.
36. [] Click **OK**.
37. [] On the **Repository** step of the wizard, click **Next**.
38. [] Leave the default settings on the **Mount Server** step of the wizard and click **Next**.
39. [] Review the settings and click **Import existing backups automatically** to continue.
40. [] Click **Apply**.
41. [] Click **Finish**.
42. [] Click the **Rescan** button on the ribbon.
43. []  **Important!** You may receive a warning that the Default Backup Repository (X:\\Backup) failed to synchronize. This warning can safely be ignored because the folder doesn't yet exist since no data has been stored there yet. Wait for the operation to complete. Click the **Close** button.
44. []  Go to the **Home** view.
45. [] Select **Backups** then **Disk (encrypted)**.
46. [] Right-click **Backup Tiny-Veeam2** in the list.
47. [] Select **Specify password**.
48. [] Click on **I have lost the password**.
49. [] Copy the request to the clipboard by clicking **Copy to clipboard**.
50. [] Click **Next**. At this step, the copied request will be sent by email or passed in another way to the Veeam Backup Enterprise Manager administrator. For our lab purposes, we will just keep it copied in the clipboard.
51. [] Minimize the **Remote Desktop Connection** window.
52. [] Go to **Configuration**.
53. [] Select **Key Management**.
54. [] Click **Password Recovery...** to open the **Password Recovery** wizard.
55. [] Paste the request. You can use the [CTRL+V] key combination or click **Paste** at the bottom of the wizard.
56. [] Click the **Next** button.
57. [] At the **Response** step, copy the text displayed in the wizard to the clipboard. Click **Finish**.
58. [] Go back to the **VEEAM-VBR2** Remote Desktop Connection.
59. [] Paste the copied response to the text window at the **Response** step of the **Encryption Key Restore** wizard.
60. [] Click **Next**.
61. [] Click **Finish**. The file content will be unlocked.
62. [] You have successfully decrypted the data.
63. [] Close the **Remote Desktop Connection to VEEAM-VBR2** server.
64. [] Close the **Veeam Backup Enterprise Manager** window.

===

# Lab 9.5: Veeam configuration backup and restore

## Step 1: Schedule configuration backups

1. [] Go to the main menu (green button in the upper left corner) of **Veeam Backup & Replication**.
2. [] Click **Configuration Backup**.
3. [] Select the **Enable configuration backup to the following repository** check box.
4. [] Verify that the **Remote Repository** backup repository is selected, then select the **Encrypt configuration backup** check box.
5. [] Choose the password we created earlier in the drop-down list.
6. [] Click the **Backup now** button to ensure that we have a current configuration backup.
7. [] Wait for the configuration backup to complete, then click **OK** to save changes and close the window.
8. [] Click on the **Backup ORCL and press CTRL+A to select all jobs job.**
9. [] **Tip:** In case the Disable button is grayed out, just apply any sorting to the list. Click the **Disable button** in the ribbon.
> Note:  Do NOT proceed until the job status is Stopped for all jobs.

===

## Step 2: Restoring a configuration backup to another Veeam server**

1. [] Log in to **VEEAM-VBR2** though the **Remote Desktop Connection**.
2. [] Use +++VEEAMINFRA\\Administrator+++ | +++Pa$$w0rd+++ to connect. Confirm that you want to connect to this computer by clicking **Yes** if prompted. You can apply configuration data from one of your Veeam servers to any other Veeam backup server in your backup infrastructure. We will restore configuration from **VEEAM-VBR** to **VEEAM-VBR2**.
3. [] If required, authenticate by filling in the credentials: *VEEAMINFRA\\Administrator | Pa$$w0rd* and click **OK**.
4. [] Open the **main menu** in the top left corner of Veeam Backup & Replication.
5. [] Choose **Configuration Backup**.
6. [] In the **Backup job status** section, click **Restore**. The **Configuration Database Restore** wizard will be launched.
7. [] Select **Migrate** as a restore scenario.
8. [] Click **Next**.
9. [] Ensure **This Server** is selected as a repository and click **Browse**.
10. [] Go to **X:\\Backups\\VeeamConfigBackup\\VEEAM-VBR**.
11. [] Select the configuration backup file stored there. The configuration backup file is named in the following way: ServerName\_YYYY-MM- DD\_HH-MM-SS.bco
12. [] Click **Open**.
13. [] Click **Analyze**.
14. [] Review the data on the file. Note that the product version is displayed. Click **Next**.
15. [] Enter **Password**: +++vmce+++. Click **Validate**.
16. [] Click **Connect** at the **Target Database** step.
17. [] Confirm that you are about to replace the current content of the database by clicking **Yes**.
18. [] Click **Restore** at the Restore Options step.
19. [] Confirm that you want to close the Veeam Backup & Replication interface by clicking **Yes**.
> Note: Because some jobs are non- scheduled, they could not be disabled, which will cause a warning.

20. [] Click **Yes** to perform a full configuration restore.
21. [] After the restore process completes, click **Next**.
22. [] Click **Start**.
> Note:  Because the Configuration Backup is encrypted, both usernames and passwords are included. If the Configuration Backup is not encrypted, you would have to enter all the passwords here.

23. [] After the process completes, click **Finish**.
24. [] Close the Remote Desktop Connection to **VEEAM-VBR2**.
25. [] We are now back at the **VEEAM-VBR** server.

===

# Lab 9.6: Introducing the Veeam PowerShell snap-in

1. [] Go to the main menu of Veeam Backup & Replication.
2. [] From the main menu, click **Console**.
3. [] Click **PowerShell** to open the console.
4. [] Click **Yes** if the warning about **PowerShell** execution policy is shown on the screen.
5. [] Type in +++Get-VBRCommand+++ and hit **Enter** on your keyboard.
6. [] Review the output -- this is a full list of all Veeam Backup & Replication cmdlets.
7. [] **Get-VBRJob** returns a list of all backup, replication and copy jobs configured in your Veeam Backup & Replication install. Type +++Get-VBRJob+++and run it.
8. [] Review the result -- all the jobs created earlier in the flow of the course.
9. [] Working in PowerShell is like working at a conveyor belt. Let's apply a parameter -- the name of the job to the output of the previous command. +++Get-VBRJob -name "Backup Tiny-Veeam2"+++
10. [] Now, only the information regarding the job in question is displayed.
11. [] **Backup Tiny-Veeam2** was returned by running this command. Now, we can perform some actions with it. Let's launch this job. Type in +++Get-VBRJob -name "Backup Tiny-Veeam2" | Start-VBRJob+++ and hit Enter.
12. [] In **PowerShell, the** job process is also displayed. Minimize the **PowerShell** window.
13. [] Check the user interface of Veeam Backup & Replication. Note that the job is now started. Minimize the **Veeam Backup & Replication** window.
14. [] Start-VBRJob is another cmdlet which also has its own parameters.
Create a variable where the result of *Get-VBRJob* will be stored, and after that, apply the command to this operation. Verify that the previous run of the job ended. After that, type in the following:
PS C:\\&gt; *$Job = Get-VBRJob -name "Backup Tiny-Veeam2"*
PS C:\\&gt; *Start-VBRJob $Job -FullBackup*
**For example:** We can use it to launch an active full backup: Get-VBRJob -name "Backup Tiny- Veeam2" | Start-VBRJob -FullBackup
15. [] The job, used as a parameter, will be launched again.
16. [] Open **File Explorer** from the **task bar**.
17. [] Review the repository (X:\\Backup\\Backup Tiny-Veeam2) to check that a new incremental backup file appeared as a result of the previous run and that a .vbk file also appeared as a result of this run. Return to the PowerShell interface by closing the **File Explorer** window.
18. [] Finally, Veeam PowerShell snap-in can be combined with regular Windows PowerShell commands. For example, instead of setting up the job name as a variable, we can use Windows PowerShell Read- Host to type in the job name. Run this script while choosing another job -- Backup ORCL.
PS C:\\&gt; *$JobName = Read-Host "Write name of your Job"*
PS C:\\&gt; *$Job = Get-VBRJob -name $JobName*
PS C:\\&gt; *Start-VBRJob $Job -FullBackup*
> Note:  If you want to configure a specific PowerShell script to be run as a post-job activity, you can create a .ps1 file out of it and type the following in job settings (**Storage** tab → **Advanced** → **Script**
→ **Post job activity**): C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\powershell.exe -Noninteractive -File "\[PathToScript\]\\\[scriptname\].ps1"

19. [] **Note:** If you want to configure a specific PowerShell script to be run as a post-job activity, you can create a .ps1 file out of it and type the following in job settings (**Storage** tab → **Advanced** → **Script** → **Post job activity**):
C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\powershell.exe -Noninteractive -File "\[PathToScript\]\\\[scriptname\].ps1"
20. [] **Note:** If you want to configure a specific PowerShell script to be run as a task in the Windows Scheduler, you would also want to save this kind of script as a .ps1 file (e.g., the content of the file can be the following):*Add-PSSnapin VeeamPSSnapin Get-VBRJob --name "Backup Tiny-Veeam2" | Start- VBRJob --FullBackup And then to set up a new task created via Windows Scheduler to run: PowerShell -file "\[PathToScript\]\\\[scriptname\].ps1"*

---

# Congratulations!

You have successfully completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
