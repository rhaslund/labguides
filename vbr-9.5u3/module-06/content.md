Module 6: Objects Recovery

---
**This lab is expected to last a maximum of 90 minutes including lab launch.**


# Lab 6.1: Perform Microsoft Exchange items recovery

1. [] Launch **Outlook Web Access** from the Windows task bar.
2. [] Enter:
 1. Username: +++administrator@veeamlab.local+++
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
14. [] Keep the default settings and click the **Next* button on the **Reason** step.
15. [] Click the **Finish** button on the **Summary** step.
> Note: The Veeam Explorer for Microsoft Exchange will launch now. It can also be launched manually from the Windows Start Menu.

16. [] Expand the **Mailbox Database** hierachy.
17. [] Expand the **testmail** mailbox.
18. [] Select the **Inbox** folder.
19. [] Select the **previously deleted e-mail** message.
20. [] Click the **Restore Items** button on the **Items** ribbon.
21. [] Select **Restore to...**.
22. [] Enter mailbox: ++testmail@veeamlab.local+++.
23. [] Select the **The following account** radio button.
24. [] Enter:
 1. User name: +++VMCELAB\Administrator+++
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

1. [] 

---

# Congratulations!

You have completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
