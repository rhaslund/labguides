# Lab 2.1
In this lab exercise you will add the Veeam Backup & Replication backup server to Veeam Backup Enterprise Manager.

1. [] Launch the **Veeam Backup Enterprise Manager** from the desktop.
> Note: Because single sign-on is allowed, you will not be prompted for any username or password.

2. [] Click the **Configuration** button in the top right corner.
3. [] Click the **Add...** button.
4. [] Click the **Yes** button to accept pushing licenses from the Enterprise Manager server to all connected backup servers.
5. [] Enter:
 1. DNS name: +++veeam-vbr.veeaminfra.local+++
 2. User name: +++VEEAMINFRA\Administrator+++
 3. Password: +++Pa$$w0rd+++

6. [] Click the **OK** button to add the server.
7. [] In the Google Chrome **Save Password?** dialogue window, click the **Never** button.
8. [] Select the **veeam-vbr.veeaminfra.local** backup server.
9. [] Click the **Schedule...** button.
10. [] Reduce the collection interval to +++2+++ (two) minutes to fit our lab needs.
11. [] Click the **OK** button.
12. [] Navigate to the **Sessions** view.
13. [] Check if any errors of automatically started collection processes occur, then close the **Veeam Backup Enterprise Manager** window.
> Note: The initial configuration of Veeam Backup Enterprise Manager is completed. We will use it in a later
lab

14. [] Close the **Veeam Backup Enterprise Manager** window.

===

# Lab 3.1

In this lab exercise you will add a VMware vSphere ESXi host and a Microsoft Hyper-V host to the Veeam Backup Server.

## Step 1: Add the VMware vSphere ESXi host

1. [] Launch the **Veeam Backup & Replication console** from the desktop.
2. [] Click the **Connect** button.
3. [] Navigate to the **Backup Infrastructure** view.
4. [] Click the **Add Server** button on the **Server** ribbon.
5. [] Select **VMware vSphere**.
6. [] Select **vSphere**.
7. [] Enter:
 1. DNS name: +++VEEAM-ESX+++
 2. Description: +++VMware vSphere ESXi host+++
 
8. [] Click the **Next** button on the **Name** step.
9. [] Click the **Add...** button.
10. [] Enter:
 1. Username: +++root+++
 2. Password: +++Pa$$w0rd+++
 3. Description: +++VEEAM-ESX+++

11. [] Click the **OK** button.
12. [] Click the **Next** button on the **Credentials** step.
13. [] Click the **Continue** button to dismiss the certificate security alert.
> Note: When you add a vCenter Server or ESX(i) host, Veeam Backup & Replication saves a thumbprint of the SSL certificate installed on the vCenter Server or ESXi host to the Veeam Backup & Replication database. During every subsequent connection to the server, Veeam Backup & Replication uses the saved thumbprint to verify the identity of the server and avoid the man-in-the-middle attack.

14. [] Click the **Finish** button on the **Summary** step.

===

## Step 2: Add a standalone Hyper-V host

1. [] Click the **Add Server** button on the **Server** ribbon.
2. [] Select **Microsoft Hyper-V**.
3. [] Select **Hyper-V**.
4. [] Enter
 1. DNS name: +++VEEAM-HYPERV+++
 2. Description: +++Microsoft Hyper-V host+++
 
5. [] Click the **Next** button on the **Name** step.
6. [] Select the **Microsoft Hyper-V server (standalone)** radio button.
7. [] Click the **Next** button on the **Type** step.
8. [] Click the **Add...** button next to the **Credentials** drop down menu.
9. [] Enter:
 1. Username: +++VEEAMINFRA\Administrator+++
 2. Password: +++Pa$$w0rd+++
 3. Description: +++VEEAMINFRA domain administrator+++

10. [] Click the **OK** button.
> Note: Generally, you would need to select credentials for the account that has local administrator permissions on the added Hyper-V Server. In our case, the Hyper-V server is domain joined, so we’re using a domain credential.

11. [] Click the **Next** button on the **Credentials** step.
12. [] Keep the default settings and click the **Apply** button on the **Apply** step.
13. [] Click the **Next** button on the **Results** step.
14. [] Click the **Finish** button on the **Summary** step.
15. [] Select **Microsoft Hyper-V** in the **Managed Servers** section of the **Backup Infrastructure** view.
> Note: The VEEAM-HYPERV host is now added to the Veeam Backup & Replication user interface.
