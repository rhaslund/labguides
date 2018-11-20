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
2. [] Click the **VEEAM-VAO\VLAB1** text link.
3. [] Click the **Run** button to launch the lab so it can start loading in the background and will be ready for later steps in this lab exercise.
4. [] Verify the **vao testing only - active directory servers** lab group is already added due to it's status as **default lab group** then click the Next button on the **Choose Lab Groups** step.
5. [] Click the **Finish** button on the **Summary* step.

===

## Step 2: Inspect a pre-created custom script

1. [] Launch the **File Explorer** from the **Windows task bar**.
2. [] Expand **Local Disk (C:)**.
3. [] Select the **Install** folder in navigation pane.
4. [] Open the **datetime** Windows PowerShell script.
5. [] The first section, **Param**, defines Veeam Availability Orchestrator step parameters where data can be sent from Veeam
Availability Orchestrator into the script. Notice **Mandatory=$true** which means the script will be halted if those step parameters have not been defined in Veeam Availability Orchestrator. The **Add-Content** commands will write data into a folder, in this example c:\utils, which must exist. Otherwise, the command will fail. The **Write-Host** command will write to the **Failover Plan** report, allowing the script to provide information back into **Veeam Availability Orchestrator**. Close the **Notepad** window.
6. [] Let's create the c:\utils folder used by the script. In the **File Explorer** window, please click the **Left arrow** button in the top left corner to navigate back to root **C:\**.
7. [] Click the **Home** menu in the **File Explorer** window.
8. [] Click the **New folder** button.
9. [] Change the folder name from **New Folder** to +++utils+++ and press the **Enter** button on the keyboard.
10. [] Verify the folder name is **utils** and then close the **File Explorer** window.

===

# Step 3: Load custom script into VAO and add it as a custom step

1. [] 

---

# Congratulations!

You have successfully completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
