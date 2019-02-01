Module 6: Objects Recovery

---
**This lab is expected to last a maximum of 90 minutes including lab launch.**


# Lab 6.1: Perform Microsoft Exchange items recovery

## Step 1: Delete an e-mail from the inbox

1. [] Launch **Outlook Web Access** from the Windows task bar.
2. [] Enter:
 1. Username: +++testmail@veeamlab.local+++
 2. Password: +++Pa$$w0rd+++

3. [] Click the **Sign In** button.
4. [] Click the **Never** button in Google Chrome to avoid saving the password.
5. [] Click the **Delete** text link to delete the most recent e-mail.
6. [] Select the **Deleted items** folder.
7. [] Click the **Empty** text link.
8. [] Click the **Yes** button to confirm deleting all the items and subfolders in the **Deleted items** folder.
9. [] Minimize the **Outlook Web Access** window.

===

## Step 2: Recovery the deleted e-mail

1. [] Launch the **Veeam Backup & Replication console** from the desktop.
2. [] Click the **Connect** button.
3. [] Select **Disk** in the **Backups** section of the **Home** view.
4. [] Expand the **Backup Exchange & SharePoint** job.
5. [] Select **VEEAM-EX01**.
6. [] Click the **Application Items** button on the **Backup** ribbon.
7. [] Select **Microsoft Exchange**.
8. [] Keep the default setting and click the **Next** button on the **Restore Point** step.
9. [] Tick the **Do not show me this page again** check box.
10. [] Click the **Next** button on the **Reason** step.
11. [] Click the **Finish** button on the **Summary** step.
> Note: The Veeam Explorer for Microsoft Exchange will launch now. It can also be launched manually from the Windows Start Menu.

12. [] Expand the **Mailbox Database** hierachy.
13. [] Expand the **testmail** mailbox.
14. [] Select the **Inbox** folder.
15. [] Select the **previously deleted e-mail** message.
16. [] Click the **Restore Items** button on the **Items** ribbon.
17. [] Select **Restore to...**.
18. [] Enter mailbox: +++testmail@veeamlab.local+++.
19. [] Select the **The following account** radio button.
20. [] Enter:
 1. User name: +++VEEAMLAB\Administrator+++
 2. Password: +++Pa$$w0rd+++

21. [] Click the **Next** button.
22. [] Enter mailbox server (CAS): +++veeam-ex01.veeamlab.local+++
23. [] Click the **Next** button.
24. [] Keep the default settings and click the **Restore** button.
25. [] Click the **OK** button.
26. [] Close the **Veeam Explorer for Microsoft Exchange** window.
27. [] Switch to the **Outlook Web Access** window using the Windows task bar.
28. [] Select the **Inbox** folder.
29. [] Confirm the restored e-mail appears then close the **Outlook Web Access** window.

====

# Lab 6.2: Perform Microsoft SharePoint items recovery

1. [] Select the **VEEAM-SP01** virtual machine.
2. [] Click the **Application Items** button on the **Backup** ribbon.
3. [] Select **Microsoft SharePoint**.
4. [] Select the **http://veeam-sp01** site.
5. [] Click the **Next** button on the **Site** step.
6. [] Select the **latest full backup**.
7. [] Click the **Next** button on the **Content Database** step.
8. [] Tick the **Do not show me this page again** check box.
9. [] Keep the default settings and click the **Next** button on the **Restore Reason** step.
10. [] Click the **Finish** button on the **Summary** step.
11. [] If prompted, click the **Yes** button to upgrade the database.
12. [] Expand **WSS_Content.mdf**.
13. [] Expand **Home**.
14. [] Expand **Content**.
15. [] Select the **Shared Documents** folder.
16. [] Click the **Restore Library** button on the **Library** ribbon.
17. [] Select the **Use the following account** radio button.
18. [] Enter:
 1. Account: +++VEEAMLAB\Administrator+++
 2. Password: +++Pa$$w0rd+++

19. [] Click the **Next** button on the **Specify target SharePoint site and domain account to be used** step.
20. [] Select the **Restore to the following list** radio button.
21. [] Enter: +++Restored Docs+++.
22. [] Click the **Next** button on the **Specify target list** step.
23. [] Click the **Restore** button on the **Specify the restore options** step.
24. [] Click the **OK** button.
25. [] Close the **Veeam Explorer for Microsoft SharePoint** window.
26. [] Launch **Google Chrome** using the Windows task bar.
27. [] Browse to +++http://veeam-sp01+++
28. [] Click the **Restored Docs** text link in the left side.
29. [] Verify the three files **invoice.docx**, **market strategy.pptx** and **quote.docx** are present in the **Restored Docs** folder then close the **Google Chrome** window.

===

# Lab 6.3: Perform Oracle items recovery

1. [] Launch **Oracle SQL Developer** from the Windows task bar (icon looks like a disk with a green arrow).
2. [] Click the **green \+** button above the **Connections** text in the **Connections** pane.
3. [] Enter:
 1. Connection Name: +++Production Oracle+++
 2. Username: +++scott+++
 3. Password: +++tiger+++
 4. Hostname: +++10.0.3.14+++
 5. SID: +++ora11g+++

4. [] Click the **Save** button.
6. [] Click the **Connect** button.
7. [] Expand the **Production Oracle** connection
8. [] Enter: +++select * from EMP+++ in the **Production Oracle** tab.
9. [] Click the **Run Script** button (icon looks like a notepad with a green arrow) or press the **F5** keyboard button.
10. [] Review the output result in the **Script Output** pane then expand **Tables (Filtered)**.
11. [] Right click the **EMP** table.
12. [] Select **Table**.
13. [] Select **Drop...**.
14. [] Click the **Apply** button
15. [] Click the **OK** button.
16. [] Click the **Run Script** button (icon looks like a notepad with a green arrow) or press the **F5** keyboard button.
> Note: Since the table has been removed, an error message will be shown in the output window at the bottom
on the tab.

17. [] Close the **Oracle SQL Developer** window.
18. [] Click the **No** button to discard changes.
19. [] Expand the **Backup Oracle** job.
20. [] Select the **VEEAM-ORCL** virtual machine.
21. [] Click the **Application items** button on the **Backup** ribbon.
22. [] Select **Oracle**.
23. [] Keep the default settings and click the **Next** button on the **Restore Point** step.
24. [] Tick the **Do not show me this page again** check box.

24. [] Click the **Next** button on the **Reason** step.
25. [] Click the **Finish** button on the **Summary** step.
26. [] Wait for the **Veeam Explorer for Oracle** window to load then select the **DB1** database.
27. [] Click the **Restore Database** button on the **Home** ribbon.
28. [] Select **Restore point-in-time state to veeam-orcl...**.
29. [] Select the **Restore to a specific point in time (requires redo log backups)** radio button.
30. [] Move the **slider** all the way to the left (select the oldest point in time available).
> **Important: Even if the slider appears to be all the way to the left, it is critical you click it and move it to the left.**

31. [] Click the **Restore** button on the **Specify restore point** step
32. [] Click the **OK** button to restore database DB1 back to server.


32. [] Enter password: +++Pa$$w0rd+++
33. [] Click the **Next** button on the **Specify target Linux server connection credentials** step.
34. [] Keep the default settings and click the **Next** button on the **Specify Oracle settings** step.
35. [] Click the **Restore** button on the **Specify database files target location** step.
36. [] Click the **Yes** button to dismiss the unable to find some of the specified paths warning.
> Note: The validating... process can take up to 3 minutes, please have some patience.

37. [] Click the **OK** button to start the restore process.
> Note: The restore process will appear to be stuck at Mounting backup and 0% for up to 10 minutes, do not interrupt the process.
>
> Note: The complete restore can take up to 20 minutes, please have some patience.

38. [] Click the **OK** button.
39. [] Close the **Veeam Explorer for Oracle** window.
40. [] Launch **Oracle SQL Developer** from the Windows task bar (icon looks like a disk with a green arrow).
41. [] Expand the **Production Oracle** connection.
42. [] Enter password: +++tiger+++
43. [] Click the **OK** button.
44. [] Enter: +++select * from EMP+++ in the **Production Oracle** tab.
45. [] Click the **Run Script** button (icon looks like a notepad with a green arrow) or press the **F5** keyboard button.
46. [] Review the output result in the **Script Output** pane then close the **Oracle SQL Developer** window.
47. [] Click the **No** button to discard changes.

===

# Lab 6.4: Perform Microsoft Active Directory items recovery

1. [] Launch the **Remote Desktop Connection client** from the Windows task bar.
2. [] Enter computer name: +++VEEAM-DC01+++
3. [] Click the **Connect** button.
3. [] Enter password: +++Pa$$w0rd+++
4. [] Click the **OK** button.
5. [] Launch the **Server Manager** from the Windows task manager.
6. [] Click the **Tools** menu.
7. [] Select **Active Directory Users and Computers**.
8. [] Expand the **veeamlab.local** domain.
9. [] Select the **Users** organizational unit.
10. [] Right click the **testmail** user.
11. [] Select **Delete**.
12. [] Click the **Yes** button.
13. [] Minimize the **Remote Desktop Connection** window.
14. [] Expand the **Backup Active Directory** job.

14. [] Select the **VEEAM-DC01** virtual machine.
15. [] Click the **Application items** button on the **Backups** ribbon.
16. [] Select **Microsoft Active Directory**.
17. [] Keep the default settings and click the **Next** button on the **Restore Point** step.
18. [] Tick the **Do not show me this page again** check box.

18. [] Keep the default settings and click the **Next** button on the **Reason** step.
19. [] Click the **Finish** button on the **Summary** step.
20. [] Expand the **veeamlab.local** domain.
21. [] Click the **Compare with Production** button on the **Home** ribbon.
22. [] Click the **Show Changed Objects Only** button on the **Home** ribbon.
23. [] Expand **Users and Computers**.
24. [] Select the **Users** organizational unit.
25. [] Select the **testmail** user.
26. [] Click the **Restore objects** button on the **Objects** ribbon.
27. [] Select **Restore objects to VEEAM-DC01.veeamlab.local**.
28. [] Wait for the restore to complete then click the **OK** button.
29. [] Switch to the **Remote Desktop Connection client** window using the Windows task bar.
30. [] Select the **Users** organizational unit.
31. [] Click the **Refresh** button or press the **F5** keyboard button.
32. [] Verify the **testmail** user appears then close the **Remote Desktop Connection client** window.
33. [] Close the **Veeam Explorer for Microsoft Active Directory** window.

===

# Lab 6.5: Perform Microsoft SQL Server items recovery

1. [] Select the **VEEAM-SP01** virtual machine.
2. [] Click the **Application items** button on the **Backups** ribbon.
3. [] Select **Microsoft SQL Server**.
4. [] Keep the default settings and click the **Next** button on the **Restore Point** step.
5. [] Tick the **Do not show me this page again** check box.
6. [] Keep the default settings and click the **Next** button on the **Reason** step.
7. [] Click the **Finish** button on the **Summary** step.
8. [] Wait for the **Veeam Explorer for Microsoft SQL Server** window to load then select the **testdb** database.
9. [] Click the **Restore Database** button on the **Database** ribbon.
10. [] Select **Restore point-in-time to VEEAM-SP01\\SQLEXPRESS...**.
11. [] Select the **Restore to a specific point in time (requires transaction log backups)** radio button.
12. [] Move the **slider** all the way to the left (select the oldest point in time).
> Note: It may appear as if the slider is already in the most far point, make sure you click it and move it to the left regardless.

13. [] Click the **Restore** button.
14. [] Click the **OK** button to start the restore process.
> Note: The restore will take less than 3 minutes.

15. [] Click the **OK** button.
16. [] Close the **Veeam Explorer for Microsoft SQL Server** window.
17. [] Launch the **Remote Desktop Connection client** from the Windows task bar.
18. [] Enter computer name: +++VEEAM-SP01+++
19. [] Click the **Connect** button.
20. [] Leave user name as **VEEAMLAB\Administrator** and enter password: +++Pa$$w0rd+++.
21. [] Click the **OK** button.
22. [] Open the **Start menu** by moving the cursor to the bottom left corner then click the **Start** button when it appears.
> Note: If you are having issues opening the start menu, please ask your instructor for assistance.

23. [] Select the **Microsoft SQL Server Management Studio** tile.
24. [] Verify the server name is +++VEEAM-SP01\SQLEXPRESS+++ then click the **Connect** button.
25. [] Expand **Databases**.
26. [] Expand the **testdb** database
27. [] Expand **Tables**
28. [] Verify the **dbo.BuildVersion** table has been restored then close the **Microsoft SQL Server Management Studio** window.
29. [] Close the **Remote Desktop Connection** window.

===

# Lab 6.6: Guest files recovery

## Step 1: Perform Windows guest files recovery through the network

1. [] Launch the **File Explorer** from the Windows task bar.
2. [] Navigate to: +++\\\\veeam-dc01\\c$\\Important Files+++
3. [] Select the **invoice.docx** file.
4. [] Press the **CTRL + A** keyboard buttons to select all files.
5. [] Click the **Home** menu.
6. [] Click the **Delete** button.
7. [] Click the **Yes** button to permanently delete these 3 items.
8. [] Close the **File Explorer** window.
9. [] Select the **VEEAM-DC01** virtual machine.
10. [] Click the **Guest Files** button on the **Backup** ribbon.
11. [] Select **Microsoft Windows**.
12. [] Keep the default settings and click the **Next** button on the **Restore Point** step.
13. [] Tick the **Do not show me this page again** check box.
14. [] Click the **Next** button on the **Reason** step.
15. [] Click the **Finish** button on the **Summary** step.
16. [] Wait for the **Backup Browser** window to open then double click the **Important Files** folder.
17. [] Select the **quote.docx** file.
18. [] Click the **Restore** button on the **File** ribbon.
19. [] Select **Overwrite**.
> Note: Select option Keep if you do not want to overwrite the existing file with the restored one.

20. [] Click the **Show details** button.
21. [] Wait until the **Restore completed** text is displayed then click the **Close** button.
22. [] Close the **Backup Browser** window.

===

## Step 2: Perform Windows guest files recovery through VMware Tools (network-less)

1. [] Launch the **VMware Host Client** from the Windows task bar.
2. [] Enter:
 1. User name: +++root+++
 2. Password: +++Pa$$w0rd+++

3. [] Click the **Virtual Machines** text link in the **Navigator** pane.
4. [] Click the **VEEAM-DC01** virtual machine text link.
5. [] Click the **Edit** button.
6. [] Untick the **Connect** check box in the **Network Adapter 1** section.
7. [] Click the **Save** button.
> Note: The virtual machine is now disconnected from the network.
>
> Important: If the Backup Browser is still open, it is important that you close it. Because an RPC network connection was detected during the first session, failover to a networkless restore (VIX) will not be attempted.

8. [] Minimize the **VMware Host Client** window.
9. [] Verify the **VEEAM-DC01** virtual machine is still selected then click the **Guest Files** button on the **Backup** ribbon.
10. [] Select **Microsoft Windows**.
11. [] Keep the default settings and click the **Next** button on the **Restore Point** step.
12. [] Click the **Finish** button on the **Summary** step.
13. [] Wait for the **Backup Browser** window to open then double click the **Important Files** folder.
14. [] Select the **invoice.docx** file.
15. [] Click the **Restore** button on the **File** ribbon.
16. [] Select **Overwrite**.
> Note: Because the network has been disconnected from the VEEAM-DC01 virtual machine this process can take a few minutes while the network connection attempt times out, please have some patience.

17. [] Click the **Show details** button.
> Note: The text Restoring via vSphere guest interaction API will be displayed to confirm the network-less restore is performed via VMware Tools.

18. [] Wait until the **Restore completed** text is displayed then click the **Close** button.
> **Important: Do NOT close the Backup Browser window at this time.**

19. [] Minimize the **Backup Browser** window.
20. [] Switch back to the **VMware Host Client** window using the Windows task bar.
21. [] Verify the **VEEAM-DC01** virtual machine is still opened then click the **Edit** button.
22. [] Tick the **Connect** check box in the **Network Adapter 1** section.
23. [] Click the **Save** button.
> Note: The virtual machine is now once again connected to the network.

24. [] Close the **VMware Host Client** window.

===

## Step 3: Perform Windows guest files recovery using a mount point

1. [] Launch the **File Explorer** from the Windows task bar.
2. [] Navigate to the +++C:\\VeeamFLR+++ folder
> Important! If you closed the Backup Browser in this folder will be empty. Ask your instructor for assistance.

3. [] Double click the **VEEAM-DC01** folder (which contains a random ID).
4. [] Double click the **Volume1** folder.
5. [] Double click the **Important Files** folder.
6. [] Select the **market strategy.pptx** file.
7. [] Click the **Home** menu.
8. [] Select **Copy**.
9. [] Navigate to +++\\\\veeam-dc01\\c$\\Important Files+++.
10. [] Click the **Home** menu.
11. [] Select **Paste**.
12. [] Verify all three files are now present in the **\\\\veeam-dc01\\c$\\Important Files** folder then close the **File Explorer** window.
13. [] Switch back to the **Backup Browser** window using the Windows task bar.
14. [] Close the **Backup Browser** window.

===

## Step 4: Perform Linux guest files recovery

1. [] Expand the **Backup Oracle** job.
2. [] Select the **VEEAM-ORCL** virtual machine.
3. [] Click the **Guest Files** button on the **Backups** ribbon.
4. [] Select **Linux and other**.
> Note: Veeam’s multi-OS restore wizard enables you to recover guest OS files from several file systems for VMware vSphere and Microsoft Hyper-V – such as Linux, Unix, BSD, MacOS and many others.

5. [] Keep the default settings and click the **Next** button on the **Restore Point** step.
6. [] Tick the **Do not show me this page again** check box.
7. [] Cick the **Next** button on the **Reason** step.
8. [] Click the **Customize** button.
9. [] Click the **Choose...** button in the **Host** section.
10. [] Select **VEEAM-ESX**.
11. [] Click the **OK** button.
12. [] Select the **Use the following IP address** radio button.
13. [] Enter:
 1. IP address: +++10.0.3.201+++
 2. Subnet mask: +++255.255.255.0+++
 3. Default gateway: +++10.0.3.3+++

14. [] Click the **OK** button.
15. [] Click the **Finish** button on the **Helper Appliance** step.
> **Important: The Starting file-level restore helper appliance... text will be displayed while this appliance is deployed to the VEEAM-ESX host and configured on the fly. This process can take up to 4 minutes, please have some patience.**
>
> Note: For file-level recovery, Veeam Backup & Replication uses a special File Level Recovery Helper (FLR helper) – a small virtual appliance based on the stripped-down Linux kernel. Whenever you perform file-level restore, Veeam Backup & Replication automatically starts the appliance and mounts the VMDK files to the FLR appliance as virtual hard drives. VMDK files are mounted directly from backup files, without prior extraction of the backup content, which makes the restore process much faster compared to competitive solutions. You can then copy individual files and folders from VM disks to your local machine drive or a network share.

16. [] Wait for the **File Level Restore** window to open then expand **LVM**.
17. [] Expand **centos-root**.
18. [] Double click the **var** folder.
19. [] Double click the **log** folder.
20. [] Select the **boot.log** file.
21. [] Click the **Copy To** button on the **Home** ribbon.
22. [] Enter path to folder: +++C:\\Users\\Administrator.VEEAMINFRA\\Desktop+++
23. [] Click the **Restore** button.
24. [] Close the **File Level Restore** window.
25. [] Close the **Veeam Backup & Replication console** window and verify the **boot.log** file is present on the **desktop**.

---

# Congratulations!

You have completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
