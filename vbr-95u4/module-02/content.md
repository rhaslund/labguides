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

# Lab 2.2

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

===

# Lab 2.3

In this lab exercise, you will review the VMware Backup Proxy on the VEEAM-VBR server.

1. [] Select **Backup Proxies** in the **Backup Infrastructure** view.
2. [] Select **VMware Backup Proxy**.
3. [] Click the **Edit Proxy** button on the **Backup Proxy** ribbon.
4. [] Click the **Choose...** button in the **Transport mode** section.
> Note: At this step, you can also specify transport mode and/or connected datastores. In production environments, it is recommended to use as many tasks as the server resources (CPU/RAM) and backup target (repository/disks) can handle. 1 task equals 1 (one) CPU core.

5. [] Review the available transport modes and click the **Cancel** button.
6. [] Click the **Cancel** button on the **Server** step.
> Note: If no additional VMware Backup Proxies are added then the Veeam Backup Server will both coordinate all job activities and handle data processing itself.

7. [] Click the **Yes** button to confirm exit without applying changes.

===

# Lab 2.4
In this lab exercise, you will add the Hyper-V off-host backup proxy to the Veeam Backup Server.

1. [] Click the **Add Proxy** button on the **Backup Proxy** ribbon.
2. [] Select **Hyper-V...**.
3. [] Enter description: +++Microsoft Hyper-V Off-Host Proxy+++
3. [] Click the **Next** button on the **Server** step.
> Note: The Hyper-V role must be enabled on the server, otherwise it is not possible to add it as an off-host backup proxy.

4. [] Keep the default settings and click the **Next** button on the **Traffic Rules** step.
5. [] Keep the default settings and click the **Apply** button on the **Review** step.
6. [] Wait for the required components to be installed and configued then click the **Next** button on the **Apply** step.
> Note: Checking for updates from Windows Update could take up to 4 minutes.

7. [] Click the **Finish** button on the **Summary** step.

===

# Lab 2.5

In this lab exercise, you will add a remote Backup Repository and a second local Backup Repository.

## Step 1: Add a remote backup repository

1. [] Select **Backup Repositories** in the **Backup Infrastructure** view.
> Note: During installation, Veeam Backup & Replication checks the volumes of the machine on which you install the product and identifies a volume with the greatest amount of free disk space. On this volume, Veeam Backup & Replication creates the Backup folder that is used as the default backup repository.

2. [] Click the **Add Repository** button on the **Backup Repository** ribbon.
3. [] Select **Direct attached storage**.
4. [] Select **Microsoft Windows**.
5. [] Enter name: +++Remote Repository+++.
6. [] Click the **Next** button on the **Name** step.
7. [] Click the **Add New...** button.
> Note: The Repository servers list contains only those servers that have been added to Veeam Backup & Replication beforehand. As the VEEAM-Remote server has not been added to Veeam Backup & Replication yet, we have to go through the New Windows Server wizard first.

8. [] Enter
 1. DNS name: +++VEEAM-Remote+++
 2. Description: Remote Backup Repository
9. [] Click the **Next** button on the **Name** step.
10. [] Click the **Credentials** drop down menu.
11. [] Select **VEEAMINFRA\Administrator**.
> Note: This account should have local administrator privileges on the added Microsoft Windows Server.

12. [] Click the **Next** button on the **Credentials** step.
13. [] Click the **Apply** button on the **Review** step.
14. [] Click the **Next** button on the **Apply** step.
15. [] Click the **Finish** button on the **Summary** step.
16. [] Click the **Populate** button on the **Server** step.
17. [] Select the **X:\\** drive.
18. [] Click the **Next** button on the **Server** step.
19. [] Verify the **Path to folder** is **X:\Backups** and click the **Next** button on the **Repository** step.
> Note: The Limit read and write data rates setting is used to limit the speed with which Veeam Backup & Replication can read and write
data to/from a backup repository.

20. [] Keep the default settings and click the **Next** button on the **Mount Server** step.
21. [] Keep the default settings and click the **Apply** button on the **Review** step.
22. [] Click the **Finish** button on the **Apply** step.
23. [] Click the **Yes** button to confirm changing the configuration backup location to the newly created repository.
> Note: The new repository has been added. We have selected the configuration backup to be stored at the remote server to ensure it will remain intact if the VEEAM-VBR server crashes.

===

## Step 2: Add a local repository

1. [] Click the **Add Repository** button on the **Backup Repository** ribbon.
2. [] Select **Direct attached storage**.
3. [] Select **Microsoft Windows**.
4. [] Enter
 1. Name: +++Local Backup Repository+++
 2. Name: +++Local Backup Repository+++
5. [] Click the **Next** button on the **Name** step.
6. [] Click the **Populate** button.
7. [] Select the **E:\\** drive.
8. [] Click the **Next** button on the **Server** step.
9. [] Verify the **Path to folder** is **E:\Backups** and click the **Next** button on the **Repository** step.
10. [] Keep the default settings and click the **Next** button on the **Mount Server** page.
11. [] Keep the default settings and click the **Apply** button on the **Review** step.
12. [] Click the **Finish** button on the **Apply** step.

===

# Lab 2.6

In this lab exercise, you will deploy a local and a remote Veeam WAN Accelerator.

## Step 1: Install a local WAN accelerator

1. [] Select **WAN Accelerators** in the **Backup Infrastructure** view.
2. [] Click the **Add WAN Accelerator** button on the **WAN Accelerator** ribbon.
3. [] Verify **Choose server** already has **VEEAM-VBR.veeaminfra.local** selected then click the **Next** button on the **Server** step.
4. [] Verify the **Folder** is set to **X:\VeeamWAN** then lower the **Cache size** to +++10+++ GB.
> **Important: WARNING! Do NOT use the default cache size of 100 GB. Leaving the default cache size**

5. [] Click the **Next** on the **Cache** step.
6. [] Click the **Apply** button on the **Review** step.
7. [] Click the **Next** button on the **Apply** step.
8. [] Click the **Finish** button on the **Summary** step.

## Step 2: Install "remote" WAN accelerator

1. [] Click the **Add WAN Accelerator** button on the **WAN Accelerator** ribbon.
2. [] Click the **Choose server** drop down menu.
3. [] Select **VEEAM-Remote**.
4. [] Click the **Next** button on the **Server** step.
5. [] Verify the **Folder** is set to **X:\VeeamWAN** then lower the **Cache size** to +++10+++ GB.
> **Important: WARNING! Do NOT use the default cache size of 100 GB. Leaving the default cache size in place will result in the lab running out of space and ultimately the job will fail**. We’re using 10 GB for demonstration only. Please check the User Guide for sizing recommendations.

6. [] Click the **Next** on the **Cache** step.
7. [] Keep the default settings and click the **Apply** button on the **Review** step.
8. [] Keep the default settings and click the **Next** button on the **Apply** step.
9. [] Click the **Finish** button on the **Summary** step.
> Note: Verify both WAN accelerators are present before continuing to the next lab.

===

# Lab 2.7:

In this lab exercise, you will connect a HPE StoreVirtual VSA to the Veeam Backup Server.

1. [] Navigate to the **Storage Infrastructure** view.
2. [] Click the **Add Storage** button.
3. [] Select **Hewlett Packard Enterprise**.
4. [] Select **StoreVirtual**.
5. [] Enter
 1. Management server DNS name: +++VEEAM-VSA+++
 2. Description: +++HPE StoreVirtual VSA+++
6. [] Click the **Next** button on the **Name** step.
7. [] Click the **Add...** button
8. [] Enter:
 1. Username: +++veeam+++ (case sensitive).
 2. Password: +++veeam+++ (case sensitive).
 3. Description: +++HPE VSA admin account+++

9. [] Click the **OK** button.
10. [] Click the **Next** button on the **Credentials** step.
11. [] Click the **Yes** button to confirm trust of the remote storage system. 
> Note: Veeam Backup & Replication saves a fingerprint of the SSH key of the storage system to the Veeam Backup & Replication database. During every subsequent connection to the server, Veeam Backup & Replication uses the saved fingerprint to verify the identity of the storage system and avoid the man-in-the-middle attack.

12. [] Keep the default settings and click the **Next** button on the **Access Options** step.
13. [] Click the **Finish** button on the **Summary** step.
14. []  Wait until the storage discovery reaches status **Success** then click the **Close** button.

===

# Lab 2.8
In this lab exercise, you will connect the tape server to the Veeam Backup Server.

1. [] Navigate to the **Tape Infrastructure** view.
2. [] There are no Tape Drives or Libraries available yet. In the lab environment, the tape library is connected to the **VEEAM-Remote** server. Click the **Add Tape Server** button on the **Tape** ribbon.
3. [] Click the **Choose server:** drop down menu.
4. [] Select **VEEAM-Remote**.
5. [] Click the **Next** button on the **Server** step.
6. [] Keep the default settings and click the **Next** button on the **Traffic** step.
7. [] Click the **Apply** button on the **Review** step.
8. [] Click the **Next** button on the **Apply** step.
9. [] Click the **Finish** button on the **Summary** step.

===

# Lab 2.9

In this lab exercise, you will set locations for the already added components.

## Step 1: Setup Tape Library location

1. [] Select **Libraries** in the **Tape Infrastructure** view.
2. [] Click the **HP MSL G3 Series 1068** tape library.
3. [] Click the **Set Location** button on the **Tape Library** ribbon.
3. [] Select **Manage Locations...**.
4. [] Click the **Add...** button.
5. [] Enter name: +++Remote Site+++.
6. [] Click the **OK** button.
7. [] Click the **Add...** button.
8. [] Enter name: +++Local Site+++.
9. [] Click the **OK** button.
10. [] Click the **OK** button.
11. [] Click the **Set Location** button on the **Tape Library** ribbon.
12. [] Select **Remote**.

===

## Step 2: Setup Backup Repository locations

1. [] Navigate to the **Backup Infrastructure** view.
2. [] Select **Backup Repositories** in the **Backup Infrastructure** view.
3. [] Select **Default Backup Repository**.
4. [] Click the **Set Location** button on the **Backup Repository** ribbon.
5. [] Select **Local Site**.
6. [] Select **Local Backup Repository**.
7. [] Click the **Set Location** button on the **Backup Repository** ribbon.
8. [] Select **Local Site**.
9. [] Select **Remote Repository**.
10. [] Click the **Set Location** button on the **Backup Repository** ribbon.
11. [] Select **Remote Site**.

===

## Step 3: Setup hypervisor locations

12. [] Navigate to the **Inventory** view.
13. [] Select **VEEAM-ESX** in the **VMware vSphere** section of the **Inventory** view.
14. [] Click the **Set Location** button on the **Server** ribbon.
15. [] Select **Local Site**.
16. [] Select **VEEAM-HYPERV** in the **Microsoft Hyper-V** section of the **Inventory** view.
17. [] Click the **Set Location** button on the **Server** ribbon.
18. [] Select **Local Site**.
19. [] Close the **Veeam Backup and Replication console** window.
