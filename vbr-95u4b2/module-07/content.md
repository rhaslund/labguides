Module 7: Verification

---
**This lab is expected to last a maximum of 45 minutes including lab launch.**


# Lab 7.1: Preparing the infrastructure

1. [] Launch the **Veeam Backup & Replication console** from the desktop.
2. [] Click the **Connect** button.
3. [] Navigate to the **Backup Infrastructure** view.
4. [] Select **Virtual Labs** in the **SureBackup** section of the **Backup Infrastructure** view.
5. [] Click the **Add Virtual Lab** button on the **Virtual Lab** ribbon.
6. [] Select **VMware...**.
7. [] Enter name: +++VEEAM-ESX VLAB1+++.
8. [] Click the **Next** button on the **Name** step.
9. [] Click the **Choose...** button in the **Host** section.
10. [] Select the **VEEAM-ESX** host.
11. [] Click the **OK** button.
12. [] Click the **Next** button on the **Host** step.
13. [] Keep the default settings and click the **Next** button on the **Datastore** step.
14. [] Click the **Configure...** button.
15. [] Click the **Browse...** button.
16. [] Expand **vSwitch0**.
17. [] Select the **MGMT** port group.
18. [] Click the **Add** button.
19. [] Select the **Use the following IP address** radio button.
20. [] Enter:
 1. IP address: +++10.0.1.101+++
 2. Subnet mask: +++255.255.255.0+++
 3. Default gateway: +++10.0.1.3+++
 4. DNS server: +++10.0.1.1+++

21. [] Click the **OK** button.
22. [] Click the **Next** button on the **Proxy** step.
23. [] Select the **Advanced single-host (manual configuration)** radio button.
24. [] Click the **Next** button on the **Networking** step.
25. [] Select the **MGMT** network mapping.
26. [] Click the **Remove** button.
27. [] Click the **Add...** button.
28. [] Click the **Browse...** button.
29. [] Expand the **VEEAM-ESX** host.
30. [] Expand the **vSwitch1** virtual switch.
31. [] Select the **LAN** port group.
32. [] Click the **Add** button.
33. [] Click the **OK** button
34. [] Click the **Next** button on the **Isolated Networks** step.
35. [] Click the **Add...** button.
36. [] Click the **Choose isolated network to connect this vNIC to** drop down menu.
37. [] Select **VEEAM-ESX VLAB1 LAN (LAN)**.
38. [] Click the **OK** button to dismiss the **Unable to resolve network settings** error.
39. [] Enter:
 1. IP address: +++10.0.3.3+++.
 2. Subnet mask: +++255.255.255.0+++.
 3. Masquerade network IP address: **10.2.3.d**.
 
40. [] Untick the **Enable DHCP service on this interface** check box.
41. [] Click the **OK** button.
42. [] Click the **Next** button on the **Network Settings** step.
43. [] Keep the default settings and click the **Next** button on the **Static Mapping** step.
> Note: Static IP mapping is used when it is necessary to provide many clients with access to an isolated VM. The static IP address is assigned to the proxy appliance network adapter connected to the production network, and IP traffic directed to the specified static IP address is routed by the proxy appliance to the VM powered on in the isolated network.

44. [] Click the **Apply** button on the **Ready to Apply** step.
45. [] Click the **Finish** button on the **Applying Configuration** step.

===

## Step 2: Connect an existing VEEAM-ESX VLAB2

1. [] Click the **Connect Virtual Lab** button on the **Virtual Lab** ribbon.
2. [] Select **VMware...**.
3. [] Expand the **VEEAM-ESX** host.
4. [] Select **VEEAM-ESX VLAB2 - Predefined**
> Note: If you don't see VEEAM-ESX VLAB2 - Predefined please request assistance from your instructor.

5. [] Click the **Connect** button.
6. [] Select the **VEEAM-ESX VLAB2 - Predefined** virtual lab.
7. [] Click the **Edit Virtual Lab** button on the **Virtual Lab** ribbon.
8. [] Keep the default settings and click the **Next** button on the **Name** step.
> Note: To load the settings for this predefined lab we will click Next on all steps until the end, then click the Finish button

9. [] Keep the default settings and click the **Next** button on the **Host** step.
10. [] Keep the default settings and click the **Next** button on the **Datastore** step.
11. [] Keep the default settings and click the **Next** button on the **Proxy** step.
12. [] Verify that the **Advanced single-host (manual configuration)** radio button is selected and click the **Next** button on the **Networking** step.
13. [] Keep the default settings and click the **Next** button on the **Isolated Networks** step.
14. [] Keep the default settings and click the **Next** button on the **Network Settings** step.
15. [] Keep the default settings and click the **Next** button on the **Static Mapping** step.
16. [] Click the **Apply** button on the **Ready to Apply** step.
17. [] Click the **Finish** button on the **Applying Configuration** step.
> Note: We need to perform this step to confirm that the validity of the settings (network mapping and configuration) will be checked and that these settings will be written into the Veeam Backup & Replication database.

===

## Step 3: Add an application group

1. [] Select **Application Groups** in the **SureBackup** section of the **Backup Infrastructure** view.
2. [] Click the **Add Group** button on the **Application Group** ribbon.
3. [] Select **VMware...**.
4. [] Enter name: +++Active Directory+++.
5. [] Click the **Next** button on the **Name** step.
6. [] Click the **Add VM** button.
7. [] Select **From backups...**.
8. [] Expand the **Backup Active Directory** job.
9. [] Select the **VEEAM-DC01** virtual machine.
10. [] Click the **Add** button.
11. [] Select the **VEEAM-DC01** virtual machine.
12. [] Click the **Edit...** button.
13. [] Tick the **DNS server** check box.
14. [] Tick the **Domain Controller (Authoritative Restore)** check box.
15. [] Tick the **Global Catalog** check box.
16. [] Click the **Startup Options** tab.
> Note: The stabilization process (waiting for the VM to reach the stabilization point: the VM boots and reports it is ready for tests) cannot exceed the value specified in the Maximum allowed boot time field. If the stabilization point cannot be determined within the Maximum allowed boot time, the recovery verification process will complete and display a timeout error. Because of this, you should be careful when specifying this value. Typically, a VM started by a SureBackup job requires more time to boot than a VM started regularly. If such an error occurs, you will need to increase the Maximum allowed boot time value and start the job again.

17. [] Click the **OK** button.
18. [] Click the **Next** button on the **Virtual Machines** step.
19. [] Click the **Finish** button on the **Summary** step.

===

# Lab 7.2: Using SureBackup

1. [] Navigate to the **Home** view.
3. [] Click the **SureBackup Job** button on the **Home** ribbon.
4. [] Select **VMware...**.
5. [] Enter:
 1. Name: +++SureBackup Exchange and SharePoint+++.
 2. Description: +++Verifying VEEAM-EX01+++.

6. [] Click the **Next** button on the **Name** step.
7. [] Keep the default settings and click the **Next** button on the **Virtual Lab** step.
8. [] Click the **Application group** drop down menu.
9. [] Select the **Active Directory** application group.
10. [] Click the **Next** button on the **Application Group** step.
> Note: If the Keep the application group running after the job completes option is enabled, the lab would not be powered off when the SureBackup Job completes, and you would be able to perform application item-level restore (U-AIR®) or use On-Demand Sandbox™ for testing, troubleshooting or training.

11. [] Tick the **Link jobs** check box.
12. [] Click the **Add...** button.
13. [] Select the **Backup Exchange & SharePoint** job.
14. [] Click the **OK** button.
15. [] Click the **Advanced** button.
16. [] Click the **Add...** button.
17. [] Expand the **Backup Exchange & SharePoint** job.
18. [] Select the **VEEAM-EX01** virtual machine.
19. [] Hold the **SHIFT** keyboard button and select the **VEEAM-SP01** virtual machine.
20. [] Click the **Add** button.
21. [] Select the **VEEAM-EX01** virtual machine.
22. [] Click the **Edit...** button.
23. [] Tick the **Mail Server** check box.
24. [] Click the **OK** button in the Verification Options window.
25. [] Select the **VEEAM-SP01** virtual machine.
26. [] Click the **Edit...** button.
27. [] Tick the **SQL Server** check box.
28. [] Tick the **Web Server** check box.
29. [] Click the **OK** button in the Verification Options window.
30. [] Click the **OK** button in the Vertification Settings window.
31. [] Click the **Next** button on the **Linked Jobs** step.
32. [] Keep the default settings and click the **Next** button on the **Settings** step.
33. [] Tick the **Run the job automatically** check box.
34. [] Select the **Monthly at this time** radio button.
35. [] Click the **Apply** button on the **Schedule** step.
36. [] Tick the **Run the job when I click Finish** check box.
37. [] Click the **Finish** button on the **Summary** step.
> **Important: A SureBackup Job will take a while, do NOT wait for it to complete before proceeding to the next lab.**

===

# Lab 7.3: Using SureReplica

1. [] Select **SureBackup** in the **Jobs** section of the **Home** view.
2. [] Click the **SureBackup Job** on the **Home** ribbon.
3. [] Select **VMware...**.
4. [] Enter:
 1. Name: +++SureReplica Tiny-Veeam+++.
 2. Description: +++Verifying Tiny-Veeam replica+++

5. [] Click the **Next** button on the **Name** step.
6. [] Click the **Virtual lab** drop down menu.
7. [] Select the **VEEAM-ESX VLAB2 - Predefined** virtual lab.
> Note: We recommend using the Virtual Lab that was created earlier for SureBackup and the VEEAM-ESX VLAB2 - Predefined for a SureReplica job because it allows two verification jobs to run at the same time and cuts down on waiting time. Otherwise, if SureReplica is launched while SureBackup is still running (already using VEEAM-ESX VLAB1), you will get an error message ("virtual lab in use").

8. [] Click the **Next** button on the **Virtual Lab** step.
9. [] Keep the default settings and click the **Next** button on the **Application Group** step.
10. [] Tick the **Link jobs** check box.
11. [] Click the **Add...** button.
12. [] Select the **Replication Tiny-Veeam** job.
13. [] Click the **OK** button.
14. [] Select the **Replication Tiny-Veeam** job.
15. [] Click the **Edit...** button.
16. [] Click the **Startup Options** tab.
17. [] Untick the **VM responds to ping on any network interface** check box.
> Note: In case a virtual machine does not respond to ping, for example due to a firewall this test can be disabled.

18. [] Click the **OK** button.
19. [] Click the **Next** button on the **Linked Jobs** step.
20. [] Keep the default settings and click the **Next** step.
21. [] Tick the **Run the job automatically** check box.
22. [] Select the **Monthly at this time** radio button.
23. [] Click the **Apply** button on the **Schedule** step.
24. [] Tick the **Run the job when I click Finish** check box.
25. [] Click the **Finish** button on the **Summary** step.
> **Important: Do NOT wait for these SureBackup jobs to complete. Instead inform your instructor that you have completed this lab.**

---

# Congratulations!

You have completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
