Module 7: DataLabs
---
**This lab is expected to last a maximum of 25 minutes including lab launch.**

# Lab 7.1: Configuration of DataLabs

## Step 1: Add default lab group to VLAB1

1. [] Launch **Veeam Availability Orchestrator** from the desktop.
2. [] Enter username: +++siteadmin@vmce.lab+++ and password: +++Pa%%w0rd+++.
3. [] Click the **Login** button.
> Note: Because the server was just started, the spinning icon may display for up to two minutes while services complete their startup.

4. [] Navigate to the **DataLabs** view.
5. [] Select the **VEEAM-VAO\VLAB1** DataLab.
> Note: Do not click on the text link VEEAM-VAO\VLAB1

6. [] Click the **Edit** button.
7. [] Click the **Add** button in the **Lab Groups** pane.
8. [] Keep the default selection of Failover and click the **Next** button on the **Lab Group Type** step.
9. [] Select the **VAO Testing Only - Active Directory Servers** VM Group.
10. [] Click the **Add** button.
11. [] Click the **Next** button on the **VM Groups** step.
12. [] Keep the defaults and click the **Next** button on the **VM Recovery Options** step.
13. [] Select **Prepare DC for Test Lab**.
14. [] Click the **Add** button.
15. [] Scroll down until **Verify Global Catalog Port** is visible.
16. [] Hold the keyboard **CTRL** button and select the following items: **Select Ping VM Network**, **Verify DNS Port** and **Verify Domain Controller Port**.
17. [] Click the **Add** button.
18. [] Click the **Next** button on the **VM Steps** step.
19. [] Click the **Finish** button on the **Summary** step.
20. [] Click the **Save** button.
21. [] Click the **OK** button to confirm saving the changes to the DataLab configuration.
22. [] Click the **Left arrow** button next to the **Edit Lab VEEAM-VAO\VLAB1** text.

===

## Step 2: Add default lab group to VLAB2

1. [] Select the **VEEAM-VAO\VLAB2** DataLab.
> Note: Do not click on the text link VEEAM-VAO\VLAB2

2. [] Click the **Edit** button.
3. [] Click the **Add** button in the **Lab Groups** pane.
4. [] Keep the default selection of Failover and click the **Next** button on the **Lab Group Type** step.
5. [] Select the **VAO Testing Only - Active Directory Servers** VM Group.
6. [] Click the **Add** button.
7. [] Click the **Next** button on the **VM Groups** step.
8. [] Keep the defaults and click the **Next** button on the **VM Recovery Options** step.
9. [] Select **Prepare DC for Test Lab**.
10. [] Click the **Add** button.
11. [] Scroll down until **Verify Global Catalog Port** is visible.
12. [] Hold the keyboard **CTRL** button and select the following items: **Select Ping VM Network**, **Verify DNS Port** and **Verify Domain Controller Port**.
13. [] Click the **Add** button.
14. [] Click the **Next** button on the **VM Steps** step.
15. [] Click the **Finish** button on the **Summary** step.
16. [] Click the **Save** button.
17. [] Click the **OK** button to confirm saving the changes to the DataLab configuration.
18. [] Click the **Left arrow** button next to the **Edit Lab VEEAM-VAO\VLAB2** text.

===

# Lab 7.2: Test DataLab VLAB1

1. [] Click the **VEEAM-VAO\VLAB1** DataLab text link.
2. [] Click the **Run** button.
3. [] Keep the default selection and click the **Next** button on the **Power Options** step.

3. [] Notice that the **VAO Testing Only – Active Directory Servers** Lab Group has already been added and that it is not possible to remove it. This is because you as a administrator earlier added this lab group as a **default lab group**. Click the **Next** button on the **Choose Lab Groups** step.
4. [] Click the **Finish** button on the **Summary** step.
5. [] Select **Lab Appliance** in the **Lab Groups** pane.
6. [] Wait for the **Lab Appliance Details** section to display: **DataLab appliance powered on successfully** (this can take up to three minutes). Select **VAO Testing Only - Active Directory Servers** in the **Lab Groups** pane.
7. [] Select **DC02** in the **Virtual Machines** pane.
8. [] Wait for all items in the **Steps** pane to be marked **Completed** with a green checkmark. Click the **Left arrow** button next to the **Lab Details: VEEAM-VAO\VLAB1** text.
> Note: It can take up to 8 minutes to complete all tests of the DC02 virtual machine, please have some patience.

9. [] Click the **Power Off** button.
10. [] Click the **Power Off** button to confirm powering off the DataLab.
11. [] Close the **Veeam Availability Orchestrator** window.

---

# Congratulations!

You have successfully completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
