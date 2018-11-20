Module 8: Working with Orchestration Plans
---
**This lab is expected to last a maximum of X minutes including lab launch.**

# Lab 8.1: Enable a template job

1. [] Launch **Veeam Availability Orchestrator** from the desktop.
2. [] Enter username: +++siteadmin@vmce.lab+++ and password: +++Pa%%w0rd+++.
3. [] Click the **Login** button.
>Note: Because the server was just started, the spinning icon may display for up to two minutes while services complete their startup.

4. [] Click the **Administration** button in the top right corner.
5. [] Navigate to the **Plan Components** view.
6. [] Click the **Template Jobs** tab.
7. [] Tick the **VEEAM-VAO\Template Backup Job for VAO** check box.
8. [] Click the **Include** button in the **Template Jobs** pane.
9. [] Click the **Exit Administration** button in the top left corner.

===

# Lab 8.2: Create a orchestration plan

1. [] Navigate to the **Orchestration Plans** view.
2. [] Click the **Manage** button.
3. [] Select **New**.
4. [] Select the **Phoenix\SharePoint Administrators** site scope.
5. [] Click the **Next** button on the **Site Scope** step.
6. [] Enter:
 1. Plan name: +++Tier1-SharePoint+++
 2. Description: +++Orchestration Plan for SharePoint servers+++
 3. Contact name: +++John Doe+++
 4. Contact email: +++administrator@vmce.lab+++

7. [] Click the **Next** button on the **Plan Name** step.
8. [] Keep the default selection of **Failover** and click the **Next** button on the **Plan Type** step.
9. [] Select **mission critical vms - sharepoint servers**.
10. [] Click the **Add** button.
11. [] Click the **Next** button on the **VM Groups** step.
12. [] Keep the defaults and click the **Next** button on the **VM Recovery Options** step.
13. [] Select **Ping VM Network**.
14. [] Click the **Add** button.
15. [] Click the **Next** button on the **VM Steps** step.
16. [] Keep the defaults and click the **Next** button on the **Protect VM Groups** step.
17. [] Keep the defaults and click the **Next** button on the **RTO & RPO** step.
18. [] Keep the defaults and click the **Next** button on the **Report Template** step.
19. [] Keep the defaults and click the **Next** button on the **Report Scheduling** step.
20. [] Untick the **Run Readiness Check after Plan creation** check box.
21. [] Click the **Next** button on the **Readiness Check** step.
22. [] Click the **Finish** button on the **Summary** step.

===

# Lab 8.3: Perform initial readiness check

1. [] Select the newly created **Tier1-SharePoint** plan.
> Note: Do not click on the Tier1-SharePoint text link.

2. [] Click the **Verify** button.
3. [] Select **Run Readiness Check**.
4. [] Click the **OK** button.
5. [] Confirm that the state has changed to **Verified (passed check)**.
6. [] Click the **View Reports** button.
7. [] Select **Readiness Check**.
8. [] Select the **Readiness Check Report for Tier1-SharePoint** report.
9. [] Click the **Open** button on the yellow download bar at the bottom of the **Internet Explorer** window.
10. [] Wait for the download to complete and click the **Open** button on the yellow download bar at the bottom of the **Internet Explorer** window.
11. [] Scroll down to the **Contents** page.
12. [] 

---

# Congratulations!

You have successfully completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
