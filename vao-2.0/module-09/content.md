Module 9: Documentation, Custom Scripts & Dashboards
---
**This lab is expected to last a maximum of X minutes including lab launch.**

# Lab 9.1: Create a new report template

1. [] Launch **Veeam Availability Orchestrator** from the desktop.
2. [] Enter:
 1. Username: +++siteadmin@vmce.lab+++
 2. Password: +++Pa%%w0rd+++

3. [] Click the ***Login*** button
>Note: Because the server was just started, the spinning icon may display for up to two minutes while services complete their startup.

4. [] Navigate to the **Report Templates** view.
5. [] Select **Veeam Default Template** in the **Templates** pane.
6. [] Click the **Clone** button.
7. [] Enter New Template Name: +++VMCE Template+++
8. [] Click the **Clone** button.

===

# Lab 9.2: Customize report template

1. [] Select the newly created **VMCE Template** in the **Templates** pane.
2. [] Click the **Edit** button.
3. [] Wait for **Microsoft Word** to launch. When prompted, enter:
 1. Username: +++siteadmin@vmce.lab+++
 2. Password: +++Pa%%w0rd+++

4. [] Click the **OK** button.
5. [] Ignore the warning about regions that overlap and click the **OK** button.
6. [] Click the **View** tab on the Microsoft Word ribbon.
7. [] Select **Edit Document**.
8. [] Select the Veeam logo in the Word document.
9. [] Press the **Delete** button on your keyboard.
10. [] Click the **Insert** tab on the Microsoft Word ribbon.
11. [] Click the **Pictures** button.
12. [] Enter file name: +++C:\Install\logo.jpg+++
13. [] Click the **Insert** button.
14. [] Close the **Microsoft Word** window.
15. [] Click the **Save** button to confirm saving changes to **VMCE template**.
16. [] Select the **Veeam Default Template** in the Templates pane.
17. [] Select the **VMCE Template** in the **Templates** pane and notice that the logo is now updated.

===

# Lab 9.3: Modify orchestration plans to utilize the new report template

1. [] Navigate to the **Orchestration Plans** view.
2. [] Select the **Tier1-Exchange** plan.
3. [] Click the **Manage** button.
4. [] Select **Disable**.
5. [] Click the **Manage** button.
6. [] Select **Edit**.
7. [] Click the **Properties** button.
8. [] Click the **Next** button on the **Plan Name** step.
9. [] Click the **Next** button on the **RTO & RPO** step.
10. [] Click the **Veeam Default Template** text link.
11. [] Select **VMCE Template**.
12. [] Click the **OK** button.
13. [] Click the **Finish** button on the **Report Template** step.
14. [] Click the **Save** button.
15. [] Click the **Save** button without ticking the **Perform Plan Readiness Check now** check box.
16. [] Click the **Left arrow** button next to the **Edit Plan Tier1-Exchange** text.
17. [] Select the **Tier1-SharePoint** plan.
18. [] Click the **Manage** button.
19. [] Select **Edit**.
20. [] Click the **Properties** button.
21. [] Click the **Next** button on the **Plan Name** step.
22. [] Click the **Next** button on the **RTO & RPO** step.
23. [] Click the **Veeam Default Template** text link.
24. [] Select **VMCE Template**.
25. [] Click the **OK** button.
26. [] Click the **Finish** button on the **Report Template** step.
27. [] Click the **Save** button.
28. [] Click the **Save** button without ticking the **Perform Plan Readiness Check now** check box.
29. [] Click the **Left arrow** button next to the **Edit Plan Tier1-SharePoint** text.

===

# Lab 9.4: Working with custom scripts

## Step 1: Prepare for later testing

1. [] Navigate to the **DataLabs** view.

---

# Congratulations!

You have successfully completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
