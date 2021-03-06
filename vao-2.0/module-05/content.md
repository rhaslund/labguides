Module 5: User Interface, User Roles & Licensing
---
**This lab is expected to last a maximum of 30 minutes including lab launch.**

# Lab 5.1: Accessing Veeam Availability Orchestrator user interface

1. [] Launch **Veeam Availability Orchestrator** from the desktop.
2. [] Enter username: +++siteadmin@vmce.lab+++ and password: +++Pa%%w0rd+++
>Note: You are no longer able to log in as administrator@vmce.lab since this account does not have sufficient permissions in Veeam Availability Orchestrator.

3. [] Click the **Login** button

5. [] Navigate to the **VMware vCenter** view.
6. [] Notice how the help system automatically opens. Click the **Suggest help topics automatically** toggle button to disable the automatic help system feature.
7. [] Click the **X** in the **VMware vCenter** help window.
> Note: You can always click the Info icon in the bottom left corner to see these tips.

8. [] Verify the **vcenter.vmce.lab** server is connected and version **6.5.0**, then navigate to the **Users and Scopes** view.
8. [] Take notice of which roles are available and then navigate to the **License** view.
9. [] Click the **Details...** text link next to the **Status** row.
10. [] Verify the license is valid and that zero licenses have been consumed then click the **OK** button.
11. [] Navigate to the **Config Check** view.
> Note: Notice that the first to-do list item **Integrate with Veeam Backup & Replication server** is not completed. This is because no replication jobs have been set up yet. Notice that the third to-do list item **Configure Veeam DataLabs** is also not completed, this is because we didn't create any virtual labs in Veeam Backup & Replication yet.

12. [] Close the **Veeam Availability Orchestrator** window.

===

# Lab 5.2: Prepare Veeam Backup & Replication: Install new license

1. [] Launch the **Veeam Backup & Replication console** from the desktop.
2. [] Click the **Connect** button.
3. [] Click the **main menu** button in the top left corner.
4. [] Select **License**.
5. [] Click the **Install License** button.
6. [] Enter +++C:\Install\veeam_availability_suite_nfr_2_2.lic+++ in the File name field.
7. [] Click the **Open** button.
8. [] Click the **Close** button.

===

# Lab 5.3: Prepare Veeam Backup & Replication: Create replication jobs

## Step 1: Create a replication job for DataLab testing

1. [] Open the **Backup Infrastructure** view.
2. [] Notice that the **vcenter.vmce.lab** server is already present because it was added in Veeam Availability Orchestrator. Navigate back to the **Home** view.
3. [] Click the **Replication Job** button.
4. [] Select **Virtual machine**.
5. [] Enter name: +++VAO Lab Group Active Directory+++.
6. [] Click the **Next** button on the **Name** step.
7. [] Click the **Add...** button.
8. [] Expand the **vcenter.vmce.lab** object.
9. [] Expand the **DR** data center.
10. [] Expand the **esx02.vmce.lab** host.
11. [] Select the **DC02** virtual machine.
12. [] Click the **Add** button.
13. [] Click the **Next** button on the **Virtual Machines** step.
14. [] Click the **Choose...** button in the **Host or cluster** section.
15. [] Expand the **vcenter.vmce.lab** object.
16. [] Expand the **DR** data center.
17. [] Select the **esx02.vmce.lab** host.
18. [] Click the **OK** button.
19. [] Click the **Next** button on the **Destination** step.
20. [] Lower the amount of restore points to keep to +++1+++ (one).
21. [] Click the **Next** button on the **Job Settings** step.
22. [] Keep the default settings and click the **Next** button on the **Data Transfer** step.
23. [] Tick the **Enable application-aware processing** check box.
24. [] Click the **Add...** button.
25. [] Select the **Standard account...** button.
26. [] Enter username +++administrator@vmce.lab+++ and password +++Pa%%w0rd+++
27. [] Click the **OK** button.
28. [] Click the **Test Now** button.
29. [] Verify all tests were successful and then click the **Close** button.
30. [] Click the **Next** button on the **Guest Processing** step.
31. [] Tick the **Run the job automatically** check box.

31. [] Click the **Apply** button on the **Schedule** step.
32. [] Tick the **Run the job when I click Finish** check box.
33. [] Click the **Finish** button on the **Summary** step.
> Do not wait for the job to complete before moving to the next lab step.

===

## Step 2: Create a replication job for SharePoint

1. [] Click the **Replication Job** button.
2. [] Select **Virtual machine**.
3. [] Enter name: +++Replication Job SharePoint+++.
4. [] Tick the **Separate virtual networks** check box.
5. [] Tick the **Different IP addressing scheme** check box.
6. [] Click the **Next** button on the **Name** step.
7. [] Click the **Add...** button.
8. [] Expand the **vcenter.vmce.lab** object.
9. [] Expand the **Production** data center.
10. [] Expand the **esx01.vmce.lab** host.
11. [] Select the **SharePoint** virtual machine.
12. [] Click the **Add** button.
13. [] Click the **Next** button on the **Virtual Machines** step.
14. [] Click the **Choose...** button in the **Host or cluster** section.
15. [] Expand the **vcenter.vmce.lab** object.
16. [] Expand the **DR** data center.
17. [] Select the **esx02.vmce.lab** host.
18. [] Click the **OK** button.
19. [] Click the **Next** button on the **Destination** step.
20. [] Click the **Add...** button.
21. [] Click the **Browse...** button in the **Source network** section.
22. [] Expand the **vcenter.vmce.lab** object.
23. [] Expand the **esx01.vmce.lab** host.
24. [] Select the **PROD LAN** network.
25. [] Click the **OK** button.
26. [] Click the **Browse...** button in the **Target network** section.
27. [] Expand the **esx02.vmce.lab** host.
28. [] Select the **DR** network.
29. [] Click the **OK** button.
30. [] Click the **OK** button to close the **Network Mapping** window.
31. [] Click the **Next** button on the **Network** step.
32. [] Click the **Add...** button.
33. [] Enter the following settings:
 1. Source VM IP address: **192.168.1.\***
 2. Target VM IP address: **192.168.2.\***
 3. Default gateway: +++192.168.2.1+++
 4. Preferred DNS server: +++192.168.2.4+++
 5. Alternate DNS server: +++192.168.1.101+++
34. [] Click the **OK** button.
35. [] Click the **Next** button on the **Re-IP** step.
36. [] Lower the amount of restore points to keep to +++1+++ (one).
37. [] Click the **Next** button on the **Job Settings** step.
> Note: In a production environment, it is critical to have redundant backup proxies on each site.

38. [] Keep the default settings and click the **Next** button on the **Data Transfer** step.
39. [] Tick the **Enable application-aware processing** check box.
40. [] Click the **Guest OS credentials** drop-down list.
41. [] Select the **administrator@vmce.lab** credential.
42. [] Click the **Next** button on the **Guest Processing** step.
43. [] Tick the **Run the job automatically** check box.
44. [] Click the **Apply** button on the **Schedule** step.
45. [] Tick the **Run the job when I click Finish button** check box.
46. [] Click the **Finish** button.
> Do not wait for the jobs to complete before moving to the next lab step.

===

# Lab 5.4: Prepare Veeam Backup & Replication: Create a backup job

1. [] Click the **Backup Job** button on the **Home** ribbon.
3. [] Select **Virtual machine...**
4. [] Enter name: +++Backup Job Exchange+++.
5. [] Click the **Next** button on the **Name** step.
6. [] Click the **Add...** button.
7. [] Expand the **Production** data center.
8. [] Expand the **esx01.vmce.lab** host.
9. [] Select the **EXCHANGE** virtual machine.
10. [] Click the **Add** button.
11. [] Click the **Next** button on the **Virtual Machines** step.
12. [] Lower the amount of restore points to keep on disk to +++1+++ (one).
13. [] Click the **Next** button on the **Storage** step.
14. [] Tick the **Enable application-aware processing** check box.
15. [] Select the **Guest OS credentials** dropdown menu.
16. [] Select **administrator@vmce.lab** in the dropdown menu.
17. [] Click the **Next** button on the **Guest Processing** step.
18. [] Tick the **Run the job automatically** check box.
19. [] Click the **Apply** button on the **Schedule** step.
20. [] Tick the **Run the job when I click Finish** check box.
21. [] Click on the **Finish** button on the **Summary** step.
> Do not wait for the jobs to complete before moving to the next lab exercise.

===

# Lab 5.5: Prepare Veeam Backup & Replication: Create new virtual labs

## Step 1: Create a virtual lab for SharePoint

1. [] Navigate to the **Backup Infrastructure** view.
2. [] Select **SureBackup** in the **Backup Infrastructure** navigation pane.
3. [] Click the **Add Virtual Lab** button.
4. [] Enter name: +++VLAB1+++.
5. [] Click the **Next** button on the **Name** step.
6. [] Click the **Choose...** button.
7. [] Expand the **vcenter.vmce.lab** object.
8. [] Expand the **DR** data center.
9. [] Select the **esx02.vmce.lab** host.
10. [] Click the **OK** button.
11. [] Click the **Next** button on the **Host** step.
12. [] Tick the **Redirect write cache** check box.
13. [] Click the **Choose...** button.
14. [] Expand the **esx02.vmce.lab** host.
15. [] Select the **ESX02:Local** datastore.
16. [] Click the **OK** button.
17. [] Click the **Next** button on the **Datastore** step.
18. [] Click the **Configure...** button in the **Proxy Appliance** section.
19. [] Select the **Use the following IP address** radio button.
20. [] Enter the following settings:
 1. IP address: +++192.168.2.6+++
 2. Subnet mask: +++255.255.255.0+++
 3. Default gateway: +++192.168.2.1+++
 4. Preferred DNS server: +++192.168.2.4+++
 5. Alternate DNS server: +++192.168.1.101+++

21. [] Click the **OK** button.
22. [] Click the **Next** button on the **Proxy** step.
23. [] Click the **Advanced single-host** radio button.
24. [] Click the **Next** button on the **Networking** step.
25. [] Click the **OK** button to ignore the **Unable to resolve default network settings** error.
26. [] Click the **Add...** button.
27. [] Click the **Browse...** button.
28. [] Expand the **vcenter.vmce.lab** object.
29. [] Expand the **esx02.vmce.lab** host.
30. [] Expand the **vSwitch0** switch.
31. [] Select the **DR** network.
32. [] Click the **Add** button.
33. [] Click the **OK** button.
34. [] Click the **Next** button on the **Isolated Networks** step.
35. [] Click the **Add...** button.
36. [] Click the **Choose isolated network** dropdown list.
37. [] Select **VLAB1 DR (DR)**.
38. [] Click the **OK** button to ignore the **Unable to resolve network settings** warning.
39. [] Enter:
 1. IP address: +++192.168.2.1+++
 2. Mask: +++255.255.255.0+++

40. [] Untick the **Enable DHCP service on this interface** check box.
41. [] Click the **OK** button.
42. [] Click the **Next** button on the **Network Settings** step.
43. [] Keep the default settings on the **Static Mapping** step and click the **Next** button.
44. [] Click the **Apply** button on the **Ready to apply** step.
45. [] Click the **Finish** button on the **Applying Configuration** step.

===

## Step 2: Create a virtual lab for Exchange

1. [] Click the **Add Virtual Lab** button.
2. [] Enter name: +++VLAB2+++.
3. [] Click the **Next** button on the **Name** step.
4. [] Click the **Choose...** button.
5. [] Expand the **vcenter.vmce.lab** object.
6. [] Expand the **DR** data center.
7. [] Select the **esx02.vmce.lab** host.
8. [] Click the **OK** button.
9. [] Click the **Next** button on the **Host** step.
10. [] Tick the **Redirect write cache** check box.

10. [] Click the **Choose...** button.
11. [] Expand the **esx02.vmce.lab** host.
12. [] Select the **ESX02:Local** datastore.
13. [] Click the **OK** button.
14. [] Click the **Next** button on the **Datastore** step.
15. [] Click the **Configure...** button in the **Production network connection** section.
16. [] Select the **Use the following IP address** radio button.
17. [] Enter the following settings:
 1. IP address: +++192.168.2.7+++
 2. Subnet mask: +++255.255.255.0+++
 3. Default gateway: +++192.168.2.1+++
 4. Preferred DNS server: +++192.168.2.4+++
 5. Alternate DNS server: +++192.168.1.101+++

18. [] Click the **OK** button.
19. [] Click the **Next** button on the **Proxy** step.
20. [] Click the **Advanced single-host** radio button.
21. [] Click the **Next** button on the **Networking** step.
22. [] Click the **OK** button to ignore the **Unable to resolve default network settings** error.
23. [] Click the **Add...** button.
24. [] Click the **Browse...** button.
25. [] Expand the **vcenter.vmce.lab** object.
26. [] Expand the **esx02.vmce.lab** host.
27. [] Expand the **vSwitch0** switch.
28. [] Select the **DR** network.
29. [] Click the **Add** button.
30. [] Click the **OK** button.
31. [] Click the **Next** button on the **Isolated Networks** step.
32. [] Click the **Add...** button.
33. [] Click the **Choose isolated network** dropdown list.
34. [] Select **VLAB2 DR (DR)**.
35. [] Click the **OK** button to ignore the **Unable to resolve network settings** warning.
36. [] Enter:
 1. IP address: +++192.168.2.1+++
 2. Mask: +++255.255.255.0+++
 3. Masquerade network IP address: **192.168.254.D**

37. [] Untick the **Enable DHCP service on this interface** check box.
38. [] Click the **OK** button.
39. [] Click the **Next** button on the **Network Settings** step.
40. [] Keep the default settings on the **Static Mapping** step and click the **Next** button.
41. [] Click the **Apply** button on the **Ready to apply** step.
42. [] Click the **Finish** button on the **Applying Configuration** step.
43. [] Close the **Veeam Backup & Replication** window.

---

# Congratulations!

You have successfully completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
