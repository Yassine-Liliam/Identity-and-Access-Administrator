# SC-300 — Administrateur Identité et accès Microsoft

Notes de révision pour l'examen de certification **SC-300**. Elles couvrent intégralement les
quatre parcours d'apprentissage officiels Microsoft Learn : 18 modules, 194 unités et
29 exercices pratiques.

Disponibles en deux langues :

| Langue | Dossier | Mots |
|---|---|---|
| Français | [`fr-FR/`](fr-FR/) | ~137 000 |
| English | [`en-US/`](en-US/) — voir [README.md](README.md) | ~120 000 |

Chaque dossier de langue contient quatre fichiers Markdown, un par parcours d'apprentissage. Les
modules et unités d'un parcours tiennent dans son propre fichier : un parcours se lit donc d'une
traite, s'imprime ou se charge dans une liseuse, et un `grep` sur le dossier couvre tout le cours.

---

## Programme

| # | Parcours d'apprentissage | Modules | Unités | Exercices | Fichier |
|---|---|---|---|---|---|
| 1 | Implémenter une solution de gestion des identités | 4 | 52 | 11 | [1-implement-identity-management-solution.md](fr-FR/1-implement-identity-management-solution.md) |
| 2 | Implémenter une solution de gestion des accès et des authentifications | 6 | 62 | 8 | [2-implement-authentication-access-management-solution.md](fr-FR/2-implement-authentication-access-management-solution.md) |
| 3 | Implémenter la gestion des accès pour les applications | 4 | 40 | 3 | [3-implement-access-management-for-apps.md](fr-FR/3-implement-access-management-for-apps.md) |
| 4 | Planifier et implémenter une stratégie de gouvernance des identités | 4 | 40 | 7 | [4-plan-implement-identity-governance-strategy.md](fr-FR/4-plan-implement-identity-governance-strategy.md) |
| | **Total** | **18** | **194** | **29** | |

### Parcours 1 — Implémenter une solution de gestion des identités

Configuration du locataire, utilisateurs et groupes, identités externes et identité hybride avec Entra Connect.

1. Implémenter la configuration initiale d'Entra ID *(11 unités)*
2. Créer, configurer et gérer des identités *(14 unités)*
3. Implémenter et gérer des identités externes *(16 unités)*
4. Implémenter et gérer l'identité hybride *(11 unités)*

### Parcours 2 — Implémenter une solution de gestion des accès et des authentifications

MFA, méthodes d'authentification, accès conditionnel, Identity Protection, RBAC Azure et Accès global sécurisé.

1. Sécurisez les utilisateurs Entra avec l'authentification multifacteur *(6 unités)*
2. Gérer l'authentification des utilisateurs *(12 unités)*
3. Planifier, implémenter et administrer l'accès conditionnel *(13 unités)*
4. Gérer Entra Identity Protection *(11 unités)*
5. Implémenter le Gestionnaire d'accès pour des ressources Azure *(10 unités)*
6. Déployer et configurer Accès global sécurisé Entra *(10 unités)*

### Parcours 3 — Implémenter la gestion des accès pour les applications

Authentification unique des applications d'entreprise, inscription d'applications, consentement,
autorisations et rôles d'application.

1. Planifier et concevoir l'intégration des applications d'entreprise pour l'authentification unique *(10 unités)*
2. Implémenter et surveiller l'intégration des applications d'entreprise pour l'authentification unique *(10 unités)*
3. Implémenter l'inscription d'application *(11 unités)*
4. Inscrire des applications à l'aide d'Entra ID *(9 unités)*

### Parcours 4 — Planifier et implémenter une stratégie de gouvernance des identités

Gestion des droits d'utilisation, révisions d'accès, PIM et surveillance avec Sentinel.

1. Planifier et implémenter la gestion des droits d'utilisation *(10 unités)*
2. Planifier, implémenter et gérer la révision d'accès *(10 unités)*
3. Planifier et implémenter un accès privilégié *(11 unités)*
4. Surveiller et gérer Entra ID *(9 unités)*

---

## Exercices

Les 29 exercices pratiques, dans l'ordre de lecture. Tous nécessitent un abonnement Azure —
voir [Prérequis des travaux pratiques](#prérequis-des-travaux-pratiques) ci-dessous.

### Parcours 1 — Gestion des identités *(11)*

| # | Exercice | Module |
|---|---|---|
| 1 | [Gérer les rôles d'utilisateurs](fr-FR/1-implement-identity-management-solution.md#exercice---gérer-les-rôles-dutilisateurs) | Configuration initiale |
| 2 | [Définition des propriétés au niveau du locataire](fr-FR/1-implement-identity-management-solution.md#exercice---définition-des-propriétés-au-niveau-du-locataire) | Configuration initiale |
| 3 | [Attribuer des licences aux utilisateurs](fr-FR/1-implement-identity-management-solution.md#exercice---attribuer-des-licences-aux-utilisateurs) | Identités |
| 4 | [Supprimer ou restaurer des utilisateurs supprimés](fr-FR/1-implement-identity-management-solution.md#exercice---supprimer-ou-restaurer-des-utilisateurs-supprimés) | Identités |
| 5 | [Ajouter des groupes dans Entra ID](fr-FR/1-implement-identity-management-solution.md#exercice--ajouter-des-groupes-dans-entra-id) | Identités |
| 6 | [Modifier les affectations de licences de groupe](fr-FR/1-implement-identity-management-solution.md#exercice---modifier-les-affectations-de-licences-de-groupe) | Identités |
| 7 | [Modifier des affectations de licence utilisateur](fr-FR/1-implement-identity-management-solution.md#exercice---modifier-des-affectations-de-licence-utilisateur) | Identités |
| 8 | [Configurer la collaboration externe](fr-FR/1-implement-identity-management-solution.md#exercice-configurer-la-collaboration-externe) | Identités externes |
| 9 | [Ajouter des utilisateurs invités au répertoire](fr-FR/1-implement-identity-management-solution.md#exercice-ajouter-des-utilisateurs-invités-au-répertoire) | Identités externes |
| 10 | [Inviter des utilisateurs en bloc](fr-FR/1-implement-identity-management-solution.md#exercice-inviter-des-utilisateurs-en-bloc) | Identités externes |
| 11 | [Explorer les groupes dynamiques](fr-FR/1-implement-identity-management-solution.md#exercice--explorer-les-groupes-dynamiques) | Identités externes |

### Parcours 2 — Authentification et gestion des accès *(8)*

| # | Exercice | Module |
|---|---|---|
| 12 | [Activer l'authentification multifacteur Entra](fr-FR/2-implement-authentication-access-management-solution.md#exercice-activer-lauthentification-multifacteur-entra) | MFA |
| 13 | [Configurer et déployer la réinitialisation du mot de passe en libre-service](fr-FR/2-implement-authentication-access-management-solution.md#excercice-de-configuration-et-de-déploiement-de-la-réinitialisation-du-mot-de-passe-en-libre-service) | Authentification des utilisateurs |
| 14 | [Gérer les valeurs de verrouillage intelligentes d'Entra](fr-FR/2-implement-authentication-access-management-solution.md#exercice--gérer-les-valeurs-de-verrouillage-intelligentes-dentra) | Authentification des utilisateurs |
| 15 | [Utiliser les paramètres de sécurité par défaut](fr-FR/2-implement-authentication-access-management-solution.md#exercice---utiliser-les-paramètres-de-sécurité-par-défaut) | Accès conditionnel |
| 16 | [Implémenter des contrôles et des affectations de stratégie d'accès conditionnel](fr-FR/2-implement-authentication-access-management-solution.md#exercice---implémenter-des-contrôles-et-des-affectations-de-stratégie-daccès-conditionnel) | Accès conditionnel |
| 17 | [Configurer des contrôles de session d'authentification](fr-FR/2-implement-authentication-access-management-solution.md#exercice---configurer-des-contrôles-de-session-dauthentification) | Accès conditionnel |
| 18 | [Activer la stratégie de connexion à risque](fr-FR/2-implement-authentication-access-management-solution.md#exercice--activer-la-stratégie-de-connexion-à-risque) | Identity Protection |
| 19 | [Configurer la stratégie d'inscription MFA](fr-FR/2-implement-authentication-access-management-solution.md#exercice-configurer-la-stratégie-dinscription-de-lauthentification-multifacteur-entra) | Identity Protection |

### Parcours 3 — Gestion des accès pour les applications *(3)*

| # | Exercice | Module |
|---|---|---|
| 20 | [Implémenter la gestion des accès pour les applications](fr-FR/3-implement-access-management-for-apps.md#lexercice-implémente-la-gestion-des-accès-pour-les-applications) | SSO applications d'entreprise |
| 21 | [Créer un rôle personnalisé pour gérer l'inscription d'application](fr-FR/3-implement-access-management-for-apps.md#exercice--créer-un-rôle-personnalisé-pour-gérer-linscription-dapplication) | SSO applications d'entreprise |
| 22 | [Ajouter des rôles à une application et recevoir des jetons](fr-FR/3-implement-access-management-for-apps.md#exercice--ajouter-des-rôles-à-une-application-et-recevoir-des-jetons) | Inscription d'application |

### Parcours 4 — Gouvernance des identités *(7)*

| # | Exercice | Module |
|---|---|---|
| 23 | [Créer et gérer un catalogue de ressources](fr-FR/4-plan-implement-identity-governance-strategy.md#exercice-création-et-gestion-dun-catalogue-de-ressources-avec-une-gestion-des-droits-dutilisation-dentra) | Droits d'utilisation |
| 24 | [Ajouter un rapport d'acceptation des conditions d'utilisation](fr-FR/4-plan-implement-identity-governance-strategy.md#exercice-ajouter-un-rapport-dacceptation-des-conditions-dutilisation) | Droits d'utilisation |
| 25 | [Gérer le cycle de vie des utilisateurs externes](fr-FR/4-plan-implement-identity-governance-strategy.md#exercice--gérer-le-cycle-de-vie-des-utilisateurs-externes-avec-la-gouvernance-des-identités-entra) | Droits d'utilisation |
| 26 | [Configurer PIM pour les rôles Entra](fr-FR/4-plan-implement-identity-governance-strategy.md#exercice-de-configuration-de-privileged-identity-management-pour-les-rôles-entra) | Accès privilégié |
| 27 | [Attribuer des rôles Entra dans PIM](fr-FR/4-plan-implement-identity-governance-strategy.md#exercice-dattribution-de-rôles-entra-dans-privileged-identity-management) | Accès privilégié |
| 28 | [Assigner des rôles de ressources Azure dans PIM](fr-FR/4-plan-implement-identity-governance-strategy.md#exercice-pour-assigner-des-rôles-de-ressources-azure-dans-la-gestion-des-identités-privilégiées) | Accès privilégié |
| 29 | [Connecter les données d'Entra ID à Microsoft Sentinel](fr-FR/4-plan-implement-identity-governance-strategy.md#exercice-connexion-de-données-dentra-id-à-microsoft-sentinel) | Surveillance |

> Le module **Planifier, implémenter et gérer la révision d'accès** (parcours 4) ne comporte pas
> d'exercice pratique : sa présentation de l'API renvoie aux tutoriels Microsoft Graph.

---

## Prérequis des travaux pratiques

Chaque exercice s'exécute sur un locataire réel. Avant de commencer le parcours 1, prévoyez :

- Un **abonnement Azure** — un compte d'essai gratuit suffit pour les 29 exercices.
- Une licence d'essai **Entra ID Premium P2**, activée depuis la page *Prise en main* du locataire.
  P2 est indispensable pour PIM, Identity Protection, les révisions d'accès et la gestion des
  droits d'utilisation (parcours 2 et 4). P1 seule ne suffit pas.
- Quelques **utilisateurs et groupes de test**, créés dans les exercices du parcours 1 puis
  réutilisés par la suite.
- Des **licences Microsoft 365** pour les exercices qui touchent à Teams, SharePoint ou Exchange.

L'exercice 29 nécessite en plus un espace de travail **Microsoft Sentinel**, facturé sur
l'abonnement — supprimez le groupe de ressources une fois terminé.

## Ordre de révision conseillé

Suivez les parcours dans l'ordre numérique : le parcours 1 met en place le locataire, les
utilisateurs et les groupes que les exercices suivants supposent déjà présents. Au sein d'un
parcours, lisez les unités théoriques avant l'exercice qui les suit : les exercices reprennent
rarement le raisonnement derrière un paramètre.

En révision plutôt qu'en apprentissage, la liste d'exercices ci-dessus fait une bonne checklist :
savoir réaliser les 29 de mémoire couvre l'essentiel de ce que l'examen demande de **faire**,
tandis que les unités couvrent ce qu'il demande de **savoir**.

## Différences avec Microsoft Learn

Le contenu suit les modules officiels unité par unité, avec quelques adaptations pour la lecture
hors ligne :

- **Captures d'écran supprimées.** Les images pointaient vers le CDN de Microsoft Learn et ne
  s'affichent pas en dehors du site. Les schémas de processus sont conservés (en texte alternatif)
  lorsqu'ils portent l'explication.
- **Temps de lecture, titres dupliqués et liens source par unité supprimés.** Chaque parcours et
  chaque module conservent le lien vers leur page d'origine sur Microsoft Learn.
- **« Microsoft Entra » raccourci en « Entra »** partout — 3 165 occurrences. Le produit est
  sans ambiguïté dans le contexte, et les phrases se lisent plus vite.
- **Phrases longues réécrites.** 312 phrases des fichiers français (237 en anglais) ont été
  scindées ou restructurées. Aucun fait, nom de rôle, prérequis de licence, paramètre ou chemin
  de portail n'a été modifié.

Le traitement est reproductible depuis l'historique git : `ee330e5` pour le nettoyage,
`d68a018` pour la réécriture.

## Source et licence

Le contenu provient des modules de formation Microsoft Learn pour
[SC-300 : Administrateur Identité et accès Microsoft](https://learn.microsoft.com/fr-fr/training/courses/sc-300t00),
© Microsoft. Il est reproduit ici à titre de notes de révision personnelles. Le contenu de
Microsoft Learn est publié sous licence [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.fr) ;
les modules font foi et sont mis à jour plus souvent que cette copie — vérifiez-les avant de vous
fier à un chemin de portail ou à un prérequis de licence précis.

Entra ID, Azure et Microsoft 365 sont des marques de Microsoft Corporation. Ce dépôt n'est ni
affilié à Microsoft ni approuvé par Microsoft.
