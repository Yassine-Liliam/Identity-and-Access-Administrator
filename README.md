# SC-300 — Microsoft Identity and Access Administrator

Study notes for the **SC-300** certification exam, covering the four official Microsoft Learn
learning paths in full: 18 modules, 194 units and 29 hands-on exercises.

Available in two languages:

| Language | Folder | Words |
|---|---|---|
| English | [`en-US/`](en-US/) | ~120,000 |
| Français | [`fr-FR/`](fr-FR/) — see [README.fr.md](README.fr.md) | ~137,000 |

Each language folder holds four Markdown files, one per learning path. A path's modules and units
all live in its own file, so you can read a whole path straight through, print it, or load it into
a reader; a `grep` across the folder searches the entire course.

---

## Agenda

| # | Learning path | Modules | Units | Exercises | File |
|---|---|---|---|---|---|
| 1 | Implement an identity management solution | 4 | 52 | 11 | [1-implement-identity-management-solution.md](en-US/1-implement-identity-management-solution.md) |
| 2 | Implement an authentication and access management solution | 6 | 62 | 8 | [2-implement-authentication-access-management-solution.md](en-US/2-implement-authentication-access-management-solution.md) |
| 3 | Implement access management for apps | 4 | 40 | 3 | [3-implement-access-management-for-apps.md](en-US/3-implement-access-management-for-apps.md) |
| 4 | Plan and implement an identity governance strategy | 4 | 40 | 7 | [4-plan-implement-identity-governance-strategy.md](en-US/4-plan-implement-identity-governance-strategy.md) |
| | **Total** | **18** | **194** | **29** | |

### Path 1 — Implement an identity management solution

Tenant configuration, users and groups, external identities, and hybrid identity with Entra Connect.

1. Implement initial configuration of Entra ID *(11 units)*
2. Create, configure, and manage identities *(14 units)*
3. Implement and manage external identities *(16 units)*
4. Implement and manage hybrid identity *(11 units)*

### Path 2 — Implement an authentication and access management solution

MFA, authentication methods, Conditional Access, Identity Protection, Azure RBAC, and Global Secure Access.

1. Secure Entra users with multifactor authentication *(6 units)*
2. Manage user authentication *(12 units)*
3. Plan, implement, and administer Conditional Access *(13 units)*
4. Manage Entra Identity Protection *(11 units)*
5. Implement access management for Azure resources *(10 units)*
6. Deploy and Configure Entra Global Secure Access *(10 units)*

### Path 3 — Implement access management for apps

Enterprise app SSO, app registration, consent, permissions, and app roles.

1. Plan and design the integration of enterprise apps for SSO *(10 units)*
2. Implement and monitor the integration of enterprise apps for SSO *(10 units)*
3. Implement app registration *(11 units)*
4. Register apps using Entra ID *(9 units)*

### Path 4 — Plan and implement an identity governance strategy

Entitlement management, access reviews, PIM, and monitoring with Sentinel.

1. Plan and implement entitlement management *(10 units)*
2. Plan, implement, and manage access review *(10 units)*
3. Plan and implement privileged access *(11 units)*
4. Monitor and maintain Entra ID *(9 units)*

---

## Exercises

All 29 hands-on exercises, in reading order. Each needs an Azure subscription — see
[Lab prerequisites](#lab-prerequisites) below.

### Path 1 — Implement an identity management solution *(11)*

| # | Exercise | Module |
|---|---|---|
| 1 | [Manage users roles](en-US/1-implement-identity-management-solution.md#exercise-manage-users-roles) | Initial configuration |
| 2 | [Setting tenant-wide properties](en-US/1-implement-identity-management-solution.md#exercise---setting-tenant-wide-properties) | Initial configuration |
| 3 | [Assign licenses to users](en-US/1-implement-identity-management-solution.md#exercise---assign-licenses-to-users) | Identities |
| 4 | [Restore or remove deleted users](en-US/1-implement-identity-management-solution.md#exercise---restore-or-remove-deleted-users) | Identities |
| 5 | [Add groups in Entra ID](en-US/1-implement-identity-management-solution.md#exercise---add-groups-in-entra-id) | Identities |
| 6 | [Change group license assignments](en-US/1-implement-identity-management-solution.md#exercise---change-group-license-assignments) | Identities |
| 7 | [Change user license assignments](en-US/1-implement-identity-management-solution.md#exercise---change-user-license-assignments) | Identities |
| 8 | [Configure external collaboration](en-US/1-implement-identity-management-solution.md#exercise---configure-external-collaboration) | External identities |
| 9 | [Add guest users to directory](en-US/1-implement-identity-management-solution.md#exercise---add-guest-users-to-directory) | External identities |
| 10 | [Invite guest users in bulk](en-US/1-implement-identity-management-solution.md#exercise---invite-guest-users-bulk) | External identities |
| 11 | [Explore dynamic groups](en-US/1-implement-identity-management-solution.md#exercise---explore-dynamic-groups) | External identities |

### Path 2 — Implement an authentication and access management solution *(8)*

| # | Exercise | Module |
|---|---|---|
| 12 | [Enable Entra multifactor authentication](en-US/2-implement-authentication-access-management-solution.md#exercise---enable-entra-multifactor-authentication) | MFA |
| 13 | [Configure and deploy self-service password reset](en-US/2-implement-authentication-access-management-solution.md#exercise-configure-and-deploy-self-service-password-reset) | User authentication |
| 14 | [Manage Entra smart lockout values](en-US/2-implement-authentication-access-management-solution.md#exercise---manage-entra-smart-lockout-values) | User authentication |
| 15 | [Work with security defaults](en-US/2-implement-authentication-access-management-solution.md#exercise---work-with-security-defaults) | Conditional Access |
| 16 | [Implement Conditional Access policies, roles and assignments](en-US/2-implement-authentication-access-management-solution.md#exercise---implement-conditional-access-policies-roles-and-assignments) | Conditional Access |
| 17 | [Configure authentication session controls](en-US/2-implement-authentication-access-management-solution.md#exercise---configure-authentication-session-controls) | Conditional Access |
| 18 | [Enable sign-in risk policy](en-US/2-implement-authentication-access-management-solution.md#exercise-enable-sign-in-risk-policy) | Identity Protection |
| 19 | [Configure MFA registration policy](en-US/2-implement-authentication-access-management-solution.md#exercise-configure-entra-multifactor-authentication-registration-policy) | Identity Protection |

### Path 3 — Implement access management for apps *(3)*

| # | Exercise | Module |
|---|---|---|
| 20 | [Implement access management for apps](en-US/3-implement-access-management-for-apps.md#exercise-implement-access-management-for-apps) | Enterprise app SSO |
| 21 | [Create a custom role to manage app registration](en-US/3-implement-access-management-for-apps.md#exercise-create-a-custom-role-to-manage-app-registration) | Enterprise app SSO |
| 22 | [Add app roles to an application and receive tokens](en-US/3-implement-access-management-for-apps.md#exercise-add-app-roles-to-an-application-and-receive-tokens) | App registration |

### Path 4 — Plan and implement an identity governance strategy *(7)*

| # | Exercise | Module |
|---|---|---|
| 23 | [Create and manage a resource catalog with entitlement management](en-US/4-plan-implement-identity-governance-strategy.md#exercise-create-and-manage-a-resource-catalog-with-entra-entitlement-management) | Entitlement management |
| 24 | [Add terms of use acceptance report](en-US/4-plan-implement-identity-governance-strategy.md#exercise-add-terms-of-use-acceptance-report) | Entitlement management |
| 25 | [Manage the lifecycle of external users](en-US/4-plan-implement-identity-governance-strategy.md#exercise-manage-the-lifecycle-of-external-users-with-entra-identity-governance) | Entitlement management |
| 26 | [Configure PIM for Entra roles](en-US/4-plan-implement-identity-governance-strategy.md#exercise-configure-privileged-identity-management-for-entra-roles) | Privileged access |
| 27 | [Assign Entra roles in PIM](en-US/4-plan-implement-identity-governance-strategy.md#exercise-assign-entra-roles-in-privileged-identity-management) | Privileged access |
| 28 | [Assign Azure resource roles in PIM](en-US/4-plan-implement-identity-governance-strategy.md#exercise-assign-azure-resource-roles-in-privileged-identity-management) | Privileged access |
| 29 | [Connect data from Entra ID to Microsoft Sentinel](en-US/4-plan-implement-identity-governance-strategy.md#exercise-connect-data-from-entra-id-to-microsoft-sentinel) | Monitoring |

> The **Plan, implement, and manage access review** module (path 4) has no hands-on exercise;
> its API walkthrough points to the Microsoft Graph tutorials instead.

---

## Lab prerequisites

Every exercise runs against a live tenant. Before starting path 1, set up:

- An **Azure subscription** — a free trial account works for all 29 exercises.
- An **Entra ID Premium P2** trial licence, activated from the tenant's *Getting started* page.
  P2 is required for PIM, Identity Protection, access reviews, and entitlement management
  (paths 2 and 4). P1 alone is not enough.
- A few **test users and groups**, created in the path 1 exercises and reused later.
- **Microsoft 365 licences** for the exercises that touch Teams, SharePoint, or Exchange.

Exercise 29 additionally needs a **Microsoft Sentinel** workspace, which bills against the
subscription — delete the resource group when you are finished.

## Suggested study order

Follow the paths in numeric order: path 1 builds the tenant, users and groups that the later
exercises assume exist. Within a path, read the conceptual units before the exercise that
follows them — the exercises rarely repeat the reasoning behind a setting.

If you are revising rather than learning, the exercise list above works as a practical checklist:
being able to complete all 29 from memory covers most of what the exam asks you to *do*, while
the units cover what it asks you to *know*.

## How these notes differ from Microsoft Learn

The content follows the official modules unit by unit, with some editing for offline reading:

- **Screenshots removed.** The images pointed at Microsoft Learn's CDN and don't resolve outside
  the site. Process diagrams are kept (as alt text) where they carry the explanation.
- **Reading times, duplicated headings, and per-unit source links removed.** Each learning path
  and module still links to its source page on Microsoft Learn.
- **"Microsoft Entra" shortened to "Entra"** throughout — 3,165 occurrences. The product is
  unambiguous in context, and the sentences read faster without it.
- **Long sentences rewritten.** 237 sentences in the English files (312 in French) were split or
  restructured for readability. No facts, role names, licence requirements, settings, or portal
  paths were changed.

The pipeline is reproducible from git history: `ee330e5` is the cleanup pass, `d68a018` the rewrite.

## Source and licence

Content is derived from the Microsoft Learn training modules for
[SC-300: Microsoft Identity and Access Administrator](https://learn.microsoft.com/en-us/training/courses/sc-300t00),
© Microsoft. It is reproduced here as personal study notes. Microsoft Learn content is published
under the [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) licence; the modules are the
authoritative version and are updated more often than this copy — check them before relying on a
specific portal path or licence requirement.

Entra ID, Azure, and Microsoft 365 are trademarks of Microsoft Corporation. This repository is not
affiliated with or endorsed by Microsoft.
