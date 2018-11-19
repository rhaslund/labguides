Module 5: User Interface, User Roles & Licensing

# Lab 5.1: Accessing Veeam Availability Orchestrator user interface

1. [] Launch **Veeam Availability Orchestrator** from the desktop.
2. [] Enter username: +++siteadmin@vmce.lab+++ and password: +++Pa%%w0rd+++.
>Note: You are no longer able to log in as administrator@vmce.lab since this account does not have sufficient permissions in Veeam Availability Orchestrator.
3. [] Click the **Login** button
4. [] Click the **Administration** button in the top right corner.
5. [] Navigate to the **Users and Scopes** view.
6. [] Notice how the help system automatically opens. Click the **toggle** button to disable the Suggest help topics automatically feature.
7. [] Click the **X** in the Users and Scopes help window.
> Note: You can always click the Info icon in the bottom left corner to see these tips.
8. [] Take notice of which roles are available and then navigate to the **License** view.
9. [] Click the **Details...** text link next to the Status row.
10. [] Verify the license is valid and that zero licenses have been consumed then click the **OK** button.
11. [] Navigate to the **Welcome** view.
12. [] Notice that the first to-do list item of Deploy VAO agent to the Veeam Backup & Replication server. is not completed. This is because no replication jobs have been set up yet. Notice that the third to-do list item is also not completed. This is because we didn't create any virtual labs yet in Veeam Backup & Replication. Close the **Veeam Availability Orchestrator** window.

# Lab 5.2: Prepare Veeam Backup & Replication: Install new license

1. [] Launch the **Veeam Backup & Replication console** from the desktop.
2. [] Click the **Connect** button.
3. [] Click the **main menu** button in the top left corner.
4. [] Select **License**.
5. [] Click the **Install License** button.
6. [] Enter +++C:\Install\veeam_availability_suite_nfr_2_2.lic+++ in the File name field.
7. [] Click the **Open** button.
8. [] Click the **Close** button.

# Lab 5.3: Prepare Veeam Backup & Replication: Create a replication jobs

## Step 1: Create a replication job

1. [] Open the **Backup Infrastructure** view.
2. [] Notice that the vcenter.vmce.lab server is already present because it was added in Veeam Availability Orchestrator. Navigate to the **Home** view.
3. [] Click on the **Replication Job** button.
4. [] Select **VMware vSphere**.
5. [] Enter name: +++VAO Lab Group Active Directory+++.
6. [] Click the **Next** button.
7. [] Click the **Add...** button.
8. [] Expand the **vcenter.vmce.lab** object.
9. [] Expand the **DR** data center.
10. [] Expand the **esx02.vmce.lab** host.
11. [] Select the **DC02** virtual machine.
12. [] Click the **Add** button.
13. [] Click the **Next** button on the **Virtual Machines** step.
14. [] Click the **Choose...** button.
15. [] Expand the **vcenter.vmce.lab** object.
16. [] Expand the **DR** data center.
17. [] Select the **esx02.vmce.lab** host.
18. [] Click the **OK** button.
19. [] Click the **Next** button on the **Destination** step.
20. [] Modify restore points to keep to +++1+++ (one).
21. [] Click the **Next** button on the **Job Settings** step.
22. [] Keep the defaults on the Data Transfer step and click the **Next** button.
23. [] Tick the **Enable application-aware processing** check box.
24. [] Click the **Add...** button.
25. [] Select the **Standard account...** button.
26. [] Enter username +++administrator@vmce.lab+++ and password +++Pa%%w0rd+++.
27. [] Click the **OK** button.
28. [] Click the **Test Now** button.
29. [] Verify all tests were successful and then click the **Close** button.
30. [] Click the **Next** button on the **Guest Processing** step.
31. [] Click the **Apply** button.
32. [] Tick the **Run the job when I click Finish** check box.
33. [] Click the **Finish** button on the **Summary** step.

## Step 2: Create second replica job

1. [] Click the **Replication Job** button.
2. [] Select **VMware vSphere**.
3. [] Enter name: +++Replication Job Exchange & SharePoint+++.
4. [] Tick the **Separate virtual networks** check box.
5. [] Tick the **Different IP addressing scheme** check box.
6. [] Click the **Next** button on the **Name** step.
7. [] Click the **Add...** button.
8. [] Expand the **vcenter.vmce.lab** object.
9. [] Expand the **Production** data center.
10. [] Expand the **esx01.vmce.lab** host.
