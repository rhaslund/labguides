Module 10: Veeam ONE Features and Functionality

---
**This lab is expected to last a maximum of 30 minutes including lab launch.**

# Lab 10.1: Setting up Veeam ONE (part two)

## Step 1: Add the Veeam Backup Enterprise Manager server

1. [] Launch **Veeam ONE Monitor** from the desktop.
2. [] Click the **Connect** button.

4. [] Click the **Add Server** button on the toolbar.
5. [] Select **Veeam Backup & Replication Server**.
6. [] Enter DNS name: +++VEEAM-VBR+++.
7. [] Untick the **Install Veeam ONE Agent** check box.
> Note: We will untick this check box since Veeam ONE is installed on the same server as the Veeam Backup Server and Veeam Backup Enterprise Manager.

7. [] Click the **Next** button on the **Name** step.
8. [] Enter:
 1. Username: +++VEEAMINFRA\Administrator+++
 2. Password: +++Pa$$w0rd+++

9. [] Click the **Next** button on the **Credentials** step.
10. [] Click the **Finish** on the **Summary** step.
11. [] Minimize the **Veeam ONE Monitor** window.

===

# Lab 10.2: Creating a custom Veeam ONE Reporter dashboard

## Step 1: Create a custom dashboard

1. [] Launch **Veeam ONE Reporter** from the desktop.
2. [] Tick the **Use Windows session credentials** check box.
3. [] Click the **Login** button.
4. [] Click the **Add new dashboard...** button in the top right corner.
5. [] Enter name: +++Student dashboard+++.
6. [] Select the top **Columns: 2** radio button.
7. [] Click the **OK** button.

===

## Step 2: Populate a dashboard

1. [] Click the **plus sign** on the left hand widget placeholder.
2. [] Enter caption: +++VI alarm+++.
3. [] Select **VMware Alarms**.
3. [] Click the **Next** button on the **Widget pack** step.
4. [] Keep the default setting and click the **Next** button on the **Widget** step.
5. [] Click the **Alarms** drop down menu.
6. [] Untick the **All items** check box.
7. [] Scroll down until the **Duplicate IP address detected** alarm is visible.
8. [] Tick the **Duplicate IP address detected** check box.
9. [] Click outside the **Alarms** drop down menu to collapse the **Alarms** drop down menu.
10. [] Click the **Finish** button on the **Options** step.
11. [] Minimize the **Veeam ONE Reporter** window.

===

# Lab 10.3. Customizing Veeam ONE Monitor alerting options

## Step 1: Set up email notifications

1. [] Switch to the **Veeam ONE Monitor** window using the Windows task bar.
2. [] Click the **Options** button.
3. [] Select **Server Settings...**.
4. [] Enter:
 1. SMTP Server: +++VEEAM-EX01.veeamlab.local+++
 2. From: +++VeeamONE@veeamlab.local+++

5. [] Click the **Send test email...** button.
6. [] Enter e-mail address: +++administrator@veeamlab.local+++.
7. [] Click the **OK** button to send the test e-mail.
8. [] Click the **OK** button to confirm the test e-mail has been sent.
9. [] Launch **Outlook Web Access** from the Windows task bar.
10. [] Enter:
 1. Username +++administrator@veeamlab.local+++
 2. Password:+++Pa$$w0rd+++

11. [] Click the **Sign In** button.
12. [] Verify that the email from **Veeam ONE Monitor** has been received then close the **Outlook Web Access** window.
13. [] Click the  **Notification Policy** tab.
14. [] Click the **Configure...** button in the **Default email notifications group** section.
15. [] Enter group of recipients: +++administrator@veeamlab.local+++
16. [] Click the **Add** button.
17. [] Click the **OK** button in the **Default Email Notification Group** window.
18. [] Click the **OK** button in the **Server Settings** window.

===

## Step 2: Create a custom alert

1. [] Navigate to the **Alarm Management** view.
2. [] Select **Virtual Machine** in the **VMware** section of the **Alarm Management** view.
3. [] Click the **New...** text link in the **Actions** pane.
4. [] Enter alarm name: +++LABTEST VM CPU usage+++.
5. [] Click the **Rules** tab.
6. [] Click the **Add...** button.
7. [] Select the **Resource usage** radio button.
8. [] Click the **Next** button on the **Choose Rule Type/Trigger type** step.

9. [] Click the **Counter** drop down menu.
10. [] Select **CPU Usage**.
11. [] Enter for the following time period: +++5+++ min.
12. [] Enter warning: +++70+++%.
13. [] Enter error: +++90+++%.
14. [] Click the **Finish** button on the **Define Rule** step.
15. [] Click the **Assignment** tab.
16. [] Click the **Add...** button in the **Assignment for alarm** section.
17. [] Select **Infrastructure tree...**.
18. [] Expand **Virtual Infrastructure**.
19. [] Tick the **VEEAM-ESX** check box.
> Note: You may want to assign the alarm to the custom categorization groups configured in **Veeam ONE Business View**. However, multiple assignment types for the same alarm cannot be combined.

20. [] Click the **Assign** button.
21. [] Click the **Save** button.

===

# Lab 10.4: Veeam ONE: Creating a Business View category and group

1. [] Navigate to the **Business View** view.
2. [] Click the **Categories** tab.
3. [] Click the **Add Category...** text link in the **Actions** pane.
4. [] Enter name: +++Veeam Courses+++
5. [] Click the **Next** button on the **Name and Object Type** step.
6. [] Keep the default setting and click the **Next** button on the **Platform** step.
7. [] Select the **Multiple conditions** radio button.
8. [] Click the **Next** button on the **Categorization Method** step.
9. [] Click the **Add..** button.
10. [] Enter name: +++Course VMs+++
11. [] Click the **Next** button on the **Group Name** step.
12. [] Click the **Property** drop down menu.
13. [] Select **Computer Name**.
14. [] Click the **Operator** drop down menu.
15. [] Select **Starts with**.
16. [] Enter value: +++VEEAM-+++
17. [] Click the **Save** button.
18. [] Click the **Add..** button.
19. [] Enter name: +++Other VMs+++
20. [] Click the **Next** button on the **Group Name** step.
21. [] Click the **Property** drop down menu.
22. [] Select **Computer Name**.
23. [] Click the **Operator** drop down menu.
24. [] Select **Does not contain**.
25. [] Enter value: +++VEEAM-+++
26. [] Click the **Save** button.
27. [] Click the **Next** button on the **Grouping Criteria** step.
28. [] Keep the default settings and click the **Save** button on the **Export** step.
29. [] Close the **Veeam ONE Monitor** window.

===

# Lab 10.5: Veeam ONE backup reporting

## Step 1. Run the Protected VMs report

1. [] Switch to the **Veeam ONE Reporter** window using the Windows task bar.
2. [] Click the **Configuration** tab.
> Note: Currently the infrastructure is scheduled to collect data from the server automatically every three hours. Since we want to see the group we have just created in the report before it is collected and synced automatically, it's required to run the data collection manually.

3. [] Navigate to the **Servers** view.
4. [] Select **VEEAM-ESX**.
5. [] Click the **Run now** button.
> **Important: Wait for the data collection to complete before continuing.**

6. [] Click the **Workspace** tab.
7. [] Select the **Veeam Backup Monitoring** folder.
8. [] Click the **Protected VMs** text link.
9. [] Select the **Business View object(s)** radio button.
> Note: The RPO is set to 1 week by default. The report will examine whether VMs have valid backup and replica restore points created within this specified time range (RPO period).

10. [] Click the **Click to choose** text link.
> Note: This will let you define Business View groups that should be analyzed in the report.

11. [] Expand the **Veeam Courses** category.
> **Important: If Veeam Courses is missing it is likely due to the collection started in the previously step has not yet finished.**

12. [] Tick the **Course VMs** check box.
13. [] Click the **OK** button.
14. [] Click the **Preview** button.
> Note: The report will open in a new window.

15. [] Review the report using the arrow buttons to switch between pages then close the **Protected VMs report** window.
> Note: A VM is considered to be Protected if there is at least one valid backup or replica restore point that meets the designated RPO for it. A VM is considered to be Unprotected if it has outdated or missing backup or replica restore points.

===

# Lab 10.6: Performing an infrastructure assessment

## Step 1: Start the VM Configuration Assessment report

1. [] Select the **VMware Infrastructure Assessment** folder.
2. [] Click the **VM Configuration Assessment** text link.
3. [] Keep the default settings and click the **Preview** button.
4. [] Review the report using the arrow buttons to switch between pages then close the **VM Configuration Assessment report** window.
5. [] Close the **Veeam ONE Reporter** window.

---

# Congratulations!

You have successfully completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
