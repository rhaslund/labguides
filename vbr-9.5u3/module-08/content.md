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

1. [] Navigate to the **Inventory** view.
2. [] Select **Physical & Cloud Infrastructure**.
3. [] Click the **Create Protection Group** button.
4. [] Keep the default name and click the **Next** button on the **Name** step.
5. [] Keep the default settings and click the **Next** button on the **Type** step.
6. [] Click the **Change** button.
7. [] Enter domain controller: +++VEEAM-DC01.veeamlab.local+++.
8. [] Click the **Account** drop down menu.
9. [] Select the **VEEAMLAB\\Administrator** account.
10. [] Click the **OK** button.
11. [] Click the **Add...** button.
12. [] Expand **Microsoft Active Directory**.
13. [] Expand the **veeamlab.local** domain.
14. [] Expand the **Computers** organizational unit.
15. [] Select the **Veeam Agents protected servers** security group.
16. [] Click the **OK** button.
17. [] Click the **Next** button on the **Active Directory** step.
18. [] Untick the **Exclude: All virtual machines** check box.
> Note: Because this is a lab training environment, we will include virtual machines. In a production environment, you would usually not want to protect virtual machines using Veeam Agents, unless, for example, the virtual machine does not support hypervisor snapshots

19. [] Untick the **All computers that have been offline for over 30 days** check box.
20. [] Click the **Next** button on the **Exclusions** step.

===

# Lab 8.3: Create a Agent Backup Job

1. [] Navigate to the **Home** view.
2. [] Select **Jobs** in the **Home** view.
3. [] Click the **Backup Job** button.
4. [] Select **Windows Computer...**.
5. [] Keep the default settings and click the **Next** button on the **Job Mode** step.
6. [] Enter name: +++Agent Backup Job Windows+++.
7. [] Click the **Next** button on the **Name** step.
8. [] Click the **Add...** button.
9. [] Select **Protection group...**.
10. [] Select **Protection Group 1**.
11. [] Click the **OK** button.
12. [] Click the **Next** button on the **Computers** step.
13. [] Keep the default setting and click the **Next** button.
14. [] Verify the **Backup Repository** has defaulted to **Main Backup Repository** then lower the amount of restore points to: +++3+++.
15. [] Click the **Advanced** button.
16. [] Click the **Throttling** tab.
17. [] Tick the **Run backup agent with low I/O priority** check box.
> Note: This feature ensures that the production workload is less impacted by the backup job.

18. [] Click the **OK** button.
19. [] Click the **Next** button on the **Storage** step.
20. [] Click the **Yes** button to dismiss the warning about a missing data location tag.
21. [] Keep the default settings and click the **Next** button on the **Guest Processing** step.
22. [] Tick the **Run the job automatically** check box.
23. [] Click the **Apply** button on the **Schedule** step.
24. [] Tick the **Run the job when I click Finish** check box.
25. [] Click the **Finish** button.

===

# Lab 8.4: Prepare Recovery Media for Bare Metal Recovery

===

Lab 8.5: Perform Bare Metal Recovery

---

# Congratulations!

You have completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
