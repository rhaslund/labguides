Module 9: Documentation, Custom Scripts & Dashboards
---
**This lab is expected to last a maximum of 60 minutes including lab launch.**

# Lab 9.1: Create a new report template

1. [] Launch **Veeam Availability Orchestrator** from the desktop.
2. [] Enter:
 1. Username: +++siteadmin@vmce.lab+++
 2. Password: +++Pa%%w0rd+++

3. [] Click the **Login** button
>Note: Because the server was just started, the spinning icon may display for up to two minutes while services complete their startup.

4. [] Navigate to the **Report Templates** view.
5. [] Select **Veeam Default Template** in the **Templates** pane.
6. [] Click the **Clone** button.
7. [] Click the **Site Scope** drop down menu.
8. [] Select **Phoenix\SharePoint Administrators**
9. [] Enter New Template Name: +++VMCE Template+++
10. [] Click the **Clone** button.

===

# Lab 9.2: Customize the report template

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

# Lab 9.3: Modify an orchestration plan to utilize the new report template

1. [] Navigate to the **Orchestration Plans** view.
2. [] Select the **Tier1-SharePoint** plan.
3. [] Click the **Manage** button.
4. [] Select **Edit**.
5. [] Click the **Properties** button.
6. [] Click the **Next** button on the **Plan Name** step.
7. [] Click the **Next** button on the **RTO & RPO** step.
8. [] Click the **Veeam Default Template** text link.
9. [] Select **VMCE Template**.
10. [] Click the **OK** button.
11. [] Click the **Finish** button on the **Report Template** step.
12. [] Click the **Save** button.
13. [] Click the **Save** button without ticking the **Perform Plan Readiness Check now** check box.
14. [] Click the **Left arrow** button next to the **Edit Plan Tier1-SharePoint** text.

===

# Lab 9.4: Working with custom scripts

## Step 1: Prepare for later testing

1. [] Navigate to the **DataLabs** view.
2. [] Click the **VEEAM-VAO\VLAB1** text link.
3. [] Click the **Run** button to launch the lab so it can start loading in the background and will be ready for later steps in this lab exercise.
4. [] Verify the **vao testing only - active directory servers** lab group is already added due to its status as **default lab group** then click the Next button on the **Choose Lab Groups** step.
5. [] Click the **Finish** button on the **Summary** step.

===

## Step 2: Inspect a pre-created custom script

1. [] Launch the **File Explorer** from the **Windows task bar**.
2. [] Expand **Local Disk \(C:\)**.
3. [] Select the **Install** folder in the navigation pane.
4. [] Open the **datetime** Windows PowerShell script.
5. [] The first section, **Param**, defines Veeam Availability Orchestrator step parameters where data can be sent from Veeam
Availability Orchestrator into the script. Notice **Mandatory=$true** which means the script will be halted if those step parameters have not been defined in Veeam Availability Orchestrator. The **Add-Content** commands will write data into a folder, in this example c:\utils, which must exist. Otherwise, the command will fail. The **Write-Host** command will write to the **Failover Plan** report, allowing the script to provide information back into **Veeam Availability Orchestrator**. Close the **Notepad** window.
6. [] Let's create the c:\utils folder used by the script. In the **File Explorer** window, please click the **Left arrow** button in the top left corner to navigate back to root **C:\\**.
7. [] Click the **Home** menu in the **File Explorer** window.
8. [] Click the **New folder** button.
9. [] Change the folder name from **New Folder** to +++utils+++ and press the **Enter** button on the keyboard.
10. [] Verify the folder name is **utils** and then close the **File Explorer** window.

===

## Step 3: Load custom script into VAO and add it as a custom step

1. [] Click the **Administration** button in the top right corner.
2. [] Navigate to the **Plan Steps view**.
3. [] Click the **Add** button in the **Steps** pane.
4. [] Enter name: +++Date & Time+++.
5. [] Click the **Browse...** button.
6. [] Enter file name: +++C:\Install\datetime.ps1+++.
7. [] Click the **Open** button.
8. [] Click the **Next** button on the **Custom Script Step** step.
9. [] Click the **Next** button on the **Step Visibility** step.
10. [] Click the **Finish** button on the **Summary** step.
11. [] Click the **Exit Administration** button in the top left corner.
12. [] Navigate to the **Orchestration Plans** view.
13. [] Select the **Tier1-SharePoint** plan.
14. [] Click the **Manage** button.
15. [] Select **Edit**.
16. [] Select **SHAREPOINT** in the **Virtual Machines** pane.
17. [] Click the **Add** button in the **Steps** pane.
18. [] Tick the **Date & Time** check box.
19. [] Click the **Add** button.
20. [] Select the **Date & Time** step.
21. [] Select **Common Parameters** in the **Step Parameters** pane.
22. [] Click the **Test Action** drop-down menu.
23. [] Select **Execute**.
24. [] Modify number of **Retries** from **10** to +++0+++.
25. [] Click the **Save** button in the **Step Parameters** pane.
26. [] Tick the **Perform Plan Readiness Check now** check box.
27. [] Click the **Save** button.

===

## Step 4: Test failover plan

1. [] Select the **Tier1-SharePoint** plan.
2. [] Click the **Verify** button.
3. [] Select **Run Lab Test**.
4. [] Click the **Next** button on the **Lab** step.
5. [] Click the **Next** button on the **Reserve Lab** step.
6. [] Click the **Next** button on the **Keep Plan Running** step.
7. [] Click the **Finish** button on the **Summary** step.
8. [] Click the **Tier1-SharePoint** text link in the **Plan** column.
9. [] Select the **Tier1-SharePoint** plan.
10. [] Select **mission critical vms - sharepoint servers** in the **Plan Groups** pane.
11. [] Select **SHAREPOINT** in the **Virtual Machines** pane.
12. [] Select **Date & Time** in the **Steps** pane.
13. [] Follow the progress in the **Step Details** pane. The error message **Cannot process command** is a result of one or more missing mandatory parameters: **planName**.". This is because the script contains two mandatory parameters: **$planName** and **$planState**. To add the missing step parameters, click the **Administration** button in the top right corner.
14. [] Select **Date & Time** in the Steps pane.
15. [] Click the **Add** button in the **Step Parameters** pane.
16. [] Enter name: +++planName+++
17. [] Click the ***...*** button next to the **Default Value** text field.
18. [] Review the list of available variables and double-click on the **%plan_name%** variable.
19. [] Click the **Save** button.
20. [] Click the **Save** button in the **Step Parameters** pane.
21. [] Tick the **Globally push the new default values into all Plans on all Sites** check box.
22. [] Click the **Save** button.
23. [] Click the **Add** button in the **Step Parameters** pane.
24. [] Enter name: +++planState+++
25. [] Click the ***...*** button next to the ***Default Value*** text field.
26. [] Double-click the **%plan_state%** variable.
27. [] Click the **Save** button.
28. [] Click the **Save** button in the **Step Parameters** pane.
29. [] Tick the **Globally push the new default values into all Plans on all Sites** check box.
30. [] Click the **Save** button.
31. [] Click the **Exit Administration** button in the top left corner.
32. [] Select the **Tier1-SharePoint** plan.
33. [] Click the **Verify** button.
34. [] Select **Run Lab Test**.
35. [] Click the **Next** button on the **Lab** step.
36. [] Click the **Next** button on the **Reserve Lab** step.
37. [] Click the **Next** button on the **Keep Plan Running** step.
38. [] Click the **Finish** button on the **Summary** step.
39. [] Click the **Tier1-SharePoint** text link in the **Plan** column.
40. [] Select the **Tier1-SharePoint** plan.
41. [] Select **mission critical vms - sharepoint servers** in the **Plan Groups** pane.
42. [] Select **SHAREPOINT** in the **Virtual Machines** pane.
43. [] Select **Date & Time** in the **Steps** pane.
44. [] Wait for the **Date & Time** step execution to finish and launch **File Explorer** from the Windows task bar.
45. [] Expand **Local Disk (C:)** in the left side **Navigation** pane.
46. [] Select the **utils** folder in the left side **Navigation** pane.
47. [] Notice two files now exist in the folder: **vao_log.txt** and **vao_test.log**. Double-click on the **vao_test** text document.
48. [] Verify that the step parameters and variables have been properly passed from Veeam Availability Orchestrator into the script. The expected output is: **Plan name is Tier1-SharePoint and state is Testing Processing**. Close the **Notepad** window.
49. [] Close the **File Explorer** window.
50. [] Navigate to the **DataLabs** view.
51. [] Click the **Power Off** button.
52. [] Click the **Power Off** button to confirm powering off the DataLab.

===

# Lab 9.5: Veeam Availability Orchestrator dashboards

1. [] Navigate to the **Dashboard** view.
> Note: **Plan Execution** chart displays orchestration plan execution results: the number of halted plans, the number of plans completed successfully, the number of plans completed with warnings and the number of plans that have not run yet. The worst state of a plan execution is **Halted**. It means that the plan has stopped processing because of a critical error. 
> **Plan Readiness Check** chart represents the results of readiness check for all plans: the number of failed checks, the number of checks completed successfully, the number of checks completed with warnings and the number of plans that have not been checked yet. The worst state of a plan readiness check is **Failed**. It means that the plan is not in the ready-to-run state.
> **Plan Testing** chart provides the results of plan testing in a DataLab: the number of failed plan tests, the number of plan tests completed successfully, the number of plan tests completed with warnings and the number of plans that have not been tested yet. The worst state of a plan testing is **Failed**. It means that the test has stopped because of a critical error for a critical VM in the lab.

2. [] Notice that the **Plan Testing** dashboard shows one plan is in a never tested state. Click the **Plan Testing** dashboard.
3. [] Select the **Plan** that has never been tested.
4. [] Click the **Verify** button.
5. [] Select **Run Lab Test**.
6. [] Click the **Next** button on the **Lab** step.
7. [] Click the **Next** button on the **Reserve Lab** step.
8. [] Select **vao testing only – active directory servers**.
9. [] Click the **Add** button.
10. [] Click the **Next** button on the **Choose Lab Groups** step.
11. [] Click the **Next** button on the **Keep Plan Running** step.
12. [] Click the **Finish** button on the **Summary** step.
13. [] Click the **Tier1-Exchange** text link in the **Plan** column.
14. [] Wait for the **Plan** test to successfully complete - this can take up to 10 minutes. Once the **Plan** test is completed, navigate to the **Dashboard** view.
15. [] Verify that the **Plan Testing** dashboard is indicating all **Plans** are in a **Passed** state.

---

# Congratulations!

You have successfully completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
