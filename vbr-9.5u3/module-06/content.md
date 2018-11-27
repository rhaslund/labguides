Module 6: Objects Recovery

---
**This lab is expected to last a maximum of 90 minutes including lab launch.**


# Lab 6.1: Perform Microsoft Exchange items recovery

1. [] Launch **Outlook Web Access** from the Windows task bar.
2. [] Enter:
 1. Username: +++testmail@veeamlab.local+++
 2. Password: +++Pa$$w0rd+++

3. [] Click the **Sign In** button.
4. [] Click the **Delete** button on the most recent e-mail.
5. [] Select the **Deleted items** folder.
6. [] Click the **Yes** button to confirm deleting all the items and subfolders in the **Deleted items** folder.
7. [] Minimize the **Outlook Web Access** window.
8. [] Select **Disk** in the **Backups** section of the **Home** view.
9. [] Expand the **Backup AD & Exchange & SharePoint** job.
10. [] Select **VEEAM-EX01**.
11. [] Click the **Application Items** button on the **Backup** ribbon.
12. [] Select **Microsoft Exchange**.
13. [] Keep the default setting and click the **Next** button on the **Restore Point** step.
14. [] Keep the default settings and click the **Next** button on the **Reason** step.
15. [] Click the **Finish** button on the **Summary** step.
> Note: The Veeam Explorer for Microsoft Exchange will launch now. It can also be launched manually from the Windows Start Menu.

16. [] Expand the **Mailbox Database** hierachy.
17. [] Expand the **testmail** mailbox.
18. [] Select the **Inbox** folder.
19. [] Select the **previously deleted e-mail** message.
20. [] Click the **Restore Items** button on the **Items** ribbon.
21. [] Select **Restore to...**.
22. [] Enter mailbox: +++testmail@veeamlab.local+++.
23. [] Select the **The following account** radio button.
24. [] Enter:
 1. User name: +++VEEAMLAB\Administrator+++
 2. Password: +++Pa$$w0rd+++

25. [] Click the **Next** button.
26. [] Wait for the automatic mailbox server discovery to populate as +++veeam-ex01.veeamlab.local+++ then click the **Next** button.
> Note: Automatic discovery of the mailbox server (CAS) can take up to 2 minutes, please have some patience.

27. [] Keep the default settings and click the **Restore** button.
28. [] Click the **OK** button.
29. [] Close the **Veeam Explorer for Microsoft Exchange** window.
30. [] Switch to the **Outlook Web Access** window using the Windows task bar.
31. [] Select the **Inbox** folder.
32. [] Confirm the restored e-mail appears then close the **Outlook Web Access** window.

====

# Lab 6.2: Perform Microsoft SharePoint items recovery

1. [] Select **Disk** in the **Backup** section of the **Home** view.
2. [] Expand the **Backup AD & Exchange & SharePoint** backup job.
3. [] Select the **VEEAM-SP01** virtual machine.
4. [] Click the **Application Items** button on the **Backup** ribbon.
5. [] Select **Microsoft SharePoint**.
6. [] Select **http://veeam-sp01**.
7. [] Click the **Next** button on the **Site** step.
8. [] Select the **latest full backup** 
9. [] Click the **Next** button on the **Content Database** step.
10. [] Keep the default settings and click the **Next** button on the **Restore Reason** step.
11. [] Click the **Finish** button on the **Summary** step.
12. [] If prompted, click the **Yes** button to upgrade the database.
13. [] Expand **WSS_Content.mdf**.
14. [] Expand **Home**.
15. [] Expand **Content**.
16. [] Check which folder containts the following three files: **invoice.docx**, **market strategy.pptx** and **quote.docx** then click the **folder**.
> Note: The files should be in either the Documents or Shared Documents list.

17. [] Click the **Restore Library** button on the **Library** ribbon.
18. [] Select the **The following account** radio button.
19. [] Enter:
 1. Account: +++VEEAMLAB\Administrator+++
 2. Password: +++Pa$$w0rd+++
 
20. [] Select the **Restore to the following list** radio button.
21. [] Enter: ++Restored Docs+++.
22. [] Click the **Next** button.
23. [] Click the **Restore** button.
24. [] Click the **OK** button.
25. [] Close the **Veeam Explorer for Microsoft SharePoint** window.
26. [] Launch the **Remote Desktop Connection** client from the Windows task bar.
27. [] Enter computer name: ++VEEAM-SP01+++
28. [] Leave user name as **VEEAMLAB\Administrator** and enter password: +++Pa$$w0rd+++.
29. [] Click the **OK** button.
30. [] Open the **Start menu** by moving the cursor to the bottom left corner then click the **Start** button when it appears.
> Note: If you are having issues opening the start menu, please ask your instructor for assistance.

31. [] Launch **Internet Explorer** using the tile.
32. [] Browse to +++http://veeam-sp01+++
33. [] Verify the **Restored Docs** list appear under **Recent**.
34. [] Close the **Remote Desktop Connection** window.

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
9. [] Click the **Run Script** button (icon looks like a notepad with a green arrow).
10. [] Review the output result in the **Script Output** pane then expand **Tables (Filtered)**.
11. [] Right click the **EMP** table.
12. [] Select **Table**.
13. [] Select **Drop...**.
14. [] Click the **Apply** button
15. [] Click the **OK** button.
16. [] Click the **Run Script** button (icon looks like a notepad with a green arrow).
> Note: Since the table has been removed, an error message will be shown in the output window at the bottom
on the tab.

17. [] Close the **Oracle SQL Developer** window.
18. [] Click the **No** button.
19. [] Select **Disk** in the **Backups** section of the **Home** view.
20. [] Expand the **Backup ORCL** job.
21. [] Right click the **VEEAM-ORCL** virtual machine.
22. [] Select **Restore application items**.
23. [] Select **Oracle databases**.
24. [] Click the **Next** button.
25. [] Keep the default settings and click the **Next** button on the **Reason** step.
26. [] Click the **Finish** button.
27. [] Wait for the **Veeam Explorer for Oracle** window to load then select the **DB1** database.
28. [] Click the **Restore Database** button on the **Home** ribbon.
29. [] Select **Restore point-in-time state to VEEAM-ORCL**.
30. [] Select the **Restore to a specific point in time (requires redo log backups)** radio button.
31. [] Move the **slider** all the way to the left (select the oldest point in time available).
32. [] Click the **Next** button.
32. [] Enter:
 1. Username: +++oracle+++
 2. Password: +++Pa$$w0rd+++

33. [] Click the **Next** button.
34. [] Click the **Next** button.
35. [] Click the **Restore** button.
36. [] Click the **Yes** button.
37. [] Click the **OK** button.
38. [] Close the **Veeam Explorer for Oracle** window.
39. [] Launch **Oracle SQL Developer** from the Windows task bar (icon looks like a disk with a green arrow).
40. [] Expand the **Production Oracle** connection.
41. [] Enter:
 1. Username: +++scott+++
 3. Password: +++tiger+++

42. [] Click the **OK** button.
43. [] Enter: +++select * from EMP+++ in the **Production Oracle** tab.
44. [] Click the **Run Script** button (icon looks like a notepad with a green arrow).
45. [] Review the output result in the **Script Output** pane then close the **Oracle SQL Developer** window.
46. [] Click the **No** button.

===

# Lab 6.4: Perform Microsoft Active Directory items recovery

1. [] Launch the **Remote Desktop Connection client** from the Windows task bar.
2. [] Enter computer name: ++VEEAM-DC01+++
3. [] Leave user name as **VEEAMLAB\Administrator** and enter password: +++Pa$$w0rd+++.
4. [] Click the **OK** button.
5. [] Launch the **Server Manager** from the Windows task manager.
6. [] Select **AD DS** in the left hand navigation pane.
7. [] Right click **VEEAM-DC01**.
8. [] Select **Active Directory Users and Computers**.
9. [] Expand the **veeamlab.local** forest.
10. [] Select the **Users** organizational unit.
11. [] Right click the **testmail** user.
12. [] Select **Delete**.
13. [] Click the **Yes** button.
14. [] Minimize the **Remote Desktop Connection** window.
15. [] Select **Disk** in the **Backups** section of the **Home** view.
16. [] Expand the **Backup AD & Exchange & SharePoint** job.
17. [] Select the **VEEAM-DC01** virtual machine.
18. [] Click the **Restore application items** button on the **Backups** ribbon.
19. [] Select **Microsoft Active Directory**.
20. [] Keep the default settings and click the **Next** button on the **Restore Point** step.
21. [] Keep the default settings and click the **Next** button on the **Reason** step.
22. [] Click the **Finish** button on the **Summary** step.
23. [] Expand the **veeamlab.local** forest.
24. [] Click the **Compare All Objects** button on the **Home** ribbon.
25. [] Click the **Show Changed Objects Only** button on the **Home** ribbon.
26. [] Expand **Users and Computers**.
27. [] Select the **Users** organizational unit.
28. [] Right click the **testmail** user.
29. [] Select **Restore to VEEAM-DC01.veeamlab.local**.
30. [] Watch the restore process then click the **OK** button.
31. [] Switch to the **Remote Desktop Connection client** window using the Windows task bar.
32. [] Click the **Refresh** button.
33. [] Verify the **testmail** user appears then close the **Remote Desktop Connection client** window.
34. [] Close the **Veeam Explorer for Microsoft Active Directory** window.

===

# Lab 6.5: Perform Microsoft SQL Server items recovery

1. [] Select **Disk** in the **Backups** section of the **Home** view.
2. [] Expand the **Backup AD & Exchange & SharePoint** job.
3. [] Select the **VEEAM-SP01** virtual machine.
3. [] Click the **Restore application items** button on the **Backups** ribbon.
4. [] Select **Microsoft SQL Server**.
5. [] Click the **Next** button.
6. [] Keep the default settings and click the **Next** button on the **Reason** step.
7. [] Click the **Finish** button on the **Summary** step.
8. [] Wait for the **Veeam Explorer for Microsoft SQL Server** window to load then expand the **SQLEXPRESS** database.
9. [] Right click the **testdb** database.
10. [] Select **Restore point-in-time state to VEEAM-SP01\\SQLEXPRESS**
11. [] Select the **Restore to a specific point in time (requires transaction log backups)** radio button.
12. [] Move the **slider** all the way to the left (select the oldest restore point).
13. [] Click the **Restore** button.
14. [] Click the **OK** button.
15. [] Click the **OK** button.
16. [] Close the **Veeam Explorer for Microsoft SQL Server** window.
17. [] Launch the **Remote Desktop Connection client** from the Windows task bar.
18. [] Enter computer name: ++VEEAM-SP01+++
19. [] Leave user name as **VEEAMLAB\Administrator** and enter password: +++Pa$$w0rd+++.
20. [] Click the **OK** button.
21. [] Open the **Start menu** by moving the cursor to the bottom left corner then click the **Start** button when it appears.
> Note: If you are having issues opening the start menu, please ask your instructor for assistance.

22. [] Select the **Microsoft SQL Server Management Studio** tile.
23. [] Verify the server name is **VEEAM-SP01\SQLEXPRESS** then click the **Connect** button.
24. [] Expand **Databases**.
25. [] Expand the **testdb** database
26. [] Expand **Tables**
27. [] Verify the **dbo.BuildVersion** table has been restored then close the **Microsoft SQL Server Management Studio** window.
28. [] Close the **Remote Desktop Connection** window.

===

# Lab 6.6: Guest files recovery

## Step 1: Perform Windows guest files recovery

1. [] Launch the **File Explorer** from the Windows task bar.
2. [] Navigate to: +++\\\\veeam-dc01\\c$\\Important Files+++
3. [] Select **all the files** in this folder.
4. [] Right click on **the selected files**.
5. [] Select **Delete**.
6. [] Click the **Yes** button.
7. [] Close the **File Explorer** window.

8. [] Select **Disk** in the **Backups** section of the **Home** view.
9. [] Expand the **Backup AD & Exchange & SharePoint** job.
10. [] Select the **VEEAM-DC01** virtual machine.
11. [] Click the **Guest Files** button on the **Backup** ribbon.
12. [] Select **Microsoft Windows**.
13. [] Keep the default settings and click the **Next** button on the **Restore Point** step.
14. [] Keep the default settings and click the **Next** button on the **Reason** step.
15. [] Click the **Finish** button on the **Summary** step.
16. [] Double click the **Important Files** folder.
17. [] Select **invoice.docx**.
18. [] Click the **Restore** button on the **File** ribbon.
19. [] Select **Overwrite**.
> Note: Select option Keep if you do not want to overwrite the existing file with the restored one.

20. [] Click the **Show details** button.
21. [] Wait until the **Restore completed** text is displayed then click the **Close** button.
22. [] Launch the **VMware vSphere Client** from the Windows task bar.
23. [] Enter:
 1. User name: +++root+++
 2. Password: +++Pa$$w0rd+++

24. [] Click the **Login** butto.
25. [] Expand the **VEEAM-ESX** host.
26. [] Expand the **Production** resource pool.
27. [] Select the **VEEAM-DC01** virtual machine.
28. [] Click the **Edit Settings** text link in the **Commands** pane.
29. [] Select **Network adapter 1**.
30. [] Untick the **Connected** check box.
31. [] Click the **OK** button.
> Important: If the Backup Browser is still open, it is important that you close it. Because an RPC network connection was detected during the first session, failover to a networkless restore (VIX) will not be attempted.

32. [] Select the **VEEAM-DC01** virtual machine.
33. [] Click the **Guest Files** button on the **Backup** ribbon.
34. [] Select **Microsoft Windows**.
35. [] Keep the default settings and click the **Next** button on the **Restore Point** step.
36. [] Keep the default settings and click the **Next** button on the **Reason** step.
37. [] Click the **Finish** button on the **Summary** step.
38. [] Double click the **Important Files** folder.
39. [] Select **invoice.docx**.
40. [] Click the **Restore** button on the **File** ribbon.
41. [] Select **Overwrite**.
> Note: Select option Keep if you do not want to overwrite the existing file with the restored one.

42. [] Click the **Show details** button.
43. [] Wait until the **Restore completed** text is displayed then switch to the **VMware vSphere Client** window
> Important: Do NOT close the Backup Browser window at this time.

44. [] Select the **VEEAM-DC01** virtual machine.
45. [] Tick the **Connected** check box.
46. [] Click the **OK** button.
47. [] Launch the **File Explorer** from the Windows task bar.
48. [] Navigate to the **C:\\VeeamFLR** folder
> Important! If you stopped the Restore Wizard in substep 36 of this module this folder will be empty. Launch it again by repeating substeps 25-36 of this module OR ask your instructor for assistance

49. [] Double click the **VEEAM-DC01** folder (which contains a random ID).
50. [] Double click the **Volume1** folder.
51. [] Right click the **market strategy.pptx** file.
52. [] Select **Copy**.
53. [] Navigate to **\\\\veeam-dc01\\c$\\Important Files**.
54. [] Right click inside the **Important Files** folder.
55. [] Select **Paste**.
56. [] Verify all three files are present in the **\\\\veeam-dc01\\c$\\Important Files** folder then close the **File Explorer** window.
57. [] Close the **VMware vSphere Client** window.
58. [] Close the **Backup Browser** window.

===

## Step 2: Perform Linux guest files recovery

1. [] Select **Disk** in the **Backups** section of the **Home** view.
2. [] Expand the **Backup ORCL** job.
3. [] Select the **VEEAM-ORCL** virtual machine.
3. [] Click the **Guest Files** button on the **Backups** ribbon.
4. [] Select **Linux**.
> Note: Veeam’s multi-OS restore wizard enables you to recover guest OS files from several file systems for VMware vSphere and Microsoft Hyper-V – such as Linux, Unix, BSD, MacOS and many others.

5. [] Keep the default settings and click the **Next** button on the **Restore Point** step.
6. [] Keep the default settings and click the **Next** button on the **Reason** step.
7. [] Click the **Customize** button.
8. [] Click the **Choose...** button in the **Host** section.
9. [] Select **VEEAM-ESX**.
10. [] Click the **OK** button.
11. [] Click the **Choose...** button in the **Resource Pool** section.
12. [] Expand the **VEEAM-ESX** host.
13. [] Select the **Production** resource pool.
14. [] Click the **OK** button.
15. [] Select the **Use the following IP address** radio button.
16. [] Enter:
 1. IP address: +++10.0.3.201+++
 2. Subnet mask: +++255.255.255.0+++
 3. Default gateway: +++10.0.3.3+++

17. [] Click the **OK** button.
18. [] Click the **Finish** button on the **Helper Appliance** step.
> Note: For file-level recovery, Veeam Backup & Replication uses a special File Level Recovery Helper (FLR helper) – a small virtual appliance based on the stripped-down Linux kernel. Whenever you perform file-level restore, Veeam Backup & Replication automatically starts the appliance and mounts the VMDK files to the FLR appliance as virtual hard drives. VMDK files are mounted directly from backup files, without prior extraction of the backup content, which makes the restore process much faster compared to competitive solutions. You can then copy individual files and folders from VM disks to your local machine drive or a network share.

19. [] Expand **LVM**.
20. [] Expand **centos-root**.
20. [] Double click the **var** folder.
21. [] Double click the **log** folder.
22. [] Select the **boot.log** file.
23. [] Click the **Copy To** button on the **Home** ribbon.
24. [] Enter path to folder: +++C:\\Users\\Administrator.VEEAMINFRA\\Desktop+++
25. [] Click the **Restore** button.
26. [] Close the **File Level Restore** window.
27. [] Verify the **boot.log** file is present on the **desktop** then close the **Veeam Backup & Replication console** window.

---

# Congratulations!

You have completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
