Module 8: Introduction to Agents

---
**This lab is expected to last a maximum of 70 minutes including lab launch.**


# Lab 8.1: Prepare Microsoft Active Directory

1. [] Launch **Remote Desktop Connection client** from the Windows task bar.
2. [] Enter computer name: +++VEEAM-DC01+++
3. [] Click the **Connect** button.
4. [] Enter password: +++Pa$$w0rd+++
5. [] Click the **OK** button.
6. [] Launch the **Server Manager** from the Windows task bar.
7. [] Click on the **Tools** text link in the top right corner.
8. [] Select **Active Directory Users and Computers**.
9. [] Close the **Server Manager** window.
10. [] Expand the **veeamlab.local** domain.
11. [] Select the **Computers** organizational unit.
12. [] Click the **Action** menu.
13. [] Select **New**.
14. [] Select **Group**.
15. [] Enter group name: +++Veeam Agent protected servers+++
16. [] Click the **OK** button.
17. [] Select the **PHYSICAL** computer.
18. [] Click the **Action** menu.
19. [] Select **Add to a group...**.
20. [] Enter object name: +++Veeam Agent protected servers+++.
21. [] Click the **OK** button.
> Note: If a new window entitled Name Not Found is displayed, you have incorrectly entered the group name. Click the Cancel button and correct the name, then click the OK button.

22. [] Verify that the **Add to Group** operation was successfully completed, then click the **OK** button.
23. [] Close the **Active Directory Users and Computers** window.
24. [] Close the **Remote Desktop Connection** window.

===

# Lab 8.2: Setup Protection Group

1. [] Launch the **Veeam Backup & Replication console** from the desktop.
2. [] Click the **Connect** button.
3. [] Navigate to the **Inventory** view.
4. [] Select **Physical & Cloud Infrastructure**.
5. [] Click the **Add Group** button on the **Protection Group** ribbon.
6. [] Keep the default name and click the **Next** button on the **Name** step.
7. [] Keep the default settings and click the **Next** button on the **Type** step.
8. [] Click the **Change** button.
9. [] Enter domain controller: +++VEEAM-DC01.veeamlab.local+++.
10. [] Click the **Account** drop down menu.
11. [] Select the **VEEAMLAB\\Administrator** account.
12. [] Click the **OK** button.
13. [] Click the **Add...** button.
14. [] Expand **Microsoft Active Directory**.
15. [] Expand the **veeamlab.local** domain.
16. [] Expand the **Computers** organizational unit.
17. [] Select the **Veeam Agents protected servers** security group.
18. [] Click the **OK** button.
19. [] Click the **Next** button on the **Active Directory** step.
20. [] Untick the **All virtual machines** check box.
> Note: Because this is a lab training environment, we will include virtual machines. In a production environment, you would usually not want to protect virtual machines using Veeam Agents, unless, for example, the virtual machine does not support hypervisor snapshots

21. [] Untick the **All computers that have been offline for over 30 days** check box.
22. [] Click the **Next** button on the **Exclusions** step.
23. [] Click the **Test Now** button.
24. [] Verify that the test has completed successfully then click the **Close** button.
25. [] Click the **Next** button on the **Credentials** step.
26. [] Tick the **Install changed block tracking driver on Windows Server OS** check box.
27. [] Tick the **Perform reboot automatically if required** check box.
28. [] Click the **Next** button on the **Options** step.
> Note: Installing the CBT driver will require a reboot of the servers. In production environments, it may be desirable to control when production servers are rebooted

29. [] Click the **Apply** button on the **Review** step.
30. [] Review the messages then click the **Next** button on the **Apply** step.
31. [] Keep the default settings and click the **Finish** button on the **Summary** step.
32. [] Wait for the rescan status to change from **In progress** to **Success** then click the **Close** button.
> Note: This process should take less than 6 minutes.

33. [] Select **Protection Group 1** in the **Physical & Cloud Infrastructure** section of the **Inventory** view and confirm that the status of **PHYSICAL.veeamlab.local** is **Installed**.


===

# Lab 8.3: Create a Agent Backup Job

1. [] Navigate to the **Home** view.
2. [] Click the **Backup Job** button.
3. [] Select **Windows computer...**.
4. [] Keep the default settings and click the **Next** button on the **Job Mode** step.
5. [] Enter name: +++Agent Backup Job Windows+++.
6. [] Click the **Next** button on the **Name** step.
7. [] Click the **Add...** button.
8. [] Select **Protection group...**.
9. [] Select **Protection Group 1**.
10. [] Click the **OK** button.
11. [] Click the **Next** button on the **Computers** step.
12. [] Keep the default setting and click the **Next** button on the **Backup Mode** step.
13. [] Click the **Backup Repository** drop down menu.
14. [] Select **Scale-out Backup Repository**.
15. [] Lower the amount of restore points to: +++3+++.
16. [] Click the **Next** button on the **Storage** step.
17. [] Click the **Yes** button to dismiss the warning about a potential data sovereignty violation.
18. [] Keep the default settings and click the **Next** button on the **Guest Processing** step.
19. [] Tick the **Run the job automatically** check box.
20. [] Click the **Apply** button on the **Schedule** step.
21. [] Tick the **Run the job when I click Finish** check box.
22. [] Click the **Finish** button.
> Important! The Agent Backup Job Windows job must be in a Stopped status with the last result as Success before continuing to the next lab exercise — this will take a maximum of 12 minutes.

===

# Lab 8.4: Prepare Recovery Media for Bare Metal Recovery

1. [] Select **Disk** in the **Backups** section of the **Home** view.
2. [] Expand the **Agent Backup Job Windows** job.
3. [] Select **PHYSICAL.veeamlab.local**.
4. [] Click the **Recovery Media** button on the **Backup** ribbon.
> Important! If you receive an error stating that the backup files are locked, it is because you did not wait for the agent backup job to complete. The Agent Backup Job Windows job must be in a Stopped status with the last result as Success before continuing to the next lab exercise — this will take a maximum of 8 minutes.

5. [] Keep the default setting and click the **Next** button on the **Recovery Media** step.
6. [] Enter folder to create recovery media in: +++C:\\Users\\Administrator.VEEAMINFRA\\Desktop\\VeeamRecoveryMedia.iso+++.
7. [] Click the **Next** button on the **Image Path** step.
8. [] Review the summary and click the **Next** button on the **Ready to Apply** step.
9. [] Wait for the creation of the recovery media to complete then click the **Finish** button on the **Progress** step.
> Note: This process should take less than one minute

===

# Lab 8.5: Perform Bare Metal Recovery

1. [] Launch the **VMware Host Client** from the Windows task bar.
2. [] Enter:
 1. User name: +++root+++
 2. Password: +++Pa$$w0rd+++

3. [] Click the **Log in** button.
4. [] Click the **Virtual Machines** text link in the **Navigator** pane.
5. [] Tick the **PHYSICAL** check box.
6. [] Click the **Shut down** button.
7. [] Wait for the **PHYSICAL** virtual machine to reach a powered off state then click the **Actions** button.
8. [] Select **Delete**.
9. [] Click the **Delete** button.
10. [] Click the **Create / Register VM** button.
11. [] Keep the default setting and click the **Next** button on the **Select creation type** step.
12. [] Enter name: +++BAREMETAL+++
13. [] Click the **Guest OS family** drop down menu.
14. [] Select **Windows**.
15. [] Click the **Guest OS version** drop down menu.
16. [] Select **Microsoft Windows Server 2012 (64-bit)**.
17. [] Click the **Next** button on the **Select a name and guest OS** step.
18. [] Select the **Local01** datastore.
19. [] Click the **Next** button on the **Select storage** step.
20. [] Click the **CPU** drop down menu.
21. [] Select **2**.
22. [] Lower the **Memory** from 4096 MB to +++2048+++ MB.
23. [] Lower the **Hard disk 1** capacity from 40 GB to +++20+++ GB.
24. [] Select the **Thin provisioned** radio button.
25. [] Click the **Next** button on the **Customize settings** step.
26. [] Click the **Finish** button on the **Ready to complete** step.
27. [] Click the **BAREMETAL** virtual machine text link.
28. [] Click the **Edit** button.
29. [] Click the **CD/DVD Drive 1** drop down menu.
30. [] Select **Datastore ISO file**.
31. [] Select the **Local01** datastore.
32. [] Click the **Upload** button.
33. [] Select **Desktop**.
34. [] Select the **VeeamRecoveryMedia.iso** file.
35. [] Click the **Open** button.
36. [] Select the newly uploaded **VeeamRecoveryMedia.iso** file.
37. [] Click the **Select** button.
38. [] Click the **Save** button.
39. [] Click the **Power on** button.
40. [] Click the **Console** button.
41. [] Wait for the **Veeam Recovery Media** screen to appear, and then select **Bare Metal Recovery**.
42. [] Select the **Network storage** radio button.
43. [] Click the **Next** button on the **Backup Location** step.
44. [] Select the **Veeam backup repository** radio button.
45. [] Click the **Next** button on the **Network Storage** step.
46. [] Enter:
 1. Veeam backup server name: +++10.0.3.2+++.
 2. Username: +++VEEAMINFRA\\Administrator+++.
 3. Password: +++Pa$$w0rd+++.

47. [] Click the **Next** button on the **Backup Server** step.
48. [] Keep the default settings and click the **Next** button on the **Backup** step.
49. [] Keep the default settings and click the **Next** button on the **Restore Point** step.
50. [] Keep the default settings and click the **Next** button on the **Restore Mode** step.
51. [] Click the **Restore** button on the **Summary** step.
> Note: Only about 10 GB of data will need to be restored - this will take a maximum of 5 minutes.

52. [] Click the **Finish** button on the **Progress** step.
53. [] Click the **Yes** button to confirm rebooting the computer.

54. [] Wait for Windows to complete startup then close the **VMware Host Client** window.
55. [] Close the **Veeam Backup & Replication console** window.

---

# Congratulations!

You have completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
