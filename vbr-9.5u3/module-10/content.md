Module 10: Veeam ONE Features and Functionality

---
**This lab is expected to last a maximum of 70 minutes including lab launch.**

# Lab 10.1: Setting up Veeam ONE (part two)

## Step 1: Add the Veeam Backup Enterprise Manager server

1. [] Launch **Veeam ONE Monitor** from the desktop.
2. [] Click the **Connect** button.
3. [] Click the **Cancel** button to dismiss the **Server Settings** window.
3. [] Click the **Add Server** button on the toolbar.
4. [] Select **Veeam Backup & Replication Server**.
5. [] Enter DNS name: +++VEEAM-VBR+++.
6. [] Click the **Next** button on the **Name** step.
7. [] Enter:
 1. Username: +++VEEAMINFRA\Administrator+++.
 2. Password: +++Pa%%w0rd+++.

8. [] Click the **Next** button on the **Credentials** step.
9. [] Click the **Finish** on the **Summary** step.
10. [] Minimize the **Veeam ONE Monitor** window.

===

# Lab 10.2: Creating a custom Veeam ONE Reporter dashboard

## Step 1: Create a custom dashboard

1. [] Launch **Veeam ONE Reporter** from the desktop.
2. [] Tick the **Use Windows session credentials** check box.
3. [] Click the **Login** button.
4. [] Click the **Add new dashboard** button in the top right corner.
5. [] Enter name: +++Student dashboard+++.
6. [] Select the top **Columns: 2** radio button.
7. [] Click the **OK** button.

===

## Step 2: Populate a dashboard**

1. [] Click the **plus sign** of the left hand widget placeholder.
2. [] Enter caption: +++VI alarm+++.
3. [] Select **VMware Alarms**.
3. [] Click the **Next** button on the **Widget pack** step.
4. [] Keep the default setting and click the **Next** button on the **Widget** step.
5. [] Click the **Virtual Infrastructure** text link.
6. [] Expand **Virtual Infrastructure**.
7. [] Verify the **VEEAM-ESX** check box is ticked then click the **OK** button.
8. [] Click the **Alarms** drop down menu.
9. [] Untick the **All items** check box.
10. [] Scroll down until the **Duplicate IP address detected** alarm is visible.
11. [] Tick the **Duplicate IP address detected** check box.
12. [] Click outside the **Alarms** drop down menu to collaps the **Alarms** drop down menu.
12. [] Click the **Finish** button on the **Options** step.
13. [] Minimize the **Veeam ONE Reporter** window.

===

# Lab 10.3. Customizing Veeam ONE Monitor alerting options

## Step 1: Set up email notifications

1. [] Switch to the **Veeam ONE Monitor** window using the Windows task bar.
3. [] Click the **Options** button.
4. [] Select **Server Settings...**.
5. [] > Enter the **SMTP options** as follows:
 1. SMTP Server: +++VEEAM-EX01.veeamlab.local+++.
 2. From: +++VeeamONE\@veeamlab.local+++

6. [] Click the **Send test email...** button.
6. [] Enter e-mail address: +++administrator\@veeamlab.local+++.
7. [] Click the **OK** button to send the test e-mail.
7. [] Click the **OK** button to confirm the test e-mail has been sent.
8. [] Launch **Outlook Web Access** from the Windows task bar.
9. [] Enter:
 1. Username +++administrator\@veeamlab.local+++
 2. Password:+++Pa$$w0rd+++

10. Click the **Sign In** button.
10. [] Verify that the email from **Veeam ONE Monitor** has been received then close the **Outlook Web Access** window.
11. [] Click the  **Notification Policy** tab.
12. [] Click the **Configure...** button in the **Default email notifications group** section.
13. [] Enter group of recipients: +++administrator\@veeamlab.local+++

14. [] Click the **Add.** button.
14. [] Click the **OK** button to close the **Default Email Notification Group** window.
15. [] Click the **OK** button to close the **Server Settings** window.

## Step 2: Create a custom alert

1. [] Navigate to the **Alarm Management** section.
2. [] Select **Virtual Machine** in the **VMware** section.
3. [] Click the **New...** text link in the **Actions pane**.
4. [] Enter alarm name: +++LABTEST VM CPU usage+++.
5. [] Click the **Rules** tab.
5. [] Click the **Add...** button.
6. [] Select the **Rule for specific conditions or state** radio button.
7. [] Click the **Next** button on the **Choose Rule Type/Trigger type** step.
8. [] Select the **Resource usage is out of allowed range** radio button.
9. [] Click the **Next** button on the **Choose Rule Type/Rule condition** step.
10. [] Click the **Counter** drop down menu.
11. [] Select **CPU Usage**.
11. [] Enter In the For the following time period: +++5+++ min.
12. [] Enter In the Warning box: +++70+++%.
13. [] Enter In the Error box: +++90+++%.
14. [] Click the **Finish** button on the **Define Rule** step.
15. [] Click the **Assignment** tab.
16. [] Click the **Add** button in the **Assignment for alarm** section.
17. [] Select **Infrastructure tree...**.

17. [] Expand **Virtual Infrastructure**.
18. [] Tick the **VEEAM-ESX** check box.
> Note: You may want to assign the alarm to the custom categorization groups configured in **Veeam ONE Business View**. However, multiple assignment types for the same alarm cannot be combined.

19. [] Click the **Assign** button.
20. [] Click the **Save** button.
21. [] Close the **Veeam ONE Monitor** window.

===

# Lab 10.4: Veeam ONE: Creating a Business View category and group

## Step 1. Create a Business View category

> 1. [] Open **Veeam ONE Business View** by double-clicking the desktop shortcut.
>
> 2. [] Enter username *VEEAMINFRA\\Administrator* and password *Pa$$w0rd*, then click the **Login** button.

3. []

Click the **Configuration** link in the top right corner.. []

> 4. [] Go to the **Categories** section.

5. []

Click **Add\.... [] **

> 6. [] In the **Add new category** dialogue box, enter *Veeam Courses* in the **Friendly name** and **Tag category to use sections**.
>
> Switch the **Group type** radio button to *Dynamic*.
>
> 7. [] Leave *Virtual Machine* in the **Choose object type** field and click the **"Not Set" groups on charts** drop-down list.
>
> **Step 2. Create Business View groups**
>
> **Action Description Illustration**

1. []

Switch to the **Groups** section.. []

2. []

Click the **Veeam Courses** tab.. []

3. []

> Click **Grouping Expression...**

> [!KNOWLEDGE] Please double check that you have selected the right Veeam Courses tab.. []

4. []

> At **Grouping Expression,** we will copy and paste the text from the document c:\\install\\businessview.txt.
>
> [!KNOWLEDGE] This expression will choose the VMs starting with "Veeam."

Click **File Explorer**.. []

> 5. [] Go to the c:\\install folder.

6. []

Open BusinessView.txt.. []

> 7. [] This expression will choose the VMs starting with "Veeam." Click the expression to select it.

8. []

Copy the expression.. []

> 9. [] Go back to the Veeam ONE Business View interface. Paste the grouping expression.

10. []

Click **OK**.. []

> 11. [] Go to the **Workspace** tab.
>
> **Lab 10.5. Veeam ONE backup reporting**
>
> Run the Protected VMs report to analyze the backup protection of VMs in your virtual environment.

===

# Step 1. Run the Protected VMs report

> **Action Description Illustration**
>
> 1. [] Open **Veeam ONE Reporter** by double-clicking the desktop shortcut.
>
> 2. [] Click the **Use Windows session credentials** check box.
>
> 3. [] Click the **Login** button.
>
> 4. [] Open the **Configuration** section.
>
> At the moment, our infrastructure is scheduled to collect data from the server automatically every three hours. Since we want to see the group we have just created in the report before it is collected and synced automatically, it's required to run the data collection manually.
>
> 5. [] Click **Servers**.
>
> 6. [] Select **VEEAM-ESX** in the list.

7. []

Click the **Run now** button on the toolbar.. []

8. []

> **Important!** Wait for the data collection to complete before proceeding.

Navigate to **Workspace**.. []

9. []

Go to **Veeam Backup Monitoring**.. []

10. []

> Scroll down and select the **Protected VMs**

report.. []

> 11. [] Choose **Business View object(s)** as the report scope.

12. []

> Click the **Click to choose** link near the **Business view object(s)** option. This will let you define Business View groups that should be analyzed in the report.
>
> Note that *1 week* is set as the **RPO**.

The report will examine whether VMs have valid backup and replica restore points created within this specified time range (RPO period).. []

> 13. [] Expand the *Veeam Courses* group.
>
> 14. [] Activate the *Course VMs* check box.

15. []

Click **OK**.. []

> 16. [] Click **Preview**. The report will open in the new tab.

17. []

> Scroll through the report. Switch between its pages using the arrow ➧ to review the information the report provides.
>
> A VM is considered to be **Protected** if there is at least one valid backup or replica restore point that meets the designated RPO for it. A VM is considered to be Unprotected if it has outdated or missing backup or replica restore points.

Close the **report preview**.. []

> 18. [] We have analyzed the backup protection of VMs in the virtual environment.
>
> **Lab 10.6. Performing an infrastructure assessment**
>
> Analyze the environment for incompatibilities and configuration errors that can potentially prevent or complicate future backup operations.

===

# Step 1. Start the VM Configuration Assessment report

> **Action Description Illustration**
>
> 1. [] Navigate to the **Workspace** tab.

2. []

Select the **VMware Infrastructure Assessment** folder.. []

3. []

> Select the **VM Configuration Assessment**

report.. []

> 4. [] Click **Preview**.

5. []

> Discuss the report findings with the instructor and the other attendees.

Close the report preview.. []


---

# Congratulations!

You have successfully completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
