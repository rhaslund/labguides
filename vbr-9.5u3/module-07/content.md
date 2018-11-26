Module 7: Verification

---
**This lab is expected to last a maximum of 45 minutes including lab launch.**


# Lab 7.1: Preparing the infrastructure

1. [] Launch the *Veeam Backup & Replication console** from the desktop.
2. [] Navigate to the **Backup Infrastructure** view.
3. [] Select **Virtual Labs** in the **SureBackup** section of the **Backup Infrastructure** view.
4. [] Click the **Add Virtual Lab** button on the **Virtual Lab** ribbon.
5. [] Select **VMware...**.
6. [] Enter name: +++VEEAM-ESX VLAB1+++.
7. [] Click the **Next** button on the **Name** step.
8. [] Click the **Choose...** button in the **Host** section.
9. [] Select the **VEEAM-ESX** host.
10. [] Click the **OK* button.
11. [] Click the **Next** button on the **Host** step.
12. [] Click the **Choose** button.
13. [] Expand the **VEEAM-ESX** host.
14. [] Select the **datastore1** datastore.
15. [] Click the **OK** button.
16. [] Click the **Next** button on the **Datastore** step.
17. [] Click the **Configure** button in the **Production network connection** section.
18. [] Click the **Browse** button.
19. [] Expand **vSwitch0**.
20. [] Select the **MGMT** port group.
21. [] Click the **Add** button.
22. [] Select the **Use the following IP address** radio button.
23. [] Enter:
 1. IP address: +++10.0.1.101+++
 2. Subnet mask: +++255.255.255.0+++
 3. Default gateway: +++10.0.1.3+++
 4. DNS server: +++10.0.1.1+++

24. [] Click the **Next** button on the **Proxy** step.
25. [] Select the **Advanced single-host (manual configuration)** radio button.
26. [] Click the **Next** button on the **Networking** step.
27. [] Click the **OK** button to dismiss the **Unable to resolve network settings** error.
28. [] Select the **MGMT** network mapping.
29. [] Click the **Remove** button.
30. [] Click the **Add...** button.
31. [] Click the **Browse...** button.
32. [] Expand the **VEEAM-ESX** host.
33. [] Expand the **vSwitch1** virtual switch.
34. [] Select the **LAN** port group.
35. [] Click the **Add** button.
36. [] Enter isolated network: ++VEEAM-ESX VLAB1 LAN+++.
> Note: Please double check that the Isolated network matches the requirements. If you need to change it, you can edit it without clicking the drop-down icon.

37. [] Click the **OK** button
38. [] Click the **Next** button on the **Isolated Networks** step.
39. [] Click the **Add...** button.
40. [] Click the **Choose isolated network to connect this vNIC to** drop down menu.
41. [] Select **VEEAM-ESX VLAB1 LAN (LAN)**.
42. [] Enter:
 1. IP address: +++10.0.3.3+++
 2. Subnet mask: +++255.255.255.0+++
 3. Masquerade network IP address: ++10.2.3.d+++
 
43. [] Untick the **Enable DHCP service on this interface** check box.
44. [] 




---

# Congratulations!

You have completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
