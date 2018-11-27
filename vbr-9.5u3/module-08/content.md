Module 8: Introduction to Agents

---
**This lab is expected to last a maximum of 70 minutes including lab launch.**


# Lab 8.1: Prepare Microsoft Active Directory

1. [] Launch **Remote Desktop Connection client** from the Windows task bar.
2. [] Enter computer name: +++VEEAM-DC01+++
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

1. [] Launch the **Veeam Backup & Replication console** from the desktop.
2. [] Click the **Connect** button.

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
> Important! The Agent Backup Job Windows job must be in a Stopped status with the last result as Success before continuing to the next lab exercise — this should take less than 12 minutes.

===

# Lab 8.4: Prepare Recovery Media for Bare Metal Recovery

1. [] Select **Disk** in the **Backups** section of the **Home** view.
2. [] Expand the **Agent Backup Job Windows** job.
3. [] Select **PHYSICAL.veeamlab.local**.
4. [] Click the **Recovery Media** button on the **Backup** ribbon.
> Important! If you receive an error stating that the backup files are locked, it is because you did not wait for the agent backup job to complete. The Agent Backup Job Windows job must be in a Stopped status with the last result as Success before continuing — this should take less than 12 minutes. Please have some patience.

5. [] Keep the default setting and click the **Next** button on the **Recovery Media** step.
6. [] Enter folder to create recovery media in: +++C:\\Users\\Administrator.VEEAMINFRA\\Desktop\\VeeamRecoveryMedia.iso+++.
7. [] Click the **Next** button on the **Image Path** step.
8. [] Review the summary and click the **Next** button on the **Ready to Apply** step.
9. [] Wait for the creation of the recovery media to complete then click the **Finish** button on the **Progress** step.
> Note: This process should take less than one minute

===

# Lab 8.5: Perform Bare Metal Recovery

1. [] Launch the **VMware vSphere Client** from the Windows task bar.
2. [] Enter:
 1. User name: +++root+++
 2. Password: +++Pa$$w0rd+++

3. [] Click the **Login** butto.
4. [] Expand the **VEEAM-ESX** host.
5. [] Expand the **Production** resource pool.
6. [] Select the **PHYSICAL** virtual machine.
7. [] Click the **Edit Settings** text link in the **Commands** pane.
8. [] Confirm that **SCSI controller 0** type is **LSI Logic SAS** then click the **Cancel** button.
> Note: During the restore, we will utilize a different disk controller to showcase how bare-metal recovery can be performed even on different hardware.
9. [] Click the **Shut Down Guest** text link in the **Commands** pane.
10. [] Click the **Yes** button.
> Note: Wait for the PHYSICAL virtual machine to reach a powered off state.

11. [] Right click the **PHYSICAL** virtual machine.
12. [] Select **Delete from Disk**.
13. [] Click the **Yes** button.
14. [] Right click the **Production** resource pool.
15. [] Select **New Virtual Machine**.
16. [] Select the **Custom** radio button.
17. [] Click the **Next** button on the **Configuration** step.
18. [] Enter name: +++BAREMETAL+++.
19. [] Select the **Local01** datastore.
20. [] Click the **Next** button on the **Storage** step.
21. [] Keep the default setting and click the **Next** button.
22. [] Click the **Version** drop down menu.
23. [] Select **Windows Server 2012 (64-bit)**.
24. [] Click the **Next** button on the **Guest Operating System** step.
25. [] Click the **Number of cores per virtual socket** drop down menu.
26. [] Select **2**.
27. [] Click the **Next** button on the **CPUs** step.
28. [] Modify the **Memory Size** to +++2+++ GB.
29. [] Click the **Next** button on the **Memory** step.
30. [] Keep the default settings and click the **Next** button on the **Network** step.
31. [] Keep the default setting and click the **Next** button on the **SCSI Controller** step.
> Note: We will later modify this virtual machine from utilizing a SCSI controller to a IDE controller.

32. [] Keep the default setting and click the **Next** button on the **Select a Disk** step.
33. [] Lower the **Disk Size** to +++20+++ GB.
34. [] Select the **Thin Provision** radio button.
35. [] Click the **Next** button on the **Create a Disk** step.
36. [] Select the **IDE (0:0)** radio button.
37. [] Click the **Next** button on the **Advanced Options** step.
38. [] Click the **Finish** button on the **Ready to Complete** step.
39. [] Select the **Tiny-Veeam** virtual machine.
40. [] Right click the **datastore1** datastore in the **Resources** section.
41. [] Select **Browse Datastore...**.
42. [] Click the **Upload files to this datastore** button (icon looks like a datastore with a green arrow pointing into the datastore)
43. [] Select **Upload file...**.
44. [] Select **Desktop** in the **Navigation** pane.
45. [] Select the **VeeamRecoveryMedia.iso** recovery media.
46. [] Click the **Open** button.
47. [] Wait for the upload to complete then close the **Datastore Browser** window.
48. [] Select the **BAREMETAL** virtual machine.
49. [] Click the **Edit Settings** text link in the **Commands** pane.
50. [] Select **CD/DVD drive 1** in the hardware list.
51. [] Select the **Datastore ISO file** radio button.
52. [] Click the **Browse** button.
53. [] Double click the **datastore1** datastore.
54. [] Select the **VeeamRecoveryMedia.iso** recovery media.
> Important: The file name may only be partially displayed as VeeamRecover…

55. [] Click the **OK** button.
56. [] Tick the **Connect at power on** check box.
57. [] Click the **OK** button.
58. [] Click the **Power on** text link in the **Commands** pane.
59. [] Click the **Open Console** text link in the **Commands** pane.
60. [] Wait for the **Veeam Recovery Media** screen to appear, and then select **Bare Metal Recovery**.
> Tip: It is possible to utilize the keyboard only instead of the mouse to avoid issues.

61. [] Select the **Network storage** radio button.
62. [] Press the **Enter** keyboard button (or click the **Next** button).
63. [] Select the **Veeam backup repository** radio button.
64. [] Press the **Enter** keyboard button (or click the **Next** button).
65. [] Enter:
 1. Veeam backup server name: +++10.0.3.2+++.
 2. Username: +++VEEAMINFRA\\Administrator+++.
 3. Password: +++Pa$$w0rd+++.

66. [] Press the **Enter** keyboard button (or click the **Next** button).
67. [] Press the **Enter** keyboard button (or click the **Next** button).
68. [] Press the **Enter** keyboard button (or click the **Next** button).
69. [] Press the **Enter** keyboard button (or click the **Next** button).
70. [] Press the **Enter** keyboard button (or click the **Restore** button).
71. [] Press the **Enter** keyboard button (or click the **Finish** button).
> Note: This process can take up to 15 minutes.

72. [] Press the **Enter** keyboard button (or click the **Yes** button).


---

# Congratulations!

You have completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
