Module 6: Configuration
---
**This lab is expected to last a maximum of 30 minutes including lab launch.**

# Lab 6.1: Assigning user roles and permissions

1. [] Launch ***Veeam Availability Orchestrator** from the Desktop.
2. [] Enter username: +++siteadmin@vmce.lab+++ and password: +++Pa%%w0rd+++.
3. [] Click the **Login** button.
>Note: Because the server was just started, the spinning icon may display for up to two minutes while services complete their startup.

4. [] Click the **Administation** button in the top right corner.
5. [] Navigate to the **Users and Scopes** view.
6. [] Click the **Add** button in the **Scope** pane.
7. [] Enter:
 1. Name: +++SharePoint Administrators+++
 2. Description: +++Scope for administrators managing Microsoft SharePoint+++
8. [] Click the **Add** button.
9. [] Select the **SharePoint Administrators** scope.
10. [] Click the **Plan Authors** role.
11. [] Click the green **\+ Add button**.
12. [] Enter account: +++planauthor+++.
13. [] Click the ***Find*** button.
14. [] Select the **Plan Author VAO** account.
15. [] Click the **Add** button.

===

# Lab 6.2: Configuring notifications

1. [] Navigate to the **Reporting** view.
2. [] Click the **Edit** text link in the **SMTP Server** section.
3. [] Enter:
 1. SMTP Server: +++exchange.vmce.lab+++
 2. Port: 25
 3. From +++veeam-vao@vmce.lab+++

4. [] Tick the **Use secure connection** check box.
5. [] Click the **Send Test Email** button.
6. [] Enter email address: +++administrator@vmce.lab+++
7. [] Click the **Send** button.
8. [] Click the **OK** button to close the info window.
> Note: If the test fails, it may simply be that the SMTP service on the Exchange server is still in a starting state. Please wait one to two minutes and try again.

9. [] Click the **Close** button.
10. [] Click the **Save** button.
11. [] Verify the state changes to **Connection Successful** and click the **Add** button in the **Recipients** pane.
12. [] Enter address: +++administrator@vmce.lab+++
13. [] Click the **Save** button.
14. [] Notice that all subscriptions are disabled by default. Tick the **Types** check box in the **Reports** pane.
15. [] Click on the **Subscribe** button in the **Reports** pane and verify that all subscriptions are in a subscribed state.
