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
3. [] Select **Windows Computer...**.
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
14. [] Select **Main Backup Repository**.
15. [] Lower the amount of restore points to: +++3+++.
16. [] Click the **Next** button on the **Storage** step.
17. [] Click the **Yes** button to dismiss the warning about a potential data sovereignty violation.
18. [] Keep the default settings and click the **Next** button on the **Guest Processing** step.
19. [] Tick the **Run the job automatically** check box.
20. [] Click the **Apply** button on the **Schedule** step.
21. [] Tick the **Run the job when I click Finish** check box.
22. [] Click the **Finish** button.
> Important! The Agent Backup Job Windows job must be in a Stopped status with the last result as Success before continuing to the next lab exercise — this will take a maximum of 9 minutes.

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

1. [] Launch the **VMware vSphere Client** from the Windows task bar.
2. [] Enter:
 1. User name: +++root+++
 2. Password: +++Pa$$w0rd+++

3. [] Click the **Login** button.
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
19. [] Click the **Next** button on the **Name and Location** step.
20. [] Select the **Local01** datastore.
21. [] Click the **Next** button on the **Storage** step.
22. [] Keep the default setting and click the **Next** button on the **Virtual Machine Version**.
23. [] Click the **Version** drop down menu.
24. [] Select **Windows Server 2012 (64-bit)**.
25. [] Click the **Next** button on the **Guest Operating System** step.
26. [] Click the **Number of cores per virtual socket** drop down menu.
27. [] Select **2**.
28. [] Click the **Next** button on the **CPUs** step.
29. [] Modify the **Memory Size** to +++2+++ GB.
30. [] Click the **Next** button on the **Memory** step.
31. [] Keep the default settings and click the **Next** button on the **Network** step.
32. [] Keep the default setting and click the **Next** button on the **SCSI Controller** step.
> Note: We will later modify this virtual machine from utilizing a SCSI controller to a IDE controller.

33. [] Keep the default setting and click the **Next** button on the **Select a Disk** step.
34. [] Lower the **Disk Size** to +++20+++ GB.
35. [] Select the **Thin Provision** radio button.
36. [] Click the **Next** button on the **Create a Disk** step.
37. [] Select the **IDE (0:0)** radio button.
38. [] Click the **Next** button on the **Advanced Options** step.
39. [] Click the **Finish** button on the **Ready to Complete** step.
40. [] Select the **BAREMETAL** virtual machine.
41. [] Right click the **Local01** datastore in the **Resources** section.
42. [] Select **Browse Datastore...**.
43. [] Click the **Upload files to this datastore** button (icon looks like a datastore with a green arrow pointing into the datastore)
44. [] Select **Upload file...**.
45. [] Select **Desktop** in the **Navigation** pane.
46. [] Select the **VeeamRecoveryMedia.iso** recovery media.
> Note: It may be necessary to scroll down.

47. [] Click the **Open** button.
48. [] Click the **Yes** button to confirm replacing any existing file(s).
49. [] Wait for the upload to complete then close the **Datastore Browser** window.
50. [] Click the **Edit Settings** text link in the **Commands** pane.
51. [] Select **CD/DVD drive 1** in the hardware list.
52. [] Select the **Datastore ISO file** radio button.
53. [] Click the **Browse...** button.
54. [] Double click the **Local01** datastore.
55. [] Select the **VeeamRecoveryMedia.iso** recovery media.
> Important: It may be necessary to scroll down. The file name may only be partially displayed as VeeamRecover…

56. [] Click the **OK** button.
57. [] Tick the **Connect at power on** check box.
58. [] Click the **OK** button.
59. [] Click the **Power On** text link in the **Commands** pane.
60. [] Click the **Open Console** text link in the **Commands** pane.
61. [] Wait for the **Veeam Recovery Media** screen to appear, and then click anywhere inside the **virtual machine console**.
62. [] Select **Bare Metal Recovery** by pressing the **down arrow** keyboard button and then the **Enter** keyboard button.
> Tip: It is possible to utilize the keyboard only instead of the mouse to avoid issues.

63. [] Select the **Network storage** radio button by pressing the **Tab** keyboard button three times, then pressing the **down arrow** keyboard button.
64. [] Press the **Enter** keyboard button (or click the **Next** button) on the **Backup Location** step.
65. [] Select the **Veeam backup repository** radio button by pressing the **down arrow** keyboard button until the **Veeam backup repository** radio button is selected.
66. [] Press the **Enter** keyboard button (or click the **Next** button) on the **Network Storage** step.
67. [] Enter:
 1. Veeam backup server name: +++10.0.3.2+++.
 2. Username: +++VEEAMINFRA\\Administrator+++.
 3. Password: +++Pa$$w0rd+++.

68. [] Press the **Enter** keyboard button (or click the **Next** button) on the **Backup Server** step.
69. [] Keep the default settings and press the **Enter** keyboard button (or click the **Next** button) on the **Backup** step.
70. [] Keep the default settings and press the **Enter** keyboard button (or click the **Next** button) on the **Restore Point** step.
71. [] Keep the default settings and press the **Tab** keyboard button three times then press the **Enter** keyboard button (or click the **Next** button) on the **Restore Mode** step.
72. [] Keep the default settings and press the **Enter** keyboard button (or click the **Restore** button) on the **Summary** step.
73. [] Press the **Enter** keyboard button (or click the **Finish** button) on the **Progress** step.
> Note: Only about 10 GB of data will need to be restored - this will take a maximum of 10 minutes.

74. [] Click the **Yes** button to confirm rebooting the computer.
75. [] Wait for Windows to complete startup then press the **CTRL** and **ALT** keyboard buttons together to release the mouse from the **virtual machine console** window.
76. [] Click the **VM** menu.
77. [] Select **Guest**.
78. [] Select **Send Ctrl\+Alt\+Del**.
79. [] Click inside the **virtual machine console** window.
80. [] Enter password: +++Pa$$w0rd+++.
81. [] Click the **right arrow login** button (or press the **Enter** keyboard button).
82. [] Click the **Cancel** button to dismiss the **Shutdown Event Tracker** window.
83. [] Close the **BAREMETAL** virtual machine console window.
84. [] Close the **VMware vSphere Client** window.
85. [] Close the **Veeam Backup & Replication console** window.

---

# Congratulations!

You have completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
