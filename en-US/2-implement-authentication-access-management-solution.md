# Implement an authentication and access management solution

> SC-300 — learning path 2/4
> https://learn.microsoft.com/en-us/training/paths/implement-authentication-access-management-solution/

## Modules

- **Secure Microsoft Entra users with multifactor authentication** (6 units)
- **Manage user authentication** (12 units)
- **Plan, implement, and administer Conditional Access** (13 units)
- **Manage Microsoft Entra Identity Protection** (11 units)
- **Implement access management for Azure resources** (10 units)
- **Deploy and Configure Microsoft Entra Global Secure Access** (10 units)


---

# Secure Microsoft Entra users with multifactor authentication

_https://learn.microsoft.com/en-us/training/modules/secure-aad-users-with-mfa/_


## Introduction

Imagine that you're a security engineer for a large manufacturing firm. Your company works on several big contracts for popular personal electronics companies, including Microsoft. Clients send you their confidential designs, which are then stored in your Azure infrastructure. Plenty of hackers would love to get their hands on the next-generation designs. It's your job to protect them.

You did significant work in hardening your network and ensuring that only the right people have access to client data. There's still a big hole to protect: user accounts. This module discusses one of the best ways to stop unauthorized users from gaining access through a username and password, which is multifactor authentication.

### Learning objectives

In this module, you:

- Learn about Microsoft Entra multifactor authentication (MFA).
- Create a plan to deploy Microsoft Entra multifactor authentication.
- Turn on Microsoft Entra multifactor authentication for users and specific apps.

### Prerequisites

- Basic knowledge of the Azure portal
- Basic knowledge of Microsoft Entra ID


## What is Microsoft Entra multifactor authentication?

Protecting your cloud assets is one of the main goals for security groups. One of the primary ways unauthorized users get access to systems is by obtaining a valid username and password. Azure can help mitigate this risk with several features of Microsoft Entra ID, including:

- **Password complexity rules**: These rules force users to generate harder-to-guess passwords.
- **Password expiration rules**: You can force users to change their passwords on a periodic basis and avoid using previously used passwords.
- **Self-service password reset (SSPR)**: This approach allows users to self-serve and reset their password if they forget it without involving an IT department.
- **Microsoft Entra ID Protection**: To help protect your organization's identities, you can configure risk-based policies that automatically respond to risky behaviors. These policies can either automatically block the behaviors or initiate remediation, including requiring password changes.
- **Microsoft Entra password protection**: You can block commonly used and compromised passwords by using a global banned-password list.
- **Microsoft Entra smart lockout**: Smart lockout helps to lock out malicious hackers who are trying to guess your user passwords or use brute-force methods to get in. It recognizes sign-ins coming from valid users and treats them differently than the sign-ins of malicious hackers and other unknown sources.
- **Microsoft Entra application proxy**: You can provision security-enhanced remote access to on-premises web applications.
- **Single sign-on (SSO)**: You can enable SSO access to your applications, including thousands of preintegrated SaaS apps.
- **Microsoft Entra Connect**: Create and manage a single identity for each user across your hybrid enterprise, keeping users, groups, and devices in sync.

These approaches are all great options that deter someone *guessing* or brute-forcing a password. However, sometimes passwords are obtained through social engineering or poor physical security practices, like putting your password on a sticky note under your keyboard! In these cases, these features don't stop an intrusion. Instead, security administrators want to turn to *Microsoft Entra multifactor authentication*.

### What is Microsoft Entra multifactor authentication?

Microsoft Entra multifactor authentication (MFA) supplies added security for your identities by requiring two or more elements for full authentication.

These elements fall into three categories:

- **Something you know**, which might be a password or the answer to a security question.
- **Something you possess**, which might be a mobile app that receives a notification or a token-generating device.
- **Something you are**, which is typically a biometric property, such as a fingerprint or face scan used on many mobile devices.

![Conceptual art showing the pieces of MFA.](https://learn.microsoft.commedia/2-mfa-example.png)

Using Microsoft Entra multifactor authentication improves identity security by limiting the impact of password exposure. To fully authenticate, a malicious hacker also needs a second factor such as the user's phone, fingerprint, or face. Multifactor authentication should always be enabled because it's the most effective way to prevent unauthorized sign-in.

Microsoft Entra multifactor authentication is the Microsoft two-step verification solution. Microsoft Entra multifactor authentication helps safeguard access to data and applications while meeting user demand for a simple sign-in process. It delivers strong authentication for a range of verification methods, including phone call, text message, or mobile app verification.

The security of Microsoft Entra multifactor authentication lies in its layered approach. Requiring multiple authentication factors presents a significant challenge for malicious hackers. Even if a malicious hacker manages to learn the user's password, it's useless without also possessing the trusted device. If the user loses the device, a person who finds it can't use it without the user's password.

### How to get multifactor authentication?

Multifactor authentication comes as part of the following offerings:

- **Microsoft Entra ID P1 or P2** or **Microsoft 365 Business**: Both of these offerings support Microsoft Entra multifactor authentication using [security defaults](https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) to require multifactor authentication.
- **Microsoft Entra ID Free** or standalone **Microsoft 365** licenses: Both use [security defaults](https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) that require multifactor authentication for your users and administrators.


## Plan your multifactor authentication deployment

Before you start deploying Microsoft Entra multifactor authentication, there are several things you should decide.

First, consider rolling out MFA in waves. Start with a small group of pilot users to evaluate the complexity of your environment and identify any setup issues or unsupported apps or devices. Then, broaden that group over time, and evaluate the results with each pass until your entire company is enrolled.

Next, make sure to create a full communication plan. Microsoft Entra multifactor authentication has several user-interaction requirements, including a registration process. Keep users informed every step of the way. Let them know what they're required to do, important dates, and how to get answers to questions if they have trouble. Microsoft provides [communication templates](https://www.microsoft.com/download/details.aspx?id=57600&WT.mc_id=rss_alldownloads_all) to help draft your communications, including posters and email templates.

### Microsoft Entra multifactor authentication policies

Microsoft Entra multifactor authentication is enforced with *Conditional Access* policies. Conditional Access policies are `IF-THEN` statements. *IF* a user wants to access a resource, *THEN* they must complete an action. For example, a payroll manager wants to access the payroll application and is required to perform multifactor authentication to access it. Other common access requests that might require MFA include:

- IF a specific cloud application is accessed.
- IF a user is accessing a specific network.
- IF a user is accessing a specific client application.
- IF a user is registering a new device.

### Deciding supported authentication methods

When you turn on Microsoft Entra multifactor authentication, you can choose the authentication methods that you want to make available. You should always support more than one method so users have a backup option in case their primary method is unavailable. You can choose from the following methods:

| Method | Description |
|---|---|
| **Mobile App Verification code** | A mobile authentication app such as the Microsoft Authenticator app can be used to retrieve an OATH verification code, which is then entered into the sign-in interface. This code is changed every 30 seconds and the app works even if connectivity is limited. This approach doesn't work in China on Android devices. |
| **Mobile app notification** | Azure can send a push notification to a mobile authentication app such as Microsoft Authenticator. The user can select the push notification and verify the sign-in. |
| **Call to a phone** | Azure can call a supplied phone number. The user then approves the authentication using the keypad. This method is preferred for backups. |
| **FIDO2 security key** | FIDO2 security keys are an unphishable standards-based passwordless authentication method. These keys are typically USB devices, but could also use Bluetooth or NFC. |
| **Windows Hello for Business** | Windows Hello for Business replaces passwords with strong two-factor authentication on devices. This authentication consists of a type of user credential that is tied to a device and uses a biometric or PIN. |
| **OATH tokens** | OATH tokens can be software applications such as the Microsoft Authenticator app and other authenticator apps. They can also be hardware-based tokens that customers can purchase from different vendors. |

Administrators can enable one or more of these options. Then users can opt in to each support authentication method they want to use.

### Selecting an authentication method

Finally, you must decide how users register their selected methods. The easiest approach is to use *Microsoft Entra ID Protection*. If your organization has a license for Identity Protection, you can configure it to prompt users to register for MFA the next time they sign in.

You can also prompt users to register for MFA when they try to use an application or service that requires multifactor authentication. Finally, you can enforce registration using a Conditional Access policy applied to an Azure group containing all users in your organization. This approach requires some manual work to periodically review the group to remove registered users. For some useful scripts to automate some of this process, see [Plan a Microsoft Entra multifactor authentication deployment](https://learn.microsoft.com/en-us/azure/active-directory/authentication/howto-mfa-getstarted#enforcing-registration).


## Exercise - Enable Microsoft Entra multifactor authentication

You can walk through the basic steps necessary to configure and enable Microsoft Entra multifactor authentication using Conditional policies. *Keep in mind that a real deployment requires significant thought and planning*. Make sure that you review the documentation links at the end of this module before you enable MFA for your environments.

Important

You need Microsoft Entra ID P1 or P2 for this exercise. You can use a [30-day free trial](https://azure.microsoft.com/trial/get-started-active-directory/) to try this feature out, or just read through the following instructions to understand the flow.

### Configure multifactor authentication options

1. Sign in to the [Azure portal](https://portal.azure.com/) using an Authentication Administrator account.
2. Search for **Microsoft Entra ID** and navigate to the Microsoft Entra ID dashboard.
3. Select **Security** in the left-hand menu.
4. Under the **Manage** menu, select **Multifactor authentication**. Here, you find options for multifactor authentication.
5. Under **Configure**, select **Additional cloud-based multifactor authentication settings**. On the resulting page, you can see all the MFA options for Azure under **Service Settings**.     You can enable or disable *app passwords* here, which allow users to create unique account passwords for apps that don't support multifactor authentication. This feature lets the user authenticate with their Microsoft Entra identity, using a different password specific to that app.

### Set up Conditional Access rules for MFA

Next, examine how to set up Conditional Access policy rules that would enforce MFA for guest users accessing specific apps on your network.

1. Switch back to the Azure portal and select **Microsoft Entra ID** > **Security** > **Conditional Access**.
2. Select **Create new policy** from the top menu.
3. Name your policy, for example, *All guests*.
4. Under **Users**, select **0 users and groups selected**.
  1. Under **Include**, choose **Select users and groups**.
  2. Select users and groups and then choose **Select**.

5. Under **Target resources**, select **No target resources selected**.
  1. Select **Cloud apps**.
  2. Under **Include**, choose **Select apps**.
  3. Under **Select**, choose **None**. Select apps from the options on the right and then choose **Select**.

6. Under **Conditions**, select **0 conditions selected**.
  1. Under **Locations**, select **Not configured**.
  2. Under **Configure**, select **Yes**, then select **Any location**.

7. Under **Grant**, select **0 controls selected**.
  1. Make sure that **Grant access** is selected.
  2. Select **Require multifactor authentication** and choose **Select**. This option enforces MFA.

8. Set **Enable policy** to **On**, and then **Create**.

MFA is now enabled for your selected applications. The next time a user or guest tries to sign into that app, they're prompted to register for MFA.


## Configure multifactor authentication methods

As mentioned earlier in the module, we recommend that users to be able to select more than one authentication method in case their primary method is unavailable.

When a user signs into a service that requires MFA the first time, they're asked to register their preferred multifactor authentication method as shown in the following screenshot:

Tip

If you followed the previous exercise and turned on MFA for an account and app, you can try accessing that app with the given user account. You should see the preceding flow.

Once they register, each time users sign into a service or app that requires MFA, the Azure sign-in process prompts for the authentication information as shown in the following image:

### Azure Authentication Methods

As you saw earlier, there are several possible authentication methods that an administrator can set up. Some of these also support Self-Service Password Reset (SSPR), which allows users to reset their password by supplying a secondary form of authentication. You can couple this service with Microsoft Entra multifactor authentication to ease the burden on IT staff.

The following table lists the authentication methods and the services that can use them.

| Authentication method | Services |
|---|---|
| **Password** | Microsoft Entra multifactor authentication and SSPR |
| **Security questions** | SSPR |
| **Email address** | SSPR |
| **Windows Hello for Business** | Microsoft Entra multifactor authentication and SSPR |
| **FIDO2 Security Key** | Microsoft Entra multifactor authentication and SSPR |
| **Microsoft Authenticator app** | Microsoft Entra multifactor authentication and SSPR |
| **OATH hardware token** | Microsoft Entra multifactor authentication and SSPR |
| **OATH software token** | Microsoft Entra multifactor authentication and SSPR |
| **Text message** | Microsoft Entra multifactor authentication and SSPR |
| **Voice call** | Microsoft Entra multifactor authentication and SSPR |
| **App passwords** | Microsoft Entra multifactor authentication in certain cases |

#### Password

This method is the only one that you can't disable.

#### Security questions

This method is available only for non-administrative accounts that use Self-Service Password Reset.

- Azure stores security questions privately and in a security-enhanced manner on a user object in the directory. Only users can answer the questions, and only during registration. An administrator can't read or change a user's questions or answers.
- Azure provides 35 predefined questions, all translated and localized based on the browser locale.
- You can customize the questions by using the administrative interface. Azure displays them in the language entered. The maximum length is 200 characters.

#### Email address

This method is available only in SSPR. We recommend that you avoid the use of an email account that doesn't require the users Microsoft Entra password to access it.

#### Windows Hello for Business

Windows Hello for Business provides reliable, fully integrated biometric authentication based on facial recognition or fingerprint matching. Windows Hello for Business, FIDO2 security keys, and Microsoft Authenticator are passwordless solutions.

#### FIDO2 security keys

FIDO2 security keys are an unphishable, standards-based, and passwordless authentication method that can come in any form factor. Fast Identity Online (FIDO) is an open standard for passwordless authentication.

Users can register and then select a FIDO2 security key at the sign-in interface as their main means of authentication. These FIDO2 security keys are typically USB devices but could also use Bluetooth or NFC.

FIDO2 security keys can be used to sign in to their Microsoft Entra ID or Microsoft Entra hybrid joined Windows 10 devices. They can get single-sign on to their cloud and on-premises resources. Users can also sign in to supported browsers.

#### Microsoft Authenticator app

This method is available for Android and iOS. Users can [register their mobile app here](https://aka.ms/mfasetup).

- The Microsoft Authenticator app helps prevent unauthorized access to accounts. It pushes a notification that helps stop fraudulent transactions to your smartphone or tablet. Users view the notification, and confirm or deny the request.
- Users can use the Microsoft Authenticator app or a third-party app as a software token to generate an OATH verification code. After the user enters the username and password, the users enter the code provided by the app on the sign-in screen. The verification code provides a second form of authentication. Users can also set the Microsoft Authenticator app to deliver a push notification that they select and approve to sign in.

#### OATH hardware tokens

**OATH** is an open standard that specifies how to generate one-time password codes. Microsoft Entra ID supports the use of OATH-TOTP `SHA-1` tokens of the 30-second or 60-second variety. Customers can get these tokens from the vendor of their choice. Secret keys are limited to 128 characters, which might not be compatible with all tokens.

#### OATH software tokens

Software OATH tokens are typically applications such as the Microsoft Authenticator app and other authenticator apps. Microsoft Entra ID generates the secret key, or seed, that's input into the app and used to generate each OTP.

#### Text message

Azure sends a verification code to a mobile phone using SMS. The user must enter the code into the browser within a specific time period to continue.

#### Voice call

Azure uses an automated voice system to call the number and the owner uses the keypad to confirm the authentication. This option isn't available to the free/trial Microsoft Entra tier.

#### App password

Certain non-browser apps don't support Microsoft Entra multifactor authentication. If users are enabled for Microsoft Entra multifactor authentication and try to use nonbrowser apps, they're unable to authenticate. The app password allows users to continue to authenticate.

### Monitoring adoption

Microsoft Entra ID includes a **Usage & insights** view in the **Monitoring** section where you can monitor the authentication methods activity. From here you can view the adoption of MFA and SSPR:

In addition to the overall registration numbers, you can also see the success and failure of registrations per authentication method. This fact allows you to understand which authentication methods your users most commonly registered and which ones are easy for them to register. This data is calculated using the last 30 days of audit logs from the combined security info registration and SSPR registration experiences.

You can drill down and see the latest registration audit information for each user by clicking the chart.

You can also learn more about SSPR usage in your organization through the **Usage** tab on the main view, as shown in the following image:

### Check your knowledge


## Summary

Using Microsoft Entra multifactor authentication, you can ensure that when users sign in to access your confidential systems and data, they are who they say they are. Microsoft Entra ID allows you to create policies to ensure that specific apps are protected, while allowing more public systems to remain easier to get to. In addition, you can use other services such as Microsoft Entra ID Protection and Azure Smart Lockout to fully protect your identity surface area.

### Further reading

To learn more about some of the topics examined in this module, check out the following links to documentation.

- [What is Microsoft Entra ID Protection?](https://learn.microsoft.com/en-us/entra/id-protection/overview-identity-protection)
- [Plan a Microsoft Entra multifactor authentication deployment](https://learn.microsoft.com/en-us/azure/active-directory/authentication/howto-mfa-getstarted)
- [Reset your work or school password using security info](https://support.microsoft.com/account-billing/reset-your-work-or-school-password-using-security-info-23dde81f-08bb-4776-ba72-e6b72b9dda9e)


---

# Manage user authentication

_https://learn.microsoft.com/en-us/training/modules/manage-user-authentication/_


## Introduction

One of the main features of an identity platform is to verify, or authenticate, credentials when a user signs in to a device, application, or service. In Microsoft Entra ID, authentication involves more than just verifying a username and password. To improve security and reduce the need for help desk assistance, Microsoft Entra authentication includes the following components:

- Self-service password reset
- Multifactor authentication
- Hybrid integration to write password changes back to on-premises environment
- Hybrid integration to enforce password protection policies for an on-premises environment
- Passwordless authentication
- Authentication to virtual machines

This module examines these components and explains how to plan, implement, and manage user authentication in Microsoft Entra ID.

### Learning objectives

In this module, you will:

- Administer authentication methods (FIDO2/Passwordless).
- Implement an authentication solution based on Windows Hello for Business.
- Configure and deploy self-service password reset.
- Deploy and manage password protection and smart lockouts.
- Implement Kerberos and certificate-based authentication.
- Configure Microsoft Entra user authentication to virtual machines.


## Administer FIDO2 and passwordless authentication methods

As part of the sign-in experience for accounts in Microsoft Entra ID, there are several ways that users can authenticate themselves. Historically, a username and password is the most common way a user would provide credentials. With modern authentication and security features in Microsoft Entra ID, that basic password should be supplemented or replaced with more secure authentication methods.

Passwordless authentication methods such as Windows Hello, FIDO2 security keys, and the Microsoft Authenticator app provide the most secure sign-in events.

Multifactor authentication (MFA) adds extra security over only using a password when a user signs in. The user can be prompted for other forms of authentication. The user might have to respond to a push notification, enter a code from a software or hardware token. Finally, the user might have to respond to an SMS or phone call.

Simplify the user on-boarding experience by registering for both MFA and self-service password reset (SSPR). Microsoft recommends you enable combined security information registration. For resiliency, we recommend you require users to register multiple authentication methods. When one method isn't available for a user during sign-in or SSPR, they can choose to authenticate with another method.

#### Authentication method strength and security

When you deploy features like multifactor authentication in your organization, review the available authentication methods. Choose the methods that meet or exceed your requirements in terms of security, usability, and availability. Where possible, use authentication methods with the highest level of security.

The following table outlines the security considerations for the available authentication methods. Availability is an indication of the user being able to use the authentication method, not of the service availability in Microsoft Entra ID:

![Diagram of an X Y grid that shows inconvenient to convenient side to side and low security to high security top to bottom.](https://learn.microsoft.com../../wwl-sci/manage-user-authentication/media/authentication-method-strength-security.png)

| **Authentication method** | **Security** | **Usability** | **Availability** |
|---|---|---|---|
| Windows Hello for Business | High | High | High |
| Microsoft Authenticator app | High | High | High |
| FIDO2 security key | High | High | High |
| OATH hardware tokens (preview) | Medium | Medium | High |
| OATH software tokens | Medium | Medium | High |
| SMS | Medium | High | Medium |
| Voice | Medium | Medium | Medium |
| Password | Low | High | High |

Tip

For flexibility and usability, we recommend that you use the Microsoft Authenticator app. This authentication method provides the best user experience and multiple modes, such as passwordless, MFA push notifications, and OATH codes.

#### How each authentication method works

Some authentication methods can be used as the primary factor when you sign in to an application or device. A good example of primary authentication is to use a FIDO2 security key or a password. Other authentication methods are only available as a secondary factor. Examples are when you use multifactor authentication or SSPR.

The following table outlines when an authentication method can be used during a sign-in event:

| **Method** | **Primary authentication** | **Secondary authentication** |
|---|---|---|
| Windows Hello for Business | Yes | MFA |
| Microsoft Authenticator app | Yes (preview) | MFA and SSPR |
| FIDO2 security key | Yes | MFA |
| OATH hardware tokens (preview) | No | MFA and SSPR |
| OATH software tokens | No | MFA and SSPR |
| SMS | Yes (preview) | MFA and SSPR |
| Voice call | No | MFA and SSPR |
| Password | Yes |   |

All of these authentication methods can be configured in the Azure portal and increasingly using the Microsoft Graph REST API beta.

Note

In Microsoft Entra ID, a password is often one of the primary authentication methods. You can't disable the password authentication method. If you use a password as the primary authentication factor, increase the security of sign-in events using multifactor authentication.

The following verification methods can be used in certain scenarios:

- App passwords - used for old applications that don't support modern authentication and can be configured for per-user multifactor authentication.
- Security questions - only used for SSPR.
- Email address - only used for SSPR.

### What is FIDO2

The FIDO (Fast IDentity Online) Alliance helps to promote open authentication specifications and reduce the use of passwords as a form of authentication. FIDO2 is the latest specification that incorporates the web authentication (WebAuthn) specification. Users can register and then select a FIDO2 security key at the sign-in interface as their main means of authentication. These FIDO2 security keys are typically USB devices, but could also use Bluetooth or NFC (near field communication). With a hardware device that handles the authentication, the security of an account is increased as there's no password that could be exposed or guessed. FIDO2 security keys can be used to sign into their Microsoft Entra ID or hybrid Microsoft Entra joined Windows 10 or 11 devices and get single-sign on to their cloud and on-premises resources. Users can also sign into supported browsers. FIDO2 security keys are a great option for enterprises who are very security sensitive or have scenarios or employees who aren't willing or able to use their phone as a second factor.

- FIDO2 security keys are an unphishable specification-based passwordless authentication method that can come in any form factor
- Fast Identity Online (FIDO) is an open specification for passwordless authentication
- FIDO allows users and organizations to leverage the specification to sign into their resources without a username or password using an external security key or a platform key built into a device

### Enable FIDO2 security key method

1. Sign into the Microsoft Entra admin center.
2. Browse to **Protection** - **Authentication methods** - **Authentication method policy**.
3. Under the method **FIDO2 Security Key**, choose the following options:
  - **Enable** - Yes or No
  - **Target** - All users or Select users

4. **Save** the configuration.

#### Manage user registration and FIDO2 security keys

1. Browse to **[https://myprofile.microsoft.com](https://myprofile.microsoft.com)**.
2. Sign in if you haven't already.
3. Select **Security Info**.
4. If the user already has at least one multifactor authentication method registered, they can immediately register a FIDO2 security key.
5. If they don't have at least one multifactor authentication method registered, they must add one.
6. Add a FIDO2 security key by selecting **Add method** and choosing **Security key**.
7. Choose **USB device** or **NFC device**.
8. Have your key ready and choose **Next**.
9. A box will appear and ask the user to create/enter a PIN for your security key and then perform the required gesture for the key, either biometric or touch.
10. The user will be returned to the combined registration experience and asked to provide a meaningful name for the key so the user can identify which one if they have multiple. Select **Next**.
11. Select **Done** to complete the process.

#### Sign in with passwordless credential

In the example below a user has already provisioned their FIDO2 security key. The user can choose to sign in on the web with their FIDO2 security key inside of a supported browser on Windows 10 version 1903 or higher or Windows 11.

### Prerequisites for cloud-only deployment

- Windows 10, version 1511 or later or Windows 11
- Microsoft Azure account
- Microsoft Entra ID
- Multifactor authentication
- Modern Management - *optional,* Microsoft Intune, or supported third-party mobile-device management (MDM)
- Microsoft Entra ID Premium subscription - *optional*, needed for automatic MDM enrollment when the device joins Microsoft Entra ID


## Explore Authenticator app and OATH tokens

The Microsoft Entra Authenticator app provides an additional level of security to your Microsoft Entra ID work or school account or your Microsoft account and is available for Android and iOS. With the Microsoft Authenticator app, users can authenticate in a passwordless way during sign-in, or as an additional verification option during self-service password reset (SSPR) or multifactor authentication events.

Users might receive a notification through the mobile app for them to approve or deny, or use the Authenticator app to generate an OATH verification code that can be entered in a sign-in interface. If you enable both a notification and verification code, users who register the Authenticator app can use either method to verify their identity.

### Microsoft Authenticator app

The Authenticator app provides a high level of security, and removes the need for the user to provide a password at sign-in. The Authenticator app can help prevent unauthorized access to accounts and stop fraudulent transactions. A push notification is sent to your smartphone or tablet for extra security. Users view the notification, and if it's legitimate, select Verify. Otherwise, they can select Deny.

The Authenticator app can be used as a software token to generate an OATH verification code. After entering your username and password, you enter the code provided by the Authenticator app into the sign-in interface. The verification code provides a second form of authentication. Users might have a combination of up to five OATH hardware tokens or authenticator applications, such as the Authenticator app, configured for use at any time.

### Open Authentication (OATH) tokens

OATH TOTP (Time-based One Time Password) is an open standard that specifies how one-time password (OTP) codes are generated. OATH TOTP can be implemented using either software or hardware to generate the codes. Microsoft Entra ID doesn't support OATH HOTP, a different code generation standard. Software OATH tokens are typically applications such as the Microsoft Authenticator app and other authenticator apps. Microsoft Entra ID generates the secret key, or seed, that's input into the app and used to generate each OTP.

The Authenticator app automatically generates codes when set up to do push notifications so a user has a backup even if their device doesn't have connectivity. Third-party applications that use OATH TOTP to generate codes can also be used.


## Implement an authentication solution based on Windows Hello for Business

In Windows 10, Windows Hello for Business replaces passwords with strong two-factor authentication on PCs and mobile devices. This authentication consists of a new type of user credential that is tied to a device and uses a biometric or PIN. Windows Hello for Business lets user authenticate to an Active Directory or Microsoft Entra account.

Windows Hello addresses the following problems with passwords:

- Strong passwords can be difficult to remember, and users often reuse passwords on multiple sites.
- Server breaches can expose symmetric network credentials (passwords).
- Passwords are subject to replay attacks.
- Users can inadvertently expose their passwords due to phishing attacks.

![Diagram of the process flow for how authentication works in Windows Hello.](https://learn.microsoft.com../../wwl-sci/manage-user-authentication/media/authentication-flow.png)

### How Windows Hello for Business works: key points

- Windows Hello credentials are based on certificate or asymmetrical key pair. Windows Hello credentials can be bound to the device, and the token that is obtained using the credential is also bound to the device.
- Identity provider (such as Active Directory, Microsoft Entra ID, or a Microsoft account) validates user identity and maps the Windows Hello public key to a user account during the registration step.
- Keys can be generated in hardware (TPM (Trusted Platform Module) 1.2 or 2.0 for enterprises, and TPM 2.0 for consumers) or software, based on the policy.
- Two-factor authentication is the combination of a key or certificate tied to a device. Then something that the person knows (a PIN) or something that the person is (biometrics). The Windows Hello gesture doesn't roam between devices and isn't shared with the server. Biometrics templates are stored locally on a device. The PIN is never stored or shared.
- The private key never leaves a device when using TPM. The authenticating server has a public key that is mapped to the user account during the registration process.
- PIN entry and biometric gesture both trigger Windows 10 to use the private key to cryptographically sign data that is sent to the identity provider. The identity provider verifies the user's identity and authenticates the user.
- Personal (Microsoft account) and corporate (Active Directory or Microsoft Entra ID) accounts use a single container for keys. All keys are separated by identity providers' domains to help ensure user privacy.
- Certificate private keys can be protected by the Windows Hello container and the Windows Hello gesture.

### Creating security groups

Windows Hello for Business uses several security groups to simplify the deployment and management.

Important

If your environment has one or more Windows Server 2016 domain controllers in the domain to which you are deploying Windows Hello for Business, then skip the Create the KeyCredentials Admins Security Group. Domains that include Windows Server 2016 domain controllers use the KeyAdmins group, which is created during the installation of the first Windows Server 2016 domain controller.

#### Create the KeyCredential Admins security group

Microsoft Entra Connect synchronizes the public key on the user object created during provisioning. You assign write and read permission to this group to the Active Directory attribute. This will ensure the Microsoft Entra Connect service can add and remove keys as part of its normal workflow.

1. Sign in a domain controller or management workstation with *Domain Admin* equivalent credentials.
2. Open **Active Directory Users and Computers**.
3. Select **View** and select **Advance Features**.
4. Expand the domain node from the navigation pane.
5. Right-select the **Users** container. Select **New**. Select **Group**.
6. Type **KeyCredential Admins** in the **Group Name** text box.
7. Select **OK**.

#### Create the Windows Hello for Business Users security group

The Windows Hello for Business Users group is used to make it easy to deploy Windows Hello for Business in phases. You assign Group Policy and Certificate template permissions to this group to simplify the deployment by adding the users to the group. This provides users with the proper permissions to configure Windows Hello for Business and to enroll in the Windows Hello for Business authentication certificate.

1. Sign in a domain controller or management workstation with *Domain Admin* equivalent credentials.
2. Open **Active Directory Users and Computers**.
3. Select **View** and select **Advanced Features**.
4. Expand the domain node from the navigation pane.
5. Right-select the **Users** container. Select **New**. Select **Group**.
6. Type **Windows Hello for Business Users** in the **Group Name** text box.
7. Select **OK**.

### Microsoft Pluton Security Processor

![Diagram of the new Microsoft Pluton C P U chip on the motherboard next to the C P U and T P M chips.](https://learn.microsoft.com../../wwl-sci/manage-user-authentication/media/pluton.png)

Today, the heart of operating system security on most PCs lives in a chip separate from the CPU, called the TPM (Trusted Platform Module). The TPM is a hardware component, which is used to help securely store keys and measurements that verify the integrity of the system. TPMs have been supported in Windows for more than 10 years and power many critical technologies such as Windows Hello and BitLocker. Based on the effectiveness of the TPM at performing critical security tasks, attackers have begun to innovate ways to attack it. This is particularly common in situations where an attacker can steal or temporarily gain physical access to a PC. These sophisticated attack techniques target the communication channel between the CPU and TPM, which is typically a bus interface. This bus interface provides the ability to share information between the main CPU and security processor. It also provides an opportunity for attackers to steal or modify information in-transit using a physical attack.

The Pluton design removes the potential for that communication channel to be attacked by building security directly into the CPU. Windows PCs using the Pluton architecture will first emulate a TPM. This emulation works with the existing TPM specifications and APIs. Finally, this will allow customers to immediately benefit from enhanced security for Windows features that rely on TPM. Some examples are BitLocker and System Guard. Windows devices with Pluton will use the Pluton security processor to protect credentials, user identities, encryption keys, and personal data. None of this information can be removed from Pluton even if an attacker has installed malware or has complete physical possession of the PC.

- Built in collaboration with AMD, Intel, Qualcomm, and others.
- Security Hardware Cryptographic Key (SHACK).
- Update / replacement for the TPM chip, which hackers are starting to learn how to get around.
- Based on technology pioneered in Azure Sphere and Xbox security.


## Exercise configure and deploy self-service password reset

Microsoft Entra self-service password reset (SSPR) gives users the ability to change or reset their password, with no administrator or helpdesk involvement. If a user's account is locked or they forget their password, they can follow prompts to unblock themselves and get back to work. This ability reduces help desk calls and loss of productivity when a user can't sign in to their device or an application.

### Benefits of self-service password reset

There are many benefits for the user and the organization to enabling self-service password reset:

- Users can reset their own password - no productivity loss
- No admin or IT intervention - enables IT to focus on bigger issues

Licensing requirements:

- Cloud based accounts - A user has to be enrolled into self-service password reset, and that a Microsoft Entra ID Premium P1 or P2 license or a Microsoft 365 Business Standard license is required.
- On-premises accounts - A user has to be enrolled into self-service password reset, and that a Microsoft Entra ID Premium P1 or P2 license or a Microsoft 365 Business Premium license.

### Enable self-service password reset

Basic steps to enable self-service password reset:

1. Sign in to the Azure portal using an account with global administrator permissions.
2. Search for and select Microsoft Entra ID, then select Password reset from the menu on the left side.
3. From the Properties page, under the option Self-service password reset, select Select group
4. Browse for and select your Microsoft Entra group, like SSPR-Test-Group, then choose Select.
5. To enable SSPR for the chosen group, select Save.

### Add a new user

Create a user account that will be added to a security group.

1. In the Microsoft Entra organization you created, under **Manage**, select **Users** then select **New User**.
2. The User pane now appears. Enter the following values:
  - User name: MonicaT
  - Name: Monica Thompson

3. Select **Show Password** and then copy it somewhere to reference it later.
4. Select **Create**.

### Create a group

You want to roll out SSPR to a limited set of users first to make sure your SSPR configuration works as expected. Let's create a security group for the limited rollout and add a user to the group.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/) using a Global administrator account.
2. Open the portal menu and then select **Identity**.
3. On the Identity menu, select **Groups**, then select **+ New Group**.
4. Create a new group using the following information:    **Setting** **Value**     Group type Security   Group name SSPRTesters   Group description Testers of SSPR rollout   Membership type Assigned   Members Monica Thompson
5. Select **Create.**

### Enable self-service password reset

Enable SSPR for the group.

1. Browse back to the Microsoft Entra admin center screen.
2. Under **Protection**, select **Password reset**.  Important If the Password reset page still displays the message Get a free Premium trial to use this feature, wait for a few minutes and then refresh the page.
3. On the Password reset dialog **Properties** page, under **Self-service password reset enabled**, select **Selected**.
4. Select **Select group**.
5. In the Default password reset policy pane, select the **SSPRTesters** group.
6. On the Password reset dialog, **Properties** page, select **Save**.
7. Under **Manage**, select and review the default values for the **Authentication methods**, **Registration**, **Notifications**, and **Customization** settings.

### Register for self-service password reset

Now that the SSPR configuration is complete, register a mobile phone number for the user you created.

1. Open a different browser or open an InPrivate or Incognito browser session and then browse to [https://aka.ms/ssprsetup](https://aka.ms/ssprsetup). This is to ensure you'll be prompted for user authentication.
2. Sign in as `MonicaT@organization-domain-name.onmicrosoft.com` with the password that you noted earlier. Replace the organization-domain-name with your domain name.
3. When prompted to update your password, enter a new password of your choice. Be sure to record the new password.
4. In the **More information required** dialog box, select **Next**.
5. On the Keep your account-secure page, user the **Phone** option or select the **I want to set up a different method** link.
6. In this example, you'll use the Phone option. Enter your mobile phone details.
7. Select **Text me a code**.
8. When you receive the code on your mobile phone, enter the code in the text box and then select Next.
9. After your phone has been registered, select Next and then select Done.
10. Close the browser. You don't need to complete the sign-in process.

### Test self-service password reset

Now let's test whether the user can reset their password.

1. Open a different browser or open an InPrivate or Incognito browser session and then browse to [https://aka.ms/sspr](https://aka.ms/sspr). This is to ensure you well be prompted for user authentication.
2. In the **Email, phone, or Skype** box, enter `MonicaT@organization-domain-name.onmicrosoft.com` and then select Next. Replace the organization-domain-name with your domain name.
3. On the Enter password page, select **Forgot my password**.
4. On the Get back into your account page, complete the requested information and then select **Next**.
5. In the **verification step 1** task, select **Text my mobile phone** or **Call my mobile phone**, enter your phone number and then select **Text**.
6. Enter your verification code and then select **Next**.
7. Choose a new password step, enter a password and then confirm your new password.
8. When complete, select **Finish**.
9. Sign in as **Monica** with the new password you created.
10. Enter your verification code and then verify you can complete the sign-in process.
11. When finished, close your browser.


## Deploy and manage password protection

Users often create passwords that use common local words such as a school, sports team, or famous person. These passwords are easy to guess and weak against dictionary-based attacks. To enforce strong passwords in your organization, Microsoft Entra Password Protection provides a global and custom banned password list. A password change request fails if there's a match in these banned passwords list.

Microsoft Entra Password Protection is designed with the following principles in mind:

- Domain controllers (DCs) never have to communicate directly with the internet.
- No new network ports are opened on DCs.
- No AD DS schema changes are required. The software uses the existing AD DS container and serviceConnectionPoint schema objects.
- No minimum AD DS domain or forest functional level (DFL/FFL) is required.
- The software doesn't create or require accounts in the AD DS domains that it protects.
- User clear-text passwords never leave the DC, either during password validation operations or at any other time.
- The software isn't dependent on other Microsoft Entra features. For example, Microsoft Entra password hash sync (PHS) isn't related or required for Microsoft Entra Password Protection.
- Incremental deployment is supported, however the password policy is only enforced where the Domain Controller Agent (DC Agent) is installed.

### Create an Azure account and add Microsoft Entra ID Premium P2 trial licenses

The tasks in this exercise and the exercises in this learning path require you to already have and Azure subscription that you can use or to sign up for an Azure trial account. If you already have your own Azure subscription, you might skip this task and continue to the next.

1. In a web browser, go to the [Azure portal](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
2. Scroll down through the page to learn more about the benefits and free services available.
3. Select **Start free**.
4. Use the wizard to sign up for your Azure trial subscription.
5. You'll need to a Microsoft Entra P2 license to complete some of the exercises. In the organization you created, search for and then select **Microsoft Entra ID**.
6. In the left navigation menu, select **Getting started**.
7. Under Getting started with Microsoft Entra, select **Get a free trial for Microsoft Entra Premium**.
8. In the Activate pane, under **Microsoft Entra Premium P2**, select **Free trial** and then select **Activate**.
9. In the navigation menu on the left, select **Overview**.
10. Refresh the browser until you see Microsoft Entra Premium P2 under the organization name. It might take a couple of minutes.
11. You might need to sign out and sign back into Microsoft Azure if you encounter any problems with expected features not being available.

### How Microsoft Entra Password Protection works

The on-premises Microsoft Entra Password Protection components work as follows:

1. Each Microsoft Entra Password Protection proxy-service-instance advertises itself to the DCs in the forest by creating a *serviceConnectionPoint* object in Active Directory.
2. Each DC Agent service for Microsoft Entra Password Protection also creates a *serviceConnectionPoint* object in Active Directory. This object is used primarily for reporting and diagnostics.
3. The DC Agent service is responsible for initiating the download of a new password policy from Microsoft Entra. The first step is to locate a Microsoft Entra Password Protection proxy-service by querying the forest for proxy *serviceConnectionPoint* objects.
4. When an available proxy service is found, the DC Agent sends a password policy download request to the proxy service. The proxy service in turn sends the request to Microsoft Entra, and then returns the response to the DC Agent service.
5. After the DC Agent service receives a new password policy from Microsoft Entra, the service stores the policy in a dedicated folder at the root of its domain *sysvol* folder share. The DC Agent service also monitors this folder in case newer policies replicate in from other DC Agent services in the domain.
6. The DC Agent service always requests a new policy at service startup. After the DC Agent service is started, it checks the age of the current locally available policy hourly. If the policy is older than one hour, the DC Agent requests a new policy from Microsoft Entra via the proxy service, as described previously. If the current policy isn't older than one hour, the DC Agent continues to use that policy.
7. When password change events are received by a DC, the cached policy is used to determine if the new password is accepted or rejected.

To protect your on-premises Active Directory Domain Services (AD DS) environment, you can install and configure Microsoft Entra Password Protection to work with your on-premises DC. This unit shows you how to install and register the Microsoft Entra Password Protection proxy-service and Microsoft Entra Password Protection DC agent in your on-premises environment.

### Deployment strategy

The following diagram shows how the basic components of Microsoft Entra Password Protection work together in an on-premises Active Directory environment:

![Diagram of How Microsoft Entra Password Protection components work together.](https://learn.microsoft.com../../wwl-sci/manage-user-authentication/media/azure-active-directory-password-protection.png)

We recommend that you start deployments in *audit* mode. Audit mode is the default initial setting, where passwords can continue to be set. Passwords that would be blocked are recorded in the event log. After you deploy the proxy-servers and DC agents in audit mode, monitor the change the password policy will have on users when the policy is enforced.

During the audit stage, many organizations find that the following situations apply:

- They need to improve existing operational processes to use more secure passwords.
- Users often use unsecure passwords.
- They need to inform users about the upcoming change in security enforcement, and how to choose more secure passwords.

It's also possible for stronger password validation to affect your existing Active Directory domain controller deployment automation. We recommend that at least one DC promotion and one DC demotion happen during the audit period evaluation to help uncover issues such as weak passwords preventing promotion and demotion.

After the feature has been running in audit mode for a reasonable period, you can switch the configuration from *Audit* to *Enforce* to require more secure passwords. Additional monitoring during this time is a good idea.

Important

Microsoft Entra Password Protection can only validate passwords during password change or set operations. Passwords that were accepted and stored in Active Directory prior to the deployment of Microsoft Entra Password Protection will never be validated and will continue working as is. Over time, all users and accounts will eventually start using Microsoft Entra Password Protection-validated passwords as their existing passwords expire. Accounts configured with "password never expires" are exempt from this.

#### Multiple forest considerations

There are no additional requirements to deploy Microsoft Entra Password Protection across multiple forests.

Each forest is independently configured. Each Microsoft Entra Password Protection proxy can only support domain controllers from the forest that it's joined to.

The Microsoft Entra Password Protection software in any forest is unaware of password protection software that's deployed in other forests, regardless of Active Directory trust configurations.

#### Read-only domain controller considerations

Password change or set events aren't processed and persisted on read-only domain controllers (RODCs). Instead, they're forwarded to writable domain controllers. You don't have to install the Microsoft Entra Password Protection DC agent software on RODCs.

Further, it's not supported to run the Microsoft Entra Password Protection proxy-service on a read-only domain controller.

#### High availability considerations

The main concern for password protection is the availability of Microsoft Entra Password Protection proxy servers when the DCs in a forest try to download new policies or other data from Azure. Each Microsoft Entra Password Protection DC agent uses a simple round-robin-style algorithm when deciding which proxy server to call. The agent skips proxy servers that aren't responding.

For most fully connected Active Directory deployments that have healthy replication of both directory and sysvol folder state, two Microsoft Entra Password Protection proxy servers is enough to ensure availability. This configuration results in timely download of new policies and other data. You can deploy additional Microsoft Entra Password Protection proxy servers if desired.

The design of the Microsoft Entra Password Protection DC agent software mitigates the usual problems that are associated with high availability. The Microsoft Entra Password Protection DC agent maintains a local cache of the most recently downloaded password policy. Even if all registered proxy servers become unavailable, the Microsoft Entra Password Protection DC agents continue to enforce their cached password policy.

A reasonable update frequency for password policies in a large deployment is usually days, not hours or less. So, brief outages of the proxy servers don't cause problems for Microsoft Entra Password Protection.

### Deployment requirements

Licensing requirements for AD Password Protection are as follows:

| **Users** | **Microsoft Entra Password Protection with global banned password list** | **Microsoft Entra Password Protection with custom banned password list** |
|---|---|---|
| Cloud-only users | Microsoft Entra Free | Microsoft Entra Premium P1 or P2 |
| Users synchronized from on-premises AD DS | Microsoft Entra Premium P1 or P2 | Microsoft Entra Premium P1 or P2 |

The following core requirements apply:

- You need an account that has Active Directory domain administrator privileges in the forest root domain to register the Windows Server Active Directory forest with Microsoft Entra.
- The Key Distribution Service must be enabled on all domain controllers in the domain that run Windows Server 2012. By default, this service is enabled via manual trigger start.
- Network connectivity must exist between at least one domain controller in each domain and at least one server that hosts the proxy service for Microsoft Entra Password Protection. This connectivity must allow the domain controller to access RPC endpoint mapper port 135 and the RPC server port on the proxy service.
  - By default, the RPC server port is a dynamic RPC port, but it can be configured to use a static port.

- All machines where the Microsoft Entra Password Protection proxy-service will be installed must have network access to the following endpoints:

| **Endpoint** | **Purpose** |
|---|---|
| `https://login.microsoftonline.com` | Authentication requests |
| `https://enterpriseregistration.windows.net` | Microsoft Entra Password Protection functionality |

#### Microsoft Entra Password Protection DC agent

The following requirements apply to the Microsoft Entra Password Protection DC agent:

- All machines where the Microsoft Entra Password Protection DC agent software will be installed must run Windows Server 2012 R2 or later.
  - The Active Directory domain or forest doesn't need to be at Windows Server 2012 R2 domain functional level (DFL) or forest functional level (FFL). There's no minimum DFL or FFL required for either the DC agent or proxy software to run.

- All machines that run the Microsoft Entra Password Protection DC agent must have .NET 4.7.2 installed.
- Any Active Directory domain that runs the Microsoft Entra Password Protection DC agent service must use Distributed File System Replication (DFSR) for sysvol replication.

#### Microsoft Entra Password Protection proxy service

The following requirements apply to the Microsoft Entra Password Protection proxy-service:

- All machines where the Microsoft Entra Password Protection proxy-service will be installed must run Windows Server 2012 R2 or later.  Note The Microsoft Entra Password Protection proxy-service deployment is a mandatory requirement for deploying Microsoft Entra Password Protection even though the domain controller may have outbound direct internet connectivity.
- All machines where the Microsoft Entra Password Protection proxy-service will be installed must have .NET 4.7.2 installed.
- All machines that host the Microsoft Entra Password Protection proxy-service must be configured to grant domain controllers the ability to sign into the proxy service. This ability is controlled via the "Access this computer from the network" privilege assignment.
- All machines that host the Microsoft Entra Password Protection proxy-service must be configured to allow outbound TLS 1.2 HTTP traffic.
- A *Global Administrator* account is required to register the Microsoft Entra Password Protection proxy-service for the first time in a given tenant. Subsequent proxy and forest registrations can use an account with at least the *Security Administrator* role.
- Network access must be enabled for the set of ports and URLs specified in the Application Proxy environment setup procedures.  Warning Microsoft Entra Password Protection proxy and Microsoft Entra Application Proxy install different versions of the Microsoft Entra Connect Agent Updater service, which is why the instructions refer to Application Proxy content. These different versions are incompatible when installed side by side. Doing so will prevent the Agent Updater service from contacting Azure for software updates, so you should never install Microsoft Entra Password Protection Proxy and Application Proxy on the same machine.

### Download required software

Two installers are required for an on-premises Microsoft Entra Password Protection deployment:

- Microsoft Entra Password Protection DC agent (*AzureADPasswordProtectionDCAgentSetup.msi*)
- Microsoft Entra Password Protection proxy (*AzureADPasswordProtectionProxySetup.exe*)

### Install and configure the proxy service

The Microsoft Entra Password Protection proxy-service is typically on a member server in your on-premises AD DS environment. Once installed, the Microsoft Entra Password Protection proxy-service communicates with Microsoft Entra to maintain a copy of the global and customer banned password lists for your Microsoft Entra tenant.

### Install the DC agent service

To install the Microsoft Entra Password Protection DC agent service, run the `AzureADPasswordProtectionDCAgentSetup.msi` package.

You can automate the software installation by using standard MSI procedures, as shown in the following example:

```console

msiexec.exe /i AzureADPasswordProtectionDCAgentSetup.msi /quiet /qn /norestart
```

The `/norestart` flag can be omitted if you prefer to have the installer automatically reboot the machine.

The software installation, or uninstallation, requires a restart. This requirement is because password filter DLLs are only loaded or unloaded by a restart.

The installation of on-premises Microsoft Entra Password Protection is complete after the DC agent software is installed on a domain controller and that computer is rebooted. No other configuration is required or possible. Password change events against the on-premises DCs use the configured banned password lists from Microsoft Entra.

Tip

You can install the Microsoft Entra Password Protection DC agent on a machine that's not yet a domain controller. In this case, the service starts and runs but remains inactive until the machine is promoted to be a domain controller.

### Upgrading the proxy service

The Microsoft Entra Password Protection proxy-service supports automatic upgrade. Automatic upgrade uses the Microsoft Entra Connect Agent Updater service, which is installed side by side with the proxy service. Automatic upgrade is on by default and might be enabled or disabled using the `Set-AzureADPasswordProtectionProxyConfiguration` cmdlet.

The current setting can be queried using the `Get-AzureADPasswordProtectionProxyConfiguration` cmdlet. We recommend that the automatic upgrade setting always is enabled.

The `Get-AzureADPasswordProtectionProxy` cmdlet might be used to query the software version of all currently installed Microsoft Entra Password Protection proxy-servers in a forest.

#### Manual upgrade process

A manual upgrade is accomplished by running the latest version of the `AzureADPasswordProtectionProxySetup.exe` software installer. The latest version of the software is available on the Microsoft Download Center.

It's not required to uninstall the current version of the Microsoft Entra Password Protection proxy-service—the installer performs an in-place upgrade. No reboot should be required when upgrading the proxy service. The software upgrade might be automated using standard MSI procedures, such as `AzureADPasswordProtectionProxySetup.exe /quiet`.

### Upgrading the DC agent

When a newer version of the Microsoft Entra Password Protection DC agent software is available, the upgrade is accomplished by running the latest version of the `AzureADPasswordProtectionDCAgentSetup.msi` software package. The latest version of the software is available on the Microsoft Download Center.

It's not required to uninstall the current version of the DC agent software—the installer performs an in-place upgrade. A reboot is always required when upgrading the DC agent software. This requirement is caused by core Windows behavior.

The software upgrade might be automated using standard MSI procedures, such as `msiexec.exe /i AzureADPasswordProtectionDCAgentSetup.msi /quiet /qn /norestart`.

You might omit the `/norestart` flag if you prefer to have the installer automatically reboot the machine.

The `Get-AzureADPasswordProtectionDCAgent` cmdlet might be used to query the software version of all currently installed Microsoft Entra Password Protection DC agents in a forest.


## Configure smart lockout thresholds

Smart lockout helps prevent bad actors who try to guess your users' passwords or use brute-force methods to get in. Smart lockout can recognize sign-ins that come from valid users and treat them differently than ones of attackers and other unknown sources. Attackers get locked out, while your users continue to access their accounts and be productive.

### How smart lockout works

By default, smart lockout locks the account from sign-in attempts for one minute after 10 failed attempts. The account locks again after each subsequent failed sign-in attempt, for one minute at first and then longer in subsequent attempts. To minimize the ways an attacker could work around this behavior, we don't disclose the rate at which the lockout period grows over additional unsuccessful sign-in attempts.

Smart lockout tracks the last three bad-password hashes to avoid incrementing the lockout counter for the same password. If someone enters the same bad password multiple times, this behavior won't cause the account to lock out.

Federated deployments that use AD FS 2016 and AF FS 2019 can enable similar benefits using AD FS Extranet Lockout and Extranet Smart Lockout.

Smart lockout is always on, for all Microsoft Entra ID customers, with these default settings that offer the right mix of security and usability. Customization of the smart lockout settings, with values specific to your organization, requires Microsoft Entra ID Premium P1 or higher licenses for your users.

Using smart lockout doesn't guarantee that a genuine user is never locked out. When smart lockout locks a user account, we try our best to not lock out the genuine user. The lockout service attempts to ensure that bad actors can't gain access to a genuine user account. The following considerations apply:

- Each Microsoft Entra data center tracks lockouts independently. A user has (`threshold\_limit * datacenter\_count`) number of attempts, if the user hits each data center.
- Smart lockout uses *familiar location* versus *unfamiliar location* to differentiate between a bad actor and the genuine user. Unfamiliar and familiar locations both have separate lockout counters.

Smart lockout can be integrated with hybrid deployments that use password hash sync or pass-through authentication to protect on-premises Active Directory Domain Services (AD DS) accounts from being locked out by attackers. By setting smart lockout policies in Microsoft Entra ID appropriately, attacks can be filtered out before they reach on-premises AD DS.

When the admin configures pass-through authentication, the following considerations apply:

- The Microsoft Entra lockout threshold is less than the AD DS account lockout threshold. Set the values so that the AD DS account lockout threshold is at least two or three times greater than the Microsoft Entra lockout threshold.
- The Microsoft Entra lockout duration must be set longer than the AD DS account lockout duration. The duration is set in seconds, while the AD duration is set in minutes.

For example, if you want your smart lockout duration to be higher than AD DS, then Microsoft Entra ID would be 120 seconds (2 minutes) while your on-premises AD is set to 1 minute (60 seconds). If you want your lockout threshold to be 5, then you want your on-premises AD lockout threshold to be 10. This configuration would ensure smart lockout prevents your on-premises AD accounts from being locked out by brute force attacks on your Microsoft Entra accounts.


## Exercise - Manage Microsoft Entra smart lockout values

### Manage Microsoft Entra smart lockout values

Based on your organizational requirements, you can customize the Microsoft Entra smart lockout values. Customization of the smart lockout settings, with values specific to your organization, requires Microsoft Entra ID Premium P1 or higher licenses for your users.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/) using a Global administrator account.
2. Open the portal menu and then select **Protection**.
3. On the Protection menu, select **Authentication Methods**.
4. On Authentications methods menu, select **Password protection**.
5. In the Password protection settings, in the **Lockout duration in seconds** box, set the value to 120.
6. Next to **Mode**, select **Enforced**.
7. Save your changes.

Note

When the smart lockout threshold is triggered, you will get the following message while the account is locked:

Your account is temporarily locked to prevent unauthorized use. Try again later, and if you still have trouble, contact your admin.


## Implement Kerberos and certificate-based authentication in Microsoft Entra ID

You can provide single sign-on for on-premises applications published through Application Proxy. The apps are secured with integrated Windows authentication. These applications require a Kerberos ticket for access. Application Proxy uses Kerberos Constrained Delegation (KCD) to support these applications. You can enable single sign-on to your applications using integrated Windows authentication. Give the Application Proxy connectors permission in Active Directory to impersonate users. The connectors use this permission to send and receive tokens on their behalf.

#### Kerberos authentication process flow

![Diagram of the process flow for Kerberos authentication in Microsoft Entra ID.  Full description of process is in the content.](https://learn.microsoft.com../../wwl-sci/manage-user-authentication/media/kerberos-authentication.png)

1. The user enters the URL to access the on premises application through Application Proxy.
2. Application Proxy redirects the request to Microsoft Entra authentication services to preauthenticate. At this point, Microsoft Entra ID applies any applicable authentication and authorization policies, such as multifactor authentication. If the user is validated, Microsoft Entra ID creates a token and sends it to the user.
3. The user passes the token to Application Proxy.
4. Application Proxy validates the token and retrieves the User Principal Name (UPN) from it, and then the Connector pulls the UPN, and the Service Principal Name (SPN) through a dually authenticated secure channel.
5. The Connector performs Kerberos Constrained Delegation (KCD) negotiation with the on premises AD, impersonating the user to get a Kerberos token to the application.
6. Active Directory sends the Kerberos token for the application to the Connector.
7. The Connector sends the original request to the application server, using the Kerberos token it received from AD.
8. The application sends the response to the Connector, which is then returned to the Application Proxy service and finally to the user.

#### Ensure your environment is ready

Before you get started with single sign-on for integrated windows authentication applications, make sure your environment is ready with the following settings and configurations:

- Your apps, like SharePoint Web apps, are set to use integrated Windows authentication.
- All your apps have Service Principal names.
- The server running the Connector and the server running the app are domain joined.
- The server running the Connector has access to read the TokenGroupsGlobalAndUniversal attribute for users.


## Configure Microsoft Entra user authentication for virtual machines

Organizations can now improve the security of Windows and Linux virtual machines (VMs) in Azure by integrating with Microsoft Entra authentication. You can now use Microsoft Entra ID as a core authentication platform to connect to:

- Windows Server 2022, 2025, or later installed with Desktop Experience.
- Windows 11 24H2 or later.
- Linux virtual machine.

You can then centrally control and enforce role-based-access and Conditional Access policies that allow or deny access to the VMs.

#### Benefits

- Use Microsoft Entra credentials to sign into Windows VMs in Azure.
- Reduce reliance on local administrator accounts.
- Password complexity and password lifetime policies configured for your Microsoft Entra ID.
- Configure Conditional Access policies to require multifactor authentication and other signals such as risky-user or sign-in risk.

#### Configure Microsoft Entra sign-in for Windows VMs

To use Microsoft Entra sign-in for Windows VM in Azure, you must:

- First enable the Microsoft Entra sign-in option for your Windows VM.
- Then configure Azure role assignments for users who are authorized to sign into the VM.

#### Configure Microsoft Entra sign-in for Linux VMs

You can enable Microsoft Entra sign-in for any of the supported Linux distributions mentioned using the Azure portal. As an example, to create an Ubuntu Server 18.04 Long Term Support (LTS) VM in Azure with Microsoft Entra ID authentication:

1. Sign into the Azure portal, with an account that has access to create VMs, and select + Create a resource.
2. Select **Create** under Ubuntu Server 18.04 LTS in the Popular view.
3. On the Management tab, Check the box to enable `Login with Microsoft Entra ID`.
4. Ensure System assigned managed identity is checked.
5. Complete the Linux virtual machine setup.


## Module assessment

Choose the best response for each of the questions below.

### Check your knowledge


## Summary and resources

Now that you have reviewed this module, you should be able to:

- Administer authentication methods (FIDO2/Passwordless).
- Implement an authentication solution based on Windows Hello for Business.
- Configure and deploy self-service password reset.
- Deploy and manage password protection and smart lockouts.
- Implement Kerberos and certificate-based authentication.
- Configure Microsoft Entra ID user authentication to virtual machines.

### Resources

To learn more about some of the idea we've examined in this module, check out the following links to documentation.

- [Enable combined security information registration in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-registration-mfa-sspr-combined)
- [Create a resilient access control management strategy in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-resilient-controls)
- [Windows Hello for Business overview](https://learn.microsoft.com/en-us/windows/security/identity-protection/hello-for-business/)
- [Microsoft Authenticator app](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-authenticator-app)
- [Passwordless authentication options for Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/authentication/how-to-plan-prerequisites-phishing-resistant-passwordless-authentication)
- [Authentication methods in Microsoft Entra ID - OATH tokens](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-oath-tokens)
- [Configure and enable users for SMS-based authentication using Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-authentication-sms-signin)
- [Enable on-premises Microsoft Entra Password Protection](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-password-ban-bad-on-premises-deploy)
- [Single sign-on using Kerberos for Application Proxy applications](https://learn.microsoft.com/en-us/entra/identity/app-proxy/how-to-configure-sso)


---

# Plan, implement, and administer Conditional Access

_https://learn.microsoft.com/en-us/training/modules/plan-implement-administer-conditional-access/_


## Introduction

Conditional Access gives a fine granularity of control over which users and identities can perform specific activities, access resources, and ensure data and systems are safe. With the introduction of Microsoft Entra Agent ID control, now extends to AI agents—you apply the same Zero Trust principles to agent identities that you apply to users and workload identities.

### Learning objectives

In this module, you will:

- Plan and implement security defaults.
- Plan Conditional Access policies.
- Implement Conditional Access policy controls and assignments (targeting, applications, and conditions).
- Test and troubleshoot Conditional Access policies.
- Implement application controls.
- Implement session management.
- Configure continuous access evaluation.
- Identify how agent identities are protected using Conditional Access.


## Plan security defaults

Managing security can be difficult with common identity-related attacks like password spray, replay, and phishing becoming more popular. Security defaults provide secure default settings that Microsoft manages on behalf of organizations to keep customers safe until organizations are ready to manage their own identity security story. Security defaults provide preconfigured security settings, such as:

- Requiring all users to register for multifactor authentication.
- Requiring administrators to perform multifactor authentication.
- Blocking legacy authentication protocols.
- Requiring users to perform multifactor authentication when necessary.
- Protecting privileged activities like access to the Azure portal.

### Availability

Microsoft security defaults are available to everyone. The goal is to ensure that all organizations have a basic level of security enabled at no extra cost. If your tenant was created on or after October 22, 2019, security defaults might already be enabled. To protect all users, security defaults are enabled on all new tenants at creation.

To enable or disable security defaults, sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a Conditional Access Administrator, then browse to **Entra ID** > **Overview** > **Properties**, and select **Manage security defaults**.

#### Who's it for?

| **Who should use security defaults?** | **Who shouldn't use security defaults?** |
|---|---|
| Organizations that want to increase their security posture but don't know how or where to start | Organizations currently using Conditional Access policies to bring signals together, make decisions, and enforce organizational policies |
| Organizations utilizing the free tier of Microsoft Entra ID Licensing | Organization with Microsoft Entra ID Premium licenses |
|   | Organizations with complex security requirements that warrant using Conditional Access |

### Policies enforced

#### Unified multifactor authentication registration

All users in your tenant must register for multifactor authentication (MFA) using the Microsoft Authenticator app. Registration is required immediately—there's no grace period. When users sign in after security defaults are enabled, they're prompted to register before they can access any resources. The MFA prompt uses number matching, where users enter a number displayed on screen into the Microsoft Authenticator app, which helps prevent MFA fatigue attacks.

#### Protecting administrators

Users with privileged access often increase access to your environment. Due to the power these accounts have, you should treat them with special care. One common method to improve the protection of privileged accounts is to require a stronger form of account verification for sign-in. In Microsoft Entra ID, you can get a stronger account verification by requiring multifactor authentication.

After registration with multifactor authentication is finished, the following Microsoft Entra administrator roles are required to perform other authentication every time they sign in:

- Global Administrator
- Application Administrator
- Authentication Administrator
- Authentication Policy Administrator
- Billing Administrator
- Cloud Application Administrator
- Conditional Access Administrator
- Exchange Administrator
- Helpdesk Administrator
- Identity Governance Administrator
- Password Administrator
- Privileged Authentication Administrator
- Privileged Role Administrator
- Security Administrator
- SharePoint Administrator
- User Administrator

#### Protecting all users

We tend to think that administrator accounts are the only accounts that need extra layers of authentication. Administrators have broad access to sensitive information and can make changes to subscription-wide settings. But attackers frequently target end users.

After these attackers gain access, they can request access to privileged information on behalf of the original account holder. They can even download the entire directory to perform a phishing attack on your whole organization.

One common method to improve protection for all users is to require a stronger form of account verification, such as multifactor authentication, for everyone. After users complete Multifactor Authentication registration, they'll be prompted for extra authentication whenever necessary. This functionality protects all applications registered with Microsoft Entra ID, including SaaS applications.

#### Blocking legacy authentication

To give your users easy access to your cloud apps, Microsoft Entra ID supports various authentication protocols, including legacy authentication. *Legacy authentication* is an authentication request made by:

- Clients that don't use modern authentication (for example, an Office 2010 client). Modern authentication encompasses clients that implement protocols, such as OAuth 2.0, to support features like multifactor authentication and smart cards. Legacy authentication typically only supports less secure mechanisms like passwords.
- Client that uses mail protocols such as IMAP, SMTP, or POP3.

Today, most compromising sign-in attempts come from legacy authentication. Legacy authentication doesn't support multifactor authentication. Even if you have a multifactor authentication policy enabled on your directory, an attacker can authenticate by using an older protocol and bypass multifactor authentication.

After security defaults are enabled in your tenant, all authentication requests made by an older protocol will be blocked. Security defaults blocks Exchange Active Sync basic authentication.


## Exercise - Work with security defaults

In this exercise, try enabling security defaults.

Note

Security Defaults are enabled on new subscriptions, so you can review the process of enabling and disabling.

To enable security defaults in your directory:

1. Browse to the [Microsoft Entra admin center](https://entra.microsoft.com/) and sign in as a Security administrator, or a Conditional Access administrator.
2. Select the Show portal menu hamburger icon and then select Identity - Overview.
3. In the left navigation, in the Manage section, select **Properties**.
4. At the bottom of the Properties dialog, select **Manage Security defaults**.
5. Set the **Enable Security defaults** toggle to **Yes.**
6. Select **Save**.

#### Disabling security defaults

Organizations that choose to implement Conditional Access policies that replace security defaults must disable security defaults.

To disable security defaults in your directory:

1. Browse to the [Azure portal](https://portal.azure.com/) and sign in using an Administrator account for the directory.
2. Select the Show portal menu hamburger icon and then select Microsoft Entra ID.
3. At the bottom of the Properties dialog, select **Manage Security defaults**.
4. Set the **Enable security defaults** toggle to **No**.
5. Select **Save**.


## Plan Conditional Access policies

Planning your Conditional Access deployment is critical to achieving your organization's access strategy for apps and resources.

In a mobile-first, cloud-first world, your users access your organization's resources from anywhere using various devices and apps. As a result, focusing on who can access a resource is no longer enough. You also need to consider where the user is, the device being used, the resource being accessed, and more.

Microsoft Entra Conditional Access (CA) analyzes signals, such as user, device, and location, to automate decisions and enforce organizational access policies for resource. You can use CA policies to apply access controls like multifactor authentication (MFA). CA policies allow you to prompt users for MFA when needed for security and to stay out of users’ way when not needed.

![Diagram of how Conditional Access works. Centralize identity provider verifies rules before access is granted.](https://learn.microsoft.com../../wwl-sci/plan-implement-administer-conditional-access/media/conditional-access-overview-how-it-works.png)

Although security defaults ensure a basic level of security, your organization needs more flexibility than security defaults offer. You can use CA to customize security defaults with more granularities and to configure new policies that meet your requirements.

#### Benefits

The benefits of deploying CA are:

- Increase productivity - only interrupt users with a sign-in condition like MFA when one or more signals warrants it. CA policies allow you to control when users are prompted for MFA, when access is blocked, and when they must use a trusted device.
- Manage risk - automating risk assessment with policy conditions means risky sign-ins are at once identified and remediated or blocked. Coupling Conditional Access with Identity Protection, which detects anomalies and suspicious events, allows you to target when access to resources is blocked or gated.
- Address compliance and governance - Conditional access enables you to audit access to applications, present terms of use for consent, and restrict access based on compliance policies.
- Manage cost - moving access policies to Microsoft Entra ID reduces the reliance on custom or on-premises solutions for CA and their infrastructure costs.
- Zero Trust - Conditional Access helps you move toward a zero-trust environment.

### Understand Conditional Access policy components

CA policies are if-then statements: If an assignment is met, then apply these access controls. When the admin configures CA policies, conditions are called *assignments*. CA policies allow you to enforce access controls on your organization’s apps based on certain assignments.

Assignments define the users and groups to be affected by the policy, the cloud apps or actions to which the policy will apply, and the conditions under which the policy will apply. Access control settings grant or block access to different cloud apps and can enable limited experiences within specific cloud apps.

Some common questions about assignments, access controls, and session controls:

- Users and Groups: Which users and groups will be included in or excluded from the policy? Does this policy include all users, specific group of users, directory roles, or external users?
- Cloud apps or actions: What application(s) will the policy apply to? What user actions will be subject to this policy?
- Conditions: Which device platforms will be included in or excluded from the policy? What are the organization’s trusted locations?
- Access controls: Do you want to grant access to resources by implementing requirements such as MFA, devices marked as compliant, or Microsoft Entra hybrid joined devices?
- Session controls: Do you want to control access to cloud apps by implementing requirements such as app enforced permissions or Conditional Access App Control?

With the introduction of Microsoft Entra Agent ID, agent identities are now first-class principals in Microsoft Entra ID. Like users or service principals, agents can be targeted by Conditional Access policies — allowing you to apply the same Zero Trust controls to AI agents that you apply to human identities. You treat agent identities similarly to how you treat workload identities: scope policies by identity type, enforce appropriate access controls, and exclude emergency or trusted agents where necessary.

#### Access token issuance

Access tokens enable clients to securely call protected web APIs, and they're used by web APIs to perform authentication and authorization. Per the OAuth specification, access tokens are opaque strings without a set format. Some identity providers (IDPs) use GUIDs; others use encrypted blobs. The Microsoft identity platform uses a variety of access token formats depending on the configuration of the API that accepts the token.

It’s important to understand how access tokens are issued.

![Diagram of the flow of issues an access token for conditional access, and how it's used.](https://learn.microsoft.com../../wwl-sci/plan-implement-administer-conditional-access/media/access-policy-token-issuance.png)

Note

If no assignment is required, and no CA policy is in effect, the default behavior is to issue an access token.

For example, consider a policy where:

IF user is in Group 1, THEN force MFA to access App 1.

IF a user not in Group 1 attempts to access the app, THEN the **“if"** condition is met, and a token is issued. Excluding users outside of Group 1 requires a separate policy to block all other users.

### Follow best practices

The Conditional Access framework provides you with great configuration flexibility. However, great flexibility also means you should carefully review each configuration policy before releasing it to avoid undesirable results.

#### Set up emergency access accounts

If you misconfigure a policy, it can lock the organizations out of the Azure portal. Mitigate the accidental administrator lockout by creating two or more emergency access accounts in your organization. You'll learn more about emergency access accounts later in this course.

#### Set up report-only mode

It can be difficult to predict the number and names of users affected by common deployment initiatives such as:

- Blocking legacy authentication.
- Requiring MFA.
- Implementing sign-in risk policies.

Report-only mode allows administrators to evaluate the CA policies before enabling them in their environment.

#### Exclude countries from which you never expect a sign-in

Microsoft Entra ID allows you to create named locations. Create a named location that includes all of the countries from which you would never expect a sign-in to occur. Then create a policy for all apps that blocks sign in from that named location. **Be sure to exempt your administrators from this policy**.

### Common policies

When planning your CA policy solution, assess whether you need to create policies to achieve the following outcomes.

- **Require MFA.** Common use cases include requiring MFA by admins, to specific apps, for all users, or from network locations you don't trust.
- **Respond to potentially compromised accounts.** Three default policies can be enabled: require all users to register for MFA, require a password change for users who are high-risk, and require MFA for users with medium or high sign-in risk.
- **Require managed devices.** The proliferation of supported devices to access your cloud resources helps to improve the productivity of your users. You probably don't want certain resources in your environment to be accessed by devices with an unknown protection level. For those resources, require that users can only access them using a managed device.
- **Require approved client applications.** Employees use their mobile devices for both personal and work tasks. For BYOD scenarios, you must decide whether to manage the entire device or just the data on it. If managing only data and access, you can require approved cloud apps that can protect your corporate data.
- **Block access.** Blocking access overrides all other assignments for a user and has the power to block your entire organization from signing on to your tenant. It can be used, for example, when you're migrating an app to Microsoft Entra ID, but you aren't ready for anyone to sign in to it yet. You can also block certain network locations from accessing your cloud apps or block apps using legacy authentication from accessing your tenant resources.  Important If you create a policy to block access for all users, be sure to exclude emergency access accounts and consider excluding all administrators from the policy.

### Build and test policies

At each stage of your deployment, ensure that you're evaluating that results are as expected.

When new policies are ready, deploy them in phases in the production environment:

- Provide internal change communication to end users.
- Start with a small set of users, and verify that the policy behaves as expected.
- When you expand a policy to include more users, continue to exclude all administrators. Excluding administrators ensures that someone still has access to a policy if a change is required.
- Apply a policy to all users only after it's thoroughly tested. Ensure you have at least one administrator account to which a policy doesn't apply.

#### Create test users

Create a set of test users that reflect the users in your production environment. Creating test users enables you to verify policies work as expected before you apply to real users and potentially disrupt their access to apps and resources.

Some organizations have test tenants for this purpose. However, it can be difficult to recreate all conditions and apps in a test tenant to fully test the outcome of a policy.

#### Create a test plan

The test plan is important to have a comparison between the expected results and the actual results. You should always have an expectation before testing something. The following table outlines example test cases. Adjust the scenarios and expected results based on how your CA policies are configured.

| **Name of policy** | **Scenario** | **Expected result** |
|---|---|---|
| Require MFA when working | Authorized user signs into app while on a trusted location / work | User isn't prompted to MFA. User is authorized for access. User is connecting from a trusted location. You could choose to require MFA in this case. |
| Require MFA when working | Authorized user signs into app while not on a trusted location / work | User is prompted to MFA and can sign in successfully |
| Require MFA (for admin) | Global Admin signs into app | Admin is prompted to MFA |
| Risky sign-ins | User signs into app using an unapproved browser | User is prompted to MFA |
| Device management | Authorized user attempts to sign in from an authorized device | Access granted |
| Device management | Authorized user attempts to sign in from an unauthorized device | Access blocked |
| Password change for risky users | Authorized user attempts to sign in with compromised credentials (high risk sign-in) | User is prompted to change password or access is blocked based on your policy |

### License requirements

- Free Microsoft Entra ID - No Conditional Access
- Free Office 365 subscription - No Conditional Access
- Microsoft Entra ID Premium 1 (or Microsoft 365 E3 and up) - Conditional access work based on standard rules
- Microsoft Entra ID Premium 2 - Conditional Access, and you get the ability to use Risky sign-in, Risky Users, and risk-based sign-in options as well (from Identity Protection)


## Implement Conditional Access policy controls and assignments

Conditional Access is an advanced capability of Microsoft Entra ID that enables you to specify detailed policies that control who can access your resources. Using Conditional Access, you can protect your applications by limiting users' access based on signals like group membership, device compliance, network location, and sign-in risk.

### Create a Conditional Access policy

This is an abbreviated guide to creating a Conditional Access policy. Full documentation is available at [What is Conditional Access?](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview).

To create a new policy:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a Conditional Access Administrator.
2. Browse to **Protection** > **Conditional Access**.
3. Select **+ New policy**.
4. Give the policy a meaningful name.
5. Configure **Assignments** — select the users, groups, or roles the policy applies to.
6. Configure **Target resources** — select the cloud apps or user actions the policy covers.
7. Configure any additional **Conditions** such as sign-in risk, device platform, or location.
8. Under **Access controls**, configure the **Grant** or **Session** controls to apply.
9. Set **Enable policy** to **Report-only** to test impact before enabling, then select **Create**.

Microsoft recommends starting all new policies in report-only mode. Monitor sign-in logs to verify expected behavior before switching the policy to **On**.

### Sign-in risk-based Conditional Access

Most users have a normal behavior that can be tracked. When they fall outside of this norm, it could be risky to allow them to just sign in. You want to block that user or ask them to perform multifactor authentication to prove that they are really who they say they are.

A sign-in risk represents the probability that a given authentication request isn't authorized by the identity owner. Organizations with Microsoft Entra ID Premium P2 licenses can create Conditional Access policies incorporating Microsoft Entra Identity Protection sign-in risk detections.

This policy can be assigned either through Conditional Access itself or through Microsoft Entra Identity Protection. Organizations should choose one of two options to enable a sign-in risk-based Conditional Access policy requiring a secure password change.

### User risk-based Conditional Access

Microsoft works with researchers, law enforcement, various security teams at Microsoft, and other trusted sources to find leaked username and password pairs. Organizations with Microsoft Entra ID Premium P2 licenses can create Conditional Access policies incorporating Microsoft Entra Identity Protection user risk detections.

Like sign-in risk-based Conditional Access, this policy can be assigned either through Conditional Access itself or through Microsoft Entra Identity Protection.

### Securing security info registration

Securing when and how users register for multifactor authentication and self-service password reset is now possible with user actions in Conditional Access policy. This preview feature is available to organizations that have enabled the combined registration preview. This functionality might be enabled in organizations where they want to use conditions like trusted network location to restrict access to register for multifactor authentication and self-service password reset (SSPR).

#### Create a policy to require registration from a trusted location

The following policy applies to all selected users who attempt to register using the combined registration experience, and it blocks access unless they are connecting from a location marked as a trusted network.

1. In the **Microsoft Entra admin center**, browse to **Protection**, then **Conditional Access**.
2. Select **+ Create new policy**.
3. In **Name**, Enter a Name for this policy. For example, **Combined Security Info Registration on Trusted Networks**.
4. Under **Assignments**, select **Users and groups**, and select the users and groups you want this policy to apply to.   Note If you were targeting AI agents instead of users, you would select **Workload identities** in the Assignments area and choose your agent identity from Microsoft Entra Agent ID at this step. The rest of the policy structure remains the same.
  1. Under **Exclude**, select **Users and groups** and choose your organization's emergency access or break-glass accounts.
  2. Select **Done**.

5. Under **Cloud apps or actions**, select **User actions**, check **Register security information**.
6. Under **Conditions**, select **Locations**.
  - Configure **Yes**.
  - Include **Any location**.
  - Exclude **All trusted locations**.
  - Select **Done** on the **Locations** screen.
  - Select **Done** on the **Conditions** screen.

7. Under **Conditions**, in **Client apps (Preview)**, set **Configure** to **Yes**, and select **Done**.
8. Under **Access controls**, select **Grant**.
  - Select **Block access**.
  - Then use the **Select** option.

9. Set **Enable policy** to **On**.
10. Then select **Save**.

At step 6 in this policy, organizations have choices they can make. The policy above requires registration from a trusted network location. Organizations can choose to utilize any available conditions in place of **Locations**. Remember that this policy is a block policy, so anything included is blocked.

You can choose to use device state instead of location in step 6 above:

1. Under **Conditions**, select **Device state (Preview)**.
2. Configure **Yes**.
3. Include **All device state**.
4. Exclude **Device Hybrid Microsoft Entra joined** and/or **Device marked as compliant.**
5. Select **Done** on the **Locations** screen.
6. Select **Done** on the **Conditions** screen.

### Block access by location

With the location condition in Conditional Access, you can control access to your cloud apps based on the network location of a user. The location condition is commonly used to block access from countries/regions where your organization knows traffic should not come from.

#### Define locations

1. Sign in to the **Microsoft Entra admin portal** as a Security Administrator, or Conditional Access Administrator.
2. Browse to **Protection**, then **Conditional Access**, then **Named locations**.
3. Choose **New location**.
4. Give your location a name.
5. Choose **IP ranges** if you know the specific externally accessible IPv4 address ranges that make up that location or **Countries/Regions**.
  1. Provide the **IP ranges** or select the **Countries/Regions** for the location you are specifying.

  - If you choose Countries/Regions, you can optionally choose to include unknown areas.

6. Choose **Save.**

#### Create a Conditional Access policy

1. Sign in to the **Microsoft Entra admin center** as a Security Administrator, or Conditional Access Administrator.
2. Browse to **Protection**, then **Conditional Access**.
3. Select **+ Create new policy**.
4. Give your policy a name. We recommend that organizations create a meaningful standard for the names of their policies.
5. Under **Assignments**, select **Users and groups.**
  1. Under **Include**, select **All users**.
  2. Under **Exclude**, select **Users and groups** and choose your organization's emergency access or break-glass accounts.
  3. Select **Done**.

6. Under **Cloud apps or actions**, then **Include**, and select **All cloud apps**.
7. Under **Conditions**, then **Location**.
  1. Set **Configure** to **Yes.**
  2. Under **Include**, select **Selected locations.**
  3. Select the blocked location you created for your organization.
  4. Choose **Select**.

8. Under **Access controls**, then select **Block Access**, and select **Select**.
9. Confirm your settings and set **Enable policy** to **On**.
10. Select **Create** to create Conditional Access Policy.

### Require compliant devices

Organizations that have deployed Microsoft Intune can use the information returned from their devices to identify devices that meet compliance requirements, such as:

- Requiring a PIN to unlock.
- Requiring device encryption.
- Requiring a minimum or maximum operating system version.
- Requiring a device is not jailbroken or rooted.

This policy compliance information is forwarded to Microsoft Entra ID where Conditional Access can make decisions to grant or block access to resources.

#### Create a Conditional Access policy

The following steps will help create a Conditional Access policy to require devices accessing resources be marked as compliant with your organization's Intune compliance policies.

1. Sign in to the **Microsoft Entra admin center** as a Security Administrator, or Conditional Access Administrator.
2. Browse to **Protection**, then **Conditional Access**.
3. Select **+ Create new policy**.
4. Give your policy a name. We recommend that organizations create a meaningful standard for the names of their policies.
5. Under **Assignments**, select **Users and groups.**
  1. Under **Include**, select **All users**.
  2. Under **Exclude**, select **Users and groups** and choose your organization's emergency access or break-glass accounts.
  3. Select **Done**.

6. Under **Cloud apps or actions**, then **Include**, and select **All cloud apps**.
  1. If you must exclude specific applications from your policy, you can choose them from the **Exclude** tab under **Select excluded cloud apps** and choose **Select**.
  2. Select **Done**.

7. Under **Conditions**, then **Client apps (Preview)**, then **Select the client apps this policy will apply to**, leave all defaults selected and select **Done**.
8. Under **Access controls**, then **Grant**, select **Require device to be marked as compliant**.
9. Select **Select**.
10. Confirm your settings and set **Enable policy** to **On**.
11. Select **Create** to create to enable your policy.

Note

You can enroll your new devices to Intune even if you select Require device to be marked as compliant for All users and All cloud apps using the steps above. Require device to be marked as compliant control does not block Intune enrollment.

#### Known behavior

On Windows 7, iOS, Android, macOS, and some third-party web browsers, Microsoft Entra ID identifies the device using a client certificate that is provisioned when the device is registered with Microsoft Entra ID. When a user first signs in through the browser, the user is prompted to select the certificate. The end user must select this certificate before they can continue to use the browser.

### Block access

For organizations with a conservative cloud migration approach, the block all policy is an option that can be used.

Warning

Misconfiguration of a block policy can lead to organizations being locked out of the Azure portal.

Policies like these can have unintended side effects. Proper testing and validation are vital before enabling. Administrators should utilize tools such as Conditional Access report-only mode and the What If tool in Conditional Access.

#### User exclusions

Conditional Access policies are powerful tools. We recommend excluding the following accounts from your policy:

- **Emergency access** or **break-glass** accounts to prevent tenant-wide account lockout. In the unlikely scenario that all administrators are locked out of your tenant, your emergency-access administrative account can be used to sign into the tenant and take steps to recover access.
- **Service accounts** and **service principals**, such as the Microsoft Entra Connect Sync Account. Service accounts are non-interactive accounts that are not tied to any particular user. They are normally used by back-end services allowing programmatic access to applications, but they are also used to sign in to systems for administrative purposes. Service accounts like these should be excluded since MFA can't be completed programmatically. Calls made by service principals are not blocked by Conditional Access.
  - If your organization has these accounts in use in scripts or code, consider replacing them with managed identities. As a temporary workaround, you can exclude these specific accounts from the baseline policy.

- **Agent identities**: AI agents registered in Microsoft Entra Agent ID can be targeted by or excluded from Conditional Access policies just like service principals. Ensure any trusted agents that require uninterrupted access are explicitly excluded, and review agent-targeted policies alongside your workload identity policies.

### Conditional Access Terms of Use (TOU)

You can create Terms of Use (TOU) for your site in the Identity Governance tools. Launch the identity governance app, and choose **Terms of use** from the menu. You have to supply a PDF file with the terms for the user. You can set up several rules like when the terms will expire, or whether the user has to open them before accepting. Once created, you can build a custom conditional rule right in identity governance. Or you can save the terms and use Conditional Access in Microsoft Entra ID. To create new Terms of use you fill in the above dialog.

The linking of consent (accept terms before access) and conditional access is getting more and more traction. Organizations get the ability to enforce a user to consent to the terms of use. Additionally, organizations can expire the consent given or change the terms of use, and request the user attests again.

Before accessing certain cloud apps in your environment, you might want to get consent from users in form of accepting your terms of use (ToU). Microsoft Entra Conditional Access provides you with:

- A simple method to configure ToU
- The option to require accepting your terms of use through a Conditional Access policy


## Exercise - Implement Conditional Access policies roles and assignments

In this exercise, create a conditional access policy.

Microsoft Entra Conditional Access is an advanced feature of Microsoft Entra ID that allows you to specify detailed policies that control who can access your resources. Using Conditional Access, you can protect your applications by limiting users' access based on things like groups, device type, location, and role.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/) using a Global administrator account.
2. Open the portal menu and then select **Identity**.
3. Then select **Protection**.
4. On the Security blade, in the left navigation, select **Conditional access**.
5. On the top menu, select **+ Create new policy**.
6. In the **Name** box, enter **Test app conditional access**. This is the name being using for this exercise, you can choose another name if you wish.
7. Under **Assignments**, select **Users and groups**.
8. On the Include tab, select the **Users and groups** check box.
9. In the Select pane, select your administrator account and then select **Select**.
10. Select **Cloud apps or actions**.
11. Verify **Cloud apps** is selected and then select **Select apps**.
12. In the Select pane, select **My apps** and then select **Select**.
13. Select **Conditions** and then select **Locations**.
14. Under **Configure**, select **Yes** and then select **Any location**.
15. Under **Access controls**, select **Grant**.
16. In the Grant pane, select **Block access** and then select **Select**.

Important

This policy is being configured for the exercise only and is being used to quickly demonstrate a conditional access policy.

1. Under **Enable policy**, select **On**, and then select **Create**.

### Test the conditional access policy

You should test your conditional access policies to ensure they working as expected.

1. Open a new browser tab and then browse to **[https://myapps.microsoft.com](https://myapps.microsoft.com)**.
2. Your credentials should be passed through.
3. Verify you are prevented from successfully accessing your My Apps page.      Note If you are signed in, close the tab, wait 1-2 minutes, and then retry.
4. Close the tab and return to the Conditional Access blade.
5. Select the **Test app conditional access** policy.
6. Under **Enable policy**, select **Off** and then select **Save**.


## Test and troubleshoot Conditional Access policies

The Conditional Access framework provides you with great configuration flexibility. However, great flexibility also means that you should carefully review each configuration policy before releasing it to avoid undesirable results. In this context, you should pay special attention to assignments affecting complete sets such as **all users / groups / cloud apps**.

Organizations should avoid the following configurations:

**For all users, all cloud apps:**

- **Block access** - This configuration blocks your entire organization.
- **Require Hybrid Microsoft Entra domain joined device** - This access-blocking policy also has the potential to block access for all users in your organization if they don't have a hybrid Microsoft Entra joined device.
- **Require app protection policy** - This access-blocking policy also has the potential to block access for all users in your organization if you don't have an Intune policy. If you're an administrator without a client application that has an Intune app protection policy, this policy blocks you from getting back into portals such as Intune and Azure.

**For all users, all cloud apps, all device platforms:**

- **Block access** - This configuration blocks your entire organization.

### Conditional Access sign-in interrupt

The first way is to review the error message that appears. For problems signing in when using a web browser, the error page itself has detailed information. This information alone describes what the problem is and suggests a solution.

In the above error, the message states that the application can only be accessed from devices or client applications that meet the company's mobile device management policy. In this case, the application and device don't meet that policy.

### Microsoft Entra sign-in events

The second method to get detailed information about the sign-in interruption is to review the Microsoft Entra sign-in events to see which Conditional Access policy or policies were applied and why.

Find more information about the problem by clicking **More Details** in the initial error page. Clicking **More Details** will reveal troubleshooting information that's helpful when searching the Microsoft Entra sign-in events for the specific failure event the user saw or when opening a support incident with Microsoft.

To find out which Conditional Access policy or policies applied and why, do the following steps:

1. Sign into the Microsoft Entra admin center as a Security Administrator, or Global Reader.
2. Browse to **Identity - Monitoring and Health**, then **Sign-ins**.
3. Find the event for the sign-in to review. Add or remove filters and columns to filter out unnecessary information.
  1. Add filters to narrow the scope:
    1. Correlation ID when you have a specific event to investigate.
    2. Conditional access to see policy failure and success. Scope your filter to show only failures to limit results.
    3. Username to see information related to specific users.
    4. Date scoped to the time frame in question.

4. Once the sign-in event that corresponds to the user's sign-in failure has been found select the **Conditional Access** tab, the tab will show the specific policy or policies that resulted in the sign-in interruption.
  1. Information in the **Troubleshooting and support** tab provides a clear reason as to why a sign-in failed, such as a device that didn't meet compliance requirements.
  2. To investigate further, drill down into the configuration of the policies by clicking on the Policy Name. Clicking the Policy Name will show the policy configuration user interface for the selected policy for review and editing.
  3. The client user and device details that were used for the Conditional Access policy assessment are also available in the **Basic Info**, **Location**, **Device Info**, **Authentication Details**, and **Additional Details** tabs of the sign-in event.

#### Policy details

Selecting the ellipsis on the right side of the policy in a sign-in event brings up policy details. This gives administrators additional information about why a policy was successfully applied or not.

The left side provides details collected at sign-in, and the right side provides details of whether those details satisfy the requirements of the applied Conditional Access policies. Conditional Access policies only apply when all conditions are satisfied or not configured.

If the information in the event isn't enough to understand the sign-in results or adjust the policy to get desired results, then a support incident can be opened. Navigate to that sign-in event's **Troubleshooting and support** tab and select **Create a new support request**.

When submitting the incident, provide the request ID and time and date from the sign-in event in the incident submission details. This information will allow Microsoft support to find the event you're concerned about.


## Implement application controls

Conditional Access App Control enables user app access and sessions to be monitored and controlled in real time based on access and session policies. Access and session policies are used within the Microsoft Defender for Cloud Apps portal to further refine filters and set actions to be taken on a user.

### Conditional Access App Control

Conditional Access App Control uses a reverse proxy architecture and is uniquely integrated with Microsoft Entra Conditional Access. Microsoft Entra Conditional Access allows you to enforce access controls on your organization’s apps based on certain conditions. The conditions define who (user or group of users) and what (which cloud apps) and where (which locations and networks) a Conditional Access policy is applied to. After you’ve determined the conditions, you can route users to Microsoft Defender for Cloud Apps where you can protect data with Conditional Access App Control by applying access and session controls.

With the access and session policies, you can:

- **Prevent data exfiltration:** You can block the download, cut, copy, and print of sensitive documents on, for example, unmanaged devices.
- **Protect on download:** Instead of blocking the download of sensitive documents, you can require documents to be labeled and protected with Azure Information Protection. This action ensures the document is protected and user access is restricted in a potentially risky session.
- **Prevent upload of unlabeled files:** Before a sensitive file is uploaded, distributed, and used by others, it’s important to make sure that the file has the right label and protection. You can ensure that unlabeled files with sensitive content are blocked from being uploaded until the user classifies the content.
- **Monitor user sessions for compliance:** Risky users are monitored when they sign into apps and their actions are logged from within the session. You can investigate and analyze user behavior to understand where, and under what conditions, session policies should be applied in the future.
- **Block access:** You can granularly block access for specific apps and users depending on several risk factors. For example, you can block them if they're using client certificates as a form of device management.
- **Block custom activities:** Some apps have unique scenarios that carry risk, for example, sending messages with sensitive content in apps like Microsoft Teams or Slack. In these kinds of scenarios, you can scan messages for sensitive content and block them in real time.

### How to: Require app protection policy and an approved client app for cloud app access with Conditional Access

People regularly use their mobile devices for both personal and work tasks. While making sure staff can be productive, organizations also want to prevent data loss from potentially unsecure applications. With Conditional Access, organizations can restrict access to approved (modern authentication-capable) client apps.

This section presents two scenarios to configure Conditional Access policies for resources like Microsoft 365, Exchange Online, and SharePoint Online.

Note

In order to require approved client apps for iOS and Android devices, these devices must first register in Microsoft Entra ID.

#### Scenario 1: Microsoft 365 apps require an approved client app

In this scenario, Contoso has decided that users using mobile devices can access all Microsoft 365 services as long as they use approved client apps, like Outlook mobile, OneDrive, and Microsoft Teams. All of their users already sign in with Microsoft Entra credentials and have licenses assigned to them that include Microsoft Entra ID Premium P1 or P2 and Microsoft Intune.

Organizations must complete the following three steps in order to require the use of an approved client app on mobile devices.

**Step 1: Policy for Android and iOS based modern authentication clients requiring the use of an approved client application when accessing Exchange Online.**

1. Sign in to the **Microsoft Entra admin center** as a Security Administrator, or Conditional Access Administrator.
2. Browse to **Identity**, then **Protection**, and then **Conditional Access**.
3. Select **+Create new policy**.
4. Give your policy a name. We recommend that organizations create a meaningful standard for the names of their policies.
5. Under **Assignments**, select **Users and groups.**
  1. Under **Include**, select **All users** or the specific **Users and groups** you wish to apply this policy to.
  2. Select **Done**.

6. Under **Cloud apps or actions**, then **Include**, select **Office 365**.
7. Under **Conditions**, select **Device platforms**.
  1. Set **Configure** to **Yes**.
  2. Include **Android** and **iOS**.

8. Under **Conditions**, select **Client apps (preview)**.
9. Set **Configure** to **Yes**.
10. Select **Mobile apps and desktop clients** and **Modern authentication clients**.
11. Under **Access controls**, then **Grant**, select **Grant access**, **Require approved client app**, and select **Select**.
12. Confirm your settings and set **Enable policy** to **On**.
13. Select **Create** to create and enable your policy.

**Step 2: Configure an Microsoft Entra Conditional Access policy for Exchange Online with ActiveSync (EAS).**

1. Browse to **Identity**, then **Protection**, and then **Conditional Access**.
2. Select **+Create new policy**.
3. Give your policy a name. We recommend that organizations create a meaningful standard for the names of their policies.
4. Under **Assignments**, select **Users and groups.**
  1. Under **Include**, select **All users** or the specific **Users and groups** you wish to apply this policy to.
  2. Select **Done**.

5. Under **Cloud apps or actions**, then **Include**, select **Office 365 Exchange Online**.
6. Under **Conditions**:
  1. **Client apps (preview)**:
    1. Set **Configure** to **Yes**.
    2. Select **Mobile apps and desktop clients** and **Exchange ActiveSync clients**.

7. Under **Access controls**, then **Grant**, select **Grant access**, **Require approved client app**, and select **Select**.
8. Confirm your settings and set **Enable policy** to **On**.
9. Select **Create** to create and enable your policy.

**Step 3: Configure Intune app protection policy for iOS and Android client applications.**

Review the article [How to create and assign app protection policies](https://learn.microsoft.com/en-us/mem/intune/apps/app-protection-policies) for steps to create app protection policies for Android and iOS.

#### Scenario 2: Exchange Online and SharePoint Online require an approved client app

In this scenario, Contoso has decided that users can only access email and SharePoint data on mobile devices as long as they use an approved client app like Outlook mobile. All of their users already sign in with Microsoft Entra credentials and have licenses assigned to them that include Microsoft Entra ID Premium P1 or P2 and Microsoft Intune.

Organizations must complete the following three steps in order to require the use of an approved client app on mobile devices and Exchange ActiveSync clients.

**Step 1: Policy for Android and iOS based modern authentication clients requiring the use of an approved client application when accessing Exchange Online and SharePoint Online.**

1. Sign in to the **Microsoft Entra admin center** as a Security Administrator, or Conditional Access Administrator.
2. Browse to **Identity**, then **Protection**, and then **Conditional Access**.
3. Select **New policy**.
4. Give your policy a name. We recommend that organizations create a meaningful standard for the names of their policies.
5. Under **Assignments**, select **Users and groups.**
  1. Under **Include**, select **All users** or the specific **Users and groups** you wish to apply this policy to.
  2. Select **Done**.

6. Under **Cloud apps or actions**, then **Include**, select **Office 365 Exchange Online** and **Office 365 SharePoint Online**.
7. Under **Conditions**, select **Device platforms**.
  1. Set **Configure** to **Yes**.
  2. Include **Android** and **iOS**.

8. Under **Conditions**, select **Client apps (preview)**.
  1. Set **Configure** to **Yes**.
  2. Select **Mobile apps and desktop clients** and **Modern authentication clients**.

9. Under **Access controls**, then **Grant**, select **Grant access**, **Require approved client app**, and select **Select**.
10. Confirm your settings and set **Enable policy** to **On**.
11. Select **Create** to create and enable your policy.

**Step 2: Policy for Exchange ActiveSync clients requiring the use of an approved client app.**

1. Browse to **Identity**, then **Protection**, and then **Conditional Access**.
2. Select **New policy**.
3. Give your policy a name. We recommend that organizations create a meaningful standard for the names of their policies.
4. Under **Assignments**, select **Users and groups.**
  1. Under **Include**, select **All users** or the specific **Users and groups** you wish to apply this policy to.
  2. Select **Done**.

5. Under **Cloud apps or actions**, then **Include**, select **Office 365 Exchange Online**.
6. Under **Conditions**:
7. **Client apps (preview)**:
  1. Set **Configure** to **Yes**.
  2. Select **Mobile apps and desktop clients** and **Exchange ActiveSync clients**.

8. Under **Access controls**, then **Grant**, select **Grant access**, **Require approved client app**, and select **Select**.
9. Confirm your settings and set **Enable policy** to **On**.
10. Select **Create** to create and enable your policy.

**Step 3: Configure Intune app protection policy for iOS and Android client applications.**

Review the article [How to create and assign app protection policies](https://learn.microsoft.com/en-us/mem/intune/apps/app-protection-policies) for steps to create app protection policies for Android and iOS.

### App protection policies overview

App protection policies (APP) are rules that ensure an organization's data remains safe or contained in a managed app. A policy can be a rule that is enforced when the user attempts to access or move "corporate" data, or a set of actions that are prohibited or monitored when the user is inside the app. A managed app has app protection policies applied to it, and it can be managed by Intune.

Mobile Application Management (MAM) app protection policies allow you to manage and protect your organization's data within an application. With **MAM without enrollment** (MAM-WE), a work or school-related app that contains sensitive data can be managed on almost any device, including personal devices in **bring-your-own-device** (BYOD) scenarios. Many productivity apps, such as the Microsoft Office apps, can be managed by Intune MAM.

#### How you can protect app data

Your employees use mobile devices for both personal and work tasks. While making sure your employees can be productive, you want to prevent data loss—intentional and unintentional. You'll also want to protect company data that is accessed from devices that you don't manage.

You can use Intune app protection policies **independent of any mobile-device management (MDM) solution**. This independence helps you protect your company's data with or without enrolling devices in a device management solution. By implementing **app-level policies**, you can restrict access to company resources and keep data within the purview of your IT department.

#### App protection policies on devices

App protection policies can be configured for apps that run on devices that are:

- **Enrolled in Microsoft Intune:** These devices are typically corporate owned.
- **Enrolled in a third-party MDM solution:** These devices are typically corporate owned.  Note Mobile app management policies should not be used with third-party mobile app management or secure container solutions.
- **Not enrolled in any mobile device management solution:** These devices are typically employee-owned devices that aren't managed or enrolled in Intune or other MDM solutions.  Important You can create mobile app management policies for Office mobile apps that connect to Microsoft 365 services. You can also protect access to Exchange on-premises mailboxes by creating Intune app protection policies for Outlook for iOS/iPadOS and Android enabled with hybrid Modern Authentication. Before using this feature, make sure you meet the Outlook for iOS/iPadOS and Android requirements. App protection policies are not supported for other apps that connect to on-premises Exchange or SharePoint services.

#### Benefits of using app protection policies

The important benefits of using app protection policies are the following:

- **Protecting your company data at the app level.** Because mobile app management doesn't require device management, you can protect company data on both managed and unmanaged devices. The management is centered on the user identity, which removes the requirement for device management.
- **End-user productivity isn't affected and policies don't apply when using the app in a personal context.** The policies are applied only in a work context, which gives you the ability to protect company data without touching personal data.
- **App protection policies ensure that the app-layer protections are in place.** For example, you can:
  - Require a PIN to open an app in a work context.
  - Control the sharing of data between apps.
  - Prevent the saving of company app data to a personal storage location.

- **MDM, in addition to MAM, ensures that the device is protected**. For example, you can require a PIN to access the device, or you can deploy managed apps to the device. You can also deploy apps to devices through your MDM solution to give you more control over app management.

There are additional benefits to using MDM with app protection policies, and companies can use app protection policies with and without MDM at the same time. For example, consider an employee who uses a phone issued by the company, as well as their personal tablet. The company phone is enrolled in MDM and protected by app protection policies, while the personal device is protected by app protection policies only.

If you apply a MAM policy to the user without setting the device state, the user will get the MAM policy on both the BYOD device and the Intune-managed device. You can also apply a MAM policy based on the managed state. So when you create an app protection policy, next to **Target to all app types**, you'd select **No**. Then do any of the following:

- Apply a less strict MAM policy to Intune managed devices, and apply a more restrictive MAM policy to non MDM-enrolled devices.
- Apply a MAM policy to unenrolled devices only.


## Implement session management and continuous access evaluation

In complex deployments, organizations might have a need to restrict authentication sessions. Some scenarios might include:

- Resource access from an unmanaged or shared device.
- Access to sensitive information from an external network.
- High priority or executive users.
- Critical business applications.

Conditional Access controls allow you to create policies that target specific use cases within your organization without affecting all users.

Before diving into details on how to configure the policy, let’s examine the default configuration.

### User sign-in frequency

Sign-in frequency defines the time period before a user is asked to sign in again when attempting to access a resource.

The Microsoft Entra ID default configuration for user sign-in frequency is a rolling window of 90 days. Asking users for credentials often seems like a sensible thing to do, but it can backfire: Users who are trained to enter their credentials without thinking can unintentionally supply them to a malicious credential prompt.

It might sound alarming to not ask for a user to sign back in; in reality any violation of IT policies will revoke the session. Some examples include a password change, an incompliant device, or an account disable. You can also explicitly revoke users’ sessions using PowerShell. The Microsoft Entra ID default configuration comes down to 'don’t ask users to provide their credentials if the security posture of their sessions hasn't changed.'

The sign-in frequency setting works with apps that have implemented OAUTH2 or OIDC protocols according to the standards. Most apps for Windows, Mac, and mobile, including the following web applications, comply with the setting.

- Word, Excel, PowerPoint Online
- OneNote Online
- Office.com
- Microsoft 365 Admin portal
- Exchange Online
- SharePoint and OneDrive
- Teams web client
- Dynamics CRM Online
- Azure portal

The sign-in frequency setting works with SAML applications as well, as long as they don't drop their own cookies and are redirected back to Microsoft Entra ID for authentication on a regular basis.

#### User sign-in frequency and multifactor authentication

Sign-in frequency previously applied only to the first factor authentication on devices that were Microsoft Entra joined, Hybrid Microsoft Entra joined, and Microsoft Entra registered. There was no easy way for our customers to re-enforce multifactor authentication (MFA) on those devices. Based on customer feedback, sign-in frequency will apply for MFA as well.

![Diagram of multifactor authentication sign-in process with sign-in frequency.](https://learn.microsoft.com../../wwl-sci/plan-implement-administer-conditional-access/media/conditional-access-flow-chart.png)

#### User sign-in frequency and device identities

If you have Microsoft Entra joined, hybrid Microsoft Entra joined, or Microsoft Entra registered devices, when a user unlocks their device or signs in interactively, this event will satisfy the sign-in frequency policy as well. In the following two examples user sign-in frequency is set to one hour:

Example 1:

- At 00:00, a user signs in to their Windows 10 Microsoft Entra joined device and starts work on a document stored on SharePoint Online.
- The user continues working on the same document on their device for an hour.
- At 01:00, the user is prompted to sign in again based on the sign-in frequency requirement in the Conditional Access policy configured by their administrator.

Example 2:

- At 00:00, a user signs in to their Windows 10 Microsoft Entra joined device and starts work on a document stored on SharePoint Online.
- At 00:30, the user gets up and takes a break, locking their device.
- At 00:45, the user returns from their break and unlocks the device.
- At 01:45, the user is prompted to sign in again based on the sign-in frequency requirement in the Conditional Access policy configured by their administrator since the last sign-in happened at 00:45.

### Persistence of browsing sessions

A persistent browser session allows users to remain signed in after closing and reopening their browser window. The Microsoft Entra ID default for browser session persistence allows users on personal devices to choose whether to persist the session by showing a 'Stay signed in?' prompt after successful authentication.

### Validation

Use the What-If tool to simulate a sign-in from the user to the target application and other conditions based on how you configured your policy. The authentication session management controls show up in the result of the tool.

### Policy deployment

To make sure that your policy works as expected, the recommended best practice is to test it before rolling it out into production. Ideally, use a test tenant to verify whether your new policy works as intended.

### Continuous Access Evaluation (CAE)

Token expiration and refresh are a standard mechanism in the industry. When a client application like Outlook connects to a service like Exchange Online, the API requests are authorized using OAuth 2.0 access tokens. By default, access tokens are valid for one hour, when they expire the client is redirected to Microsoft Entra ID to refresh them. That refresh period provides an opportunity to reevaluate policies for user access. For example: we might choose not to refresh the token because of a Conditional Access policy, or because the user has been disabled in the directory.

However, there is lag between when conditions change for a user, and when policy changes are enforced. Timely response to policy violations or security issues really requires a "conversation" between the token issuer, and the relying party (enlightened app). This two-way conversation gives us two important capabilities. The relying party can see when properties change, like network location, and tell the token issuer. It also gives the token issuer a way to tell the relying party to stop respecting tokens for a given user because of account compromise, disablement, or other concerns. The mechanism for this conversation is continuous access evaluation (CAE).

#### Benefits

There are several key benefits to continuous access evaluation.

- User termination or password change/reset: User session revocation will be enforced in near real time.
- Network location change: Conditional Access location policies will be enforced in near real time.
- Token export to a machine outside of a trusted network can be prevented with Conditional Access location policies.

#### Evaluation and revocation process flow

![Diagram of the process flow when an access token is revoked and a client has to reverify access.](https://learn.microsoft.com../../wwl-sci/plan-implement-administer-conditional-access/media/user-revocation-event-flow.png)

1. A continuous access evaluation (CAE)-capable client presents credentials or a refresh token to Microsoft Entra ID asking for an access token for some resource.
2. An access token is returned along with other artifacts to the client.
3. An Administrator explicitly revokes all refresh tokens for the user. A revocation event will be sent to the resource provider from Microsoft Entra ID.
4. An access token is presented to the resource provider. The resource provider evaluates the validity of the token and checks whether there's any revocation event for the user. The resource provider uses this information to decide to grant access to the resource or not.
5. In the case of the diagram, the resource provider denies access, and sends a 401+ claim challenge back to the client.
6. The CAE-capable client understands the 401+ claim challenge. It bypasses the caches and goes back to step 1, sending its refresh token along with the claim challenge back to Microsoft Entra ID. Microsoft Entra ID will then reevaluate all the conditions and prompt the user to reauthenticate in this case.


## Exercise - Configure authentication session controls

In this exercise you will configure sign in frequency controls using a conditional access policy.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/) using an Administrator account.
2. Open the portal menu and then select **Identity**.
3. On the Identity menu, then select **Protection**.
4. On the Protection menu, select **Conditional access**.
5. On the top menu, select **New policy**.

1. In the **Name** box, enter **Sign in frequency**.
2. Under **Assignments**, select **Users and groups**.
3. On the Include tab, select the **Users and groups** check box.
4. In the Select pane, select your administrator account and then select **Select**.
5. Select **Cloud apps or actions**.
6. Verify **Cloud apps** is selected and then select **Select apps**.
7. In the Select pane, select **Office 365** and then select **Select**.
8. Under **Access controls**, select **Session**.
9. In the **Session** pane, select **Sign-in frequency**.
10. In the value box, enter **30**.
11. Select the units menu, select **Days**, and then select **Select**.
12. Under **Enable policy**, select **Report-only**, and then select **Create**.

## Microsoft Entra Conditional Access Optimization agent

The Conditional Access optimization agent helps you ensure all users are protected by policy. It recommends policies and changes based on best practices aligned with Zero Trust and Microsoft learning.

The Conditional Access optimization agent evaluates policies such as requiring multifactor authentication (MFA). The agent enforces device based controls (device compliance, app protection policies, and domain-joined devices). Finally, the agent can help block legacy authentication and device code flow.

The agent also evaluates all existing enabled policies to propose potential consolidation of similar policies.

#### Requirement to use the Conditional Access optimization agent

- You must have at least the **Microsoft Entra ID P1 license**.
- You must have available **Security Compute Units (SCU)**.
- To activate the agent the first time, you need the Security Administrator or higher role.
- You can assign Conditional Access Administrators with Security Copilot access.
  - For more information, see Assign Security Copilot access

- Device-based controls require **Microsoft Intune licenses**.

#### Conditional Access optimization agent key features

The Conditional Access optimization agent scans your tenant for new users and applications and determines if Conditional Access policies are applicable. The key features include:

| Feature | Description |
|---|---|
| Require MFA | The agent identifies users who aren't covered by a Conditional Access policy that requires MFA and can update the policy. |
| Require device-based controls | The agent can enforce device-based controls, such as device compliance, app protection policies, and domain-joined devices. |
| Block legacy authentication | User accounts with legacy authentication are blocked from signing in. |
| Policy consolidation | The agent scans your policy and identifies overlapping settings. For example, if you have more than one policy that has the same grant controls, the agent suggests consolidating those policies into one. |
| Block device code flow | The agent looks for a policy blocking device code flow authentication. |
| One-click remediation | When the agent identifies a suggestion, you can select Apply suggestion to have the agent update the associated policy with one press of a button. |

### Give the Conditional Access optimization agent a try

[](https://microsoftlearning.github.io/click-throughs/docs/IG/interactive_guide_explore_conditional_access_optimization_agent_web/story.html)


## Module assessment

Choose the best response for each of the questions below.

### Check your knowledge


## Summary and resources

After completing this module, you are able to:

- Plan and implement security defaults.
- Plan your Conditional Access policies.
- Implement Conditional Access policy controls and assignments (targeting, applications, and conditions).
- Test and troubleshoot Conditional Access policies.
- Implement application controls.
- Implement session management.
- Configure continuous access evaluation.

### Resources

To learn more about the technology in this module, check out the following links to documentation:

- [What is Conditional Access?](https://youtu.be/ffMAw2IVO7A)
- [How to deploy Conditional Access?](https://youtu.be/c_izIRNJNuk)
- [How to roll out CA policies to end users?](https://youtu.be/0_Fze7Zpyvc)
- [Conditional Access with device controls](https://youtu.be/NcONUf-jeS4)
- [Conditional Access with Microsoft Entra MFA](https://youtu.be/Tbc-SU97G-w)
- [Conditional Access in Enterprise Mobility + Security](https://youtu.be/A7IrxAH87wc)
- [Using the location condition in a Conditional Access policy](https://learn.microsoft.com/en-us/entra/identity/conditional-access/howto-conditional-access-policy-location)
- [Use compliance policies to set rules for devices you manage with Intune](https://learn.microsoft.com/en-us/mem/intune/fundamentals/deployment-plan-compliance-policies)
- [Introducing security defaults](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/introducing-security-defaults/ba-p/1061414)
- [Plan a Conditional Access deployment](https://learn.microsoft.com/en-us/entra/identity/conditional-access/plan-conditional-access)
- [Continuous Access Evaluation (CAE](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-continuous-access-evaluation))
- [Conditional Access for agent identities (Microsoft Entra Agent ID)](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-policy-common)


---

# Manage Microsoft Entra Identity Protection

_https://learn.microsoft.com/en-us/training/modules/manage-azure-active-directory-identity-protection/_


## Introduction

Protecting users' identity by monitoring their usage and sign-in patterns ensures a secure cloud solution. Explore how to design and implement Microsoft Entra Identity Protection.

#### Watch this video

In this video, get a high-level overview of Identity Protection, a feature of Microsoft Entra ID. You learn about different types of detections, risks, and risk policies that exist in Identity Protection. The video explains the benefits of the risk policies, recent UX enhancements, powerful APIs, improved risk assessment, and overall alignment along risky users and risky sign-ins.

### Learning objectives

In this module, you will:

- Review Identity Protection basics.
- Implement and manage a user risk policy.
- Implement and manage sign-in risk policies.
- Implement and manage multifactor authentication (MFA) registration policy.
- Monitor, investigate, and remediate elevated risky users.
- Explore Microsoft Defender for Identity


## Review identity protection basics

Identity Protection is a service that enables organizations to view the security posture of any account. Organizations can accomplish three key tasks:

- Automate the detection and remediation of identity-based risks.
- Investigate risks using data in the portal.
- Export risk detection data to third-party utilities for further analysis.

Always remember that Microsoft Entra Identity Protection requires a Microsoft Entra ID Premium P2 license to operate. Licensing is covered in more detail in a later unit.

Identity Protection uses the knowledge Microsoft has gained from its position in organizations with Microsoft Entra ID, the consumer space with Microsoft Accounts, and in gaming with Xbox to protect your users. Microsoft analyzes 6.5 trillion signals per day to identify and protect customers from threats.

The signals generated by and fed to Identity Protection can be further fed into tools like Conditional Access to make access decisions or fed back to a security information and event management (SIEM) tool for further investigation based on your organization's enforced policies.

### Risk detection and remediation

Identity Protection identifies risks in the following classifications:

| **Risk detection type** | **Description** |
|---|---|
| Anonymous IP address | Sign in from an anonymous IP address (for example: Tor browser, anonymizer VPNs). |
| Atypical travel | Sign in from an atypical location based on the user's recent sign ins. |
| Malicious IP address | Sign in from a malicious IP address. |
| Unfamiliar sign in properties | Sign in with properties we've not seen recently for the given user. |
| Leaked credentials | Indicates that the user's valid credentials have been leaked. |
| Password spray | Indicates that multiple usernames are being attacked using common passwords in a unified brute-force manner. |
| Microsoft Entra threat intelligence | Microsoft's internal and external threat intelligence sources have identified a known attack pattern. |
| Anomalous token | Detects unusual characteristics in a token, such as an unusual token lifetime or a token replayed from an unfamiliar location. |
| Token issuer anomaly | Detects when the SAML token issuer for the associated SAML token is potentially compromised. |
| Suspicious browser | Detects anomalous sign-in activity across multiple tenants from the same browser. |
| Verified threat actor IP | Detects sign-in activity from IP addresses known to be associated with verified threat actors. |
| New country | This detection is discovered by Microsoft Defender for Cloud Apps (MDCA). |
| Activity from anonymous IP address | This detection is discovered by MDCA. |
| Suspicious inbox forwarding | This detection is discovered by MDCA. |

### Permissions

Identity Protection requires users be a Security Reader, Security Operator, Security Administrator, Global Reader Administrator in order to access.

| **Role** | **Can do** | **Can't do** |
|---|---|---|
| Security Administrator | Full access to Identity Protection | Reset password for a user |
| Security Operator | View all Identity Protection reports and Overview screen, Dismiss user risk, confirm safe sign-in, confirm compromise | Configure or change policies, Reset password for a user, Configure alerts |
| Security Reader | View all Identity Protection reports and Overview screen | Configure or change policies, Reset password for a user, Configure alerts, Give feedback on detections |

The Security Operator role can't access the Risky sign-ins report. Conditional Access Administrators can also create policies that factor in sign-in risk as a condition.

### License requirements

Using this feature requires a Microsoft Entra ID Premium P2 license.

| **Capability** | **Details** | **Microsoft Entra ID Free / Microsoft 365 Apps** | **Microsoft Entra ID Premium P1** | **Microsoft Entra ID Premium P2** |
|---|---|---|---|---|
| Risk policies | User risk policy (via Identity Protection) | No | No | Yes |
| Risk policies | Sign-in risk policy (via Identity Protection or Conditional Access) | No | No | Yes |
| Security reports | Overview | No | No | Yes |
| Security reports | Risky users | Limited information. Only users with medium and high risk are shown. No details drawer or risk history. | Limited information. Only users with medium and high risk are shown. No details drawer or risk history. | Full access |
| Security reports | Risky sign ins | Limited information. No risk detail or risk level is shown. | Limited information. No risk detail or risk level is shown. | Full access |
| Security reports | Risk detections | No | Limited information. No details drawer. | Full access |
| Notifications | Users at risk detected alerts | No | No | Yes |
| Notifications | Weekly digest | No | No | Yes |
|   | MFA registration policy | No | No | Yes |


## Implement and manage user risk policy

There are two risk policies that can be enabled in the directory:

- **Sign-in risk policy**: The sign-in risk policy detects suspicious actions that come along with the sign-in. It's focused on the sign-in activity itself and analyzes the probability that the sign-in was performed by some other than the user.
- **User risk policy**: The user risk policy detects the probability that a user account has been compromised by detecting risk events that are atypical of a user's behavior.

Both policies work to automate the response to risk detections in your environment and allow users to self-remediate when risk is detected.

#### Watch the video

In this video, learn how to deploy Microsoft Entra Identity Protection by configuring risk-based policies (user risk and sign-in risk) in your organization. You also learn best practices on how to gradually roll out these policies and MFA registration in your organization.

### Prerequisites

If your organization wants to allow users to self-remediate when risks are detected, users must be registered for both self-service password reset and multifactor authentication. We recommend enabling the combined security information registration experience. Allowing users to self-remediate gets them back to a productive state more quickly without requiring administrator intervention. Administrators can still see these events and investigate them after the fact.

### Choosing acceptable risk levels

Organizations must decide the level of risk they're willing to accept, balancing user experience and security posture.

Microsoft's recommendation is to set the user risk policy threshold to **High** and the sign-in risk policy to **Medium and higher**.

Choosing a **High** threshold reduces the number of times a policy is triggered and minimizes the challenge to users. However, it excludes **Low** and **Medium** risk detections from the policy, which does not block an attacker from exploiting a compromised identity. Selecting a **Low** threshold introduces extra user interrupts but increased security posture.

### Exclusions

All of the policies allow for excluding users such as your emergency access or break-glass administrator accounts. Organizations determine when they need to exclude other accounts from specific policies based on the way the accounts are used. All exclusions should be reviewed regularly to see if they're still applicable.

Configured trusted network locations are used by Identity Protection in some risk detections to reduce false positives.


## Exercise enable sign-in risk policy

### Enable user risk policy

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/) using a Global administrator account.
2. Open the portal menu and then select **Identity**.
3. On the Identity menu, select **Protection**.
4. On the Security blade, in the left navigation, select **Identity protection**.
5. In the Identity protection blade, in the left navigation, select User risk policy.
6. Under **Assignments**, select **All users** and review the available options. You can select from **All users** or **Select individuals and groups** if limiting your rollout. Additionally, you can choose to exclude users from the policy.
7. Under **User risk**, select **Low and above**.
8. In the User risk pane, select **High** and then select **Done**.
9. Under **Controls**, then **Access**, and then select **Block access**.
10. In the Access pane, review the available options.

Tip

Microsoft's recommendation is to Allow access and Require password change.

1. Select the **Require password change** check box and then select **Done**.
2. Under **Enforce Policy**, select **On** and then select **Save**.

### Enable sign-in risk policy

1. On the Identity protection blade, in the left navigation, select **Sign-in risk policy**.
2. As with the User risk policy, the Sign-in risk policy can be assigned to users and groups and allows you to exclude users from the policy.
3. Under **Sign-in risk**, select **Medium and above**.
4. In the Sign-in risk pane, select **High** and then select **Done**.
5. Under **Controls**, then **Access**, and then select **Block access**.
6. Select the **Require multifactor authentication** check box and then select **Done**.
7. Under **Enforce Policy**, select **On** and then select **Save**.


## Exercise configure Microsoft Entra multifactor authentication registration policy

### Policy configuration

Multifactor authentication provides a means to verify who you are using more than just a username and password. It provides a second layer of security to user sign-ins. For users to be able to respond to MFA prompts, they must first register for multifactor authentication.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/) using a Global administrator account.
2. Open the portal menu and then select **Identity**.
3. On the Identity men, select **Protection**.
4. On the Security blade, in the left navigation, select **Identity protection**.
5. In the Identity protection blade, in the left navigation, select **Multifactor authentication registration policy**.
6. Under **Assignments**, select **All users** and review the available options. You can select from **All users** or **Select individuals and groups** if limiting your rollout. Additionally, you can choose to exclude users from the policy.
7. Under **Controls**, notice that the **Require Microsoft Entra ID multifactor authentication registration** is selected and cannot be changed.
8. Under **Enforce Policy**, select **Enabled** and then select **Save**.


## Monitor, investigate, and remediate elevated risky users

### Investigate risk

Identity Protection provides organizations with three reports they can use to investigate identity risks in their environment: **risky users**, **risky sign-ins**, and **risk detections**. Investigating events is key to better understanding and identifying any weak points in your security strategy.

All three reports allow for downloading of events in .CSV format for further analysis outside of the Azure portal. The risky users and risky sign-ins reports allow for downloading the most recent 2,500 entries, while the risk detections report allows for downloading the most recent 5,000 records.

Organizations can take advantage of the Microsoft Graph API integrations to aggregate data with other sources they have access to as an organization.

You can find the three reports in the **Microsoft Entra admin center**, then **Identity**, and then **Protection - Identity Protection**.

#### Navigating the reports

Each report launches with a list of all detections for the period shown at the top of the report. Each report allows for the addition or removal of columns based on administrator preference. Administrators can choose to download the data in .CSV or .JSON format. Reports can be filtered using the filters across the top of the report.

Selecting individual entries enables more entries at the top of the report, such as the ability to confirm a sign-in as compromised or safe, confirm a user as compromised, or dismiss user risk.

Selecting individual entries expands a details window below the detections. The details view allows administrators to investigate and perform actions on each detection.

#### Risky users

With the information provided by the risky users report, administrators can find:

- Which users are at risk, have had risk remediated, or have had risk dismissed?
- Details about detections.
- History of all risky sign-ins.
- Risk history.

Administrators can then choose to take action on these events. They can choose to:

- Reset the user password.
- Confirm user compromise.
- Dismiss user risk.
- Block user from signing in.
- Investigate in Microsoft Defender for Identity.

#### Risky sign-ins

The risky sign-ins report contains filterable data for up to the past 30 days (one month).

With the information provided by the risky sign-ins report, administrators can find:

- Which sign-ins are classified as at risk, confirmed compromised, confirmed safe, dismissed, or remediated.
- Real-time and aggregate risk levels associated with sign-in attempts.
- Detection types triggered.
- Conditional Access policies applied.
- MFA details.
- Device information.
- Application information.
- Location information.

Administrators can then choose to take action on these events. Administrators can choose to:

- Confirm sign-in compromise.
- Confirm sign-in safe.

#### Risk detections

The risk detections report contains filterable data for up to the past 90 days (three months).

With the information provided by the risk detections report, administrators can find:

- Information about each risk detection including type.
- Other risks triggered at the same time.
- Sign-in attempt location.

Administrators can then choose to return to the user's risk or sign-ins report to take actions based on information gathered.

The risk detection report also provides a clickable link to the detection in the Microsoft Defender for Cloud Apps (MDCA) portal where you can view more logs and alerts.

Note

Our system detects that the risk event that contributed to the risk user risk score was a false positive or that the user risk was remediated with policy enforcement such as completing an MFA prompt or secure password change. Therefore, our system dismisses the risk state, and a risk detail of “AI confirmed sign-in safe” will surface and no longer contribute to the user’s risk.

### Remediate risks and unblock users

After completing your investigation, you'll want to take action to remediate the risk or unblock users. Organizations also have the option to enable automated remediation using their risk policies. Organizations should try to close all risk detections that they're presented with in a time period your organization is comfortable with. Microsoft recommends closing events as soon as possible because time matters when working with risk.

#### Remediation

All active risk detections contribute to the calculation of a value called *user risk level*. The user risk level is an indicator (low, medium, high) for the probability that an account has been compromised. As an administrator, you want to get all risk detections closed, so that the affected users are no longer at risk.

Some risk detections are marked by Identity Protection as "Closed (system)" because the events were no longer determined to be risky.

Administrators have the following options to remediate:

- Self-remediation with risk policy.
- Manual password reset.
- Dismiss user risk.
- Close individual risk detections manually.

#### Self-remediation with risk policy

If you allow users to self-remediate, with multifactor authentication (MFA) and self-service password reset (SSPR) in your risk policies, they can unblock themselves when risk is detected. These detections are then considered closed. Users must have previously registered for MFA and SSPR in order to use when risk is detected.

Some detections don't raise risk to the level where a user self-remediation would be required, but administrators should still evaluate these detections. Administrators determine that other measures are necessary, such as blocking access from locations or lowering the acceptable risk in their policies.

#### Manual password reset

If requiring a password reset using a user risk policy isn't an option, administrators can close all risk detections for a user with a manual password reset.

Administrators are given two options when resetting a password for their users:

**Generate a temporary password** - By generating a temporary password, you can immediately bring an identity back into a safe state. This method requires contacting the affected users since they need to know what the temporary password is. Because the password is temporary, the user is prompted to change the password to something new during the next sign-in.

**Require the user to reset password** - Requiring the users to reset passwords enables self-recovery without contacting help desk or an administrator. This method only applies to users who are registered for MFA and SSPR. For users who haven't been registered, this option isn't available.

#### Dismiss user risk

If a password reset isn't an option for you because, for example, the user has been deleted, you can choose to dismiss user risk detections.

When you select **Dismiss user risk**, all events are closed and the affected user is no longer at risk. However, because this method doesn't affect the existing password, it doesn't bring the related identity back into a safe state.

#### Close individual risk detections manually

By closing individual risk detections manually, you can lower the user risk level. Typically, risk detections are closed manually in response to a related investigation, such as when talking to a user reveals that an active risk detection isn't required anymore.

When closing risk detections manually, you can choose to take any of the following actions to change the status of a risk detection:

- Confirm user compromised.
- Dismiss user risk.
- Confirm sign-in safe.
- Confirm sign-in compromised.

#### Unblocking users

An administrator chooses to block a sign-in based on their risk policy or investigations. A block occurs based on either sign-in or user risk.

#### Unblocking based on user risk

To unblock an account blocked due to user risk, administrators have the following options:

- **Reset password** - You can reset the user's password.
- **Dismiss user risk** - The user risk policy blocks a user if the configured user risk level for blocking access has been reached. You can reduce a user's risk level by dismissing user risk or manually closing reported risk detections.
- **Exclude the user from policy** - If you think that the current configuration of your sign-in policy is causing issues for specific users, you can exclude the users from it.
- **Disable policy** - If you think that your policy configuration is causing issues for all your users, you can disable the policy.

#### Unblocking based on sign-in risk

To unblock an account based on sign-in risk, administrators have the following options:

- **Sign in from a familiar location or device** - A common reason for blocked suspicious sign-ins are sign-in attempts from unfamiliar locations or devices. Your users can quickly determine whether this reason is the blocking reason by trying to sign in from a familiar location or device.
- **Exclude the user from policy** - If you think that the current configuration of your sign-in policy is causing issues for specific users, you can exclude the users from it.
- **Disable policy** - If you think that your policy configuration is causing issues for all your users, you can disable the policy.

#### PowerShell preview

Using the Microsoft Graph PowerShell SDK Preview module, organizations can manage risk using PowerShell. The preview modules and sample code are located in the [Azure GitHub repo](https://github.com/AzureAD/IdentityProtectionTools).

### Use the Microsoft Graph API

Microsoft Graph is the Microsoft unified API endpoint and the home of Microsoft Entra Identity Protection APIs. There are three APIs that expose information about risky users and sign-ins: `riskDetection, riskyUsers, and signIn`.

`riskDetection`allows you to query Microsoft Graph for a list of both user and sign-in linked risk detections and associated information about the detection.

`riskyUsers`allows you to query Microsoft Graph for information about users that Identity Protection detected as being risky.

`signIn` allows you to query Microsoft Graph for information on Microsoft Entra ID sign-ins with specific properties related to risk state, detail, and level.

This section gets you started with connecting to the Microsoft Graph and querying these APIs. For an in-depth introduction, full documentation, and access to the Graph Explorer, see the Microsoft Graph site ([https://graph.microsoft.io/](https://graph.microsoft.io/)) or the specific reference documentation for the `riskDetection, riskyUsers, and signIn` APIs.

#### Connect to Microsoft Graph

There are four steps to accessing Identity Protection data through Microsoft Graph: retrieve your domain name, create a new app registration, configure API permissions, and configure a valid credential.

#### Retrieve your domain name

1. Sign in to the Microsoft Entra admin center.
2. Browse to **Identity**, then open Settings, and select **Domain names**.
3. Take note of the .onmicrosoft.com domain. You need this information in a later step.

#### Create a new app registration

1. In the Microsoft Entra admin center, browse to **Identity and Applications**, then **App registrations**.
2. Select **New registration**.
3. On the **Create** page, perform the following steps:
  1. In the **Name** textbox, type a name for your application (for example: Microsoft Entra Risk Detection API).
  2. Under **Supported account types**, select the type of accounts that use the APIs.
  3. Select **Register**.

4. Copy the **Application ID**.

#### Configure API permissions

1. From the **Application** you created, select **API permissions**.
2. On the **Configured permissions** page, in the toolbar on the top, select **Add a permission**.
3. On the **Add API access** page, choose **Select an API**.
4. On the **Select an API** page, select **Microsoft Graph**, and then select **Select**.
5. On the **Request API permissions** page:
  1. Select **Application permissions**.
  2. Select the checkboxes next to IdentityRiskEvent.Read.All and IdentityRiskyUser.Read.All.
  3. Select **Add permissions**.

6. Select **Grant admin consent for domain.**

#### Configure a valid credential

1. From the **Application** you created, select **Certificates and secrets**.
2. Under **Client secrets**, select **New client secret**.
  1. Give the client secret a **Description** and set the expiration time period according to your organizational policies.
  2. Select **Add**.  Note If you lose this key, you have to return to this section and create a new key. Keep this key a secret: Anyone who has it can access your data.

#### Authenticate to Microsoft Graph and query the Identity Protection risk detections API

At this point, you should have:

- The name of your tenant's domain
- The Application (client) ID
- The client secret or certificate

To authenticate, send a post request to `https://login.microsoft.com` with the following parameters in the body:

- grant_type: `client_credentials`
- resource: `https://graph.microsoft.com`
- client_id:
- client_secret:

If successful, this request returns an authentication token. To call the API, create a header with the following parameter:

```http
Authorization`="<token_type> <access_token>"
```

When authenticating, you can find the token type and access token in the returned token.

Send this header as a request to the following API URL: `https://graph.microsoft.com/v1.0/identityProtection/riskDetections`.

The response, if successful, is a collection of identity risk detections and associated data in the OData JSON format, which can be parsed and handled as you see fit.

#### Sample

This sample shows the use of a shared secret to authenticate. In a production environment, storing secrets in code is frowned upon. Organizations can use managed identities for Azure resources to secure these credentials.

Here’s sample code for authenticating and calling the API using PowerShell. Just add your client ID, the secret key, and the tenant domain.

```powershell
    $ClientID      = "<your client ID here>"        # Should be a ~36 hex character string; insert your info here

    $ClientSecret  = "<your client secret here>"    # Should be a ~44 character string; insert your info here

    $tenantdomain  = "<your tenant domain here>"    # For example, contoso.onmicrosoft.com

    $loginURL      = "https://login.microsoft.com"

    $resource      = "https://graph.microsoft.com"

    $body          = @{grant_type="client_credentials";resource=$resource;client_id=$ClientID;client_secret=$ClientSecret}

    $oauth        = Invoke-RestMethod -Method Post -Uri $loginURL/$tenantdomain/oauth2/token?api-version=1.0 -Body $body

    Write-Output $oauth

    if ($oauth.access_token -ne $null) {

        $headerParams = @{'Authorization'="$($oauth.token_type) $($oauth.access_token)"}

        $url = "https://graph.microsoft.com/v1.0/identityProtection/riskDetections"

        Write-Output $url

        $myReport = (Invoke-WebRequest -UseBasicParsing -Headers $headerParams -Uri $url)

        foreach ($event in ($myReport.Content | ConvertFrom-Json).value) {

            Write-Output $event

        }

    } else {

        Write-Host "ERROR: No Access Token"

    }
```

#### Get all of the offline risk detections (riskDetection API)

With Identity Protection sign-in risk policies, you can apply conditions when risk is detected in real time. But what about detections that are discovered offline? To understand what detections occurred offline and, thus, wouldn't have triggered the sign-in risk policy, you can query the `riskDetection` API.

```http
GET https://graph.microsoft.com/v1.0/identityProtection/riskDetections?$filter=detectionTimingType eq 'offline'
```

#### Get all of the users who successfully passed an MFA challenge triggered by risky sign-ins policy (riskyUsers API)

To understand the value Identity Protection risk-based policies have on your organization, you can query all of the users who successfully passed an MFA challenge triggered by a risky sign-ins policy. This information can help you understand which users Identity Protection has falsely detected as a risk and which of your legitimate users are performing actions that the AI deems risky.

```http
GET https://graph.microsoft.com/v1.0/identityProtection/riskyUsers?$filter=riskDetail eq 'userPassedMFADrivenByRiskBasedPolicy'
```


## Implement security for workload identities

Microsoft Entra Identity Protection has historically protected users in detecting, investigating, and remediating identity-based risks. Identity protection has extended these capabilities to workload identities to protect applications, service principals, and Managed Identities.

A workload identity is an identity that allows an application or service principal access to resources, sometimes in the context of a user. These workload identities differ from traditional user accounts as they:

- Can’t perform multifactor authentication.
- Often have no formal lifecycle process.
- Need to store their credentials or secrets somewhere.

These differences make workload identities harder to manage and put them at higher risk for compromise.

#### Requirements to use workload identity protection

To make use of workload identity risk, including the Risky workload identities blade and the Workload identity detections tab in the Risk detections blade, in the Microsoft Entra admin center you must have the following.

- Microsoft Entra ID Premium P2 licensing
- Logged in user must be assigned either:
  - Security administrator
  - Security operator
  - Security reader

#### What types of risks are detected?

| **Detection name** | **Detection type** | **Description** |
|---|---|---|
| Microsoft Entra threat intelligence | Offline | This risk detection indicates some activity that's consistent with known attack patterns based on Microsoft's internal and external threat intelligence sources. |
| Suspicious Sign-ins | Offline | This risk detection indicates sign-in properties or patterns that are unusual for this service principal. |
|   |   | The detection learns the baselines sign-in behavior for workload identities in your tenant in between 2 and 60 days, and fires if one or more of the following unfamiliar properties appear during a later sign-in: IP address / ASN, target resource, user agent, hosting/non-hosting IP change, IP country, credential type. |
| Unusual addition of credentials to an OAuth app | Offline | This detection is discovered by Microsoft Defender for Cloud Apps. This detection identifies the suspicious addition of privileged credentials to an OAuth app. This can indicate that an attacker has compromised the app, and is using it for malicious activity. |
| Admin confirmed account compromised | Offline | This detection indicates an admin has selected 'Confirm compromised' in the Risky Workload Identities UI or using riskyServicePrincipals API. To see which admin has confirmed this account compromised, check the account’s risk history (via UI or API). |
| Leaked Credentials | Offline | This risk detection indicates that the account's valid credentials have been leaked. This leak can occur when someone checks in the credentials in public code artifact on GitHub, or when the credentials are leaked through a data breach. |

#### Add conditional access protection

Using **Conditional Access for workload identities**, you can block access for specific accounts you choose when Identity Protection marks them "at risk." Policy can be applied to single-tenant service principals that have been registered in your tenant. Third-party SaaS, multi-tenanted apps, and managed identities are out of scope.


## Explore Microsoft Defender for Identity

Microsoft Defender for Identity (formerly Azure Advanced Threat Protection) is a cloud-based security solution. Defender for identity uses your on-premises Active Directory signals to identify, detect, and investigate advanced threats, compromised identities, and malicious insider actions directed at your organization. Defender for Identity enables SecOp analysts and security professionals struggling to detect advanced attacks in hybrid environments to:

- Monitor users, entity behavior, and activities with learning-based analytics
- Protect user identities and credentials stored in Active Directory
- Identify and investigate suspicious user activities and advanced attacks throughout the kill chain
- Provide clear incident information on a simple timeline for fast triage

#### Process flow for Defender for Identity

![Diagram of the data flow for protecting identities using Microsoft Defender for Identity.](https://learn.microsoft.com../../wwl-sci/manage-azure-active-directory-identity-protection/media/defender-identity-topology.png)

Defender for Identity consists of the following components:

- **Microsoft Defender portal** - Defender for Identity is managed through the Microsoft Defender portal (`security.microsoft.com`). The portal displays data received from Defender for Identity sensors and enables you to monitor, manage, and investigate threats in your network environment.
- **Defender for Identity sensor** - Defender for Identity sensors can be directly installed on the following servers:
  - Domain controllers: The sensor directly monitors domain controller traffic, without the need for a dedicated server, or configuration of port mirroring.
  - Active Directory Federated Services (AD FS): The sensor directly monitors network traffic and authentication events.

- **Defender for Identity cloud service** - Defender for Identity cloud service runs on Azure infrastructure and is currently deployed in the US, Europe, and Asia. Defender for Identity cloud service is connected to Microsoft's threat intelligence.


## Explore the Identity Risk Management Agent

The Identity Risk Management Agent in Microsoft Entra ID Protection provides proactive risk management capabilities by analyzing user behavior. The agent then suggests actions to mitigate potential identity risks. You can configure the settings to meet your organization's needs. By using a Large Language Model, the agent helps security administrators review and respond to risky activities before they lead to security incidents.

### Prerequisites

- You must have at least the Microsoft Entra ID P2 license.
- You must have available security compute units (SCU).
- You must have the appropriate Microsoft Entra role.
  - **Security Administrator** - required to activate the agent the first time and view the agent and take action on the suggestions.
  - **Security Reader** and **Global Reader** - view the agent and any suggestions (can't take actions).

### How the agent works

The agent checks for new risky identities that weren't previously identified. If new risky identities are found, it takes the following steps (no SCUs consumed):

1. The agent checks for new risky users in your tenant who currently have a risk state of "At risk".
2. The agent identifies risky users that are within your defined scope settings.

If the agent finds new suggestions, it takes the following steps (SCUs consumed):

| Step | Agent activity |
|---|---|
| Investigate the risky user | The agent checks the user's risky sign-ins and risk detections to analyze what's risky about this user. |
| Generate findings and a risk summary | The agent generates findings based on the investigation, which includes a thorough risk summary explaining the suggestion and defining the key risk factors. |
| Generate a recommended remediation action | The agent suggests a remediation action, using the information gathered during the investigation. |
| Answer questions through chat | IT administrators ask the agent questions related to the risky users and the risk summary. |
| Store custom instructions in agent memory | Customers can give the agent custom instructions through agent chat, which the agent stores in its memory and applies for future runs. Currently, agent memory can store preferred remediation actions. |

### Using the agent

1. Sign in to the **Microsoft Entra admin center** as at least a Security Administrator.
2. Browse to **ID Protection** > **Risky users**.
3. Look for the banner at the top of the page.
4. Select **Start agent**

#### Configuring agent settings

With the **Risky users** page open, select the **Agent view**. Select the ellipses in the upper-right corner and then select Settings.

- **Controls** - provide the roles and permissions needed to run the agent.
- **Triggers** - set when and how the agent is run:
  - Continuous monitoring - checks for new risky users every 5 minutes
  - Daily trigger - agent runs once per day
  - Manual run - agent runs only when manually launched

- **Scope** - By default, the agent investigates the most recent 100 risky users within the last 90 days. You can control the scope of for agent scan by adjusting several options.
  - Select users and groups option to search for and select the users and groups you want the agent to scan.
  - Set the maximum recent risky users to scan within 1-100.
  - Select which risk levels to include in the scan. All risk levels are selected by default.
  - Set a specific time frame for the scope:
    - Last 7 days
    - Last 14 days
    - Last 30 days
    - Custom time frame up to 90 days

- **Communications** - enter a set of users to receive notifications of the agent run.
- **Memory** - list of user confirmed safe items that were false positives.

### Explore the agent findings report

#### Agent summary

An agent summary appears at the top of the Agent view, showing recent agent activities. This tile provides quick access to the Chat with agent feature and a Manage agent button, which lets you trigger a one-time run or open agent settings.

#### Agent suggestions

Agent suggestions are displayed below the agent summary. Hover over a suggestion to highlight impacted users in the table. Selecting a suggestion filters the table to show only those users for review. Each suggestion includes a bulk action button, so you can apply the action with one button.

Currently, the following remediation actions are available in agent suggestions:

- Dismiss risk
- Reset password

#### Risky users table with agent suggestions

The lower half of the report lists all risky users. Select a user to view agent findings, risk factors, and suggestions specific to that user. The Agent suggestion column also shows recommended remediation actions directly in the table. Select the action button to apply a remediation to individual users.

#### Risky user details

The Risky user details page provides a new Agent view, which presents agent findings specific to a risky user. This view includes the following information:

- **Basic user information**: Username, current risk level, and User Principal Name (UPN)
- **Agent findings**: The agent provides a verdict of Compromised or Not compromised based on its investigation
- **Risk summary**: A detailed explanation of the agent's findings, based on analysis of the user's sign-ins and behaviors
- **Risk factors**: Key risk indicators summarized for easy review
- **Suggested remediation action**: A call-to-action button that allows you to quickly start remediating the risk


## Module assessment

Choose the best response for each of the questions below.

### Check your knowledge


## Summary and resources

Now that you have reviewed this module, you should be able to:

- Review Identity Protection basics.
- Implement and manage a user risk policy.
- Implement and manage sign-in risk policies.
- Implement and manage multifactor authentication (MFA) registration policy.
- Monitor, investigate, and remediate elevated risky users.
- Explore Microsoft Defender for Identity

### Resources

Use these resources to discover more.

- [Enabling combined security information registration in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-registration-mfa-sspr-combined)
- [Manage emergency access accounts in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/security-emergency-access)
- [How To: Configure and enable risk policies](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-configure-risk-policies)
- [What are managed identities for Azure resources?](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview)
- [Remediate risks and unblock users](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-remediate-unblock)
- [Microsoft Entra Identity Protection notifications](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-configure-notifications)
- [Identity Protection policies](https://learn.microsoft.com/en-us/entra/id-protection/concept-identity-protection-policies)
- [What is Microsoft Defender for Identity](https://learn.microsoft.com/en-us/defender-for-identity/what-is)


---

# Implement access management for Azure resources

_https://learn.microsoft.com/en-us/training/modules/implement-access-management-for-azure-resources/_


## Introduction

This module will cover how to assign and manage access to resources in Azure using Azure roles. When you create a resource, you want to know that only specific access is granted to users and groups. Only allow users that need to access data or a resource, the permissions to do so. How can you control access? By assigning a role with the specific permissions needed. There are built-in Azure roles and you can create custom-roles as needed.

An application might also need to have permission to access data or other Azure resources. Learn how to set up managed identities, which allow the application to gain access to only resources you allow. You can give granular access to secrets, keys, and certificates stored in a key vault to your users and applications. You protect both the items stored in the key vault, and who can use them. And finally, you'll look at the new tool Microsoft Entra Permission Management. Learn to gather, review, and restrict the permission assigned across your cloud solutions.

#### Learning objectives

By the end of this module will be able to:

- Assign Azure roles and custom roles to access Azure resources.
- Create and manage application access with managed identities.
- Configure and manage access into Azure Key Vault.
- Retrieve object from a key vault securely.
- Explore the capabilities of Microsoft Entra Permissions Management.

#### Prerequisites

None


## Assign Azure roles

Azure role-based access control (Azure RBAC) is the authorization system you use to manage access to Azure resources. To grant access, you assign roles to users, groups, service principals, or managed identities at a particular scope. Primary steps to follow when assigning an Azure role:

1. Who needs access?
  - **User** - Only a single person is needed for the task. You can assign a role to users in other tenants.
  - **Group** - Use when you need to grant a set of users the same role.
  - **Service Principal** - Assign a role to a service principal when you want to grant an application access to an Azure resource.
  - **Managed Identity** - Use the managed identity when you want an application to manage credentials for authentication.

2. Select the right role. Use the built-in roles or create a custom role with the specific capabilities you need.

- Built-in Azure roles
  - Owner - full access to all resources.
  - Contributor - Can create and manage all types of Azure resources, but can't grant access.
  - Reader - Can view the available Azure resources.
  - User Access Administrator - Assign access to Azure resources.
  - Other task specific roles, like Virtual Machine Contributor, can be assigned.

1. Identify what level to assign the role (the Scope). Scope is the set of resources that the access applies to. In Azure, you can specify a scope at four levels: management group, subscription, resource group, and resource. Scopes are structured in a parent-child relationship. Each level of hierarchy makes the scope more specific. You can assign roles at any of these levels of scope. The level you select determines how widely the role is applied. Lower levels inherit role permissions from higher levels. Example:
  - If you assign the **Reader role** to a user at the **management group scope**, that user can read everything in all subscriptions in the management group.
  - If you assign the **Billing Reader role** to a group at the **subscription scope**, the members of that group can read billing data for every resource group and resource in the subscription.
  - If you assign the **Contributor role** to an application at the **resource group scope**, it can manage resources of all types in that resource group, but not other resource groups in the subscription. It's a best practice to grant security-principals the least privilege they need to perform their job. Avoid assigning broader roles at broader scopes even if it initially seems more convenient. By limiting roles and scopes, you limit what resources are at risk if the security-principal is ever compromised. For more information, see Understand scope.

2. Confirm the currently logged in user has the rights need to assign the Azure role.
3. Assign the role. Once you know the security-principal, role, and scope, you can assign the role. You can assign roles using the Azure portal, Azure PowerShell, Azure CLI, Azure SDKs, or REST APIs. You can have up to 4,000 role assignments in each subscription. This limit includes role assignments at the subscription, resource group, and resource scopes. You can have up to 500 role assignments in each management group.

#### Assign an Azure role from the portal

Whether you are in the User, Group, Resource Group, or Subscription you use the Access content (IAM) page to make the assign. The official name is identity and access management (IAM) and appears in several locations in the Azure portal.

#### Assign an Azure role with script

PowerShell using the Microsoft Graph PowerShell cmdlet

```
New-AzRoleAssignment -ObjectId <objectId> `
-RoleDefinitionName <roleName> `
-Scope /subscriptions/<subscriptionId>/resourcegroups/<resourceGroupName>/providers/<providerName>/<resourceType>/<resourceSubType>/<resourceName>
```

CLI scripting

```
az role assignment create --assignee "{assignee}" \
--role "{roleNameOrId}" \
--resource-group "{resourceGroupName}"
```


## Configure custom Azure roles

If the Azure built-in roles don't meet the specific needs of your organization, you can create your own Azure custom roles. Just like built-in roles, you can assign custom roles to users, groups, and service principals at management group (in preview only), subscription and resource group scopes. Custom roles are stored in a Microsoft Entra ID and can be shared across subscriptions. Each directory can have up to 5000 custom roles. Custom roles can be created using the Azure portal, Azure PowerShell, Azure CLI, or the REST API.

#### Create the custom role from the user interface

You would assign a custom role to a user, group, or other resource the same as you do for built-in. Your admin gets to control exactly with capabilities the custom role has access to. The principle of least privilege let's you pick just the capabilities you need. To create the custom role:

1. Open Microsoft Entra admin center.
2. From the **Identity** menu, Select **Roles and administration**.
3. Select **+ New custom role**.
4. Then name and assign the capabilities needed.

#### Create a custom role from a JSON template

You can use a JSON file to create a custom role. Here's a sample:

```
{
    "properties": {
        "roleName": "Billing Reader Plus",
        "description": "Read billing data and download invoices",
        "assignableScopes": [
            "/subscriptions/your-subscription-number"
        ],
        "permissions": [
            {
                "actions": [
                    "Microsoft.Authorization/*/read",
                    "Microsoft.Billing/*/read",
                    "Microsoft.Commerce/*/read",
                    "Microsoft.Consumption/*/read",
                    "Microsoft.Management/managementGroups/read",
                    "Microsoft.CostManagement/*/read",
                    "Microsoft.Support/*"
                ],
                "notActions": [],
                "dataActions": [],
                "notDataActions": []
            }
        ]
    }
}
```

The asterisk (`*`) is used as a wildcard. If you need to assign all of the **read** permissions from the **Billing** resource that use this command **Microsoft/Billing/*/read**. The wildcard can exist at any level.


## Create and configure managed identities

A common challenge when creating a cloud solution is the management of secrets, credentials, certificates, and keys. These secure elements are used to secure communication between services. Managed identities eliminate the need for developers to manage these credentials.

While developers can securely store the secrets in Azure Key Vault, services need a way to access Azure Key Vault. Managed identities provide an automatically managed identity in Microsoft Entra ID for applications to use when connecting to resources. The managed identity supports authentication via Microsoft Entra ID. Applications can use managed identities to obtain Microsoft Entra tokens without having to manage any credentials.

#### Benefits of using managed identities

- You don't need to manage credentials. Credentials aren’t even accessible to you.
- You can use managed identities to authenticate to any resource that supports Microsoft Entra authentication, including your own applications. Managed identities can be used without any extra cost.

#### Types of managed identity

| **Identity type** | **Description and usage** |
|---|---|
| System-assigned | Some Azure services allow you to enable a managed identity directly on a service instance. When you enable a system-assigned managed identity, an identity is created in Microsoft Entra ID. The identity is tied to the lifecycle of that service instance. When the resource is deleted, Azure automatically deletes the identity for you. By design, only that Azure resource can use this identity to request tokens from Microsoft Entra ID. |
| User-assigned | You might also create a managed identity as a standalone Azure resource. You can create a user-assigned managed identity and assign it to one or more instances of an Azure service. For user-assigned managed identities, the identity is managed separately from the resources that use it. |

Always remember that managed identities are assigned to an application. So, you need to configure and manage the identity within the services they're being used. If you have an application running in a virtual machine (Linux or Windows), then you add and configure the identity there. If you're using a managed identity with a cloud-app, function, or app service, then you configure and manage it there. Let's look at adding a managed identity to a cloud-built app using the App Service.

#### Managed identity in Azure portal for an App Service

The basic steps, to create and add an identity to your app, are:

1. Build your App.
2. Open the App in the Azure portal.
3. Select **Identity** from the menu then select either **System assigned** or **User assigned**.
4. Select the **+ Add** item and complete the wizard.

You can perform a similar action using script within the CLI, PowerShell, or with a template. Sample could look like:

**Using the CLI**

```
az webapp identity assign --resource-group <group-name> --name <app-name> --identities <identity-name>
```

Or using **PowerShell** with the AZ.ManagedServiceIdentity module installed

```
Update-AzFunctionApp -Name <app-name> -ResourceGroupName <group-name> -IdentityType UserAssigned -IdentityId $userAssignedIdentity.Id
```

Or within a **template**

```
"identity": {
    "type": "UserAssigned",
    "userAssignedIdentities": {
        "<RESOURCEID>": {}
    }
}
```

#### Value of managed identity

As stated at the beginning of this page, when you build an app, you need a method to grant it access to resources. To take advantage of the concepts of **zero trust** you can use managed identities. You only assign the minimum privileges that the managed identity needs. Then only assign access the minimum resources needed. Least-privilege will keep your applications and data protected.


## Access Azure resources with managed identities

Managed identities for Azure resources are a feature of Microsoft Entra ID. Each Azure service that supports managed-identities are subject to their own timeline. Make sure you review the availability status of managed identities for your resource and known issues before you begin. After you've configured an Azure resource with a managed identity, you can give the managed identity access to another resource.

#### Add access to other resources

After you've enabled managed identity on an Azure resource, such as an Azure App Service application or Azure virtual machine, you might need to grant access to more resources. Let's say you want add access to a storage account to your managed identity.

1. Sign in to the Azure portal using an account associated with the Azure subscription under which you've configured the managed identity.
2. Navigate to the desired resource on which you want to modify access control. In this example, we're giving an Azure virtual machine access to a storage account, so we navigate to the storage account.
3. Select Access control (IAM).
4. Select Add > Add role assignment to open the Add role assignment page.
5. Pick the Owner, Contributor, or Reader based on the least privilege rules for your applications needs.
6. Select the managed identity you want assigned.
7. Complete the assignment with the **Review + assign** option.


## Analyze Azure role permissions

What is a permission? The dictionary definition of permission is the **consent or authorization to perform a specific action**. In Microsoft Entra ID, you've permissions for each of the operations you're able to do. Permission can range from viewing your settings, to be able to change your setting. Then move on to granting permission to add or remove users and beyond. There are two primary places where permission can be assigned, at a user or group level. However, they all pass down to the user at the final point. When dealing with users, you've both a member-user and a guest-user. The default permissions for the guest-user are slightly less than the member.

#### What is a sample of the default permissions for users?

| **Member Users** | **Guest Users** |
|---|---|
| Enumerate list of users and their contacts | Read own properties |
| Invite guest users | Invite guest users |
| Can create Security and Microsoft 365 Groups | Can search for nonhidden groups by name |
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

You only want to grant the permissions a user needs. So be careful to know what all permissions are granted when you assign a role. You can see the list of permissions in the **Attribute definition reader**. To open it, launch Microsoft Entra ID, then open the **Roles and administrators** screen. Next select a role, and open its description page from the ellipsis (...) menu. Depending on the role you chose, you'll see a large number of permissions or possibly a small number. Two sets of permissions:

- Role permissions
- Guest and service principal basic read permissions


## Configure Azure Key Vault RBAC policies

You can grant access to Azure Key Vault using either role-based access control (RBAC) or using Key Vault access policies. Either method works to protect your secrets, certificates, and keys. Access policies give you a little more granular control, but can be harder to manage. Choose the best option based on your security posture needs.

#### Assign a Key Vault access policy

A Key Vault access policy determines whether a user, application, or group, can perform operations on Key Vault secrets, keys, and certificates. You can assign access policies using the Azure portal, the Azure CLI, or Azure PowerShell. Key vault supports up to 1024 access policy entries, with each entry granting a distinct set of permissions to a particular security principal. Because of this limitation, we recommend assigning access policies to groups of users, where possible, rather than individual users. Using groups makes it much easier to manage permissions for multiple people in your organization.

1. Open **Key Vault** in the Azure portal.
2. Select your key vault or create a new one.
3. From the menu select **Access policies**, then select **+ Add Access Policy**.
4. Use the dialog to assign the specific permission you want service principal to have.  Note Service principal represents the user, group, or application you're assigning the policy to.
5. Select **Add** to save and apply the access policy.

You can complete this activity using a saved template, PowerShell, CLI, and the Azure portal.

#### Assign a Key Vault access using Role-based access control (RBAC)

Azure RBAC allows users to manage Key, Secrets, and Certificates permissions. It provides one place to manage all permissions across all key vaults. The Azure RBAC model allows you to set permissions on different scope levels: management group, subscription, resource group, or individual resources. Azure RBAC for key vault also enables you to have separate permissions on individual keys, secrets, and certificates. Our recommendation is to use a vault per application per environment (Development, Pre-Production, and Production).

There are two actions required to use roles to access data within your Key Vault.

1. Enable role-based access control in your key vault.
2. Open key vault **Identity and Access (IAM)** from the menu. Then assign the role as you've done in other scenarios; like managed identity.

| **Built-in role** | **Description** |
|---|---|
| Key Vault Administrator | Perform all data plane operations on a key vault and all objects in it, including certificates, keys, and secrets. Can't manage key vault resources or manage role assignments. |
| Key Vault Certificates Officer | Perform any action on the certificates of a key vault, except manage permissions. |
| Key Vault Crypto Officer | Perform any action on the keys of a key vault, except manage permissions. |
| Key Vault Crypto Service Encryption User | Read metadata of keys and perform wrap/unwrap operations. |
| Key Vault Crypto User | Perform cryptographic operations using keys. |
| Key Vault Reader | Read metadata of key vaults and its certificates, keys, and secrets. Can't read sensitive values such as secret contents or key material. |
| Key Vault Secrets Officer | Perform any action on the secrets of a key vault, except manage permissions. |
| Key Vault Secrets User | Read secret contents. |


## Retrieve objects from Azure Key Vault

Azure Key Vault is a secure tool for storing secrets, keys, and certificate. Once stored, these items can be used by users and applications to perform actions and operations in a secure method. The process to retrieve any of these resources is common. So we'll look at how to review a secret from a key vault.

#### Add a secret to your key vault

To add a secret to the vault, follow the steps:

1. Navigate to your new key vault in the Azure portal
2. On the Key Vault settings pages, select **Secrets**.
3. Select on **Generate/Import**.
4. On the Create a secret screen choose the following values:    **Setting** **Value to enter**     Upload options Manual   Name mySC300keyvaultSecret   Value This is my secret
5. Select **Create**.

#### Retrieve a secret using the Azure portal

This process is simple. Open your key vault, then open the secret you created. Select the **Show secret value** button.

#### Retrieve a secret using CLI or PowerShell

You can quickly and easily grab a secret from your key vault using scripting languages.

**CLI**

```
az keyvault secret show --name "mySC300keyvaultSecret" --vault-name "<your-unique-keyvault-name>" --query "value"
```

***PowerShell***

```
$secret = Get-AzKeyVaultSecret -VaultName "<your-unique-keyvault-name>" -Name "mySC300keyvaultSecret" -AsPlainText
```

#### Retrieve a secret in an application

If you're building an application that needs access to your key vault secrets, certificates, and keys that can be done. You can access the key vault using .NET, Node.js, Python, and other languages.


## Knowledge check

Choose the best response for each of the questions below.

### Check your knowledge


## Summary and resources

When you create a resource, you want to know that only specific access is granted to users and groups. In this module you learned the different methods to assign and control access to Azure resources.

During this module you have learned to:

- Assign Azure roles and custom roles to access Azure resources.
- Create and manage application access with managed identities.
- Configure and manage access into Azure Key Vault.
- Retrieve object from a key vault securely.
- Explore the capabilities of Microsoft Entra Permissions Management.

### To learn more, research using these links

- [Assign Azure roles using the Azure portal - Azure RBAC](https://learn.microsoft.com/en-us/azure/role-based-access-control/role-assignments-steps)
- [Create or update Azure custom roles using the Azure portal - Azure RBAC](https://learn.microsoft.com/en-us/azure/role-based-access-control/custom-roles)
- [Configure managed identities using the Azure portal - Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/)
- [Assign a managed identity access to a resource using the Azure portal - Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/how-to-assign-access-azure-resource?pivots=identity-mi-access-cli)
- [Understand Azure role definitions - Azure RBAC](https://learn.microsoft.com/en-us/azure/role-based-access-control/role-definitions)
- [Grant permission to applications to access an Azure key vault using Azure RBAC](https://learn.microsoft.com/en-us/azure/key-vault/general/assign-access-policy)
- [Create and access a secret in Azure Key Vault](https://learn.microsoft.com/en-us/azure/key-vault/secrets/quick-create-portal)


---

# Deploy and Configure Microsoft Entra Global Secure Access

_https://learn.microsoft.com/en-us/training/modules/deploy-configure-microsoft-entra-global-secure-access/_


## Introduction

The modern workforce transitioned from traditional office settings to working from nearly anywhere. The transition in working location necessitates an identity-aware, cloud-delivered network perimeter. This identity-aware perimeter is known as Security Service Edge (SSE). The Microsoft SSE solution includes Microsoft Entra Internet Access and Microsoft Entra Private Access, collectively referred to as Global Secure Access. This solution is founded on Zero Trust principles, emphasizing least privilege, explicit verification, and an assumption of breach to ensure security in the cloud era.

Scenario: Imagine your company has a sales representative working remotely from a coffee shop. The sales rep needs to access sensitive customer data stored in the company's cloud services. To ensure secure access, the representative would use Microsoft Security Service Edge (SSE) solution. In this case Microsoft Entra Private Access. The sales rep securely connects to the company's network, authenticates their identity, and accesses the required data. Access happens without exposing data to the public internet; all while adhering to the Zero Trust principles of least privilege and explicit verification.

In this module, you learn how to implement Microsoft Entra Private and Microsoft Entra Internet Access using Azure and Microsoft Entra.


## Explore Global Secure Access

![Diagram of the high level process flow for Global Secure Access in Microsoft Entra. Microsoft Entra Private Access and Internet Access are the gateways to resources.](https://learn.microsoft.com../../wwl-sci/deploy-configure-microsoft-entra-global-secure-access/media/global-secure-access-diagram.png)

### Microsoft Security Service Edge (SSE) solution

Microsoft Entra Internet Access and Microsoft Entra Private Access is a solution that merges network, identity, and endpoint access controls so you can securely access any app or resource, from anywhere. You can enable access orchestration for employees, business partners, and digital workloads. With existing functionality in Microsoft Entra, continuously monitor and adjust user access in real time if permissions or risk level changes. The Global Secure Access uses a unified portal to streamline the roll-out and management of the access control capabilities. Access is delivered from the Microsoft Wide Area Network across its global network of regions and edge locations. This private network enables organizations to connect users and devices to public and private resources seamlessly and securely.

### Microsoft Entra Internet Access

Microsoft Entra Internet Access secures access to Microsoft services, SaaS, and public internet apps while protecting users, devices, and data against internet threats. Secure access to public internet apps through the identity-centric, device-aware, cloud-delivered Secure Web Gateway (SWG) of Microsoft Entra Internet Access.

#### Key features

- Prevent stolen token replay attacks with compliant network checks in Conditional Access.
- Apply universal tenant restrictions to prevent data exfiltration.
- Enriched logs with network and device signals.
- Improve the precision of risk assessments on users, locations, and devices.
- Acquire network traffic from the desktop client or from a remote network.
- Dedicated public internet traffic forwarding profile.
- Protect user access to the public internet while using Microsoft Secure Web Gateway (SWG).
- Regulate access to websites based on their content categories and domain names.
- Apply universal Conditional Access policies for all internet destinations.

### Microsoft Entra Private Access

Microsoft Entra Private Access provides your users secure access to your private, corporate resources. Microsoft Entra Private Access builds on the capabilities of Microsoft Entra application proxy and extends access to any private resource, port, and protocol. Remote users connect to private apps across hybrid and multicloud environments, private networks, and data centers from any device and network without requiring a VPN. The service offers per-app adaptive access based on Conditional Access policies.

#### Key features

- Zero Trust based access to a range of IP addresses and/or Fully Qualified Domain Names (FQDNs) without requiring a legacy VPN.
- Modernize legacy app authentication with Conditional Access.
- Provide a seamless end-user experience by deploying side-by-side with your existing non-Microsoft SSE solutions.

### Before you begin

Licensing:

- Microsoft Entra ID P1 or P2 license
- Microsoft Entra Internet Access license and/or Microsoft Entra Private Access license

Roles:

- Global Secure Access Administrator role assigned to at least one administrator.

It's recommended that you visit the [Zero Trust Guidance Center](https://learn.microsoft.com/en-us/security/zero-trust/) to plan out your implementation. Additionally, you can make all configuration changes in the Microsoft Entra admin center at [https://entra.microsoft.com](https://entra.microsoft.com).


## Deploy and configure Microsoft Entra Internet Access

There are four main steps for getting Microsoft Entra Internet Access deployed within your company. After you complete these four steps, users with the Global Secure Access client installed on their Windows device can securely access Microsoft resources from anywhere. Conditional Access policies for Microsoft traffic are only enforced when the user has the Global Secure Access client. Microsoft traffic is accessible through remote network connectivity without the Global Secure Access client, but the Conditional Access policy isn't enforced in that path.

##### Steps

| Steps | Description |
|---|---|
| 1. Enable the Microsoft traffic forwarding profile. | With the Microsoft profile enabled, Microsoft Entra Internet Access acquires the traffic going to Microsoft services, like Exchange Online and SharePoint Online. |
| 2. Install the Global Secure Access Client on end-user devices. | Download and install the client app to capture and control access from the client. |
| 3. Enable tenant restrictions. | Configure which tenants / organizations are allowed or blocked |
| 4. Enable enhanced Global Secure Access signaling and Conditional Access. | Use Conditional Access and Global Secure Access to prevent attacks. |

### Enable Microsoft traffic forwarding profile

1. Sign in to the Microsoft Entra admin center as a Global Secure Access Administrator.
2. Browse to Global Secure Access > Connect > Traffic forwarding.
3. Enable the Microsoft traffic profile.

Turns on Microsoft traffic forwarding and creates the following configurations in Microsoft Entra:

| Configuration Setup | Description |
|---|---|
| Policies (network routing) | 1. **Exchange Online**, 2. **SharePoint Online and OneDrive for Business**, and 3. **Entra ID and MSGraph** - These use fully qualified domain names or IP subnets to manage network traffic. |
| Conditional Access Policy | **Linked Conditional Access policies** - Captures all traffic to Microsoft Services, routes to the network policies defined earlier if conditions are met. |
| User and Group | Specify specific users or groups that this traffic forward applies to. |

For more information, refer to [Enable and manage Microsoft traffic forwarding](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-manage-microsoft-profile).

### Deploy Global Secure Access client for Windows (or Android)

The client is quick and easy to install. It can be deployed via mobile device management tools like Microsoft Intune, or manually installed on each device. You need to download the client from the Microsoft Entra admin center, then use your choice of deployment methods.

##### Download the client

1. Sign in to the Microsoft Entra admin center as a Global Secure Access Administrator.
2. Browse to Global Secure Access > Connect > Client download.
3. Select Download Client.

##### Install the client

1. Copy the Global Secure Access client setup file to your client machine.
2. Run the GlobalSecureAccessClient.exe setup file. Accept the software license terms.
3. The client is installed and users are prompted to sign in with their Microsoft Entra credentials.
4. Users sign in and the connection icon turns green. Double-clicking on the connection icon opens a notification with client information showing a connected state.

You can install the Android client instead using either Microsoft Intune or Microsoft Defender for Endpoint on Android. The process is similar, but you get the client app from the Android store.

### Configure the Tenant Restrictions

Administrators use tenant restrictions to control user access to external tenants on their network. Tenant restrictions, with cross tenant access settings, add tenant-level restrictions and more granularity such as individual user, group, and application controls. Tenant restrictions move policy management from network proxies to a cloud-based portal. Allow internal identities, such as employees, to access specific external tenants on your managed network. Block access to nonallowed tenants for internal identities. Block external identities, such as contractors and vendors, from accessing all external tenants.

##### Set up Tenant Restrictions

1. Sign in to the Microsoft Entra admin center as at least a Security Administrator.
2. Browse to Identity > External Identities > Cross-tenant access settings, then select Organizational settings.
3. Select **Add organization**.
4. On the **Add organization** pane, type the full domain name (or tenant ID) for the organization.
5. Select the organization in the search results, and then select Add. The organization appears in the Organizational settings list. At this point, all access settings for this organization are inherited from your default settings. To change the settings for this organization, select the Inherited from default link under the Inbound access or Outbound access column.
6. Modify the organization's settings.

##### Enable Global Secure Access

Once you created the tenant restriction policies, you can utilize Global Secure Access to apply tagging for tenant restrictions. An administrator with both the Global Secure Access Administrator and Security Administrator roles must take the following steps to enable enforcement with Global Secure Access.

1. Sign in to the Microsoft Entra admin center as a Global Secure Access Administrator.
2. Browse to Global Secure Access > Global Settings > Session Management > Tenant Restrictions.
3. Select the toggle to Enable tagging to enforce tenant restrictions on your network.
4. Select Save.

##### How it works

![Diagram of the process flow of how tenant restrictions work. Request comes in from a tenant. The tenant is compared to the restriction policy.](https://learn.microsoft.com../../wwl-sci/deploy-configure-microsoft-entra-global-secure-access/media/tenant-restrictions-flow.png)

| Steps | Description |
|---|---|
| 1. | Contoso configures a **tenant restrictions v2** policy in their cross-tenant access settings to block all external accounts and external apps. Contoso enforces the policy using Global Secure Access universal tenant restrictions. |
| 2. | A user with a Contoso-managed device tries to access a Microsoft Entra integrated app with an unsanctioned external identity. |
| 3. | Authentication plane protection: Microsoft Entra ID, with Contoso's policy, blocks unsanctioned external accounts from accessing external tenants. |
| 4. | Data plane protection: With universal tenant restrictions v2 through Global Secure Access, data plane protection covers Microsoft Graph. If the user tries to reuse an infiltrated Microsoft Entra ID-issued token to access Microsoft Graph, the request is blocked. For SharePoint Online, any attempt at anonymously accessing resources is also blocked. Data plane protection for third-party apps such as Slack isn't in scope. |

### Enable enhanced Global Secure Access signaling and Conditional Access

Organizations who use Conditional Access along with the Global Secure Access, can prevent malicious access to Microsoft apps, SaaS apps, and private line-of-business (LoB) apps. You can configure multiple conditions to provide defense-in-depth. These conditions might include device compliance, location, and more to provide protection against user identity or token theft. Global Secure Access introduces the concept of a compliant network within Conditional Access. This compliant network check ensures users connect from a verified network connectivity.

The Global Secure Access Client installed on devices or users behind configured remote networks allows administrators to secure resources behind a compliant network with advanced Conditional Access controls. This compliant network feature makes it easier for administrators to manage and maintain, without having to maintain a list of all of an organization's locations IP addresses. Administrators don't need to push traffic through their organization's VPN egress points to ensure security. Continuous Access Evaluation (CAE) with the compliant network feature is currently supported for SharePoint Online. With CAE, you can enforce defense-in-depth with token theft replay protection.

##### Enable Global Secure Access signaling

1. Sign in to the Microsoft Entra admin center as a Global Secure Access Administrator.
2. Browse to Global Secure Access > Global settings > Session management > Adaptive access.
3. Select the toggle to Enable Global Secure Access signaling in Conditional Access.
4. Browse to Protection > Conditional Access > Named locations. Confirm you have a location called All Compliant Network locations with location type Network Access. Organizations can optionally mark this location as trusted.

##### Build your Conditional Access policy for networks

1. Sign in to the Microsoft Entra admin center as at least a Conditional Access Administrator.
2. Browse to Protection > Conditional Access.
3. Select Create new policy.
4. Give your policy a name. We recommend that organizations create a meaningful standard for the names of their policies.
5. Under Assignments, select Users or workload identities.
  - Under Include, select All users.
  - Under Exclude, select Users and groups and choose your organization's emergency access or break-glass accounts.

6. Review Target resources > Include, and select Select apps.
  - Choose Office 365 Exchange Online, and/or Office 365 SharePoint Online, and/or any of your SaaS apps.
  - The specific Office 365 cloud app in the app picker is currently NOT supported, so don't select this cloud app.

7. Review the Conditions > Location.
  - Set Configure to Yes.
  - Under Include, select Any location.
  - Under Exclude, select Selected locations.
    - Select the All Compliant Network locations.

  - Choose Select.

8. Explore Access controls:
  - Grant, select Block Access, and select Select.

9. Confirm your settings and set Enable policy to On.
10. Select the Create button to create to enable your policy.


## Deploy and configure Microsoft Entra Private Access

Similar to configuring Microsoft Entra Internet Access, there are four main steps for getting Microsoft Entra Private Access deployed within your company. After you complete these four steps, users with the Global Secure Access client installed on a Windows device can connect to your primary resources, through a Quick Access app, and private network connector.

##### Steps

| Steps | Description |
|---|---|
| 1. Configure a Microsoft Entra private network connector and connector group. | Create connection between an on-premises server and Global Secure Access. |
| 2. Configure Quick Access to your private resources. | Define specific fully qualified domain names (FQDNs) or IP addresses of private resources to include in Microsoft Entra Private Access. |
| 3. Enable the Private Access traffic forwarding profile. | Turn on Private Access and link from on-premises router to remote networks. |
| 4. Install and configure the Global Secure Access Client on end-user devices. | Deploy the client software onto devices, so they can access the traffic flow. |

### Configure a Microsoft Entra private network connector and connector groups

Connectors are lightweight agents that sit on a server in a private network and facilitate the outbound connection to the Global Secure Access service. Connectors must be installed on a Windows Server that has access to the backend resources and applications. You can organize connectors into connector groups, with each group handling traffic to specific applications.

##### Configuring the Windows Server for connectors

The Microsoft Entra private network connector requires a server running Windows Server 2016 or later. You install the private network connector on the server. This connector server needs to connect to the Microsoft Entra Private Access service and application proxy service and the private resources or applications that you plan to publish.

- For high availability in your environment, we recommend having more than one Windows server.
- The minimum .NET version required for the connector is v4.7.2+.
- Require Transport Layer Security (TLS) 1.2 be enabled on Windows Server.

Open ports for **outbound**

| Port number | What the port is used for |
|---|---|
| 80 | Downloading certificate revocation lists (CRLs) while validating the TLS/SSL certificate |
| 443 | All outbound communication with the Application Proxy service |

Allow access to some URLs

| URL | Port | What the port is used for |
|---|---|---|
| `site`.msappproxy.net, and `site`.servicebus.windows.net | 443/HTTPS | Communication between the connector and the Application Proxy cloud service |
| crl3.digicert.com, crl4.digicert.com, ocsp.digicert.com, crl.microsoft.com, oneocsp.microsoft.com, and ocsp.msocsp.com | 80/HTTP | The connector uses these URLs to verify certificates. |
| login.windows.net, secure.aadcdn.microsoftonline-p.com, `site`.microsoftonline.com, `site`.microsoftonline-p.com, `site`.msauth.net, `site`.msauthimages.net, `site`.msecnd.net, `site`.msftauth.net, `site`.msftauthimages.net, `site`.phonefactor.net, enterpriseregistration.windows.net, management.azure.com, policykeyservice.dc.ad.msft.net, ctldl.windowsupdate.com, and [www.microsoft.com/pkiops](https://www.microsoft.com/pkiops) | 443/HTTPS | The connector uses these URLs during the registration process. |
| ctldl.windowsupdate.com, and [www.microsoft.com/pkiops](https://www.microsoft.com/pkiops) | 80/HTTP | The connector uses these URLs during the registration process. |

##### Install the connector using Microsoft Entra

1. Sign in to the Microsoft Entra admin center as a Global Administrator of the directory that uses Application Proxy.
2. Select your username in the upper-right corner. Verify sign-in to a directory that uses Application Proxy. If you need to change directories, select Switch directory and choose a directory that uses Application Proxy.
3. Browse to Global Secure Access > Connect > Connectors.
4. Select Download connector service.
5. Read the Terms of Service. When ready, select Accept terms & Download.
6. Install the connector using the Run option at the bottom of the screen.
7. Install the service by following the instructions in the wizard. When prompted to register the connector with the Application Proxy for your Microsoft Entra tenant, provide your Global Administrator credentials.

##### Verify the connector installed

On Windows Server:

1. Select the Windows key and enter services.msc to open the Windows Services Manager.
2. Check to see if the status for the following services is Running.
  - Microsoft Entra private network connector enables connectivity.
  - Microsoft Entra private network connector Updater is an automated update service.
  - The updater checks for new versions of the connector and updates the connector as needed.

3. If the status for the services isn't Running, right-click to select each service and choose Start.

In Microsoft Entra:

1. Sign in to the Microsoft Entra admin center as a Global Administrator of the directory that uses Application Proxy.
2. Browse to Global Secure Access > Connect > Connectors.
  - All of your connectors and connector groups appear on this page.

3. Verify the details by viewing the connector.
  - Expand the connector to view the details.
  - An active green label indicates that your connector can connect to the service. However, even though the label is green, a network issue could still block the connector from receiving messages.

##### Create groups of connectors

1. For quicker assignments, you can group different connectors together.
2. Browse to Global Secure Access > Connect > Connectors.
3. Select New connector group.
4. Give your new connector group a name, then use the dropdown menu to select which connectors belong in this group.
5. Select Save.

### Configure Quick Access for Global Secure Access

With Global Secure Access, you can define specific fully qualified domain names (FQDNs) or IP addresses of private resources to include in the traffic for Microsoft Entra Private Access. Your organization's employees can then access the apps and sites that you specify. Explore how to configure Quick Access for Microsoft Entra Private Access.

##### Set up Quick Access name and connector group

On the Quick Access page, you provide a name for the Quick Access app, select a connector group, and add application segments, which include FQDNs and IP addresses. You can complete all three steps at the same time, or you can add the application segments after the initial setup is complete.

1. Sign in to the Microsoft Entra admin center with the appropriate roles.
2. Browse to Global Secure Access > Applications > Quick access.
3. Enter a name. We recommend using the name Quick Access.
4. Select a Connector group from the dropdown menu. Existing connector groups appear in the dropdown menu.
  - Created in the previous step.

5. Select the Save button at the bottom of the page to create your "Quick Access" app without FQDNs and IP addresses.

##### Add an application segment

The **Add Quick Access** application segment portion of this process is where you define the FQDNs and IP addresses that you want to include in the traffic for Microsoft Entra Private Access. You can add these resources when you create the Quick Access app or return to add more or edit them later.

1. Sign in to the Microsoft Entra admin center.
2. Browse to Global Secure Access > Applications > Quick Access.
3. Select **Add Quick Access** application segment.
4. In the **Create application segment** panel, select a Destination type.
5. Enter the appropriate details for the selected destination type. Depending on what you select, the subsequent fields change accordingly.
  - IP address:
    - Internet Protocol version 4 (IPv4) address, such as 192.0.2.1, that identifies a device on the network.
    - Provide the ports that you want to include.

  - Fully qualified domain name (including wildcard FQDNs):
    - Domain name that specifies the exact location of a computer or a host in the Domain Name System (DNS).
    - Provide the ports to include.
    - NetBIOS isn't supported. For example, use contoso.local/app1 instead of contoso/app1.

  - IP address range (CIDR):
    - Classless Inter-Domain Routing (CIDR) represents a range of IP addresses. An IP address is followed by a suffix indicating the number of network bits in the subnet mask.
    - For example, 192.0.2.0/24 indicates that the first 24 bits of the IP address represent the network address, while the remaining 8 bits represents the host address.
    - Provide the starting address, network mask, and ports.

  - IP address range (IP to IP):
    - Range of IP addresses from start IP (such as 192.0.2.1) to end IP (such as 192.0.2.10).
    - Provide the IP address start, end, and ports.

  - Enter the ports and select the Apply button.  The following table provides the most commonly used ports and their associated networking protocols:    Port Protocol     22 Secure Shell (SSH)   80 Hypertext Transfer Protocol (HTTP)   443 Hypertext Transfer Protocol Secure (HTTPS)   445 Server Message Blocks (SMB) file sharing   3389 Remote Desktop Protocol (RDP)
    - Separate multiple ports with a comma.
    - Specify port ranges with a hyphen.
    - Spaces between values are removed when you apply the changes.
    - For example, 400-500, 80, 443.

6. Select the Save button when finished.

##### Assign users and groups for Quick Access

1. Sign in to the Microsoft Entra admin center.
2. Browse to Global Secure Access > Applications > Quick Access.
3. Select the Edit application settings button from Quick Access.
4. Select Users and groups from the side menu.
5. Add users and groups as needed.

You can enable specific Conditional Access policies as needed.

### Enable Traffic forwarding - Microsoft Entra Private Access

Now that you have your Quick Access app configured, your private resources added, users assigned to the app, you can enable the Private access profile from the Traffic forwarding area of Global Secure Access.

The Private Access traffic forwarding profile routes traffic to your private network through the Global Secure Access Client. Enabling this traffic forwarding profile allows remote workers to connect to internal resources without a VPN. With the features of Microsoft Entra Private Access, you can control which private resources to tunnel through the service and apply Conditional Access policies to secure access to those services. Once your configurations are in place, you can view and manage all of those configurations from one place.

1. Sign in to the Microsoft Entra admin center.
2. Browse to Global Secure Access > Connect > Traffic forwarding.
3. Select the checkbox for Private access profile.

### Deploy Global Secure Access client for Windows (or Android)

The client is quick and easy to install. It can be deployed via mobile device management tools like Microsoft Intune, or manually installed on each device. You need to download the client from the Microsoft Entra admin center, then use your choice of deployment methods.

##### Download the client

1. Sign in to the Microsoft Entra admin center as a Global Secure Access Administrator.
2. Browse to Global Secure Access > Connect > Client download.
3. Select Download Client.

##### Install the client

1. Copy the Global Secure Access client setup file to your client machine.
2. Run the GlobalSecureAccessClient.exe setup file. Accept the software license terms.
3. The client is installed and users are prompted to sign in with their Microsoft Entra credentials.
4. Users sign in and the connection icon turns green. Double-clicking on the connection icon opens a notification with client information showing a connected state.

You can install the Android client instead using either Microsoft Intune or Microsoft Defender for Endpoint on Android. The process is similar, but you get the client app from the Android store.


## Explore how to use the Dashboard to drive Global Secure Access

To access the dashboard:

1. Sign in to the Microsoft Entra admin center as a Global Secure Access Administrator.
2. Browse to Global Secure Access > Dashboard.

The Global Secure Access dashboard provides you with visualizations of the network traffic acquired by the Microsoft Entra Private and Microsoft Entra Internet Access services. The dashboard aggregates data from your network configurations, including devices, users, and tenants. The dashboard uses several widgets that provide you with visibility into several different types of data:

- Volume of devices using the Global Secure Access client
- Changes in the number of active devices
- Alerts and important notifications
- Service usage patterns
- Most used destinations
- Unique users accessing the network across all your tenants
- Most popular website categories
- Most used private application segments

### Global Secure Access snapshot

This widget provides a summary of how many users and devices are using the service and how many applications were secured through the service.

- Users: The number of distinct users seen in the last 24 hours. The data uses the user principal name (UPN).
- Devices: The number of distinct devices seen in the last 24 hours. The data uses the device ID.
- Workloads: The number of distinct destinations seen in the last 24 hours. The data uses fully qualified domain names (FQDNs) and IP addresses. The Global Secure Access snapshot has a filter to show data by Internet Access, Private Access, or Microsoft traffic.

### Alerts and notifications (preview)

This widget shows network activity and helps identify suspicious activities or trends identified by the network data. Common alerts are:

- Unhealthy remote network: An unhealthy remote network has one or more device-links disconnected.
- Increased external tenants activity: The number of users accessing external tenants increased.
- Token and device inconsistency: The original token is used on a different device.
- Web content blocked: Access to the website is blocked. Navigate to a related alert detail page with additional information.

### Usage profiling (preview)

The Usage profiling widget displays usage patterns over a selected period of time. Select the Display by filter to view the following usage categories:

- Transactions
- Users
- Devices
- Bytes sent
- Bytes received

### Top used destinations

The top-visited destinations widget shows all types of traffic and sorts by the number of transactions. You can select a different traffic type to narrow down the results. There are several filters available:

- Transactions: The destinations with the highest number of transactions, showing the total number of transactions in the last 24 hours.
- Users: The destinations most used by users, showing the number of distinct users (UPN) accessing the destination in the last 24 hours.
- Devices: The destinations most used by devices, showing the number of distinct device IDs accessing the destination in the last 24 hours.
- Bytes sent: The destinations (IP address) with the highest number of bytes sent, showing the total number of bytes sent in the last 24 hours.
- Bytes received: The destinations (IP address) with the highest number of bytes received, showing the total number of bytes received in the last 24 hours. Select the View all destinations button to see more details about the destinations.

### Cross-tenant access

Global Secure Access provides visibility into the number of users and devices that are accessing other tenants. This widget displays the following information:

- Sign-ins: The number of sign-ins through Microsoft Entra ID to Microsoft services in the last 24 hours. This widget provides you with information about the activity in your tenant.
- Total distinct tenants: The number of distinct tenant IDs seen in the last 24 hours.
- Unseen tenants: The number of distinct tenant IDs that were seen in the last 24 hours, but not in the previous seven days.
- Users: The number of distinct user sign-ins to other tenants in the last 24 hours.
- Devices: The number of distinct devices that signed in to other tenants in the last 24 hours. Select the **Configure tenant restrictions** button to navigate to the Session management area of Global Secure Access, where you can check the settings of your tenant restrictions.

### Web category filtering

The Web category filtering widget displays the top categories of web content that are blocked or allowed. These categories can be used to determine what sites or categories of sites you might want to block. Sort the results using the following categories:

- Transactions: Shows the total number of transactions in the last 24 hours.
- Users: The number of distinct users (UPN) accessing the destination in the last 24 hours.
- Devices: The number of distinct device IDs accessing the destination in the last 24 hours. Select View all web categories to view more details about your network traffic.

### Device status

The Device status widgets display the active and inactive devices that you deployed.

- Active devices: The number of distinct device IDs seen in the last 24 hours and the % change during that time.
- Inactive devices: The number of distinct device IDs that were seen in the last seven days, but not during the last 24 hours. The % change during the last 24 hours is also displayed.


## Create remote networks for use with Global Secure Access

Remote networks are remote locations, such as a branch office, or networks that require internet connectivity. Setting up remote networks connects your users in remote locations to Global Secure Access. Once a remote network is configured, you can assign a traffic forwarding profile to manage your corporate network traffic. Global Secure Access provides remote network connectivity so you can apply network security policies to your outbound traffic.

There are multiple ways to connect remote networks to Global Secure Access. In a nutshell, you're creating an Internet Protocol Security (IPSec) tunnel between a core router, known as the customer premises equipment (CPE), at your remote network and the nearest Global Secure Access endpoint. All internet-bound traffic is routed through the core router of the remote network for security policy evaluation in the cloud. Installation of a client isn't required on individual devices.

There are five primary steps to configure a Remote Network. In this process, you're building a bridge from an on-premises router in your office to Global Secure Access. These steps can be performed in Microsoft Entra admin center or via the Microsoft Graph API. Note the final step is performed on the on-premises router.

| Steps | Description |
|---|---|
| Basics | Define the name of your remote network and the region where you want to connect. |
| Connectivity | Enter the data about your on-premises router, where the signal comes from. |
| Traffic Forwarding | Add a traffic forwarding profile to define the type traffic network traffic to allow through. |
| Review Configuration | In this step, you confirm the setup of the remote network and gather settings you need to configure in the on-premises router. |
| Setup on-premises router | Use the management console of your on-premises router to enter the Microsoft connectivity settings from the previous step. |

### Configure - Basics

1. Sign in to the Microsoft Entra admin center as a Global Secure Access Administrator.
2. Browse to Global Secure Access > Connect > Remote networks.
3. Basics tab - Select the Create remote network button and provide the details.    Values requested     Name   Region

### Set up - Connectivity

1. Select **Next: Connectivity**.    Values requested     Name   Device type - usually a router   IP address of the device   Type of redundancy to enable   Bandwidth

### Enable - Traffic forwarding profiles

1. Select **Next** to open the Traffic forwarding setup.
  - You can create a new traffic forwarding profile, or select one created during Microsoft Entra Private Access or Microsoft Entra Internet Access.

### Complete configuration - Set up your on-premises router

All your remote networks appear on the Remote network page. Select the View configuration link in the Connectivity details column. These details contain the connectivity information from the Microsoft side of the bidirectional communication channel that you use to set up your CPE.

With the Microsoft connection data, it's time to update the on-premises router configuration. This step is performed in the management console of your CPE, not in Microsoft Entra admin center. Until you complete this step, your IPsec isn't set up. IPsec is a bidirectional communication. Internet Key Exchange (IKE) negotiations happen between two parties before the tunnel is successfully set up. So, don't miss this step.


## Use Conditional Access with Global Secure Access

After deploying your Global Secure Access, you can use Conditional Access to add more layers of security and protection. Organizations who use Conditional Access along with the Global Secure Access, can prevent malicious access to Microsoft apps, SaaS apps, and private line-of-business (LoB) apps using multiple conditions to provide defense-in-depth. These conditions might include device compliance, location, and more to provide protection against user identity or token theft.

There are several new types of checks introduced into Conditional Access with Global Secure Access:

| Conditional Access check | What it does |
|---|---|
| Compliant network check | This compliant network check ensures users connect from a verified network connectivity model for their specific tenant and are compliant with security policies enforced by administrators. |
| Private Access apps | Applying Conditional Access policies to your Microsoft Entra Private Access apps is a powerful way to enforce security policies for your internal, private resources. |
| Source IP restoration | With a cloud based network proxy between users and their resources, the IP address that the resources see doesn't match the actual source IP address. Source IP restoration in Global Secure Access allows backward compatibility for Microsoft Entra customers to continue using original user Source IP. |

To use the **Compliant network check** and the **Source IP restoration** capabilities, you need to have **Global Secure Access signaling for Conditional Access** enabled. This step only has to be performed once, before we go into the direct Conditional Access options. You perform this step before using any of the below features in Conditional Access.

### Enable Global Secure Access signaling for Conditional Access

To enable the required setting to allow the compliant network check, an administrator must take the following steps.

1. Sign in to the Microsoft Entra admin center as a Global Secure Access Administrator.
2. Browse to Global Secure Access > Global settings > Session management > Adaptive access.
3. Select the toggle to Enable CA Signaling for Microsoft Entra ID (covering all cloud apps). Continuous Access Evaluation (CAE) signaling is automatically enabled for Office 365 (preview).
4. Browse to Protection > Conditional Access > Named locations.
  - Confirm you have a location called All Compliant Network locations with location type Network Access. Organizations can optionally mark this location as trusted.

### Compliant Network Check

Compliant network enforcement happens at authentication plane and at the data plane (preview). Microsoft Entra ID performs Authentication plane enforcement at the time of user authentication. Data plane enforcement works with services that support Continuous Access Evaluation (CAE). Currently only Exchange Online and SharePoint Online support this capability. With CAE, you can enforce defense-in-depth with token theft replay protection.

Using this check you can ensure that other organizations using Microsoft's Global Secure Access services can't access your resources. For example: Contoso can protect their services like Exchange Online and SharePoint Online behind their compliant network check to ensure only Contoso users can access these resources. If another organization like Fabrikam was using a compliant network check, they wouldn't pass Contoso's compliant network check.

##### Protect your resources behind the compliant network

The compliant network Conditional Access policy can be used to protect your Microsoft and other applications. A typical policy will 'Block' access for all network locations except Compliant Network.

1. Sign in to the Microsoft Entra admin center as at least a Conditional Access Administrator.
2. Browse to Protection > Conditional Access.
3. Select Create new policy.
4. Give your policy a name. We recommend that organizations create a meaningful standard for the names of their policies.
5. Under Assignments, select Users or workload identities.
  - Under Include, select All users.
  - Under Exclude, select Users and groups and choose your organization's emergency access or break-glass accounts.

6. Under Target resources > Include, and choose Select apps.
  - Choose Office 365 Exchange Online, and/or Office 365 SharePoint Online, and/or any of your SaaS apps.
  - The specific Office 365 cloud app in the app picker is currently NOT supported, so don't select this cloud app.

7. Under Conditions > Location.
  - Set Configure to Yes.
  - Under Include, select Any location.
  - Under Exclude, choose Selected locations.
    - Select the All Compliant Network locations.

  - Choose Select.

8. Under Access controls:
  - Grant, select Block Access, and choose Select.

9. Confirm your settings and set Enable policy to On.
10. Select the Create button to create to enable your policy.

### Conditional Access for Private Access apps

You can create a Conditional Access policy for your Quick Access or Private Access apps from Global Secure Access. Starting the process from Global Secure Access automatically adds the selected app as the Target resource for the policy. All you need to do is configure the policy settings.

1. Sign in to the Microsoft Entra admin center as at least a Conditional Access Administrator.
2. Browse to Global Secure Access > Applications > Enterprise applications.
3. Select an application from the list.
4. Select Conditional Access from the side menu. Any existing Conditional Access policies appear in a list.
5. Select Create new policy. The selected app appears in the Target resources details.
6. Configure the conditions, access controls, and assign users and groups as needed.

You see the addition of the Quick Access and Private Access selector from Global Secure Access.

### Source IP Restoration

Source IP restoration in Global Secure Access allows backward compatibility for Microsoft Entra customers to continue using original user Source IP. Administrators can benefit from the following capabilities:

- Continue to enforce Source IP-based location policies across both Conditional Access and continuous access evaluation.
- Identity Protection risk detections get a consistent view of original user Source IP address for assessing various risk scores.
- Original user Source IP is also made available in Microsoft Entra sign-in logs.

##### Known limitations

- When source IP restoration is enabled, you can only see the source IP. The IP address of the Global Secure Access service isn't visible.
- Source IP restoration is currently supported for only Microsoft traffic, like SharePoint Online, Exchange Online, Teams, and Microsoft Graph.
- With CAE’s strict location enforcement, users are blocked despite being in a trusted IP range.

##### Enabling

Source IP Restoration is enabled when you turn on **Global Secure Access signaling**. Further configuration and changes shouldn't be required.

### User exclusions

Conditional Access policies are powerful tools. We recommend excluding the following accounts from your policies:

- **Emergency access or break-glass accounts** to prevent tenant-wide account lockout.
- **Service accounts and service principals**, such as the Microsoft Entra Connect Sync Account. Service accounts are non-interactive accounts that aren't tied to any particular user.


## Explore logs and monitoring options with Global Secure Access

You need to monitor the activity of the traffic flowing through your networks. Global Secure Access logs, provide data points you can review to gain insights into your network traffic.

### Global Secure Access Audit logs

The Microsoft Entra audit log is a valuable source of information when researching or troubleshooting changes to your Microsoft Entra environment. Changes related to Global Secure Access are captured in the audit logs. Logs have categories, such as filtering policy, forwarding profiles, remote network management, and more.

#### Access audit logs from Global Secure Access or the Microsoft Entra admin center

##### From Global Secure Access

1. Sign in to the Microsoft Entra admin center using one of the required roles.
2. Browse to Global Secure Access > Audit logs. The filters are prepopulated with the categories and activities related to Global Secure Access.

##### From Microsoft Entra monitoring and health

1. Sign in to the Microsoft Entra admin center using one of the required roles.
2. Browse to Identity > Monitoring & health > Audit logs.
3. Select the Date range you want to query.
4. Open the Service filter, select Global Secure Access, and select Apply.
5. Open the Category filter, select at least one of the available options, and select Apply.

### Traffic logs (preview)

The Global Secure Access traffic logs provide a summary of the network connections and transactions that are occurring in your environment. These logs look at who accessed what traffic from where, and with what result. The traffic logs provide a snapshot of all connections in your environment and categorize traffic. The logs details provide the traffic type destination, source IP, and more. To better understand those details, it's helpful to look at the three levels of the logs and their relationship to each other.

A user accessing a website represents one session, and within that session there could be multiple connections, and within that connection there could be multiple transactions.

- Session: A session starts with the first URL a user accesses. That session could then open many connections, for example, a news site that contains multiple ads from several different sites.
- Connection: A connection includes the source and destination IP, source and destination port, and fully qualified domain name (FQDN). The connection components comprise the 5-tuple.
- Transaction: A transaction is a unique request and response pair.

### How to view the traffic logs

1. Sign in to the Microsoft Entra admin center as at least a Reports Reader.
2. Global Secure Access > Monitor > Traffic logs.

Various filters and export options are available for the traffic logs.

### Enriched Office 365 logs (preview)

The Enriched Office 365 logs provide you with the information you need to gain insights into the performance, experience, and availability of the Microsoft 365 apps your organization uses. You can integrate the logs with a Log Analytics workspace or Security Information and Event Management (SIEM) tool for further analysis. The enriched Microsoft 365 logs provide information about Microsoft 365 workloads, so you can review network diagnostic data, performance data, and security events relevant to Microsoft 365 apps. For example, if access to Microsoft 365 is blocked for a user in your organization, you need visibility into how the user's device is connecting to your network.

##### These logs provide

- Improved latency
- Additional information added to original logs
- Accurate IP address

##### How to view the logs

Viewing enriched Microsoft 365 audit logs is a one-time, two-step process. First, collect Global Secure Access Network Traffic logs and Microsoft 365 Unified Audit logs to the same endpoint (Microsoft Sentinel is the recommended workspace). Second, create your own join query to correlate the two tables, or use the out-of-the-box Global Secure Access Enriched Microsoft 365 Logs workbook that already applies the required queries.

Note

Instead of a separate enriched log stream, use the two existing log tables — Microsoft 365 **OfficeActivity** and Global Secure Access **NetworkAccessTraffic** — and combine the data by using a Unique Token ID. At this time, only SharePoint Online logs are available for log enrichment.

##### Send logs to an endpoint

1. Sign in to the Microsoft Entra admin center as at least a Security Administrator.
2. Browse to Identity > Monitoring & health > Diagnostic settings.
3. Select Add Diagnostic setting.
4. Give your diagnostic setting a name.
5. Select **NetworkAccessTrafficLogs**.
6. Select the Destination details for where you'd like to send the logs. Choose any or all of the following destinations:
  - Send to Log Analytics workspace.
  - Archive to a storage account.
  - Stream to an event hub.
  - Send to partner solution.

### Log retention and storage

Traffic logs and remote network health logs: These logs are retained within the system for 30 days. This duration allows for ample time to review and analyze recent activities and network health status.

- Audit logs: The retention period for audit logs varies depending on your Microsoft Entra ID license.
- Office logs: Office logs are maintained for a shorter duration, up to only 24 hours.


## Module assessment

Choose the best response for each of the questions.

### Check your knowledge


## Summary and resources

In this module, you learned how to configure and manage Microsoft's Security Service Edge (SSE) solution through Microsoft Entra Global Secure Access. This comprehensive solution provides secure access to any app or resource from anywhere by merging network, identity, and endpoint access controls into a unified cloud-delivered platform.

You explored the deployment and configuration of both Microsoft Entra Internet Access and Microsoft Entra Private Access, understanding how each component addresses different security needs. Microsoft Entra Internet Access protects users accessing Microsoft services, SaaS apps, and public internet resources through an identity-centric Secure Web Gateway. Microsoft Entra Private Access provides secure, VPN-less access to private corporate resources across hybrid and multicloud environments.

Throughout this module, you gained hands-on knowledge of key implementation tasks, including:

- Enabling traffic forwarding profiles for Microsoft, internet, and private access
- Deploying the Global Secure Access client to end-user devices
- Configuring tenant restrictions to prevent data exfiltration
- Setting up remote networks with IPsec tunnels for branch office connectivity
- Creating Quick Access applications for private resource access
- Implementing Conditional Access policies with compliant network checks and source IP restoration
- Monitoring network activity through the Global Secure Access dashboard and various log types

By completing this module, you now have the foundational knowledge to implement Microsoft Entra Global Secure Access as part of a Zero Trust security strategy, enabling your organization to secure access to resources while maintaining visibility and control over network traffic.

#### Additional reading

- [Global Secure Access documentation](https://learn.microsoft.com/en-us/entra/global-secure-access/)
- [Zero Trust Guidance Center](https://learn.microsoft.com/en-us/security/zero-trust/)
- [Microsoft Entra Conditional Access documentation](https://learn.microsoft.com/en-us/entra/identity/conditional-access/)
