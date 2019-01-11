Module 6: Configuration
---
**This lab is expected to last a maximum of 20 minutes including lab launch.**

# Lab 6.1: Assigning user roles and permissions

1. [] Launch **Veeam Availability Orchestrator** from the Desktop.
2. [] Enter username: +++siteadmin@vmce.lab+++ and password: +++Pa%%w0rd+++.
3. [] Click the **Login** button.
>Note: Because the server was just started, the spinning icon may display for up to two minutes while services complete their startup.

4. [] Click the **Administation** button in the top right corner.
5. [] Navigate to the **Users and Scopes** view.
6. [] Click the **Add** button in the **Scopes** pane.
7. [] Enter:
 1. Name: +++SharePoint Administrators+++
 2. Description: +++Scope for administrators managing Microsoft SharePoint+++
8. [] Click the **Add** button.
9. [] Select the **SharePoint Administrators** scope.
10. [] Click the **Add** button in the **Users and Groups** pane.
11. [] Enter:
 1. Domain: +++VMCE+++
 2. Account: +++planauthor+++.
13. [] Click the **Find** button.
14. [] Select the **Plan Author** account.
15. [] Click the **Add** button.

===

# Lab 6.2: Configuring notifications

1. [] Navigate to the **Reporting** view.
2. [] Click the **Edit** text link in the **SMTP Server** section.
3. [] Enter:
 1. SMTP Server: +++exchange.vmce.lab+++
 2. Port: 25
 3. From +++veeam-vao@vmce.lab+++

4. [] Tick the **Use secure connection** check box.
5. [] Click the **Send Test Email** button.
6. [] Enter email address: +++administrator@vmce.lab+++
7. [] Click the **Send** button.
8. [] Click the **OK** button to close the info window.
> Note: If the test fails, it may simply be that the SMTP service on the Exchange server is still in a starting state. Please wait one to two minutes and try again.

9. [] Click the **Close** button.
10. [] Click the **Save** button.
11. [] Verify the state changes to **Connection Successful** and click the **Add** button in the **Recipients** pane.
12. [] Enter address: +++administrator@vmce.lab+++
13. [] Click the **Save** button.
14. [] Notice that all subscriptions are disabled by default. Tick the **Types** check box in the **Reports** pane.
15. [] Click the **Subscribe** button in the **Reports** pane and verify that all subscriptions are in a subscribed state.
16. [] Minimize the **Veeam Availability Orchestrator** window.
17. [] Launch **Outlook Web Access** from the desktop.
18. [] Enter username: +++administrator@vmce.lab+++ and password: +++Pa%%w0rd+++.
19. [] Click the **Sign in** button.
20. [] Verify that you see the Veeam Availability Orchestrator test message and close the **Outlook Web Access window**.

===

# Lab 6.3: Create a recovery location

1. [] Switch back to the previously minimized **Veeam Availability Orchestrator** window.
1. [] Navigate to the **Recovery Locations** view.
2. [] Click the **Add** button.
3. [] Enter name: +++DR site+++
4. [] Click the **Next** button on the **Location Name** step.

7. [] Select the **VAO DR Locations – Gold – Tier 1** group.
8. [] Click the **Add** button.
9. [] Click the **Next** button on the **Compute Resources** step.
10. [] Select the **VAO DR Locations – Gold – Tier 1** group.
11. [] Click the **Add** button.
12. [] Click the **Next** button on the **Storage Resources** step.
13. [] Keep the default values and click the **Next** button on the **Resource Usage** step.
14. [] Click on the **Instant VM Recovery is:** drop down menu.
15. [] Select **Enabled**.
16. [] Click the **Next** button on the **Instant VM Recovery (IVR)** step.
17. [] Tick the **Enable re-IP** check box.
18. [] Click the **Add** button.
19. [] Enter:
 1. Source VM IP Address: +++192.168.1.\*+++
 2. Source VM Subnet mask: +++255.255.255.0+++
 3. Target VM IP Address: +++192.168.2.\*+++
 4. Target VM IP Subnet mask: +++255.255.255.0+++
 5. Default gateway:  +++192.168.2.1+++
 6. Preferred DNS server: +++192.168.2.4+++
 7. Alternate DNS server: +++192.168.1.101+++

20. [] Click the **Add** button.
21. [] Click the **Next** button on the **Re-IP Rules** step.
22. [] Tick the **Enable Network Mapping** check box.
23. [] Select **PROD LAN in Production** in the **Source network** section.
24. [] Select **DR in DR** in the **Target network** section.
24. [] Click the **Add** button.
25. [] Click the **Next** button on the **Network Mapping** step.
26. [] Click the **Finish** button on the **Summary** step.

===

# Lab 6.4: Configure plan components

1. [] Navigate to the **Plan Components** view.
2. [] Verify you see VM groups named **Mission Critical – Exchange Servers** and **Mission Critical – Sharepoint Servers** and that they are both enabled. Each VM group represents a vSphere tag. Tags are by default collected every three hours from your production environment. After you enable VM groups for a Veeam Availability Orchestrator site, you can add these groups to failover plans for the site. Click the **Default** text link in the **Scopes** pane at the top.
4. [] Untick the **Default** checkbox in the **Scope** pane.
5. [] Tick the **SharePoint Administrators** checkbox in the **Scope** pane.
6. [] Click the **OK** button.
7. [] Tick the **mission critical vms – sharepoint servers** checkbox in the **VM Groups** pane.
8. [] Click the **Include** button.
12. [] Click the **Plan Steps** tab.
> Important: Use the Plan Steps tab inside the Plan Components view. Do NOT change to the Plan Steps view.

13. [] Review the list of default steps provided by Veeam, these cannot be deleted - only custom steps can be deleted. Tick the **Verify Exchange Mailbox** check box.
17. [] Tick the **Verify Exchange MAPI Connectivity** check box.
18. [] Tick the **Verify Exchange Services** check box.
20. [] Tick the **Verify Mail Server Port** check box.
21. [] Click the **Exclude** button in the **Steps** pane.

22. [] Click the **Credentials** tab.
23. [] Click the **SharePoint Administrators** text link in the **Scopes** pane at the top.
24. [] Tick the **Default** check box in the **Scope** pane.
> Note: Both the Default and SharePoint Administrators scopes must be selected.

25. [] Click the **OK** button.
23. [] Tick the **administrator@vmce.lab** check box so that it can be used in plans.
24. [] Click the **Include** button in the **Credentials** pane.
25. [] Click the **Recovery Locations** tab.
> Important: Use the Recovery Locations tab inside the Plan Components view. Do NOT change to the Recovery Locations view.

26. [] Tick the **DR Site** checkbox.
27. [] Click the **Include** button.

25. [] Navigate to the **DataLab Allocation** view.
26. [] Verify the **VLAB1** and **VLAB2** DataLabs created earlier shows up and then tick the **VEEAM-VAO\VLAB1** check box.
27. [] Click the **Assign** button in the **DataLabs** pane.
28. [] Select the **SharePoint Administrators** scope.
29. [] Click the **OK** button.
30. [] Untick the **VEEAM-VAO\VLAB1** check box.
31. [] Tick the **VEEAM-VAO\VLAB2** check box.
32. [] Click the **Assign** button in the **DataLabs** pane.
33. [] Select the **Default** scope.
34. [] Click the **OK** button.

===

# Lab 6.5: Create a template job

1. [] Close the **Veeam Availability Orchestrator** window.
1. [] Launch the **Veeam Backup & Replication Console** from the desktop.
2. [] Click the **Connect** button.
3. [] Click the **Backup Job** button on the **Home** ribbon.
4. [] Select **Virtual machine...**.
5. [] Enter name: +++Template Backup Job for VAO+++, and enter description: +++This job is a \[VAO template\] to re-protect failed over VMs+++.
6. [] Click the **Next** button on the **Name** step.
7. [] Click the **Add...** button.
8. [] The current view selection is **Hosts and Clusters**. Click on the **VMs and Templates** view button.
9. [] Expand the **vcenter.vmce.lab** object.
10. [] Expand the **DR** data center object.
11. [] Select the **Empty folder for VAO template jobs** folder.
12. [] Click the **Add** button.
13. [] Click the **Next** button on the **Virtual Machines** step.
14. [] Keep the defaults and click the **Next** button on the **Storage** step.
15. [] Keep the defaults and click the **Next** button on the **Guest Processing** step.
16. [] Do not schedule the job and click the **Apply** button on the **Schedule** step.
17. [] Click the **Finish** button on the **Summary** step.
18. [] Close the **Veeam Backup & Replication** console.
> Note: The template job will not be visible in Veeam Availability Orchestrator until after the next data collection interval. Once it is visible in Veeam Availability Orchestrator, it must be enabled before it can be used.

---

# Congratulations!

You have successfully completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
