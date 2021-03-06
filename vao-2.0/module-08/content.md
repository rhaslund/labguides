Module 8: Working with Orchestration Plans
---
**This lab is expected to last a maximum of 60 minutes including lab launch.**

# Lab 8.1: Enable a template job

1. [] Launch **Veeam Availability Orchestrator** from the desktop.
2. [] Enter:
 1. Username: +++siteadmin@vmce.lab+++
 2. Password: +++Pa%%w0rd+++

3. [] Click the **Login** button.
>Note: Because the server was just started, the spinning icon may display for up to two minutes while services complete their startup.

4. [] Click the **Administration** button in the top right corner.
5. [] Navigate to the **Plan Components** view.
6. [] Click the **Template Jobs** tab.
7. [] Tick the **VEEAM-VAO\Template Backup Job for VAO** check box.
8. [] Click the **Include** button in the **Template Jobs** pane.
9. [] Click the **Exit Administration** button in the top left corner.
10. [] Click the **Site Administrator VAO** text link in the top right corner.
11. [] Select **Logout**.

===

# Lab 8.2: Create a orchestration plan

1. [] Enter:
 1. Username: +++planauthor@vmce.lab+++
 2. Password: +++Pa%%w0rd+++
2. [] Click the **Login** button.
1. [] Navigate to the **Orchestration Plans** view.
2. [] Click the **Manage** button.
3. [] Select **New**.
4. [] Enter:
 1. Plan name: +++Tier1-SharePoint+++
 2. Description: +++Orchestration Plan for SharePoint servers+++
 3. Contact name: +++John Doe+++
 4. Contact email: +++administrator@vmce.lab+++

5. [] Click the **Next** button on the **Plan Name** step.
8. [] Keep the default selection of **Failover** and click the **Next** button on the **Plan Type** step.
9. [] Select **Mission Critical VMs - Sharepoint Servers**.
10. [] Click the **Add** button.
11. [] Click the **Next** button on the **VM Groups** step.
12. [] Keep the defaults and click the **Next** button on the **VM Recovery Options** step.
13. [] Select **Ping VM Network**.
14. [] Click the **Add** button.
15. [] Click the **Next** button on the **VM Steps** step.
16. [] Keep the defaults and click the **Next** button on the **Protect VM Groups** step.
17. [] Increase the **Target RPO** to: +++48+++ hours.
17. [] Click the **Next** button on the **RTO & RPO** step.
18. [] Keep the defaults and click the **Next** button on the **Report Template** step.
19. [] Keep the defaults and click the **Next** button on the **Report Scheduling** step.
20. [] Untick the **Run Readiness Check after Plan creation** check box.
21. [] Click the **Next** button on the **Readiness Check** step.
22. [] Click the **Finish** button on the **Summary** step.

===

# Lab 8.3: Perform initial readiness check

1. [] Select the newly created **Tier1-SharePoint** plan.
> Note: Do not click the Tier1-SharePoint text link.

2. [] Click the **Verify** button.
3. [] Select **Run Readiness Check**.
4. [] Click the **OK** button.
5. [] Confirm that the state has changed to **Verified (passed check)**, then click the **View Reports** button.
6. [] Select **Readiness Check**.
7. [] Click the **Tier1-SharePoint** text link with the **Readiness Check** type.
8. [] Click the **Open** button on the yellow download bar at the bottom of the **Internet Explorer** window.
9. [] Wait for the download to complete and click the **Open** button on the yellow download bar at the bottom of the **Internet Explorer** window.
10. [] Scroll down to the **Contents** page.
11. [] Click the **Plan Group Details** text link.
12. [] Review the **Plan Group Details** results and close the **Adobe Acrobat Reader** window.

===

# Lab 8.4: Customizing a orchestration plan

1. [] Navigate to the **Orchestration Plans** view.
2. [] Select the newly created **Tier1-SharePoint** plan.
> Note: Do not click the Tier1-SharePoint text link.

3. [] Click the **Manage** button.
4. [] Select **Edit**.
5. [] Select the **SHAREPOINT** virtual machine.
6. [] Click the **Add** button in the **Steps** pane.
7. [] Tick the **Shutdown Source VM** check box.
8. [] Scroll down until **Verify SQL Port** is visible.
9. [] Tick the **Verify SQL Port** check box.
10. [] Tick the **Verify SQL Database** check box.
11. [] Tick the **Verify SharePoint URL** check box.
12. [] Click the **Add** button.
13. [] Select **Shutdown Source VM** in the **Steps** pane.
14. [] Click the **Up arrow** button in the **Steps** pane until **Shutdown Source VM** is the first step listed.
15. [] Select **Verify SQL Database** in the **Steps** pane.
16. [] Select **Windows Credentials** in the **Step Parameters** pane.
17. [] Click the **NONE** text link under **Default Value**.
18. [] Select the **administrator@vmce.lab** credential.
19. [] Click the **OK** button.
20. [] Select **Verify SharePoint URL** in the **Steps** pane.
21. [] Select **Windows Credentials** in the **Step Parameters** pane.
22. [] Click the **NONE** text link under **Default Value**.
23. [] Select the **administrator@vmce.lab** credential.
24. [] Click the **OK** button.
25. [] Select **SharePoint URL** in the **Step Parameters** pane.
26. [] Enter +++http://%vm_fqdn%+++ into the **Default Value** text box.
27. [] Click the **Save** button under the **Edit Plan Tier1-SharePoint** text.
28. [] Tick the **Perform Plan Readiness Check now** check box.
29. [] Click the **Save** button.

===

# Lab 8.5: Test the orchestration plan

1. [] Verify the State column of the **Tier1-SharePoint** plan is in **Verified (passed check)** state. Select the **Tier1-SharePoint** plan.
2. [] Click the **Verify** button.
3. [] Select **Run DataLab Test**.
4. [] Verify the **VEEAM-VAO\VLAB1** is **Powered Off** and click the **Next** button on the **DataLab** step.
5. [] Keep the default settings and click the **Next** button on the **Power Options** step.
6. [] Notice that the **VAO Testing Only - Active Directory Servers** lab group has already been added and is greyed out. This is because an administrator has added this lab group as a **default lab group**. Click the **Next** button on the **Choose Lab Groups** step.
7. [] Click the **Finish** button on the **Summary** step.
8. [] Navigate to the **DataLabs** view.
9. [] Click the **VEEAM-VAO\VLAB1** text link in the **Lab** column.
10. [] Select the **VAO Testing Only - Active Directory Servers** lab group.
11. [] Select the **DC02** virtual machine.
> Note: It can take up to 6 minutes to fully start the Lab Appliance, please have some patience.

12. [] Wait for all steps of the **DC02** virtual machine to reach a status of **Completed** with a green checkmark (scroll left if the **Plan** is not visible).
> Note: It can take up to 8 minutes to complete all tests of the DC02 virtual machine, please have some patience.

13. [] Select the **Tier1-SharePoint** plan.
14. [] Select **Mission Critical VMs - SharePoint Servers** in the **Plan Group** pane.
15. [] Select **SHAREPOINT** in the **Virtual Machines** pane.
16. [] Click the **VM Console** button in the **Virtual Machines** pane.
17. [] A new tab opens in **Internet Explorer** displaying the virtual machine console of the **SHAREPOINT** server running inside the DataLab. Close the **VM Console** tab in **Internet Explorer**.
18. [] Wait for all steps of the **SHAREPOINT** virtual machine to reach a status of **Completed** with a green checkmark and click the **Left arrow** next to the **Lab Details VEEAM-VAO\VLAB1** text.
> Note: The Shutdown Source VM step will be in a Skipped status since this is a test and not a real failover.

19. [] Notice that the **VEEAM-VAO\VLAB1** DataLab is in the **Powered Off** state because the lab test has completed. Navigate to the **Orchestration Plans** view.

===

# Lab 8.6: Launch orchestration plan

1. [] Verify that the **Tier1-SharePoint** plan **State** column displays **Verified (passed test and check)** and select the **Tier1-SharePoint** plan.
> Note: While you can force a orchestration plan to launch even if it is not enabled, it is best practice to enable a orchestration plan once it has been created, tested and deemed ready for use during a disaster.

2. [] Click the **Manage** button.
3. [] Select **Enable**.
4. [] Click the **Launch** button.
5. [] Select **Run**.
6. [] Enter password: +++Pa%%w0rd+++
7. [] Click the **Next** button on the **Enter Credentials** step.
8. [] Keep the default settings and click the **Next** button on the **Restore Point** step.
9. [] Verify the action is **Failover** and then click the **Finish** button on the **Summary** step.
10. [] Click the **Tier1-SharePoint** text link in the **Plan** column.
11. [] Select **Mission Critical VMs - SharePoint Servers** in the **Plan Group** pane.
12. [] Select **SHAREPOINT** in the **Virtual Machines** pane.
13. [] Wait for all steps to reach the **Completed** status and then click the **Left arrow** button next to the **Plan Details: Tier1-SharePoint** text.

===

# Lab 8.7: Undo failover

1. [] Select the **Tier1-SharePoint** plan.
2. [] Click the **Launch** button.
3. [] Select **Undo**.
4. [] Enter password: +++Pa%%w0rd+++.
5. [] Click the **Next** button on the **Enter Credentials** step.
6. [] Verify the action is **Undo Failover (Force)** and then click the **Finish** button on the **Summary** step.
7. [] Click the **Tier1-SharePoint** text link in the **Plan** column.
8. [] Select **Mission Critical VMs - SharePoint Servers** in the **Plan Group** pane.
9. [] Select **SHAREPOINT** in the **Virtual Machines** pane.
10. [] Select **Process Replica VM** in the **Steps** pane.
11. [] Wait for the **Step Details** pane to display the following step: **Process Replica VM execution finished**. Verify in the top left corner that **Undo Failover** displays a green checkmark, that the status is **Complete**, that there are no errors or warnings, and then click the **Left arrow** button.
> Note: This process can take up to 4 minutes, please have some patience.

12. [] Select the **Tier1-SharePoint** plan.
13. [] Notice that the **State** column displays that the **Tier1-SharePoint** plan is in the **Undo Failover** state and click the **Manage** button.
14. [] Select **Reset**.
15. [] Enter password: +++Pa%%w0rd+++
16. [] Click the **Next** button on the **Enter Credentials** step.
17. [] Keep the default setting and click the **Next** button on the Reset Actions step.
18. [] Keep the default setting and click the **Next** button on the **Readiness Check** step.
19. [] Click the **Finish** button on the **Summary** step.
> Note: Notice that resetting an orchestration plan changes the plan from enabled to disabled.

20. [] Click the **Plan Author** text link in the top right corner.
21. [] Select **Logout**.

===

# Lab 8.8: Create a second orchestration plan and chain with the first plan

## Step 1: Create a second orchestration plan

1. [] Enter
 1. Username: +++siteadmin@vmce.lab+++
 2. Password: +++Pa%%w0rd+++
 
2. [] Click the **Login** button.
3. [] Navigate to the **Orchestration Plans** view.
4. [] Click the **Manage** button.
5. [] Select **New**.
6. [] Keep the default selection of the **Default** scope and click the **Next** button on the **Scope** step.
7. [] Enter:
 1. Plan name: +++Tier1-Exchange+++
 2. Description: +++Orchestration Plan for Exchange servers+++
 3. Contact name: +++John Doe+++
 4. Contact email: +++administrator@vmce.lab+++

8. [] Click the **Next** button on the **Plan Name** step.
9. [] Select the **Restore** radio button.
10. [] Click the **Next** button on the **Plan Type** step.
11. [] Select **DR site**.
12. [] Click the **Next** button on the **Recovery Location** step.
13. [] Select **Mission Critical VMs - Exchange Servers**.
14. [] Click the **Add** button.
15. [] Click the **Next** button on the **VM Groups** step.
16. [] Keep the default settings and click the **Next** button on the **VM Recovery Options** step.
17. [] Hold the keyboard **CTRL** button and select the following items: **Ping VM Network**, **Shutdown Source VM**, **Verify Exchange Services** and **Verify Exchange MAPI Connectivity**.
18. [] Click the **Add** button.
19. [] Select **Shutdown Source VM** in the **Steps** pane.
20. [] Click the **Up arrow** button in the **Steps** pane until **Shutdown Source VM** is the first step listed.
> Note: The order of the items should be:
> 
> Shutdown Source VM
>
> Restore VM
>
> Check VM Heartbeat
>
> Ping VM Network
>
> Verify Exchange Services
>
> Verify Exchange MAPI Connectivity

21. [] Click the **Next** button on the **VM Steps** step.
22. [] Tick the **Override Credentials** check box.
23. [] Click the **Choose...** text link.
24. [] Select the **administrator@vmce.lab** credential.
25. [] Click the **OK** button.
26. [] Click the **Next** button on the **Choose Credentials** step.
27. [] Keep the default settings and click the **Next** button on the **Protect VM Groups** step.
28. [] Increase the **Target RPO** to +++48+++ hours.
29. [] Click the **Next** button on the **RTO & RPO** step.
30. [] Keep the default settings and click the **Next** button on the **Report Template** step.
31. [] Keep the default settings and click the **Next** button on the **Report Scheduling** step.
32. [] Untick the **Run Readiness Check after Plan creation** check box.
33. [] Click the **Next** button on the **Readiness Check** step.
34. [] Click the **Finish** button on the **Summary** step.
35. [] Select the **Tier1-Exchange** plan.
36. [] Click the **Manage** button.
37. [] Select **Enable**.

===

## Step 2: Chain orchestration plans

1. [] Select the **Tier1-SharePoint** plan.
2. [] Click the **Launch** button.
3. [] Select **Schedule**.
4. [] Enter password: +++Pa%%w0rd+++
5. [] Click the **Next** button on the **Enter Credentials** step.
6. [] Tick the **Enable Scheduled execution for this Plan** check box.
7. [] Select the **Schedule after** radio button.
8. [] Click the **Choose a Plan...** text link.
9. [] Select **Tier1-Exchange** in the **Available Plans** pane.
> Note: If the list of available plans is empty, you forgot to enable the Tier1-Exchange Orchestration Plan at the end of step 1.

10. [] Click the **OK** button.
11. [] Click the **Next** button on the **Options** step.
12. [] Click the **Finish** button on the **Summary** step.
13. [] Select the **Tier1-Exchange** plan.
14. [] Click the **Launch** button.
15. [] Select **Run**.
16. [] Enter password: +++Pa%%w0rd+++
17. [] Click the **Next** button on the **Enter Credentials** step.
18. [] Keep the default settings and click the **Next** button on the **Recovery Location** step.
18. [] Keep the default settings and click the **Next** button on the **Restore Point** step.
19. [] Notice there is a new step, **Chained Plans**, compared to prior to chaining the orchestration plans. In a complete disaster situation, a Veeam Availability Orchestrator site admin would most likely want to launch all orchestration plans in the order they are chained. However, in some cases, perhaps only a single application is affected, and the remaining applications are still functioning without issues in production. In the event only a orchestration plan should be executed, without also launching any chained plans, simply untick the **Also execute the chained plans** check box. Click the **Cancel** button on the **Chained Plans** step.
20. [] Close the **Veeam Availability Orchestrator** window.

---

# Congratulations!

You have successfully completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
