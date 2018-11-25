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

---

# Congratulations!

You have completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
