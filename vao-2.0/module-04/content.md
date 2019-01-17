Module 4: Deployment and Installation
---
**This lab is expected to last a maximum of 25 minutes including lab launch.**

# Lab 4.1: Veeam Availability Orchestrator installation

1. [] Open **File Explorer** from Windows task bar.
2. [] Expand **This PC**.
3. [] Select **DVD Drive (D:)**.
4. [] Launch the **Setup.exe** file.
5. [] Close the **File Explorer** window.
6. [] Click the **Install** button.
7. [] Tick the **I accept the terms of the Veeam license agreement** check box.
8. [] Tick the **I accept the terms of the 3rd party components license agreements** check box.

8. [] Click the Next button on the **License agreement** step.
9. [] Keep the default program features and click the **Next** button on the **Program features** step.
10. [] Click the **Browse...** button.
11. [] Enter +++C:\Install\veeam_availability_orchestrator_nfr_20.lic+++ into the File name field.
12. [] Click the **Open** button.
13. [] Click the **Next** button on the **Provide License Key** step.
14. [] Keep default username: VMCE\Administrator and enter password: +++Pa%%w0rd+++.
15. [] Click the **Next** button on the **Service Account** step.
16. [] Click the **Install** button to start the installation on the **Default Configuration** step.
> Note: The installation process can take up to 25 minutes, please have some patience. The installation takes quite some time because many components need to be installed such as Microsoft SQL Server, Veeam Backup & Replication, Veaam ONE and of course Veeam Availability Orchestrator.

17. [] Click the **Finish** button to close the Veeam® Availability Orchestrator setup wizard.
18. [] Click the **Yes** button to logoff the VEEAM-VAO server.
> Note: Logoff is required because during installation of Veeam ONE, a local group named Veeam ONE Administrators is created and a user is added to it. In this lab environment you will automatically be logged back into the Desktop.

===

# Lab 4.2: Initial configuration
1. [] Launch **Veeam Availability Orchestrator** from the desktop.
2. [] Enter username: +++administrator@vmce.lab+++ and password: +++Pa%%w0rd+++.
3. [] Click the **Login** button.
4. [] Click the **Next** button on the **Welcome** step.
5. [] Enter:
 1. Name: +++Phoenix+++
 2. Site description: +++Disaster Recovery site+++
 3. Contact name: +++John Doe+++
 4. Contact email: +++administrator@vmce.lab+++.

6. [] Click the **Next** button on the **Server Details** step.
7. [] Click the **Add** button.
8. [] Enter account: +++site admin+++.
9. [] Click the **Find** button.
10. [] Select the discovered account: **Site Administrator VAO**.
11. [] Click the **Add** button.
12. [] Click the **Next** button on the **Choose Administrators** step.
13. [] Click the **Skip** button on the **Deploy VAO agent** step.
> Note: In a production environment, it would be recommended to deploy Veeam Availability Orchestrator to a separate server than your Veeam backup server. At this step, you would connect either to your Veeam Backup Server or Veeam Backup Enterprise Manager. Since this is a training environment, we will skip this step and utilize the integrated Veeam backup server.

14. [] Enter:
 1. Server: +++vcenter.vmce.lab+++
 2. User name: +++svcVeeam@vsphere.local+++
 3. Password: +++Pa%%w0rd+++.
> Note: If a 443 connection error is displayed, it could be the VMware vCenter Server services are still starting up, please wait 1-2 minutes and try again.

15. [] Click the **Next** button on the **VMware vCenter Server** step.
16. [] Click the **Finish** button on the **Summary** step.
17. [] Wait for the **Welcome! Please log in** text message and then close the **Veeam Availability Orchestrator** interface.

---

# Congratulations!

You have successfully completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
