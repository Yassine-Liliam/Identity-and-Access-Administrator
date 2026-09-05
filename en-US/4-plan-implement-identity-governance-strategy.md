# Plan and implement an identity governance strategy

> SC-300 — learning path 4/4
> https://learn.microsoft.com/en-us/training/paths/plan-implement-identity-governance-strategy/

## Modules

- **Plan and implement entitlement management** (10 units)
- **Plan, implement, and manage access review** (10 units)
- **Plan and implement privileged access** (11 units)
- **Monitor and maintain Entra ID** (9 units)


---

# Plan and implement entitlement management

_https://learn.microsoft.com/en-us/training/modules/plan-implement-entitlement-management/_


## Introduction

New users or external users joining your site need access assignments to Azure solutions. When users wait for resources, you risk losing their engagement and productivity. Explore how to entitle users to access your site and resources. In this module, you learn how to provide the appropriate access to your users, create reviews for that access, and more.

### Learning objectives

By the end of this module, you will be able to:

- Define catalogs.
- Define access packages.
- Plan, implement, and manage entitlements.
- Implement and manage terms of use.
- Manage the lifecycle of external users in Entra Identity Governance settings.
- Configure and manage connected organizations.
- Review per-user entitlements.

### Prerequisites

None.


## Define access packages

### Why use entitlement management?

Enterprise organizations often face challenges when managing employee access to resources such as:

- Users don't know what access they should have, and even if they do, they can have difficulty locating the right individuals to approve their access
- Once users find and receive access to a resource, they hold on to access longer than is required for business purposes

These problems are compounded for users who need access from another organization, such as external users who are from supply chain organizations or other business partners. For example, Entra entitlement management can help organizations ensure that everyone has access to the correct directories and that all user access is managed consistently.

This video provides an overview of entitlement management and its value:

**Watch this video to learn more about Entra entitlement management**

### What can I do with entitlement management?

Capabilities of entitlement management include:

| **Entitlement management capability** | **Description and value** |
|---|---|
| Delegate to non-administrators the ability to create access packages. | These access packages contain resources that users can request, and the delegated access package managers can define policies with rules for which users can request, who must approve their access, and when access expires. |
| Select connected organizations whose users can request access. | When a user who isn't yet in your directory requests access and is approved, they're automatically invited into your directory and assigned access. When their access expires, if they have no other access package assignments, their B2B account in your directory can be automatically removed. |

### Summary of terminology

Before exploring entitlement management and its documentation in depth, you should know the terms below. Feel free to reference back to this list at any time during this course.

| **Term** | **Description** |
|---|---|
| access package | A bundle of resources that a team or project needs and is governed with policies. An access package is always contained in a catalog. You would create a new access package for a scenario in which users need to request access. |
| access request | A request to access the resources in an access package. A request typically goes through an approval workflow. If approved, the requesting user receives an access package assignment. |
| assignment | An assignment of an access package to a user ensures the user has all the resource roles of that access package. Access package assignments typically have a time limit before they expire. |
| catalog | A container of related resources and access packages. Catalogs are used for delegation so non-administrators can create their own access packages. Catalog owners can add resources they own to a catalog. |
| catalog creator | A collection of users who are authorized to create new catalogs. When a non-administrator user who is authorized to be a catalog creator creates a new catalog, they automatically become the owner of that catalog. |
| connected organization | An external Entra directory or domain that you have a relationship with. The users from a connected organization can be specified in a policy as being allowed to request access. |
| policy | A set of rules that defines the access lifecycle, such as how users get access, who can approve, and how long users have access through an assignment. A policy is linked to an access package. For example, an access package could have two policies: one for employees to request access and a second for external users to request access. |
| resource | An asset, such as an Office group, a security group, an application, or a SharePoint Online site, with a role that a user can be granted permissions to. |
| resource directory | A directory that has one or more resources to share. |
| resource role | A collection of permissions associated with and defined by a resource. A group has two roles: member and owner. SharePoint sites typically have three roles but can have additional custom roles. Applications can have custom roles. |

### What are access packages and what resources can I manage with them?

Entitlement management introduces to Entra ID the concept of an *access package*. An access package is a bundle of all the resources with the access a user needs to work on a project or perform their task. Access packages are used to govern access for your internal employees and users outside your organization. You can manage user access to the following resources with entitlement management:

- Membership of Entra security groups.
- Membership of Microsoft 365 Groups and Teams.
- Assignment to Entra enterprise applications, including SaaS applications and custom-integrated applications that support federation/single-sign-on and/or provisioning.
- Membership of SharePoint Online sites.

You can also control access to other resources that rely upon Entra security groups or Microsoft 365 Groups. For example, you can provide:

- Licenses for Microsoft 365 by using a security group in an access package and configuring group-based licensing for that group.
- Access to manage Azure resources by using a security group in an access package and creating an Azure role assignment for that group.
- Access to manage Entra roles by using groups assignable to roles in an access package and assigning a role to that group.

### How do I control who gets access?

With an **access package**, an administrator or delegated access package manager lists the resources (groups, apps, and sites) and the roles the users need for those resources.

Access packages also include one or more *policies*. A policy defines the rules or guardrails for assignment to access package. Each policy ensures that only the appropriate users can request access, that their request has approvers, and that their access to those resources is time-limited and expires if not renewed.

Within each policy, an administrator or access package manager defines three things: which already existing users are eligible to request access, the process to approve or deny access, and the duration of a user's access.

### When should I use access packages?

Access packages don't replace other mechanisms for access assignment. They're most appropriate in situations such as when:

- Employees need time-limited access for a particular task. For example, you might use group-based licensing and a dynamic group to give all employees an Exchange Online mailbox. Access packages then cover the situations where employees need additional access, such as reading departmental resources from another department.
- Access requires the approval of an employee's manager or other designated individuals.
- Departments wish to manage their own access policies for their resources without IT involvement.
- Two or more organizations are collaborating on a project, so multiple users from one organization need to be brought in via Entra B2B to access another organization's resources.

The following diagram shows an example of the elements in entitlement management:

![Diagram of the Entitlement management overview. Process flow and components of entitlement.](https://learn.microsoft.com../../wwl-sci/plan-implement-entitlement-management/media/entitlement-management-overview.png)

In **Access package 1**, there's only one single group as a resource. Access is defined with a policy that enables a set of users in the directory to request access. **Access package 2** includes a group, an application, and a SharePoint Online site as resources. Access is defined with two different policies. The first policy enables a set of users in the directory to request access. The second policy enables users in an external directory to request access.


## Exercise create and manage a resource catalog with Entra entitlement management

### Create an Azure account and add Entra ID Premium P2 trial licenses

The tasks in this exercise require an Azure subscription. You also find the exercises in this learning path need an Azure subscription. If you don't already have one, you can sign up for an Azure trial account. If you already have your own Azure subscription, you can skip this task.

1. In a web browser, go to [Azure portal](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
2. Scroll down through the page to learn more about the benefits and free services available.
3. Select **Start free**.
4. Use the wizard to sign up for your Azure trial subscription.
5. You need an Entra ID P2 license to complete some of the exercises. In the organization you created, search for and then select **Entra ID**.
6. In the left navigation menu, select **Getting started**.
7. Under Getting started with Entra ID, select **Get a free trial for Entra ID Premium**.
8. In the Activate pane, under **Entra ID PREMIUM P2**, select **Free trial** and then select **Activate**.
9. In the navigation menu on the left, select **Overview**.
10. Refresh the browser until you see Entra ID Premium P2 under the organization name. It takes a couple of minutes.
11. The license takes a few minutes to activate. You need to sign out and sign back into Microsoft Azure. Try restarting if you encounter problems with expected features not being available.

### Create a catalog

A catalog is a container of resources and access packages. You create a catalog when you want to group related resources and access packages. Whoever creates the catalog becomes the first catalog owner. A catalog owner can add other catalog owners.

1. Sign in to the [Entra admin center](https://entra.microsoft.com/) as an Administrator.
  - Entra ID Premium P1, P2, EMS E3, or EMS E5 subscription.
  - If you don't have one of these subscriptions, you can get Entra ID Premium or enable Entra ID Premium trial.
  - One of the following administrator accounts for the directory you want to configure:
    - Security Administrator
    - Conditional Access Administrator

2. From **Entra ID** home screen, select **ID Governance**.
3. In the left menu, under **Entitlement management**, select **Catalogs**.
4. On the top menu, select **+New Catalog**.
5. In the New catalog pane, in the **Name** box, enter **Marketing**.
6. In the **Description** box, enter **For marketing department users**. Users will see this information in an access package's details.
7. **Enabled for external users** allows users in selected external directories to be able to request access packages in this catalog. No changes will be made to this setting.
8. Under **Enabled, select No**. You can choose to enable the catalog for immediate use. You can disable if you intend to stage it or keep it unavailable. For this exercise, the catalog doesn't need to be enabled.
9. Select Create.

### Add resources to a catalog

To include resources in an access package, the resources must exist in a catalog. The types of resources you can add are groups, applications, and SharePoint Online sites. The groups can be cloud-created Microsoft 365 Groups or cloud-created Entra security groups. The applications can be Entra enterprise applications, including both SaaS applications and your own applications federated to Entra ID. The sites can be SharePoint Online sites or SharePoint Online site collections.

1. On the Identity Governance screen, if necessary, select **Catalogs**.
2. In the **Catalogs** list, select **Marketing**.
3. In the left navigation, under **Manage**, select **Resources**.
4. On the menu, select + **Add resources**.
5. In the Add resources to catalog screen, review the available options.
6. You might not have selected any resources in Groups and Teams, Applications, or SharePoint sites. To add a resource to the catalog, select a resource category, then select a resource from that category. For this exercise, it's okay to choose any resource you have available.
7. When finished, select **Add**. These resources can now be included in access packages within the catalog.

### Add more catalog owners

The user that created a catalog becomes the first catalog owner. To delegate management of a catalog, you add users to the catalog owner role. This helps share the catalog management responsibilities.

1. In the Marketing catalog, in the left navigation menu, select Roles and administrators. If necessary, in the Azure portal, browse to **Entra ID**, then **ID Governance**, then **Catalogs** and then select **Marketing**.
2. On the top menu, review the available roles and then select **+ Add owner**.
3. In the Select members pane, select your administrator account and then select **Select**.
4. Review the newly added role in the Roles and administrators list.

### Edit a catalog

You can edit the name and description for a catalog. Users see this information in an access package's details.

1. In the Marketing screen, in the left navigation, select **Overview**.
2. On the top menu, select **Edit**.
3. Review the setting and, under **Properties** in the **Enabled** field, select **Yes**.
4. Select **Save**.

### Delete a catalog

You can delete a catalog, but only if it doesn't have any access packages.

1. In the Marketing catalog’s Overview page, on the top menu, select Delete.
2. In the Delete dialog box, review the information and then select **Yes**.


## Configure entitlement management

There are several ways that you can configure entitlement management for your organization. However, if you're just getting started, it's helpful to understand the common scenarios for administrators, catalog owners, access package managers, approvers, and requestors.

- Delegate
  - Administrator: Delegate management of resources.
  - Catalog creator: Delegate management of resources.
  - Catalog owner: Delegate management of resources.
  - Catalog owner: Delegate management of access packages via assigning the access package manager role.

- Govern access for users in your organization
- Access package manager: Allow employees in your organization to request access to resources.
- Requestor: Request access to resources.
- Approver: Approve requests to resources.
- Requestor: View the resources you already have access to.
- Govern access for users outside your organization
  - Administrator: Collaborate with an external partner organization.
  - Access package manager: Collaborate with an external partner organization.
  - Requestor: Request access to resources as an external user.
  - Approver: Approve requests to resources.
  - Requestor: View the resources your already have access to.

- Day-to-day management
  - Access package manager: Update the resources for a project.
  - Access package manager: Update the duration for a project.
  - Access package manager: Update how access is approved for a project.
  - Access package manager: Update the people for a project.
  - Access package manager: Directly assign specific users to an access package.

- Assignments and reports
  - Administrator: View who has assignments to an access package.
  - Administrator: View resources assigned to users.

### Programmatic administration

You can also manage access packages, catalogs, policies, requests, and assignments using Microsoft Graph. A user in an appropriate role with an application that has the delegated `EntitlementManagement.ReadWrite.All` permission can call the [entitlement management API](https://learn.microsoft.com/en-us/graph/tutorial-access-package-api).


## Exercise add terms of use acceptance report

### What are terms of use for Entitlement Management

Entra terms of use policies use the PDF format to present content. The PDF file can be any content, such as existing contract documents, allowing you to collect end-user agreements during user sign-in. To support users on mobile devices, the recommended font size in the PDF is 24 point. Remember that terms of use PDF documents can contain an End User License Agreement (EULA). The user has to commit to before access resources based on their entitlement settings.

### Add terms of use

Once you finalize your terms of use document, use the following procedure to add it.

1. Sign in to the [Entra admin center](https://entra.microsoft.com/) as a Global administrator.
2. Open **ID Governance**.
3. In the left navigation menu open Entitlement Management, then under **Terms of use**, select **Terms of use**.
4. On the Terms of use page, on the top menu, select **+ New terms**.
5. In the **Name** box, enter **Testing terms of use**. Set the name the terms-of-use in the admin center.
6. In the **Display name** box, enter **Contoso Terms of Use**. The title that users see when they sign-in.
7. Select the **Terms of use document box**, browse to your finalized terms of use PDF, and select it. For this exercise, you can choose any PDF you have. Another option is use Microsoft Word to create the terms of use doc and then save as PDF.
8. Select the language for your terms of use document. The language option allows you to upload multiple terms of use, each with a different language. The version of the terms of use that an end user sees, is based on their browser preferences.
9. To require end users to view the terms of use before accepting them, set **Require users to expand the terms of use** to **On**.
10. To require end users to accept your terms of use on every device they're accessing from, set **Require users to consent on every device** to **On**. Users are required to install other applications if this option is enabled.  Warning Consent on every device requires users to register each device with Entra ID before getting access.
11. If you want to expire terms of use consents on a schedule, set **Expire consents** to **On**. When set to On, two extra schedule settings are displayed.    ​
12. Use the **Expire starting on** and **Frequency** settings to specify the schedule for terms of use expirations. The following table shows the result for a couple of example settings:    **Expire starting on** **Frequency** **Result**     Today's date Monthly The users must accept the terms of use and then reaccept every month, starting today.   Date in the future Monthly The users must accept the terms of use, starting today. When the future date occurs, consents expire and then users must reaccept every month.    For example, if you set the expire starting on date to **Jan 1** and frequency to **Monthly**, here's how expirations might occur for two users:    **User** **First accept date** **First expire date** **Second expire date** **Third expire date**     Alice January 1 February 1 March 1 April 1   Bob January 15 February 1 March 1 April 1
13. Use the **Duration before reacceptance requires (days)** setting to specify the number of days before the user must reaccept the terms of use. This setting allows users to follow their own schedule. For example, if you set the duration to **30** days, here's how expirations might occur for two users:    **User** **First accept date** **First expire date** **Second expire date** **Third expire date**     Alice January 1 January 31 March 2 April 1   Bob January 15 February 14 March 16 April 15
14. Under **Conditional Access**, select **Custom policy**.    **Template** **Description**     Custom policy Select the users, groups, and apps that the terms of use apply to.   Create Conditional Access policy later Terms of use appear in the grant control list when creating a Conditional Access policy.
15. When complete, select **Create**.    ​
16. When the terms of use are created, you're redirected to the Conditional Access policy page. On the page, in the **Name** box, enter **Enforce ToU**.
17. Under **Assignments**, select **Users and groups**.
18. On the include tab, select **Users and groups** check box.
19. In the Select pane, select an account you would like to use to test the terms of use policy. If you choose your administrator account, like all Conditional Access policies, be sure you have another account with enough permissions to change the Conditional Access policy. You need to ensure your administrator account isn't locked out should the Conditional Access policy result in an undesirable outcome.
20. Select **Cloud apps or actions**.
21. Select **All cloud apps**.
22. Under **Access controls**, select **Grant**.
23. In the Grant pane, select **Testing terms of use** and then select **Select**.
24. Under **Enable policy**, select **On**.
25. When complete, select **Create**.    ​
26. If you chose to use your own account, you can refresh your browser. You're prompted to sign in again. When you sign in, you again must accept the terms of use.

### View report of who accepted and declined

The terms-of-use-screen shows a count of the users who accepted and declined. These counts and who accepted/declined are stored for the life of the terms of use.

1. In Microsoft Azure, in **Identity Governance**, then **Terms of use**, locate your terms of use.
2. For the terms of use, select the numbers under **Accepted** or **Declined** to view the current state for users.
3. In this exercise, you might not have any accepted or declined terms of use. In the following example, the **Accepted** value was selected. You can see the reported user information for those that accepted the terms of use.
4. To view the history for an individual user, select the ellipsis to the right of the user name and then **View History**.
5. In the view history pane, you see a history of all the accepts, declines, and expirations.

### What terms of use look like for users

1. Once the terms of use are created and enforced, users who are in scope see the terms of use page.
2. Users can view the terms of use and, if necessary, use buttons to zoom in and out.
3. On mobile devices, the terms of use display similar to the following example.

#### How users can review their terms of use

Users can review and see the terms of use that they accepted by using the following procedure.

1. Browse to [https://myaccount.microsoft.com](https://myapps.microsoft.com/) and then sign in using your user account.
2. On the Overview page, select VIEW SETTINGS AND PRIVACY.
3. On the Settings and Privacy page, select the **Privacy** tab.
4. Under **Organization’s notice**, you can review the terms of use you accepted.

### Edit terms of use details

You can edit some details of terms of use, but you can't modify an existing document. The following procedure describes how to edit the details.

1. Sign in to the [Entra admin center](https://entra.microsoft.com/) as a Global administrator.
2. Open ID Governance and the select **Entitlement management**.
3. In the left navigation menu, under **Terms of use**, select **Terms of use**.
4. Select the terms of use you want to edit.
5. On the top menu, select **Edit terms**.
6. In the Edit terms of use pane, you can change the following settings:
  - **Name** – The internal name of the ToU that isn't shared with end users.
  - **Display name** – The name that end users can see when viewing the ToU.
  - **Require users to expand the terms of use** – Set to **On** forces the end use to expand the terms of use document before accepting it.
  - **Update an existing terms-of-use** document.
  - You can add a language to an existing ToU. There are other settings you can change, such as require users to consent on every device, and expire consents. You can also set duration before reacceptance, or Conditional Access policy. You must create a new terms-of-use.

7. Once you're done, select **Save** to save your changes.

### Update an existing terms-of-use document

You can be required to update the terms of use document.

1. Select the terms of use you want to edit.
2. Select **Edit terms**.
3. In the **Language Options** table, identify the terms of use language you want to update and then, in the **Action** column, select **Update**.
4. In the Update terms of use version pane, you can upload a new version of your terms of use document.
5. Additionally, you can use the **Require reaccept** toggle button if you want to require your users to accept this new version the next time they sign in. If you don't require your users to reaccept, their previous consent stays current. Only new users who haven't consented before or whose consent expires see the new version.
6. Once you upload your new pdf and decided on reaccept, select **Add**.
7. You now see the most recent version under the Document column.


## Exercise manage the lifecycle of external users with Entra identity governance

### Manage the lifecycle of external users in Entra ID Governance settings

You can select what happens when an external user, who was invited to your directory through an access package request being approved, no longer has any access package assignments. This situation can happen if the user relinquishes all their access package assignments, or their last access package assignment expires. By default, when an external user no longer has any access package assignments, they're blocked from signing in to your directory. After 30 days, their guest user account is removed from your directory.

1. Sign in to the Entra admin center as an Administrator. An account with User administrator is required to complete these tasks.
2. Open **ID Governance**.
3. In the left navigation menu, under **Entitlement management**, select **Settings**.
4. On the top menu, select **Edit**.
5. In the **Manage the lifecycle of external users** section, review the different settings for external users. To block an external user from signing in to this directory once they lose their last assignment to any access packages, set the **Block external user from signing in to this directory** to **Yes**. If a user is blocked from signing in to the directory, the user is unable to re-request the access package or request another access in this directory. Don't configure blocking them from signing in if they'll later need to request access to other access packages.
6. To remove an external user's guest account in this directory once they lose their last assignment to any access packages, set **Remove external** user to **Yes**.  Note Entitlement management only removes accounts that were invited through entitlement management. Also a user is blocked from signing in. The user is removed from this directory even if that user was added to resources in this directory that weren't access package assignments. If the guest was present in this directory before receiving access package assignments, they'll remain. However, if the guest was invited through an access package assignment, they'll still be removed.
7. If you want to remove the guest user account in this directory, you can set the number of days before it's removed. To remove the guest user account as soon as they lose their last assignment to any access packages, set **Number of days before removing external user from this directory** to **0**.
8. If you made any changes, select **Save**.


## Configure and manage connected organizations

With Entra entitlement management, you can collaborate with people outside your organization. If you frequently collaborate with users in an external directory or domain, you can add them as a connected organization. This article describes how to add a connected organization so that you can allow users outside your organization to request resources in your directory.

### What is a connected organization?

A connected organization is another organization that you have a relationship with. For the users in that organization to access your resources, such as your SharePoint Online sites or apps, you need a representation of that organization's users in that directory. Because in most cases the users in that organization aren't already in your Entra directory, you can use entitlement management to bring them into your Entra directory as needed.

There are three ways that entitlement management lets you specify the users that form a connected organization. It could be

- users in another Entra directory (from any Microsoft cloud),
- users in another non-Entra directory that has been configured for direct federation, or
- users in another non-Entra directory, whose email addresses all have the same domain name in common.

### Add a connected organization

To add an external directory or domain as a connected organization, follow the instructions in this section. **Prerequisite role:** Identity Governance administrator, or User administrator

1. In the **Entra admin center**, select **ID Governance**, and then select **Entitlement management**.
2. In the left pane, select **Connected organizations**, and then select **+ Add connected organization**.
3. Select the **Basics** tab, and then enter a display name and description for the organization.
  - The state will automatically be set to Configured when you create a new connected organization. For more information about state properties, see State properties of connected organizations

4. Select the **Directory + domain** tab, and then select **Add directory + domain**.
  - The Select directories + domains pane opens.

5. In the search box, enter a domain name to search for the Entra directory or domain. Be sure to enter the entire domain name.
  - Confirm that the organization name and authentication type are correct.

6. Select **Add** to add the Entra directory or domain. Currently, you can add only one directory or domain per connected organization.
7. After you've added the directory or domain, select Select.
  - The organization appears in the list.

8. Select the **Sponsors** tab, and then add optional sponsors for this connected organization.
  - Sponsors are internal or external users already in your directory. Sponsors are the point of contact for the relationship with this connected organization.
  - When you select Add/Remove, a pane opens in which you can choose internal or external sponsors. The pane displays an unfiltered list of users and groups in your directory.

9. Select the **Review + create** tab, review your organization settings, and then select **Create**.


## Review per-user entitlements

In Entra entitlement management, you can see who has been assigned to access packages, their policy, and status. If an access package has an appropriate policy, you can also directly assign user to an access package. This article describes how to view, add, and remove assignments for access packages.

### Governance

Following the rules of **zero trust** you review your entitlement packages regularly. There are tools built into the system to support this review.

### View who has an assignment

**Required role**

- Identity Governance administrator
- User administrator
- Catalog owner
- Access package manager
- Access package assignment manager

Follow these steps to review assignments:

1. In the Entra admin center, select **ID Governance** and then select **Entitlement management**.
2. In the left menu, select **Access packages** and then open the access package.
3. select Assignments to see a list of active assignments.
4. select a specific assignment to see additional details.
5. To see a list of assignments that did not have all resource roles properly provisioned, select the filter status and select **Delivering**.
  - You can see additional details on delivery errors by locating the user's corresponding request on the Requests page.

6. To see expired assignments, select the filter status and select **Expired**.
7. To download a **CSV file** of the filtered list, select **Download**.

### Review the assignments with PowerShell

You can perform a query in PowerShell to get the per-user list of assignments. This can help with scripting and automation of the management tasks.

PowerShell

```
Connect-MgGraph -Scopes "EntitlementManagement.Read.All"
Select-MgProfile -Name "beta"
$accesspackage = Get-MgEntitlementManagementAccessPackage -DisplayNameEq "Marketing Campaign"
$assignments = Get-MgEntitlementManagementAccessPackageAssignment -AccessPackageId $accesspackage.Id -ExpandProperty target -All -ErrorAction Stop
$assignments | ft Id,AssignmentState,TargetId,{$_.Target.DisplayName}
```

### Remove an assignment

If you find an assignment that is out of date, take action. You can remove an assignment that a user or an administrator had previously requested.

1. In the Entra admin center, select **ID Governance** and then select **Entitlement management**.
2. In the left menu, select **Access packages** and then open the access package.
3. In the left menu, select **Assignments**.
4. select the check box next to the user whose assignment you want to remove from the access package.
5. select the **Remove** button near the top of the left pane.


## Module assessment

Choose the best response for each of the questions below.

### Check your knowledge


## Summary and resources

Now that you reviewed this module, you're able to:

- Define catalogs.
- Define access packages.
- Plan, implement, and manage entitlements.
- Implement and manage terms of use.
- Manage the lifecycle of external users in Entra ID Governance settings.
- Configure and manage connected organization.
- Review per user entitlements.

In this module, you learned how to manage permissions and access for your internal and external users in order to protect the security of your company information. Through hands on exercises, you created an Azure account, created and managed a catalog of resources, added terms of use and acceptance reporting, and managed the lifecycle of external users. Armed with this new knowledge, you can now implement access reviews in your own organization.

### Resources

Use these resources to discover more.

- FAQs [https://learn.microsoft.com/azure/active-directory/conditional-access/terms-of-use](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/terms-of-use)
- [What is Entra entitlement management](https://learn.microsoft.com/en-us/azure/active-directory/governance/entitlement-management-overview)
- [Common scenarios in Entra entitlement management](https://learn.microsoft.com/en-us/azure/active-directory/governance/entitlement-management-scenarios)
- [Review assignments in Entra entitlement management](https://learn.microsoft.com/en-us/azure/active-directory/governance/entitlement-management-access-package-assignments)
- [Add a connected organization in Entra entitlement management](https://learn.microsoft.com/en-us/azure/active-directory/governance/entitlement-management-organization)


---

# Plan, implement, and manage access review

_https://learn.microsoft.com/en-us/training/modules/plan-implement-manage-access-review/_


## Introduction

As your organization grows, managing who has access to what becomes increasingly difficult. Employees change roles, guests accumulate permissions they no longer need, and privileged assignments persist long after a project ends. Without a systematic process for reviewing and recertifying access, your environment accumulates risk—and audit findings quickly follow.

Entra access reviews give you a structured way to manage user access drift. They let you schedule periodic reviews of group memberships, application assignments, and privileged role assignments, then automate the outcome—removing access that reviewers deny—without manual follow-up.

In this module, you plan for and implement access reviews in Entra ID Governance. You learn why access reviews matter to your organization's security posture. You learn to create and configure them for different resource types, and how to monitor and automate their outcomes. You also explore the Access Review Agent, which uses AI to guide reviewers through the process directly in Microsoft Teams.

### Learning objectives

By the end of this module, you are able to:

- Plan for access reviews.
- Create access reviews for groups and apps.
- Monitor access review findings.
- Create and manage access review programs.
- Automate access review management tasks.
- Configure recurring access reviews.
- Describe the Access Review Agent and how it helps reviewers complete access reviews.

### Prerequisites

- Knowledge of Entra user creation and access management

Note

Some features of access reviews require a **Entra ID Governance** or **Entra Suite** subscription. Some capabilities work with an Entra ID P2 subscription. Confirm your licensing before deployment.


## Plan for access reviews

### What is an access review?

An **Access Review** as the name implies, is a planned review of the access needs, rights, and history of user access. Access reviews help ensure that the right people have the right access to the right resources. They mitigate access risk by protecting, monitoring, and auditing access to critical assets—while ensuring employee and business partner productivity. Access reviews are a feature of Entra ID Governance and require a **Entra ID Governance** or **Entra Suite** subscription. Some capabilities work with an Entra ID P2 subscription.

Consider your organizational needs to determine the strategy for deploying access reviews in your environment.

### Engage the right stakeholders

When technology projects fail, they typically do so due to mismatched expectations, outcomes, and responsibilities. To avoid these pitfalls, ensure that you're engaging the right stakeholders and that project roles are clear. For access reviews, include representatives from the following teams within your organization:

- **IT administration** manages your IT infrastructure and administers your cloud investments and software as a service (SaaS) apps. This team reviews privileged access to infrastructure and apps, schedules access reviews on exception-list groups, and ensures that programmatic access through service principals is governed.
- **Security teams** ensure the plan meets the organization's security requirements and enforce Zero Trust. This team reduces risk, enforces least-privilege access, and uses tools to maintain a centralized view of who has access to what.
- **Development teams** build and maintain applications for your organization. This team controls who can access components in SaaS, PaaS, and IaaS resources and manages groups used for internal application development.
- **Business units** manage projects and own applications. This team reviews and approves or denies access to groups and applications for internal and external users.
- **Corporate governance** ensures that the organization follows internal policy and complies with regulations.  Note For reviews requiring manual evaluations, be sure to plan for adequate reviewers and review cycles that meet your policy and compliance needs. If review cycles are too frequent, or there are too few reviewers, quality is lost and too many or too few people have access.

### What is Entra ID Governance?

Entra ID Governance enables you to balance your organization's need for security and employee productivity with the right processes and visibility. It provides capabilities that give the right people the right access to the right resources. It also helps you mitigate access risk by protecting, monitoring, and auditing access to critical assets—while keeping employees and business partners productive.

Identity Governance gives organizations the ability to complete tasks across employees, business partners and vendors, and across services and applications both on-premises and in clouds. Specifically, it's intended to help organizations address these four key questions:

- Which users should have access to which resources?
- What are those users doing with that access?
- Are there effective organizational controls for managing access?
- Can auditors verify that the controls are working?

### Plan a pilot

We encourage customers to initially pilot access reviews with a small group and target noncritical resources. Piloting can help you adjust processes and communications as needed and increase users’ and reviewers’ ability to meet security and compliance requirements.

In your pilot, we recommend that you:

- Start with reviews where the results aren't automatically applied, and you can control the implications.
- Ensure that all users have valid email addresses listed in Entra ID and that they receive email communication to take the appropriate action.
- Document any access removed as a part of the pilot in case you need to quickly restore it.
- Monitor audit logs to ensure all events are properly audited.

#### What resource types can be reviewed?

Once you integrate your organization’s resources with Entra ID (such as users, applications, and groups), they can be managed and reviewed.

Typical targets for review include:

- User access to applications integrated with Entra ID for single sign-on (such as SaaS, line-of-business).
- Group membership (synchronized to Entra ID, or created in Entra ID or Microsoft 365, including Microsoft Teams).
- Access Package that groups resources (groups, apps, and sites) into a single package to manage access.
- Entra roles and Azure Resource roles as defined in Privileged Identity Management (PIM).
- Custom data resources (preview)—access rights managed through external resource types connected to Entra ID Governance.

#### Who creates and manages access reviews?

The administrative role required to create, manage, or read an Access Review depends on the type of resource being reviewed.

| **Resource type** | **Create and manage access reviews (Creators)** | **Read Access Review results** |
|---|---|---|
| Group or application | Global Administrator | Global administrator |
|   | User Administrator | Global reader |
|   | Identity Governance administrator | User administrator |
|   | Privileged Role administrator (only does review for Entra assignable groups) | Identity Governance Administrator |
|   | Group owner | Privileged Role Administrator |
|   |   | Security reader |
|   |   | Group owner |
| Entra role | Global Administrator |   |
|   | Privileged Role Administrator | Global administrator |
|   |   | Global reader |
|   |   | User administrator |
|   |   | Privileged Role Administrator |
|   |   | Security reader |
| Azure resource roles | Global Administrator | Global Administrator |
|   | User Access Administrator | User Access Administrator |
|   | Resource Owner | Resource owner |
|   |   | Reader (for the resource) |
| Access package | Global Administrator | Global Administrator |
|   | User Administrator |   |
|   | Identity Governance Administrator | Global reader |
|   |   | User administrator |
|   |   | Identity Governance administrator |
|   |   | Security reader |

#### Who reviews the access to the resource?

The creator of the access review decides at the time of creation who performs the review. This setting can't be changed once the review is started. Reviewers are represented by three personas:

- Resource Owners, who are the business owners of the resource.
- A set of individually selected delegates, as selected by the access reviews administrator.
- End users who will each self-attest to their need for continued access.

When the administrator creates an Access Review, administrators can choose one or more reviewers. All reviewers can start and carry out a review, choosing to grant users continued access to a resource or removing them.

#### Components of an access review

Before implementing your access reviews, you should plan the types of reviews relevant to your organization. To do so, you need to make business decisions about what you want to review and the actions to take based on those reviews.

To create an access review policy, you must have the following information.

- What resource(s) must be reviewed?
- Whose access is being reviewed?
- How often should the review occur?
- Who performs the review?
- How will they be notified to review?
- What are the timelines to be enforced for review?
- What automatic actions should be enforced based on the review?
- What happens if the reviewer doesn't respond in time?
- What manual actions are taken as a result based on the review?
- What communications should be sent based on actions taken?

**Example Access Review plan**

| **Component** | **Value** |
|---|---|
| Resources to review | Access to Microsoft Dynamics |
| Review frequency | Monthly |
| Who performs review | Dynamics business group program managers |
| Notification | Email 24 hours prior to review to alias Dynamics-Pms |
|   | Ensure reviewer buy-in and completion by including custom message to reviewers |
| Timeline | 48 hours from notification |
| Automatic actions | Remove access from any account that has no interactive sign-in within 90 days by removing the user from the security group dynamics-access |
|   | *Perform actions if not reviewed within timeline* |
| Manual actions | Reviewers perform removals approval prior to automated action if desired |
| Communications | Send internal (member) users who are removed an email explaining they're removed and how to regain access |

### Plan access reviews for access packages

Access packages can vastly simplify your governance and Access Review strategy. An Access Package is a bundle of all the resources with the access a user needs to work on a project or perform their task. For example, you might create an Access Package that includes all the applications developers in your organization need, or all applications external users should have access to. An administrator or delegated Access Package manager then groups the resources (groups or apps) and the roles the users need for those resources.

When creating an Access Package, you can create one or more access policies. They set the conditions for which users can request an Access Package, what the approval process looks like, and how often a person has to re-request access. Access reviews are configured while creating or editing an Access Package policy.

### Plan access reviews for groups

Besides Access Packages, reviewing group membership is the most effective way of governing access. We recommend that access to resources is assigned via security groups or Microsoft 365 groups, and that users are added to those groups to gain access.

A single group can be granted access to all appropriate resources. You can assign the group access to individual resources, or to an Access Package that groups applications and other resources. With this method, you can review access to the group rather than an individual’s access to each application.

Group membership reviewed by:

- Administrators
- Group owners
- Selected users, delegated review capability when the review is created
- Members of the group, attesting for themselves

#### Group ownership

We recommend that group owners review membership, as they're best situated to know who needs access. Ownership of groups differs with the type of group.

- Groups that are created in Microsoft 365 and Entra ID have one or more well-defined owners. In most cases, these owners make perfect reviewers for their own groups as they know who should have access. For example, Microsoft Teams uses Microsoft 365 Groups as the underlying authorization model to grant users access to resources in SharePoint, Exchange, OneNote, or other Microsoft 365 services. The creator of the team automatically becomes an owner and should be responsible for attesting to the membership of that group.
- Groups created manually in the Entra admin center portal or via scripting through Microsoft Graph might not necessarily have owners defined. We recommend that you define them either through the admin portal in the group’s "Owners" section or via Graph.
- Groups that are synchronized from on-premises Active Directory can't have an owner in Entra ID. When creating an Access Review for them, you should select individuals who are best suited to decide on membership in them.  Note We recommend defining business policies that define how groups are created to ensure clear group ownership and accountability for regular review of membership.

#### Review membership of exclusion groups in CA policies

There are times when Conditional Access policies designed to keep your network secure shouldn't apply to all users. For example, a CA policy that only allows users to sign in while on the corporate network might not apply to the sales team, which travels extensively. In that case, the sales team members would be put into a group and that group would be excluded from the CA policy.

#### Review external users' group memberships

To minimize manual work and associated potential errors, consider using Dynamic Groups to assign group membership based on a user’s attributes. You want to create one or more Dynamic Groups for external users. The internal sponsor can act as a reviewer for membership in the group.

#### Review access to on-premises groups

Access reviews can't change the group membership of groups that you synchronize from on-premises with Entra Connect. With synced groups, the source of authority is on-premises. You can still use access reviews to schedule and maintain regular reviews of on-premises groups. Reviewers take action in the on-premises group. This strategy keeps access reviews as the tool for all reviews. You can use the results from an Access Review on on-premises groups and process them further. The data is available in a CSV file or from Microsoft Graph.

### Plan access reviews for applications

When you review access to an application, you're reviewing the access for employees and external identities to the information and data within the application. Choose to review an application when you need to know who has access to a specific application, instead of an Access Package or a group.

We recommend you plan reviews for applications in the following scenarios:

- Users are granted direct access to the application (outside of a group or Access Package).
- The application exposes critical or sensitive information.
- The application has specific compliance requirements to which you must attest.
- You suspect inappropriate access.

#### Reviewers for an application

Access reviews can be for the members of a group or for users who were assigned to an application. Applications in Entra ID don't necessarily have an owner, which is why the option for selecting the application owner as a reviewer isn't possible. You can further scope a review to review only guest users assigned to the application, rather than reviewing all access.

### Plan review of Entra ID and Azure resource roles

Privileged Identity Management (PIM) simplifies how enterprises manage privileged access to resources in Entra ID. This keeps the list of privileged roles, both in Entra ID and Azure resources, smaller and increases the overall security of the directory.

Access reviews allow reviewers to attest whether users still need to be in a role. Just like access reviews for Access Packages, reviews for Entra roles and Azure resource are integrated into the PIM admin user experience. We recommend you review the following role assignments regularly:

- Global Administrator
- User Administrator
- Privileged Authentication Administrator
- Conditional Access Administrator
- Security Administrator
- All Microsoft 365 and Dynamics Service Administration roles

### Deploy access reviews

After you prepare a strategy and a plan to review access for resources integrated with Entra ID, deploy and manage reviews by using the resources listed.

#### Review access packages

To reduce the risk of stale access, administrators can enable periodic reviews of users who have active assignments to an access package. You can create access reviews, perform access reviews for others that are assigned to an Access Package, or perform a self-review of assigned Access Package.

#### Review groups and apps

Employees' and guests' access needs to groups and applications likely change over time. To reduce the risk associated with stale access assignments, administrators can create access reviews for group members or application access.

You can create access reviews for group members or application access, and perform those reviews for members of a group or users with access to an application. You can also let members review their own access to a group or an application, view access reviews, and take action for on-premises groups with PowerShell.

#### Review Entra roles

To reduce the risk associated with stale role assignments, you should regularly review access of privileged Entra roles.

#### Review Azure resource roles

To reduce the risk associated with stale role assignments, you should regularly review access of privileged Azure resource roles.

### Use the access reviews API

The access reviews methods in the Microsoft Graph API are available for both application and user contexts. The scripts running in the application context, the account used to run the API (the service principle) must be granted the “AccessReview.Read.All” permission to query access reviews information.

Popular access reviews tasks to automate using the Graph API for access reviews are:

- Create and start an Access Review.
- Manually end an Access Review before its scheduled end.
- List all running Access Reviews and their status.
- See the history of a review series and the decisions and actions taken in each review.
- Collect decisions from an Access Review.
- Collect decisions from completed reviews where the reviewer took a different decision than what the system recommended.  Note When creating new Graph API queries for automation, we recommend using the Graph Explorer. You can build and explore your Graph queries before putting them into scripts and code. This can help you quickly iterate your query so that you get exactly the results you're looking for, without changing the code of your script.

### Monitor access reviews

Access reviews activities are recorded and available from the Entra audit logs. You can filter the audit data on the category, activity type, and date range. Here's a sample query:

| **Category** | **Policy** |
|---|---|
| Activity type | Create access review |
|   | Update access review |
|   | Access Review ended |
|   | Delete access review |
|   | Approve decision |
|   | Deny decision |
|   | Reset decision |
|   | Apply decision |
| Date range | Seven days |

For more advanced queries and analysis of access reviews, and to track changes and completion of reviews, we recommend exporting your Entra Audit Logs to Azure Log Analytics or Azure Event Hubs. When logs are stored in Azure Log Analytics, you can use the powerful analytics language and build your own dashboards.

### Plan communications

Communication is critical to the success of any new business process. Proactively communicate to users how and when their experience changes and how to gain support if they experience issues.

**Communicate changes in accountability**: Access Reviews support shifting responsibility of reviewing and acting on continued access to business owners. Decoupling access decisions from IT drives more accurate access decisions. This is a cultural change in resource owners' accountability and responsibility. Proactively communicate this change and ensure resource owners are trained and able to use the insights to make good decisions.

Clearly, IT wants to stay in control for all infrastructure-related access decisions and privileged role assignments.

**Customize email communication**: When you schedule a review, you nominate users who perform this review. These reviewers then receive an email notification of new reviews assigned to them, and reminders before a review assigned to them expires.

Administrators can choose to send this notification either halfway before the review expires or a day before it expires.

The email sent to reviewers can be customized to include a custom short message that encourages them to act on the review. We recommend you use the other text to:

- Include a personal message to reviewers, so they understand it's sent by your Compliance or IT department.
- Include a hyperlink or reference to internal information on what the expectations of the review are and other reference or training material.
- Include a link to instructions on how to perform a self-review of access.

Upon selecting Start review, reviewers are directed to the MyAccess portal for group and application Access Reviews. The portal gives them an overview of all users who have access to the resource they're reviewing and system recommendations based on last sign-in and access information.

### How many licenses must you have?

An Entra ID Premium P2 license is required for each member or guest user who:

- Is assigned as a reviewer
- Performs a self-review
- Is a group owner performing an access review
- Is an application owner performing an access review

Licenses aren't required for users with the Global Administrator or User Administrator roles who set up access reviews, configure settings, or apply review decisions.

Entra ID Premium P2 licenses aren't required for Global Administrators or User Administrators who set up access reviews, configure settings, or apply the decisions from the reviews.


## Create access reviews for groups and apps

Access to groups and applications for employees and guests changes over time. To reduce the risk associated with stale access assignments, administrators can use Entra ID to create access reviews for group members or application access. If you need to routinely review access, you can also create recurring access reviews.

### Prerequisites

- Entra ID Governance or Entra Suite (Entra ID Premium P2 provides limited capabilities)
- Identity Governance Administrator or Global Administrator

### Create one or more access reviews

1. Sign in to the [Entra admin center](https://entra.microsoft.com) as at least an **Identity Governance Administrator**.
2. Browse to **ID Governance** > **Access reviews**.
3. Select **New access review** to create a new access review.
4. On the Access reviews template screen, select **Review access to a resource type**.
5. In the **Select what to review** box, select the resource you want to review.
6. If you selected **Teams + Groups**, you have two options:
  - **All Microsoft 365 groups with guest users**. Select this option if you want to create recurring reviews on all your guest users across all your Microsoft Teams and Microsoft 365 groups in your organization. You can choose to exclude certain groups by selecting **Select group(s) to exclude**.
  - **Select teams + groups**. Select this option if you want to specify a finite set of teams or groups to review. A list of groups to choose from appears on the side of the screen.

7. If you selected **Applications**, select one or more applications.
8. Select a scope for the review. Your options are:  If you're reviewing group membership, you can also target only inactive users. In the **Users scope** section, select **Inactive users (on tenant level)** and specify the number of days inactive (up to 730 days).
  - **Guest users only**. Limits the review to Entra B2B guest users in your directory.
  - **Everyone**. Scopes the review to all user objects associated with the resource.  Note If you selected **All Microsoft 365 groups with guest users**, your only option is to review **Guest users only**.

9. Select **Next: Reviews**.
10. In the **Select reviewers** section, select one or more people to perform the access reviews. You can choose from:
  - **Group owner(s)** (only available when performing a review on a team or group)
  - **Selected user(s) or groups(s)**
  - **Users review their own access**
  - **Managers of users**. If you choose **Managers of users** or **Group owner(s)**, you can also specify a fallback reviewer. Fallback reviewers are asked to complete a review when the user has no manager in the directory or the group has no owner.

11. In the **Specify recurrence of review** section, you can specify a frequency such as **Weekly, Monthly, Quarterly, Semi-annually, Annually**. You then specify a **Duration**, which defines how long a review is open for input from reviewers. For example, the maximum duration that you can set for a monthly review is 27 days to avoid overlapping reviews. You might want to shorten the duration to ensure that your reviewers input is applied earlier. Next, you can select a **Start date** and **End date**.
12. Select **Next: Settings**.
13. In the **Upon completion settings**, you can specify what happens after the review completes.     If you want to automatically remove access for denied users, set **Auto apply results to resource** to **Enable**. If you want to manually apply the results when the review completes, set the switch to **Disable**. Use the **If reviewers don't respond** list to specify what happens for users that aren't reviewed by the reviewer within the review period. This setting doesn't change users who were reviewed manually. If the final reviewers' decision is Deny, then the user's access is removed.  Use the Action to apply on denied **guest** users to specify what happens to guest users if they're denied.
  - No change - Leave user's access unchanged
  - Remove access - Remove user's access
  - Approve access - Approve user's access
  - Take recommendations - Take the system's recommendation on denying or approving the user's continued access

  - **Remove user’s membership from the resource** removes denied user’s access to the group or application being reviewed. Tenant sign-in continues to work.
  - **Block user from signing in for 30 days, then remove user from the tenant** blocks the denied users from signing in to the tenant, even if they have access to other resources. If there was a mistake or if an admin decides to re-enable one’s access, they can do so within 30 days after the user is disabled. If there's no action taken on the disabled user accounts, they're deleted from the tenant.
  - Action to apply on denied guest users isn't configurable on reviews scoped to more than guest users. It's also not configurable for reviews of all Microsoft 365 groups with guest users. When not configurable, the default option of removing user's membership from the resource is used on denied users.

14. In the **Enable review decision helpers** section, choose whether your reviewer receives recommendations during the review process.
15. In the **Advanced settings** section, you can choose the following
  - Set **Justification required** to **Enable** to require the reviewer to supply a reason for approval.
  - Set **email notifications** to **Enable** to have Entra ID send email notifications to reviewers when an access review starts, and to administrators when a review completes.
  - Set **Reminders** to **Enable** to have Entra ID send reminders of access reviews in progress to reviewers who haven't completed their review. These reminders are half-way through the duration of the review.
  - The content of the email sent to reviewers is autogenerated based on the review details, such as review name, resource name, and due date. If you need to communicate additional information, such as extra instructions or contact information, specify these details in the **Additional content for reviewer email** section. The information you enter is included in the invitation and reminder emails sent to assigned reviewers.
  - Select **Access Review Agent (Preview)** to allow reviewers to complete the access review in Microsoft Teams using natural language, insights, and recommendations. This option requires more setup—see the Access Review Agent unit for details.

16. Select **Next: Review + Create**.
17. Name the access review. Optionally, give the review a description. The name and description are shown to the reviewers.
18. Review the information and select **Create**.

### Start the access review

Once you specified the settings for an access review, select **Start**. The access review appears in your list with an indicator of its status.

By default, Entra ID sends an email to reviewers shortly after the review starts. If you choose not to have Entra ID send the email, be sure to inform the reviewers that an access review is waiting for them to complete. You can show them the instructions for how to review access to groups or applications. If your review is for guests to review their own access, show them the instructions for how to review access for yourself to groups or applications.

If you assigned guests as reviewers and they haven't accepted the invite, they don't receive an email from access reviews because they must first accept the invitation.

### Access review status table

| **Status** | **Definition** |
|---|---|
| NotStarted | Review was created, user discovery is waiting to start. |
| Initializing | User discovery is in progress to identify all users who are part of the review. |
| Starting | Review is starting. If email notifications are enabled, emails are being sent to reviewers. |
| InProgress | Review started. If email notifications are enabled, emails are sent to reviewers. Reviewers can submit decisions until the due date. |
| Completing | Review is being completed, and emails are being sent to the review owner. |
| Auto-Reviewing | Review is in a system reviewing stage. The system is recording decisions for users who weren't reviewed based on recommendations or preconfigured decisions. |
| Auto-Reviewed | Decisions are recorded by the system for all users who weren't reviewed. Review is ready to proceed to **Applying** if Auto-Apply is enabled. |
| Applying | There will be no change in access for users who were approved. |
| Applied | Denied users, if any, are removed from the resource or directory. |
| Failed | Review couldn't progress. This error could be related to the deletion of the tenant, a change in licenses, or other internal tenant changes. |

### Create reviews via APIs

You can also create access reviews using APIs. What you do to manage access reviews of groups and application users in the Entra admin center can also be done using Microsoft Graph APIs.


## Create and configure access reviews programmatically

Entra access reviews are a feature of Entra ID Governance. Access reviews help to ensure that the right identities have the right access to the right resources in the organization. Access reviews can be implemented programmatically using the access reviews API in Microsoft Graph.

To create an access review using Graph, call the Graph API to create an access review schedule definition. The caller must be either a user with at least the **Identity Governance Administrator** role, using an application that has the delegated `AccessReview.ReadWrite.All` permission, or an application with the `AccessReview.ReadWrite.All` application permission.

You can also create an access review in PowerShell with the `New-MgIdentityGovernanceAccessReviewDefinition` cmdlet from the Microsoft Graph PowerShell cmdlets for Identity Governance module.

The access reviews API in Microsoft Graph enables organizations to audit and attest to the access that identities are assigned to resources in the organization. For example, access to a SharePoint site that contains customer contact information. And by using the access reviews API, organizations can check and attest to access to such groups and by extension, resources.

### Access Review API for security groups

This learning module doesn't recreate the step-by-step method to use the API. For that information, see the article [Review access to security groups using access reviews APIs.](https://learn.microsoft.com/en-us/graph/tutorial-accessreviews-securitygroup) To review guest access in Microsoft 365 groups via API, see [Review access to Microsoft 365 groups using access reviews APIs](https://learn.microsoft.com/en-us/graph/tutorial-accessreviews-m365group). Here are the high-level steps that need to be performed.

1. Create an access review for the security group
2. List instances of the access review
3. Verify who was contacted for the review
4. Get decisions
5. Self-attest to a pending access decision
6. Confirm the decisions and the status of the access review
7. Clean up resources

During each step you can use the API to create the access review, assign it, check the results, and act on that information.


## Monitor access review findings

Entra ID simplifies how enterprises manage access to groups and applications with Entra access reviews. Other Microsoft Online Services such as Microsoft 365 can also be managed with Entra access reviews.

### Perform access review using My Apps

You can start the access review process from the notification email or by going directly to the site.

1. **Email**:
2. Select the **Start review** link to open the access review.
3. **If you don't have the email**, you can find your pending access reviews by following these steps:
  1. Sign in to the My Access portal at [https://myaccess.microsoft.com](https://myaccess.microsoft.com/).
  2. Select **Access reviews** from the left menu to see a list of pending access reviews assigned to you.  Important If no access reviews appear, there are no access reviews to perform for that organization and no action is needed at this time.
  3. Select the name of the access review you want to perform.

Once you open the access review, you see the names of users who need to have their access reviewed.

There are two ways that you can approve or deny access:

- You can approve or deny access for one or more users manually by choosing the appropriate action for each user request.
- You can accept the system recommendations.

#### Approve or deny access for one or more users

1. Review the list of users and decide whether to approve or deny their continued access.
  - To approve or deny access for a single user, select the circle next to their name.
  - To approve or deny access for multiple users, select the circles next to each user.

2. Select **Approve** or **Deny** on the bar.  Note If you're unsure, you can select "Don't know" and the user gets to keep their access and your choice is recorded in the audit logs.
3. The administrator of the access review can require that you supply a reason in the **Reason** box for your decision.
  - Even when a reason isn't required, you can still provide a reason for your decision and the information that you include is available to other reviewers.

4. Once you specify the action to take, select **Save**.
  - If a user is denied access, they aren't removed immediately. They're removed when the review period ends or when an administrator stops the review if [Auto apply](https://learn.microsoft.com/en-us/azure/active-directory/governance/complete-access-review) is enabled.
  - If there are multiple reviewers, the last submitted response is recorded. Consider an example where an administrator designates two reviewers – Alice and Bob. Alice opens the access review first and approves a user's access request. Before the review period ends, Bob opens the access review and denies access on the same request previously approved by Alice. The last decision denying the access is the response that gets recorded.

#### Approve or deny access based on recommendations

To make access reviews easier and faster for you, we also provide recommendations that you can accept with a single selection. The system generates recommendations using two methods:

- **No sign-in within 30 days**: Users who haven't signed in during the past 30 days are recommended for denial. The user's last sign-in date displays alongside the recommendation.
- **Peer outlier**: If a user doesn't have the same access as their peers, the system recommends denial based on the user's average distance in the organization's reporting structure.

To accept recommendations:

1. Select one or more users, then select **Accept recommendations** on the bar. Or, to accept recommendations for all unreviewed users, make sure no users are selected and then select **Accept recommendations** on the top bar.
2. Select **Submit** to confirm.


## Automate access review management tasks

You can choose to have access removal automated by setting the **Auto apply results to resource** to **Enable**. Once the review is completed and ends, users not approved by the reviewer are automatically removed from the resource—or kept with continued access. Access removal could mean removing their group membership, their application assignment, or revoking their right to elevate to a privileged role.

### Take recommendations

The recommendations are displayed to reviewers as part of the reviewer experience and indicate a person's last sign-in to the tenant or last access to an application. This information helps reviewers make the right access decision. Selecting "Take recommendations" follows the access review recommendations. At the end of an access review, the system applies these recommendations automatically for users that reviewers failed to respond to.

Recommendations are based on the criteria in the access review. For example, if you configure the review to remove access with no sign-in for 30 days, it recommends removing all users who fit that criterion. This applies to both interactive and non-interactive sign-ins. Recommendations can also be based on **peer outlier** analysis—if a user doesn't have the same access as others in their reporting structure, the system recommends denial. Microsoft is continually working on enhancing recommendations.

### Review guest user access

Use Access Reviews to review and clean up collaboration partners’ identities from external organizations. Configuration of a per-partner review can satisfy compliance requirements.

External identities can be granted access to company resources through one of the following actions:

- Added to a group.
- Invited to Teams.
- Assigned to an enterprise application or access package.
- Assigned a privileged role in Entra ID or in an Azure subscription.

This [sample script](https://github.com/microsoft/access-reviews-samples/tree/master/ExternalIdentityUse) shows where external identities invited into the tenant are used. You can see external users' group membership, role assignments, and application assignments in Entra ID. The script won't show any assignments outside of Entra ID, such as direct rights assignment to SharePoint resources, without the use of groups.

When creating an Access Review for groups or applications, you can choose to let the reviewer focus on **Everyone with access**, or **Guest users only**. By selecting Guest users only, reviewers are provided a focused list of external identities from Entra B2B that have access to the resource.


## Configure recurring access reviews

Access reviews can be set to occur on a recurring basis. Name your access review, select a start date, frequency, duration, and specify when the series ends—you can choose **Never**, a specific end date, or a set number of occurrences. Reviewers are notified at the start of each review. Reviewers can approve or deny access with a friendly interface and with the help of smart recommendations.

Why are recurring access reviews important? Because of lifecycle management. Everything that starts needs to have an end date. Between the start and end, we need to ensure permissions are what we need them to be. Not too much, not too little. And we regularly ask an owner if everything is still what they want it to be. With recurrence, we make sure this checking is done regularly.

After a recurring review series starts, you can update its settings or reviewers at any time. When updating, you can apply changes to just the **Current** instance (the active review) or to the **Series** (all future recurrences). For example, if a reviewer leaves the organization, update the Series to replace them for all upcoming reviews. If you only need to adjust settings for the review in progress, update the Current instance instead.


## Explore the Access Review Agent in Entra

Historically, access reviews are a manual process that can lead to potential errors and mistakes. Reviewers don't always have access to records and data to make review decisions, and often don't have enough time to complete the review. What if there was an agent that could help with the task?

### Access Review Agent in Entra

Empower your reviewers to make fast and accurate access decisions. The Access Review Agent with Entra ID Governance delivers insights and recommendations so reviewers can complete their work through a simple conversation, right inside Microsoft Teams.

#### How the agent works

The Access Review Agent proactively scans for active access reviews in your tenant. The agent then analyzes identified reviews by gathering extra insights, and generates a recommendation (approve / deny). The recommendation also includes a justification summary for each decision. The agent guides reviewers, in natural language, through the review process in Microsoft Teams. As the agent guides them through the review, they can examine the agent's reasoning behind the recommendations, ask questions in the context of the review itself, and finally make their own informed decision. The agents recommendation (approve / deny) for each decision relies on a deterministic scoring mechanism powered by multiple signals.

##### The agent considers the following signals:

- **User inactivity**: If the user signed in (recently)
- **User-to-Group affiliation**: If the user has a low affiliation with other users who have this access
- **Account enabled**: If the user's account is enabled (accountEnabled property)
- **Employment status**: If the user's employment ended (employeeLeaveDateTime property)
- **Lifecycle workflow history**: If the user has a mover workflow ran for them in the past 30 days
- **Decisions from previous reviews**: For recurring reviews, decisions from previous review iterations are considered
- **Access request history**: For access package assignment reviews, the request and approval history is considered

#### Prerequisites

To use the Access Review Agent in Entra, you need:

- Entra ID Governance *or* Entra Suite licenses.
- Onboard to Security Copilot with at least one security compute unit (SCU).
- Admins must have at least all the following roles to set up and manage the agent in the Entra admin center:
  - Identity Governance Administrator
  - Lifecycle Workflows Administrator
  - Security Copilot Contributor in Security Copilot

- For reviewers to use the Access Review Agent, they must have access to Microsoft Teams and must have an active access review assigned. They need to have the assigned role: -Security Copilot Contributor

#### Limitations

Once agents are started, they can't be stopped or paused. It might take a few minutes to run. We recommend running the agent from the Entra admin center.

### Enabling the Access Review Agent

1. With an account that has at least all the following roles, sign in to the Entra admin center:
  - Identity Governance Administrator
  - Lifecycle Workflows Administrator
  - Security Copilot Contributor

2. From the new home page, select Go to agents from the agent notification card.
  - You can also select Agents from the left navigation menu.

3. Select View details on the Access Review Agent tile.
4. Select Start agent to begin your first run.
  - A message that says "The agent is starting its first run" appears in the upper-right corner. The first run might take a few minutes to complete.

### Enable the access review agent for existing group and application access reviews

To update an existing access review for the Access Review Agent, perform the following steps:

1. Sign in to the Entra admin center as at least an Identity Governance Administrator.
2. Browse to **ID Governance** then **Access reviews**.
3. Select the access review you want the agent to support.
4. On the access review overview page, select **Settings** under **Manage** (one time review), or **Settings** under **Series** (recurring review).
5. Under Advanced Settings, check the box on the setting that says Access Review Agent (Preview).
6. Select Save.


## Module assessment

Choose the best response for each of the questions below.

### Check your knowledge


## Summary and resources

After completing this module, you're able to:

- Plan for access reviews.
- Create access reviews for groups and apps.
- Monitor access review findings.
- Create and manage access review programs.
- Automate access review management tasks.
- Configure recurring access reviews.
- Use the Access Review Agent to complete access reviews using natural language in Microsoft Teams.

In this module, you learned how to prepare for and perform access reviews. Access reviews are essential to the security of your organization, and how to configure them to occur on a recurring basis.

### Resources

Use these resources to discover more.

- [What are Access Reviews?](https://learn.microsoft.com/en-us/entra/id-governance/access-reviews-overview)
- [Manage user and guest access with Access Reviews](https://learn.microsoft.com/en-us/entra/id-governance/manage-access-review)
- [Review your access to resources with Entra Access Reviews](https://learn.microsoft.com/en-us/entra/id-governance/self-access-review)
- [Access review API overview](https://learn.microsoft.com/en-us/entra/id-governance/create-access-review#create-an-access-review-programmatically)
- [Access Review Agent](https://learn.microsoft.com/en-us/entra/id-governance/access-review-agent)
- [Review access to security groups using access reviews APIs](https://learn.microsoft.com/en-us/graph/tutorial-accessreviews-securitygroup)


---

# Plan and implement privileged access

_https://learn.microsoft.com/en-us/training/modules/plan-implement-privileged-access/_


## Introduction

To increase the security of your Azure solution, you must ensure that administrative roles are protected and managed. Explore how to use Privileged Identity Management (PIM) to protect your data and resources. In this module, you learn how to create an access strategy. Then you configure and assign PIM roles and resources, and manage emergency-access accounts.

### Learning objectives

By the end of this module, you are able to:

- Define a privileged access strategy for administrative users (resources, roles, approvals, thresholds).
- Configure PIM for Azure Roles.
- Configure PIM for Azure resources.
- Assign roles.
- Manage PIM requests.
- Analyze PIM audit history and reports.
- Create and manage emergency access accounts.
- Configure privileged access groups

Organizations want to minimize the number of people who have access to secure information or resources. Minimizing access reduces the chance of a malicious actor getting that access. It can also help prevent an authorized user inadvertently impacting a sensitive resource. However, users still need to carry out privileged operations in Entra ID, Azure, Microsoft 365, or SaaS apps. Organizations can give users just-in-time privileged access to Azure resources. Then can track and manage the need for oversight of what those users are doing with their administrator privileges.

### Prerequisites

None


## Define a privileged access strategy for administrative users

### What is Privileged identity management (PIM)?

PIM is a service in Entra ID, for managing access to privileged resources. PIM enables you to manage, control, and monitor access to important resources in your organization. Such resources include those in Entra ID, Azure, and other Microsoft Online Services, such as Microsoft 365 or Microsoft Intune.

### What does PIM do?

PIM provides time-based and approval-based role activation to access resources. This helps to mitigate the risks of excessive, unnecessary, or misused access permissions on resources that you care about. Key features of PIM include:

- Provide just-in-time privileged access to Entra ID and Azure resources
- Assign time-bound access to resources using start and end dates
- Require approval to activate privileged roles
- Enforce Azure Multifactor Authentication to activate any role
- Use justification to understand why users activate
- Get notifications when privileged roles are activated
- Conduct access reviews to ensure users still need roles
- Download audit history for internal or external audit

Before you deploy PIM in your organization, follow the instructions and understand the concepts in this section. This will help you create a plan tailored to your organization’s privileged identity requirements.

Note

PIM requires a Premium P2 license.

### Identify your stakeholders

The following section helps you identify all the stakeholders who are involved in the project. You'll look at who needs to approve, review, or stay informed. It includes separate tables for deploying PIM for Entra roles and PIM for Azure roles. Add stakeholders to the following table as appropriate for your organization.

SO = Approval on this project

R = Review this project and provide input

I = Informed of this project

#### Stakeholders: Privileged Identity Management for Entra roles

| **Name** | **Role** | **Action** |
|---|---|---|
| Name and email | **Identity architect or Azure Global Administrator** - A representative from the identity management team in charge of defining how to align this change with the core identity management infrastructure in your organization. | SO/R/I |
| Name and email | **Service owner or Line manager** - A representative from the IT owners of a service or a group of services. They're key in making decisions and helping to roll out PIM for their team. | SO/R/I |
| Name and email | **Security owner** - A representative from the security team who can approve that the plan meets the security requirements of your organization. | SO/R |
| Name and email | **IT support manager / Helpdesk** - A representative from the IT support organization who can provide feedback on the supportability of this change from a helpdesk perspective. | R/I |
| Name and email for pilot users | **Privileged role users** - The group of users for which privileged identity management is implemented. They'll need to know how to activate their roles once PIM is implemented. | I |

#### Stakeholders: Privileged Identity Management for Azure roles

| **Name** | **Role** | **Action** |
|---|---|---|
| Name and email | **Subscription/Resource owner** - A representative from the IT owners of each subscription or resource that you want to deploy PIM for. | SO/R/I |
| Name and email | **Security owner** - A representative from the security team that can approve that the plan meets the security requirements of your organization. | SO/R |
| Name and email | **IT support manager / Helpdesk** - A representative from the IT support organization who can provide feedback on the supportability of this change from a helpdesk perspective. | R/I |
| Name and email for pilot users | **Azure role users** - The group of users for which privileged identity management is implemented. They'll need to know how to activate their roles once PIM is implemented. | I |

### Start using Privileged Identity Management

As part of the planning process, prepare PIM by following our "Start using Privileged Identity Management" article. PIM gives you access to some features that are designed to help with your deployment.

If your goal is to deploy PIM for Azure resources, follow our "Discover Azure resources to manage in Privileged Identity Management" article. Only owners of subscriptions and management groups can bring these resources under management by PIM. After it's under management, the PIM functionality is available for owners at all levels, including management group, subscription, resource group, and resource. If you're a Global Administrator trying to deploy PIM for your Azure resources, you can elevate access to manage all Azure subscriptions. That gives you access to all Azure resources in the directory for discovery. However, we advise that you get approval from each of your subscription owners before managing their resources with PIM.

### Enforce principle of least privilege

It's important to make sure that you've enforced the principle of least privilege in your organization for both your Entra ID and your Azure roles.

#### Plan least privilege delegation

For Entra roles, organizations commonly assign the Global Administrator role to a number of administrators, when most of them only need one or two specific and less-powerful administrator roles. With a large number of Global Administrators or other high-privilege roles, it's hard to track your privileged role assignments closely enough.

Follow these steps to implement the principle of least privilege for your Entra roles.

1. Understand the granularity of the roles by reading and understanding the available Entra administrator roles. You and your team should also reference administrator roles by identity task in Entra ID, which explains the least privileged role for specific tasks.
2. List who has privileged roles in your organization. You can use the PIM Discovery and insights (preview) to reduce your exposure.
3. For all Global Administrators in your organization, find out why they need the role. Then remove them from the Global Administrator role and assign built-in roles or custom roles with lower privilege inside Entra ID. FYI, Microsoft currently only has about 10 administrators with the Global Administrator role.
4. For all other Entra roles, review the list of assignments, identify administrators who no longer need the role, and remove them from their assignments.

To automate the last two steps, you can use access reviews in PIM. Following the steps in "Start an access review for Entra roles in Privileged Identity Management," you can set up an access review for every Entra ID role that has one or more members.

Set the reviewers to **Members (self)**. All users in the role will receive an email asking them to confirm that they need the access. Also, turn on **Require reason on approval** in the advanced settings so that users must state why they need the role. Based on this information, you can remove users from unnecessary roles or delegate them to more granular administrator roles.

Access reviews rely on emails to notify people to review their access to the roles. If you've privileged accounts that don’t have emails linked, be sure to populate the secondary email field on those accounts.

#### Plan Azure resource role delegation

For Azure subscriptions and resources, you can set up a similar Access review process to review the roles in each subscription or resource. The goal of this process is to minimize Owner and User Access Administrator assignments attached to each subscription or resource and to remove unnecessary assignments. However, organizations often delegate such tasks to the owner of each subscription or resource because they have a better understanding of the specific roles (especially custom roles).

If you're in the Global Administrator role trying to deploy PIM for Azure roles in your organization, you can elevate access to manage all Azure subscriptions, which gets you access to each subscription. You can then find each subscription owner and work with them to remove unnecessary assignments and minimize owner role assignment.

Users with the Owner role for an Azure subscription can also use access reviews for Azure resources to audit and remove unnecessary role assignments, much like the process described earlier for Entra roles.

### Decide which role assignments should be protected by Privileged Identity Management

After cleaning up privileged role assignments in your organization, you'll need to decide which roles to protect with PIM.

If a role is protected by PIM, eligible users assigned to it must elevate to use the privileges granted by the role. The elevation process might also include obtaining approval, using Azure Multifactor Authentication, and providing the reason they're activating. PIM can also track elevations through notifications and the PIM and Entra audit event logs.

Choosing which roles to protect with PIM can be difficult and will be different for each organization. This section provides our best practices for Entra roles and Azure roles.

#### Entra roles

It's important to prioritize protecting Entra roles that have the most permissions. Based on usage patterns among all PIM customers, the top 10 Entra roles managed by PIM are:

- Global Administrator
- Security Administrator
- User Administrator
- Exchange Administrator
- SharePoint Administrator
- Intune Administrator
- Security Reader
- Service Administrator
- Billing Administrator
- Skype for Business Administrator  Tip Microsoft recommends managing all your Global Administrators and Security Administrators with PIM as a first step, because they can do the most harm when compromised.

It's important to consider the most sensitive data and permissions for your organization. As an example, some organizations want to protect their Power BI Administrator role or their Teams Administrator role using PIM, since they can access data and change core workflows.

If there are any roles with guest users assigned, they're vulnerable to attack.

Tip

Microsoft recommends that you manage all roles with guest users using PIM to reduce risk associated with compromised guest user accounts.

Reader roles like the Directory Reader, Message Center Reader, and Security Reader are sometimes regarded as less important than other roles, because they don’t have write permission. However, we have some customers who also protect those roles because attackers with access to those accounts might be able to read sensitive data, including personal data. Take this risk into consideration when deciding whether you want reader roles in your organization to be managed using PIM.

#### Azure roles

When deciding which role assignments should be managed using PIM for Azure resources, you must first identify the subscriptions/resources that are most vital for your organization. Examples of such subscriptions/resources are:

- Resources that host the most sensitive data.
- Resources that core customer-facing applications depend on.

If you're a Global Administrator having trouble deciding which subscriptions and resources are most important, contact the subscription owners in your organization to gather a list of the resources each subscription manages. Then, work with the subscription owners to group the resources based on severity level in the case they're compromised (low, medium, high). Prioritize managing resources with PIM based on this severity level.

Tip

Microsoft recommends you work with subscription/resource owners of critical services to set up PIM workflow for all roles inside sensitive subscriptions/resources.

PIM for Azure resources supports time-bound service accounts. You should treat service accounts exactly the same as you would treat a regular user account.

For subscriptions/resources that aren't as critical, you won’t need to set up PIM for all roles. However, you should still protect the Owner and User Access Administrator roles with PIM.

Tip

Microsoft recommends that you manage Owner roles and User Access Administrator roles of all subscriptions/resources using PIM.

### Decide whether to use a group to assign roles

Whether to assign a role to a group instead of to individual users is a strategic decision. When planning, consider assigning a role to a group to manage role assignments when:

- Many users are assigned to a role.
- You want to delegate assigning the role.

#### Many users are assigned to a role

Manually keeping track of who is assigned to a role and managing their assignments based on when they need it can take time. To assign a group to a role, first create a role-assignable group and then assign the group as eligible for a role. This action subjects everyone in the group to the same activation process as individual users who are eligible to elevate into the role. Group members activate their assignments to the group individually using the PIM activation request and approval process. The group isn't activated—just the user's group membership.

#### You want to delegate assigning the role

A group owner can manage membership for a group. For Entra ID role-assignable groups, only the Privileged Role Administrator, the Global Administrator, and the group owners can manage group membership. When an admin adds new members to the group, the member gets access to the roles to which the group is assigned whether the assignment is eligible or active. Use group owners to delegate the management of group membership for an assigned role to reduce the breadth of privilege required.

Tip

Microsoft recommends that you bring Entra ID role-assignable groups under management by PIM. After a role-assignable group is brought under management by PIM, it's called a privileged access group. Use PIM to require group owners to activate their Owner role assignment before they can manage group membership.

### Decide which role assignments should be permanent or eligible

Once you've decided the list of roles to be managed by PIM, you must decide which users should get the eligible role versus the permanently active role. **Permanently active roles are the normal roles assigned through Entra ID and Azure resources, while eligible roles can only be assigned in PIM.**

Microsoft recommends zero permanently active assignments for both Entra roles and Azure roles, apart from the two recommended break-glass emergency access accounts, which should have the permanent Global Administrator role.

Even though we recommend zero standing-administrators, it's sometimes difficult for organizations to achieve this right away. Things to consider when making this decision include:

- Frequency of elevation – If the user only needs the privileged assignment once, they shouldn’t have the permanent assignment. On the other hand, a user can be considered for the permanent role if they need it for their day-to-day job and PIM would greatly reduce their productivity.
- Cases specific to your organization – The person being given the eligible role may be from a distant team, or a high-ranking executive, to the point that communicating and enforcing the elevation process is difficult. They can be considered for the permanent role.  Tip Microsoft recommends you to set up recurring access reviews for users with permanent role assignments.

### Draft your Privileged Identity Management settings

Before you implement your PIM solution, it's good practice to draft your PIM settings for every privileged role your organization uses. This section has some examples of PIM settings for particular roles; they are for reference only and might be different for your organization. Each of these settings is explained in detail with Microsoft’s recommendations after the tables.

#### Privileged Identity Management settings for Entra roles

| **Setting** | **Global Administrator** | **Exchange Administrator** | **Helpdesk Administrator** |
|---|---|---|---|
| Require MFA; two-step verification | Yes | Yes | No |
| Notification | Yes | Yes | No |
| Incident ticket | Yes | No | Yes |
| Require approval | Yes | No | No |
| Approver | Other Global Administrators | None | None |
| Activation Duration | 1 hour | 2 hour | 8 hour |
| Permanent admin | Emergency access accounts | None | None |

#### Privileged Identity Management settings for Azure roles

| **Setting** | **Owner of critical subscriptions** | **User Access Administrator of less critical subscriptions** | **Virtual Machine Contributor** |
|---|---|---|---|
| Require MFA; two-step verification | Yes | Yes | No |
| Notification | Yes | Yes | Yes |
| Require approval | Yes | No | No |
| Approver | Other owners of the subscription | None | None |
| Activation Duration | 1 hour | 1 hour | 3 hour |
| Active admin | None | None | None |
| Active expiration | n/a | n/a | n/a |

The following table describes each of the settings.

| **Setting** | **Description** |
|---|---|
| Role | Name of the role you're defining the settings for. |
| Require MFA; two-step verification | Whether the eligible user needs to perform MFA; two-step verification before activating the role. |
|   | **Microsoft recommends** you enforce MFA; two-step verification for all administrator roles, especially if the roles have guest users. |
| Notification | If set to true, Global Administrator, Privileged Role Administrator, and Security Administrator in the organization will receive an email notification when an eligible user activates the role. |
|   | Some organizations don’t have an email address tied to their administrator accounts. To get these email notifications, set an alternative email address so administrators will receive these emails. |
| Incident ticket | Whether the eligible user needs to record an incident ticket number when activating their role. This setting helps an organization identify each activation with an internal incident number to mitigate unwanted activations. |
|   | **Microsoft recommends** taking advantage of incident ticket numbers to tie PIM into your internal system. This method can be useful for approvers who need context for the activation. |
| Require approval | Whether the eligible user needs to get approval to activate the role. |
|   | **Microsoft recommends** that you set up approval for roles with the most permission. Based on usage patterns of all PIM customers, Global Administrator, User Administrator, Exchange Administrator, Security Administrator, and Password Administrator are the most common roles with approval required. |
| Approver | If approval is required to activate the eligible role, list the people who should approve the request. By default, PIM sets the approver to be all users who are privileged role administrators whether they are permanent or eligible. |
|   | If a user is both eligible for an Entra role and an approver of the role, they will not be able to approve themselves. |
|   | **Microsoft recommends** that you choose approvers to be users who are most knowledgeable about the role and its frequent users rather than a Global Administrator. |
| Activation duration | The length of time a user will be activated in the role before it will expire. |
| Permanent admin | List of users who will be a permanent administrator for the role (never have to activate). |
|   | **Microsoft recommends** you have zero standing administrator for all roles except for Global Administrators. |
| Active admin | For Azure resources, active administrator is the list of users who will never have to activate to use the role. This list is not referred to as permanent administrator like in Entra roles because you can set an expiration time for when the user will lose this role. |
| Active expiration | Active role assignments for Azure roles expire after the configured duration. You can choose from 15 days, 1 month, 3 months, 6 months, 1 year or permanently active. |
| Eligible expiration | Eligible role assignments for Azure roles expire after this duration. You can choose from 15 days, 1 month, 3 months, 6 months, 1 year or permanently eligible. |


## Configure Privileged Identity Management for Azure resources

Using Entra PIM, you can improve the protection of your Azure resources. This is helpful to:

- Organizations that already use PIM to protect Entra roles.
- Management group and subscription owners who are trying to secure production resources.

When you first set up PIM for Azure resources, you need to discover and select the resources to protect with PIM. There's no limit to the number of resources that you can manage with PIM. However, we recommend starting with your most critical production resources.

### Discover resources

1. Sign in to the Entra admin center.
2. Open **Entra Privileged Identity Management**.
3. Select **Azure resources**.If this is your first time using PIM for Azure resources, you'll see a **Discover resources** page.
4. If another administrator in your organization is already managing Azure resources in PIM, you'll see a list of the resources that are currently being managed.
5. Select **Discover resources** to launch the discovery experience.
6. On the **Discovery** page, use **Resource state filter** and Select resource type to filter the management groups or subscriptions you have write permission to. It's probably easiest to start with **All** initially. You can search for and select management group or subscription resources to manage in PIM. When you manage a management group or a subscription in PIM, you can also manage its child resources.  Note When you add a new child Azure resource to a PIM-managed management group, you can bring the child resource under management by searching for it in PIM.
7. Select any unmanaged resources that you want to manage.
8. Select **Manage resource** to start managing the selected resources.
9. If you see a message to confirm the onboarding of the selected resource for management, select **Yes**


## Exercise configure Privileged Identity Management for Entra roles

### Configure Entra role settings

#### Open role settings

Follow these steps to open the settings for an Entra role.

1. Sign in to the [Entra admin center](https://entra.microsoft.com/) as a tenant administrator.
2. Search for and then select **Entra Privileged Identity Management.**
3. In the Privileged Identity Management screen, in the left navigation, select **Entra roles.**
4. On the Quick start page, in the left navigation, select **Settings.**
5. Review the list of roles and then, in the **Search by role name**, enter **compliance**.
6. In the results, select **Compliance Administrator**.
7. Review the role-setting details information.

#### Require approval to activate

If setting multiple approvers, approval completes as soon as one of them approves or denies. You can't require approval from at least two users. To require approval to activate a role, follow these steps.

1. In the Role setting details page, on the top menu, select **Edit**.
2. In the Edit role setting – Compliance Administrator screen, select the **Require approval to activate** check box.
3. Select **Select approvers**.
4. In the Select a member pane, select your administrator account, and then select **Select**.
5. Once you have configured the role settings, select **Update** to save your changes.


## Exercise assign Entra roles in Privileged Identity Management

With Entra ID, a Global administrator can make permanent Entra admin role assignments. These role assignments can be created using the Azure portal or using PowerShell commands.

The Entra Privileged Identity Management (PIM) service also allows Privileged role administrators to make permanent admin role assignments. Additionally, Privileged role administrators can make users eligible for Entra admin roles. An eligible administrator can activate the role when they need it, and then their permissions expire once they're done.

### Assign a role

Follow these steps to make a user eligible for an Entra admin role.

1. Sign in to the [Entra admin center](https://entra.microsoft.com/) as a tenant administrator.
2. Search for and then select **Entra Privileged Identity Management.**
3. In the Privileged Identity Management screen, in the left navigation, select **Entra roles.**
4. On the Quick start page, in the left navigation, select **Roles**.
5. On the top menu, select **+ Add assignments.**
6. In the Add assignments pane, on the **Membership** tab, review the settings.
7. Select the **Select role** menu and then select **Compliance Administrator**. You can use the **Search role by name** filter to help located a role.
8. Under **Select member(s),** select **No members selected**.
9. In the Select a member pane, select your administrator account, and then select **Select**.
10. In the Add assignments screen, select **Next**.
11. On the **Settings** tab, under **Assignment type**, review the available options. For this task, use the default setting.
  - Eligible assignments require the member of the role to perform an action to use the role. Actions might include performing a multifactor authentication (MFA) check, providing a business justification, or requesting approval from designated approvers.
  - Active assignments don't require the member to perform any action to use the role. Members assigned as active have the privileges always assigned to the role.

12. Review the remaining settings and then select **Assign**.

### Activate your Entra roles

When you need to assume an Entra role, you can request activation by opening **My roles** in Privileged Identity Management.

1. On the Privileged Identity Management screen, in the left navigation menu, select **My roles.**
2. In the My roles pane, review the list of eligible assignments.
3. In the Compliance Administrator role row, select **Activate**.
4. In the Activate – Compliance Administrator pane, select **Additional verification required,** and then follow the instructions to provide extra security verification. You're required to authenticate only once per session.
5. After you've completed the security verification, in the Activate – Compliance Administrator pane, in the **Reason** box, enter the justification for activating this role.
6. Select **Activate**.

### Assign a role with restricted scope

For certain roles, the scope of the granted permissions can be restricted to a single admin unit, service principal, or application. This procedure is an example if assigning a role that has the scope of an administrative unit.

1. Browse to the Privileged Identity Management screen, and in the left navigation menu, select **Entra roles.**
2. In the Roles pane, on the top menu, select **+ Add assignments.**
3. In the Add assignments screen, select the **Select role** menu, and then select **User administrator.**
4. Select the **Scope type** menu and review the available options. For now, you'll use the **Directory** scope type.  Tip Go to [Manage administrative units in Entra ID](https://learn.microsoft.com/en-us/azure/active-directory/roles/administrative-units) to find more information about the administrative unit scope type.
5. Similar to assigning a role without a restricted scope. Add members, and complete the settings options. For now, select **Cancel**.

### Update or remove an existing role assignment

Follow these steps to update or remove an existing role assignment.

1. In the Open Entra Privileged Identity Management then Entra roles screen, in the left navigation, select **Assignments**.
2. In **Assignments** list, for Compliance Administrator, review the options in the **Action** column.
3. Select **Update** and review the options available in the Membership settings pane. When complete, close the pane.
4. Select **Remove**.
5. In the **Remove** dialog box, review the information, and then select **Yes**.


## Exercise assign Azure resource roles in Privileged Identity Management

### Assign Azure resource roles

Entra Privileged Identity Management (PIM) can manage the built-in Azure resource roles, as well as custom roles, including (but not limited to):

- Owner
- User Access Administrator
- Contributor
- Security Admin
- Security Manager

Follow these steps to make a user eligible for an Azure resource role.

1. Sign in to the [Entra admin center](https://entra.microsoft.com/) as a tenant administrator.
2. Search for and then select **Entra Privileged Identity Management.**
3. In the Privileged Identity Management menu, in the left navigation, select **Azure resources.**
4. On the top menu, select **Discover resources**.
5. In the Azure resources – Discovery screen, select your subscription and then, on the top menu, select **Manage resource**.
6. In the **Onboarding selected resource for management** dialog box, review the information and then select **OK**.
7. When onboarding completes, close the Azure resources – Discovery screen.
8. In the Azure resources screen, select the resource you just added.
9. In the left navigation menu, under **Manage**, select **Roles** to see the list of roles for Azure resources.
10. On the top menu, select + **Add assignments**.
11. In the **Add assignments dialog**, select the **Select role** menu and then select **API Management Service Contributor.**
12. Under **Select member(s),** select **No member selected**.
13. In the Select a member or group pane, select an account from your organization that will be assigned the role.
14. Select **Next**.
15. On the **Settings** tab, under **Assignment type**, select **Eligible**.
  - **Eligible** assignments require the member of the role to perform an action to use the role. Actions might include performing a multifactor authentication (MFA) check, providing a business justification, or requesting approval from designated approvers.
  - **Active** assignments do not require the member to perform any action to use the role. Members assigned as active have the privileges always assigned to the role.

16. Specify an assignment duration by changing the start and end dates and times.
17. When finished, select **Assign**.
18. After the new role assignment is created, a status notification is displayed.

### Update or remove an existing resource role assignment

Follow these steps to update or remove an existing role assignment.

1. Open **Entra Privileged Identity Management**.
2. Select **Azure resources**.
3. Select the resource you want to manage to open its overview page.
4. Under **Manage**, select **Assignments**.
5. On the **Eligible roles** tab, in the Action column, review the available options.
6. Select **Remove**.
7. In the **Remove** dialog box, review the information and then select **Yes**.


## Plan and configure Privileged Access Groups

In Privileged Identity Management (PIM), you can now assign eligibility for membership or ownership of privileged access groups. You can assign Entra ID built-in roles to cloud groups and use PIM to manage group member and owner eligibility and activation. With the privileged access groups preview, you can give workload-specific administrators quick access to multiple roles with a single just-in-time request.

**Example**: Your **Tier 0 Office Admins** might need just-in-time access to the **Exchange Admin**, **Office Apps Admin**, **Teams Admin**, and **Search Admin** roles to thoroughly investigate incidents daily.

You can create a role-assignable group called “Tier 0 Office Admins”, and make it eligible for assignment to the four roles previously mentioned (or any Entra built-in roles). Then you enable it for Privileged Access in the group’s Activity section. Once enabled for privileged access, you can assign your admins and owners to the group. When the admins elevate the group into the roles, your staff will have permissions from all four Entra roles.

### Require different policies for each role assignable group

Some organizations use tools like Entra business-to-business (B2B) collaboration to invite their partners as guests to their Entra organization. Instead of a single just-in-time policy for all assignments to a privileged role, you can create two different privileged access groups with their own policies. You can enforce less strict requirements for your trusted employees, and stricter requirements like approval workflow for your partners when they request activation into their assigned role.

## Analyze Privileged Identity Management audit history and reports

With PIM, you can view activity, activations, and audit history for privileged access group members and owners within your Entra organization.

If your organization has outsourced management functions to a service provider who uses [Azure delegated resource management](https://learn.microsoft.com/en-us/azure/lighthouse/concepts/azure-delegated-resource-management), role assignments authorized by that service provider won't be shown here.

Follow these steps to view the audit history for privileged access groups.

### View resource audit history

### **Resource audit** gives you a view of all activity associated with your privileged access groups.

1. Open **Entra Privileged Identity Management**.
2. Select **Groups**.
3. Select the privileged access group you want to view audit history for.
4. Under **Activity**, select **Resource audit**.
5. Filter the history using a predefined date or custom range.

### View my audit

**My audit** enables you to view your personal role activity for a privileged access group.

1. Open **Entra Privileged Identity Management**.
2. Select **Groups**.
3. Select the privileged access group you want to view audit history for.
4. Under **Activity**, select **My audit**.
5. Filter the history using a predefined date or custom range.


## Create and manage emergency access accounts

It's important that you prevent being accidentally locked out of your Entra ID. With Entra ID, you can't sign in or activate another user's account as an administrator. You can mitigate the chance of accidental lack of administrative access. The secret, create two or more *emergency access accounts* in your organization.

Emergency access accounts are highly privileged, and they aren't assigned to specific individuals. Emergency access accounts are limited to emergency or "break glass"' scenarios where normal administrative accounts can't be used. We recommend that you restrict access to emergency account. Use the accounts only when it's necessary.

This article provides guidelines for managing emergency access accounts in Entra ID.

### Why use an emergency access account

An organization might need to use an emergency access account in the following situations:

- The user accounts are federated, and federation is currently unavailable because of a cell-network break or an identity-provider outage. For example, if the identity provider host in your environment has gone down, users might be unable to sign in when Entra ID redirects to their identity provider.
- The administrators are registered through Entra Multifactor Authentication. All their individual devices are unavailable or the service is unavailable. Users might be unable to complete multifactor authentication to activate a role. For example, a cell network outage is preventing them from answering phone calls or receiving text messages. Especially when these authentication-methods are the only two authentication mechanisms that they registered.
- The person with the most recent Global Administrator access has left the organization. Entra ID prevents the last Global Administrator account from being deleted, but it doesn't prevent the account from being deleted or disabled on-premises. Either situation might make the organization unable to recover the account.
- Unforeseen circumstances such as a natural disaster emergency, during which a mobile phone or other networks might be unavailable.

### Create emergency access accounts

Create two or more emergency access accounts. These accounts should be cloud-only accounts that use the .onmicrosoft.com domain and that aren't federated or synchronized from an on-premises environment.

When an admin configures emergency accounts, the following requirements must be met:

- The emergency access accounts shouldn't be associated with any individual user in the organization. Make sure that your accounts aren't connected with any employee-supplied mobile phones, hardware tokens that travel with individual employees, or other employee-specific credentials. This precaution covers instances where an individual employee is unreachable when the credential is needed. Any registered devices need to be kept in known, secure location. These locations need multiple means of communicating with Entra ID.
- The authentication mechanism used for an emergency access account should be distinct. Keep it separate from that used by your other administrative accounts, including other emergency-access accounts. For example, if your normal administrator sign-in is via on-premises MFA, then multifactor authentication would be a different mechanism. However, if multifactor authentication is your primary part of authentication for your administrative accounts, then consider a different approach for emergency-accounts. Try things such as using Conditional Access with a third-party MFA provider via Custom controls.
- The device or credential must not expire or be in scope of automated cleanup due to lack of use.
- You should make the Global Administrator role assignment permanent for your emergency access accounts.

#### Exclude at least one account from phone-based multifactor authentication

To reduce the risk of an attack resulting from a compromised password, Entra ID recommends that you require multifactor authentication for all individual users. This group includes administrators and all others (for example, financial officers) whose compromised account would have a significant opportunity to cause harm.

However, at least one of your emergency access accounts shouldn't have the same multifactor authentication mechanism as your other non-emergency accounts. This includes third-party multifactor authentication solutions. You may have a Conditional Access policy requiring multifactor authentication for every administrator for Entra ID and other connected software as a service (SaaS) apps. Exclude emergency access accounts from that requirement, and configure a different mechanism for them instead. Additionally, you should make sure the accounts don't have a per-user multifactor authentication policy.

#### Exclude at least one account from Conditional Access policies

During an emergency, you don't want a policy to potentially block your access to fix an issue. At least one emergency access account should be excluded from all Conditional Access policies.

### Federation guidance

Organizations that use AD Domain Services and ADFS, or a similar identity provider, to federate to Entra ID have another option: configure an emergency access account whose MFA claim could be supplied by that identity provider. For example, the emergency access account could be backed by a certificate and key pair such as one stored on a smartcard. When that user is authenticated to AD, ADFS can supply a claim to Entra ID indicating that the user has met MFA requirements. Even with this approach, organizations must still have cloud-based emergency access accounts in case federation can't be established.

### Monitor sign in and audit logs

Organizations should monitor sign in and audit log activity from the emergency accounts and trigger notifications to other administrators. When you monitor the activity on break-glass accounts, you can verify these accounts are only used for testing or actual emergencies. You can use Azure Log Analytics to monitor the sign-in logs and trigger email and SMS alerts to your admins whenever break-glass accounts sign in.

### Validate accounts regularly

When you train staff members to use emergency access accounts and validate the emergency access accounts, at minimum do the following steps at regular intervals:

- Ensure that security-monitoring staff is aware that the account-check activity is ongoing.
- Ensure that the emergency break-glass process to use these accounts is documented and current.
- Ensure that administrators and security officers who might need to perform these steps during an emergency are trained on the process.
- Update the account credentials, in particular any passwords, for your emergency access accounts, and then validate that the emergency access accounts can sign in and perform administrative tasks.
- Ensure that users haven't registered multifactor authentication or self-service password reset (SSPR) to any individual user’s device or personal details.
- If the accounts are registered for multifactor authentication to a device, for use during sign-in or role activation, make sure that device is accessible to all administrators who might need it during an emergency. Also verify that the device can communicate through at least two network paths that don't share a common failure mode. For example, the device can communicate to the internet through both a facility's wireless network and a cell provider network.

These steps should be performed at regular intervals and for key changes:

- At least every 90 days
- When there has been a recent change in IT staff, such as a job change, a departure, or a new hire
- When the Entra subscriptions in the organization have changed


## Module assessment

Choose the best response for each of the questions below.

### Check your knowledge


## Summary and resources

Now that you reviewed this module, you're able to:

- Define a privileged access strategy for administrative users (resources, roles, approvals, thresholds).
- Configure PIM for Entra roles.
- Configure PIM for Azure resources.
- Assign roles.
- Manage PIM requests.
- Analyze PIM audit history and reports.
- Create and manage emergency access accounts.
- Configure privileged access groups

In this module, you learned how to develop a privileged access strategy. This included steps such as identifying stakeholders, deciding on role assignments, and identifying groups to assign roles. You assigned Entra roles in PIM and learned how to analyze audit history and reports. Armed with this new knowledge, you can now implement privileged access in your organization.

### Resources

To learn more about these topics, review these links.

- [Elevate access to manage all Azure subscriptions](https://learn.microsoft.com/en-us/azure/role-based-access-control/elevate-access-global-admin)
- [Access reviews for Azure resources](https://learn.microsoft.com/en-us/azure/active-directory/privileged-identity-management/pim-resource-roles-start-access-review)
- [Break-glass emergency access accounts](https://learn.microsoft.com/en-us/azure/active-directory/roles/security-emergency-access)
- [Management capabilities for Privileged Access groups](https://learn.microsoft.com/en-us/azure/active-directory/privileged-identity-management/groups-features)


---

# Monitor and maintain Entra ID

_https://learn.microsoft.com/en-us/training/modules/monitor-maintain-azure-active-directory/_


## Introduction

Entra ID audit and diagnostic logs provide a rich view into how users are accessing your Azure solution. Learn to monitor, troubleshoot, and analyze sign-in data.

### Learning objectives

By the end of this module, you're able to:

- Analyze and investigate sign-in logs to troubleshoot access issues.
- Review and monitor Entra audit logs.
- Enable and integrate Entra diagnostic logs with Log Analytics / Microsoft Sentinel.
- Export sign-in and audit logs to a third-party SIEM tool.
- Review Entra activity by using Log Analytics / Microsoft Sentinel, excluding KQL use.
- Analyze Entra workbooks/reporting.
- Monitor security posture with identity secure score.
- Configure notifications.

### Prerequisites

None


## Analyze and investigate sign-in logs to troubleshoot access issues

The reporting architecture in Entra ID consists of the following components:

- **Activity**
  - **Sign-ins** - Information about the usage of managed applications and user sign-in activities.
  - **Audit logs** - Audit logs provide system activity information about users and group management, managed applications, and directory activities.
  - **Provisioning logs** - Provisioning logs enable customers to monitor activity by the provisioning service, such as creating a group in ServiceNow or a user imported from Workday.

- **Security**
  - **Risky sign-ins** - A risky sign-in is an indicator for a sign-in attempt by someone who isn't the legitimate owner of a user account.
  - **Users flagged for risk** - A risky user is an indicator for a user account that might have been compromised.

#### Who can access the data?

- Users in the Security Administrator, Security Reader or Administrator, Global Reader, and Report Reader roles
- Any user (non-admins) can access their own sign-ins

#### What Entra license do you need to access sign-in activity?

The sign-in activity report is available in all editions of Entra ID and can also be accessed through the Microsoft Graph API.

### Sign-ins report

The user sign-ins report provides answers to the following questions:

- What is the sign-in pattern of a user?
- How many users have signed in over a week?
- What’s the status of these sign-ins?

On the Azure portal menu, select **Entra ID**, or search for and select **Entra ID** from any page.

Under **Monitoring**, select **Sign-ins** to open the Sign-ins report.

It takes up to two hours for sign-in records to show up in the portal.

Important

The sign-ins report only displays the interactive sign-ins—those in which a user manually signs in using their username and password. Non-interactive sign-ins, such as service-to-service authentication, are not displayed in the sign-ins report.

A sign-ins log has a default list view that shows the:

- Sign-in date
- Related user
- Application the user has signed in to
- Sign-in status
- Status of the risk detection
- Status of the multifactor authentication (MFA) requirement

You can customize the list view by selecting Columns in the toolbar.

The Columns dialog gives you access to the selectable attributes. In a sign-in report, you can't have fields that have more than one value for a given sign-in request as column. For example, the rule is true for authentication details, Conditional Access data, and network location.

Select an item in the list view to get more detailed information.

Customers can now troubleshoot Conditional Access policies through all sign-in reports. When an admin selects the Conditional Access tab for a sign-in record, customers can review the Conditional Access status. They can also dive into the details of the policies that applied to the sign-in, and the result for each policy. For more information, see the [FAQ about CA information in all sign-ins](https://learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/reports-faq).

### Filter sign-in activities

First, narrow down the reported data to a level that works for you. Second, filter sign-in data using date field as default filter. Entra ID provides you with a broad range of other filters you can set:

**Request ID** - The ID of the request you care about.

**User** - The name or the user principal name (UPN) of the user you care about.

**Application** - The name of the target application.

**Status** - The sign-in status you care about:

- Success
- Failure
- Interrupted

**IP address** - The IP address of the device used to connect to your tenant.

**Location** - The location the connection was initiated from:

- City
- State/Province
- Country/Region

**Resource** - The name of the service used for the sign-in.

**Resource ID** - The ID of the service used for the sign-in.

**Client app** - The type of the client app used to connect to your tenant:

| **Name** | **Modern authentication** | **Description** |
|---|---|---|
| Authenticated SMTP |   | Used by POP and IMAP clients to send email messages. |
| Autodiscover |   | Used by Outlook and EAS clients to find and connect to mailboxes in Exchange Online. |
| Exchange ActiveSync |   | Shows all sign-in attempts where the EAS protocol has been attempted. |
| Browser | Yes | Shows all sign-in attempts from users using web browsers. |
| Exchange ActiveSync |   | Shows all sign-in attempts from users with client apps using Exchange ActiveSync to connect to Exchange Online. |
| Exchange Online PowerShell |   | Used to connect to Exchange Online with remote PowerShell. If you block basic authentication for Exchange Online PowerShell, you need to use the Exchange Online PowerShell module to connect. |
| Exchange Web Services |   | A programming interface that's used by Outlook, Outlook for Mac, and third-party apps. |
| IMAP4 |   | A legacy mail client using IMAP to retrieve email. |
| MAPI over HTTP |   | Used by Outlook 2010 and later. |
| Mobile apps and desktop clients | Yes | Shows all sign-in attempts from users using mobile apps and desktop clients. |
| Offline Address Book |   | A copy of address list collections that are downloaded and used by Outlook. |
| Outlook Anywhere (RPC over HTTP) |   | Used by Outlook 2016 and earlier. |
| Outlook Service |   | Used by the Mail and Calendar app for Windows 10. |
| POP3 |   | A legacy mail client using POP3 to retrieve email. |
| Reporting Web Services |   | Used to retrieve report data in Exchange Online. |
| Other clients |   | Shows all sign-in attempts from users where the client app is not included or unknown. |

**Operating system** - The operating system running on the device used to sign on to your tenant.

**Device browser** - If the connection was initiated from a browser, this field enables you to filter by browser name.

**Correlation ID** - The correlation ID of the activity.

**Conditional Access** - The status of the applied Conditional Access rules.

- **Not applied**: No policy applied to the user and application during sign-in.
- **Success**: One or more Conditional Access policies applied to the user and application (but not necessarily the other conditions) during sign-in.
- **Failure**: The sign-in satisfied the user and application condition of at least one Conditional Access policy, and grant controls are either not satisfied or set to block access.

### Download sign-in activities

Select the **Download** option to create a CSV or JSON file of the most recent 250,000 records. Start with **Download Sign-ins** if you want to work with the data outside the Azure portal.

Important

The number of records you can download is constrained by the [Entra ID report retention policies](https://learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/reference-reports-data-retention).

### Sign-ins data shortcuts

Entra ID and the Azure portal both provide you with additional entry points to sign-in data:

- Identity Protection, found in Entra ID - Security - Identity Protection
- Users
- Groups
- Enterprise applications

#### Users sign-in data in Identity Protection

The user sign-in graph in the **Identity Protection** overview page shows weekly aggregations of sign-ins. The default for the period is 30 days.

Select a day in the sign-in graph, you get an overview of the sign-in activities for this day.

Each row in the sign-in activities list shows:

- Who has signed in?
- What application was the target of the sign-in?
- What is the status of the sign-in?
- What is the MFA status of the sign-in?

When the admin selects an item, you get more details about the sign-in operation:

- User ID
- User
- Username
- Application ID
- Application
- Client
- Location
- IP address
- Date
- MFA Required
- Sign-in status  Note IP addresses are issued in such a way that there is no definitive connection between an IP address and the physical location of the computer using it. Mapping IP addresses is also complicated because mobile providers and VPNs issue IP addresses from central pools, often very far from where the client device is actually used. Currently in Entra reports, converting an IP address to a physical location is a best effort based on traces, registry data, reverse look-ups, and other information.

On the **Users** page, you get a complete overview of all user sign-ins by selecting **Sign-ins** in the **Activity** section.

### Usage of managed applications

With an application-centric view of your sign-in data, you can answer questions such as:

- Who is using my applications?
- What are the top three applications in my organization?
- How is my newest application doing?

The entry point to this data is the top three applications in your organization. The data is contained within the last 30 days report in the **Overview** section under **Enterprise applications**.

The app-usage graphs weekly aggregations of sign-ins for your top three applications in a given time period. The default time period is 30 days.

If you want to, you can set the focus on a specific application.

When you select a day in the app usage graph, you get a detailed list of the sign-in activities.

The **Sign-ins** option gives you a complete overview of all sign-in events to your applications.

### Microsoft 365 activity logs

You can view Microsoft 365 activity logs from the Microsoft 365 admin center. Microsoft 365 activity and Entra activity logs share a significant number of the directory resources. Only the Microsoft 365 admin center provides a full view of the Microsoft 365 activity logs.

You can also access the Microsoft 365 activity logs programmatically by using the Office 365 Management APIs.


## Review and monitor Entra audit logs

The Entra audit logs provide records of system activities for compliance. To access the audit report, select **Audit logs** in the **Monitoring** section of **Entra ID**.

An audit log has a default list view that shows the:

- Date and time of the occurrence
- Service that logged the occurrence
- Category and name of the activity (*what*)
- Status of the activity (success or failure)
- Target
- Initiator/actor (who) of an activity

You can customize the list view by clicking **Columns** in the toolbar.

Custom columns enables you to display other fields or remove fields that are already displayed.

Select an item in the list view to get more detailed information.

### Filtering audit logs

You can filter the audit data on the following fields:

- Service
- Category
- Activity
- Status
- Target
- Initiated by (Actor)
- Date range

The **Service** filter allows you to select from a drop-down list of the following services:

- All
- Entra Management UX
- Access Reviews
- Account Provisioning
- Application Proxy
- Authentication Methods
- Business to Customer (B2C)
- Conditional Access
- Core Directory
- Entitlement Management
- Hybrid Authentication
- Identity Protection
- Invited Users
- MIM Service
- MyApps
- Privileged Identity Management (PIM)
- Self-service Group Management
- Self-service Password Management
- Terms of Use

The **Category** filter enables you to select one of the following filters:

- All
- Administrative unit
- ApplicationManagement
- Authentication
- Authorization
- Contact
- Device
- DeviceConfiguration
- DirectoryManagement
- EntitlementManagement
- GroupManagement
- KerberosDomain
- KeyManagement
- Label
- Other
- PermissionGrantPolicy
- Policy
- ResourceManagement
- RoleManagement
- UserManagement

The **Activity** filter is based on the category and activity resource type selection you make. You can select a specific activity you want to see or choose all.

You can get the list of all Audit Activities using the Graph API: `https://graph.windows.net/<tenantdomain>/activities/auditActivityTypesV2?api-version=beta`

The **Status** filter allows you to filter based on the status of an audit operation. The status can be one of the following values:

- All
- Success
- Failure

The **Target** filter allows you to search for a particular target by the starting of the name or user principal name (UPN). The target name and UPN are case-sensitive.

The **Initiated by** filter enables you to define what an actor's name or a universal principal name (UPN) starts with. The name and UPN are case-sensitive.

The **Date range** filter enables to you to define a timeframe for the returned `data.Possible` values are:

- 7 days
- 24 hours
- Custom

When you select a custom timeframe, you can configure a start time and an end time.

You can also choose to download the filtered data, up to 250,000 records, by selecting the **Download** button. You can download the logs in either CSV or JSON format. The number of records you can download is constrained by the Entra report retention policies.

### Audit logs shortcuts

In addition to **Entra ID**, the Azure portal provides you with two other entry points to audit data:

- Users and groups
- Enterprise applications

#### Users and groups audit logs

With user and group-based audit reports, you can get answers to questions such as:

- What types of updates were applied to users?
- How many users were changed?
- How many passwords were changed?
- What has an administrator done in a directory?
- What are the groups that were added?
- Are there groups with membership changes?
- Have the owners of a group been changed?
- What licenses were assigned to a group or a user?

To review only auditing data related to users, use the filtered view under **Audit logs** in the **Monitoring** section of the **Users** tab. This entry point has **UserManagement** as preselected category.

To review only auditing data related to groups, use the filtered view under **Audit logs** in the **Monitoring** section of the **Groups** tab. This entry point has **GroupManagement** as preselected category.

#### Enterprise applications audit logs

With application-based audit reports, you can get answers to questions such as:

- What applications were added or updated?
- What applications were removed?
- Has a service principal for an application changed?
- Have the names of applications been changed?
- Who gave consent to an application?

If you want to review audit data related to your applications, you can find a filtered view under **Audit logs** in the **Activity** section of the **Enterprise applications** screen. This entry point has **Enterprise applications** preselected as the **Application Type**.

### Microsoft 365 activity logs

You can view Microsoft 365 activity logs from the Microsoft 365 admin center. Even though Microsoft 365 activity and Entra activity logs share numerous directory resources, only the Microsoft 365 admin center provides a full view of the Microsoft 365 activity logs. You can also access the Microsoft 365 activity logs programmatically by using the Office 365 Management APIs.


## Exercise connect data from Entra ID to Microsoft Sentinel

In this unit we take a look at what is Microsoft Sentinel?

A security information and event management (SIEM) aggregates and analyzes activity. A security orchestration automation and remediation (SOAR) tool collects data on security threats and responds. Microsoft Sentinel is a scalable, cloud-native SIEM, and SOAR solution. Microsoft Sentinel is your birds-eye view across the enterprise alleviating the stress of increasingly sophisticated attacks, increasing volumes of alerts, and long resolution time frames.

- Collect data at cloud scale across all users, devices, applications, and infrastructure, both on-premises and in multiple clouds
- Detect previously undetected threats, and minimize false positives using Microsoft analytics and unparalleled threat intelligence
- Investigate threats with artificial intelligence, and hunt for suspicious activities at scale, tapping into years of cyber security work at Microsoft
- Respond to incidents rapidly with built-in orchestration and automation of common tasks

### Prerequisites

- An Entra ID P1 or P2 license is required to ingest sign-in logs into Microsoft Sentinel. Any Entra ID license (Free/O365/P1/P2) is sufficient to ingest the other log types. Additional per-gigabyte charges might apply for Azure Monitor (Log Analytics) and Microsoft Sentinel.
- Your user must be assigned the Microsoft Sentinel Contributor role on the workspace.
- Your user must be assigned the Security Administrator role on the tenant you want to stream the logs from.
- Your user must have read and write permissions to the Entra diagnostic settings to be able to see the connection status.

### Create and add a Microsoft Sentinel workspace

Use these instructions if you don't already have a workspace available to Microsoft Sentinel.

1. Sign in to the [Azure portal](https://portal.azure.com/) as a tenant administrator.
2. Search for and select **Microsoft Sentinel**.
3. In the Microsoft Sentinel workspaces screen, on the menu, select **+ Add**. If you already have a Microsoft Sentinel workspace, you can select that and continue to the next task.
4. In the Add Microsoft Sentinel to a workspace screen, select **Create a new workspace**.
5. Use the following information to create a new log analytics workspace:    **Setting** **Value**     Subscription Use your current subscription.   Resource group Use an existing resource group or create a new one.   Name Lab-workspace-yourinitialsanddate.    The workspace must be a globally unique value.   Pricing tier Pay-as-you-go
6. When complete, select your new workspace and then select **Add** to add the workspace to Microsoft Sentinel.

### Connect to Entra ID

You can use Microsoft Sentinel's built-in connector to collect data from Entra ID and stream it into Microsoft Sentinel. The connector allows you to stream [sign in logs](https://learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/concept-sign-ins) and [audit logs](https://learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/concept-audit-logs).

1. In Microsoft Sentinel, in the navigation menu on the left, under **Configuration**, select **Data connectors**.
2. In the **Data connectors** list, select **Entra ID** and then select **Open connector page**.
3. Under **Configuration**, select the **Entra Sign in logs** and **Audit logs** checkboxes and then select **Apply changes**.
4. Close the Entra ID connector page.


## Export logs to third-party security information and event management system

Since the introduction of Azure Monitor, significant strides have been made to consolidate Azure services onto a single logging pipeline. Most of the top Azure services, including Azure Resource Manager and Microsoft Defender for Cloud, have onboarded to Azure Monitor and are producing relevant security logs.

Integration with key capabilities like security information and event management (SIEM) tools is also simpler now: you can route data to a single Azure Event Hubs and enable multiple diagnostic settings per resource. Work in flight will ease setup and management of log routing across large Azure environments.

Azure has also partnered with the top SIEM partners to build connectors that get the data from Azure Monitor into those tools. These connectors consume data routed to Azure Event Hubs by Azure Monitor: a simple, scalable, and manageable approach for delivering log data to an external application. It's also the Microsoft recommended approach for integrating Azure with SIEM tools going forward.

We’ve continued to support customers who are using the Azure Log Integration tool (AzLog) to integrate with these same SIEMs. AzLog was initially released to help customers navigate the complex process of consolidating, translating, and forwarding logs from a variety of Azure services to a SIEM tool. At the time, Azure Monitor didn’t exist, and there was very little standardization in terms of how Azure services exposed log data to customers. Some dumped data into a storage account, others exposed an API, etc.

### Integration recommendations

The table below indicates what you should do based on the SIEM tool(s) you're using and your current integration status. Only SIEM tools that were officially supported by AzLog are included below.

| **SIEM Tool** | **Currently using log integrator** | **Currently investigating SIEM integration options** |
|---|---|---|
| Splunk | Begin migrating to the Azure Monitor Add-On for Splunk. | Use the Azure Monitor Add-On for Splunk. |
| IBM QRadar | Begin migrating to the Microsoft Azure DSM and Microsoft Azure Event Hubs Protocol, available from the IBM support website. | Use the Microsoft Azure DSM and Microsoft Azure Event Hubs Protocol, available from the IBM support website. You can learn more about the integration with Azure. |
| ArcSight | The ArcSight Azure Event Hubs smart connector is available as part of the ArcSight smart connector collection. |   |

### Integration roadmap

Today, Azure Monitor’s SIEM integration capabilities can’t do everything the Azure Log Integration tool could do. Below is our roadmap for addressing known gaps between what you could accomplish with Azure Log Integration and what you can accomplish with Azure Monitor.

**Entra logs** – Entra logs are the only log type directly integrated with AzLog that aren’t yet available in Azure Monitor.

**Integrate Azure VM logs** – AzLog provided the option to integrate your Azure VM guest operating system logs (e.g., Windows Security Events) with select SIEMs. Azure Monitor has agents available for Linux and Windows that are capable of routing OS logs to an Azure Event Hubs, but end-to-end integration with SIEMs is nontrivial.

**End-to-end setup** – AzLog has a script that automates the end-to-end setup of log sources. Azure Monitor already offers the ability to script out creation of diagnostic settings. On top of that, we’re partnering with the Azure Policy team to deliver seamless enablement via Resource Manager policies, which ensure log data is routed from all sources.

**Integration with other SIEM tools** – AzLog provided a generic capability to push standardized Azure logs in JSON format to disk. While other SIEM tools weren’t officially supported by AzLog, this offered a way to easily get log data into tools such as LogRhythm. Our recommendation for customers using AzLog for these tools is to work with the producer of that tool to provide an Azure Monitor Event Hubs integration.

The security of your Azure environment is always top priority on the Azure team, both in how we engineer the Azure platform and in the capabilities we provide for you to secure your own assets on it. Moving SIEM integration to Azure Monitor is a step towards enabling you to manageably secure your applications on Azure at scale.


## Analyze Entra workbooks and reporting

With the usage and insights report, you can get an application-centric view of your sign-in data. You can find answers to the following questions:

- What are the most used applications in my organization?
- What applications have the most failed sign-ins?
- What are the top sign-in errors for each application?

### Prerequisites

To access the data from the usage and insights report, you need:

- An Entra tenant.
- An Entra ID P1 or P2 license.
- A user in the Security Administrator, Security Reader or Report Reader roles.

In addition, any user (non-admins) can access their own sign-ins.

### Access the usage and insights report

1. Navigate to the Azure portal.
2. Select the right directory, then select **Entra ID** and choose **Enterprise applications**.
3. From the **Activity** section, select **Usage and insights** to open the report.

### Use the report

The usage and insights report lists the applications with one or more sign-in attempts. You can sort it by the number of successful sign-ins, failed sign-ins, and the success rate.

Clicking **load more** at the bottom of the list allows you to view additional applications on the page. You can select the date range to view all applications that have been used within the range.

You can also set the focus on a specific application. Select **view sign-in activity** to see the sign-in activity over time for the application, as well as the top errors.

When you select a day in the application usage graph, you get a detailed list of the sign-in activities for the application.

## Monitor security posture with Identity Secure Score

The identity secure score is percentage that functions as an indicator for how aligned you are with Microsoft's best practice recommendations for security. Each improvement action in identity secure score is tailored to your specific configuration.

The score helps you to:

- Objectively measure your identity security posture
- Plan identity security improvements
- Review the success of your improvements

You can access the score and related information on the identity secure score dashboard. On this dashboard, you find:

- The secure score for your identity
- A comparison graph showing how your Identity secure score compares to other tenants in the same industry and similar size
- A trend graph showing any change to the secure score for your Identity over time
- A list of possible improvements

By following the improvement actions, you can:

- Improve your security posture and your score
- Take advantage the features available to your organization as part of your identity investments

### How do I get my secure score?

The identity secure score is available in all editions of Entra ID. Organizations can access their identity secure score, with the following steps:

1. Azure portal.
2. Entra ID.
3. Security.
4. Identity Secure Score.

### How are controls scored?

Controls can be scored in two ways. Some are scored in a binary fashion - you get 100% of the score if you have the feature or setting configured based on our recommendation. Other scores are calculated as a percentage of the total configuration. For example, an improvement recommendation might state you’ll get a maximum of 10.71% if you protect all your users with MFA. If only 5 of your 100 total users are protected, you would be given a partial score around 0.53% (5 protected / 100 total * 10.71% maximum = 0.53% partial score).

### How should I interpret my score?

Your score improves for configuring recommended security features or performing security-related tasks (like reading reports). Some actions are scored for partial completion, like enabling multifactor authentication (MFA) for your users. Your secure score is directly representative of the Microsoft security services you use. Remember that security must be balanced with usability. All security controls have a user affect component. Controls with low user lock-down should have little to no effect on your users' day-to-day operations.


## Module assessment

Choose the best response for each of the questions below.

### Check your knowledge


## Summary and resources

Once you implemented an identity solution in Azure, you have to monitor it. There are several tools from Microsoft Sentinel to log files to support your organization in this process.

Now that you reviewed this module, you're able to:

- Analyze and investigate sign-in logs to troubleshoot access issues.
- Review and monitor Entra audit logs.
- Enable and integrate Entra diagnostic logs with Log Analytics / Microsoft Sentinel.
- Export sign-in and audit logs to a third-party SIEM tool.
- Review Entra activity by using Log Analytics / Microsoft Sentinel, excluding KQL use.
- Analyze Entra workbooks/reporting.
- Monitor security posture with identity secure score.
- Configure notifications.

In this module, you learned how to monitor and maintain your Entra ID through analyzing logs of all types.

To go deeper, have a look at these articles:

- [What is Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/overview)
- [Microsoft Sentinel data connectors](https://learn.microsoft.com/en-us/azure/sentinel/connect-data-sources)
- [Kusto Query Language in Microsoft Sentinel](https://learn.microsoft.com/en-us/kusto/query)
- [Identity secure score in Entra ID](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-identity-secure-score)
