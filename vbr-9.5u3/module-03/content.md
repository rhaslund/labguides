Module 3: Initial Configuration
---
**This lab is expected to last a maximum of 40 minutes including lab launch.**

# Lab 3.1: Connecting virtual infrastructure servers

Add a vSphere host and a Hyper-V host to Veeam Backup & Replication.

## Step 1: Add vSphere Server or standalone ESXi

1. [] Launch the **Veeam Backup & Replication console** from the desktop.
2. [] Click the **Connect** button.
3. [] Navigate to the **Backup Infrastructure** view.
4. [] Click the **Add Server** button on the **Server** ribbon.
5. [] Select **VMware vSphere**.
6. [] Enter DNS name: +++VEEAM-ESX+++
7. [] Click the **Next** button on the **Name** step.
8. [] Click the **Add...** button.
9. [] Enter:
 1. Username: +++root+++
 2. Password: +++Pa$$w0rd+++
 3. Description: +++VEEAM-ESX+++

10. [] Click the **OK** button.
11. [] Click the **Next** button on the **Credentials** step.
12. [] Click the **Connect** button to dismiss the security warning.
> Note: When you add a vCenter Server or ESX(i) host, Veeam Backup & Replication saves a thumbprint of the SSL certificate installed on the vCenter Server or ESX(i) host to the Veeam Backup & Replication database. During every subsequent connection to the server, Veeam Backup & Replication uses the saved thumbprint to verify the identity of the server and avoid the man-in-the-middle attack.

13. [] Click the **Finish** button on the **Summary** step.

===

## Step 2: Add a standalone Hyper-V Server

1. [] Select **Managed Servers** in the **Backup Infrastructure** view.
2. [] Click the **Add Server** button on the **Server** ribbon.
3. [] Select **Microsoft Hyper-V**.
4. [] Enter DNS name: +++VEEAM-HYPERV+++
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
12. [] Click the **Apply** button on the **Apply** step.
13. [] Click the **Next** button on the **Results** step.
14. [] Click the **Finish** button on the **Summary** step.
15. [] Select **Microsoft Hyper-V** in the **Managed Servers** section of the **Backup Infrastructure** view.
> Note: The VEEAM-HYPERV host is now added to the Veeam Backup & Replication user interface.

===

# Lab 3.2: Configuring a backup proxy

1. [] Select **Backup Proxies** in the **Backup Infrastructure** view.
2. [] Select **VMware Backup Proxy**.
3. [] Click the **Edit Proxy** button on the **Backup Proxy** ribbon.
4. [] Click the **Choose...** button in the **Transport mode** section.
> Note: At this step, you can also specify transport mode and/or connected datastores. In production environments, it is recommended to use as many tasks as the server resources (CPU/RAM) and backup target (repository/disks) can handle. 1 task equals 1 (one) CPU core.

5. [] Review the available transport modes and click the **Cancel** button.
6. [] Click the **Finish** button on the **Server** step.
> Note: If no additional VMware Backup Proxies are added then the Veeam Backup
Server will both coordinate all job activities and handle data processing itself.

===

# Lab 3.3: Configuring a backup repository

## Step 1: Add a remote backup repository

1. [] Select **Backup Repositories** in the **Backup Infrastructure** view.
> Note: During installation, Veeam Backup & Replication checks the volumes of the machine on which you install the product and identifies a volume with the greatest amount of free disk space. On this volume, Veeam Backup & Replication creates the Backup folder that is used as the default backup repository.

2. [] Click the **Add Repository** button.
3. [] Enter name: +++Remote Repository+++.
4. [] Click the **Next** button on the **Name** step.
5. [] Select **Microsoft Windows Server**.
6. [] Click the **Add new** button.
> Note: The Repository servers list contains only those servers that have been added to Veeam Backup & Replication beforehand. As the VEEAM-Remote server has not been added to Veeam Backup & Replication yet, we have to go through the New Windows Server wizard first.

7. [] Enter DNS name: +++VEEAM-Remote+++.
8. [] Click the **Next** button on the **Name** step.
9. [] Click the **Credentials** drop down menu.
10. [] Select **VEEAMINFRA\Administrator**.
> Note: This account should have administrator privileges on the added Microsoft Windows Server.

11. [] Click the **next** button on the **Credentials** step.
12. [] Click the **Apply** button on the **Review** step.
13. [] Click the **Next** button on the **Apply** step.
14. [] Click the **Finish** button on the **Summary** step.
15. [] Click the **Populate** button on the **Server** step.
16. [] Select **X:\\**.
17. [] Click the **Next** button on the **Server** step.
18. [] Verify the **Path to folder** is **X:\Backups** and click the **Next** button on the **Repository** step.
> Note: The Limit read and write data rates setting is used to limit the speed with which Veeam Backup & Replication can read and write
data to/from a backup repository.

19. [] Click the **Next** button on the **Mount Server** step.
20. [] Click the **Apply** button on the **Review** step.
21. [] Click the **Finish** button on the **Apply** step.
22. [] Click the **Yes** button to confirm changing the configuration backup location to the newly created repository.
> Note: The new repository has been added. We have selected the configuration backup to be stored at the remote site to ensure it will remain intact if the VEEAM-VBR VM crashes.

===

## Step 2: Add a local repository

1. [] Click the **Add Repository** button on the **Backup Repository** ribbon.
2. [] Enter name: +++Local Backup Repository+++.
3. [] Click the **Next** button on the **Name** step.
4. [] Select **Microsoft Windows Server**.
5. [] Click the **Next** button on the **Type** step.
6. [] Click the **Populate** button.
7. [] Select **E:\\**.
8. [] Click the **Next** button on the **Server** step.
9. [] Verify the **Path to folder** is **E:\Backups** and click the **Next** button.
10. [] Keep the default settings and click the **Next** button on the **Mount Server** page.
11. [] Click the **Apply** button on the **Review** step.
12. [] Click the **Finish** button on the **Apply** step.

===

## Step 3: Add a Scale-out Backup Repository

1. [] Select **Scale-out Repositories** in the **Backup Infrastructure** view.
2. [] Click the **Add Scale-out Repository** button on the **Scale-Out Repository** ribbon.
> Note: Note: Scale-out Backup Repository embraces several repositories (extents), summarizing their capacity and offering flexible options for keeping massive backups. The Scale-out Backup Repository option is only available in Enterprise and Enterprise Plus editions of Veeam Backup & Replication.

3. [] Enter name: +++Main Backup Repository+++
4. [] Click the **Next** button on the **Name** step.
5. [] Click the **Add...** button.
6. [] Tick the **Default Backup Repository** check box.
7. [] Tick the **Local Backup Repository** check box.
> Note: Note: A repository that you plan to use as an extent of the Scale-out Backup Repository cannot be
used for storing configuration backups or replica metadata

8. [] Click the **OK** button.
9. [] Click the **Next** button on the **Extents** step.
10. [] Click the **Yes** button to accept that agent permissions and backup encryption settings currently present on the added extents will be lost.
11. [] Click the **Apply** button on the **Policy** step.
12. [] Click the **Finish** button on the **Summary** step.

===

# Lab 3.4. Setting up notifications

1. [] Click the **≡** button in the top left corner.
2. [] Select **General Options**.
3. [] Click the **E-mail settings** tab.
4. [] Tick the **Enable e-mail notifications** check box.
5. [] Enter:
 1. SMTP server: +++veeam-ex01.veeamlab.local+++
 2. From: +++VeeamBackup@veeamlab.local+++
 3. To: +++administrator@veeamlab.local+++

6. [] Click the **Apply** button.
7. [] Click the **Test Message** button.
8. [] Click the **OK** button.
> Note: Note: You can find Outlook Web Access (OWA) in the task bar of the VEEAM-VBR server. When you start OWA, you can log in as: administrator@veeamlab.local

9. [] Click the **OK** button.

===

# Lab 3.5: Setup locations

1. [] Select the **Main Repository** Scale-out Repository.
2. [] Click the **Location** button on the **Scale-out Repository** ribbon.
3. [] Select **Manage Locations...**.
4. [] Click the **Add...** button.
5. [] Enter name: +++Remote Site+++.
6. [] Click the **OK** button.
7. [] Click the **Add...** button.
8. [] Enter name: +++Local+++.
9. [] Click the **OK** button.
10. [] Click the **OK** button.
11. [] Click the **Location** button on the **Scale-out Repository** ribbon.
12. [] Select **Local**.
13. [] Select **Backup Repositories** in the **Backup Infrastructure** view.
14. [] Select **Remote Repository**.
15. [] Click the **Location** button on the **Backup Repository** ribbon.
16. [] Select **Remote Site**.
17. [] Navigate to the **Inventory** view.
18. [] Select **VEEAM-ESX**.
19. [] Click the **Location** button on the **Server** ribbon.
20. [] Select **Local**.
21. [] Select **VEEAM-HYPERV**.
22. [] Click the **Location** button on the **Server** ribbon.
23. [] Select **Local**.

---

# Congratulations!

You have completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
