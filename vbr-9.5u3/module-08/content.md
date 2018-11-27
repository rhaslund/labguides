Module 8: Introduction to Agents

---
**This lab is expected to last a maximum of 70 minutes including lab launch.**


# Lab 8.1: Prepare Microsoft Active Directory

1. [] Launch **Remote Desktop Connection client** from the Windows task bar.
2. [] Enter computer name: ++VEEAM-DC01+++
3. [] Leave user name as **VEEAMLAB\Administrator** and enter password: +++Pa$$w0rd+++.
4. [] Click the **OK** button.
5. [] Launch the **Server Manager** from the Windows task bar.
6. [] Click on the **Tools** text link in the top right corner.
7. [] Select **Active Directory Users and Computers**.
8. [] Expand the **veeamlab.local** domain.
9. [] Select the **Computers** organizational unit.
10. [] Click the **Actions** menu.
11. [] Select **New**.
12. [] Select **Group**.
13. [] Enter group name: +++Veeam Agent protected servers+++
14. [] Click the **OK** button.
15. [] Select the **PHYSICAL** computer.
16. [] Click the **Actions** menu.
17. [] Select **Add to a group...**.
18. [] Enter object name: +++Veeam Agent protected servers+++.
19. [] Click the **OK** button.
> Note: If a new window entitled Name Not Found is displayed, you have incorrectly entered the group name. Click the Cancel button and correct the name, then click the OK button.

20. [] Verify that the **Add to Group** operation was successfully completed, then click the **OK** button.
21. [] Close the **Remote Desktop Connection** window.

===

# Lab 8.2: Setup Protection Group

===

# Lab 8.3: Create a Agent Backup Job

===

# Lab 8.4: Prepare Recovery Media for Bare Metal Recovery

===

Lab 8.5: Perform Bare Metal Recovery

---

# Congratulations!

You have completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
