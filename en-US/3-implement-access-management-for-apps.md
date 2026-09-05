# Implement access management for apps

> SC-300 — learning path 3/4
> https://learn.microsoft.com/en-us/training/paths/implement-access-management-for-apps/

## Modules

- **Plan and design the integration of enterprise apps for SSO** (10 units)
- **Implement and monitor the integration of enterprise apps for SSO** (10 units)
- **Implement app registration** (11 units)
- **Register apps using Microsoft Entra ID** (9 units)


---

# Plan and design the integration of enterprise apps for SSO

_https://learn.microsoft.com/en-us/training/modules/plan-design-integration-of-enterprise-apps-for-sso/_


## Introduction

In this module, you discover apps used within your environment. Then, you design and implement access management and app management roles. In addition, you configure preintegrated (gallery) SaaS apps.

### Learning objectives

In this module, you:

- Discover apps by using Defender for Cloud Apps app discovery.
- Design and implement access management for apps.
- Design and implement app management roles.
- Configure preintegrated (gallery) SaaS apps.
- Explore application connectors and OAuth apps.

### Prerequisites

- Solid usage experience of admin centers within the Microsoft Cloud.
- Experience with using applications in the cloud


## Discover apps by using Microsoft Defender for Cloud Apps and Active Directory Federation Services app report

To start learning how to protect cloud apps, you first need to learn what Cloud Access Security Broker (CASB) is. Then, learn what the Microsoft implementation of CASB is.

**CASB** - Cloud Access Security Broker - An on-premises or cloud-based security policy enforcement point, placed between cloud service consumers and cloud service providers to combine and interject enterprise security policies as the cloud-based resources are accessed.

**MDCA** - Microsoft Defender for Cloud Apps - The Microsoft implementation of a CASB service to protect data, services, and applications with enterprise policies. It provides supplemental reporting and analytics services

### Microsoft Defender for Cloud Apps

Moving to the cloud increases flexibility for employees and IT alike. However, it also introduces new challenges and complexities for keeping your organization secure. To get the full benefit of cloud apps and services, an IT team must find the right balance of supporting access while maintaining control to protect critical data. Microsoft Defender for Cloud Apps (MDCA) is a Cloud Access Security Broker (CASB) that supports various deployment modes, including log collection, API connectors, and reverse proxy. It provides rich visibility, control over data travel, and sophisticated analytics to identify and combat cyberthreats across all your Microsoft and third-party cloud services. Microsoft Defender for Cloud Apps natively integrates with leading Microsoft solutions and is designed with security professionals in mind. It provides simple deployment, centralized management, and innovative automation capabilities. Microsoft Defender for Cloud Apps is a comprehensive cross-SaaS solution bringing deep visibility, strong data controls, and enhanced threat protection to your cloud apps. Cloud Discovery, a feature of Microsoft Defender for Cloud Apps, enables you to gain visibility into Shadow IT by discovering cloud apps in use.

#### Architecture

Microsoft Defender for Cloud Apps integrates visibility with your cloud by:

- Using Cloud Discovery to map and identify your cloud environment and the cloud apps your organization is using.
- Sanctioning and de-authorizing apps in your cloud.
- Using easy-to-deploy app connectors that take advantage of provider APIs, for visibility and governance of apps that you connect to.
- Using Conditional Access App Control protection to get real-time visibility and control over access and activities within your cloud apps.
- Helping you have continuous control by setting and continually fine-tuning policies.  ![Diagram of Microsoft Defender for Cloud Apps architecture. How are apps found and managed.](https://learn.microsoft.com../../wwl-sci/plan-design-integration-of-enterprise-apps-for-sso/media/proxy-architecture.png)

#### Cloud Discovery

Cloud Discovery uses your traffic logs to dynamically discover and analyze the cloud apps your organization is using. To create a snapshot report of your organization's cloud use, manually upload log files from your firewalls or proxies for analysis. To set up continuous reports, use Microsoft Defender for Cloud Apps log collectors to periodically forward your logs.

**Review the Cloud Discovery Dashboard**

The admin should review the information in the Cloud Discovery Dashboard first, to get a general picture of your Cloud Discovery apps. Look for:

- First look at the overall cloud app use in your organization in the High-level usage overview.
- Then, dive one level deeper to see which are the top categories used in your org for each of the different use parameters. You can see how much of this usage is by Sanction apps.
- Go even deeper and see all the apps in a specific category in the Discovered apps tab.
- You can see the top users and source IP addresses to identify which users are the most dominant users of cloud apps in your organization.
- Check how the discovered apps spread according to geographic location (according to their HQ) in the App Headquarters map.
- Finally, don't forget to review the risk score of the discovered app in the App risk overview. Check the discovery alerts status to see how many open alerts should you investigate.

**Filtering Discovered Apps**

- **App tag** - Select whether the app was sanctioned or unsanctioned or not tagged. Additionally, you can create a custom tag for your app and then use it to filter for specific types of apps.
- **Apps and domains** - Enables you to search for specific apps or apps used in specific domains.
- **Categories** - The categories filter, located on the left of the page, enables you to search for types of apps according to app categories. Example categories include social network apps, cloud storage apps, and hosting services. You can select multiple categories at a time, or a single category, then apply the basic and advanced filters on top.
- **Compliance risk factor** - Search for a specific standards, certification, and compliance that the app might comply with (HIPAA, ISO 27001, SOC 2, PCI-DSS, and more.).
- **General risk factor** - Search for general risk factors such as consumer popularity, data center locale, and more.
- **Risk score** - Enables apps to filter by risk score so that you can focus on, for example, reviewing only highly risky apps. You can also override the risk score set by Microsoft Defender for Cloud Apps. For more information, see Working with the risk score.
- **Security risk factor** - Enables you to filter based on specific security measures (such as Encryption at rest, multifactor authentication, etc.).
- **Usage** - Enables filtering based on the usage statistics of this app. Usage such as apps with less than or more than a specified number of data uploads, apps with more than or less than a specified number of Users.
- **Legal risk factor** - Provides the ability to filter based on all the regulations and policies that are in-place to ensure data protection and privacy of the app's users. Examples include safe-customer-data ready cloud apps, DMCA, and data retention policy.

#### Sanctioning and unsanctioning an app

You can use Microsoft Defender for Cloud Apps to sanction or unsanction apps in your organization by using the *Cloud app catalog*. The Microsoft team of analysts has an extensive and continuously growing catalog of more than 16,000 cloud apps that are ranked and scored based on industry standards. Use the Cloud app catalog to rate the risk for your cloud apps based on regulatory certifications, industry standards, and best practices. Then, customize the scores and weights of various parameters to your organization's needs. Based on these scores, Microsoft Defender for Cloud Apps monitors how risky an app is. Scoring is based on more than 80 risk factors that might affect your environment.

### Active Directory Federation Services

If you have an on-premises directory that contains user accounts, you likely have many applications to which users authenticate. Each of these apps is configured for users to access using their identities. Users can also authenticate directly with your on-premises Active Directory. Active Directory Federation Services (AD FS) is a standards-based on-premises identity service. AD FS extends the ability to use single-sign-on (SSO) functionality between trusted business partners without requiring users to sign in separately to each application - federation. Many organizations have software as a service (SaaS) or custom line-of-business (LOB) apps federated directly to AD FS, alongside Microsoft 365 and Microsoft Entra ID based apps.

To increase application security, your goal is to have a single set of access controls and policies across your on-premises and cloud environments.

Many organizations use AD FS to provide SSO to cloud applications. Moving your AD FS applications to Microsoft Entra ID for authentication provides significant benefits, especially in terms of cost management, risk management, productivity, compliance, and governance. But understanding which applications are compatible with Microsoft Entra ID and identifying specific migration steps can be time consuming.

Sometimes the organization might be using alternate on-premises or cloud identity providers, such as SiteMinder, Oracle Access Manager, PingFederate, etc. Most of them are on-premises installations. Some cloud providers, such as Okta and OneLogin, offer similar services.

The AD FS application activity report in the Azure portal enables you to quickly identify which applications you can migrate to Microsoft Entra ID. It assesses all AD FS applications for compatibility with Microsoft Entra ID, checks for any issues, and gives guidance on preparing individual applications for migration. With the AD FS application activity report, you can discover AD FS applications and scope your migration. The AD FS application activity report lists all AD FS applications in your organization that have had an active user logged in within the last 30 days. The activity data is available to users who are assigned any of these admin roles: global reader / administrator, report reader, security reader, application administrator, or cloud application administrator.

### Types of apps to migrate

Migrating all your application authentication to Microsoft Entra ID is optimal, as it gives you a single control plane for identity and access management.

There are two types of applications to migrate:

1. SaaS applications, which are procured by the organization.
2. Line-of-business applications, which are developed by the organization and not meant to be used by other companies. Your applications might use modern or legacy protocols for authentication. Most SaaS applications use modern authentication protocols and provide guidance on how to enable SSO. Consider first migrating applications that use modern authentication protocols (such as SAML and Open ID Connect). These apps can be reconfigured to authenticate with Microsoft Entra ID via either a built-in connector in our App Gallery, or by registering the application in Microsoft Entra ID. Integrate apps using older protocols by using [Application Proxy](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/what-is-application-proxy) and/or Microsoft Entra Domain Services.

### Discover AD FS applications that can be migrated

The AD FS application activity report is available in the Azure portal under Microsoft Entra **Usage and insights** reporting. The AD FS application activity report analyzes each AD FS application to determine whether it can be migrated as-is or after review.

1. Sign in to the Azure portal with an admin role that has access to AD FS application activity data (administrator, report reader, security reader, application administrator, or cloud application administrator).
2. Select **Microsoft Entra ID**, and then select **Enterprise applications**.
3. Under **Activity**, select **Usage and insights**, and then select **AD FS application activity** to open a list of all AD FS applications in your organization.
4. For each application in the AD FS application activity list, view the **Migration status**:

- **Ready to migrate** means the AD FS application configuration is fully supported in Microsoft Entra ID and can be migrated as-is.
- **Needs review** means some of the application's settings can be migrated to Microsoft Entra ID, but you'll need to review the settings that can't be migrated as-is.
- **Additional steps required** means Microsoft Entra ID doesn't support some of the application's settings, so the application can’t be migrated in its current state.


## Configure connectors to apps

App connectors use the APIs of app providers to enable greater visibility and control by Microsoft Defender for Cloud Apps over the apps you connect to. Microsoft Defender for Cloud Apps (MDCA) uses the APIs provided by the cloud provider. All communication between Defender for Cloud Apps and connected apps is encrypted using HTTPS. Each service has its own framework and API limitations such as throttling, API limits, dynamic time-shifting API windows, and others. Microsoft Defender for Cloud Apps worked with the services to optimize the usage of the APIs and to provide the best performance. Taking into account different limitations services impose on the APIs, the Defender for Cloud Apps uses the allowed capacity. Some operations, such as scanning all files in the tenant, require numerous APIs so they're spread over a longer period. Expect some policies to run for several hours or several days.

### Multi-instance support

Defender for Cloud Apps supports multiple instances of the same connected app. For example, if you've more than one instance of Salesforce (one for sales, one for marketing) you can connect both to Defender for Cloud Apps. You can manage the different instances from the same console to create granular policies and deeper investigation. This support applies only to API connected apps, not to Cloud Discovered apps or Proxy connected apps.

### How it works

Defender for Cloud Apps is deployed with system admin privileges to allow full access to all objects in your environment. The App Connector flow is as follows:

1. Defender for Cloud Apps scans and saves authentication permissions.
2. Defender for Cloud Apps requests the user list. The first time the request is done, it might take some time until the scan completes.
3. After completion of the user request, Defender for Cloud Apps periodically scans users, groups, activities, and files. All activities will be available after the first full scan.

Connections might take some time depending on the size of the tenant, the number of users, and the size and number of files that need to be scanned. Depending on the app to which you're connecting, API connection enables the following items:

- **Account information** - Visibility into users, accounts, profile information, status (suspended, active, disabled) groups, and privileges.
- **Audit trail** - Visibility into user activities, admin activities, sign-in activities.
- **Account governance** - Ability to suspend users, revoke passwords, etc.
- **App permissions** - Visibility into issued tokens and their permissions.
- **App permission governance** - Ability to remove tokens.
- **Data scan** - Scanning of unstructured data using two processes -periodically (every 12 hours) and in real-time scan (triggered each time a change is detected).
- **Data governance** - Ability to quarantine files, including files in trash, and overwrite files.


## Exercise implement access management for apps

### Create an Azure account and add Microsoft Entra ID Premium P2 trial licenses

The tasks in this exercise and the exercises in this learning path require you to already have and Azure subscription that you can use or to sign up for an Azure trial account. If you already have your own Azure subscription, you skip this task and continue to the next.

1. In a web browser, go to [Azure free subscription portal](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
2. Scroll down through the page to learn more about the benefits and free services available.
3. Select **Start free**.
4. Use the wizard to sign up for your Azure trial subscription.
5. You need to a Microsoft Entra ID P2 license to complete some of the exercises. In the organization you created, search for and then select **Microsoft Entra ID**.
6. In the left navigation menu, select **Getting started**.
7. Under Getting started with Microsoft Entra ID, select **Get a free trial for Microsoft Entra ID Premium**.
8. In the Activate pane, under **Microsoft Entra ID PREMIUM P2**, select **Free trial** and then select **Activate**.
9. In the navigation menu on the left, select **Overview**.
10. Refresh the browser until you see Microsoft Entra ID Premium P2 under the organization name. It takes a couple of minutes.
11. You need to sign out and sign back into Microsoft Azure if you encounter any problems with expected features not being available.

### Add an app to your Microsoft Entra tenant

Here, you add an Enterprise app that you can use for the exercise.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/) using a Global Administrator account.
2. Open the portal menu and then select **Identity**.
3. On the **Identity menu**, under **Applications**, select **Enterprise applications**.
4. In the **Enterprise applications** pane, select **+ New application**.
5. In the **Browse Microsoft Entra Gallery** page, in the **Search application** box, enter **GitHub**.
6. In the results, select **GitHub Enterprise Cloud – Enterprise Account**.
7. In the **GitHub Enterprise Cloud – Enterprise Account**, review the settings and then select **Create**.
8. Once the account is created, you're redirected to the **GitHub Enterprise Cloud – Enterprise Account** screen.

### Assign users to an app

Assign your administrator account to the recently added app.

1. On the **GitHub Enterprise Cloud – Enterprise Account** screen, on the **Overview** page, under **Getting Started**, select **1. Assign users and groups**. Alternatively, in the left navigation, under **Manage**, you can select **Users and groups**.
2. On the **Users and groups** page, on the menu, select **+Add user/group**.
3. On the **Add Assignment** dialog, select **Users and groups**.
4. In the **Users and groups** pane, select your administrator account and then **Select**.
5. Select **Assign**.


## Design and implement app management roles

This unit describes how to use permissions granted by custom roles in Microsoft Entra ID to address your application management needs. In Microsoft Entra ID, you can delegate application creation and management permissions by:

- Restricting who can create applications and manage the applications they create.
- Assigning one or more owners to an application. Assigning owners is a simple way to grant someone the ability to manage all aspects of Microsoft Entra ID configuration for a specific application.
- Assigning a built-in administrative role that grants access to manage configuration in Microsoft Entra ID for all applications. Built-in roles are the recommended way to grant IT experts access to manage broad application configuration permissions without granting access to manage other parts of Microsoft Entra ID not related to application configuration.
- Creating a custom role defining specific permissions and assigning it to someone either to the scope of a single application as a limited owner, or at the directory scope (all applications) as a limited administrator.

It's important to consider granting access using one of the above methods for two reasons. First, delegating the ability to perform administrative tasks reduces global administrator overhead. Second, using limited permissions improves your security posture and reduces the potential for unauthorized access.

### Restrict who can create applications

In Microsoft Entra ID, all users can register application registrations and manage all aspects of applications they create. Everyone also has the ability to consent to apps accessing company data on their behalf. You can choose to selectively grant those permissions by setting the global switches to "No" and adding the selected users to the Application Developer role.

#### To disable the default ability to create application registrations or consent to applications

1. Sign in to your Microsoft Entra organization with an account that's eligible for the Global Administrator role in your Microsoft Entra organization.
2. Set one or both of the following:
  - On the **User settings** page for your organization, set the **Users can register applications** setting to No. This disables the default ability for users to create application registrations.
  - On the **User Settings** for enterprise applications, configure if users can add Gallery Apps to My App or if Office 365 apps appear in the Office portal.
  - On the **Consent and Permissions** settings for enterprise applications, set the **Users can consent to applications accessing company data on their behalf** setting to No. This disables the default ability for users to consent to applications accessing company data on their behalf.

#### Grant individual permissions to create and consent to applications when the default ability is disabled

Assign the Application Developer role to grant the ability to create application registrations when the **Users can register applications** setting is set to No. This role also grants permission to consent on one's own behalf when the **Users can consent to apps accessing company data on their behalf** setting is set to No. As a system behavior, when a user creates a new application registration, they're automatically added as the first owner. Ownership permissions give the user the ability to manage all aspects of an application registration or enterprise application that they own.

### Assign application owners

Assigning owners is a simple way to grant the ability to manage all aspects of Microsoft Entra ID configuration for a specific application registration or enterprise application. As a system behavior, when a user creates a new application registration, they're automatically added as the first owner. Ownership permissions give the user the ability to manage all aspects of an application registration or enterprise application that they own. The original owner can be removed and additional owners can be added.

#### Enterprise application owners

As an owner, a user can manage the organization-specific configuration of the enterprise application, such as the SSO configuration, provisioning, and user assignments. An owner can also add or remove other owners. Unlike Global Administrators, owners can manage only the enterprise applications they own.

In some cases, enterprise applications created from the application gallery include both an enterprise application and an application registration. When this is true, adding an owner to the enterprise application automatically adds the owner to the corresponding application registration as an owner.

#### To assign an owner to an enterprise application

1. Sign in to your Microsoft Entra organization with an account that's eligible for the Application Administrator or Cloud Application Administrator for the organization.
2. On the **App registrations** page for the organization, select an app to open the Overview page for the app.
3. Select **Owners** to see the list of the owners for the app.
4. Select **Add** to select one or more owners to add to the app.

Important

Users and service principals can be owners of application registrations. Only users can be owners of enterprise applications. Groups can't be assigned as owners of either.

Owners can add credentials to an application and use those credentials to impersonate the application’s identity. The application has more permissions than the owner, and thus would be an elevation of privilege over what the owner has access to as a user or service principal. Depending on the application's permissions, an application owner could potentially create or update users or other objects while impersonating the application.

### Assign built-in application admin roles

Microsoft Entra ID has a set of built-in admin roles for granting access to manage configuration in Microsoft Entra ID for all applications. These roles are the recommended way to grant IT experts access to manage broad application configuration permissions without granting access to manage other parts of Microsoft Entra ID not related to application configuration.

- Application Administrator: Users in this role can create and manage all aspects of enterprise applications, application registrations, and application proxy settings. This role also grants the ability to consent to delegated permissions and application permissions, excluding Microsoft Graph. Users assigned to this role aren't added as owners when creating new application registrations or enterprise applications.
- Cloud Application Administrator: Users in this role have the same permissions as the Application Administrator role, excluding the ability to manage application proxy. Users assigned to this role aren't added as owners when creating new application registrations or enterprise applications.  Important Application Administrators and Cloud Application Administrators can add credentials to an application and use those credentials to impersonate the application’s identity. The application has permissions that are an elevation of privilege over the admin role's permissions. Depending on the application's permissions, an admin in one of these roles could potentially create or update users or other objects while impersonating the application. Neither role grants the ability to manage Conditional Access settings.

### Create and assign a custom role

Creating custom roles and assigning custom roles are separate steps:

- Create a custom *role definition* and add permissions to it from a preset list. These are the same permissions used in the built-in roles.
- Create a *role assignment* to assign the custom role.

This separation enables you to create a single role definition and then assign it many times at different *scopes*. A custom role can be assigned at organization-wide scope or at the scope of a single Microsoft Entra object. An example of an object scope is a single app registration. When an administrator uses different scopes, however, the same role definition can be assigned to one person over all of the app registrations in the organization, and then to another person over only a single app or specific app registrations.

Tips when creating and using custom roles for delegating application management:

- Custom roles only grant access in the most current app registration screen of the Microsoft Entra admin center. They don't grant access in the legacy app registrations screen.
- Custom roles don't grant access to the Microsoft Entra ID portal when the **Restrict access to Microsoft Entra ID administration** portal user setting is set to Yes.
- For app registrations the user has access to, role assignments only show up in the **All applications** tab on the **App registration** page. They don't show up in the **Owned applications** tab.


## Exercise create a custom role to manage app registration

Create a new custom role that can be used to grant access to manage app registrations.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/) using an Administrator account.
2. Open the portal menu and then select **Identity**.
3. On the **Identity** menu, then open **Roles and admins** menu, and select **Roles and administrators.**
4. On the **Roles and administrators** screen, on the menu, select **New custom role.**
5. In the **New custom role** dialog, on the **Basics** tab, in the name box, enter **My custom app role**.
6. Review the remaining options and then select **Next**.
7. On the **Permissions** tab, review the available permissions.
8. In the **Search by permission name or description** box, enter credentials.
9. In the results, select the **Manage** permissions and then select **Next**.
10. Review the changes and then select **Create.**


## Configure preintegrated gallery SaaS apps

As you know, Microsoft Entra ID has a gallery that contains thousands of pre-integrated applications. Many of the applications your organization uses are probably already in the gallery. If an app is added to your Microsoft Entra tenant, you can configure properties for the app, manage user access to the app, and configure SSO so users can sign in to the app with their Microsoft Entra credentials. This unit will show you how to configure properties for the app.

### Configure application (app) properties

To edit the app properties:

1. In the Microsoft Entra admin center Identity menu, select **Enterprise applications**. Then find and select the application you want to configure.
2. In the **Manage** section, select **Properties** to open the **Properties** pane for editing.
3. Take a moment to understand the options available. The options available will depend on how the app is integrated with Microsoft Entra ID. For example, an app that uses SAML-based SSO will have fields such as *User access URL* whereas an app that uses OIDC-based SSO won't. Apps added through **Microsoft Entra ID - App registrations** are by default OIDC-based apps, while apps added **through Microsoft Entra ID - Enterprise applications** might use any SSO standard. All apps will have fields for configuring when an app appears and can be used. These fields are:
  - **Enabled for users to sign in?** determines whether users assigned to the application can sign in.
  - **User assignment required?** determines whether users who aren't assigned to the application can sign in.
  - **Visible to users?** determines whether users assigned to an app can see it in [My Apps](https://myapps.microsoft.com/) and Microsoft 365 app launcher. (See the waffle menu in the upper-left corner of a Microsoft 365 website.)

4. When you're finished, select **Save**

### Use a custom logo

1. To use a custom logo:
2. Create a logo that's 215 by 215 pixels and save it in .png format.
3. In the Microsoft Entra admin center, select **Enterprise applications**. Then find and select the application you want to configure.
4. In the **Manage** section, select **Properties** to open the **Properties** pane for editing.
5. Select the icon to upload the logo.
6. Then you're finished, select **Save**.

### Add notes

You can use the notes field to add any information that is relevant for the management of the application.

1. In the Microsoft Entra admin center, select **Enterprise applications**. Then find and select the application you want to configure.
2. In the **Manage** section, select **Properties** to open the **Properties** pane for editing.
3. Update the Notes field, select **Save**.


## Implement and manage policies for OAuth apps

In addition to the existing investigation of OAuth apps connected to your environment, you can set permission policies so that you get automated notifications when an OAuth app meets certain criteria. For example, you can automatically be alerted when there are apps that require a high permission level and were authorized by more than 50 users. OAuth app policies enable you to investigate which permissions each app requested and which users authorized them for Office 365, and other OAuth apps. You're also able to mark these permissions as approved or banned. Marking them as banned will disable the correlating Enterprise Application.

### Create a new OAuth app policy

1. Launch **Microsoft Defender for Cloud Apps** at [https://security.microsoft.com](https://security.microsoft.com).
2. Scroll down the menu on left until you get to the **Cloud apps** section.
3. Select **OAuth apps**.
4. Filter the apps according to your needs.

- For example, you can view all apps that request Permission to Modify calendars in your mailbox.

1. Select the **New policy** from search button.
2. You can use the **Community use** filter to get information on whether allowing permission to this app is common, uncommon, or rare.
  - This filter can be helpful if you have an app that's rare and requests permission that has a high severity level or requests permission from many users.

3. You can set the policy based on the group memberships of the users who authorized the apps.

- For example, an admin can decide to set a policy that revokes uncommon apps if they ask for high permissions, only if the user who authorized the permissions is a member of the Administrators group.

#### Control policies

Alternatively, you can also create the policy by selecting **Control** followed by **Policies**. Then select **Create policy** followed by **OAuth app policy**.


## Module Assessment

Choose the best response for each of the questions.

### Check your knowledge


## Summary and resources

After finishing this module, you're able to:

- Discover apps by using app discovery in Microsoft Defender or Active Directory app report.
- Design and implement access management for apps.
- Design and implement app management roles.
- Configure preintegrated (gallery) SaaS apps.
- Explore application connectors and OAuth apps.

### Resources

Use these resources to discover more:

- [What is single-sign-on in Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [Connected apps with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-cloud-apps/enable-instant-visibility-protection-and-governance-actions-for-your-apps)
- [Quickstart: Enable single-sign-on for an enterprise application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-setup-sso)
- [Create policies to control OAuth apps](https://learn.microsoft.com/en-us/defender-cloud-apps/app-permission-policy)


---

# Implement and monitor the integration of enterprise apps for SSO

_https://learn.microsoft.com/en-us/training/modules/implement-monitor-integration-of-enterprise-apps-for-sso/_


## Introduction

In this module, you learn how to implement token customizations and implement and configure consent settings. You also learn how to integrate on-premises apps by using Microsoft Entra application proxy, and also integrate custom software as a service (SaaS) apps for single-sign-on (SSO). Finally, you explore how to implement application user provisioning and monitor and audit access to Microsoft Entra ID integrated enterprise applications.

### Learning objectives

In this module, you:

- Implement token customizations
- Implement and configure consent settings
- Integrate on-premises apps by using Microsoft Entra application proxy
- Integrate custom SaaS apps for SSO
- Implement application user provisioning
- Create and manage application collections
- Monitor and audit access to Microsoft Entra ID integrated enterprise applications

### Prerequisites

- Management of users and administrators in Microsoft Entra ID
- Experience with setting up conditional access


## Implement token customizations

You can specify the lifetime of a token issued by Microsoft identity platform. Additionally, you can set token lifetimes for all apps in your organization, for a multitenant (multiple organizations) application, or for a specific service principal in your organization. In Microsoft Entra ID, a policy object represents a set of rules that are enforced on individual applications or on all applications in an organization. Each policy type has a unique structure, with a set of properties that are applied to objects to which they're assigned.

You can designate a policy as the default policy for your organization. The policy is applied to any application in the organization, as long as it isn't overridden by a policy with a higher priority. You also can assign a policy to specific applications. The order of priority varies by policy type.

### Configure authentication session management with Conditional Access

In complex deployments, organizations might have a need to restrict authentication sessions. These complex scenarios might include:

- Resource access from an unmanaged or shared device.
- Access to sensitive information from an external network.
- High-impact users.
- Critical business applications.

Conditional Access controls allow you to create policies that target specific use cases within your organization without affecting all users.

For more information, see the link in the resources at the end of this module.

### Customize Tokens for Microsoft Entra ID

| **Access and ID token lifetime** | **Refresh token lifetime (days)** | **Refresh token sliding windows lifetime** | **Lifetime length (days)** |
|---|---|---|---|
| The lifetime of the OAuth 2.0 bearer token and ID token | The maximum time period before which a refresh token can be used to acquire a new access token | The refresh token sliding window type | After time period elapses, the user is forced to reauthenticate |

![Diagram of the Refresh token lifetime - token is valid for a specified amount of time and the access token must be refreshed before it expires.](https://learn.microsoft.com../../wwl-sci/implement-monitor-integration-of-enterprise-apps-for-sso/media/token-customize-timeline.png)

### Configure optional claims as part of your token

Application developers can use optional claims in their Microsoft Entra ID applications to specify which claims they want in tokens sent to their application.

You can use optional claims to:

- Select other claims to include in tokens for your application.
- Change the behavior of certain claims that the Microsoft identity platform returns in tokens.
- Add access custom claims for your application.

While optional claims are supported in both v1.0 and v2.0 format tokens, and SAML tokens, they provide most of their value when moving from v1.0 to v2.0. One of the goals of the Microsoft identity platform is smaller token sizes to ensure optimal performance by clients. As a result, several claims formerly included in the access and ID tokens are no longer present in v2.0 tokens and must be asked for specifically on a per-application basis.

## Implement and configure consent settings

You can integrate your applications with the Microsoft identity platform to allow users to sign in with their work or school account and access the organization's data to deliver rich data-driven experiences.

Before an application can access the organization's data, a user must grant the application permissions to do so. Different permissions allow different levels of access. By default, all users can consent to applications for permissions that don't require administrator consent. For example, by default, a user can consent to allow an app to access their mailbox. However, they can't consent to allow an app unfettered access to read and write to all files in your organization.

By allowing users to grant apps access to data, users can easily acquire useful applications and be productive. However, in some situations this configuration can represent a risk if it isn't carefully monitored and controlled.

Important

To reduce the risk of malicious applications attempting to trick users into granting them access to your organization's data, it is recommended that you allow user consent only for applications that have been published by a [verified publisher](https://learn.microsoft.com/en-us/azure/active-directory/develop/publisher-verification-overview).

### User consent settings

App consent policies describe conditions that must be met before an app can be consented to. These policies might include conditions on the app requesting access, and the permissions the app is requesting.

By choosing which app consent policies apply for all users, you can set limits on when end users are allowed to grant consent to apps and when they'll be required to request administrator review and approval.

- **Disable user consent** – Users can't grant permissions to applications. Users can continue to sign into apps they had previously consented to or that are consented to by administrators on their behalf, but they'll not be allowed to consent to new permissions or to new apps on their own. Only users who have been granted a directory role that includes the permission to grant consent will be able to consent to new apps.
- **Users can consent to apps from [verified publisher](https://learn.microsoft.com/en-us/azure/active-directory/develop/publisher-verification-overview)s or your organization, but only for permissions you choose**– All users can only consent to apps that were published by a verified publisher and apps that are registered in your tenant. Users can only consent to the permissions you have classified as `low impact`. You must [classify permissions](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/configure-permission-classifications) to choose which permissions users are allowed to consent to.
- **Users can consent to all apps** – This option allows all users to consent to any permission that doesn't require administrator consent for any application.
- **Custom app consent policy** – For even more options over the conditions governing when users consent, you can [create custom app consent policies](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/manage-app-consent-policies) and configure those to apply for user consent.

### Risk-based step-up consent

Risk-based step-up consent helps reduce user exposure to malicious apps that make illicit consent requests. If Microsoft detects a risky end-user consent request, the request will require a step-up to admin consent instead. This capability is enabled by default, but it will only result in a behavior change when end-user consent is enabled.

When a risky consent request is detected, the consent prompt will display a message indicating that admin approval is needed. If the admin consent request workflow is enabled, the user can send the request to an administrator for further review directly from the consent prompt. If it isn't enabled, the following message will be displayed:

- **AADSTS90094:** needs permission to access resources in your organization that only an admin can grant. Ask an admin to grant permission to this app before you can use it.

In this case, an audit event will also be logged with a Category of **ApplicationManagement**, an Activity Type of **Consent to application**, and a Status Reason of **Risky application detected.**

Important

Administrators should evaluate all consent requests carefully before approving a request, especially when Microsoft has detected risk.


## Integrate on-premises apps with Microsoft Entra application proxy

**What is Application Proxy?** Application Proxy is a feature of Microsoft Entra ID that enables users to access on-premises web applications from a remote client. Application Proxy includes both the Application Proxy service that runs in the cloud, and the Application Proxy connector that runs on an on-premises server. Microsoft Entra ID, the Application Proxy service, and the Application Proxy connector work together to securely pass the user sign-on token from Microsoft Entra ID to the web application.

The Application Proxy for Microsoft Entra ID provides secure remote access to on-premises web applications. After a single sign-on to Microsoft Entra ID, users can access both cloud and on-premises applications through an external URL or an internal application portal. For example, Application Proxy can provide remote access and single sign-on to Remote Desktop, SharePoint, Teams, Tableau, Qlik, and line of business (LOB) applications.

Application Proxy works with:

- Web applications that use [Integrated Windows Authentication](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/application-proxy-configure-single-sign-on-with-kcd) for authentication.
- Web applications that use form-based or [header-based](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/application-proxy-configure-single-sign-on-with-headers) access.
- Web APIs that you want to expose to rich applications on different devices.
- Applications hosted behind a [Remote Desktop Gateway](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/application-proxy-integrate-with-remote-desktop-services).
- Rich client apps that are integrated with the Microsoft Authentication Library (MSAL).

Application Proxy is recommended for giving remote users access to internal resources. Application Proxy replaces the need for a virtual private network (VPN) or reverse proxy. It is not intended for internal users on the corporate network. These users who unnecessarily use Application Proxy can introduce unexpected and undesirable performance issues.

### How Application Proxy works

The following diagram shows how Microsoft Entra ID and Application Proxy work together to provide single sign-on to on-premises applications.

![Diagram of the Microsoft Entra Application Proxy process flow. A successful configuration is shown.](https://learn.microsoft.com../../wwl-sci/implement-monitor-integration-of-enterprise-apps-for-sso/media/azure-app-proxxy.png)

1. After the user has accessed the application through an endpoint, the user is directed to the Microsoft Entra sign-in page.
2. After a successful sign-in, Microsoft Entra ID sends a token to the user's client device.
3. The client sends the token to the Application Proxy service, which retrieves the user principal name (UPN) and security principal name (SPN) from the token. Application Proxy then sends the request to the Application Proxy connector.
4. If you have configured single sign-on, the connector performs any additional authentication required on behalf of the user.
5. The connector sends the request to the on-premises application.
6. The response is sent through the connector and Application Proxy service to the user.

### Add an on-premises application for remote access through Application Proxy in Microsoft Entra ID

Launch and interact with this Interactive Guide to learn more about enabling integrated windows authentication to on-premises applications with Microsoft Entra Application Proxy - **[Enable Integrated Windows Authentication Interactive Guide](https://mslearn.cloudguides.com/guides/Provide%20secure%20remote%20access%20to%20on-premises%20applications%20with%20Azure%20AD%20Application%20Proxy)**


## Integrate custom SaaS apps for single sign-on

![Diagram of Microsoft Entra ID being the single-sign-on provider for cloud apps. User and external users log into Microsoft Entra ID, then connect to cloud applications.](https://learn.microsoft.com../../wwl-sci/implement-monitor-integration-of-enterprise-apps-for-sso/media/app-single-sign-on.png)

- You can use Microsoft Entra ID as your identity system for just about any app. Many apps are already pre-configured and can be set up with minimal effort. These pre-configured apps are published in the Microsoft Entra ID App Gallery.
- You can manually configure most apps for single-sign-on if they aren't already in the gallery. Microsoft Entra ID provides several SSO options. SAML-based SSO and OIDC-based SSO.

Effectively, apps can delegate maintenance of their own username and password information to a centralized identity provider, Microsoft Entra ID as an example. Delegating authentication and authorization enables scenarios such as Conditional Access policies that require a user to be in a specific location or require multifactor authentication. The use of single-sign-on (SSO), enables a user to sign in once and then be automatically signed in to all of the web apps that share the same centralized directory.

Microsoft identity platform simplifies authorization and authentication for application developers by providing identity as a service, with support for industry-standard protocols such as OAuth 2.0 and OpenID Connect, as well as open-source libraries for different platforms to help you start coding quickly. It allows developers to build applications that sign in all Microsoft identities, get tokens to call Microsoft Graph, other Microsoft APIs, or APIs that developers have built.

The following list is a brief comparison of the various protocols used by Microsoft identity platform.

- **OAuth vs. OpenID Connect**: OAuth is used for authorization and OpenID Connect (OIDC) is used for authentication. OpenID Connect is built on top of OAuth 2.0, which means the terminology and flow are similar between the two. You can even authenticate a user using OpenID Connect and get authorization to access a protected resource that the user owns using OAuth 2.0 in one request.
- **OAuth vs. SAML**: OAuth is used for authorization and Security Assertion Markup Language (SAML) is used for authentication.
- **OpenID Connect vs. SAML**: Both OpenID Connect and SAML are used to authenticate a user and are used to enable single-sign-on. SAML authentication is commonly used with identity providers such as Active Directory Federation Services (ADFS) federated to Microsoft Entra ID and is therefore frequently used in enterprise applications. OpenID Connect is commonly used for apps that are purely in the cloud, such as mobile apps, web sites, and web APIs.

If you have an application that you want to integrate with Microsoft Entra ID to provide the single-sign-on experience for your users, please see the article ClaimsXRay in Microsoft Entra ID with Directory Extension, linked below:

[ClaimsXRay in Microsoft Entra ID with Directory Extension](https://techcommunity.microsoft.com/t5/core-infrastructure-and-security/claimsxray-in-azuread-with-directory-extension/ba-p/1505737)


## Implement application-based user provisioning

In Microsoft Entra ID, the term app provisioning refers to automatically creating user identities and roles in the cloud ([SaaS](https://azure.microsoft.com/overview/what-is-saas/)) applications that users need access to. In addition to creating user identities, automatic provisioning includes the maintenance and removal of user identities as status or roles change. A common scenario is provisioning a Microsoft Entra user into applications like [Dropbox](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/dropboxforbusiness-provisioning-tutorial), [Salesforce](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/salesforce-provisioning-tutorial), [ServiceNow](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/servicenow-provisioning-tutorial), and more.

![Diagram of the process flow for Provisioning. You can automate and govern the provisioning process.](https://learn.microsoft.com../../wwl-sci/implement-monitor-integration-of-enterprise-apps-for-sso/media/provision-overview.png)

This feature lets you to the following actions.

- **Automate provisioning**: Automatically create new accounts in the right systems for new people when they join a team or organization.
- **Automate deprovisioning**: Automatically deactivate accounts in the right systems when people leave a team or organization.
- **Synchronize data between systems:** Ensure that the identities in the apps and systems are kept up to date based on changes in the directory or the human resources system.
- **Provision groups**: Provisioning a group to the applications that supports them.
- **Govern access:** Monitor and audit who has been provisioned into the applications.
- **Seamlessly deploy in brown field scenarios**: Match existing identities between systems and allow for easy integration, even when users already exist in the target system.
- **Use rich customization**: Take advantage of customizable attribute mappings that define what user data should flow from the source system to the target system.
- **Get alerts for critical events**: The provisioning service provides alerts for critical events and allows for Log Analytics integration where you can define custom alerts to suit your business needs.

### Manual vs. automatic provisioning

Applications in the Microsoft Entra ID gallery support either manual or automatic provisioning.

- Manual provisioning means there's no automatic Microsoft Entra provisioning connector for the app yet. User accounts must be created manually. Examples of this include adding users directly into the administrative portal of the app or uploading a spreadsheet with user account details. Consult the documentation provided by the app or contact the app developer to determine what mechanisms are available.
- Automatic means that a Microsoft Entra provisioning connector has been developed for this application. Follow the setup tutorial for setting up provisioning for the application.

In the Microsoft Entra ID gallery, applications that support automatic provisioning are designated by a **Provisioning** icon.

The provisioning mode supported by an application is also visible on the **Provisioning** tab once you've added the application to your **Enterprise apps**.

### System for Cross-domain Identity Management

To help automate provisioning and deprovisioning, apps expose proprietary user and group APIs. However, every app tries to perform the same actions, such as creating or updating users, adding users to groups, or deprovisioning users. Yet, all these simple actions are implemented just slightly differently, using different endpoint paths, different methods to specify user information, and a different schema to represent each element of information.

To address these challenges, the System for Cross-domain Identity Management (SCIM) specification provides a common user schema to help users move into, out of, and around apps. SCIM is becoming the standard for provisioning and, when used in conjunction with federation standards like SAML or OpenID Connect, provides administrators an end-to-end, standards-based solution for access management.

### Build a System for Cross-domain Identity Management endpoint and configure user provisioning with Microsoft Entra ID

As an application developer, you can use the System for Cross-Domain Identity Management (SCIM) user management API to enable automatic provisioning of users and groups between your application and Microsoft Entra ID. The SCIM specification provides a common user schema for provisioning. When used in conjunction with federation standards like SAML or OpenID Connect, SCIM gives administrators an end-to-end, standards-based solution for access management.

SCIM is a standardized definition of two endpoints: a /Users endpoint and a /Groups endpoint. It uses common Representational state transfer (REST) verbs to create, update, and delete objects, and a pre-defined schema for common attributes like group name, username, first name, last name, and email. Apps that offer a SCIM 2.0 REST API can reduce or eliminate the pain of working with a proprietary user management API. For example, any compliant SCIM client knows how to make an HTTP POST of a JSON object to the /Users endpoint to create a new user entry. Instead of needing a slightly different API for the same basic actions, apps that conform to the SCIM standard can instantly take advantage of preexisting clients, tools, and code.

![Diagram of Microsoft Entra ID with user provisioning sharing data with external apps.](https://learn.microsoft.com../../wwl-sci/implement-monitor-integration-of-enterprise-apps-for-sso/media/system-for-cross-domain-identity-management-provision-overview.png)

The standard user object schema and REST APIs for management defined in SCIM 2.0 allow identity providers and apps to integrate with each other more easily. Application developers that build a SCIM endpoint can integrate with any SCIM-compliant client without having to do custom work, rather than starting from scratch and building the implementation completely on your own, you can rely on a number of open source SCIM libraries published by the SCIM community.


## Monitor and audit access to Microsoft Entra integrated enterprise applications

With Microsoft Entra ID reports, you can get the information needed to determine how your environment is doing. With the usage and insights report, you can get an application-centric view of your sign-in data and find answers to the following questions:

- What are the top used applications in the organization?
- What applications have the most failed sign-ins?
- What are the top sign-in errors for each application?

### Access the usage and insights report

1. Navigate to the [Microsoft Entra admin center](https://entra.microsoft.com/).
2. Select the Identity menu, then select **Applications** and choose **Enterprise applications**.
3. From the **Activity** section, select **Usage & insights** to open the report.

### Use the report

The usage and insights report shows the list of applications with one or more sign-in attempts and allows you to sort by the number of successful sign-ins, failed sign-ins, and the success rate.

Selecting **load more** at the bottom of the list allows you to view more applications on the page. You can select the date range to view all applications that have been used within the range.

You can also set the focus on a specific application. Select **view sign-in activity** to see the sign-in activity over time for the application and the top errors.

When you select a day in the application usage graph, you get a detailed list of the sign-in activities for the application.

### Audit logs

The Microsoft Entra audit logs provide records of system activities for compliance. Users in the Security Administrator, Security Reader, Report Reader, Global Reader or Administrator roles can access their data. To access the audit report, select **Audit logs** in the **Monitoring** section of **Microsoft Entra ID**.

An audit log has a default list view that shows:

- the date and time of the occurrence
- the service that logged the occurrence
- the category and name of the activity (what)
- the status of the activity (success or failure)
- the target
- the initiator/actor (who) of an activity

You can customize the list view by clicking **Columns** in the toolbar.

This enables you to display other fields or remove fields that are already displayed.

Select an item in the list view to get more detailed information.

### Enterprise applications audit logs

With application-based audit reports, you can get answers to questions such as:

- What applications have been added or updated?
- What applications have been removed?
- Has a service principal for an application changed?
- Have the names of applications been changed?
- Who gave consent to an application?

If you want to review audit data related to your applications, you can find a filtered view under **Audit logs** in the **Activity** section of the **Enterprise applications** screen. This entry point has **Enterprise applications** preselected as the **Application Type**.

## Create and manage application collections

Your users can use the My Apps portal to view and start the cloud-based applications they have access to. By default, all the applications a user can access are listed together on a single page. To better organize this page for your users, if you have a Microsoft Entra ID Premium P1, or P2 license you can set up collections. With a collection, you can group together applications that are related (for example, by job role, task, or project). Then they display on a separate tab for easy usage. A collection essentially applies a filter to the applications a user can already access, so the user sees only those applications in the collection that have been assigned to them.

### Create and admin application collection

Admin collections are managed through the Azure portal. For example, if you assign users or groups as an owner, then they can only manage the collection through the Azure portal.

1. Open the Microsoft Entra admin center and sign in as an admin.
2. Go to **Identity**, next open the **Applications** menu, then select **Enterprise Applications**.
3. Under **Manage**, select **App Launchers**.
4. Select **New collection**.

- In the New collection page, enter a Name for the collection (we recommend not using "collection" in the name. Then enter a Description.

1. Select the **Applications tab**. Select **+ Add application** to open the Add applications page.

- Select all the applications you want to add to the collection, or use the Search box to find applications.

1. When you're finished adding applications, select **Add**.

- The list of selected applications appears. You can use the arrows to change the order of applications in the list.

1. Select the **Owners tab**. Select **+ Add users and groups**, to open the Add users and groups page
2. Select the users or groups you want to assign ownership to.
3. When you're finished selecting users and groups, choose **Select**.
4. Select Review + Create. The properties for the new collection appear.

### My apps portal

You can also use the [My Apps](https://myapps.microsoft.com) portal (`https://myapps.microsoft.com`) to add app collections. My Apps is a web-based portal that is used for managing and launching applications in Microsoft Entra ID. To work with applications in My Apps, use an organizational account in Microsoft Entra ID and obtain access granted by the Microsoft Entra administrator. My Apps is separate from the Azure portal and doesn't require users to have an Azure subscription or Microsoft 365 subscription.

Users access the My Apps portal to:

- Discover applications to which they have access
- Request new applications that the organization supports for self-service
- Create personal collections of applications
- Manage access to applications

By default, all applications are listed together on a single page. Collections can be used to group together related applications and present them on a separate tab, making them easier to find. For example, use collections to create logical groupings of applications for specific job roles, tasks, projects, and so on. Every application to which a user has access appears in the default Apps collection, but a user can remove applications from the collection.

#### Create a collection using the My Apps portal

Follow these steps to create a collection.

1. Open the **[My Apps](https://myapps.microsoft.com) portal**.
2. Select the ellipsis (...) on the apps screen.
3. Choose **Manage collections.**
4. Select **Create collection.**
5. Select the **+ Add apps** option to add all the apps you want in the collection.
6. After picking your apps, select the **Add selected apps** button.
7. Give the collection a name and choose **Create collection**.


## Knowledge check

Choose the best response for each of the questions below.

### Check your knowledge


## Summary and resources

After finishing this module, you're able to:

- Implement token customizations
- Implement and configure consent settings
- Integrate on-premises apps by using Microsoft Entra application proxy
- Integrate custom SaaS apps for SSO (single sign-on)
- Implement application user provisioning
- Create and manage application collections
- Monitor and audit access/sign-on to Microsoft Entra ID integrated enterprise applications

### Resources

Use these resources to discover more.

- [ClaimsXRay in Microsoft Entra ID with Directory Extension](https://techcommunity.microsoft.com/t5/core-infrastructure-and-security/claimsxray-in-azuread-with-directory-extension/ba-p/1505737)
- [Configure authentication session management](https://learn.microsoft.com/en-us/entra/identity/conditional-access/howto-conditional-access-session-lifetime)
- [My Apps portal overview](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/myapps-overview)
- [Create collections on the My Apps portal](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/access-panel-collections)


---

# Implement app registration

_https://learn.microsoft.com/en-us/training/modules/implement-app-registration/_


## Introduction

In this module, you plan your line-of-business application registration strategy, implement application registrations, and configure application permissions.

### Learning objectives

In this module, you will:

- Plan your line-of-business application registration strategy.
- Implement application registrations.
- Configure application permissions.
- Establish and maintain an application governance process.

### Prerequisites

- Experience using the Microsoft Cloud admin portals.
- Previous experience with cloud and on-premises applications.


## Plan your line of business application registration strategy

This unit looks at why applications integrate with Microsoft Entra ID. Add applications to Microsoft Entra ID to apply one or more of the services it provides, including:

- Application authentication and authorization.
- User authentication and authorization.
- Single-sign-on (SSO) using federation or password.
- User provisioning and synchronization.
- Role-based access control: Use the directory to define application roles to perform role-based authorization checks in an application.
- OAuth authorization services: Used by Microsoft 365 and other Microsoft applications to authorize access to APIs/resources.
- Application publishing and proxy: Publish an application from a private network to the internet.
- Directory schema extension attributes: Extend the schema of service principal and user objects to store extra data in Microsoft Entra ID.

There are two representations of applications in Microsoft Entra ID: [application objects](https://learn.microsoft.com/en-us/entra/identity-platform/app-objects-and-service-principals) and service principals. The next two sections explain each, and how they interact with one another in the Azure portal.

### What are application objects and where do they come from?

You can manage application objects in the Azure portal through the App Registrations experience. Application objects define and describe the application to Microsoft Entra ID, enabling your identity provider to know how to issue tokens to the application based on its settings. The application object will only exist in its home directory, even if it's a multitenant application supporting service principals in other directories. The application object includes any of the following (as well as additional information not mentioned here):

- Name, logo, and publisher
- Redirect URIs
- Secrets (symmetric and/or asymmetric keys used to authenticate the application)
- API dependencies (OAuth)
- Published APIs/resources/scopes (OAuth)
- App roles (RBAC)
- SSO metadata and configuration
- User provisioning metadata and configuration
- Proxy metadata and configuration

You can create application objects through multiple pathways, including:

- Application registrations in the Azure portal.
- Creating a new application using Visual Studio and configuring it to use Microsoft Entra authentication.
- When an admin adds an application from the app gallery (which will also create a service principal).
- Using the Microsoft Graph API or PowerShell to create a new application.
- Many other pathways, including various developer experiences in Azure and in API explorer experiences across developer centers.

### What are service principals and where do they come from?

You can manage service principals in the Azure portal through the Enterprise Applications experience. Service principals govern an application connecting to Microsoft Entra ID and can be considered the instance of the application in your directory. Any given application can have at most one application object (which is registered in a "home" directory) and one or more service principal objects representing instances of the application in every directory in which it acts.

The service principal can include:

- A reference back to an application object through the application ID property.
- Records of local user and group application-role assignments.
- Records of local user and admin permissions granted to the application.
  - For example: permission for the application to access a particular user's email.

- Records of local policies including Conditional Access policy.
- Records of alternate local settings for an application.
  - Claims transformation rules.
  - Attribute mappings (User provisioning).
  - Directory-specific app roles (if the application supports custom roles).
  - Directory-specific name or logo.

Like application objects, service principals can be created through multiple pathways, including:

- When users sign in to a third-party application integrated with Microsoft Entra ID.
  - During sign-in, users are asked to give permission to the application to access their profile and other permissions. The first person to give consent causes a service principal that represents the application to be added to the directory.

- When users sign in to Microsoft online services like Microsoft 365.
  - When you subscribe to Microsoft 365 or begin a trial, one or more service principals are created in the directory representing the various services that are used to deliver all of the functionality associated with Microsoft 365.
  - Some Microsoft 365 services, like SharePoint, create service principals on an ongoing basis to allow secure communication between components, including workflows.

- When an admin adds an application from the app gallery (this will also create an underlying app object).
- Add an application to use the Microsoft Entra Application Proxy.
- Connect an application for SSO using SAML or password SSO.
- Programmatically via the Microsoft Graph API or PowerShell.

### How are application objects and service principals related to each other?

An application has one application object in its home directory that's referenced by one or more service principals in each of the directories where it operates (including the application's home directory).

![Diagram of the relationship between app objects and service principals.](https://learn.microsoft.com../../wwl-sci/implement-app-registration/media/how-apps-added-azure-active-directory.png)

In the preceding diagram, Microsoft maintains two directories internally (shown on the left) that it uses to publish applications:

- One for Microsoft Apps (Microsoft services directory).
- One for preintegrated third-party applications (App gallery directory).

Application publishers/vendors who integrate with Microsoft Entra ID are required to have a publishing directory (shown on the right as "Some SaaS directory").

Applications that you add (represented as "App (yours)" in the diagram) include:

- Apps you developed (integrated with Microsoft Entra ID).
- Apps you connected for SSO.
- Apps you published using the Microsoft Entra Application Proxy.

#### Notes and exceptions to service principals

Not all service principals point back to an application object. When Microsoft Entra ID was originally built, the services provided to applications were more limited, and the service principal was sufficient for establishing an application identity. The original service principal was closer in shape to the Windows Server Active Directory service account. For this reason, it's still possible to create service principals through different pathways, such as using PowerShell, without first creating an application object. The Microsoft Graph API requires an application object before creating a service principal.

Not all of the information described above is currently exposed programmatically. The following are only available in the UI:

- Claims transformation rules
- Attribute mappings (User provisioning)

For more detailed information on the service principal and application objects, see the Microsoft Graph API reference documentation:

- Application
- Service Principal

### Adding a new app registration

![Diagram of the relationship between app objects and service principals, focusing on process flow.](https://learn.microsoft.com../../wwl-sci/implement-app-registration/media/register-new-app.png)

**Process flow of the diagram**

1. User requests to register an application – a request token is issued.
2. Authorization endpoint sends back an Authentication.
3. User consents to have the application registration.
4. Service is created from the application
5. Token returned to the user.

### Who has permission to add applications to my Microsoft Entra instance?

You can assign roles like Application Administrator, and Cloud Application Administrator to perform these tasks. You **must remember** that by default all users in your directory have rights to register application objects they're developing, and they have discretion over which applications they share / give access to their organizational data through consent. When the first user in your directory connects to an application, and grants consent that will create a service principal. Otherwise, the consent grant information will be stored on the existing service principal.

Allowing users to register and consent to applications might initially sound concerning, but keep the following in mind:

- Applications have been able to leverage Windows Server Active Directory for user authentication for many years without requiring the application to be registered or recorded in the directory. Now the organization will have improved visibility to exactly how many applications are using the directory and for what purpose.
- Delegating these responsibilities to users negates the need for an admin-driven application registration and publishing process. With Active Directory Federation Services (AD FS), an admin likely had to add an application as a relying party on behalf of their developers. Now developers can deploy themselves (self-service).
- Users signing in to applications using their organization accounts for business purposes is a good thing. If they subsequently leave the organization, they'll automatically lose access to their account in the application they were using.
- Having a record of what data was shared with which application is a good thing. Data is more transportable than ever and it's useful to have a clear record of who shared what data with which applications.
- API owners who use Microsoft Entra ID for OAuth decide exactly what permissions users are able to grant to applications and which permissions require an admin to agree to. Only admins can consent to larger scopes and more significant permissions, while user consent is scoped to the users' own data and capabilities.
- When a user adds or allows an application to access their data, the event can be audited. You can view the Audit Reports within the Azure portal to determine how an application was added to the directory.

If you still want to prevent users in your directory from registering applications and from signing in to applications without administrator approval, two settings enable you to turn off those capabilities:

To prevent users from consenting to applications on their own behalf:

- In the Azure portal, go to the User settings section under Enterprise applications.
- Change **Users can consent to apps accessing company data on their behalf** to **No**.  Note If you decide to turn off user consent, an admin will be required to consent to any new application a user needs to use.

To prevent users from registering their own applications:

- In the Azure portal, go to the User settings section under Microsoft Entra ID.
- Change **Users can register applications** to **No**.

### Tenancy in Microsoft Entra ID

Microsoft Entra organizes objects like users and apps into groups called *tenants*. Tenants enable an administrator to set policies on the users within the organization and the apps that the organization owns to meet their security and operational policies.

#### Who can access your app?

When it comes to developing apps, developers can choose to configure their app to be either single-tenant or multitenant during app registration in the Azure portal.

- Single-tenant apps are only available in the tenant they were registered in, also known as their home tenant.
- Multitenant apps are available to users in both their home tenant and other tenants.

In the Azure portal, you can configure your app to be single-tenant or multitenant by setting the audience as follows:

**Specific app access**

| **Audience** | **Single/multitenant** | **Who can sign in** |
|---|---|---|
| Accounts in this directory only | Single tenant | All user and guest accounts in your directory can use your application or API. *Use this option if your target audience is internal to your organization*. |
| Accounts in any Microsoft Entra directory | Multitenant | All users and guests with a work or school account from Microsoft can use your application or API. This includes schools and businesses that use Microsoft 365. *Use this option if your target audience is business or educational customers.* |
| Accounts in any Microsoft Entra directory and personal Microsoft accounts (such as Skype, Xbox, Outlook.com) | Multitenant | All users with a work, school, or personal Microsoft account can use your application or API. It includes schools and businesses that use Microsoft 365, as well as personal accounts that are used to sign in to services like Xbox and Skype. *Use this option to target the widest set of Microsoft accounts.* |

#### Best practices for multitenant apps

Building great multitenant apps can be challenging because of the number of different policies that IT administrators can set in their tenants. If you choose to build a multitenant app, follow these best practices:

- Test your app in a tenant that has configured Conditional Access policies.
- Follow the principle of least user access to ensure that your app only requests permissions it actually needs.
- Provide appropriate names and descriptions for any permissions you expose as part of your app. This helps users and admins know what they're agreeing to when they attempt to use your app's APIs. For more information, see the best practices section in the permissions guide.


## Implement application registration

Each application you want the Microsoft identity platform to perform identity and access management (IAM) for must be registered. Register an app in the Azure portal so the Microsoft identity platform can provide authentication and authorization services for your application and its users. Whether it's a client application, like a web or mobile app, or a web API that backs a client app, registering it establishes a trust relationship between your application and the identity provider, the Microsoft identity platform.


## Register an application

Registering your application establishes a trust relationship between your app and the Microsoft identity platform. The trust is unidirectional: Your app trusts the Microsoft identity platform—not the other way around.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/) using an Administrator account.
2. Open the portal menu and then select **Identity**.
3. On the **Identity** menu, under **Applications**, select **App registrations.**
4. On the **App registrations** page, on the menu, select **+ New registration**.
5. On the **register an application** dialog, register an app named **Demo app** using the default values. You don't need to enter the redirect URI.
6. When complete, you'll be directed to the **Demo app** screen.

### Add a redirect URI

A redirect URI is the location where the Microsoft identity platform redirects a user's client and sends security tokens after authentication. In a production web application, for example, the redirect URI is often a public endpoint where your app is running. During development, it's common to also add the endpoint where you run your app locally.

Add and modify redirect URIs for your registered applications by configuring their platform settings.

### Configure platform settings

Settings for each application type, including redirect URIs, are configured in **Platform configurations** in the Azure portal. Some platforms, like **Web** and **Single-page applications**, require you to manually specify a redirect URI. For other platforms, like mobile and desktop, you can select from redirect URIs generated for you when you configure their other settings.

To configure application settings based on the platform or device you're targeting:

1. Select your application in **App registrations** in the Azure portal.
2. Under **Manage**, select **Authentication**.
3. Under **Platform configurations**, select **Add a platform**.
4. In **Configure platforms**, select the tile for your application type (platform) to configure its settings.        **Platform** **Configuration settings**     Web Enter a **Redirect URI** for your app, the location where Microsoft identity platform redirects a user's client and sends security tokens after authentication. Select this platform for standard web applications that run on a server.   Single-page application Enter a **Redirect URI** for your app, the location where Microsoft identity platform redirects a user's client and sends security tokens after authentication. Select this platform if you're building a client-side web app in JavaScript or with a framework like Angular, Vue.js, React.js, or Blazor WebAssembly.   iOS/macOS Enter the app **Bundle ID**, found in XCode in *Info.plist* or Build Settings.A redirect URI is generated for you when you specify a Bundle ID.   Android Enter the app **Package name**, which you can find in the AndroidManifest.xml file, and generate and enter the **Signature hash**.A redirect URI is generated for you when you specify these settings.   Mobile and desktop applications Select one of the **Suggested redirect URIs** or specify a **Custom redirect URI**.For desktop applications, we recommend:https://login.microsoftonline.com/common/oauth2/nativeclient Select this platform for mobile applications that aren't using the latest Microsoft Authentication Library (MSAL) or aren't using a broker. Also select this platform for desktop applications.
5. Select **Configure** to complete the platform configuration.

### Add credentials

Credentials are used by confidential client applications that access a web API. Examples of confidential clients include web apps, other web APIs, and service-type and daemon-type applications. Credentials allow your application to authenticate as itself, requiring no interaction from a user at runtime.

You can add both certificates and client secrets (a string) as credentials to your confidential client app registration.

### Add a certificate

Sometimes called a *public key*, certificates are the recommended credential type, because as they provide a higher level of assurance than a client secret. When using a trusted public certificate, you can add the certificate using the Certificates & secrets feature. Your certificate must be one of the following file types: `.cer`, `.pem`, `.crt`.

### Add a client secret

The client secret, also known as an *application password*, is a string value your app can use in place of a certificate to identity itself. It's the easier of the two credential types to use. It's often used during development, but is considered less secure than a certificate. You should use certificates in your applications running in production.

1. Select your application in **App registrations** in the Azure portal.
2. Select **Certificates and secrets**, then select **New client secret**.
3. Add a description for your client secret.
4. Select a duration.
5. Select **Add**.
6. **Record the secret's value** for use in your client application code; It's *never displayed again* after you leave this page.

### Register the web API

To provide scoped access to the resources in your web API, you must first register the API with the Microsoft identity platform.

1. Perform the steps above.
2. Skip the **Add a redirect URI** and **Configure platform settings** sections. You don't need to configure a redirect URI for a web API since no user is logged in interactively.
3. Skip the **Add credentials** section for now. Only if your API accesses a downstream API would it need its own credentials—a scenario not covered in this article.

With your web API registered, you're ready to add the scopes that your API's code can use to provide granular permission to consumers of your API.

### Add a scope

The code in a client application requests permission to perform operations defined by your web API by passing an access token along with its requests to the protected resource (the web API). Your web API then performs the requested operation only if the access token it receives contains the scopes (also known as application permissions) required for the operation.

First, follow these steps to create an example scope named Employees.Read.All:

1. Sign in to the Azure portal.
2. If you have access to multiple tenants, use the **Directory + subscription** filter in the top menu to select the tenant containing your client app's registration.
3. Select **Microsoft Entra ID**, then **App registrations**, and then select your API's app registration.
4. Select **Expose an API**, then **Add a scope**.
5. You're prompted to set an **Application ID URI** if you haven't yet configured one. The App ID URI acts as the prefix for the scopes you'll reference in your API's code, and it must be globally unique. You can use the default value provided, which is in the form `api://` , or specify a more readable URI like `https://contoso.com/api`.
6. Next, specify the scope's attributes in the **Add a scope pane**. For this walk-through, you can use the example values or specify your own.    **Field** **Description** **Example**     Scope name The name of your scope. A common scope naming convention is resource.operation.constraint. Employees.Read.All   Who can consent The admin chooses if this scope can be consented to by users, or if admin consent is required. Select Admins only for higher-privileged permissions. Admins and users   Admin consent display name A short description of the scope's purpose that only admins will see. Read-only access to employee records   Admin consent description A more detailed description of the permission granted by the scope that only admins will see. Allow the application to have read-only access to all employee data.   User consent display name A short description of the scope's purpose. Shown to users only if you set the *Who can consent to Admins and users*. Read-only access to your employee records   User consent description A more detailed description of the permission granted by the scope. Shown to users only if you set the *Who can consent to Admins and users*. Allow the application to have read-only access to your employee data.
7. Set the **State** to **Enabled**, and then select **Add scope**.
8. (Optional) To suppress prompting for consent by users of your app to the scopes you've defined, you can *pre-authorize* the client application to access your web API. Pre-authorize *only* those client applications you trust since your users won't have the opportunity to decline consent.
  1. Under **Authorized client applications**, select **Add a client application.**
  2. Enter the **Application (client) ID** of the client application you want to pre-authorize. For example, that of a web application you've previously registered.
  3. Under **Authorized scopes**, select the scopes for which you want to suppress consent prompting, then select **Add application**.
  4. If you followed this optional step, the client app is now a pre-authorized client app (PCA), and users won't be prompted for their consent when signing into it.

#### Add a scope requiring admin consent

Next, add another example scope named Employees.Write.All that only admins can consent to. Scopes that require admin consent are typically used for providing access to higher-privileged operations, often by client applications that run as backend services or daemons that don't sign in a user interactively.

To add the Employees.Write.All example scope, follow the steps above and specify these values in the **Add a scope** pane:

| **Field** | **Example value** |
|---|---|
| Scope name | Employees.Write.All |
| Who can consent | Admins only |
| Admin consent display name | Write access to employee records |
| Admin consent description | Allow the application to have write access to all employee data. |
| User consent display name | None (leave empty) |
| User consent description | None (leave empty) |

#### Verify the exposed scopes

If you successfully added both example scopes described in the previous sections, they'll appear in the **Expose an API** pane of your web API's app registration, similar to this image:

As shown in the image, a scope's full string is the concatenation of your web API's **Application ID URI** and the scope's **Scope name**.

For example, if your web API's application ID URI is `https://contoso.com/api` and the scope name is Employees.Read.All, the full scope is:

`https://contoso.com/api/Employees.Read.All`

#### Using the exposed scopes

Next, you'll configure a client app's registration with access to your web API and the scopes you defined by following the steps above.

Once a client app registration is granted permission to access your web API, the client can be issued an OAuth 2.0 access token by the Microsoft identity platform. When the client calls the web API, it presents an access token whose scope (scp) claim is set to the permissions you've specified in the client's app registration.

You can expose additional scopes later as necessary. Consider that your web API can expose multiple scopes associated with several operations. Your resource can control access to the web API at runtime by evaluating the scope (scp) claim(s) in the OAuth 2.0 access token it receives.

#### What is going on behind the scenes

- The app registration is created in the home tenant
- The app is instantiated with a security principal in Microsoft Entra ID
- The security principal is granted consent by either the first user or admin, based on the setup of the exposed API
- The security principal is granted the security token as the user accesses the application and uses the API


## Configure permission for an application

Admins will need to configure permissions and consent in the Microsoft identity platform endpoint.

Applications that integrate with Microsoft identity platform follow an authorization model that gives users and administrators control over how data can be accessed. The implementation of the authorization model has been updated on the Microsoft identity platform endpoint, and it changes how an app must interact with the Microsoft identity platform. This unit covers the basic concepts of this authorization model, including scopes, permissions, and consent.

### Scopes and permissions

The Microsoft identity platform implements the OAuth 2.0 authorization protocol, a method through which a third-party app can access web-hosted resources on behalf of a user. Any web-hosted resource that integrates with the Microsoft identity platform has a resource identifier, or *Application ID URI*. For example, Microsoft's web-hosted resources include:

- Microsoft Graph: `https://graph.microsoft.com`
- Microsoft 365 Mail API: `https://outlook.office.com`
- Azure Key Vault: `https://vault.azure.net`

The same is true for any third-party resources that have integrated with the Microsoft identity platform. Any of these resources also can define a set of permissions that can be used to divide the functionality of that resource into smaller chunks. As an example, Microsoft Graph has defined permissions for tasks such as:

- Read a user's calendar.
- Write to a user's calendar.
- Send mail as a user.

When the app defines these types of permissions, the resource has fine-grained control over its data and how API functionality is exposed. A third-party app can request these permissions from users and administrators who must approve the request before the app can access data or act on a user's behalf. App development organization can put the functions of resources into smaller permission sets, developers can build third-party apps to request only the specific permissions that they need to perform their function. Users and administrators can know exactly what data the app has access to, and they can be more confident that it isn't behaving with malicious intent. Developers should always abide by the concept of least privilege, asking for only the permissions they need for their applications to function.

In OAuth 2.0, these types of permissions are called *scopes*. They're also often referred to as *permissions*. A permission is represented in the Microsoft identity platform as a string value. Continuing with the Microsoft Graph example, the string value for each permission is:

- Read a user's calendar by using Calendars.Read
- Write to a user's calendar by using Calendars.ReadWrite
- Send mail as a user using by Mail.Send

An app most commonly requests these permissions by specifying the scopes in requests to the Microsoft identity platform authorize endpoint. However, certain high-privilege permissions can only be granted through administrator consent and requested/granted using the administrator consent endpoint.

### Permission types

Microsoft identity platform supports two types of permissions: **delegated permissions** and **application permissions**.

- **Delegated permissions** are used by apps that have a signed-in user present. For these apps, either the user or an administrator consents to the permissions that the app requests, and the app is delegated permission to act as the signed-in user when making calls to the target resource. Some delegated permissions can be consented to by non-administrative users, but some higher-privileged permissions require administrator consent. To learn which administrator roles can consent to delegated permissions, see Administrator role permissions in Microsoft Entra ID.
- **Application permissions** are used by apps that run without a signed-in user present; for example, apps that run as background services or daemons. Only an administrator can consent to application permissions.

*Effective permissions* are those that your app will have when making requests to the target resource. It's important to understand the difference between the delegated and application permissions that your app is granted and its effective permissions when making calls to the target resource.

- For delegated permissions, the *effective permissions* of your app will be the least privileged intersection of the delegated permissions the app has been granted (via consent) and the privileges of the currently signed-in user. Your app can never have more privileges than the signed-in user. Within organizations, the privileges of the signed-in user are determined by policy or by membership in one or more administrator roles. To learn which administrator roles can consent to delegated permissions, see Administrator role permissions in Microsoft Entra ID.
- For example, assume your app has been granted the *User.ReadWrite.All* delegated permission. This permission nominally grants your app permission to read and update the profile of every user in an organization. If the signed-in user is an application administrator, your app will be able to update the profile of every user in the organization. However, if the signed-in user isn't in an administrator role, your app will be able to update only the profile of the signed-in user. It will not be able to update the profiles of other users in the organization, because the user whom it has permission to act on behalf of doesn't have those privileges.
- For application permissions, the *effective permissions* of your app will be the full level of privileges implied by the permission. For example, an app that has the *User.ReadWrite.All* application permission can update the profile of every user in the organization.

### OpenID Connect Scopes

The Microsoft identity platform implementation of OpenID Connect has a few well-defined scopes that are also hosted on the Microsoft Graph: openid, email, profile, and offline_access. The address and phone OpenID Connect scopes aren't supported.

Requesting the OIDC scopes and a token will give you a token to call the UserInfo endpoint.

#### Openid

If an app performs sign-in by using OpenID Connect, it must request the openid scope. The openid scope shows on the work account consent page as the `sign you in` permission and on the personal Microsoft account consent page as the "View your profile and connect to apps and services using your Microsoft account" permission. With this permission, an app can receive a unique identifier for the user in the form of the sub claim. It also gives the app access to the UserInfo endpoint. The openid scope can be used at the Microsoft identity platform token endpoint to acquire ID tokens, which can be used by the app for authentication.

#### email

The email scope can be used with the openid scope and any others. It gives the app access to the user's primary email address in the form of the email claim. The email claim is included in a token only if an email address is associated with the user account, which isn't always the case. If it uses the email scope, your app should be prepared to handle a case in which the email claim doesn't exist in the token.

#### profile

The profile scope can be used with the openid scope and any others. It gives the app access to a substantial amount of information about the user. The information it can access includes, but isn't limited to, the user's given name, surname, preferred username, and object ID. For a complete list of the profile claims available in the `id_tokens` parameter for a specific user, see the `id_tokens` reference.

#### offline_access

The offline_access scope gives your app access to resources on behalf of the user for an extended time. On the consent page, this scope appears as the "Maintain access to data you have given it access to" permission. When a user approves the `offline_access` scope, your app can receive refresh tokens from the Microsoft identity platform token endpoint. Refresh tokens are long-lived. Your app can get new access tokens as older ones expire.

On the Microsoft identity platform (requests made to the v2.0 endpoint), your app must explicitly request the offline_access scope to receive refresh tokens. This means that when you redeem an authorization code in the OAuth 2.0 authorization code flow, you'll receive only an access token from the /token endpoint. The access token is valid for a short time, usually expiring in one hour. At that point, your app needs to redirect the user back to the /authorize endpoint to get a new authorization code. During this redirect, depending on the type of app, the user might need to enter their credentials again or consent again to permissions.

Note

When you are using a Single Page Application (SPA) the refresh token is always provided.

Note

This permission appears on all consent screens today, even for flows that don't provide a refresh token (the *implicit flow*). This is to cover scenarios where a client can begin within the implicit flow, and then move on to the code flow where a refresh token is expected.

### Requesting individual user consent

In an OpenID Connect or OAuth 2.0 authorization request, an app can request the permissions it needs by using the scope query parameter. When a user signs into an app, the app sends a request for permission. The scope parameter is a space-separated list of delegated permissions that the app is requesting. Each permission is indicated by appending the permission value to the resource's identifier (the Application ID URI). In the request example, the app needs delegated permission to read the user's calendar and send mail as the user.

After the user enters their credentials, the Microsoft identity platform endpoint checks for a matching record of user consent. If the user hasn't consented to any of the requested permissions in the past, nor has an administrator consented to these permissions on behalf of the entire organization, the Microsoft identity platform endpoint asks the user to grant the requested permissions.

Note

At this time, the offline_access ("Maintain access to data you have given it access to") and user.read ("Sign you in and read your profile") permissions are automatically included in the initial consent to an application. These permissions are generally required for proper app functionality; offline_access gives the app access to refresh tokens, critical for native and web apps, while user.read gives access to the sub claim, allowing the client or app to correctly identify the user over time and access rudimentary user information.

When the user approves the permission request, consent is recorded, and the user doesn't have to consent again on subsequent sign-ins to the application.

### Requesting consent for an entire tenant

Often, when an organization purchases a license or subscription for an application, the organization wants to proactively configure the application for use by all members of the organization. As part of this process, an administrator can grant consent for the application to act on behalf of any user in the tenant. If the admin grants consent for the entire tenant, the organization's users won't see a consent page for the application. Additionally, applications must use the admin consent endpoint to request application permissions.


## Grant tenant-wide admin consent to applications

For applications your organization has developed or for those that are registered directly in your Microsoft Entra tenant, you can grant tenant-wide admin consent from App registrations in the Azure portal.

Warning

Granting tenant-wide admin consent to an application will grant the app and the app's publisher access to your organization's data. Carefully review the permissions the application is requesting before granting consent.

Granting tenant-wide admin consent requires you to sign in as a user that is authorized to consent on behalf of the organization. This includes Privileged Role Administrator. A user can also be authorized to grant tenant-wide consent if they're assigned a custom directory role that includes the permission to grant permissions to applications.

1. In a previous exercise, you created an app named Demo app. If necessary, in Microsoft Azure, browse to **Microsoft Entra ID** then **App registrations** then Demo app.
2. On the **Demo app** screen, locate and copy and save each **Application (client) ID** and **Directory (tenant) ID** values so that you can use them later.
3. In the left navigation, under **Manage**, select **API permissions**.
4. Under **Configured permissions**, select **Grant admin consent**.
5. Review the dialogue box, and then select **Yes.**

Warning

Granting tenant-wide admin consent through App registrations will revoke any permissions that had previously been granted tenant-wide. Permissions previously granted by users on their own behalf won't be affected.

### Grant admin consent in Enterprise apps

You can grant tenant-wide admin consent through Enterprise applications if the application has already been provisioned in your tenant.

1. In Microsoft Azure, browse to **Microsoft Entra ID**, then **Enterprise applications**, and then **Demo app**.
2. On the **Demo app** screen, in the left navigation, under **Security,** select **Permissions.**
3. Under **Permissions**, select **Grant admin consent.**
4. When prompted, sign in using your Privileged Role Administrator account.
5. In the **Permissions requested** dialog box, review the information and then select **Accept**.

### Construct the URL for granting tenant-wide admin consent

When you're granting tenant-wide admin consent using either method described above, a window opens from the Azure portal to prompt for tenant-wide admin consent. If you know the client ID of the application (also known as the application ID), you can build the same URL to grant tenant-wide admin consent.

1. The tenant-wide admin consent URL follows the following format: `https://login.microsoftonline.com/{tenant-id}/adminconsent?client_id={client-id}` where:
  - `{client-id}` is the application's client ID (also known as app ID).
  - `{tenant-id}` is your organization's tenant ID or any verified domain name.

2. As always, carefully review the permissions an application requests before granting consent.

### Admin-restricted permissions

Some high-privilege permissions in the Microsoft ecosystem can be set to *admin-restricted*. Examples of these kinds of permissions include:

- Read all user's full profiles by using User.Read.All
- Write data to an organization's directory by using Directory.ReadWrite.All
- Read all groups in an organization's directory by using Groups.Read.All

Although a consumer user might grant an application access to this kind of data, organizational users are restricted from granting access to the same set of sensitive company data. If your application requests access to one of these permissions from an organizational user, the user receives an error message that says they're not authorized to consent to your app's permissions.

If your app requires access to admin-restricted scopes for organizations, you should request them directly from a company administrator, also by using the admin consent endpoint, described next.

If the application is requesting high-privilege delegated permissions and an administrator grants these permissions via the admin consent endpoint, consent is granted for all users in the tenant.

If the application is requesting application permissions and an administrator grants these permissions via the admin consent endpoint, this grant isn't given on behalf of any specific user. Instead, the client application is granted permissions directly. These types of permissions are only used by daemon services and other non-interactive applications that run in the background.

### Using the admin consent endpoint

Note

After the admin grants admin consent using the admin consent endpoint, you've finished granting admin consent and users don't need to perform any further additional actions. After granting admin consent, users can get an access token via a typical auth flow, and the resulting access token will have the consented permissions.

When a Company Administrator uses your application and is directed to the authorized endpoint, Microsoft identity platform will detect the user's role and ask them if they would like to consent on behalf of the entire tenant for the permissions you've requested. However, there's also a dedicated admin consent endpoint you can use if you would like to proactively request that an administrator grants permission on behalf of the entire tenant. Using this endpoint is also necessary for requesting application permissions (which can't be requested using the authorized endpoint).

If you follow these steps, your app can request permissions for all users in a tenant, including admin-restricted scopes. This is a high-privilege operation and should only be done if necessary for your scenario.

#### Request the permissions in the app registration portal

Applications are able to note which permissions they require (both delegated and application) in the app registration portal. This allows use of the /.default scope and the Azure portal's "Grant admin consent" option. In general, it's best practice to ensure that the permissions statically defined for a given application are a superset of the permissions that it will be requesting dynamically/incrementally.

#### To configure the list of statically requested permissions for an application

1. Go to your application in the Azure portal – App registrations experience, or create an app if you haven't already.
2. Locate the **API Permissions** section, then select **Add a permission**.
3. Select **Microsoft Graph** from the list of available APIs and then add the permissions that your app requires.
4. **Save** the app registration.

### Recommended: Sign the user into your app

Typically, when you build an application that uses the admin consent endpoint, the app needs a page or view in which the admin can approve the app's permissions. This page can be part of the app's sign-up flow, part of the app's settings, or a dedicated "connect" flow. In many cases, it makes sense for the app to show this "connect" view only after a user has signed in with a work or school Microsoft account.

When you sign the user into your app, you can identify the organization to which the admin belongs before asking them to approve the necessary permissions. Although not strictly necessary, it can help you create a more intuitive experience for your organizational users. To sign in the user, follow the Microsoft identity platform protocol tutorials.

### Using permissions

After the user consents to permissions for your app, your app can acquire access tokens that represent your app's permission to access a resource in some capacity. An access token can be used only for a single resource, but encoded inside the access token is every permission that your app has been granted for that resource. When you're ready to request permissions from your organization's admin, you can redirect the user to the Microsoft identity platform *admin consent endpoint*. Line breaks are for legibility only.

```
GET https://login.microsoftonline.com/\{tenant\}/v2.0/adminconsent?

client_id=00001111-aaaa-2222-bbbb-3333cccc4444

state=12345

redirect_uri=http://localhost/myapp/permissions

scope=

    https://graph.microsoft.com/calendars.read

    https://graph.microsoft.com/mail.send
```

| **Parameter** | **Condition** | **Description** |
|---|---|---|
| tenant | Required | The directory tenant that you want to request permission from. Can be provided in GUID or friendly name format OR generically referenced with organizations as seen in the example. Don't use "common," as personal accounts can\t provide admin consent except in the context of a tenant. To ensure best compatibility with personal accounts that manage tenants, use the tenant ID when possible. |
| client_id | Required | The **Application (client) ID** that the Azure portal – App registrations experience assigned to your app. |
| redirect_uri | Required | The redirect URI where you want the response to be sent for your app to handle. It must exactly match one of the redirect URIs that you registered in the app registration portal. |
| state | Recommended | A value included in the request that will also be returned in the token response. It can be a string of any content you want. Use the state to encode information about the user's state in the app before the authentication request occurred, such as the page or view they were on. |
| scope | Required | Defines the set of permissions being requested by the application. This can be either static (using /.default) or dynamic scopes. This can include the OIDC scopes (openid, profile, email). |

At this point, Microsoft Entra ID requires a tenant administrator to sign in to complete the request. The administrator is asked to approve all the permissions that you've requested in the scope parameter.


## Implement application authorization

**Application roles** are used to assign permissions to users. You define app roles by using the Azure portal. When a user signs into the application, Microsoft Entra ID emits a roles claim for each role that the user has been granted individually to the user and from their group membership.

There are two ways to declare app roles by using the Azure portal:

- App roles UI, then Preview
- App manifest editor


## Exercise add app roles to an application and receive tokens

You can declare app roles using the app roles UI.

Important

The app roles portal UI feature is in public preview. This preview is provided without a service-level agreement and isn't recommended for production workloads. Certain features might be unsupported or have constrained capabilities.

To create an app role by using the Azure portal's user interface:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/) using an Administrator account.
2. Open the portal menu and then select **Identity**.
3. On the **Identity** menu, under **Applications,** select **App registrations**.
4. Select **App roles**, and then select **Create app role**.
5. In the **Create app role** pane, in the **Display name** box, enter **Survey Writer**.
6. Under **Allow member types**, select **User/Groups**.
7. In the **Value** box, enter **Survey.Create**.
8. In the **Description** box, enter **Writers can create surveys**.
9. Notice that the description is a mandatory field.
10. Verify the **Do you want to enable this app role** is selected and then select **Apply.**

### Assign users and groups to roles

Once you've added app roles in your application, you can assign users and groups to the roles. Assign users and groups to roles through the portal's UI or programmatically using [Microsoft Graph](https://learn.microsoft.com/en-us/graph/api/user-post-approleassignments). When the users assigned to the various app roles sign in to the application, their tokens will have their assigned roles in the roles claim.

To assign users and groups to roles by using the Azure portal:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/).
2. In the Identity navigation menu on the left, open **Applications** select **Enterprise applications.**
3. In the **All applications** list, select **Demo app**.
4. This app was created in an earlier exercise.
5. Under **Manage**, select **Users and groups.**
6. On the menu, select **+ Add user/group.**
7. On the **Add Assignment** dialog, select **Users and groups**.
8. A list of users and security groups is displayed. You can search for a certain user or group, as well as select multiple users and groups that appear in the list.
9. After you have selected users and groups, select **Select**.
10. When using the **Select a role** assignment, all the roles that you've defined for the application are displayed.
11. Choose a role and then select **Select**.
12. Select **Assign** to finish the assignment of users and groups to the app.
13. Confirm that the users and groups you added appear in the **Users and groups** list.


## Manage and monitor application by using app governance

Cyberattacks have become increasingly sophisticated in the ways they exploit the apps you have deployed in your on-premises and cloud infrastructures. Cyberattacks establish a starting point for privilege escalation, lateral movement, and exfiltration of your data. To understand the potential risks and stop these types of attacks, you need to gain clear visibility into your organization’s app compliance posture. Then you need to look for when an app exhibits anomalous behaviors and to respond when these behaviors present risks to your environment, data, and users.

The app governance add-on feature to Defender for Cloud Apps is a security and policy management capability designed for OAuth-enabled apps that access Microsoft 365 data through Microsoft Graph APIs. App governance delivers full visibility, remediation, and governance into how these apps and their users access, use, and share your sensitive data stored in Microsoft 365 through actionable insights and automated policy alerts and actions.

App governance provides you with comprehensive:

- **Insights**: See a view of all the third-party apps for the Microsoft 365 platform in your tenant on a single dashboard. You can see all the apps’ status and alert activities and react or respond to them.
- **Governance**: Create proactive or reactive policies for app and user patterns and behaviors and protect your users from using non-compliant or malicious apps and limiting the access of risky apps to your data.
- **Detection**: Be alerted and notified when there are anomalies in app activity and when non-compliant, malicious, or risky apps are used.
- **Remediation**: Along with automatic remediation capabilities, use remediation controls in a timely manner to respond to anomalous app activity detections.

### Enable Defender for Cloud Apps sync

To enable app governance sync with Defender for Cloud Apps, follow these steps:

1. Ensure Office 365 is connected in Defender for Cloud Apps.
2. Ensure Office 365 Microsoft Entra ID apps are enabled.
3. Go to your Defender for Cloud Apps portal – `https://portal.cloudappsecurity.com`
4. Select the gear icon (top-right corner) and select Settings.
5. Under Threat Protection, select App Governance.
6. Select Enable App Governance integration, and then select Save. To verify the integration with Defender for Cloud Apps is active, look for the app governance policies listed below to appear in Defender for Cloud Apps. The new policies might take few minutes to appear once integration is enabled.
  - Microsoft 365 OAuth app Reputation
  - Microsoft 365 OAuth Phishing Detection
  - Microsoft 365 OAuth App Governance


## Module assessment

Choose the best response for each of the questions below.

### Check your knowledge


## Summary and resources

Now that you reviewed this module, you're able to:

- Plan your line-of-business application registration strategy.
- Implement application registrations.
- Configure application permissions.
- Establish and maintain an application governance process.

### Resources

To explore with more depth, use these resources:

- [App governance add-on to Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-manage-app-governance)
- [Configure adaptive session lifetime policies](https://learn.microsoft.com/en-us/entra/identity/conditional-access/howto-conditional-access-session-lifetime)


---

# Register apps using Microsoft Entra ID

_https://learn.microsoft.com/en-us/training/modules/register-apps-use-microsoft-entra-id/_


## Introduction

Application registration in Microsoft Entra ID is the process of ensuring that the identity system is aware of what applications are used. This way you can confirm the user has access to the app and that the app has access to any needed resources. You ensure the security and privacy of users, apps, and your data.

### Scenario

Imagine you're an application developer who wants to create an application that requires authentication and authorization. You want to ensure that only authorized users can access the app and that the app can access the necessary resources.

By registering your application with Microsoft Entra ID, you can provide an identity configuration for your application that allows it to integrate with the Microsoft identity platform. This registration process enables several key capabilities:

- **Custom branding**: Customize the branding of your application in the sign-in dialog box. This branding is important because signing in is the first experience a user has with your app.
- **Tenant configuration**: Choose between single-tenant application (your organization), or multitenant application (accept accounts from other tenants). You can also allow personal Microsoft accounts or social accounts from LinkedIn, Google, and so on.
- **Permission management**: Request scope permissions, such as the user.read scope, which grants permission to read the profile of the signed-in user. Define scopes that control access to your web API.
- **Secure authentication**: Configure secure authentication methods. For confidential client applications that can hold credentials securely (like web applications with trusted back-end servers), you can use client secrets, certificates, or modern alternatives like managed identities for enhanced security.

### Learning objectives

- Benefits of registering an app.
- Single-tenant versus multitenant apps.
- What happens when an app is registered.
- Relationship between application objects and service principals.

### Goals

The goal of this module is to teach you how to register your application with Microsoft Entra ID, then how to configure it to integrate with the Microsoft identity platform. Learn how to customize the branding of your application in the sign-in dialog box. Then explore how to request scope permissions, and how to share a secret with the Microsoft identity platform that proves the app's identity. Finally, learn about single-tenant versus multitenant apps, application objects, and service principal objects, and the relationship between them.


## Plan for app registration

Application registration in Microsoft Entra ID is the process of ensuring that your identity system is aware of what applications are used. You can confirm the user has access to the app and that the app has access to any needed resources. App registration ensures the security and privacy of users, apps, and your data.

### Benefits of registering an app

When you register your application with Microsoft Entra ID, you're providing an identity configuration for your application that allows it to integrate with the Microsoft identity platform. Registering the app also allows you to:

- Customize the branding of your application in the sign-in dialog.
  - Branding is important because signing in is the first experience a user has with your app.

- Decide if you want to allow users to sign in only if they belong to your organization.
  - Signing in to your own organization is known as a single-tenant application.
  - You can allow users to sign in by using any work or school account, which is known as a multitenant application.
  - You can also allow personal Microsoft accounts or a social account from LinkedIn, Google, and so on.

- Request scope permissions.
  - For example, you can request the "user.read" scope, which grants permission to read the profile of the signed-in user.

- Define a scope that defines access to your web API.
  - Typically, when an app wants to access your API, it needs to request permissions to the scopes you define.

- Share a secret with the Microsoft identity platform that proves the app's identity.
  - Using a secret is relevant in the case where the app is a confidential client application. A confidential client application is an application that can hold credentials securely, like a web client. A trusted back-end server is required to store the credentials.

#### Single tenant versus multitenant apps

As the name implies, an app registered as a single-tenant app is only available to users and resources in that specific tenant. For apps registered as multitenant apps, users from different tenants can access the apps. The multitenant scenario should be used intentionally when needed. In the multitenant scenario, a service principal object is created in the directory for each tenant the app has users. The creation of the service principal happens at the time of app registration in the source tenant, and during the first user authentication in other tenants. When it comes to developing apps, developers can choose to configure their app to be either single-tenant or multitenant during app registration in the Microsoft Entra admin center.

- Single-tenant apps are only available in the tenant they were registered in, also known as their home tenant.
- Multitenant apps are available to users in both their home tenant and other tenants.

In the Microsoft Entra admin center, you can configure your app to be single-tenant or multitenant by setting the audience as follows.

| **Audience** | **Single/multitenant** | **Who can sign in** |
|---|---|---|
| Accounts in this directory only | Single-tenant | All user and guest accounts in your directory can use your application or API. |
| Accounts in any Microsoft Entra directory | Multitenant | All users and guests with a work or school account from Microsoft can use your application or API. Access includes schools and businesses that use Microsoft 365. |
| Accounts in any Microsoft Entra directory and personal Microsoft accounts (such as Skype, Xbox, Outlook.com) | Multitenant | All users with a work or school, or personal Microsoft account can use your application or API. It includes schools and businesses that use Microsoft 365 as well as personal accounts that are used to sign in to services like Xbox and Skype. |

### What happens when an app is registered

After the app is registered, it's given a unique identifier that it shares with the Microsoft identity platform when it requests tokens. If the app is a confidential client application, it shares the secret or the public key depending on whether certificates or secrets were used.

Important

As of August 2024, new applications receive v2 access tokens by default (instead of v1) for improved security. This change affects how tokens are formatted and what claims they contain.

There are two representations of applications in Microsoft Entra ID:

- **Application objects** - Although there are exceptions, application objects can be considered the definition of an application.
- **Service principals** - Can be considered an instance of an application. Service principals generally reference an application object, and one application object can be referenced by multiple service principals across directories.

The Microsoft identity platform represents applications by using a model that fulfills two main functions. First, the identity platform will Identify the app by the authentication protocols it supports. And second, it provides all the identifiers, URLs, secrets, and related information that are needed to authenticate.

The Microsoft identity platform:

- Holds all the data required to support authentication at runtime.
- Holds all the data for deciding what resources an app might need to access, and under what circumstances a given request should be fulfilled.
- Provides infrastructure for implementing app provisioning within the app developer's tenant, and to any other Microsoft Entra tenant.
- Handles user consent during token request time and facilitates the dynamic provisioning of apps across tenants.

Consent is the process of a resource owner granting authorization for a client application to access protected resources, under specific permissions, on behalf of the resource owner. Microsoft Entra enables users and administrators to dynamically grant or deny consent for the app to access resources on their behalf. And ultimately enables administrators to decide what apps are allowed to do and which users can use specific apps, and how the directory resources are accessed.


## Explore application objects and service principals

After completing the app registration, you have a globally unique instance of the app (the application object) that lives within your home tenant or directory. You also have a globally unique ID for your app (the app/client ID). In the Microsoft Entra admin center, you can then add secrets or certificates and scopes to make your app work, customize the branding of your app in the sign-in dialog, and more.

If you register an application in the Microsoft Entra admin center, an application object and a service principal object are automatically created in your home tenant. If you register/create an application using the Microsoft Graph APIs, creating the service principal object is a separate step.

Note

**Security Best Practice**: For applications authentication (workload identities), Microsoft recommends using certificates instead of passwords for enhanced security. For Azure workloads, managed identities are the preferred approach as they eliminate the need to manage credentials entirely.

### Application object

A Microsoft Entra application is defined by its application object, which resides in the Microsoft Entra tenant where the application was registered (known as the application's "home" tenant). An application object is used as a template or blueprint to create one or more service principal objects. A service principal is created in every tenant where the application is used. Similar to a class in object-oriented programming, the application object has some static properties that are applied to all the created service principals (or application instances).

The application object describes three aspects of an application:

- How the service can issue tokens in order to access the application
- The resources that the application might need to access
- The actions that the application can take

The application object might include (but not limited to):

- Name, logo, and publisher
- Redirect URIs
- Authentication credentials:
  - Certificates (recommended for enhanced security)
  - Client secrets (passwords - use only when certificates aren't feasible)

- API dependencies (OAuth)
- Published APIs/resources/scopes (OAuth)
- App roles
- Single sign-on (SSO) metadata and configuration
- User provisioning metadata and configuration
- Proxy metadata and configuration

### Service principal object

To access resources that secured by a Microsoft Entra tenant, the entity that requires access must be represented by a security principal. This requirement is true for both users (user principal) and applications (service principal). The security principal defines the access policy and permissions for the user/application in the Microsoft Entra tenant. This enables core features such as authentication of the user/application during sign-in, and authorization during resource access. The types of service principal:

- **Application** - The service principal is the local representation, or application instance, of a global application object in a single tenant or directory. In this case, a service principal is a concrete instance created from the application object and inherits certain properties from that application object. When an application is given permission to access resources in a tenant, a service principal object is created.
- **Managed identity** (Recommended for Azure workloads) - The service principal is used to represent a managed identity. Managed identities eliminate the need for developers to manage credentials, reducing security risks, and operational overhead. Managed identities provide an identity for applications to use when connecting to resources that support Microsoft Entra authentication. A managed identity is the preferred approach for Azure-hosted applications.
- **Legacy** - The service principal represents a legacy app, which is an app created before app registrations were introduced or an app created through legacy experiences. A legacy service principal can have credentials, service principal names, reply URLs, and other properties. Legacy service principals should be migrated to modern app registrations when possible.

The service principal can include:

- A reference back to an application object through the application ID property
- Records of local user and group application-role assignments
- Records of local user and admin permissions granted to the application
- Records of local policies including Conditional Access policy
- Records of alternate local settings for an application

### Relationship between application objects and service principals

The application object is the global representation of your application for use across all tenants, and the service principal is the local representation for use in a specific tenant. The application object serves as the template from which common and default properties are derived for use in creating corresponding service principal objects. An application object has:

- A one-to-one relationship with the software application
- A one-to-many relationship with its corresponding service principal object(s)

A service principal must be created in each tenant where the application is used, enabling it to establish an identity for sign-in and/or access to resources being secured by the tenant. A single-tenant application has only one service principal (in its home tenant), created and consented for use during application registration. A multitenant application also has a service principal created in each tenant where a user from that tenant has consented to its use.

### Managing Application Objects and Service Principals

Always have a management strategy and process for maintaining your service principals.

#### Consequences of Modifications and Deletion

Any changes made to your application object are reflected in its service principal object in the application's home tenant only. This means:

- Deleting an application object will also delete its home tenant service principal object
- However, restoring the application object through the Microsoft Entra admin center won't restore its corresponding service principal
- Service principals in other tenants (for multitenant apps) remain independent of the home tenant's application object

#### Finding Service Principals

You can find service principals associated with an application object in the Microsoft Entra admin center by navigating to the application registration overview and selecting **Managed application in local directory**.

Important

When working with workload identities (non-human identities like applications), always consider the security implications of credential management and prefer managed identities for Azure resources whenever possible.


## Create app registrations

This unit demonstrates registering an application in Microsoft Entra ID using a single-page application (SPA). To register a single-page application in the Microsoft identity platform, complete the following steps. The process is straightforward and requires only a few pieces of information.

Note

This example uses a single-page application, but the core registration process is similar for other application types (web apps, mobile apps, etc.). The main differences are in the platform-specific configuration steps.

### Create the app registration

  Steps are based on the Microsoft Entra admin center:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/) with appropriate permissions (at least Application Developer role).
2. Under the **Identity** menu, expand the **Applications** menu.
3. Select **App registrations**, then **New registration**.
4. Enter a **Name** for your application. Users of your app might see this name, and you can change it later.
5. Choose the **Supported account types** for the application. For most single-tenant applications, select "Accounts in this organizational directory only." Do NOT enter a Redirect URI at this stage.
6. Select **Register** to create the app registration.

Important

Record the **Application (client) ID** and **Directory (tenant) ID** from the Overview page, as you'll need these values to configure your application code.

### Configure the Single-Page Application Platform

Follow these steps to add a redirect URI for an app that uses MSAL.js 2.0 or later. MSAL.js 2.0+ supports the authorization code flow with Proof Key for Code Exchange (PKCE) and Cross-Origin Resource Sharing (CORS), which provides enhanced security compared to the legacy implicit grant flow.

1. In the **Microsoft Entra admin center**, select the app registration you created in the previous step.
2. Under **Manage**, select **Authentication**.
3. Select **+ Add a platform**.
4. Under **Web applications**, select the **Single-page application** tile.
5. Under **Redirect URIs**, enter a redirect URI (for example, `http://localhost:3000/` for local development).
6. Do **NOT** select either checkbox under **Implicit grant and hybrid flows** - legacy patterns no longer recommended.
7. Select **Save** to finish adding the redirect URI.

Note

**Security Note**: The Single-page application (SPA) platform configuration automatically enables the authorization code flow with PKCE. PKCE is more secure than the legacy implicit grant flow. Modern SPAs should use this approach.

### Registration Complete

The registration of your single-page application (SPA) is complete. You configured a redirect URI to which the client is redirected, and any security tokens are sent. By configuring your redirect URI using the Single-page application tile in the **Add a platform** pane, your application registration is configured to support the authorization code flow with PKCE and CORS.

**Next Steps:**

- Configure API permissions if your app needs to access Microsoft Graph or other APIs
- Add certificates or client secrets if your app type requires them (not needed for SPAs using authorization code flow)
- Test your configuration with your application code

Note

**Best Practice**: New app registrations are hidden from users by default. When you're ready for users to see the app on their My Apps page, you can enable it through **Enterprise apps** then **Properties** and set **Visible to users?** value to **Yes**.


## Configure app authentication

The settings for each application type, including redirect URIs, are configured in **Platform configurations** in the Microsoft Entra admin center. Some platforms, like **Web** and **Single-page applications**, require you to manually specify a redirect URI. For other platforms, like **mobile and desktop**, you can select from redirect URIs generated for you when you configure their other settings.

Important

Platform-specific configuration ensures that your application uses the appropriate authentication flow and security settings for each target environment.

To configure application settings based on the platform or device you're targeting, follow these steps:

1. Open the **Microsoft Entra admin center**, then under **Applications**, select **App registrations**.
2. Select your application.
3. Under **Manage**, select **Authentication**.
4. Under **Platform configurations**, select **Add a platform**.
5. Under **Configure platforms**, select the tile for your application type (platform) to configure its settings.        **Platform** **Configuration settings**     Web Enter a **Redirect URI** for your server-side web application. This URI is where the Microsoft identity platform redirects users and sends security tokens after authentication. You can also configure front-channel sign out URLs and token settings.   Single-page application Enter a **Redirect URI** for your client-side JavaScript application (Angular, React, Vue.js, or Blazor WebAssembly). Uses authorization code flow with Proof Key for Code Exchange (PKCE) for enhanced security. You can also configure front-channel sign out URLs.   iOS / macOS Enter the app **Bundle ID**. Find it in **Build Settings** or in Xcode in *Info.plist*. A redirect URI is automatically generated for you.   Android Enter the app **Package name** (found in *AndroidManifest.xml*) and generate the **Signature hash**. A redirect URI is automatically generated for you.   Mobile and desktop applications Select from suggested **Redirect URIs** or specify **Custom redirect URIs**. For desktop apps with embedded browser: `https://login.microsoftonline.com/common/oauth2/nativeclient`. For desktop apps with system browser: `http://localhost`. Choose based on your authentication library requirements.
6. Select **Configure** to complete the platform configuration.

Note

**Security Note**: Each platform type has specific security requirements. Single-page applications automatically use authorization code flow with PKCE, while web applications can use various flows depending on your configuration.

#### Redirect URI

A redirect URI (also called reply URL) is the location where the authorization server sends the user once the app has successfully authorized and granted an authorization code or access token. The authorization server sends the code or token to the redirect URI, so it's important you register the correct location as part of the app registration process.

**Critical Security Requirements:** The Microsoft Entra application model specifies these restrictions for redirect URIs:

- **HTTPS requirement**: Redirect URIs must begin with the scheme `https`. There are exceptions for localhost redirect URIs during development.
- **Case sensitivity**: Redirect URIs are case-sensitive and must match the case of the URL path of your running application.
- **Trailing slash handling**:
  - Redirect URIs not configured with a path segment are returned with a trailing slash (`/`) in the response
  - Redirect URIs that contain a path segment aren't appended with a trailing slash in the response

- **Special characters**: Redirect URIs don't support these special characters: `! $ ' ( ) , ;`

Note

**Best Practice**: Always test your redirect URIs in a development environment before deploying to production to ensure proper token handling and security.


## Configure API permissions

The Microsoft identity platform implements the OAuth 2.0 authorization protocol. OAuth 2.0 is a method through which an external app can access web-hosted resources on behalf of a user. Any web-hosted resource that integrates with the Microsoft identity platform has a resource identifier, or **Application ID URI**. The same is true for any external resources integrated with the Microsoft identity platform.

Any of these resources can also define a set of **permissions** (also called **scopes**) that can be used to divide the functionality of that resource into smaller chunks. As an example, Microsoft Graph has permissions to do the following tasks (among others):

- Read a user's calendar
- Write to a user's calendar
- Send mail as a user

**Security Benefits:** Because of these types of permission definitions, the resource has fine-grained control over its data and how API functionality is exposed. A external app can request these permissions from users and administrators, who must approve the request before the app can access data or act on a user's behalf. When a resource's functionality is chunked into small permission sets, external apps can be built to request only the permissions that they need to perform their function.

**Principle of Least Privilege:** Users and administrators can know exactly what data the app can access, and administrators can be more confident that the app isn't behaving with malicious intent. Developers should always request **least privilege**, asking for only the permissions they need for their applications to function.

### Configure API permissions

Configure **delegated permissions** to Microsoft Graph to enable your client application to perform operations on behalf of the logged-in user, for example reading their email or modifying their profile. By default, users of your client app are asked when they sign in to consent to the delegated permissions configured for it.

Important

Delegated permissions operate on behalf of the signed-in user, meaning the app can only access data that the user themselves could access. This provides an additional security layer beyond just the app's permissions.

1. Sign in to the **Microsoft Entra admin center**.
2. Select **Applications** then **App registrations**, and then select your client application.
3. Select **API permissions** then **Add a permission** > **Microsoft Graph**.
4. Select **Delegated permissions**. Microsoft Graph exposes many permissions, with the most commonly used shown at the top of the list.
5. Under **Select permissions**, select the following permissions:    **Permission** **Description** **Use Case**     email View users' email address Display user's email in app UI   offline_access Maintain access to data you gave it access to Enable refresh tokens for long-term access   openid Sign users in Basic authentication (required for sign-in)   profile View users' basic profile Display user's name and basic profile info
6. Select **Add permissions** to complete the process.

Note

These are the basic **OpenID Connect** scopes commonly requested by most applications. You may need additional permissions based on your specific application requirements.

**Admin Consent**: As an administrator, you can grant consent on behalf of all users in your organization, eliminating the need for individual user consent. Admin concent is useful for organizational applications where admin approval is preferred or required by policy.


## Create app roles

**App roles** are a powerful feature you can and should configure when performing an app registration. An app role is a custom claim that can be applied to users, groups, or applications. The claim appears in the token generated when a user authenticates for an app. The app role data in the token can then be used in the application for authorization purposes.

**Key Benefits:**

- **Alternative to Group Claims**: App roles provide an alternative to using groups for authorization, which helps avoid group overage issues and doesn't require Microsoft Entra ID P1 licensing
- **Fine-grained Authorization**: Enables precise control over what users can do within your application
- **Simplified Code**: Your application can check for specific role claims instead of mapping groups to permissions

To take advantage of this feature, you define app roles that allow users and groups as member types. As shown in the following screen, select **Users/Groups** for **Allowed member types** when creating app roles.

### How App Roles Appear in Tokens

After the application admin creates app roles in your app's registration, IT administrators can assign users and groups to these roles. Your app receives a **roles claim** in tokens (ID tokens for applications, access tokens for APIs) containing all the signed-in user's assigned roles, as shown in the following token sample:

```
"iss": "https://login.microsoftonline.com/833ced3d-cb2e-41de-92f1-29e2af035ddc/v2.0",
"iat": 1670826509, "nbf": 1670826509, "exp": 1670830409,
"name": "Kyle Marsh",
"oid": "aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb",
"preferred_username": "kylemar@idfordevs.dev",
"roles": [
"Approver",
"Reviewer"
],
"sub": "dx-4lf-0loB3c3uVrULnZ2VTLuRRWYff0q7-QlIfYU4",
"tid": "bbbbcccc-1111-dddd-2222-eeee3333ffff",
```

### Best Practices for App Roles

**Always Define a Baseline User Role:** When you create app roles that allow users and groups as members, always define a baseline user role with no elevated authorization permissions. When an Enterprise App configuration requires assignment, only users with direct assignment to an application or membership in a group assigned to the app can use the app.

**Assignment Requirements:** When a user or group is assigned to the app, one of the defined app roles must be part of the assignment. If your app has elevated roles (such as "admin") for the app, then all users and groups would automatically be assigned the admin role, which violates the principle of least privilege.

**Recommended Approach:** When you define a base role (such as "user" or "reader"), users and groups assigned to the app can be assigned this base user role, ensuring appropriate access levels.

### Advantages of Using App Roles

**Avoiding Group Overage Claims:** In addition to avoiding group overage claims, app roles provide several advantages over traditional group-based authorization.

**Simplified Authorization Logic:** Another key advantage isn't needing to map between groups or names and their meaning in your application. For example, your code can simply look for the "admin" role claim. The alternative of iterating through groups in the group claims and determining which group IDs should be granted admin functionality.

**Better Security and Maintainability:**

- **Clear Intent**: Role names like "admin," "editor," and "viewer" are more descriptive than group GUIDs
- **Reduced Complexity**: No need to maintain group ID mappings in your application code
- **Better Portability**: App roles can be easily replicated across different environments


## Module assessment

Choose the best response for each of the questions below.

### Check your knowledge


## Summary

App registration in Microsoft Entra ID is the foundational process of establishing an identity configuration for your application within the Microsoft identity platform. This process ensures secure integration and provides fine-grained control over authentication and authorization.

### Key Learning Outcomes

In this module, you learned how to:

**Plan and Configure App Registration:**

- Understand the relationship between application objects and service principals
- Choose appropriate supported account types (single-tenant vs. multitenant)
- Plan for security requirements and authentication flows

**Implement Modern Authentication:**

- Configure single-page applications using authorization code flow with Proof Key for Code Exchange (PKCE)
- Set up platform-specific authentication settings
- Implement secure redirect URI patterns

**Manage API Permissions and Authorization:**

- Configure delegated permissions following the principle of least privilege
- Understand the difference between delegated and application permissions
- Implement proper consent workflows

**Advanced Security Features:**

- Create and manage app roles for fine-grained authorization
- Design baseline user roles to avoid privilege escalation
- Implement certificate-based authentication over client secrets

### Security Best Practices Covered

**Modern Authentication Flows:**

- Authorization code flow with PKCE for enhanced security
- Proper token handling and validation
- Secure credential management (certificates preferred over secrets)

**Access Control:**

- Principle of least privilege in permission requests
- Role-based access control using app roles
- Proper separation between user and application permissions

**Workload Identity Security:**

- Managed identities as the preferred approach for Azure workloads
- Secure service principal management
- Certificate-based authentication for enhanced security

### Modern Terminology and Tools

This module emphasized current Microsoft Entra ID terminology and tools:

- **Microsoft Entra admin center** as the primary management interface
- **Workload identities** for nonhuman identity management
- **Application objects** and **service principals** relationship
- **PKCE** and **CORS** for modern web application security

By implementing these practices, you can ensure that your applications integrate securely with the Microsoft identity platform while following current security standards and best practices.
