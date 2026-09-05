# Implement an identity management solution using Microsoft Entra ID

> SC-300 — learning path 1/4
> https://learn.microsoft.com/en-us/training/paths/implement-identity-management-solution/

## Modules

- **Implement initial configuration of Microsoft Entra ID** (11 units)
- **Create, configure, and manage identities** (14 units)
- **Implement and manage external identities** (16 units)
- **Implement and manage hybrid identity** (11 units)


---

# Implement initial configuration of Microsoft Entra ID

_https://learn.microsoft.com/en-us/training/modules/implement-initial-configuration-of-azure-active-directory/_


## Introduction

In this module, you learn how to configure and manage a Microsoft Entra tenant. You explore Microsoft Entra roles, custom domains, and company branding options. In addition, you learn how to configure delegation by using administrative units and configure several tenant-wide settings within Microsoft Entra ID.

### Learning objectives

In this module, you will:

- Configure company branding.
- Configure and manage Microsoft Entra roles.
- Configure delegation by using administrative units.
- Configure and manage custom domains.
- Evaluate permissions based on role assignments and settings.
- Configure tenant-wide settings.

### Prerequisites

Prior usage experience with the Azure portal user interface or the Microsoft Entra admin center.


## Configure company brand

You can use your organization's logo and custom color schemes to provide a consistent experience on your sign-in pages. Your sign-in pages appear when users sign in to your organization's web-based apps, such as Microsoft 365, which uses Microsoft Entra ID as your identity provider. Adding custom branding requires you to have either **Microsoft Entra ID premium P1, P2, or Office 365 (for Office 365 apps)** license.

To set the company branding, open up the Microsoft Entra ID page in the Azure portal. Then launch **Company branding** from the Manage menu. A premium license is required for the menu option to be present.

| **Setting** | **Description** |
|---|---|
| Language | The language is automatically set as your default and can't be changed. |
| Sign-in page background image | Select a .png or .jpg image file for the background of your sign-in pages. The image is anchored to the center of the browser, and scales to the size of the viewable space. You can't select an image larger than 1920x1080 pixels in size or that has a file size more than 300,000 bytes. |
| Banner logo | Select a .png or .jpg version of your logo to appear on the sign-in page after the user enters a username and on the My Apps portal page. |
| Username hint | Type the hint text that appears to users if they forget their username. This text must be Unicode, without links or code, and can't exceed 64 characters. If guests sign in to your app, we suggest not adding this hint. |
| Sign-in page text and formatting | Type the text that appears on the bottom of the sign-in page. You can use this text to communicate additional information, such as the phone number to your help desk or a legal statement. This text must be Unicode and not exceed 1,024 characters. |


## Configure and manage Microsoft Entra roles

Microsoft Entra ID is Microsoft’s cloud-based identity and access management service, which helps your employee's sign-in and access resources in:

- External resources, such as Microsoft 365, the Azure portal, and thousands of other SaaS applications.
- Internal resources, such as apps on your corporate network and intranet, along with any cloud apps developed by your own organization.

### Who uses Microsoft Entra ID?

Microsoft Entra ID is intended for:

- **IT admins** - As an IT admin, you can use Microsoft Entra ID to control access to your apps and your app resources, based on your business requirements. For example, you can use Microsoft Entra ID to require multifactor authentication when accessing important organizational resources. Additionally, you can use Microsoft Entra ID to automate user provisioning between your existing Windows Server AD and your cloud apps, including Microsoft 365. Finally, Microsoft Entra ID gives you powerful tools to automatically help protect user identities and credentials and to meet your access governance requirements.
- **App developers** - As an app developer, you can use Microsoft Entra ID as a standards-based approach for adding single sign-on (SSO) to your app, allowing it to work with a user's preexisting credentials. Microsoft Entra ID also provides APIs that can help you build personalized app experiences using existing organizational data.
- **Microsoft 365, Office 365, Azure, or Dynamics CRM Online subscribers** - As a subscriber, you're already using Microsoft Entra ID. Each Microsoft 365, Office 365, Azure, and Dynamics CRM Online tenant is automatically a Microsoft Entra tenant. You can immediately start to manage access to your integrated cloud apps.

In Microsoft Entra ID, if one of your users needs permission to manage Microsoft Entra resources, you must assign them to a role that provides the permissions they need.

If you're new to Azure, you might find it a little challenging to understand all the different roles in Azure. The following section helps explain the following roles and provides additional information on Azure roles and Microsoft Entra roles:

- Classic subscription administrator roles
- Azure roles
- Microsoft Entra roles

### Microsoft Entra roles

Microsoft Entra roles are used to manage Microsoft Entra resources in a directory. Actions such as create or edit users are the most common. However, the need to assign administrative roles to others, reset user passwords, manage user licenses, and manage domains are common. The following table describes a few of the more important Microsoft Entra roles.

| **Microsoft Entra role** | **Permissions** | **Notes** |
|---|---|---|
| Global Administrator | Manage access to all administrative features in Microsoft Entra ID, and services that federate to Microsoft Entra ID | The person who signs up for the Microsoft Entra tenant becomes the first Global Administrator. |
|   | Assign administrator roles to others |   |
|   | Reset the password for any user and all other administrators |   |
| User Administrator | Create and manage all aspects of users and groups |   |
|   | Manage support tickets |   |
|   | Monitor service health |   |
|   | Change passwords for users, Helpdesk administrators, and other User Administrators |   |
| Billing Administrator | Make purchases |   |
|   | Manage subscriptions |   |
|   | Manage support tickets |   |
|   | Monitors service health |   |

In the Azure portal, you can see the list of Microsoft Entra roles on the **Roles and administrators** screen.

### Differences between Azure roles and Microsoft Entra roles

At a high level, Azure roles control permissions to manage Azure resources, while Microsoft Entra roles control permissions to manage Microsoft Entra resources. The following table compares some of the differences.

| **Azure roles** | **Microsoft Entra roles** |
|---|---|
| Manage access to Azure resources | Manage access to Microsoft Entra resources |
| Supports custom roles | Supports custom roles |
| Scope can be specified at multiple levels (management group, subscription, resource group, resource) | Scope is at the tenant level or can be applied to an Administrative Unit |
| Role information can be accessed in Azure portal, Azure CLI, Azure PowerShell, Azure Resource Manager templates, REST API | Role information can be accessed in Azure admin portal, Microsoft 365 admin center, Microsoft Graph, and PowerShell |

#### Do Azure roles and Microsoft Entra roles overlap?

By default, Azure roles and Microsoft Entra roles don't span Azure and Microsoft Entra ID. However, if a Global Administrator elevates their access by choosing the **Access management for Azure resources** switch in the Azure portal, they're granted the User Access Administrator role (an Azure role) on all subscriptions for a particular tenant. The User Access Administrator role enables the user to grant other users access to Azure resources. This switch can be helpful to regain access to a subscription.

Several Microsoft Entra roles span Microsoft Entra ID and Microsoft 365, such as the Global and User Administrator roles. For example, if you're assigned the Global Administrator role, you have administrator capabilities in Microsoft Entra ID and Microsoft 365, such as making changes to Microsoft Exchange and Microsoft SharePoint. However, by default, the Global Administrator doesn't have access to Azure resources.

Note

Microsoft doesn't recommend the use of the Global Administrator role. It's recommended that you follow the principle of least privilege when performing administrative tasks.

![Diagram of relationship of Azure roles to Microsoft Entra roles. Azure roles accessed in Azure tenant.  Microsoft Entra roles also accessed from Microsoft Entra ID and Microsoft 365.](https://learn.microsoft.com../../wwl-sci/implement-initial-configuration-of-azure-active-directory/media/azure-office-roles.png)

### Assign roles

There are multiple ways to assign roles within Microsoft Entra ID. You need to pick the one that best meets your needs. The user interface might be slightly different for each method, however the configuration options are similar. Methods for assigning roles include:

- Assign a role to a user or group
  - **Microsoft Entra ID** - **Roles and administration** - **Select a role** - **+ Add Assignment**

- Assign a user or group to a role
  - **Microsoft Entra ID** - Open **Users** (or Groups) - Select an **User** (or group) - **Assigned roles** - **+ Add Assignment**

- Assign a role to a broad-scope, like a Subscription, Resource Group, or Management Group
  - Done via the **Access control (IAM)** within each settings screen

- Assign a role using PowerShell or Microsoft Graph API
- Assign a role using Privileged Identity Management (PIM)

The best method for your configuration needs can be used, but care must be taken as there are no built in restrictions. You could accidentally assign an administrative role to a group with users who don't need administrative access. Extra permissions could lead to a solution modified by a user without proper knowledge of what they're doing, or even a potential avenue for attackers. Proper identity governance is the key.

#### Example - using PIM to assign a role

A common way to assign Microsoft Entra roles to a user is on the Assigned roles page for a user. You can also configure the user eligibility to be elevated just-in-time into a role using **Privileged Identity Management (PIM)**.

Note

If you have a Microsoft Entra ID Premium P2 license plan and already use PIM, all role management tasks are performed in the Privileged Identity Management experience. This feature is currently limited to assigning only one role at a time. You can't currently select multiple roles and assign them to a user all at once.

### Create and assign a custom role in Microsoft Entra ID

This section describes how to create new custom roles in Microsoft Entra ID. For the basics of custom roles, see the [custom roles overview](https://learn.microsoft.com/en-us/azure/active-directory/roles/custom-overview). The role can be assigned either at the directory-level scope or an app registration resource scope only.

Custom roles can be created in the [Roles and administrators](https://portal.azure.com/) tab on the Microsoft Entra ID overview page.

1. Select **Microsoft Entra ID** - **Roles and administrators** - **New custom role**.
2. On the **Basics** tab, provide a name and description for the role and then select **Next**.
3. On the **Permissions** tab, select the permissions necessary to manage basic properties and credential properties of app registrations.
4. First, enter "credentials" in the search bar and select the `microsoft.directory/applications/credentials/update` permission.
5. Next, enter "basic" in the search bar, select the `microsoft.directory/applications/basic/update` permission, and then select **Next**.
6. On the **Review + create** tab, review the permissions and select **Create**.

Your custom role shows up in the list of available roles to assign.


## Exercise manage users roles

You need to assign extra permissions to one of your newly created administrators. In this exercise, you'll create a user account to use in the exercises.

### Create an Azure account and add Microsoft Entra ID Premium P2 trial licenses

The tasks in this exercise and the exercises in this learning path require you to already have an Azure subscription that you can use or to sign up for an Azure trial account. If you already have your own Azure subscription, you might skip this task and continue to the next.

1. In a web browser, go to [Azure portal](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
2. Scroll down through the page to learn more about the benefits and free services available.
3. Select **Start free**.
4. Use the wizard to sign up for your Azure trial subscription.
5. You need to a Microsoft Entra ID P2 license to complete some of the exercises. In the organization you created, search for and then select Microsoft Entra ID.
6. Select **Licenses** in the menu.
7. In the right **Quick tasks** menu of the Licenses - Overview page, select **Get a free trial**
8. Under Getting started with Microsoft Entra ID, select **Get a free trial for Microsoft Entra ID Premium**.
9. In the Activate pane, under Microsoft Entra ID **PREMIUM P2**, select **Free trial** and then select **Activate**.
10. In the navigation menu on the left, select **Overview**.
11. Refresh the browser until you see Microsoft Entra ID Premium P2 under the organization name. It might take a couple of minutes.
12. You might need to sign out and sign back into Microsoft Azure if you encounter any problems with expected features not being available.

### Add a new user

Now, let's create a user account.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/) as a Global administrator
2. In the menu on the left expand the **Identity** section.
3. In the left navigation menu, under **Users**, select **All Users**, then select +**New User**.
4. Create a user using the following information:    **Setting** **Value**     User principal name AdeleV   Mail nickname (you might have to uncheck the *Derive from user principal name*. AdeleV   Display name Adele Vance   Password Pass@word1
5. Select **Create**. The user is now created and registered to your organization.

### Assign a role to a user

Using Microsoft Entra ID, you can designate limited administrators to manage identity tasks in less-privileged roles. Administrators can be assigned for such purposes as adding or changing users, assigning administrative roles, resetting user passwords, managing user licenses, and managing domain names.

1. In Microsoft Entra ID, All users screen, select **Adele Vance**.
2. On the **user’s profile** page, select **Assigned roles**. The **Assigned roles** page appears.
3. Select **Add assignments**, select the role to assign to the user (for example, *Application administrator*), and then select **Add**.
4. Select **+ Add Assignment.**

The newly assigned Application administrator role appears on the user’s **Assigned roles** page.

### Remove a role assignment

If you need to remove the role assignment from a user, you can also do that from the **Assigned roles** page.

#### To remove a role assignment from a user

1. In Microsoft Entra ID, select **Users - All User**, and then select the user getting the role assignment removed. For example, *Adele Vance*.
2. Select **Assigned roles**, then select the name of the role your wish to removed - `Application Administrator`.
3. On the far right side of the screen, select **Remove**. Then select **Yes** option when prompted for confirmation.

The Application administrator role is removed from the user and it no longer appears on the **Adele Vance – Assigned roles** page.


## Configure delegation by using administrative units

Administrative units are Microsoft Entra ID resources that can be containers for other Microsoft Entra resources. An administrative unit can contain only users, groups, and devices.

Administrative units restrict permissions in a role to any portion of your organization that you define. You could, for example, use administrative units to delegate the Helpdesk Administrator role to regional support specialists, so they can manage users only in the region that they support. You can manage administrative units by using the Azure portal, PowerShell cmdlets and scripts, or Microsoft Graph.

#### What is an administrative unit?

In Microsoft Entra ID, using a single tenant if you assign a user any administrator role, they're now an admin over every user in the tenant. Always think about the security principle of least privilege, it's always the best way to grant administrative responsibilities. Administrative units are containers created to solve for this challenge in Microsoft Entra ID. If you want a User Administrator to be able to manage only a specific set of users and group. Say to only manage users in the Research Department of a hospital. You could set up an administrative unit. Within that administrative unit you would add the users and groups for the research team, then you would add a specific user to the User Administrator role within the administrative unit, call them Admin-for-research. Admin-for-research would be able to manage the users in the administrative unit but not across the entire tenant, which helps to achieve the principle of least privilege.

#### What admin roles are available for an administrative unit?

You can have users in the following roles to manage your administrative unit:

- Authentication administrator
- Helpdesk administrator
- License administrator
- Password administrator
- User administrator

Note

If you're familiar with on-premises Active Directory, this capability was handled by setting up Organizational Units (OUs) in your directory and adding your users to the OU.

### Plan your administrative units

You can use administrative units to logically group Microsoft Entra resources. An organization whose IT department is scattered globally might create administrative units that define relevant geographical boundaries. In another scenario, where a global organization has suborganizations that are semi-autonomous in their operations, administrative units could represent the suborganizations.

The administrative units creation criteria are guided by the unique requirements of an organization. Administrative units are a common way to define structure across Microsoft 365 services. We recommend that you prepare your administrative units with their use across Microsoft 365 services in mind. You can get maximum value out of administrative units when you can associate common resources across Microsoft 365 under an administrative unit.

You can expect the creation of administrative units in the organization to go through the following stages:

1. **Initial adoption**: Your organization will start creating administrative units based on initial criteria, and the number of administrative units will increase as the criteria are refined.
2. **Pruning**: After the criteria are defined, administrative units that are no longer required will be deleted.
3. **Stabilization**: Your organizational structure is defined, and the number of administrative units isn't going to change significantly in the short term.

### Delegate administration in Microsoft Entra ID

With organizational growth comes complexity. One common response is to reduce some of the workload of access management with Microsoft Entra admin roles. You can assign the least possible privilege to users to access their apps and perform their tasks. There are many reasons for an organization move toward a more decentralized administration.

In Microsoft Entra ID, you can delegate Application creation and management permissions in the following ways:

- Restricting who can create applications and manage the applications they create. By default in Microsoft Entra ID, all users can register application registrations and manage all aspects of applications they create. You can restrict to only allow selected people that permission.
- Assigning one or more owners to an application. A simple way to grant someone the ability to manage all aspects of Microsoft Entra ID configuration for a specific application.
- Assigning a built-in administrative role that grants access to manage configuration in Microsoft Entra ID for all applications. The recommended way to grant IT experts access to manage broad application configuration permissions without granting access to manage other parts of Microsoft Entra ID not related to application configuration.
- Create a custom role to define specific permissions. Then assign the role to a user to assign a limited-owner. Or you could assign at the directory scope - all applications - as a limited-administrator.

When granting access, use one of the above methods for two reasons. First, delegating the ability to perform administrative tasks reduces administrative overhead. Second, using limited permissions improves your security posture and reduces the potential for unauthorized access.

### Plan for Delegation

It's work to develop a delegation model that fits your needs. Developing a delegation model is an iterative design process, and we suggest you follow these steps:

- Define the roles you need
- Delegate app administration
- Grant the ability to register applications
- Delegate app ownership
- Develop a security plan
- Establish emergency accounts
- Secure your administrator roles
- Make privileged elevation temporary

### Define roles

Determine the directory tasks carried out by administrators and how they map to roles. Each task should be evaluated for frequency, importance, and difficulty. These criteria are vital aspects of task definition because they govern whether a permission should be delegated:

- Tasks that you do routinely, have limited risk, and are trivial to complete are excellent candidates for delegation.
- Tasks that you do rarely but have potential risk across the organization and require high skill levels should be considered carefully before delegating. Instead, you can temporarily elevate an account to the required role or reassign the task.

### Delegate app administration

The proliferation of apps within your organization can strain your delegation model. If it places the burden for application access management on the Global Administrator, it's likely that model increases its overhead as time goes on. If you granted people the Global Administrator role for things like configuring enterprise applications, you can now offload them to the following less-privileged roles. Doing so helps to improve your security posture and reduces the potential for unfortunate mistakes. The most-privileged application administrator roles are:

- The **Application Administrator** role, which grants the ability to manage all applications in the directory, including registrations, single sign-on settings, user and group assignments and licensing, Application Proxy settings, and consent. It doesn't grant the ability to manage Conditional Access.
- The **Cloud Application Administrator** role, which grants all the abilities of the Application Administrator, except it doesn't grant access to Application Proxy settings (because it has no on-premises permission).

### Delegate app registration

By default, all users can create application registrations. To selectively grant the ability to create application registrations:

- Set **Users can register applications** to No in **User settings**
- Assign the user to the Application Developer role

To selectively grant the ability to consent to allow an application to access data:

- Set **Users can consent to applications accessing company data on their behalf** To No in **User settings** under Enterprise apps
- Assign the user to the Application Developer role

When an Application Developer creates a new application registration, they're automatically added as the first owner.

### Delegate app ownership

For even finer-grained app access delegation, you can assign ownership to individual enterprise applications. You improve existing support for assigning application registration owners. Ownership is assigned on a per-enterprise application basis in the Enterprise Applications screen. The benefit is owners can manage only the enterprise applications they own. For example, you can assign an owner for the Salesforce application, and that owner can manage access to and configuration for Salesforce, and no other applications. An enterprise application can have many owners, and a user can be the owner for many enterprise applications. There are two app owner roles:

- The **Enterprise Application Owner** role grants the ability to manage the ‘enterprise applications that the user owns, including single sign-on settings, user and group assignments, and adding more owners. It doesn't grant the ability to manage Application Proxy settings or Conditional Access.
- The **Application Registration Owner** role grants the ability to manage application registrations for app that the user owns, including the application manifest and adding other owners.

### Develop a security plan

Microsoft Entra ID provides an extensive guide to planning and executing a security plan on your Microsoft Entra admin roles, [Securing privileged access for hybrid and cloud deployments](https://learn.microsoft.com/en-us/azure/active-directory/roles/security-planning).

### Establish emergency accounts

To maintain access to your identity management store when issue arises, prepare emergency access accounts according to [Create emergency-access administrative accounts](https://learn.microsoft.com/en-us/azure/active-directory/roles/security-emergency-access).

### Secure your administrator roles

Attackers who get control of privileged accounts can do tremendous damage. Always protect these accounts first. Use the Security Defaults feature that is available to all Microsoft Entra organizations. Security Defaults enforces multifactor authentication on privileged Microsoft Entra accounts.


## Analyze Microsoft Entra role permissions

What is a permission? The dictionary definition of permission is the **consent or authorization to perform a specific action**. In Microsoft Entra ID, you have permissions for each of the operations you're able to do. Permission can range from viewing your settings, to be able to change your setting. Then move on to granting permission to add or remove users and beyond. There are two primary places where permission can be assigned, at a user or group level. However, they all pass down to the user at the final point. When dealing with users, you have both a member-user and a guest-user. The default permissions for the guest-user are slightly less than the member.

#### Sample of the default permissions for users

| **Member Users** | **Guest Users** |
|---|---|
| Enumerate list of users and their contacts | Read own properties |
| Invite guest users | Invite guest users |
| Can create Security and Microsoft 365 Groups | Can search for non-hidden groups by name |
| Register new applications | Read properties of registered and enterprise applications |

Note

This is just a small subset, to show differences. If you want a full list of the [Default User Permissions](https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/users-default-permissions)

#### Controlling permissions - add and restrict

You can use the **User Settings** inside of Microsoft Entra ID – Manage menu to restrict or control the default permissions of the default users. Or you can use Roles and administrators to add new permissions onto your users and group. Always use the concept of Least Privilege and make sure the users only have the rights they need. In User settings you can restrict the user's ability to:

- Register applications
- Access the Azure portal
- Block LinkedIn connections
- Manage settings for external collaboration

By adding roles to a given user account or group, you can add permissions on to member users, guest users, and service principals. Adding roles gives permissions to perform specific activities. Actions are limited, which allows the rule of least privilege.

#### Exploring available permissions

If possible, you only want to grant the minimum permissions a user needs. So be sure to know what all permissions are granted when you assign a role. You can see the list of permissions in the description of each role. To open, launch Microsoft Entra ID, then open the **Roles and administrators** screen. Next select a role, and open its description page from the ellipsis (...) menu. Depending on the role you chose, you'll see a large or small number of permissions. Two sets of permissions:

- Role permissions
- Guest and service principal basic read permissions


## Configure and manage custom domains

A domain name is a part of the identifier for many Microsoft Entra ID resources: it's part of a user name or email address for a user, part of the address for a group, and is sometimes part of the app ID URI for an application. A resource in Microsoft Entra ID can include a domain name that's owned by the organization that contains the resource. Only a Global Administrator can manage domains in Microsoft Entra ID.

### Set the primary domain name for your Microsoft Entra organization

When your organization is created, the initial domain name, such as ‘contoso.onmicrosoft.com,’ is also the primary domain name.

Important

The person who creates the tenant is automatically the Global administrator for that tenant. The Global administrator can add other administrators to the tenant. When adding new administrators, always use the principle of least privilege.

The primary domain is the default domain name for a new user when you create a new user. Setting a primary domain name streamlines the process for an administrator to create new users in the portal. To change the primary domain name:

1. Sign in to the [Azure portal](https://portal.azure.com/) with an account that's an Administrator for the organization.
2. Select **Microsoft Entra ID.**
3. Select **Custom domain names**.
4. Select the name of the domain that you want to be the primary domain.
5. Select the **Make primary** command. Confirm your choice when prompted.

You can change the primary domain name for your organization to be any verified custom domain that isn't federated. Changing the primary domain for your organization won't change the user name for any existing users.

### Add custom domain names to your Microsoft Entra organization

You can add up to 900 managed domain names. If you're configuring all your domains for federation with on-premises Active Directory, you can add up to 450 domain names in each organization.

### Add subdomains of a custom domain

If you want to add a subdomain name such as ‘europe.contoso.com’ to your organization, you should first add and verify the root domain, such as contoso.com. The subdomain is automatically verified by Microsoft Entra ID. To see the verified subdomain you added, refresh the domain list in the browser.

If you've already added a contoso.com domain to one Microsoft Entra organization, you can also verify the subdomain europe.contoso.com in a different Microsoft Entra organization. When adding the subdomain, you're prompted to add a TXT record in the DNS hosting provider.

### What to do if you change the DNS registrar for your custom domain name

If you change the DNS registrars, there are no additional configuration tasks in Microsoft Entra ID. You can continue using the domain name with Microsoft Entra ID without interruption. If you use your custom domain name with Microsoft 365, Intune, or other services that rely on custom domain names in Microsoft Entra ID, see the documentation for those services.

### Delete a custom domain name

You can delete a custom domain name from your Microsoft Entra ID if your organization no longer uses that domain name, or if you need to use that domain name with another Microsoft Entra ID.

To delete a custom domain name, you must first ensure that no resources in your organization rely on the domain name. You can't delete a domain name from your organization if:

- Any user has a user name, email address, or proxy address that includes the domain name.
- Any group has an email address or proxy address that includes the domain name.
- Any application in your Microsoft Entra ID has an app ID URI that includes the domain name.

You must change or delete any such resource in your Microsoft Entra organization before you can delete the custom domain name.

#### ForceDelete option

**ForceDelete** can be used to remove a domain name in the Microsoft Entra admin center or using Microsoft Graph API. These options use an asynchronous operation and update all references from the custom domain name like “user@contoso.com” to the initial default domain name such as “user@contoso.onmicrosoft.com.”

To call **ForceDelete** in the Azure portal, you must ensure that there are fewer than 1000 references to the domain name, and any references where Exchange is the provisioning service must be updated or removed in the Exchange Admin Center. Exchange Mail-Enabled Security Groups and distributed lists are included. Also, the **ForceDelete** operation won't succeed if either of the following is true:

- You purchased a domain via Microsoft 365 domain subscription services
- You're a partner administering on behalf of another customer organization

The following actions are performed as part of the **ForceDelete** operation:

- Renames the UPN, EmailAddress, and ProxyAddress of users with references to the custom domain name to the initial default domain name.
- Renames the EmailAddress of groups with references to the custom domain name to the initial default domain name.
- Renames the identifierUris of applications with references to the custom domain name to the initial default domain name.

An error is returned when:

- The number of objects to be renamed is greater than 1000
- One of the applications to be renamed is a multitenant app


## Configure tenant-wide setting

Tenant-wide settings are the configuration options that apply to all resources within your tenant as the name implies. These tenant wide options are set in specific places, to control the look, feel, and configuration of your tenant and its members. The below menu options are based on the Microsoft Entra admin center.

Tenant-wide option

- **Tenant Properties**
  - Identity - Overview page - Properties
  - Where you give the name of your directory and set values like the primary contact

- **User Settings**
  - Identity - Users - User Settings
  - Where you define what global rights your users have, like registering applications

- **External Collaboration Settings**
  - Identity - External I - User Settings - Manage external collaboration
  - Where you define what task an external guest user can perform like inviting more guest users

### Configure tenant-wide user settings

In Microsoft Entra ID, all users are granted a set of default permissions. A user’s access consists of the type of user, their role assignments, and their ownership of individual objects. The default user permissions can be changed only in user settings in Microsoft Entra ID.

#### Member and guest users

The set of default permissions received depends on whether the user is a native member of the tenant (member user). Or if the user is invited from another directory as a B2B collaboration guest (guest user).

- Member users can register applications, manage their own profile photo and mobile phone number, change their own password, and invite B2B guests. In addition, users can read all directory information (with a few exceptions).
- Guest users have restricted directory permissions. They can manage their own profile, change their own password, and retrieve some information about other users, groups, and apps; however, they can't read all directory information. For example, guest users can't enumerate the list of all users, groups, and other directory objects. Guests can be added to administrator roles, which grant them full read and write permissions contained in the role. Guests can also invite other guests.

The following default permissions for member users can be restricted in the following ways:

| **Permission** | **Setting explanation** |
|---|---|
| Users can register application | By default, member users can register applications. |
|   | Setting this option to No prevents users from creating application registrations. The ability can then be granted back to specific individuals by adding them to the Application Developer role. |
| Restrict access to Microsoft Entra administration portal | Setting this option to No lets non-administrators use the Microsoft Entra administration portal to read and manage Microsoft Entra resources. Yes restricts all non-administrators from accessing any Microsoft Entra data in the administration portal. |
|   | This setting doesn't restrict access to Microsoft Entra data using PowerShell or other clients such as Visual Studio. When set to Yes, to grant a specific non-admin user the ability to use the Microsoft Entra administration portal assign any administrative role such as the Directory Readers role. |
|   | This role allows reading basic directory information, which member users have by default (guests and service principals don't). |

#### Sign in with LinkedIn

With more than 500 million members worldwide, LinkedIn is the largest and most trusted source of professional identities. Use this power to enhance the sign-in experience of your sites and applications.

Use sign in with LinkedIn to:

- Reduce friction and obtain more sign-ups by allowing members to Sign In with LinkedIn, without having the need to create a new account.
- Minimize the costs and time associated with implementing your own sign-in, identity, profile management, and password management.
- Personalize your sites and applications with the latest member profiles.

#### Manage security defaults

Managing security can be difficult with common identity-related attacks like password spray, replay, and phishing becoming more popular. Security defaults make it easier to help protect your organization from these attacks with preconfigured security settings:

- Requiring all users to register for multifactor authentication (MFA).
- Requiring administrators to perform multifactor authentication.
- Blocking legacy authentication protocols.
- Requiring users to perform multifactor authentication when necessary.
- Protecting privileged activities like access to the Azure portal.

#### Availability

Microsoft is making **Security Defaults** available to everyone. The goal is to ensure that all organizations have a basic level of security enabled at no extra cost.

### Configure the external user options

Here you configure the actions that external users can take while using the cloud resources of your tenant.

- **Guest user access** - Guest users can be given rights to where they operate almost as a full user, to restriction where they can only look at their own content.
- **Guest invite settings** - Who can invite guests to join the organization; from guest themselves to only admins.
- **Guest self-service up** - Allow guest to partake in self-service options for users.

### Configure tenant properties for the directory

Set the basic values that define the look at feel of your tenant within Microsoft Entra ID.

- **Name** - friendly name for your tenant, for use in the Azure portal
- **Country or region** - location of your primary company and the Azure datacenters being used
- **Notification language** - language used for sending notifications and alerts
- **Tenant ID** - unique identifier for your tenant, used programatically
- **Technical contact** - primary contact for the tenant (defaults to the user who created the tenant)
- **Global privacy contact** - user or alias to contact for privacy concerns or issues
- **Privacy statement URL** - link to a PDF or webpage containing the privacy rules for your cloud solutions


## Exercise - setting tenant-wide properties

Your goal is to change the tenant display name.

1. Browse to the [Azure portal](https://portal.azure.com/) and sign in using an Administrator account for the directory.
2. Select the **Show portal menu** hamburger icon and then select **Microsoft Entra ID**.
3. In the left navigation, in the Manage section, select **Properties**.
4. In the **Name** box, change the tenant name. For example, Contoso Marketing Company can be changed to Contoso Marketing Company 2.
5. Select **Save** to update the tenant properties.

#### Find the Country / region associated with your tenant

1. In the **Microsoft Entra ID** screen, in the Manage section, select **Properties**.
2. Under **Tenant properties**, locate **Country / region** and review the information.  Important When the tenant is created, the Country / region is specified at that time. This setting can't be changed later.

#### Find the location associated with your tenant

Just as the Country / region is found in the Microsoft Entra ID Properties dialog, so is the location information.

1. In the **Properties** screen, under **Tenant properties**, locate **Location** and review the information.

#### Find the tenant ID

Azure subscriptions have a trust relationship with Microsoft Entra ID. Microsoft Entra ID is trusted to authenticate users, services, and devices for the subscription. Each subscription has a tenant ID associated with it, and there are a few ways you can find the tenant ID for your subscription.

1. In the **Microsoft Entra ID** screen, in the Manage section, select **Properties**.
2. Under **Tenant properties**, locate **Tenant ID**. Tenant ID is your unique tenant identifier.

#### Change the Technical contact, add your privacy info, Global privacy contact, and Privacy statement URL

Microsoft strongly recommends you add both your global privacy contact and your organization's privacy statement, so your internal employees and external guests can review your policies. Because privacy statements are uniquely created and tailored for each business, we strongly recommend you contact a lawyer for assistance.

Note

For information about viewing or deleting personal data, see [Azure Data Subject Requests](https://learn.microsoft.com/en-us/microsoft-365/compliance/gdpr-dsr-azure). For more information, see the [Service Trust portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

You add your organization's privacy information in the **Properties** area of Microsoft Entra ID. To access the Properties area and add your privacy information:

1. In the **Microsoft Entra ID** screen, in the Manage section, select **Properties**.

1. Add your privacy info for your employees:

- **Technical contact**. Type the email address for the person to contact for technical support within your organization.
- **Global privacy contact**. Type the email address for the person to contact for inquiries about personal data privacy. This person is also who Microsoft contacts if there's a data breach. If there's no person listed here, Microsoft contacts the administrator who owns the tenant.
- **Privacy statement URL**. Type the link to your organization's document that describes how your organization handles both internal and external guest's data privacy.

1. Select **Save**.


## Knowledge check

Choose the best response for each of the questions below.

### Check your knowledge


## Summary and resources

Now that you reviewed this module, you're able to:

- Configure and manage Microsoft Entra roles.
- Configure and manage custom domains.
- Evaluate permissions based on role assignments and settings.
- Configure delegation by using administrative units.
- Configure tenant-wide settings.

### Resources

Use these resources to discover more.

- Information about which roles manage Azure resources and which roles manage Microsoft Entra resources is available at [Classic subscription administrator roles, Azure roles, and Microsoft Entra roles](https://learn.microsoft.com/en-us/azure/role-based-access-control/rbac-and-directory-admin-roles).
- For more information about roles, see [Understand Azure role definitions](https://learn.microsoft.com/en-us/azure/role-based-access-control/role-definitions).
- For information about how to use PIM, see [Privileged Identity Management](https://learn.microsoft.com/en-us/azure/active-directory/privileged-identity-management/).
- The following step-by-step guides provide information on how you can use Conditional Access to configure equivalent policies to those policies enabled by security defaults:
  - [Require MFA for administrators](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa)
  - [Require MFA for Azure management](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/howto-conditional-access-policy-azure-management)
  - [Block legacy authentication](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)
  - [Require MFA for all users](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa)
  - [Require MFA registration](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/howto-identity-protection-configure-mfa-policy) - Requires Microsoft Entra Identity Protection part of Microsoft Entra ID Premium P2.


---

# Create, configure, and manage identities

_https://learn.microsoft.com/en-us/training/modules/create-configure-manage-identities/_


## Introduction

Transitioning workloads to the cloud involves more than just moving servers, websites, and data. Companies need to think about how to secure those resources by defining authorized users. Next, companies need to ensure that users only have access to data that they need, that user authorization is limited only to the services available to them, and that users only perform operations authorized for them to perform. Access to cloud-based workloads is controlled centrally in two ways. First by providing a definitive identity for each user that they use for every service. Second by ensuring employees and vendors have enough access to do their jobs.

Microsoft Entra ID, the Microsoft cloud-based identity and access management service, helps make these challenges easier to solve. Microsoft Entra ID provides end-to-end identity management, including single sign-on and multifactor authentication to help protect your users and your data. In this module, you learn the basics of creating, configuring, and managing users and groups of users. You also learn to manage licenses and device registration.

### Learning objectives

In this module, you:

- Create, configure, and manage users
- Create, configure, and manage groups
- Manage licenses
- Configure and manage device registration
- Explore custom security attributes and automatic provisioning

### Prerequisites

- Basic understanding of identity management
- Some experience with Active Directory a plus
- Experience with Zero Trust helpful


## Create, configure, and manage users

Every user who needs access to resources needs a user account in Microsoft Entra ID. A user account contains all the information needed to authenticate the user during the sign-on process. Once authenticated, Microsoft Entra ID builds an access token to authorize the user and determine what resources they can access and what they can do with those resources.

You use the **Microsoft Entra admin center** to work with user objects. Keep in mind that you can only work with a single directory at a time. You can use the **Directory + Subscription** panel to switch directories. The admin center also has a **Switch directory** button in the toolbar, which makes it easy to switch to another available directory.

### View users

To view the Microsoft Entra users, select the **Users** entry under **Identity**, then open the **All Users** view. Take a minute to access the admin center and view your users. Notice the **User Type** column to see members and guests, as the following figure depicts.

Typically, Microsoft Entra ID defines users in three ways:

- **Cloud identities** - These users exist only in Microsoft Entra ID. Examples are administrator accounts and users that you manage yourself. Their source is **Microsoft Entra ID** or **External Microsoft Entra directory** if the user is defined in another Microsoft Entra instance but needs access to subscription resources controlled by this directory. When these accounts are removed from the primary directory, they're deleted.
- **Directory-synchronized identities** - These users exist in an on-premises Active Directory. A synchronization activity brings these users into Microsoft Entra ID. **Microsoft Entra Cloud Sync** is the recommended synchronization tool for most organizations—it uses a lightweight cloud-managed agent and supports multiple disconnected forests. **Microsoft Entra Connect Sync** remains available for complex scenarios such as device synchronization or groups with more than 50,000 members. Their source is **Windows Server AD**.
- **Guest users** - These users exist outside your organization. Examples are accounts from other cloud providers and Microsoft accounts. Their source is **Invited user**. This type of account is useful when external vendors or contractors need access to your organization's resources. Once their help is no longer necessary, you can remove the account and all of their access.


## Exercise - assign licenses to users

**Exercise environment needs** - this lab assumes you have a basic Microsoft Entra tenant with at least User Administrator rights to complete it. You can get a free trial subscription for at [Try Azure for Free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).

### Create a new user in Microsoft Entra ID

You can skip creating this user if you created the same user in the earlier module.

1. Browse to the Identity menu in the [Microsoft Entra admin center](https://entra.microsoft.com/).
2. In the left navigation, under select **Users**, then **All Users.**
3. Within the Users page, on the menu, select + **New user** and **Create new user**.
4. Create a user using the following information:    **Setting** **Value**     User principal name ChrisG   Name Chris Green   First name Chris   Last name Green   Password make up a unique password
5. When complete, verify the account for Chris Green is shown in the **All users** list.

### Create a security group in Microsoft Entra ID

1. Browse to the Microsoft Entra admin center screen.
2. In the left navigation, under **Identity**, select **Groups** and then **All groups**.
3. In the Groups screen, on the menu, select **New group**.
4. Create a group using the following information:    **Setting** **Value**     Group type Security   Group name Marketing   Membership type Assigned   Owners Assign your own administrator account as the group owner   Members Chris Green
5. When complete, verify the group named **Marketing** is shown in the **All groups** list.

### Assign a license to a group

License assignment to groups is managed through the Microsoft 365 admin center.

1. Go to the Microsoft 365 admin center at [https://admin.microsoft.com](https://admin.microsoft.com).
2. Select **Billing** from the menu on the left.
3. Select **Licenses**.
4. From the list of licenses you have available, select one.
5. Select **Groups** from the list near the top of the screen.
6. On the Groups page, select **+ Assign license**.
7. Search for and select the **Marketing** group you created earlier.
8. Select the **Assign** button at the bottom of the dialog.
9. You should get a message that licenses were successfully assigned.

### Restore or remove a recently deleted user with Microsoft Entra ID

After you delete a user, the account remains in a suspended state for 30 days. During that 30-day window, the user account can be restored, along with all its properties. After that 30-day window passes, the permanent deletion process is automatically started.

You can view your restorable users, restore a deleted user, or permanently delete a user using Microsoft Entra ID user interface.

Important

You can't restore a permanently deleted user.

### Required permissions

You must have one of the following roles to restore or permanently delete users.

- Global administrator
- Partner Tier-1 Support
- Partner Tier-2 Support
- User administrator


## Exercise - restore or remove deleted users

**Exercise environment needs** - this lab assumes you have a basic Microsoft Entra tenant with at least User Administrator rights to complete it. You can get a free trial subscription at [Try Microsoft Azure for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).

### Remove a user from Microsoft Entra ID

1. Browse to the [Microsoft Entra admin center](https://entra.microsoft.com/).
2. In the left navigation, under **Identity**, select **Users**.
3. In the **Users** list, select the check box for a user to delete. For example, select **Chris Green**.  Tip Selecting users from the list allows you to manage multiple users at the same time. If you select the user, to open that user’s page, you'll only be managing that individual user.
4. With the user account selected, on the menu, select **Delete user**.
5. Review the dialog box and then select **OK**.

### Restore a deleted user

You can see all the users that were deleted less than 30 days ago. These users can be restored.

1. In the Users page, in the left navigation, select **Deleted users**.
2. Review the list of deleted users and select the user you deleted.  Important By default, deleted user accounts are permanently removed from Microsoft Entra ID automatically after 30 days.
3. On the menu, select **Restore user**.
4. Review the dialog box and then select **OK**.
5. In the left navigation, select **All users**.
6. Verify the user was restored.


## Create, configure, and manage groups

A Microsoft Entra group helps organize users, which makes it easier to manage permissions. Using groups lets the resource owner (or Microsoft Entra directory owner), assign a set of access permissions to all the members of the group, instead of having to provide the rights one-by-one. Groups let you define a security boundary and then add and remove specific users to grant or deny access with a minimum amount of effort. Even better, Microsoft Entra ID supports the ability to define membership based on rules - such as what department a user works in, or the job title they have.

Microsoft Entra ID allows you to define two different types of groups.

- **Security groups** - the most common type of groups and are used to manage access to shared resources. Members of a security group can include users, devices, and service principals. For example, you can create a security group for a specific security policy. By doing it this way, you can give a set of permissions to all the members at once, instead of having to add permissions to each member individually. This option requires a Microsoft Entra administrator.
- **Microsoft 365 groups** - provide collaboration opportunities by giving members access to a shared mailbox, calendar, files, SharePoint site, and more. This option also lets you give people outside of your organization access to the group. This option is available to users and admins.

### View available groups

You can view all groups through the **Groups** item under **Identity** in the Microsoft Entra admin center. A new Microsoft Entra ID deployment has no groups defined.

The second characteristic of a group that you need to be aware of is the **Membership Type**. This specifies how individual members are added to the group. The three types are:

- **Assigned** - members are added and maintained manually.
- **Dynamic User** - users are added and removed automatically based on rules that evaluate user attributes such as department, job title, or location.
- **Dynamic Device** - devices are added and removed automatically based on rules that evaluate device attributes. Applies to security groups only; Microsoft 365 groups support dynamic users but not dynamic devices.

### Dynamic groups

With dynamic membership, Microsoft Entra ID automatically adds or removes users or devices from a group based on rules you define. When a member's attributes change—for example, a user moves to a different department—all dynamic membership rules in the tenant are reevaluated, and the user is added to or removed from groups accordingly.

Dynamic membership requires a **Microsoft Entra ID P1** license (or Intune for Education for device-based rules).

For example, you can create a rule that automatically adds all users whose **Department** attribute equals "Marketing" to a Marketing security group, keeping membership current without manual updates.


## Exercise - add groups in Microsoft Entra ID

**Exercise environment needs** - this lab assumes you have a basic Microsoft Entra tenant with at least User Administrator rights to complete it. You can get a free trial subscription at [Try Microsoft Azure for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).

### Create a Microsoft 365 group in Microsoft Entra ID

1. Browse to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. In the left navigation, under **Identity**, select **Groups**.
3. In the Groups page, on the menu, select **New group**.
4. Create a group using the following information:    **Setting** **Value**     Group type Microsoft 365   Group name Northwest Sales   Membership type Assigned   Owners Assign your own administrator account as the group owner   Members Assign a member of this group
5. When complete, verify the group named **Northwest sales** is shown in the **All groups** list.
6. You have to refresh the **All groups** a couple of times for the new group to show up.


## Configure and manage device registration

With the proliferation of devices of all shapes and sizes and the proliferation of bring-your-own-device (BYOD), IT professionals are faced with two somewhat opposing goals:

- Allow end users to be productive wherever and whenever and on any device
- Protect the organization's assets

To protect these assets, IT-staff needs to first manage the device identities. IT-staff can build on the device identity with tools like Microsoft Intune to ensure standards for security and compliance are met. Microsoft Entra ID enables single sign-on to devices, apps, and services from anywhere through these devices.

- Your users get access to your organization's assets they need.
- Your IT-staff gets the controls they need to secure your organization.

### Microsoft Entra registered devices

The goal of Microsoft Entra registered devices is to provide your users with support for the BYOD or mobile device scenarios. In these scenarios, a user can access your organization’s Microsoft Entra ID controlled resources using a personal device.

| **Microsoft Entra registered** | **Description** |
|---|---|
| Definition | Registered to Microsoft Entra ID without requiring organizational account to sign in to the device |
| Primary audience | Applicable to Bring your own device (BYOD), and Mobile devices |
| Device ownership | User or Organization |
| Operating systems | Windows 10 or newer, macOS 10.15 or newer, iOS 15 or newer, Android, Linux (Ubuntu 20.04/22.04/24.04 LTS, Red Hat Enterprise Linux 8/9 LTS) |
| Device sign in options | End-user local credentials, Password, Windows Hello, PIN, Biometrics |
| Device management | Mobile Device Management (example: Microsoft Intune), Mobile Application Management |
| Key capabilities | SSO to cloud resources, Conditional Access when enrolled in Intune, Conditional Access via App protection policy |

![Diagram of Microsoft Entra registered devices. Shows a laptop and cell registered.](https://learn.microsoft.com../../wwl-sci/create-configure-manage-identities/media/azure-active-directory-registered-device.png)

Microsoft Entra registered devices are signed in to using a local account like a Microsoft account on a Windows 10 or newer device, but additionally have a Microsoft Entra account attached for access to organizational resources. Access to resources in the organization can be further limited based on that Microsoft Entra account and Conditional Access policies applied to the device identity.

Administrators can secure and further control these Microsoft Entra registered devices using Mobile Device Management (MDM) tools like Microsoft Intune. MDM provides a means to enforce organization-required configurations like requiring storage to be encrypted, password complexity, and security software kept updated.

Microsoft Entra ID registration can be accomplished when accessing a work application for the first time or manually using the Windows 10 or Windows 11 Settings menu.

#### Scenarios for registered devices

A user in your organization wants to access tools for email, reporting time-off, and benefits enrollment from their home PC. Your organization has these tools behind a Conditional Access policy that requires access from an Intune compliant device. The user adds their organization account and registers their home PC with Microsoft Entra ID and the required Intune policies are enforced giving the user access to their resources.

Another user wants to access their organizational email on their personal Android phone infected by a root-kit. Your company requires a compliant device and created an Intune compliance policy to block any rooted devices. The employee is stopped from accessing organizational resources on this device.

### Microsoft Entra joined devices

Microsoft Entra joined is intended for organizations that want to be cloud-first or cloud-only. Any organization can deploy Microsoft Entra joined devices no matter the size or industry. Microsoft Entra joined enables access to both cloud and on-premises apps and resources.

| **Microsoft Entra joined** | **Description** |
|---|---|
| Definition | Joined only to Microsoft Entra ID requiring organizational account to sign in to the device |
| Primary audience | Suitable for both cloud-only and hybrid organizations |
| Device ownership | Organization |
| Operating systems | All Windows 10 and Windows 11 devices (except Home editions); Windows Server 2019 and newer VMs in Azure (Server Core not supported); macOS 13 or newer (preview) |
| Device management | Mobile Device Management (example: Microsoft Intune) |
| Key capabilities | SSO to both cloud and on-premises resources, Conditional Access, Self-service Password Reset and Windows Hello PIN reset |

Microsoft Entra joined devices are signed in to using an organizational Microsoft Entra account. Access to resources in the organization can be further limited based on that Microsoft Entra account and Conditional Access policies applied to the device identity.

Administrators can secure and further control Microsoft Entra joined devices using Mobile Device Management (MDM) tools like Microsoft Intune or in co-management scenarios using Microsoft Endpoint Configuration Manager. These tools provide a means to enforce organization-required configurations like requiring storage to be encrypted, password complexity, software installations, and software updates. Administrators can make organization applications available to Microsoft Entra joined devices using Configuration Manager.

Microsoft Entra joined can be accomplished using self-service options like the Out of Box Experience (OOBE), bulk enrollment, or Windows Autopilot.

Microsoft Entra joined devices can still maintain single sign-on access to on-premises resources when they are on the organization's network. Microsoft Entra joined devices authenticate to on-premises servers like for file, print, and other applications.

#### Scenarios for joined devices

Although Microsoft Entra joined is primarily intended for organizations that don't have an on-premises Windows Server Active Directory infrastructure, you can certainly use it in scenarios where:

- You want to transition to cloud-based infrastructure using Microsoft Entra ID and MDM like Intune.
- You can’t use an on-premises domain join, for example, if you need to get mobile devices such as tablets and phones under control.
- Your users primarily need to access Microsoft 365 or other SaaS apps integrated with Microsoft Entra ID.
- You want to manage a group of users in Microsoft Entra ID instead of in Active Directory. This scenario can apply, for example, to seasonal workers, contractors, or students.
- You want to provide joining capabilities to workers in remote branch offices with limited on-premises infrastructure.

You can configure Microsoft Entra joined devices for all Windows 10 and Windows 11 devices except for the Home editions.

The goal of Microsoft Entra joined devices is to simplify:

- Windows deployments of work-owned devices
- Access to organizational apps and resources from any Windows device
- Cloud-based management of work-owned devices
- Users to sign in to their devices with their Microsoft Entra ID or synced Active Directory work or school accounts.

![Diagram of Microsoft Entra joined devices connected to the cloud. A laptop registered to your cloud directory.](https://learn.microsoft.com../../wwl-sci/create-configure-manage-identities/media/azure-active-directory-joined-device.png)

Microsoft Entra Joined can be deployed by using many different methods.

### Hybrid Microsoft Entra joined devices

For more than a decade, many organizations have used the domain join to their on-premises Active Directory to enable:

- IT departments to manage work-owned devices from a central location.
- Users to sign in to their devices with their Active Directory work or school accounts.

Typically, organizations with an on-premises footprint rely on imaging methods to configure devices, and they often use **Configuration Manager** or **group policy (GP)** to manage them.

If your environment has an on-premises AD footprint and you also want benefit from the capabilities provided by Microsoft Entra ID, you can implement hybrid Microsoft Entra joined devices. These devices are devices that are joined to your on-premises Active Directory and registered with your Microsoft Entra directory.

| **Hybrid Microsoft Entra joined** | **Description** |
|---|---|
| Definition | Joined to on-premises AD and Microsoft Entra ID requiring organizational account to sign in to the device |
| Primary audience | Suitable for hybrid organizations with existing on-premises AD infrastructure |
| Device ownership | Organization |
| Operating systems | Windows 10, Windows 11 (except Home editions), Windows Server 2016, 2019, and 2022 |
| Device sign in options | Password or Windows Hello for Business |
| Device management | Group Policy, Configuration Manager standalone, or co-management with Microsoft Intune |
| Key capabilities | SSO to both cloud and on-premises resources, Conditional Access, Self-service Password Reset and Windows Hello PIN reset |

![Diagram of the process flow of Hybrid Microsoft Entra joined devices. A laptop is registered to an on-premises active directory.](https://learn.microsoft.com../../wwl-sci/create-configure-manage-identities/media/azure-active-directory-hybrid-joined-device.png)

#### Scenarios for hybrid joined

Use Microsoft Entra hybrid joined devices if:

- You have Win32 apps deployed to these devices that rely on Active Directory machine authentication.
- You want to continue to use Group Policy to manage device configuration.
- You want to continue to use existing imaging solutions to deploy and configure devices.

### Device writeback (no longer supported)

Device writeback is no longer supported and is no longer a recommended approach for hybrid identity scenarios. It is replaced by **Cloud Kerberos Trust**, which allows Microsoft Entra joined and hybrid joined devices to authenticate to on-premises resources without requiring device objects to be written back to on-premises Active Directory.

For organizations planning new hybrid deployments, use Cloud Kerberos Trust to enable on-premises SSO and Windows Hello for Business in hybrid environments. See [Configure Microsoft Entra Kerberos for on-premises single sign-on](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-authentication-passwordless-security-key-on-premises) for guidance.


## Manage licenses

Microsoft paid cloud services, such as Microsoft 365, Enterprise Mobility + Security, Dynamics 365, and other similar products, require licenses. These licenses are assigned to each user who needs access to these services. To manage licenses, administrators use the [Microsoft 365 admin center](https://admin.microsoft.com/) or PowerShell and Microsoft Graph API. Microsoft Entra ID is the underlying infrastructure that supports identity management for all Microsoft cloud services. Microsoft Entra ID stores information about license assignment states for users.

Without group-based licensing, assigning licenses at the individual user level makes large-scale management difficult. For example, to add or remove user licenses based on organizational changes, such as users joining or leaving the organization or a department, an administrator often must write a complex PowerShell script. This script makes individual calls to the cloud service.

To address those challenges, Microsoft Entra ID now includes group-based licensing. You can assign one or more product licenses to a group. Microsoft Entra ID ensures that the licenses are assigned to all members of the group. Any new members who join the group are assigned the appropriate licenses. When they leave the group, those licenses are removed. This licensing management eliminates the need for automating license management via PowerShell to reflect changes in the organization and departmental structure on a per-user basis.

### License requirements

You must have one of the following licenses to use group-based licensing:

- Paid or trial subscription for Microsoft Entra ID Premium P1 and greater
- Paid or trial edition Office 365 Enterprise E3 or greater

#### Required number of licenses

For any groups assigned a license, you must also have a license for each unique member. While you don't have to assign each member of the group a license, you must have at least enough licenses to include all of the members. For example, if you have 1,000 unique members who are part of licensed groups in your tenant, you must have at least 1,000 licenses to meet the licensing agreement.

### Features

Here are the main features of group-based licensing:

- Licenses can be assigned to any security group in Microsoft Entra ID. Security groups can be synced from on-premises by using Microsoft Entra Cloud Sync (recommended) or Microsoft Entra Connect Sync. You can also create security groups directly in Microsoft Entra ID (also called cloud-only groups), or automatically via the Microsoft Entra dynamic group feature.
- When a product license is assigned to a group, the administrator can disable one or more service plans in the product. Typically, this assignment is done when the organization isn't yet ready to start using a service included in a product. For example, the administrator might assign Microsoft 365 to a department, but temporarily disable the Viva Engage service.
- All Microsoft cloud services that require user-level licensing are supported. This support includes all Microsoft 365 products, Enterprise Mobility + Security, and Dynamics 365.
- Group-based licensing is currently available only through the [Microsoft 365 admin center](https://admin.microsoft.com/).
- Microsoft Entra ID automatically manages license modifications that result from group membership changes. Typically, license modifications are effective within minutes of a membership change.
- A user can be a member of multiple groups with license policies specified. A user can also have some licenses that were directly assigned, outside of any groups. The resulting user state is a combination of all assigned product and service licenses. If a user is assigned same license from multiple sources, the license is consumed only once.
- In some cases, licenses can't be assigned to a user. For example, there might not be enough available licenses in the tenant, or conflicting services are assigned at the same time. Administrators have access to information about users for whom Microsoft Entra ID couldn't fully process group licenses. They can then take corrective action based on that information.

Some Microsoft services aren't available in all locations. The administrator, before assigning a license to a user, should specify usage location in the User Profile.

For group license assignment, any users without a usage location specified inherit the location of the directory. If you have users in multiple locations, we recommend that you always set usage location as part of your user creation. Usage location helps ensure the result of license assignment is always correct and users don't receive services in locations that aren't allowed.


## Exercise - change group license assignments

**Exercise environment needs** - this lab assumes you have a basic Microsoft Entra tenant with at least User Administrator rights to complete it. You can get a free trial subscription at [Try Microsoft Azure for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).

### Change group license assignment

1. Open [https://entra.microsoft.com](https://entra.microsoft.com) to get to the Microsoft Entra admin center.
2. In the left navigation, open **Groups**.
3. Select **All groups**, then select one of the available groups.
4. In the left navigation, under **Manage**, select **Licenses**.

You see a list of any license assignments that are currently made. And you find that you have to use the Microsoft 365 Admin Center to make any updates.

1. Review the current assignments and then, on the menu, select **+ Assignments**.
2. Open [https://admin.microsoft.com](https://admin.microsoft.com) to open the Microsoft 365 admin center.
3. Select **Billing**. Then select **Licenses**.
4. Select an available license from the list.
5. Select **Groups** from the menu near the top of the page.
6. Select the **+ Assign licenses** option.
7. Pick the group you were looking at earlier in Microsoft Entra. Then select the **Assign** button at the bottom of the page.
8. On the group’s Licenses page, review the change. You should be able to see the change in both the Microsoft Entra admin center and the Microsoft 365 admin center.

### Identify and resolve license assignment problems for a group in Microsoft Entra ID

Group-based licensing in Microsoft Entra ID introduces the concept of users in a licensing error state. In this section, we explain the reasons why users might end up in this state.

When you assign licenses directly to individual users, without using group-based licensing, the assignment operation might fail. For example, when you execute the PowerShell cmdlet `Set-MgUserLicense` on a user object, the cmdlet can fail for many reasons that are related to business logic. For example, there might be an insufficient number of licenses or a conflict between two service plans that can't be assigned at the same time. The problem is immediately reported back to you.

When you're using group-based licensing the same errors can occur, but they happen in the background while the Microsoft Entra service is assigning licenses. For this reason, the errors can't be communicated to you immediately. Instead, they're recorded on the user object and then reported via the administrative portal. The original intent to license the user is never lost, but it's recorded in an error state for future investigation and resolution.

### Not enough licenses

**Problem**: There aren't enough available licenses for one of the products specified in the group. You need to either purchase more licenses for the product or free up unused licenses from other users or groups.

To see how many licenses are available, go to **Microsoft Entra - Identity - Billing** , then **Licenses**, then **All products**.

To see which users and groups are consuming licenses, select a product. Under **Licensed users**, you see a list of all users who have licenses assigned directly or via one or more groups. Under **Licensed groups**, you see all groups with product licenses assigned.

**PowerShell**: PowerShell cmdlets report this error as *CountViolation*.

### Service plans that conflict

**Problem**: One of the products specified in the group contains a service plan that conflicts with another service plan that's already assigned to the user via a different product. Some service plans are configured in a way that they can't be assigned to the same user as another, related service plan.

Consider the following example. A user has a license for Office 365 Enterprise *E1* assigned directly, with all the plans enabled. The user is added to a group that has the Office 365 Enterprise *E3* product assigned to it. The E3 product contains service plans that can't overlap with the plans that are included in E1, so the group license assignment fails with the **Conflicting service plans** error. In this example, the conflicting service plans are:

- SharePoint Online (Plan 2) conflicts with SharePoint Online (Plan 1).
- Exchange Online (Plan 2) conflicts with Exchange Online (Plan 1).

To solve this conflict, you need to disable two of the plans. You can disable the E1 license directly assigned to the user. Or, you need to modify the entire group license assignment and disable the plans in the E3 license. Alternatively, you might decide to remove the E1 license from the user if it's redundant in the context of the E3 license.

The decision about how to resolve conflicting product licenses always belongs to the administrator. Microsoft Entra ID doesn't automatically resolve license conflicts.

**PowerShell**: PowerShell cmdlets report this error as *MutuallyExclusiveViolation*.

### Other products depend on this license

**Problem**: One of the products specified in the group contains a service plan that must be enabled for another service plan, in another product, to function. This error occurs when Microsoft Entra ID attempts to remove the underlying service plan. For example, this can happen when you remove the user from the group.

To solve this problem, you need to make sure that the required plan is still assigned to users through some other method or that the dependent services are disabled for those users. After doing that, you can properly remove the group license from those users.

**PowerShell**: PowerShell cmdlets report this error as *DependencyViolation*.

### Usage location isn't allowed

**Problem**: Some Microsoft services aren't available in all locations because of local laws and regulations. Before you can assign a license to a user, you must specify the **Usage location** property for the user. You can specify the location under the **User**, then **Profile**, then **Edit** the section in the Azure portal.

When Microsoft Entra ID attempts to assign a group license to a user whose usage location isn't supported, it fails and records an error on the user.

To solve this problem, remove users from unsupported locations from the licensed group. Alternatively, if the current usage location values don't represent the actual user location, you can modify them so that the licenses are correctly assigned next time (if the new location is supported). You can specify the usage location under the user's **Properties** tab in the [Microsoft Entra admin center](https://entra.microsoft.com).

**PowerShell**: PowerShell cmdlets report this error as *ProhibitedInUsageLocationViolation*.

Note

When Microsoft Entra ID assigns group licenses, any users without a specified usage location inherit the location of the directory. We recommend that administrators set the correct usage location values on users before using group-based licensing to comply with local laws and regulations.

### Duplicate proxy addresses

If you use Exchange Online, some users in your organization might be incorrectly configured with the same proxy address value. When group-based licensing tries to assign a license to such a user, it fails and shows “Proxy address is already being used.”

After you resolve any proxy address problems for the affected users, make sure to force license processing on the group to ensure that the licenses can now be applied.

### Microsoft Entra Mail and ProxyAddresses attribute change

**Problem**: While updating license assignment on a user or a group, you might see that the Microsoft Entra Mail and ProxyAddresses attribute of some users are changed.

Updating license assignment on a user causes the proxy address calculation to be triggered, which can change user attributes.

### LicenseAssignmentAttributeConcurrencyException in audit logs

**Problem**: User has LicenseAssignmentAttributeConcurrencyException for license assignment in audit logs. When group-based licensing tries to process concurrent license assignment of the same license to a user, this exception is recorded on the user. This typically happens when a user is a member of more than one group with same assigned license. Microsoft Entra ID retries processing the user license and will resolve the issue. There's no action required from the customer to fix this issue.

### More than one product license assigned to a group

You can assign more than one product license to a group. For example, you can assign Office 365 Enterprise E3 and Enterprise Mobility + Security to a group to easily enable all included services for users.

Microsoft Entra ID attempts to assign all licenses that are specified in the group to each user. If Microsoft Entra ID can't assign one of the products because of business logic problems, it won't assign the other licenses in the group either. An example is if there aren't enough licenses for all, or if there are conflicts with other services that are enabled on the user.

You can see the users who failed to get assigned and check which products are affected by this problem.

### When a licensed group is deleted

You must remove all licenses assigned to a group before you can delete the group. However, removing licenses from all the users in the group can take time. There can be failures if user has a dependent license assigned. If a user has a license that's dependent on a license, which is being removed due to group deletion, the license assignment to the user is converted from inherited to direct.

For example, consider a group that has Office 365 E3/E5 assigned with a Skype for Business service plan enabled. Also imagine that a few members of the group have Audio Conferencing licenses assigned directly. When the group is deleted, group-based licensing tries to remove Office 365 E3/E5 from all users. Because Audio Conferencing is dependent on Skype for Business, for any users with Audio Conferencing assigned, group-based licensing converts the Office 365 E3/E5 licenses to direct license assignment.

### Manage licenses for products with prerequisites

Some Microsoft Online products you might own are *add-ons*. Add-ons require a prerequisite service plan to be enabled for a user or a group before they can be assigned a license. With group-based licensing, the system requires that both the prerequisite and add-on service plans be present in the same group to ensure that any users who are added to the group can receive the fully working product. Let's consider the following example:

Microsoft Workplace Analytics is an add-on product. It contains a single service plan with the same name. We can only assign this service plan to a user, or group, when one of the following prerequisites is also assigned:

- Exchange Online (Plan 1)
- Exchange Online (Plan 2)

If we try to assign this product on its own to a group, the portal returns a notification message. If we select the item details, it shows the following error message:

License operation failed. Make sure that the group has necessary services before adding or removing a dependent service. **The service Microsoft Workplace Analytics requires Exchange Online (Plan 2) to be enabled as well**.

To assign this add-on license to a group, we must ensure that the group also contains the prerequisite service plan. For example, we might update an existing group that already contains the full Office 365 E3 product, and then add the add-on product to it.

It's also possible to create a standalone group that contains only the minimum required products to make the add-on work. It can then be used to license only selected users for the add-on product. Based on the previous example, you would assign the following products to the same group:

- Office 365 Enterprise E3 with only the Exchange Online (Plan 2) service plan enabled
- Microsoft Workplace Analytics

From now on, any users added to this group consume one license of the E3 product and one license of the Workplace Analytics product. At the same time, those users can be members of another group that gives them the full E3 product, and they still consume only one license for that product.

Tip

You can create multiple groups for each prerequisite service plan. For example, if you use both Office 365 Enterprise E1 and Office 365 Enterprise E3 for your users, you can create two groups to license Microsoft Workplace Analytics: one that uses E1 as a prerequisite and the other that uses E3. This lets you distribute the add-on to E1 and E3 users without consuming more licenses.

### Force the group license process to resolve errors

Depending on what steps taken to resolve the errors, it might be necessary to manually trigger the processing of a group to update the user state.

For example, if you free up some licenses by removing direct license assignments from users, you need to trigger the processing of groups that previously failed to fully license all user members. To reprocess a group, go to the group pane, open **Licenses**, and then select the **Reprocess** button on the toolbar.

### Force the user license process to resolve errors

Depending on what steps taken to resolve the errors, it might be necessary to manually trigger the processing of a user to update the user's state.

For example, after you resolve duplicate proxy address problem for an affected user, you need to trigger the processing of the user. To reprocess a user, go to the user pane, open **Licenses**, and then select the **Reprocess** button on the toolbar.

### How to migrate users with individual licenses to group licenses

You can have existing licenses deployed to users in the organizations via direct assignment; that is, using PowerShell scripts or other tools to assign individual user licenses. Before you begin using group-based licensing to manage licenses in your organization, you can use this migration plan to seamlessly replace existing solutions with group-based licensing.

Keep in mind that you should avoid a situation in which migrating to group-based licensing results in users temporarily losing their currently assigned licenses. Any process that result in removal of licenses should be avoided to remove the risk of users losing access to services and their data.

#### Recommended migration process

1. You have existing automation (for example, PowerShell) managing license assignment and removal for users. Leave it running as is.
2. Create a new licensing group (or decide which existing groups to use) and make sure that all required users are added as members.
3. Assign the required licenses to those groups; your goal should be to reflect the same licensing state your existing automation (for example, PowerShell) is applying to those users.
4. Verify that licenses are applied to all users in those groups. This application can be done by checking the processing state on each group and by checking Audit Logs.
  - You can perform a random check of a few individual users by looking at their license details. You see that they have the same licenses assigned “directly” and “inherited” from groups.
  - You can run a PowerShell script to [verify how licenses are assigned to users](https://learn.microsoft.com/en-us/azure/active-directory/enterprise-users/licensing-group-advanced).
  - When the same product license is assigned to the user both directly and through a group, only one license is consumed by the user. Hence no more licenses are required to perform migration.

5. Verify that no license assignments failed by checking each group for users in error state.

Consider removing the original direct assignments. We recommend that you do it gradually, and monitor the outcome on a subset of users first. If you leave the original direct assignments on users, when the users leave their licensed groups they retain the directly assigned licenses, which might not be what you want.

#### An example

An organization has 1,000 users. All users require Office 365 Enterprise E3 licenses. Currently the organization has a PowerShell script running on premises, adding and removing licenses from users as they come and go. However, the organization wants to replace the script with group-based licensing so licenses can be managed automatically by Microsoft Entra ID.

Here is what the migration process could look like:

1. Using the Azure portal, assign the Office 365 E3 license to the **All users** group in Microsoft Entra ID.
2. Confirm that license assignment has completed for all users. Go to the overview page for the group, select **Licenses**, and check the processing status at the top of the **Licenses** page.
  - Look for “Latest license changes have been applied to all users" to confirm processing has completed.
  - Look for a notification on top about any users for whom licenses were not successfully assigned. Did we run out of licenses for some users? Do some users have conflicting license plans that prevent them from inheriting group licenses?

3. You need to check a few users to verify that they have both the direct and group licenses applied. Go to the profile page for a user, select Licenses, and examine the state of licenses.

- This is the expected user state during migration:

1. After confirming that both direct and group licenses are equivalent, you can start removing direct licenses from users. You can test this by removing them for individual users in the portal and then run automation scripts to have them removed in bulk. Here's an example of the same user with the direct licenses removed through the portal. Notice that the license state remains unchanged, but we no longer see direct assignments.

### Change license assignments for a user or group in Microsoft Entra ID

This section describes how to move users and groups between service license plans in Microsoft Entra ID. The goal is to ensure that there's no loss of service or data during the license change. Users should switch between services seamlessly. The license plan assignment steps in this section describe changing a user or group on Office 365 E1 to Office 365 E3, but the steps apply to all license plans. When you update license assignments for a user or group, the license assignment removals and new assignments are made simultaneously so that users don't lose access to their services during license changes or see license conflicts between plans.

Before you update the license assignments, verify certain assumptions are true for all of the users or groups to be updated. If the assumptions aren't true for all of the users in a group, the migration might fail for some. As a result, some of the users might lose access to services or data. Ensure that:

- Users have the current license plan that's assigned to a group and inherited by the user and not assigned directly.
- You have enough available licenses for the license plan you're assigning. If you don't have enough licenses, some users might not be assigned the new license plan. You can check the number of available licenses.
- Always confirm users don't have assigned service licenses that can conflict with the desired license or prevent removal of the current license. For example, a license from a service such as Workplace Analytics or Project Online that has a dependency on other services.
- If you manage groups on-premises and sync them into Microsoft Entra ID via Microsoft Entra Connect, then you add or remove users by using your on-premises system. It can take some time for the changes to sync with Microsoft Entra ID to be picked up by group licensing.
- If you're using Microsoft Entra dynamic group memberships, you add or remove users by changing their attributes, but the update process for license assignments remains the same.


## Exercise - change user license assignments

**Exercise environment needs** - this lab assumes you have a basic Microsoft Entra tenant with at least User Administrator rights to complete it. You can get a free trial subscription at [Try Microsoft Azure for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).

### Create a new user in Microsoft Entra ID

1. Browse to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. In the left navigation, under **Identity**, select **Users**.
3. In the Users page, on the menu, select **+ New user** and then **Create new user**.
4. Create a user using the following information:    **Setting** **Value**     User name DominiqueK   Name Dominique Koch   First name Dominique   Last name Koch   Password Make a unique password for the user   Usage location Select your preferred usage location
5. When complete, verify the account for Dominique Koch is shown in the **All users** list.

### Update user license assignments

License assignment to individual users is managed through the Microsoft 365 admin center.

1. Open the [Microsoft 365 admin center](https://admin.microsoft.com).
2. Select **Billing**, then select **Licenses**.
3. Select an available license from the list.
4. Select **Licensed users** from the menu near the top of the page.
5. Select **+ Assign licenses**.
6. Search for and select **Dominique Koch**, then select **Assign** at the bottom of the page.
7. When complete, verify the license is listed on Dominique Koch's profile in the Microsoft Entra admin center under **Identity** > **Users** > select the user > **Licenses**.


## Create custom security attributes

### What is a custom security attribute?

Custom security attributes in Microsoft Entra ID are business-specific attributes (key-value pairs) that you can define and assign to Microsoft Entra objects. These attributes can be used to store information, categorize objects, or enforce fine-grained access control over specific Azure resources.

#### Why use custom security attributes?

- Extend user profiles, such as add Hourly Salary to all my employees.
- Ensure only administrators can see the Hourly Salary attribute in my employees' profiles.
- Categorize hundreds or thousands of applications to easily create a filterable inventory for auditing.
- Grant users access to the Azure Storage blobs belonging to a project.

#### What can I do with custom security attributes?

- Define business-specific information (attributes) for your tenant.
- Add custom security attributes to Microsoft Entra users and enterprise applications (service principals).
- Manage Microsoft Entra objects using custom security attributes with queries and filters.
- Provide attribute governance so attributes determine who can get access.

Custom security attributes are **not** supported in Microsoft Entra Domain Services, SAML token claims, or JSON Web Token (JWT) claims.

#### Features of custom security attributes

- Available tenant-wide
- Include a description
- Support different data types: Boolean, integer, string
- Support single value or multiple values
- Support user-defined free-form values or predefined values
- Assign custom security attributes to directory synced users from an on-premises Active Directory


## Explore automatic user creation

![Diagram of the process flow for auto user provisioning in Microsoft Entra ID. Auto provision users and groups.](https://learn.microsoft.com../../wwl-sci/create-configure-manage-identities/media/automatic-user-provisioning.png)

#### Components of SCIM (System for Cross-Domain Identity Management)

- **HCM system** - Applications and technologies that enable Human Capital Management process and practices that support and automate HR processes throughout the employee lifecycle.
- **Microsoft Entra Provisioning Service** - Uses the SCIM 2.0 protocol for automatic provisioning. The service connects to the SCIM endpoint for the application, and uses the SCIM user object schema and REST APIs to automate provisioning and deprovisioning of users and groups.
- **Microsoft Entra ID** - User repository used to manage the lifecycle of identities and their entitlements.
- **Target system** - Application or system that has SCIM endpoint and works with the Microsoft Entra provisioning to enable automatic provisioning of users and groups.

#### Why use SCIM?

System for Cross-Domain Identity Management (SCIM) is an open standard protocol for automating the exchange of user identity information between identity domains and IT systems. SCIM ensures that employees added to the Human Capital Management (HCM) system automatically have accounts created in Microsoft Entra ID or Windows Server Active Directory. User attributes and profiles are synchronized between the two systems, updating, or removing users based on the user status or role change.

The key is keeping your identity systems up to date. If a user can be automatically deprovisioned from Microsoft Entra ID as soon as they're removed from your HR systems, you have less worry about a possible breach.

#### API-driven inbound provisioning

Not all HR systems expose a SCIM endpoint. For these scenarios, Microsoft Entra ID supports **API-driven inbound provisioning**, which reached general availability in March 2024. Instead of requiring the source system to push data via SCIM, any automation tool, or script can retrieve workforce data from any system of record and send it to the Microsoft Entra provisioning API. Supported authoritative sources include Workday, SAP SuccessFactors, and any custom HR system integrated via the API. This approach gives organizations flexibility to automate identity lifecycle management regardless of their HR platform's native integration capabilities.


## Module assessment

Choose the best response for each of the questions below.

### Check your knowledge


## Summary and resources

You completed this module, you are able to:

- Create, configure, and manage users
- Create, configure, and manage groups
- Manage licenses
- Configure and manage device registration
- Explore custom security attributes and automatic account provisioning

### Resources

Use these resources to discover more:

- [Quickstart: Create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users)
- [Bulk create users in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/users/users-bulk-add)
- [Create a basic group and add members using Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/fundamentals/how-to-manage-groups)
- [Create or update a dynamic membership group in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/users/groups-create-rule)
- [What is Microsoft Entra Cloud Sync?](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/what-is-cloud-sync)
- [Manage license requests](https://learn.microsoft.com/en-us/microsoft-365/commerce/licenses/manage-license-requests)
- [Assign licenses to users - Microsoft 365 Admin Center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/assign-licenses-to-users)
- [Plan Microsoft Entra device deployment](https://learn.microsoft.com/en-us/entra/identity/devices/plan-device-deployment)
- [API-driven inbound provisioning concepts](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/inbound-provisioning-api-concepts)


---

# Implement and manage external identities

_https://learn.microsoft.com/en-us/training/modules/implement-manage-external-identities/_


## Introduction

Being able to invite external users to use your Azure resources is a great benefit, but it needs to be done in a secure way. This module is designed to help you understand how to enable secure B2B collaboration scenarios with users outside your organization, including managing external collaboration settings in Microsoft Entra ID and inviting users individually or in bulk. You will also learn about managing external user accounts and configuring identity providers.

### Learning objectives

In this module, you:

- Manage external collaboration settings in Microsoft Entra ID.
- Invite external users (individually or in bulk).
- Manage external user accounts in Microsoft Entra ID.
- Configure identity providers (social and SAML/WS-fed).
- Explore Microsoft Entra Verified ID.

### Prerequisites

None


## Describe guest access and Business to Business accounts

![Diagram of allowing external users to join your Microsoft Entra tenant as a guest user.](https://learn.microsoft.com../../wwl-sci/implement-manage-external-identities/media/guest-user-diagram.png)

#### Define guest users

Microsoft Entra B2B collaboration is a feature within Microsoft Entra External Identities, part of Microsoft Entra that lets you invite guest users to collaborate with your organization. With B2B collaboration, you can securely share your company's applications and services with external users, while maintaining control over your own corporate data. Work safely and securely with external partners, large or small, even if they don't have Microsoft Entra ID or an IT department.

#### How guest users join your Microsoft Entra tenant

A simple invitation and redemption process lets partners use their own credentials to access your company's resources. You can also enable self-service sign-up user flows to let external users sign up for apps or resources themselves. Once the external user has redeemed their invitation or completed sign-up, they're represented in your directory as a user object. B2B collaboration user objects are typically given a user type of "guest" and can be identified by the #EXT# extension in their user principal name.

Developers can use Microsoft Entra ID business-to-business APIs to customize the invitation process or write applications like self-service sign-up portals.

#### B2B collaboration

B2B collaboration is a capability of Microsoft Entra External Identities that lets you collaborate with users and partners outside of your organization. With B2B collaboration, an external user is invited to sign in to your Microsoft Entra organization using their own credentials. This B2B collaboration user can then access the apps and resources you want to share with them. A user object is created for the B2B collaboration user in the same directory as your employees. B2B collaboration user objects have limited privileges in your directory by default, and they can be managed like employees, added to groups, and so on.


## Manage external collaboration

Microsoft Entra External Identities is a feature that makes it possible for you to allow people outside your organization to access your apps and resources. Your partners, distributors, suppliers, vendors, and other guest users can "bring their own identities." Whether they have a corporate or government-issued digital identity, or an unmanaged social identity like Google or Facebook, they can use their own credentials to sign in. The external user’s identity provider manages their identity, and you manage access to your apps with Microsoft Entra ID to keep your resources protected.

### Invitation redemption flow

![Diagram of the redemption of an external invitation to join Microsoft Entra tenant as a guest.](https://learn.microsoft.com../../wwl-sci/implement-manage-external-identities/media/business-to-business-invitation-redemption.png)

1. Microsoft Entra ID performs user-based discovery to determine if the user already exists in a managed Microsoft Entra tenant. (Unmanaged Microsoft Entra accounts can no longer be used for redemption.) If the user’s User Principal Name (UPN) matches both an existing Microsoft Entra account and a personal MSA, the user is prompted to choose which account they want to redeem with.
2. If an admin has enabled SAML/WS-Fed IdP federation, Microsoft Entra ID checks if the user’s domain suffix matches the domain of a configured SAML/WS-Fed identity provider and redirects the user to the pre-configured identity provider.
3. If an admin has enabled Google federation, Microsoft Entra ID checks if the user’s domain suffix is gmail.com, or googlemail.com and redirects the user to Google.
4. The redemption process checks if the user has an existing personal MSA. If the user already has an existing MSA, they'll sign in with their existing MSA.
5. Once the user’s home directory is identified, the user is sent to the corresponding identity provider to sign in.
6. If no home directory is found and the email one-time passcode feature is enabled for guests, a passcode is sent to the user through the invited email. The user retrieves and enters this passcode in the Microsoft Entra sign-in page.
7. If no home directory is found and email one-time passcode for guests is disabled, the user is prompted to create a consumer MSA with the invited email. We support creating an MSA with work emails in domains that aren't verified in Microsoft Entra ID.
8. The user, after authenticating to the right identity provider, is redirected to Microsoft Entra ID to complete the consent experience.

### External identities scenarios

Microsoft Entra External Identities focus less on a user's relationship to your organization and more on how the user wants to sign in to your apps and resources. Within this framework, Microsoft Entra ID supports various scenarios.

A B2B collaboration scenario allows you to invite external users into your own tenant as "guest" users that you can assign permissions to (for authorization) while letting them use their existing credentials (for authentication). Users sign in to the shared resources using a simple invitation and redemption process with their work, school, or other email account. You can also use Microsoft Entra entitlement management to configure policies that manage access for external users. And now with the availability of self-service sign up user flows, you can allow external users to sign up for applications themselves. The experience can be customized to allow sign up with a work, school, or social identity (such as Google or Facebook). You can also collect information about the user during the sign up process.

The following list identifies an example B2B collaboration scenario and details some of the capabilities it provides:

- Primary scenario - Collaboration using Microsoft applications (Microsoft 365, Teams, and so on) or your own applications (SaaS apps, custom-developed apps, and so on).
- Intended for - Collaborating with business partners from external organizations like suppliers, partners, vendors. Users appear as guest users in your directory.
- Identity providers supported - External users can collaborate using work accounts, school accounts, any email address, SAML and WS-Fed based identity providers, Gmail, and Facebook.
- External user management - External users are managed in the same directory as employees, but are typically annotated as guest users. Guest users can be managed the same way as employees, added to the same groups, and so on.
- Single sign-on (SSO) - SSO to all Microsoft Entra-connected apps is supported. For example, you can provide access to Microsoft 365 or on-premises apps, and to other SaaS apps such as Salesforce or Workday.
- Security policy and compliance - Managed by the host/inviting organization (for example, with Conditional Access policies).
- Branding - Host/inviting organization's brand is used.

### Manage external collaboration settings in Microsoft Entra ID

This unit describes how to enable Microsoft Entra B2B collaboration. Then, we explore the ability to designate who can invite guests and determine the permissions that guests have.

By default, all users and guests in your directory can invite guests even if they're not assigned to an admin role. External collaboration settings let you turn guest invitations on or off for different types of users in your organization. You can also delegate invitations to individual users by assigning roles that allow them to invite guests.

Microsoft Entra ID allows you to restrict what external guest users can see in your Microsoft Entra directory. By default, guest users are granted a limited permission level. The guests are blocked from listing users, groups, or other directory resources, but the guests can see membership of non-hidden groups. Admins can change the guest permissions setting allowing you to restrict guest access even further, so that guests can only view their own profile information. For details, see [Restrict guest access permissions](https://learn.microsoft.com/en-us/entra/identity/users/users-restrict-guest-permissions).

### Configure business-to-business external collaboration settings

With Microsoft Entra B2B (Business to Business) collaboration, a tenant admin can set the following invitation policies:

- Turn off invitations (no external users can be invited)
- Only admins and users in the Guest Inviter role can invite (only admins and users in the Guest Inviter role can invite)
- Admins, the Guest Inviter role, and members can invite (same as above setting, but invited members can also invite external users)
- All users, including guests, can invite (as the name implies, all users in the tenant can invite external users)

By default, all users, including guests, can invite guest users.


## Exercise - configure external collaboration

### Configure external collaboration settings

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/) as a tenant administrator.
2. Select **Identity.**
3. Select **External Identities - External collaboration settings**.
4. Under **Guest user access**, review access levels that are available and then select **Guest user access is restricted to properties and memberships of their own directory objects (most restrictive)**.

Note

- Guest users have the same access as members (most inclusive): This option gives guests the same access to Microsoft Entra resources and directory data as member users.
- Guest users access limited to properties and memberships of directory objects: (Default) This setting blocks guest users from certain directory tasks, like enumerating users, groups, or other directory resources. Guests can see membership of all nonhidden groups.
- Guest user access is restricted to properties and memberships of their own directory objects (most restrictive): With this setting, guests can access only their own profiles. Guests aren't allowed to see other users' profiles, groups, or group memberships.

1. Under **Guest invite settings**, mark **Only user assigned to specific admin roles can invite guest users**.
2. Inviting guests to collaborate moves the least restrictive option, where anyone can invite guests, to the most restrictive where no one can invite guests.
3. Anyone in the organization can invite guests: Set to allow anyone to invite guest users, including users, admins, and even other guest users.
4. Member users and users assigned to specific admin roles: Set to allow only full members of the organization or members of admin groups to invite guests.
5. Only users assigned specific admin roles: Set to allow only those people included in specific admin roles to invite guests.
6. No one in organization can invite guests: Set to restrict all guest user invites by members.
7. Users in the **Guest Inviter role** can invite guests, if admin users can invite guest.

  ​
 12. Under **Collaboration restrictions**, review the available options and accept the default settings.

Important

You can create either an allowlist or a blocklist. You can't set up both types of lists. By default, whatever domains aren't in the allowlist are on the blocklist, and vice versa. You can create only one policy per organization. You can update the policy to include more domains, or you can delete the policy to create a new one. The number of domains you can add to an allowlist or blocklist is limited only by the size of the policy. The maximum size of the entire policy is 25 KB (25,000 characters), which includes the allowlist or blocklist and any other parameters configured for other features. This list works independently from OneDrive and SharePoint Online allow/block lists. If you want to restrict individual file sharing in SharePoint Online, you need to set up an allow or blocklist for OneDrive for Business and SharePoint Online. The list doesn't apply to external users who redeemed the invitation. The list will be enforced after the list is set up. If a user invitation is in a pending state, and you set a policy that blocks their domain, the user's attempt to redeem the invitation fails.

1. When finished, save your changes.


## Invite external users - individually and in bulk

As a user who is assigned any of the limited administrator directory roles, you can use the Azure portal to invite B2B collaboration users. You can invite guest users to the directory, to a group, or to an application. After you invite a user through any of these methods, the invited user's account is added to Microsoft Entra ID, with a user type of *Guest*. The guest user must then redeem their invitation to access resources. An invitation of a user does not expire.

![Diagram of how a guest user is invited to the directory, and how they can access resources once they are granted access.](https://learn.microsoft.com../../wwl-sci/implement-manage-external-identities/media/external-user-flow.png)

After you add a guest user to the directory, you can either send the guest user a direct link to a shared app, or the guest user can select the redemption URL in the invitation email. Make sure your organization's external collaboration settings are configured such that you're allowed to invite guests. By default, all users and admins can invite guests. But your organization's external collaboration policies might be configured to prevent certain types of users or admins from inviting guests.

### How users in your organization can invite guest users to an app

After a guest user has been added to the directory in Microsoft Entra ID, an application owner can send the guest user a direct link to the app they want to share. Microsoft Entra admins can also set up self-service management for gallery or SAML-based apps in their Microsoft Entra tenant. This way, application owners can manage their own guest users, even if the guest users haven’t been added to the directory yet. When an app is configured for self-service, the application owner uses their Access Panel to invite a guest user to an app or add a guest user to a group that has access to the app. Self-service app management for gallery and SAML-based apps requires some initial setup by an admin, which can be summarized as follows:

- Enable self-service group management for your tenant
- Create a group to assign to the app and make the user an owner
- Configure the app for self-service and assign the group to the app

### How to bulk invite Microsoft Entra B2B collaboration users

If you use Microsoft Entra B2B collaboration to work with external partners, you can invite multiple guest users to your organization at the same time. Specifically, you do the following:

- Use **Bulk invite users** to prepare a comma-separated value (.csv) file with the user information and invitation preferences
- Upload the .csv file to Microsoft Entra ID
- Verify the users were added to the directory

#### Understand the CSV template

Download and fill in the bulk upload CSV template to help you successfully invite Microsoft Entra ID guest users in bulk. The CSV template you download might look like this example:

#### CSV template structure

This CSV template will always open with two rows of existing data. The rows in a downloaded CSV template are as follows:

- **Version number**: The first row containing the version number must be included in the upload CSV.
- **Column headings**: The format of the column headings is **Item name**`[PropertyName]`**Required or blank**. For example, `Email address to invite [inviteeEmail] Required`. Some older versions of the template might have slight variations.
- **Examples row**: We have included in the template a row of examples of acceptable values for each column. You must remove the examples row and replace it with your own entries.

#### Additional guidance

- The first two rows of the upload template must not be removed or modified, or the upload can't be processed.
- The required columns are listed first.
- We don't recommend adding new columns to the template. Any additional columns you add are ignored and not processed.
- We recommend that you download the latest version of the CSV template as often as possible.


## Exercise - add guest users to directory

In this exercise, you need to add guest users to the directory.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/) as a user who is assigned a limited administrator directory role or the Guest Inviter role.
2. Select **Identity**
3. Under **Users**, select **All Users**.
4. Select **New user - Invite external user**.

1. On the New user page, select **Invite user** and then add your information as the guest user.
2. Group email addresses are not supported; enter the email address for an individual. Also, some email providers allow users to add a plus symbol (+) and additional text to their email addresses to help with things like inbox filtering. However, Microsoft Entra ID does not currently support plus symbols in email addresses. To avoid delivery issues, omit the plus symbol and any characters following it up to the @ symbol.
3. When complete, select **Invite**.
4. On the Users screen, verify your account is listed and, in the **User type** column, verify **Guest** is shown.

After you send the invitation, the user account is automatically added to the directory as a guest.


## Exercise - invite guest users bulk

Use this exercise to learn to invite guest users in bulk.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/) with an account that is a User administrator in the organization.
2. In the navigation pane, select **Identity**.
3. Under **Users**, select **All Users**.
4. On the All users screen, on the menu, select **Bulk operations - Bulk invite**.    ​
5. In the Bulk invite users pane, select **Download** to a sample CSV template with invitation properties.
6. Using an editor to view the CSV file, review the template.

Note

- **Email address to invite** - The user who will receive an invitation.
- **Redirection url** - The URL to which the invited user is forwarded after accepting the invitation.

1. Open the .csv template and add a line for each guest user. Required values are:    ​
2. Save the file.
3. On the Bulk invite users page, under **Upload your csv file**, browse to the file. When you select the file, validation of the .csv file starts.
4. After the file contents are validated, you'll see **File uploaded successfully**. If there are errors, you must fix them before you can submit the job.    ​
5. When your file passes validation, select **Submit** to start the Azure bulk operation that adds the invitations.
6. To view the job status, select **view the status of each operation**. Or, you can select **Bulk operation results** in the Activity section. For details about each line item within the bulk operation, select the values under the **# Success**, **# Failure**, or **Total Requests** columns. If failures occurred, the reasons for failure will be listed.    ​
7. When the job completes, you'll see a notification that the bulk operation succeeded.


## Demo - manage guest users in Microsoft Entra ID

[Launch the click through demo](https://mslearn.cloudguides.com/guides/Manage%20Guest%20User%20Access%20in%20Azure%20AD%20for%20B2B%20Collaboration?azure-portal=true)

In this interactive guide, you’ll learn how to manage guest user access in Microsoft Entra ID for business-to-business (B2B) collaboration. You’ll see how to invite external users to collaborate, assign resources to guest users, and create Conditional Access policies to keep data secure.


## Manage external user accounts in Microsoft Entra ID

Microsoft Entra B2B collaboration users are added as guest users to the directory, and guest permissions in the directory are restricted by default. Your business might need some guest users to fill higher-privilege roles in your organization. To support defining higher-privilege roles, guest users can be added to any roles you desire, based on your organization's needs.

### Add a B2B user to a role

Microsoft recommends that organizations use the rule of least privilege. You can use Privileged Identity Management (PIM) to grant access for B2B/guest users.

### Key properties of the Microsoft Entra B2B collaboration user

#### UserType

This property indicates the relationship of the user to the host tenancy. This property can have two values:

- **Member**: This value indicates an employee of the host organization and a user in the organization's payroll. For example, this user expects to have access to internal-only sites. This user isn't considered an external collaborator.
- **Guest**: This value indicates a user who isn't considered internal to the company, such as an external collaborator, partner, or customer. Such a user isn't expected to receive a CEO's internal memo or receive company benefits, for example.  Note The UserType has no relation to how the user signs in, the directory role of the user, and so on. This property simply indicates the user's relationship to the host organization and allows the organization to enforce policies that depend on this property.

#### Identities

This property indicates the user’s primary identity provider. A user can have several identity providers, which can be viewed by selecting the link next to Identities in the user’s profile or by querying the identities property via the Microsoft Graph API.

| **Identities property value** | **Sign-in state** |
|---|---|
| External Microsoft Entra tenant | This user is homed in an external organization and authenticates by using a Microsoft Entra account that belongs to the other organization. |
| Microsoft account | This user is homed in a Microsoft account and authenticates by using a Microsoft account. |
| {host’s domain} | This user authenticates by using a Microsoft Entra account that belongs to this organization. |
| google.com | This user has a Gmail account and has signed up by using self-service to the other organization. |
| facebook.com | This user has a Facebook account and has signed up by using self-service to the other organization. |
| mail | This user has signed up by using Microsoft Entra Email one-time passcode (OTP). |
| {issuer URI} | This user is homed in an external organization that doesn't use Microsoft Entra ID as their identity provider, but instead uses a SAML/WS-Fed-based identity provider. |

#### Can Microsoft Entra B2B users be added as members instead of guests?

Typically, a Microsoft Entra B2B user and guest user are synonymous. Therefore, a Microsoft Entra B2B collaboration user is added as a user with UserType = Guest by default. However, in some cases, the partner organization is a member of a larger organization to which the host organization also belongs. If so, the host organization might want to treat users in the partner organization as members instead of guests. Use the Microsoft Entra user properties to change a guest into a member.

#### Filter for guest users in the directory

#### Convert UserType

It's possible to convert UserType from Member to Guest and vice-versa by using PowerShell. However, the UserType property represents the user's relationship to the organization. Therefore, you should change this property only if the relationship of the user to the organization changes. If the relationship of the user changes, should the user principal names (UPN) change? Should the user continue to have access to the same resources? Should a mailbox be assigned? We don't recommend changing the UserType by using PowerShell as an atomic activity. Also, in case this property becomes immutable by using PowerShell, we don't recommend taking a dependency on this value.

### Remove guest user limitations

There might be cases where you want to give your guest users higher privileges. You can add a guest user to any role and even remove the default guest user restrictions in the directory to give a user the same privileges as members. It's possible to turn off the default limitations so that a guest user in the company directory has the same permissions as a member user. Remove the limitation in the user settings within Microsoft Entra ID menu.

### Dynamic groups and Microsoft Entra B2B collaboration

#### What are dynamic groups?

Dynamic configuration of security group membership for Microsoft Entra ID is available in the [Azure portal](https://portal.azure.com/). Administrators can set rules to populate groups that are created in Microsoft Entra ID based on user attributes (such as userType, department, or country/region). Members can be automatically added to or removed from a security group based on their attributes. These groups can provide access to applications or cloud resources (SharePoint sites, documents) and to assign licenses to members.

The appropriate Microsoft Entra ID Premium P1 or P2 licensing is required to create and use dynamic groups.


## Manage external users in Microsoft 365 workloads

Similar to Microsoft Entra ID, Microsoft 365 can invite guest users into the directory for collaboration purposes. Those users show in the user list as external, and have limited to no rights in Microsoft 365. However, they can be assigned collaboration rights to any Microsoft 365 workload. Guest users can even be given licenses to allow them to perform specific operations.

#### External collaboration options in Microsoft 365

With Microsoft 365, your users can collaborate with people outside your organization in a variety of ways. Users can share files, invite guests to teams, have meetings with external participants, and chat with people from other organizations. The following table shows the primary ways people from outside your organization can access your Microsoft 365 resources:

| **Activity** | **Account type** | **Default setting** |
|---|---|---|
| Authenticated file and folder sharing | Guest account | Enabled |
| Site sharing | Guest account | Enabled |
| Team sharing | Guest account | Enabled |
| Shared channel in Teams | Existing Microsoft 365 external account | Disabled |
| External chat and meetings | Existing Microsoft 365 external account | Enabled |
| Anonymous meeting join | None | Enabled |
| Unauthenticated file and folder sharing | None | Enabled |

People outside your organization do not have access unless a user in your organization initiates one of these activities. You can disable any of these settings if you don't want to allow that activity in your organization.

#### Governance and management

As with any account in Microsoft Entra ID, you need to review and manage them regularly. Set up procedures to validate all users accounts, especially guest users, regularly. If an account does not need a capability, then remove it. If a user, guest or member, no longer needs a license or access then remove it.

Tools to manage Microsoft 365 guest users:

- Microsoft 365 admin center: `https://admin.microsoft.com`
- Microsoft Entra admin center: `https://entra.microsoft.com`
- Microsoft Entra ID within the Azure portal
- By script in Microsoft Graph, PowerShell, or CLI
- Within most of the Microsoft 365 workloads


## Exercise - explore dynamic groups

The goal of this exercise is to create a dynamic group with all users as members.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/) with an account that is assigned the User administrator role in the tenant.
2. Select **Identity**.
3. Under **Groups**, select **All Groups**, and then select **New group**.
4. On the New Group page, under **Group type**, select **Security**.
5. In the **Group name** box, enter **All company users dynamic group**.
6. Select the **Membership type** menu and then select **Dynamic User**.
7. Under **Dynamic user members**, select **Add dynamic query**.
8. On the right above the **Rule syntax** box, select **Edit**.
9. In the Edit rule syntax pane, enter the following expression in the **Rule syntax** box: user.objectId -ne null
10. Select **OK**. The rule appears in the Rule syntax box.

1. Select **Save**. The new dynamic group will now include B2B guest users as well as member users.
2. On the New group page, select **Create** to create the group.


## Implement and manage Microsoft Entra Verified ID

#### What is Entra Verified ID?

Microsoft Entra Verified ID safeguards your organization with an identity solution that's seamless and decentralized. The service allows you to issue and verify credentials. For issuers, Microsoft Entra ID provides a service that they can customize and use to issue their own verifiable credentials. For verifiers, the service provides a free REST API that makes it easy to request and accept verifiable credentials in your apps and services.

We use IDs in our daily lives. We have drivers licenses that we use as evidence of our ability to operate a car. Universities issue diplomas that prove we attained a level of education. We use passports to prove who we are to authorities as we arrive to other countries / regions. The data model describes how we could handle these types of scenarios when working over the internet but in a secure manner that respects users' privacy. In short, verifiable credentials are data objects consisting of claims made by the issuer attesting information about a subject. These claims are identified by schema and include the DID issuer and subject. The issuer's DID creates a digital signature as proof that they attest to this information.

#### Deploying the Microsoft Entra Verified ID service

To deploy Microsoft Entra Verified ID, you will need:

- An Azure tenant with a subscription
- A Microsoft Entra ID premium license
- Logged in as the global administrator
- A configured Azure Key Vault instance

To set up Microsoft Entra Verified ID, follow these steps:

1. In the Azure portal, search for verifiable credentials. Then, select Verifiable Credentials (Preview).
2. From the left menu, select Getting started.
3. Set up your organization by providing the following information:    **Setting** **Description of value to enter**     Organization name Enter a name to reference your business within Verifiable Credentials. Your customers don't see this name.   Domain Enter a domain that's added to a service endpoint in your decentralized identity (DID) document. The domain is what binds your DID to something tangible that the user might know about your business. Microsoft Authenticator and other digital wallets use this information to validate that your DID is linked to your domain. If the wallet can verify the DID, it displays a verified symbol. If the wallet can't verify the DID, it informs the user that the credential was issued by an organization it couldn't validate.   Key vault Enter the name of the key vault you have in your tenant.
4. Select Save and create credential.

Note that these are just the general steps needed to deploy the Microsoft Entra Verified ID service. Follow the article list above for more details.


## Configure identity providers

Direct federation is now called **SAML/WS-Fed identity provider** (IdP) federation. You can set up federation with any organization whose identity provider (IdP) supports the Security Assertion Markup Language (SAML) 2.0 or WS-Federation (WS-Fed) protocol. When you set up SAML/WS-Fed IdP federation with a partner's IdP, new guest users from that domain can use their own IdP-managed organizational account to sign in to your Microsoft Entra tenant and start collaborating with you. There's no need for the guest user to create a separate Microsoft Entra account.

### When is a guest user authenticated with SAML/WS-Fed IdP federation?

After you set up federation with an organization's SAML/WS-Fed IdP, any new guest users you invite will be authenticated using that SAML/WS-Fed IdP. It’s important to note that setting up federation doesn’t change the authentication method for guest users who have already redeemed an invitation from you. Here are some examples:

- Guest users have already redeemed invitations from you, and then later you set up federation with the organization's SAML/WS-Fed IdP. These guest users continue to use the same authentication method they used before you set up federation.
- You set up federation with an organization's SAML/WS-Fed IdP and invite guest users, and then the partner organization later moves to Microsoft Entra ID. The guest users who have already redeemed invitations continue to use the federated SAML/WS-Fed IdP, as long as the federation policy in your tenant exists.
- You delete federation with an organization's SAML/WS-Fed IdP. Any guest users currently using the SAML/WS-Fed IdP are unable to sign in.

In any of these scenarios, you can update a guest user’s authentication method by resetting their redemption status. SAML/WS-Fed IdP federation is tied to domain namespaces, such as contoso.com and fabrikam.com. When the admin establishes federation with AD FS or a third-party IdP, organizations associate one or more domain-namespaces to these IdPs.

### End-user experience

With SAML/WS-Fed IdP federation, guest users sign into your Microsoft Entra tenant using their own organizational account. When they're accessing shared resources and are prompted for sign-in, users are redirected to their IdP. After successful sign-in, users are returned to Microsoft Entra ID to access resources. If the Microsoft Entra session expires or becomes invalid and the federated IdP has SSO enabled, the user experiences SSO. If the federated user's session is valid, the user isn't prompted to sign in again. Otherwise, the user is redirected to their IdP for sign-in.

### Security Assertion Markup Language 2.0 configuration

Microsoft Entra B2B can be configured to federate with identity providers that use the SAML protocol with specific requirements listed below.

Note

You can associate multiple domains with a single federation configuration. The partner's domain can be either Microsoft Entra verified or unverified.

#### Required Security Assertion Markup Language 2.0 attributes and claims

The following tables show requirements for specific attributes and claims that must be configured at the third-party identity provider. To set up federation, the following attributes must be received in the SAML 2.0 response from the identity provider. These attributes can be configured by linking to the online security token service XML file or by entering them manually. Ensure the value matches the cloud for which you're setting up external federation.

Required attributes for the SAML 2.0 response from the IdP:

| **Attribute** | **Value for a workforce tenant** | **Value for an external tenant** |
|---|---|---|
| AssertionConsumerService | `https://login.microsoftonline.com/login.srf` | `https://<tenantID>.ciamlogin.com/login.srf` |
| Audience | `https://login.microsoftonline.com/<tenant ID>/` (recommended). Existing federations that use the global endpoint `urn:federation:MicrosoftOnline` continue to work, but new federations should use the tenanted endpoint. | `https://login.microsoftonline.com/<tenant ID>/` (recommended). |
| Issuer | The issuer URI of the partner IdP, for example `https://www.example.com/exk10l6w90DHM0yi...` | The issuer URI of the partner IdP, for example `https://www.example.com/exk10l6w90DHM0yi...` |

Required claims for the SAML 2.0 token issued by the IdP:

| **Attribute** | **Value** |
|---|---|
| NameID Format | `urn:oasis:names:tc:SAML:2.0:nameid-format:persistent` |
| emailaddress | `https://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress` |

### WS-Federation configuration

Microsoft Entra B2B can be configured to federate with identity providers that use the WS-Fed protocol with some specific requirements as listed below. Currently, the two WS-Fed providers that have been tested for compatibility with Microsoft Entra ID are AD FS and Shibboleth.

The partner's domain can be either Microsoft Entra verified or unverified. If the partner's passive authentication URL domain doesn't match the target domain (or a host within it), the partner must add a DNS TXT record for the authentication URL domain to enable federation.

#### Required WS-Federation attributes and claims

The following tables show requirements for specific attributes and claims that must be configured at the third-party WS-Fed identity provider. To set up federation, the following attributes must be received in the WS-Fed message from the identity provider. These attributes can be configured by linking to the online security token service XML file or by entering them manually. Ensure the value matches the cloud for which you're setting up external federation.

Required attributes in the WS-Fed message from the IdP:

| **Attribute** | **Value for a workforce tenant** | **Value for an external tenant** |
|---|---|---|
| PassiveRequestorEndpoint | `https://login.microsoftonline.com/login.srf` | `https://<tenantID>.ciamlogin.com/login.srf` |
| Audience | `https://login.microsoftonline.com/<tenant ID>/` (recommended). Existing federations that use the global endpoint `urn:federation:MicrosoftOnline` continue to work, but new federations should use the tenanted endpoint. | `https://login.microsoftonline.com/<tenant ID>/` (recommended). |
| Issuer | The issuer URI of the partner IdP, for example `https://www.example.com/exk10l6w90DHM0yi...` | The issuer URI of the partner IdP, for example `https://www.example.com/exk10l6w90DHM0yi...` |

Required claims for the WS-Fed token issued by the IdP:

| **Attribute** | **Value** |
|---|---|
| ImmutableID | `https://schemas.microsoft.com/LiveID/Federation/2008/05/ImmutableID` |
| emailaddress | `https://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress` |

### Add Google as an identity provider for B2B guest users

By setting up federation with Google, you can allow invited users to sign in to your shared apps and resources with their own Gmail accounts, without having to create Microsoft accounts.

Note

Google federation is designed specifically for Gmail users. To federate with G Suite domains, use [direct federation](https://learn.microsoft.com/en-us/education/windows/configure-aad-google-trust).

### What is the experience for the Google user?

When you send an invitation to Google Gmail users, the guest users should access your shared apps or resources by using a link that includes the tenant context. Their experience varies depending on whether they're already signed in to Google:

- Guest users who aren't signed in to Google will be prompted to do so.
- Guest users who are already signed in to Google will be prompted to choose the account they want to use. They must choose the account you used to invite them.

Guest users who see a *header too long* error can clear their cookies or open a private or incognito window and try to sign in again.

### Deprecation of WebView sign-in support

Google is deprecating embedded web-view sign-in support (Starting September 30, 2021). If your apps authenticate users with an embedded web-view and you're using Google federation with Microsoft Entra B2C or Microsoft Entra B2B for external user invitations or self-service sign-up, Google Gmail users won't be able to authenticate.

The following are known scenarios that will affect Gmail users:

- Microsoft apps (e.g. Teams and Power Apps) on Windows.
- Windows apps that use the WebView control, WebView2, or the older WebBrowser control, for authentication. These apps should migrate to using the Web Account Manager (WAM) flow.
- Android applications using the WebView UI element.
- iOS applications using UIWebView/WKWebview.
- Apps using Microsoft Authentication Library.

This change doesn't affect:

- Web apps
- Microsoft 365 services that are accessed through a website (for example, SharePoint Online, Office web apps, and Teams web app)
- Mobile apps using system web-views for authentication (SFSafariViewController on iOS, Custom Tabs on Android).
- Google Workspace identities, for example when you’re using SAML-based federation with Google Workspace.
- Windows apps that use the Web Account Manager (WAM) or Web Authentication Broker (WAB).

### Sign-in endpoints

Google guest users can sign in to your multitenant or Microsoft first-party apps by using a common endpoint (a general app URL that doesn't include your tenant context). During sign-in, the guest user selects **Sign-in options**, and then selects **Sign in to an organization**. They then enter the name of your organization and continue signing in using their Google credentials.

Google guest users can also use application endpoints that include your tenant information, for example:

- `https://myapps.microsoft.com/?tenantid=<your tenant ID>`
- `https://myapps.microsoft.com/<your verified domain>.onmicrosoft.com`
- `https://portal.azure.com/<your tenant ID>`

You can also give Google guest users a direct link to an application or resource that includes your tenant information, for example `https://myapps.microsoft.com/signin/X/<application ID>?tenantId=<your tenant ID>`.

#### Step 1: Configure a Google developer project

First, create a new project in the Google Developers Console to obtain a client ID and a client secret that you can later add to Microsoft Entra ID.

1. Go to the Google APIs at [https://console.developers.google.com](https://console.developers.google.com/), and sign in with your Google account. We recommend that you use a shared team Google account.
2. Accept the terms of service if you're prompted to do so.
3. Create a new project: On the dashboard, select **Create Project**, give the project a name (for example, **Microsoft Entra B2B**), and then select **Create**:

  ​
 4. On the **APIs and Services** page, select **View** under your new project. 5. Select **Go to APIs overview** on the APIs card. Select **OAuth consent screen**. 6. Select **External**, and then select **Create**. 7. On the **OAuth consent screen**, enter an **Application name**:

  ​
 8. Scroll to the **Authorized domains** section and enter **microsoftonline.com**:

  ​
 9. Select **Save**. 10. Select **Credentials**. On the **Create credentials** menu, select **OAuth client ID**:

  ​
 11. Under **Application type**, select **Web application**. Give the application a suitable name, like **Microsoft Entra B2B**. Under **Authorized redirect URIs**, enter the following URIs:

- `https://login.microsoftonline.com`
- `https://login.microsoftonline.com/te/ tenant ID /oauth2/authresp` (where **tenant ID** is your tenant ID in Azure)

  ​
 12. Select **Create**. Copy the client ID and client secret. You'll use them when you add the identity provider in the Azure portal.

### Step 2: Configure Google federation in Microsoft Entra ID

You'll now set the Google client ID and client secret. You can use the Azure portal or PowerShell to do so. Be sure to test your Google federation configuration by inviting yourself. Use a Gmail address and try to redeem the invitation with your invited Google account.

**To configure Google federation in the Azure portal**

1. Go to the [Azure portal](https://portal.azure.com/). On the left pane, select **Microsoft Entra ID**.
2. Select **External Identities**.
3. Select **All identity providers**, and then select the **Google** button.
4. Enter the client ID and client secret you obtained earlier. Select **Save**:

  ​

### How do I remove Google federation?

You can delete your Google federation setup. If you do so, Google guest users who have already redeemed their invitation won't be able to sign in. But you can give them access to your resources again by deleting them from the directory and reinviting them.

**To delete Google federation in Microsoft Entra ID**

1. Go to the [Azure portal](https://portal.azure.com/). On the left pane, select **Microsoft Entra ID**.
2. Select **External Identities**.
3. Select **All identity providers**.
4. On the **Google** line, select the ellipsis button (**...**) and then select **Delete**.

  ​
 5. Select **Yes** to confirm the deletion.

### Add Facebook as an identity provider for external identities

You can add Facebook to your self-service-sign-up user flows (Preview) so that users can sign in to your applications using their own Facebook accounts. Allow users to sign in using Facebook, you'll need to enable self-service sign-up for your tenant. After you add Facebook as an identity provider, set up a user flow for the application and select Facebook as one of the sign-in options.

Note

Users can only use their Facebook accounts to sign up through apps using self-service-sign-up and user flows. Users cannot be invited and redeem their invitation using a Facebook account.

### Create an app in the Facebook developers console

To use a Facebook account as an identity provider, you need to create an application in the Facebook developers console. If you don't already have a Facebook account, you can sign up at [https://www.facebook.com/](https://www.facebook.com/).

Note

Use the following URLs in the steps 9 and 16 below.

- For **Site URL** enter the address of your application, such as `https://contoso.com`.
- For **Valid OAuth redirect URIs**, enter `https://login.microsoftonline.com/te/ tenant-id /oauth2/authresp`. You can find your `tenant-ID`in the Microsoft Entra ID Overview screen.

1. Sign in to [Facebook for developers](https://developers.facebook.com/) with your Facebook account credentials.
2. If you haven't already done so, you need to register as a Facebook developer. Select **Get Started** on the upper-right corner of the page, accept Facebook's policies, and complete the registration steps.
3. Select **My Apps** and then **Create App**.
4. Enter a **Display Name** and a valid **Contact Email**.
5. Select **Create App ID**. You have to accept Facebook platform policies and complete an online security check.
6. Select **Settings** then select **Basic**.
7. Choose a **Category**, for example Business and Pages. This value is required by Facebook, but not used for Microsoft Entra ID.
8. At the bottom of the page, select **Add Platform**, and then select **Website**.
9. In **Site URL**, enter the appropriate URL (noted above).
10. In **Privacy Policy URL**, enter the URL for the page where you maintain privacy information for your application, for example `https://www.contoso.com`.
11. Select **Save Changes**.
12. At the top of the page, copy the value of **App ID**.
13. Select **Show** and copy the value of **App Secret**. You use both of them to configure Facebook as an identity provider in your tenant. **App Secret** is an essential security credential.
14. Select the plus sign next to **PRODUCTS**, and then select **Set up** under **Facebook Login**.
15. Under **Facebook Login**, select **Settings**.
16. In **Valid OAuth redirect URIs**, enter the appropriate URL (noted above).
17. Select **Save Changes** at the bottom of the page.
18. To make your Facebook application available to Microsoft Entra ID, select the Status selector at the top right of the page and turn it **On** to make the Application public, and then select **Switch Mode**. At this point, the Status should change from **Development** to **Live**.

### Configure a Facebook account as an identity provider

Now you'll set the Facebook client ID and client secret, either by entering it in Microsoft Entra admin center or by using PowerShell. You can test your Facebook configuration by signing up via a user flow on an app enabled for self-service sign-up.

#### To configure Facebook federation in the Microsoft Entra ID screen

1. Sign in to the [Azure portal](https://portal.azure.com/) as the global administrator of your Microsoft Entra tenant.
2. Under **Azure services**, select **Microsoft Entra ID**.
3. In the left menu, select **External Identities**.
4. Select **All identity providers**, then select **Facebook**.
5. For the **Client ID**, enter the **App ID** of the Facebook application that you created earlier.
6. For the **Client secret**, enter the **App Secret** that you recorded.

  ​
 7. Select **Save**.

### How do I remove Facebook federation?

You can delete your Facebook federation setup. If you do so, any users who have signed up through user flows with their Facebook accounts will no longer be able to sign in.

#### To delete Facebook federation in Microsoft Entra ID:

1. Go to the [Azure portal](https://portal.azure.com/). In the left pane, select **Microsoft Entra ID**.
2. Select **External Identities**.
3. Select **All identity providers**.
4. On the **Facebook** line, select the context menu (**...**) and then select **Delete**.
5. Select **Yes** to confirm deletion.


## Implement cross-tenant access controls

Microsoft Entra organizations can use external identities cross-tenant access settings to manage how they collaborate with other Microsoft Entra organizations or Microsoft clouds. Cross-tenant access settings give you granular control over how external Microsoft Entra organizations collaborate with you, **inbound access**. You can also control how your users collaborate with external Microsoft Entra organizations, **outbound access**.

#### Manage inbound and outbound settings

By default, B2B collaboration with other Microsoft Entra organizations is enabled, and B2B direct connect is blocked. But the following comprehensive admin settings let you manage both of these features.

| **Cross-tenant access setting name** | **Operations managed** |
|---|---|
| Outbound access settings | Control whether users can access resources in an external organization. You can apply settings to everyone, or specify individual users, groups, and applications. |
| Inbound access settings | Control whether users from external Microsoft Entra organizations can access resources in your organization. You can apply these settings to everyone, or specify individual users, groups, and applications. |
| Trust settings (inbound) | Determine whether your Conditional Access policies will trust the multifactor authentication (MFA). You can also require compliant device, and hybrid Microsoft Entra joined device. And finally, allow or restrict user from an external organization if their users have already satisfied these requirements in their home tenants. |
| B2b direct connect | Set up a mutual trust relationship with another Microsoft Entra organization for seamless collaboration. This feature currently works with Microsoft Teams shared channels. |

#### Organizational specific configuration

Above you explored the default settings. These settings are applied to all external connections. However, you can configure specific collaboration settings on a per organization basis as well. In the **cross-tenant access control** screen choose **Organizational settings** then add the tenant. Once added you can configure the inbound and outbound settings.

#### Microsoft Cloud-specific configuration

What if your company has government contracts that need to connect to Microsoft Azure Government or Microsoft Azure China. Use the **Microsoft cloud settings** to connect to and configure the collaboration settings.

#### B2B Direct Connect

B2B direct connect requires a mutual trust relationship between two Microsoft Entra organizations to allow access to each other's resources. Both the resource organization and the external organization need to mutually enable B2B direct connect in their cross-tenant access settings. When the trust is established, the B2B direct connect user has single sign-on access to resources outside their organization using credentials from their home Microsoft Entra organization.

Currently, B2B direct connect capabilities work with Teams shared channels. When B2B direct connect is established between two organizations, users in one organization can create a shared channel in Teams and invite an external B2B direct connect user to it. Then from within Teams, the B2B direct connect user can seamlessly access the shared channel in their home tenant Teams instance, without having to manually sign in to the organization hosting the shared channel.


## Knowledge check

Choose the best response for each of the questions below.

### Check your knowledge


## Summary and resources

Now that you reviewed this module, you're able to:

- Manage external collaboration settings in Microsoft Entra ID
- Invite external users (individually or in bulk)
- Manage external user accounts in Microsoft Entra ID
- Configure identity providers (social and SAML/WS-fed)
- Explore Microsoft Entra Verified ID

### Resources

Use these resources to discover more:

- [External Identities documentation](https://learn.microsoft.com/en-us/entra/external-id/)
- [Enable B2B external collaboration and manage who can invite guest users](https://learn.microsoft.com/en-us/entra/external-id/external-collaboration-settings-configure)
- [What is a guest user access in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/external-id/user-properties)
- [Set up the Microsoft Entra Verified ID service](https://learn.microsoft.com/en-us/entra/verified-id/verifiable-credentials-configure-tenant)
- [Cross-tenant access with Microsoft Entra External Identities](https://learn.microsoft.com/en-us/entra/architecture/external-identity-deployment-architectures)


---

# Implement and manage hybrid identity

_https://learn.microsoft.com/en-us/training/modules/implement-manage-hybrid-identity/_


## Introduction

Hybrid identity allows corporations to have identity solutions that span on-premises and cloud-based environments. This capability provides unified authentication and authorization capabilities to resources regardless of their location.

Organizations today are adding cloud application to their existing on-premises apps, which makes them hybrid companies. They need to have identity solutions that authenticate and authorize users to access applications and the underlying data in a secure way. An on-premises Active Directory solution isn't enough; extending to the cloud with Microsoft Entra ID is necessary to provide a hybrid identity solution.

In this module, you implement and manage a hybrid identity solution using Microsoft Entra ID and Microsoft Entra Connect. You learn how to use the password hash synchronization (PHS) and pass-through authentication (PTA) to ensure you have the right authentication method for your needs. Then you explore how single-sign-on (SSO) enables your users to access the apps they need while using secure access methods. Next, you see how to connect to other existing external directories with Active Directory Federated Services (ADFS). Finally, you learn how Microsoft Entra Connect Health monitors the health of your identity solution and how to troubleshoot some common synchronization errors.

By the end of this module, you're able to implement and manage a hybrid identity solution.

### Learning objectives

In this module, you:

- Plan, design, and implement Microsoft Entra Connect
- Manage Microsoft Entra Connect
- Implement and manage password hash synchronization (PHS)
- Implement and manage pass-through authentication (PTA)
- Implement and manage seamless single sign-on (seamless SSO)
- Implement and manage federation excluding manual AD FS deployments
- Troubleshoot synchronization errors
- Implement and manage Microsoft Entra Connect Health

### Prerequisites

None


## Plan, design, and implement Microsoft Entra Connect

Microsoft Entra Connect is a solution that bridges an organizations on-premises Active Directory with your cloud-based Microsoft Entra ID. IT can synchronize identities from on-premises into Azure and ensures a consistent identity across both platforms. This connection enables services like password hash synchronization, pass-through authentication, and seamless single sign-on (SSO).

Microsoft Entra Connect is the Microsoft tool designed to meet and accomplish your hybrid identity goals. It provides the following capabilities:

- Synchronization - Responsible for creating users, groups, and other objects. Then, making sure identity information for your on-premises users and groups is matching the cloud. This synchronization also includes password hashes.
- Password hash synchronization - A sign-in method that synchronizes a hash of a user's on-premises AD password with Microsoft Entra ID.
- Pass-through authentication - A sign-in method that allows users to use the same password on-premises and in the cloud, but doesn't require the extra infrastructure of a federated environment.
- Federation integration - Federation is an optional part of Microsoft Entra Connect and can be used to configure a hybrid environment using an on-premises AD FS infrastructure. It also provides AD FS management capabilities such as certificate renewal and more AD FS server deployments.
- Health monitoring - Microsoft Entra Connect-Health provides robust monitoring.

### Why use Microsoft Entra Connect?

Integrating your on-premises directories with Microsoft Entra ID makes your users more productive by providing a common identity for accessing both cloud and on-premises resources. With Microsoft Entra Connect, users can use a single identity to access on-premises applications and cloud services such as Microsoft 365. Additionally, organizations can provide an easy deployment experience for synchronization and sign-in using a single tool. Microsoft Entra Connect replaces older versions of identity integration tools; and is included in your Microsoft Entra ID subscription.

### Select an authentication method

Identity is the new control plane of IT security, so authentication is an organization’s access guard to the new cloud world. Organizations need an identity control plane that strengthens their security and keeps their cloud apps safe from intruders. When the Microsoft Entra hybrid identity solution is your new control plane, authentication is the foundation of cloud access. Choosing the correct authentication method is a crucial first decision in setting up a Microsoft Entra hybrid identity solution. To choose an authentication method, you need to consider the time, existing infrastructure, complexity, and cost of implementing your choice. These factors are different for every organization and might change over time.

#### Cloud authentication

When you choose this authentication method, Microsoft Entra ID handles users' sign-in process. When you couple with seamless single sign-on (SSO), users can sign into cloud apps without having to reenter their credentials. With cloud authentication, you can choose from two options:

**Microsoft Entra password hash synchronization (PHS)**. The simplest way to enable authentication for on-premises directory objects in Microsoft Entra. Users can use the same username and password that they use on-premises without having to deploy any more infrastructure.

- **Effort** - Password hash synchronization requires the least effort regarding deployment, maintenance, and infrastructure. This level of effort typically applies to organizations that only need their users to sign in to Microsoft 365, SaaS apps, and other Microsoft Entra ID-based resources. When turned on, password hash synchronization is part of the Microsoft Entra Connect sync process and runs every two minutes.
- **User experience** - To improve users' sign-in experience, deploy seamless SSO with password hash synchronization. Seamless SSO eliminates unnecessary prompts when users are signed in.
- **Advanced scenarios** - If organizations choose to, it's possible to use insights from identities with Microsoft Entra Identity Protection reports with Microsoft Entra ID Premium P2. An example is the leaked credentials report. Windows Hello for Business has specific requirements when you use password hash synchronization. Microsoft Entra Domain Services requires password hash synchronization to create users with their corporate credentials in the managed domain.
- **Business continuity** - Using password hash synchronization with cloud authentication is highly available as a cloud service that scales to all Microsoft datacenters. To make sure password hash synchronization doesn't go down for extended periods, deploy a second Microsoft Entra Connect server in staging mode in a standby configuration.
- **Considerations** - Currently, password hash synchronization doesn't immediately enforce changes in on-premises account states. In this situation, a user has access to cloud apps until the user account state is synchronized to Microsoft Entra ID. Organizations might want to overcome this limitation by running a new synchronization cycle after administrators do bulk updates to on-premises user account states. An example is disabling accounts.

**Microsoft Entra pass-through authentication (PTA)**. Provides a simple password validation for Microsoft Entra authentication services by using a software agent that runs on one or more on-premises servers. The servers validate the users directly with your on-premises Active Directory, which ensures that the password validation doesn't happen in the cloud. Companies with a security requirement to immediately enforce on-premises user account states, password policies, and sign in hours might use this authentication method.

- **Effort** - For pass-through authentication, you need one or more (we recommend three) lightweight agents installed on existing servers. These agents must have access to your on-premises Active Directory Domain Services, including your on-premises AD domain controllers. They need outbound access to the Internet and access to your domain controllers. For this reason, it's not supported to deploy the agents in a perimeter network.
- **User experience** - To improve users' sign-in experience, deploy seamless SSO with pass-through authentication. Seamless SSO eliminates unnecessary prompts after users sign in.
- **Advanced scenarios** - Pass-through authentication enforces the on-premises account policy at the time of sign-in. For example, access is denied when an on-premises user’s account state is disabled, locked out, or their password expires. Access can also be denied if the sign-in attempt falls outside the hours when the user is allowed to sign in.
- **Business continuity** - We recommend that you deploy two extra pass-through authentication agents. These extras are in addition to the first agent on the Microsoft Entra Connect server. This deployment ensures high availability of authentication requests. When you have three agents deployed, one agent can still fail when another agent is down for maintenance.
- **Considerations** - You can use password hash synchronization as a backup authentication method for pass-through authentication when the agents can't validate a user's credentials due to a significant on-premises failure. Fail over to password hash synchronization doesn't happen automatically and you must use Microsoft Entra Connect to switch the sign-in method manually.

#### Federated authentication

When you choose this authentication method, Microsoft Entra ID hands off the authentication process to a separate trusted authentication system, such as on-premises Active Directory Federation Services (AD FS), to validate the user’s password. The authentication system can provide other advanced authentication requirements. Examples are smartcard-based authentication or third party multifactor authentication.

- **Effort** - A federated authentication system relies on an external trusted system to authenticate users. Some companies want to reuse their existing federated system investment with their Microsoft Entra hybrid identity solution. The maintenance and management of the federated system falls outside the control of Microsoft Entra ID. It's up to the organization by using the federated system to make sure it's deployed securely and can handle the authentication load.
- **User experience** - The user experience of federated authentication depends on the implementation of the features, topology, and configuration of the federation farm. Some organizations need this flexibility to adapt and configure the access to the federation farm to suit their security requirements. For example, it's possible to configure internally connected users and devices to sign in users automatically, without prompting them for credentials. This configuration works because they already signed into their devices. If necessary, some advanced security features make users' sign-in process more difficult.
- **Advanced scenarios** - A federated authentication solution is required when customers have an authentication requirement that Microsoft Entra ID doesn't support natively.
  - Authentication that requires smartcards or certificates.
  - On-premises MFA servers or third party multifactor providers requiring a federated identity provider.
  - Authentication by using third party authentication solutions.
  - Sign in that requires a sAMAccountName, for example DOMAIN\username, instead of a User Principal Name (UPN), for example, user@domain.com.

- **Business continuity** - Federated systems typically require a load-balanced array of servers, known as a farm. This farm is configured in an internal network and perimeter network topology to ensure high availability for authentication requests.
- **Considerations** - Federated systems typically require a more significant investment in on-premises infrastructure. Most organizations choose this option if they already have an on-premises federation investment. And if it's a strong business requirement to use a single-identity provider. Federation is more complex to operate and troubleshoot compared to cloud authentication solutions.

### Architecture diagrams

The following diagrams outline the high-level architecture components required for each authentication method you can use with your Microsoft Entra hybrid identity solution. They provide an overview to help you compare the differences between the solutions.

- Simplicity of a password hash synchronization solution:
- Agent requirements of pass-through authentication, using two agents for redundancy:
- Components required for federation in your perimeter and internal network of your organization:

### Recommendations

Your identity system ensures your users' access to cloud apps and the line-of-business apps that you migrate and make available in the cloud. To keep authorized users productive and bad actors out of your organization’s sensitive data, authentication controls access to apps.

Use or enable password hash synchronization for whichever authentication method you choose, for the following reasons:

- **High availability and disaster recovery** - Pass-through authentication and federation rely on on-premises infrastructure. For pass-through authentication, the on-premises footprint includes the server hardware and networking the pass-through authentication agents require. For federation, the on-premises footprint is even larger. It requires servers in your perimeter network to proxy authentication requests and the internal federation servers. To avoid single points of failure, deploy redundant servers. Then authentication requests will always be serviced if any component fails. Both pass-through authentication and federation also rely on domain controllers to respond to authentication requests, which can also fail. Many of these components need maintenance to stay healthy. Outages are more likely when maintenance isn't planned and implemented correctly. Avoid outages by using password hash synchronization because the Microsoft Entra cloud authentication service scales globally and is always available.
- **On-premises outage survival** - The consequences of an on-premises outage due to a cyber-attack or disaster can be substantial, ranging from reputational brand damage to a paralyzed organization unable to deal with the attack. Recently, many organizations were victims of malware attacks, including targeted ransomware, which caused their on-premises servers to go down. When Microsoft helps customers deal with these kinds of attacks, it sees two categories of organizations:
  - Organizations that turned on password hash synchronization, with federated or pass-through authentication change their primary authentication. They can then use password hash synchronization. They were back online in a matter of hours. By using access to email via Microsoft 365, they worked to resolve issues and access other cloud-based workloads.
  - Organizations that didn’t previously enable password hash synchronization had to resort to untrusted external consumer email systems for communications to resolve issues. In those cases, it took them weeks to restore their on-premises identity infrastructure before users were able to sign in to cloud-based apps again.

- **Identity protection** - One of the best ways to protect users in the cloud is Microsoft Entra Identity Protection with Microsoft Entra Premium P2. Microsoft continually scans the Internet for user and password lists that bad actors sell and make available on the dark web. Microsoft Entra ID can use this information to verify if any of the usernames and passwords in your organization are compromised. Therefore, it's critical to enable password hash synchronization no matter which authentication method you use, whether it's federated or pass-through authentication. Leaked credentials are presented as a report. Use this information to block or force users to change their passwords when they try to sign in with leaked passwords.

### Microsoft Entra Connect design concepts

This section describes areas that must be thought through during the implementation design of Microsoft Entra Connect. It's a deep dive on certain areas and these concepts are briefly described in other documents as well.

### sourceAnchor

The sourceAnchor attribute is defined as *an attribute immutable during the lifetime of an object*. It uniquely identifies an object as being the same object on-premises and in Microsoft Entra ID. The attribute is also called **immutableId** and the two names are used interchangeable. The attribute is used for the following scenarios:

- When a new sync engine server is built, or rebuilt after a disaster recovery scenario, this attribute links existing objects in Microsoft Entra ID with objects on-premises.
- If you move from a cloud-only identity to a synchronized identity model, then this attribute allows objects to "hard match" existing objects in Microsoft Entra ID with on-premises objects.
- If you use federation, then this attribute together with the **userPrincipalName** is used in the claim to uniquely identify a user.

The attribute value must follow the following rules:

- Fewer than 60 characters in length
  - Characters not being a-z, A-Z, or 0-9 are encoded and counted as three characters

- Not contain a special character: `\ ! # $ % & * + / = ? ^ { } | ~ > < ( ) ' ; : , [ ] " @ _`
- Must be globally unique
- Must be either a string, integer, or binary
- Shouldn't be based on user's name because names can change
- Shouldn't be case-sensitive and avoid values that vary by case
- Should be assigned when the object is created

If you have a single forest on-premises, the attribute you should use is **objectGuid**. You can also use the objectGuid attribute when you use express settings in Microsoft Entra Connect. And also the attribute used by DirSync. If you have multiple forests and don't move users between forests and domains, then **objectGUID** is a good attribute to use. Another solution is to pick an existing attribute you know doesn't change. Commonly used attributes include **employeeID**. If you consider an attribute that contains letters, make sure there's no chance the case (upper case vs. lower case) can change for the attribute's value. Bad attributes include those attributes with the name of the user. Once the sourceAnchor attribute is decided, the wizard stores the information in your Microsoft Entra tenant. The information will be used by future installation of Microsoft Entra Connect.

### Microsoft Entra sign-in

The synchronization settings of your on-premises directory integration with Microsoft Entra ID can affect the way user authenticates. Microsoft Entra uses userPrincipalName (UPN) to authenticate the user. However, when you synchronize your users, you must choose the attribute to be used for value of userPrincipalName carefully. When you're selecting the attribute for providing the value of UPN to be used in Azure one should ensure

- The attribute values conform to the UPN syntax (RFC 822), the format username@domain
- The suffix in the values matches to one of the verified custom domains in Microsoft Entra ID

In express settings, the assumed choice for the attribute is userPrincipalName. If the userPrincipalName attribute doesn't contain the value you want your users to sign in to Azure, then you must choose **Custom Installation**.

#### Custom domain state and User Principal Name

Ensure that there's a verified domain for the User Principal Name (UPN) suffix. John is a user in contoso.com. You want John to use the on-premises UPN john@contoso.com to sign in to Azure after you have synced users to your Microsoft Entra directory contoso.onmicrosoft.com. To do so, you need to add and verify contoso.com as a custom domain in Microsoft Entra ID before you can start syncing the users. If the UPN suffix of John, for example contoso.com, doesn't match a verified domain in Microsoft Entra ID, then the tool replaces the UPN suffix with contoso.onmicrosoft.com.

Some organizations have non-routable domains, like contoso.local, or simple single label domains like contoso. You're not able to verify a non-routable domain. Microsoft Entra Connect can sync to only a verified domain in Microsoft Entra ID. When you create a Microsoft Entra directory, it creates a routable domain that becomes default domain for your Microsoft Entra ID for example, contoso.onmicrosoft.com. Therefore, it becomes necessary to verify any other routable domain in such a scenario in case you don't want to sync to the default onmicrosoft.com domain.

Microsoft Entra Connect detects if you're running in a non-routable domain environment and would appropriately warn you from going ahead with express settings. If you're operating in a non-routable domain, then it's likely that the UPN, of the users, has a non-routable suffix too. For example, if you're running under contoso.local, Microsoft Entra Connect suggests you use custom settings rather than using express settings. Using custom settings, you're able to specify the attribute that should be used as UPN to sign in to Azure after the users are synced to Microsoft Entra ID.

### Topologies for Microsoft Entra Connect

This section describes various on-premises and Microsoft Entra ID topologies that use Microsoft Entra Connect sync as the key integration solution; it includes both supported and unsupported configurations.

| **Common topology** | **Description** |
|---|---|
| Single forest, single Microsoft Entra tenant | The most common topology is a single on-premises forest, with one or multiple domains, and a single Microsoft Entra tenant. For authentication, password hash synchronization is used. The express installation of Microsoft Entra Connect supports only this topology. |
| Multiple forests, single Microsoft Entra tenant | Many organizations have environments with multiple on-premises Active Directory forests. There are various reasons for having more than one on-premises Active Directory forest. Typical examples are designs with account-resource forests and the result of a merger or acquisition. When you have multiple forests, all forests must be reachable by a single Microsoft Entra Connect sync server. The server must be joined to a domain. If necessary to reach all forests, you can place the server in a perimeter network (also known as DMZ, demilitarized zone, and screened subnet). |
| Multiple forests, single sync server, users are represented in only one directory | In this environment, all on-premises forests are treated as separate entities. No user is present in any other forest. Each forest has its own Exchange organization, and there's no GALSync between the forests. This topology might be the situation after a merger/acquisition or in an organization where each business unit operates independently. These forests are in the same organization in Microsoft Entra ID and appear with a unified GAL. In the preceding picture, each object in every forest is represented once in the metaverse and aggregated in the target tenant. |
| Multiple forests: full mesh with optional GALSync | A full mesh topology allows users and resources to be located in any forest. Commonly, there are two-way trusts between the forests. If Exchange is present in more than one forest, there might be (optionally) an on-premises GALSync solution. Every user is then represented as a contact in all other forests. GALSync is commonly implemented through FIM 2010 or MIM 2016. Microsoft Entra Connect can't be used for on-premises GALSync. |
| Multiple forests: account-resource forest | In this scenario, one (or more) resource forest trusts all account forests. The resource forest typically has an extended Active Directory schema with Exchange and Teams. All Exchange and Teams services, along with other shared services, are located in this forest. Users have a disabled user account in this forest, and the mailbox is linked to the account forest. |
| Staging server | Microsoft Entra Connect supports installing a second server in *staging mode*. A server in this mode reads data from all connected directories but doesn't write anything to connected directories. It uses the normal synchronization cycle and therefore has an updated copy of the identity data. |
| Multiple Microsoft Entra tenants | There's a 1:1 relationship between a Microsoft Entra Connect sync server and a tenant. For each Microsoft Entra tenant, you need one Microsoft Entra Connect sync server installation. The AD tenant instances are isolated by design. That is, users in one tenant can't see users in the other tenant. Separation of users is a supported configuration. Otherwise, you should use the single Microsoft Entra tenant model. |
| Each object only once in a Microsoft Entra tenant | In this topology, one Microsoft Entra Connect sync server is connected to each tenant. The Microsoft Entra Connect sync servers must be configured for filtering so that each has a mutually exclusive set of objects to operate on. You can, for example, scope each server to a particular domain or organizational unit. |

### Microsoft Entra Connect component factors

The following diagram shows a high-level architecture of provisioning engine connecting to a single forest, although multiple forests are supported. This architecture shows how the various components interact with each other.

![Diagram of how the connected directories and Microsoft Entra Connect provisioning engine interact. Includes Connector Space and Metaverse components in an SQL Database.](https://learn.microsoft.com../../wwl-sci/implement-manage-hybrid-identity/media/azure-active-directory-connect-internal.png)

The provisioning engine connects to each Active Directory forest and to Microsoft Entra ID. The process of reading information from each directory is called Import. Export refers to updating the directories from the provisioning engine. Sync evaluates the rules of how the objects will flow inside the provisioning engine.

Microsoft Entra Connect uses the following staging areas, rules, and processes to allow the sync from Active Directory to Microsoft Entra ID:

- **Connector Space (CS)** - Objects from each connected directory (CD), the actual directories, are staged here first before they can be processed by the provisioning engine. Microsoft Entra ID has its own CS and each forest you connect to will have its own CS.
- **Metaverse (MV)** - Objects that need to be synced are created here based on the sync rules. Objects must exist in the MV before they can populate objects and attributes to the other connected directories. There's only one MV.
- **Sync rules** - They decide which objects will be created (projected) or connected (joined) to objects in the MV. The sync rules also decide which attribute values will be copied or transformed to and from the directories.
- **Run profiles** - Bundles the process steps of copying objects and their attribute values according to the sync rules between the staging areas and connected directories.

### Microsoft Entra cloud sync

Microsoft Entra Connect cloud sync is designed to accomplish hybrid identity goals for synchronization of users, groups and contacts to Microsoft Entra ID. The synchronization is accomplished by using the **cloud provisioning agent** instead of the Microsoft Entra Connect application. It can be used alongside Microsoft Entra Connect sync and it provides the following benefits:

- Support for synchronizing to a Microsoft Entra tenant from a multi-forest disconnected Active Directory forest environment: The common scenarios include merger and acquisition. The acquired company's AD forests are isolated from the parent company's AD forests. The companies that have historically had multiple AD forests.
- Simplified installation with light-weight provisioning agents: The agents act as a bridge from AD to Microsoft Entra ID, with all the sync configuration managed in the cloud.
- Multiple provisioning agents can be used to simplify high availability deployments, critical for organizations relying upon password hash synchronization from AD to Microsoft Entra ID.
- Support for large groups with up to fifty-thousand members. It's recommended to use only the OU scoping filter when synchronizing large groups.

![Diagram of the process flow that shows on-premises Active Directory items like users and group being synchronized into the cloud by Cloud Sync.](https://learn.microsoft.com../../wwl-sci/implement-manage-hybrid-identity/media/azure-active-directory-cloud-sync.png)

With Microsoft Entra Connect cloud sync, provisioning from AD to Microsoft Entra ID is orchestrated in Microsoft Online Services. An organization only needs to deploy, in their on-premises or IaaS-hosted environment, a light-weight agent that acts as a bridge between Microsoft Entra ID and AD. The provisioning configuration is stored and managed as part of the service. Reminder that the sync runs every 2 minutes.


## Implement manage password hash synchronization (PHS)

### How password hash synchronization works

Password hash synchronization is one of the sign-in methods used to accomplish hybrid identity. Microsoft Entra Connect synchronizes a hash, of the hash, of a user's password from an on-premises Active Directory instance to a cloud-based Microsoft Entra instance.

![Diagram of Microsoft Entra Connect passes a password hash for a user between on-premises and in the cloud.](https://learn.microsoft.com../../wwl-sci/implement-manage-hybrid-identity/media/password-hash-sync-architecture.png)

Active Directory Domain Services stores passwords in the form of a hash value representation of the actual user password. A hash value is a result of a one-way mathematical function (the hashing algorithm). There's no method to revert the result of a one-way function to the plain text version of a password. To synchronize your password, Microsoft Entra Connect sync extracts your password hash from the on-premises Active Directory instance. Extra security processing is applied to the password hash before it's synchronized to the Microsoft Entra authentication service. Passwords are synchronized on a per-user basis and in chronological order.

The actual data flow of the password hash synchronization process is similar to the synchronization of user data. However, passwords are synchronized more frequently than the standard directory synchronization window for other attributes. The password hash synchronization process runs every 2 minutes. You can't modify the frequency of this process. When you synchronize a password, it overwrites the existing cloud password.

The first time you enable the password hash synchronization feature, it performs an initial synchronization of the passwords of all in-scope users. You can't explicitly define a subset of user passwords that you want to synchronize during the first synchronization. Once the initial synchronization completes, you can set up a **selective password hash synch** for future synchronizations.

If there are multiple connectors, it's possible to disable password hash sync for some connectors but not others. When you change an on-premises password, the updated password is synchronized, most often in a matter of minutes. The password hash synchronization feature automatically retries failed synchronization attempts. If an error occurs during an attempt to synchronize a password, an error is logged in your event viewer.

### Enable password hash synchronization

When you install Microsoft Entra Connect by using the **Express Settings** option, password hash synchronization is automatically enabled. If you use custom settings when you install Microsoft Entra Connect, password hash synchronization is available on the user sign-in page.

### Password hash synchronization and Federal Information Processing standard

If your server is locked down according to Federal Information Processing Standard (FIPS), then MD5 is disabled.

**To enable MD5 for password hash synchronization, perform the following steps:**

1. Go to `%programfiles%\Azure A D Sync\Bin`.
2. Open miiserver.exe.config.
3. Go to the configuration/runtime node at the end of the file.
4. Add the following node: `<enforceFIPSPolicy enabled="false"/>`
5. Save your changes.

For reference, this snippet is what it should look like:

```
   <configuration>
      <runtime>
        <enforceFIPSPolicy enabled="false"/>
      </runtime>
   </configuration>
```

### Using PingFederate

Configure PingFederate with Microsoft Entra Connect to set up federation with the domain you want connected. The following prerequisites are required:

- PingFederate 8.4 or later.
- An TLS/SSL certificate for the federation service name that you intend to use (for example, sts.contoso.com).

After you choose to set up federation by using PingFederate in AD Connect, you're asked to verify the domain you want to federate. Select the domain from the drop-down menu.

Configure PingFederate as the federation server for each federated Azure domain. Then select Export Settings to share this information with your PingFederate administrator. The federation server administrator updates the configuration and provides the PingFederate server URL and port number so that Microsoft Entra Connect can verify the metadata settings.


## Implement manage pass-through authentication (PTA)

Microsoft Entra pass-through authentication allows your users to sign in to both on-premises and cloud-based applications by using the same passwords. Pass-through authentication signs users in by validating their passwords directly against on-premises Active Directory.

### Enable the feature

Enable pass-through authentication through [Microsoft Entra Connect](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/whatis-hybrid-identity).

If you're installing Microsoft Entra Connect for the first time, choose the [custom installation path](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-install-custom). At the **User sign-in** page, choose **Pass-through authentication** as the **Sign On method**. On successful completion, a pass-through authentication agent is installed on the same server as Microsoft Entra Connect. In addition, the pass-through authentication feature is enabled on your tenant.

If you have already installed Microsoft Entra Connect by using the express installation or the custom installation path, select the **Change user sign-in** task on Microsoft Entra Connect, and then select **Next**. Then select **Pass-through authentication** as the sign-in method. On successful completion, a pass-through authentication agent is installed on the same server as Microsoft Entra Connect and the feature is enabled on your tenant.

Important

Pass-through authentication is a tenant-level feature. Turning it on affects the sign-in for users across all the managed domains in your tenant. If you're switching from Active Directory Federation Services (AD FS) to Pass-through authentication, you should wait at least 12 hours before shutting down your AD FS infrastructure. This wait time is to ensure that users can keep signing in to Exchange ActiveSync during the transition.


## Explore pass-through authentication and seamless single sign-on (SSO)

Microsoft Entra seamless single sign-on (seamless SSO) automatically signs in users from their network-connected corporate desktops. Seamless SSO provides your users with easy access to cloud-based applications without needing any other on-premises components.

Seamless SSO can be combined with either the Password Hash Synchronization or Pass-through Authentication sign-in methods. Seamless SSO is not applicable to Active Directory Federation Services (ADFS).

### Key benefits

- Great user experience
  - Users are automatically signed into both on-premises and cloud-based applications.
  - Users don't have to enter their passwords repeatedly.

- Easy to deploy & administer
  - No additional components needed on-premises to make this work.
  - Works with any method of cloud authentication - Password Hash Synchronization or Pass-through Authentication.
  - Can be rolled out to some or all your users using Group Policy.

### How does sign-in on a web browser with Seamless SSO work?

The sign-in flow on a web browser is as follows:

1. The user tries to access a web application (for example, the Outlook Web App - `https://outlook.office365.com/owa/`) from a domain-joined corporate device inside your corporate network.
2. If the user isn't already signed in, the user is redirected to the Microsoft Entra sign-in page.
3. The user types in their user name into the Microsoft Entra sign-in page.
4. Using JavaScript in the background, Microsoft Entra ID challenges the browser, via a 401 Unauthorized response, to provide a Kerberos ticket.
5. The browser, in turn, requests a ticket from Active Directory for the AZUREADSSOACC computer account (which represents Microsoft Entra ID).
6. Active Directory locates the computer account and returns a Kerberos ticket to the browser encrypted with the computer account's secret.
7. The browser forwards the Kerberos ticket it acquired from Active Directory to Microsoft Entra ID.
8. Microsoft Entra ID decrypts the Kerberos ticket, which includes the identity of the user signed into the corporate device, using the previously shared key.
9. After evaluation, Microsoft Entra ID either returns a token back to the application or asks the user to perform additional proofs, such as multifactor authentication.
10. If the user sign-in is successful, the user is able to access the application.

### How does sign-in on a native client with Seamless SSO work?

The sign-in flow on a native client is as follows:

1. The user tries to access a native application (for example, the Outlook client) from a domain-joined corporate device inside your corporate network.
2. If the user isn't already signed in, the native application retrieves the username of the user from the device's Windows session.
3. The app sends the username to Microsoft Entra ID, and retrieves your tenant's WS-Trust MEX endpoint. This WS-Trust endpoint is used exclusively by the Seamless SSO feature, and isn't a general implementation of the WS-Trust protocol on Microsoft Entra ID.
4. The app then queries the WS-Trust MEX endpoint to see if integrated authentication endpoint is available. The integrated authentication endpoint is used exclusively by the Seamless SSO feature.
5. If step 4 succeeds, a Kerberos challenge is issued.
6. If the app is able to retrieve the Kerberos ticket, it forwards it up to Microsoft Entra integrated authentication endpoint.
7. Microsoft Entra ID decrypts the Kerberos ticket and validates it.
8. Microsoft Entra ID signs the user in, and issues a SAML token to the app.
9. The app then submits the SAML token to Microsoft Entra ID OAuth2 token endpoint.
10. Microsoft Entra ID validates the SAML token and issues an access token, a refresh token for the specified resource, and an ID token to the app.
11. The user gets access to the app's resource.


## Implement and manage federation

Federation can use a new or existing on-premises Active Directory farm in Windows Server 2012 R2 (or later), and Microsoft Entra Connect enable users to log into Microsoft Entra resources using their on-premises password.

![Diagram of federation between on-premises and Microsoft Entra ID. Shows users able log into both on-premises and cloud resources with a single shared sign in.](https://learn.microsoft.com../../wwl-sci/implement-manage-hybrid-identity/media/sc300-federation-flow-diagram.png)

Federation is a collection of domains that have established trust. The level of trust varies, but typically includes authentication and almost always includes authorization. A typical federation might include a number of organizations that have established trust for shared access to a set of resources.

You can federate your on-premises environment with Microsoft Entra ID and use this federation for authentication and authorization. This sign-in method ensures that all user authentication occurs on-premises. This method allows administrators to implement more rigorous levels of access control. Federation with AD FS and PingFederate is available.

With federated sign-in, your users can sign in to Microsoft Entra based services with their on-premises passwords. While they're on the corporate network, they don't even have to enter their passwords. By using the federation option with AD FS, you can deploy a new or existing farm with AD FS in Windows Server 2012 R2 or later. If you choose to specify an existing farm, Microsoft Entra Connect configures the trust between your farm and Microsoft Entra ID so that your users can sign in.

### Requirement to deploy federation with AD FS and Microsoft Entra Connect

Deploying to an AD FS farm, you need:

- Local administrator credentials on your federation servers.
- Local administrator credentials on any workgroup servers (not domain-joined) that you intend to deploy the Web Application Proxy role on.
- The machine that you run the wizard on to be able to connect to any other machines that you want to install AD FS or Web Application Proxy on by using Windows Remote Management.

### Set up your federation using Microsoft Entra Connect to connect to an AD FS farm

**Specify the AD FS servers** - Specify the servers where you want to install AD FS. You can add one or more servers, depending on your capacity needs. Before you set up this configuration, join all AD FS servers to Active Directory. This step isn't required for the Web Application Proxy servers. Microsoft recommends installing a single AD FS server for test and pilot deployments. After the initial configuration, you can add and deploy more servers to meet your scaling needs by running Microsoft Entra Connect again.

**Specify the Web Application Proxy servers** - Specify your Web Application Proxy servers. The Web Application Proxy server is deployed in your perimeter network, facing the extranet. It supports authentication requests from the extranet. You can add one or more servers, depending on your capacity needs. After the initial configuration, you can add and deploy more servers to meet your scaling needs by running Microsoft Entra Connect again.

**Specify the service account for the AD FS service** - The AD FS service requires a domain service account to authenticate users and to look up user information in Active Directory. It can support two types of service accounts:

- Group managed service account
- Domain user account

**Select the Microsoft Entra domain that you want to federate** - Use the Microsoft Entra domain page to set up the federation relationship between AD FS and Microsoft Entra ID. Here, you configure AD FS to provide security tokens to Microsoft Entra ID. You also configure Microsoft Entra ID to trust the tokens from this AD FS instance. On this page, you can configure only a single domain in the initial installation. You can configure more domains later by running Microsoft Entra Connect again.

### Microsoft Entra Connect tools to manage your federation

You can complete various AD FS-related tasks in Microsoft Entra Connect with minimal user intervention by using the Microsoft Entra Connect wizard. Even after you've finished installing Microsoft Entra Connect by running the wizard, you can run the wizard again to do other tasks. For example, you can use the wizard to repair the trust with Microsoft 365, federate with Microsoft Entra ID using alternate sign in ID, and add an AD FS Web Application Proxy (WAP) server.

**Repair the trust** - You can use Microsoft Entra Connect to check the current health of the AD FS and Microsoft Entra ID trust and take appropriate actions to repair the trust.

**Federate with Microsoft Entra ID using AlternateID** - It's recommended that the on-premises User Principal Name(UPN) and the cloud User Principal Name are kept the same. If the on-premises UPN uses a non-routable domain (ex. Contoso.local) or can't be changed due to local application dependencies, we recommend setting up alternate sign in ID. Alternate sign in ID allows you to configure a sign-in experience where users can sign in with an attribute other than their UPN, such as mail. The choice for User Principal Name in Microsoft Entra ID Connect defaults to the userPrincipalName attribute in Active Directory. If you choose any other attribute for User Principal Name and are federating using AD FS, then Microsoft Entra Connect will configure AD FS for alternate sign in ID.

**Add a federated domain** - It's easy to add a domain to be federated with Microsoft Entra ID by using Microsoft Entra Connect. Microsoft Entra Connect adds the domain for federation and modifies the claim rules to correctly reflect the issuer when you have multiple domains federated with Microsoft Entra ID.

Along with **Add and AD FS Server** and **Add an AD FS Web Application Proxy server**.

### Device writeback

Device writeback is used to enable device-based conditional Access for ADFS-protected devices. This conditional Access provides extra security and assurance that access to applications is granted only to trusted devices. Device writeback enables this security by synchronizing all devices registered in Azure back to the on-premises Active Directory. When configured during setup, the following operations are performed to prepare the AD forest:

- If they don't exist already, create and configure new containers and objects under: **CN=Device Registration Configuration,CN=Services,CN=Configuration,[forest dn ]**.
- If they don't exist already, create and configure new containers and objects under: **CN=RegisteredDevices,[domain-dn]**. Device objects will be created in this container.
- Set necessary permissions on the Microsoft Entra Connector account, to manage devices on your Active Directory.


## Trouble-shoot synchronization errors

Errors could occur when identity data is synchronized from Windows Server Active Directory (AD DS) to Microsoft Entra ID. This section provides an overview of different types of sync errors, some of the possible scenarios that cause those errors and potential ways to fix the errors. This section includes the common error types, but doesn't cover all the possible errors.

With the latest version of Microsoft Entra Connect, a report of Synchronization Errors is available in the [Azure portal](https://aka.ms/aadconnecthealth) as part of Microsoft Entra Connect Health for sync.

Microsoft Entra Connect performs three types of operations from the directories it keeps in sync: Import, Synchronization, and Export. Errors can take place in all the operations. This section mainly focuses on errors during Export to Microsoft Entra ID.

### Errors during export to Microsoft Entra ID

The following section describes different types of synchronization errors that can occur during the export operation to Microsoft Entra ID using the Microsoft Entra connector. This connector can be identified by the name format being `contoso.onmicrosoft.com`. Errors during export to Microsoft Entra ID indicate that the operation (add, update, delete etc.,) attempted by Microsoft Entra Connect (Sync Engine) on Microsoft Entra directory failed.

### Data mismatch errors

#### InvalidSoftMatch

**Description**

- When Microsoft Entra Connect (sync engine) instructs directory to add or update objects, Microsoft Entra ID matches the incoming object using the **sourceAnchor** attribute to the **immutableId** attribute of objects in Microsoft Entra ID. This match is called a **Hard Match**.
- When Microsoft Entra ID **doesn't find** any object that matches the **immutableId** attribute with the **sourceAnchor** attribute of the incoming object, before provisioning a new object, it falls back to use the ProxyAddresses and UserPrincipalName attributes to find a match. This match is called a **Soft Match**. The Soft Match is designed to match objects already present in Microsoft Entra ID with the new objects being added/updated during synchronization that represent the same entity (users, groups) on premises.
- **InvalidSoftMatch** error occurs when the hard match doesn't find any matching object **AND** soft match finds a matching object but that object has a different value of *immutableId* than the incoming object's *SourceAnchor*, suggesting that the matching object was synchronized with another object from on premises Active Directory.

In other words, in order for the soft match to work, the object to be soft-matched with shouldn't have any value for the *immutableId*. If any object with *immutableId* set with a value is failing the hard-match but satisfying the soft-match criteria, the operation would result in an InvalidSoftMatch synchronization error.

Microsoft Entra directory schema doesn't allow two or more objects to have the same value of the following attributes. (This isn't an exhaustive list.)

- ProxyAddresses
- UserPrincipalName
- onPremisesSecurityIdentifier
- ObjectId

[Microsoft Entra Attribute Duplicate Attribute Resiliency](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency) feature is also being rolled out as the default behavior of Microsoft Entra ID. This will reduce the number of synchronization errors seen by Microsoft Entra Connect (as well as other sync clients) by making Microsoft Entra ID more resilient in the way it handles duplicated ProxyAddresses and UserPrincipalName attributes present in on premises AD environments. This feature doesn't fix the duplication errors. So the data still needs to be fixed. But it allows provisioning of new objects which are otherwise blocked from being provisioned due to duplicated values in Microsoft Entra ID. This will also reduce the number of synchronization errors returned to the synchronization client. If this feature is enabled for your Tenant, you won't see the InvalidSoftMatch synchronization errors seen during provisioning of new objects.

**Example scenarios for InvalidSoftMatch**

- Two or more objects with the same value for the ProxyAddresses attribute exist in on-premises Active Directory. Only one is getting provisioned in Microsoft Entra ID.
- Two or more objects with the same value for the userPrincipalName attribute exist in on-premises Active Directory. Only one is getting provisioned in Microsoft Entra ID.
- An object was added in the on premises Active Directory with the same value of ProxyAddresses attribute as that of an existing object in Microsoft Entra directory. The object added on premises isn't getting provisioned in Microsoft Entra directory.
- An object was added in on premises Active Directory with the same value of userPrincipalName attribute as that of an account in Microsoft Entra ID. The object isn't getting provisioned in Microsoft Entra ID.
- A synced account was moved from Forest A to Forest B. Microsoft Entra Connect (sync engine) was using ObjectGUID attribute to compute the SourceAnchor. After the forest move, the value of the SourceAnchor is different. The new object (from Forest B) is failing to sync with the existing object in Microsoft Entra ID.
- A synced object got accidentally deleted from on premises Active Directory and a new object was created in Active Directory for the same entity (such as user) without deleting the account in Microsoft Entra ID. The new account fails to sync with the existing Microsoft Entra object.
- Microsoft Entra Connect was uninstalled and reinstalled. During the reinstallation, a different attribute was chosen as the SourceAnchor. All the objects that had previously synced stopped syncing with InvalidSoftMatch error.

**Example case:**

1. **Bob Smith** is a synced user in Microsoft Entra ID from on premises Active Directory of *contoso.com*
2. Bob Smith's **UserPrincipalName** is set as **bobs@contoso.com**.
3. **"abcdefghijklmnopqrstuv=="** is the **SourceAnchor** calculated by Microsoft Entra Connect using Bob Smith's **objectGUID** from on premises Active Directory, which is the **immutableId** for Bob Smith in Microsoft Entra ID.
4. Bob also has following values for the **proxyAddresses** attribute:

- smtp: bobs@contoso.com
- smtp: bob.smith@contoso.com
- **smtp: bob@contoso.com**

1. A new user, **Bob Taylor**, is added to the on premises Active Directory.
2. Bob Taylor's **UserPrincipalName** is set as **bobt@contoso.com**.
3. **"abcdefghijkl0123456789==""** is the **sourceAnchor** calculated by Microsoft Entra Connect using Bob Taylor's **objectGUID** from on premises Active Directory. Bob Taylor's object has NOT synced to Microsoft Entra ID yet.
4. Bob Taylor has the following values for the proxyAddresses attribute

- smtp: bobt@contoso.com
- smtp: bob.taylor@contoso.com
- **smtp: bob@contoso.com**

1. During sync, Microsoft Entra Connect will recognize the addition of Bob Taylor in on premises Active Directory and ask Microsoft Entra ID to make the same change.
2. Microsoft Entra ID will first perform hard match. That is, it will search if there's any object with the immutableId equal to "abcdefghijkl0123456789==". Hard Match will fail, since no other object in Microsoft Entra ID will have that immutableId.
3. Microsoft Entra ID will then attempt to soft-match Bob Taylor. That is, it will search if there's any object with proxyAddresses equal to the three values, including smtp: bob@contoso.com
4. Microsoft Entra ID will find Bob Smith's object to match the soft-match criteria. But this object has the value of immutableId = "abcdefghijklmnopqrstuv==". which indicates this object was synced from another object from on premises Active Directory. Thus, Microsoft Entra ID can't soft-match these objects and results in an **InvalidSoftMatch** sync error.

**How to fix InvalidSoftMatch error**

The most common reason for the InvalidSoftMatch error is two objects with different SourceAnchor (immutableId) have the same value for the ProxyAddresses and/or UserPrincipalName attributes, which are used during the soft-match process on Microsoft Entra ID. In order to fix the Invalid Soft-Match

1. Identify the duplicated proxyAddresses, userPrincipalName, or other attribute value that's causing the error. Also identify which two (or more) objects are involved in the conflict. The report generated by [Microsoft Entra Connect Health for sync](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-health-sync) can help you identify the two objects.
2. Identify which object should continue to have the duplicated value and which object shouldn't.
3. Remove the duplicated value from the object that shouldn't have that value. You should make the change in the directory where the object is sourced from. In some cases, you need to delete one of the objects in conflict.
4. If you made the change in the on premises AD, let Microsoft Entra Connect sync the change.

Sync error reports within Microsoft Entra Connect Health for sync are updated every 30 minutes and include the errors from the latest synchronization attempt.

Note

ImmutableId, by definition, shouldn't change in the lifetime of the object. If Microsoft Entra Connect wasn't configured with some of the scenarios in mind from the above list, you could end up in a situation where Microsoft Entra Connect calculates a different value of the SourceAnchor for the AD object that represents the same entity (same user/group/contact etc.,) that has an existing Microsoft Entra Object that you wish to continue using.

#### ObjectTypeMismatch

**Description**

When Microsoft Entra ID attempts to soft match two objects, it's possible that two objects of different "object type" (such as User, Group, Contact etc.) have the same values for the attributes used to perform the soft-match. As duplication of these attributes isn't permitted in Microsoft Entra, the operation can result in "ObjectTypeMismatch" synchronization error.

**Example scenarios for ObjectTypeMismatch error**

- A mail enabled security group is created in Microsoft 365. Admin adds a new user or contact in on premises AD (that's not synchronized to Microsoft Entra ID yet) with the same value for the ProxyAddresses attribute as that of the Microsoft 365 group.

**Example case**

1. Admin creates a new mail enabled security group in Microsoft 365 for the Tax department and provides an email address as tax@contoso.com. This group is assigned the ProxyAddresses attribute value of **smtp: tax@contoso.com**
2. A new user joins Contoso.com and an account is created for the user on premises with the proxyAddress as **smtp: tax@contoso.com**
3. When Microsoft Entra Connect will sync the new user account, it will get the "ObjectTypeMismatch" error.

**How to fix ObjectTypeMismatch error**

The most common reason for the ObjectTypeMismatch error is two objects of different type (User, Group, Contact etc.) have the same value for the ProxyAddresses attribute. In order to fix the ObjectTypeMismatch:

1. Identify the duplicated proxyAddresses (or other attribute) value that's causing the error. Also identify which two (or more) objects are involved in the conflict. The report generated by [Microsoft Entra Connect Health for sync](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-health-sync) can help you identify the two objects.
2. Identify which object should continue to have the duplicated value and which object shouldn't.
3. Remove the duplicated value from the object that shouldn't have that value. You should make the change in the directory where the object is sourced from. In some cases, you need to delete one of the objects in conflict.
4. If you made the change in the on premises AD, let Microsoft Entra Connect sync the change. Sync error report within Microsoft Entra Connect Health for sync gets updated every 30 minutes and includes the errors from the latest synchronization attempt.

### Duplicate attributes

#### AttributeValueMustBeUnique

#### Description

Microsoft Entra schema doesn't allow two or more objects to have the same value of the following attributes. That is each object in Microsoft Entra ID is forced to have a unique value of these attributes at a given instance.

- ProxyAddresses
- UserPrincipalName

If Microsoft Entra Connect attempts to add a new object or update an existing object with a value for the above attributes that is already assigned to another object in Microsoft Entra ID, the operation results in the "AttributeValueMustBeUnique" sync error.

#### Possible scenarios:

Duplicate value is assigned to an already synced object, which conflicts with another synced object.

#### Example case:

1. **Bob Smith** is a synced user in Microsoft Entra ID from on premises Active Directory of contoso.com
2. Bob Smith's **UserPrincipalName** on premises is set as **bobs@contoso.com**.
3. Bob also has following values for the **proxyAddresses** attribute:

- smtp: bobs@contoso.com
- smtp: bob.smith@contoso.com
- **smtp: bob@contoso.com**

1. A new user, **Bob Taylor**, is added to the on premises Active Directory.
2. Bob Taylor's **UserPrincipalName** is set as **bobt@contoso.com**.
3. **Bob Taylor** has the following values for the **ProxyAddresses** attribute i. smtp: bobt@contoso.com ii. smtp: bob.taylor@contoso.com
4. Bob Taylor's object is synchronized with Microsoft Entra ID successfully.
5. Admin decided to update Bob Taylor's **ProxyAddresses** attribute with the following value: i. **smtp: bob@contoso.com**
6. Microsoft Entra ID will attempt to update Bob Taylor's object in Microsoft Entra ID with the above value, but that operation will fail as that ProxyAddresses value is already assigned to Bob Smith, resulting in "AttributeValueMustBeUnique" error.

#### How to fix AttributeValueMustBeUnique error

The most common reason for the AttributeValueMustBeUnique error is two objects with different SourceAnchor (immutableId) have the same value for the ProxyAddresses and/or UserPrincipalName attributes. In order to fix AttributeValueMustBeUnique error

1. Identify the duplicated proxyAddresses, userPrincipalName or other attribute value that's causing the error. Also identify which two (or more) objects are involved in the conflict. The report generated by [Microsoft Entra Connect Health for sync](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-health-sync) can help you identify the two objects.
2. Identify which object should continue to have the duplicated value and which object shouldn't.
3. Remove the duplicated value from the object that shouldn't have that value. You should make the change in the directory where the object is sourced from. In some cases, you need to delete one of the objects in conflict.
4. If you made the change in the on premises AD, let Microsoft Entra Connect sync the change for the error to get fixed.

### Data validation failures

#### IdentityDataValidationFailed

#### Description

Microsoft Entra ID enforces various restrictions on the data itself before allowing that data to be written into the directory. These restrictions are to ensure that end users get the best possible experiences while using the applications that depend on this data.

#### Scenarios

The UserPrincipalName attribute value has invalid/unsupported characters. b. The UserPrincipalName attribute doesn't follow the required format.

#### How to fix IdentityDataValidationFailed error

Ensure that the userPrincipalName attribute has supported characters and required format.

#### FederatedDomainChangeError

#### Description

This case results in a **"FederatedDomainChangeError"** sync error when the suffix of a user's UserPrincipalName is changed from one federated domain to another federated domain.

#### Scenarios

For a synchronized user, the UserPrincipalName suffix was changed from one federated domain to another federated domain on premises. For example, *UserPrincipalName = bob@contoso.com* was changed to *UserPrincipalName = bob@fabrikam.com*.

#### Example

1. Bob Smith, an account for Contoso.com, gets added as a new user in Active Directory with the UserPrincipalName bob@contoso.com
2. Bob moves to a different division of Contoso.com called Fabrikam.com and their UserPrincipalName is changed to bob@fabrikam.com
3. Both contoso.com and fabrikam.com domains are federated domains with Microsoft Entra ID.
4. Bob's userPrincipalName doesn't get updated and results in a "FederatedDomainChangeError" sync error.

### LargeObject

#### Description

When an attribute exceeds the allowed size limit, length limit or count limit set by Microsoft Entra schema, the synchronization operation results in the **LargeObject** or **ExceededAllowedLength** sync error. Typically this error occurs for the following attributes

- userCertificate
- userSMIMECertificate
- thumbnailPhoto
- proxyAddresses

#### Possible scenarios

1. Bob's userCertificate attribute is storing too many certificates assigned to Bob. These include older, expired certificates. The hard limit is 15 certificates.
2. Bob's userSMIMECertificate attribute is storing too many certificates assigned to Bob. These include older, expired certificates. The hard limit is 15 certificates.
3. Bob's thumbnailPhoto set in Active Directory is too large to be synced in Microsoft Entra ID.
4. During automatic population of the ProxyAddresses attribute in Active Directory, an object has too many ProxyAddresses assigned.

#### How to fix

Ensure that the attribute causing the error is within the allowed limitation.

### Admin role conflict

#### Description

An **Existing Admin Role Conflict** will occur on a user object during synchronization when that user object has:

- administrative permissions and
- the same UserPrincipalName as an existing Microsoft Entra object

Microsoft Entra Connect isn't allowed to soft-match a user object from on-premises AD with a user object in Microsoft Entra ID that has an administrative role assigned to it.

#### How to fix

To resolve this issue do the following:

1. Remove the Microsoft Entra account (owner) from all admin roles.
2. **Hard Delete** the Quarantined object in the cloud.
3. The next sync cycle will take care of soft-matching the on-premises user to the cloud account (since the cloud user is now no longer a global GA).
4. Restore the role memberships for the owner.

Note

You can assign the administrative role to the existing user object again after the soft-match between the on-premises user object and the Microsoft Entra user object has completed.


## Implement Microsoft Entra Connect Health

Microsoft Entra Connect Health provides monitoring of your on-premises identity infrastructure. It enables you to maintain a reliable connection to Microsoft 365 and Microsoft Online Services. This reliability is achieved by providing monitoring capabilities for your key identity components. Also, it makes the key data points about these components easily accessible.

The information is presented in the [Microsoft Entra Connect Health portal](https://aka.ms/aadconnecthealth). Use the Microsoft Entra Connect Health portal to view alerts, performance monitoring, usage analytics, and other information. Microsoft Entra Connect Health enables the single lens of health for your key identity components in one place.

![Diagram of Microsoft Entra Connect Health. Shows how Microsoft Entra Connect is maintained.](https://learn.microsoft.com../../wwl-sci/implement-manage-hybrid-identity/media/azure-active-directory-connect-health-2.png)

Using the Microsoft Entra Connect Health feature requires a Microsoft Entra ID Premium P1 license.

### Microsoft Entra Connect Health agent installation

This section provides instructions for installing and configuring the Microsoft Entra Connect Health agents.

### Requirements

- Microsoft Entra ID Premium is installed.
- You're a global administrator in Microsoft Entra ID.
- The Microsoft Entra Connect Health agent is installed on each targeted server.
- The Azure service endpoints have outbound connectivity.
- Outbound connectivity is based on IP addresses.
- TLS inspection for outbound traffic is filtered or disabled.
- Firewall ports on the server are running the agent.
  - The agent requires the following firewall ports to be open so that it can communicate with the Microsoft Entra Connect Health service endpoints:
    - TCP port 443
    - TCP port 5671

  - The latest version of the agent doesn't require port 5671. Upgrade to the latest version so that only port 443 is required.

- PowerShell version 4.0 or newer is installed.
- FIPS (Federal Information Processing Standard) is disabled.

### Install the agent

Download and install the Microsoft Entra Connect Health agent from the Download Center.

### Install the agent for Active Directory Federation Service

Note

Your Active Directory Federation Server (AD FS) server should be different from your Sync server. Don't install the AD FS agent on your Sync server.

Before you install the agent, make sure your AD FS server host name is unique and isn't present in the AD FS service. To start the agent installation, double-click the *.exe* file that you downloaded. In the first window, select **Install**.

After the installation finishes, select **Configure Now**.

A PowerShell window opens to start the agent registration process. When you're prompted, sign in by using a Microsoft Entra ID account that has permissions to register the agent. By default, the global admin account has permissions.

After you sign in, PowerShell continues. When it finishes, you can close PowerShell. The configuration is complete.

At this point, the agent services should start automatically to allow the agent to securely upload the required data to the cloud service.

If you haven't met all of the prerequisites, warnings appear in the PowerShell window. Be sure to complete the requirements before you install the agent. The following screenshot shows an example of these warnings.

To verify that the agent was installed, look for the following services on the server. If you completed the configuration, they should already be running. Otherwise, they're stopped until the configuration is complete.

- Microsoft Entra Connect Health AD FS Diagnostics Service
- Microsoft Entra Connect Health AD FS Insights Service
- Microsoft Entra Connect Health AD FS Monitoring Service

### Install the agent for Sync

The Microsoft Entra Connect Health agent for Sync is installed automatically in the latest version of Microsoft Entra Connect. To use Microsoft Entra Connect for Sync, download the latest version of Microsoft Entra Connect and install it.

To verify the agent has been installed, look for the following services on the server. If you completed the configuration, the services should already be running. Otherwise, the services are stopped until the configuration is complete.

- Microsoft Entra Connect Health Sync Insights Service
- Microsoft Entra Connect Health Sync Monitoring Service

Note

Remember that you must have Microsoft Entra ID Premium to use Microsoft Entra Connect Health. If you don't have Microsoft Entra ID Premium, you can't complete the configuration in the Azure portal.


## Manage Microsoft Entra Health

This section describes various operations you can perform by using Microsoft Entra Connect Health.

### Enable email notifications

You can configure the Microsoft Entra Connect Health service to send email notifications when alerts indicate that your identity infrastructure isn't healthy. This occurs when an alert is generated, and when it's resolved.

Note

Email notifications are enabled by default.

#### To enable Microsoft Entra Connect Health email notifications

1. Open the **Alerts** dialog for the service for which you want to receive email notification.
2. From the action bar, select **Notification Settings**.
3. At the email notification switch, select **ON**.
4. Select the check box if you want all global administrators to receive email notifications.
5. If you want to receive email notifications at any other email addresses, specify them in the **Additional Email Recipients** box. To remove an email address from this list, select the entry and select **Delete**.
6. To finalize the changes, select **Save**. Changes take effect only after you save.

Note

When there are issues processing synchronization requests in our back-end service, this service sends a notification email with the details of the error to the administrative contact email address(es) of your tenant. We heard feedback from customers that in certain cases the volume of these messages is prohibitively large so we're changing the way we send these messages.

Instead of sending a message for every sync error every time it occurs we'll send out a daily digest of all errors the back-end service has returned. This enables customers to process these errors in a more efficient manner and reduces the number of duplicate error messages.

### Delete a server or service instance

Note

Microsoft Entra ID premium license is required for the deletion steps.

In some instances, you might want to remove a server from being monitored. Here's what you need to know to remove a server from the Microsoft Entra Connect Health service.

When you're deleting a server, be aware of the following:

- This action stops collecting any further data from that server. This server is removed from the monitoring service. After this action, you aren't able to view new alerts, monitoring, or usage analytics data for this server.
- This action doesn't uninstall the Health Agent from your server. If you have not uninstalled the Health Agent before performing this step, you might see errors related to the Health Agent on the server.
- This action doesn't delete the data already collected from this server. That data is deleted in accordance with the Azure data retention policy.
- After performing this action, if you want to start monitoring the same server again, you must uninstall and reinstall the Health Agent on this server.

#### Delete a server from the Microsoft Entra Connect Health service

Note

Microsoft Entra ID premium license is required for the deletion steps.

Microsoft Entra Connect Health for Active Directory Federation Services (AD FS) and Microsoft Entra Connect (Sync):

1. Open the **Server** screen from the **Server List** dialog by selecting the server name to be removed.
2. On the **Server** screen, from the action bar, select **Delete**.

1. Confirm by typing the server name in the confirmation box.
2. Select **Delete**.

Microsoft Entra Connect Health for Microsoft Entra Domain Services:

1. Open the **Domain Controllers** dashboard.
2. Select the domain controller to be removed.
3. From the action bar, select **Delete Selected**.
4. Confirm the action to delete the server.
5. Select **Delete**.

#### Delete a service instance from Microsoft Entra Connect Health service

In some instances, you might want to remove a service instance. Here's what you need to know to remove a service instance from the Microsoft Entra Connect Health service.

When you're deleting a service instance, be aware of the following:

- This action removes the current service instance from the monitoring service.
- This action doesn't uninstall or remove the Health Agent from any of the servers that were monitored as part of this service instance. If you haven't uninstalled the Health Agent before performing this step, you might see errors related to the Health Agent on the servers.
- All data from this service instance is deleted in accordance with the Azure data retention policy.
- After performing this action, if you want to start monitoring the service, uninstall and reinstall the Health Agent on all the servers. After performing this action, if you want to start monitoring the same server again, uninstall, reinstall, and register the Health Agent on that server.

#### To delete a service instance from the Microsoft Entra Connect Health service

1. Open the **Service** screen from the **Service List** dialog by selecting the service identifier (farm name) that you want to remove.
2. On the **Service** screen, from the action bar, select **Delete**.

1. Confirm by typing the service name in the confirmation box (for example: sts.contoso.com).
2. Select **Delete**.

### Manage access with Azure Role Based Access Control

Azure role-based access control (Azure RBAC) for Microsoft Entra Connect Health provides access to users and groups. Azure RBAC assigns roles to the intended users and groups, and provides a mechanism to share administrator duty within your directory. Always thing of the principle of least privilege when assigning access.

#### Roles

Microsoft Entra Connect Health supports the following built-in roles:

| **Role** | **Permissions** |
|---|---|
| Owner | Owners can *manage access* (for example, assign a role to a user or group), *view all information* (for example, view alerts) from the portal, and *change settings* (for example, email notifications) within Microsoft Entra Connect Health. By default, Microsoft Entra global administrators are assigned this role, and this can't be changed. |
| Contributor | Contributors can *view all information* (for example, view alerts) from the portal, and *change settings* (for example, email notifications) within Microsoft Entra Connect Health. |
| Reader | Readers can *view all information* (for example, view alerts) from the portal within Microsoft Entra Connect Health. |

All other roles (such as User Access Administrators or DevTest Labs Users) have no impact to access within Microsoft Entra Connect Health, even if the roles are available in the portal experience.

#### Access scope

Microsoft Entra Connect Health supports managing access at two levels:

- **All service instances**: This is the recommended path in most cases. It controls access for all service instances (for example, an AD FS farm) across all role types that are being monitored by Microsoft Entra Connect Health.
- **Service instance**: In some cases, you might need to segregate access based on role types or by a service instance. In this case, you can manage access at the service instance level.

Permission is granted if an end user has access either at the directory or service instance level.

#### Allow users or groups access to Microsoft Entra Connect Health

The following steps show how to allow access.

**Step 1: Select the appropriate access scope**

To allow a user access at the *all service instances* level within Microsoft Entra Connect Health, open the main screen in Microsoft Entra Connect Health.

**Step 2: Add users and groups, and assign roles**

1. From the **Configure** section, select **Users**.

1. Select **Add**.
2. In the **Select a role** pane, select a role (for example, **Owner**).

1. Type the name or identifier of the targeted user or group. You can select one or more users or groups at the same time. select **Select**.

1. Select **OK**.
2. After the role assignment is complete, the users and groups appear in the list.

Now the listed users and groups have access, according to their assigned roles.

- The Invite Users feature isn't supported within Microsoft Entra Connect Health.

**Step 3: Share the location with users or groups**

1. After you assign permissions, a user can access Microsoft Entra Connect Health by going [here](https://aka.ms/aadconnecthealth).
2. On the screen, the user can pin the screen, or different parts of it, to the dashboard. Select the **Pin to dashboard** icon.

#### Remove users or groups

You can remove a user or a group added to Microsoft Entra Connect Health and Azure RBAC. Select the user or group with the secondary action, and select **Remove**.

### Diagnose and remediate duplicated attribute sync errors

### Overview

Taking one step farther to highlight sync errors, Microsoft Entra Connect Health introduces self-service remediation. It troubleshoots duplicated attribute sync errors and fixes objects that are orphaned from Microsoft Entra ID. The diagnosis feature has these benefits:

- It provides a diagnostic procedure that narrows down duplicated attribute sync errors. And it gives specific fixes.
- It applies a fix for dedicated scenarios from Microsoft Entra ID to resolve the error in a single step.
- No upgrade or configuration is required to enable this feature.

### Problems

#### A common scenario

When **QuarantinedAttributeValueMustBeUnique** and **AttributeValueMustBeUnique** sync errors happen, it's common to see a **UserPrincipalName** or **Proxy Addresses** conflict in Microsoft Entra ID. You might solve the sync errors by updating the conflicting source object from the on-premises side. The sync error will be resolved after the next sync. For example, this image indicates that two users have a conflict of their **UserPrincipalName**. Both are **Joe.J@contoso.com**. The conflicting objects are quarantined in Microsoft Entra ID.

![Diagram of the Diagnose sync error common scenarios. Most likely place to see errors.](https://learn.microsoft.com../../wwl-sci/implement-manage-hybrid-identity/media/identity-fix-common-case.png)

#### Orphaned object scenario

Occasionally, you might find that an existing user loses the **Source Anchor**. The deletion of the source object happened in on-premises Active Directory. But the change of deletion signal never got synchronized to Microsoft Entra ID. This loss happens for reasons like sync engine issues or domain migration. When the same object gets restored or recreated, logically, an existing user should be the user to sync from the **Source Anchor**.

When an existing user is a cloud-only object, you can also see the conflicting user synchronized to Microsoft Entra ID. The user can't be matched in sync to the existing object. There's no direct way to remap the **Source Anchor**.

As an example, the existing object in Microsoft Entra ID preserves the license of Joe. A newly synchronized object with a different **Source Anchor** occurs in a duplicated attribute state in Microsoft Entra ID. Changes for Joe in on-premises Active Directory won't be applied to Joe’s original user (existing object) in Microsoft Entra ID.

### Diagnostic and troubleshooting steps in Connect Health

The diagnose feature supports user objects with the following duplicated attributes:

| **Attribute name** | **Synchronization error types** |
|---|---|
| UserPrincipalName | QuarantinedAttributeValueMustBeUnique or AttributeValueMustBeUnique |
| ProxyAddresses | QuarantinedAttributeValueMustBeUnique or AttributeValueMustBeUnique |
| SipProxyAddress | AttributeValueMustBeUnique |
| OnPremiseSecurityIdentifier | AttributeValueMustBeUnique |

Important

To access this feature a **Contributor** permission from Azure RBAC, is required.

Follow the steps from the Azure portal to narrow down the sync error details and provide more specific solutions:

![Digram of the Sync error diagnosis steps. Use these steps to reach a resolution.](https://learn.microsoft.com../../wwl-sci/implement-manage-hybrid-identity/media/identity-fix-steps.png)

From the Azure portal, take a few steps to identify specific fixable scenarios:

1. Check the **Diagnose status** column. The status shows if there's a possible way to fix a sync error directly from Microsoft Entra ID. In other words, a troubleshooting flow exists that can narrow down the error case and potentially fix it.

| **Status** | **What does it mean?** |
|---|---|
| Not Started | You haven't visited this diagnosis process. Depending on the diagnostic result, there's a potential way to fix the sync error directly from the portal. |
| Manual Fix Required | The error doesn't fit the criteria of available fixes from the portal. Either conflicting object types aren't users, or you already went through the diagnostic steps, and no fix resolution was available from the portal. In the latter case, a fix from the on-premises side is still one of the solutions. |
| Pending Sync | A fix was applied. The portal is waiting for the next sync cycle to clear the error. |

1. Select the **Diagnose** button under the error details. You'll answer a few questions and identify the sync error details. Answers to the questions help identify an orphaned object case.
2. If a **Close** button appears at the end of the diagnostics, there's no quick fix available from the portal based on your answers. Refer to the solution shown in the last step. Fixes from on-premises are still the solutions. Select the **Close** button. The status of the current sync error switches to **Manual fix required**. The status stays during the current sync cycle.
3. After an orphaned object case is identified, you can fix the duplicated attributes sync errors directly from the portal. To trigger the process, select the **Apply Fix** button. The status of the current sync error updates to **Pending sync**.
4. After the next sync cycle, the error should be removed from the list.


## Module assessment

Choose the best response for each of the questions below.

### Check your knowledge


## Summary and resources

Now that you reviewed this module, you're able to:

- Plan, design, and implement Microsoft Entra Directory Connect (AADC), including password hash synchronization (PHS), pass-through authentication (PTA), seamless single-sign-on (Seamless SSO), and federation
- Manage Microsoft Entra Directory Connect (AADC)
- Manage password hash synchronization (PHS)
- Manage pass-through authentication (PTA)
- Manage seamless single-sign-on (Seamless SSO)
- Manage federation excluding manual ADFS deployments
- Troubleshoot synchronization errors
- Implement and manage Microsoft Entra Directory Connect Health

### Resources

- [What is hybrid identity with Microsoft Entra ID](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/whatis-hybrid-identity)
- [Integrate a single AD forest using password hash](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/tutorial-password-hash-sync)
- [Hybrid Identity documentation](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/)
- [Microsoft Entra Connect - Configure AD DS Connector Account permission](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-configure-ad-ds-connector-account)
