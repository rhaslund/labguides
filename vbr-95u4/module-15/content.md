Module 15: Additional resources
---
**This lab is expected to last a maximum of XX minutes including lab launch.**


# Lab 15.1: Install Veeam Backup & Replication

1. [] Launch the **File Explorer** from the Windows task bar.
2. [] Select the **DVD Drive (D:)** drive.
3. [] Launch the **Setup** file.
4. [] Click the **Install** button on the left hand side.
5. [] Tick the **I accept the terms of the Veeam license agreement** check box.
6. [] Tick the **I accept the terms of the 3rd party components license agreements** check box.
7. [] Click the **Next** button on the **License Agreement** step.
8. [] Click the **Browse...** button.
9. [] Enter: +++C:\Install+++
10. [] Click the **Open** button.
11. [] Select the **veeam_availability_suite_nfr_2_2.lic** file.
12. [] Click the **Open** button.
13. [] Click the **Next** button on the **Provide License** step.
14. [] Keep the default settings and click the **Next** button on the **Program features** step.
15. [] Click the **Install** button to deploy missing features.
16. [] Verify all requirements are now in a **Passed** status then click the **Next** button on the **System Configuration Check** step.
17. [] Keep the default settings and click the **Install** button on the **Default Configuration** step.
18. [] Click the **Finish** button.

===

# Lab 15.2: Install Veeam Backup Enterprise Manager

1. [] Click the **Install** text link in the **Veeam Backup Enterprise Manager** section.
2. [] Tick the **I accept the terms of the Veeam license agreement** check box.
3. [] Tick the **I accept the terms of the 3rd party components license agreements** check box.
4. [] Click the **Next** button on the **License Agreement** step.
5. [] Keep the default settings and click the **Next** button on the **Provide License** step.
> Note: Veeam Backup Enterprise Manager simply uses the same license as was just installed for Veeam Backup & Replication.

6. [] Keep the default settings and click the **Next** button on the **Program features** step.
7. [] Click the **Install** button to deploy missing features.
8. [] Verify all requirements are now in a **Passed** status then click the **Next** button on the **System Configuration Check** step.
9. [] Keep the default settings and click the **Next** button on the **Service Account Credentials** step.
10. [] Keep the default settings and click the **Next** button on the **SQL Server Instance** step.
11. [] Keep the default settings and click the **Next** button on the **Additional Configuration** step.
12. [] Click the **Install** button on the **Ready to Install** step.
13. [] Click the **Finish** button.
14. [] Close the **Veeam Backup & Replication setup** window.

===

# Lab 15.3: Install Veeam ONE

1. [] Click the **Install** button on the left hand side.
2. [] Select the **I accept the terms of the Veeam license agreement** radio button.
3. [] Select the **I accept the terms of the 3rd party components license agreement** radio button.
4. [] Click the **Next** button on the **License Agreement** step.
5. [] Keep the default selection of **Typical** and click the **Next** button on the **Setup Type** step.
6. [] Keep the default path and click the **Next** button on the **Installation Path** step.
7. [] Enter password: +++Pa$$w0rd+++
8. [] Click the **Next** button on the **Service Account Credentials** step.
9. [] Keep the default settings and click the **Next** button on the **SQL Server Instance** step.
10. [] Click the **Browse...** button.
11. [] Select the **Veeam-10instances-entplus-monitoring-nfr.lic** file.
12. [] Click the **Open** button.
13. [] Click the **Next** button on the **Provide License** step.
14. [] Keep the default settings and click the **Next** button on the **Connection Information** step.
15. [] Keep the default path and click the **Next** button on the **Performance Data Caching** step.
16. [] Click the **Skip virtual infrastructure configuration** button on the **Virtual Infrastructure Type** step.
17. [] Keep the default setting and click the **Next** button on the **Data Collection Mode** step.
18. [] Click the **Install** button on the **Ready to Install** step.
19. [] Click the **Finish** button.
20. [] Close the **Veeam ONE setup** window.
21. [] Close the **File Explorer** window.

===

# Lab 15.4: Install the second Veeam Backup Server

1. [] Launch the **Remote Desktop Connection client** from the Windows task bar.
2. [] Enter computer: +++VEEAM-VBR2+++
3. [] Click the **Connect** button.
4. [] Enter password: +++Pa$$w0rd+++
5. [] Click the **OK** button.
6. [] Launch **File Explorer** from the Windows task bar.
7. [] Select the **DVD Drive (D:)** drive.
8. [] Launch the **Setup** file.
9. [] Click the **Install** button on the left hand side.
10. [] Tick the **I accept the terms in the license agreement** check box.
11. [] Tick the **I accept the terms of the 3rd party components license agreements** check box.
12. [] Click the **Next** button on the **License Agreement** step.
13. [] Click the **Browse...** button.
14. [] Enter file name: +++\\\\veeam-vbr\\install+++
15. [] Click the **Open** button.
16. [] Select the **veeam_availability_suite_nfr_2_2.lic** file.
17. [] Click the **Open** button.
18. [] Click the **Next** button on the **Provide License** step.
19. [] Keep the default settings and click the **Next** button on the **Program features** step.
20. [] Click the **Install** button to deploy missing features.
21. [] Click the **Next** button on the **System Configuration Check** step.
22. [] Keep the default settings and click the **Install** button on the **Default Configuration** step.
23. [] Click the **Finish** button.
24. [] Close the **Veeam Backup & Replication setup** window.
25. [] Close the **File Explorer** window.
26. [] Close the **Remote Desktop Connction** window.

---

# Congratulations!

You have completed this Module, to mark the lab as complete click on the menu in the upper right-hand corner and select **End**.
