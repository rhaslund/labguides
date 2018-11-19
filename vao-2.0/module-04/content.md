Module 4: Deployment and Installation
This lab is expected to last a maximum of 25 minutes including lab launch.
---

## Lab 4.1: Veeam Availability Orchestrator installation

1. [] Open **File Explorer** from Windows task bar.
2. [] Expand **This PC**.
3. [] Select **DVD Drive (D:)**.
4. [] Launch the **Setup.exe** file.
5. [] Close the **File Explorer** window.
6. [] Click the **Install** button.
7. [] Select the **I accept the terms in the license agreement** radio button.
8. [] Click the Next button.
9. [] Keep the default program features and click the **Next** button.
10. [] Click the **Browse...** button.
11. [] Enter C:\Install\veeam_availability_orchestrator_nfr_20.lic into the File name field.
12. [] Click the **Open** button.
13. [] Click the **Next** button.
14. [] Keep default username: VMCE\Administrator and enter password: +++Pa%%w0rd+++.
15. [] Click the **Next** button.
16. [] Click the **Install** button to start the installation.
> Note: The installation process will take up to 15 minutes.

17. [] Click the **Finish** button to close the Veeam® Availability Orchestrator setup wizard.
18. [] Click the **Yes** button to logoff the VEEAM-VAO server.
> Note: Logoff is required because during installation of Veeam ONE, a local group named Veeam ONE Administrators and added a user to it.

===

## Lab 4.2: Initial configuration
1. [] Launch **Veeam Availability Orchestrator** from the desktop.
2. [] Enter username: +++administrator@vmce.lab+++ and password: +++Pa%%w0rd+++.
3. [] Click the **Login** button.
4. [] Click the **Next** button on the Welcome step.
5. [] Keep the default selection of **DR Site** and click the **Next** button.
> Note: Site type cannot be changed after initial configuration.

6. [] Enter name: +++Phoenix+++, site description: +++Disaster Recovery site+++, contact name: +++John Doe+++, and contact email: +++administrator@vmce.lab+++.
7. [] Click the **Next** button.
8. [] Click the **Add** button.
9. [] Enter account: +++site admin+++.
10. [] Click the ***Find*** button.
11. [] Select the discovered account: ***Site Administrator VAO***.
12. [] Click the **Add** button.
13. [] Click the **Next** button on the **Choose Site Administrators** step.
14. [] Click the **Skip** button on the **Deploy VAO agent** step.
> Note: In a production environment, it would be recommended to deploy Veeam Availability Orchestrator to a separate server than your Veeam backup server. At this step, you would connect either to your Veeam Backup Server or Veeam Backup Enterprise Manager. Since this is a training environment, we will skip this step and utilize the integrated Veeam backup server.

15. [] Enter server: +++vcenter.vmce.lab+++, username: +++svcVeeam@vsphere.local+++ and password: +++Pa%%w0rd+++.
16. [] Click the **Next** button on the **VMware Server** step.
17. [] Click the **Finish** button.
18. [] Wait for the Welcome! Please log in text message and then close the **Veeam Availability Orchestrator** interface.

---

# Congratulations!

You have successfully completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
