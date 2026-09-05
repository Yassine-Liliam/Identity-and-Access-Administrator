# Implémenter une solution de gestion des identités à l’aide de l’ID Entra

> SC-300 — learning path 1/4
> https://learn.microsoft.com/fr-fr/training/paths/implement-identity-management-solution/

## Modules

- **Implémenter la configuration initiale d’Entra ID** (11 units)
- **Créer, configurer et gérer des identités** (14 units)
- **Implémenter et gérer des identités externes** (16 units)
- **Implémenter et gérer l’identité hybride** (11 units)


---

# Implémenter la configuration initiale d’Entra ID

_https://learn.microsoft.com/fr-fr/training/modules/implement-initial-configuration-of-azure-active-directory/_


## Présentation

Dans ce module, vous allez apprendre à configurer et gérer un locataire Entra. Vous explorez les rôles Entra, les domaines personnalisés et les options de personnalisation de l'entreprise. En outre, vous allez apprendre à configurer la délégation à l'aide d'unités administratives et à configurer plusieurs paramètres à l'échelle du locataire dans Entra ID.

### Objectifs d’apprentissage

Dans ce module, vous allez :

- Configurer la marque de l’entreprise.
- Configurer et gérer les rôles Entra
- Configurer la délégation à l’aide d’unités administratives.
- Configurer et gérer des domaines personnalisés.
- Évaluez les autorisations en fonction des attributions de rôles et des paramètres.
- Configurez les paramètres à l’échelle du locataire.

### Prérequis

Expérience d'utilisation antérieure avec l'interface utilisateur du portail Azure ou le Centre d'administration Entra.


## Configurer la marque de l’entreprise

Vous pouvez utiliser le logo de votre organisation et des modèles de couleurs personnalisés pour fournir une expérience cohérente sur vos pages de connexion. Vos pages de connexion s'affichent quand les utilisateurs se connectent aux applications Web de votre organisation, comme Microsoft 365, qui utilisent Entra ID comme fournisseur d'identité. L'ajout d'une marque personnalisée nécessite que vous ayez une licence **Entra ID premium P1, P2, ou Office 365 (pour les applications Office 365)**.

Pour personnaliser la marque de l'entreprise, ouvrez la page Entra ID dans le portail Azure. Lancez ensuite **Marque de société** à partir du menu Gérer. Une licence Premium est requise pour que l’option de menu apparaisse.

| **Paramètre** | **Description** |
|---|---|
| Langue | La langue est définie automatiquement par défaut et ne peut pas être modifiée. |
| Image d’arrière-plan de la page de connexion | Sélectionnez un fichier image .png ou .jpg pour l’arrière-plan de vos pages de connexion. L’image est ancrée au centre du navigateur et s’ajuste à la taille de l’espace affichable. Vous ne pouvez pas sélectionner une image dont la taille est supérieure à 1 920 x 1 080 pixels ou dont la taille de fichier est supérieure à 300 000 octets. |
| Logo de bannière | Sélectionnez une version .png ou .jpg de votre logo, qui apparaît sur la page de connexion une fois que l’utilisateur a entré un nom d’utilisateur et sur la page du portail Mes applications. |
| Indication sur le nom d’utilisateur | Entrez le texte d’indication qui s’affiche pour les utilisateurs ayant oublié leur nom d’utilisateur. Ce texte doit être au format Unicode, ne comporter aucun lien ni code, et ne pas dépasser 64 caractères. Si des invités se connectent à votre application, nous vous suggérons de ne pas ajouter cet indicateur. |
| Texte et mise en forme de la page de connexion | Entrez le texte qui apparaît au bas de la page de connexion. Vous pouvez utiliser ce texte pour communiquer des informations supplémentaires telles que le numéro de téléphone à votre support technique ou une mention légale. Ce texte doit être au format Unicode et ne doit pas dépasser 1 024 caractères. |


## Configurer et gérer les rôles Entra

Entra ID est le service de gestion des identités et des accès basé sur le cloud de Microsoft, qui permet à vos employés de se connecter et d'accéder aux ressources dans :

- Ressources externes telles que Microsoft 365, le portail Azure et des milliers d’autres applications SaaS.
- Ressources internes telles que les applications situées sur votre réseau d’entreprise et intranet ainsi que les applications cloud développées par votre propre organisation.

### Qui utilise Entra ID ?

Entra ID est destiné aux :

- **administrateurs informatiques** – en tant qu'administrateur informatique, vous pouvez utiliser Entra ID pour contrôler l'accès à vos applications et à vos ressources d'application, en fonction de vos exigences professionnelles. Par exemple, vous pouvez utiliser Entra ID pour exiger une authentification multifacteur lors de l'accès à des ressources organisationnelles importantes. En outre, vous pouvez utiliser Entra ID pour automatiser l'approvisionnement des utilisateurs entre votre Windows Server AD existant et vos applications cloud, notamment Microsoft 365. Entra ID vous offre enfin des outils puissants pour vous aider à protéger automatiquement les identités et informations d’identification des utilisateurs et à répondre à vos exigences en matière de gouvernance.
- **Développeurs** d’applications : Entra ID vous offre une approche basée sur des normes pour ajouter l’authentification unique (SSO) à votre application, qui peut alors utiliser les informations d’identification préexistantes d’un utilisateur. Entra ID fournit également des API qui peuvent vous aider à créer des expériences d'application personnalisées en utilisant les données organisationnelles existantes.
- **abonnés à Microsoft 365, Office 365, Azure ou Dynamics CRM Online** – En tant qu'abonné, vous utilisez déjà Entra ID. Chaque abonné Microsoft 365, Office 365, Azure et Dynamics CRM Online est automatiquement un abonné Entra. Vous pouvez immédiatement commencer à gérer l’accès à vos applications cloud intégrées.

Dans Entra ID, si l'un de vos utilisateurs a besoin d'une autorisation pour gérer les ressources Entra, vous devez lui attribuer un rôle qui lui donne les autorisations dont il a besoin.

Si vous débutez sur Azure, vous trouverez peut-être un peu difficile de comprendre l'ensemble des différents rôles dans Azure. La section suivante explique les rôles suivants et fournit des informations supplémentaires sur les rôles Azure et Entra :

- Rôles d’administrateur d’abonnements classique
- Rôles Azure
- Rôles Entra

### Rôles Entra

Les rôles Entra sont utilisés pour gérer les ressources Entra dans un répertoire. Les actions telles que la création ou la modification d’utilisateurs sont les plus courantes. Toutefois, la nécessité d’attribuer des rôles d’administration à d’autres personnes, de réinitialiser les mots de passe utilisateur, de gérer les licences utilisateur et de gérer les domaines est courante. Le tableau suivant décrit quelques-uns des rôles Entra les plus importants.

| **Rôle Entra** | **autorisations** | **Remarques** |
|---|---|---|
| Administrateur général | Gérer l'accès à toutes les fonctionnalités administratives d’Entra ID et aux services rassemblés dans Entra ID. | La personne qui s'inscrit comme abonné d’Entra devient automatiquement administrateur général. |
|   | Attribution des rôles d’administrateur à d’autres personnes |   |
|   | Réinitialisation des mots de passe des utilisateurs et de tous les autres administrateurs |   |
| Administrateur d'utilisateurs | Création et gestion de tous les aspects liés aux utilisateurs et aux groupes |   |
|   | Gestion des tickets de support |   |
|   | Suivi de l’intégrité des services |   |
|   | Changement des mots de passe des utilisateurs, des administrateurs du support technique et autres administrateurs d’utilisateurs |   |
| Administrateur de facturation | Achats |   |
|   | Gérer les abonnements |   |
|   | Gestion des tickets de support |   |
|   | Suivi de l’intégrité des services |   |

Dans le portail Azure, vous pouvez voir la liste des rôles Entra à l'écran **Rôles et administrateurs**.

### Les différences entre les rôles Azure et les rôles Entra

Globalement, les rôles Azure contrôlent les autorisations pour gérer les ressources Azure, tandis que les rôles Entra contrôlent les autorisations pour gérer les ressources Entra. Le tableau suivant compare quelques différences.

| **Rôles Azure** | **Rôles Entra** |
|---|---|
| Gérer l’accès aux ressources Azure | Gérer l’accès aux ressources Entra |
| Prise en charge des rôles personnalisés | Prise en charge des rôles personnalisés |
| L’étendue peut être spécifiée à plusieurs niveaux (groupe d’administration, abonnement, groupe de ressources, ressource) | L’étendue est au niveau de l’abonné ou peut être appliquée à une unité administrative |
| Les informations sur les rôles sont accessibles dans le portail Azure, Azure CLI, Azure PowerShell, les modèles Azure Resource Manager et l’API REST | Les informations des rôles sont accessibles dans le portail d'administration Azure, Centre d'administration Microsoft 365, Microsoft Graph et PowerShell |

#### Les rôles Azure et les rôles Entra se recoupent-ils ?

Par défaut, les rôles Azure et les rôles Entra n’englobent pas Azure et Entra ID. Toutefois, un administrateur général peut élever son accès avec le commutateur **Gestion des accès pour les ressources Azure** du portail Azure. Il reçoit alors le rôle Administrateur d’accès utilisateur (rôle Azure) sur tous les abonnements d’un locataire particulier. Le rôle Administrateur de l’accès utilisateur permet à l’utilisateur d’accorder à d’autres utilisateurs l’accès aux ressources Azure. Ce commutateur peut être utile pour récupérer l’accès à un abonnement.

Plusieurs rôles Entra couvrent l’ID Entra et Microsoft 365, tels que les rôles d’administrateur général et d’utilisateur. Par exemple, si vous avez le rôle Administrateur général, vous disposez de fonctionnalités d’administrateur dans Entra ID et Microsoft 365, telles que l’apport de modifications à Microsoft Exchange et Microsoft SharePoint. Toutefois, par défaut, l’administrateur général n’a pas accès aux ressources Azure.

Remarque

Microsoft ne recommande pas l’utilisation du rôle Administrateur général. Il est recommandé de suivre le principe du privilège minimum lors de l’exécution de tâches administratives.

![Diagramme de la relation entre les rôles Azure et les rôles Entra. Rôles Azure accessibles dans le locataire Azure. Les rôles Entra sont également accessibles depuis Entra ID et Microsoft 365.](https://learn.microsoft.com../../wwl-sci/implement-initial-configuration-of-azure-active-directory/media/azure-office-roles.png)

### Affecter des rôles

Il existe plusieurs façons d'attribuer des rôles dans Entra ID. Vous devez choisir celui qui répond le mieux à vos besoins. L’interface utilisateur peut être légèrement différente pour chaque méthode, mais les options de configuration sont similaires. Les méthodes d’affectation de rôles sont les suivantes :

- Attribuer un rôle à un utilisateur ou un groupe
  - **Entra ID** - **Rôles et administration** - **Sélectionner un rôle** - **+ Ajouter une attribution**

- Affecter un utilisateur ou un groupe à un rôle
  - **Entra ID** – Ouvrir **Utilisateurs** (ou Groupes) – Sélectionner un **utilisateur** (ou un groupe) – **Rôles attribués** - **+ Ajouter une attribution**

- Attribuer un rôle à une étendue, comme un abonnement, un groupe de ressources ou un groupe d’administration
  - Via le **contrôle d’accès (IAM)** au sein de chaque écran de paramètres

- Affecter un rôle à l’aide de PowerShell ou d’une API Microsoft Graph
- Affecter un rôle à un groupe à l’aide de Privileged Identity Management

La meilleure méthode pour vos besoins de configuration peut être utilisée, mais il faut veiller à ce qu’il n’y ait pas de restrictions intégrées. Vous pouvez attribuer accidentellement un rôle d’administration à un groupe avec des utilisateurs qui n’ont pas besoin d’un accès administratif. Les autorisations supplémentaires peuvent entraîner la modification d’une solution par un utilisateur n’ayant pas clairement conscience de ses actions, ou même constituer un angle d’attaque potentiel pour les attaquants. La bonne gouvernance des identités est la clé.

#### Exemple : utilisation de PIM pour affecter un rôle

L'attribution de rôles Entra à un utilisateur se fait généralement sur la page Rôles attribués à un utilisateur. Vous pouvez également configurer l’éligibilité de l’utilisateur à disposer du droit d’être promu juste-à-temps dans un rôle avec **Privileged Identity Management (PIM)**.

Remarque

Si vous disposez d’un plan de licence Entra ID Premium P2 et que vous utilisez déjà PIM, toutes les tâches de gestion des rôles sont effectuées dans l’expérience Privileged Identity Management. Cette fonctionnalité est actuellement limitée à l’attribution d’un seul rôle à la fois. Actuellement, vous ne pouvez pas sélectionner plusieurs rôles et les affecter à un utilisateur tous en même temps.

### Créer et attribuer un rôle personnalisé dans Entra ID

Cette section explique comment créer de nouveaux rôles personnalisés dans Entra ID. Pour connaître les principes de base des rôles personnalisés, consultez la [vue d’ensemble des rôles personnalisés](https://learn.microsoft.com/fr-fr/azure/active-directory/roles/custom-overview). Le rôle peut être affecté soit au niveau de l’étendue au niveau du répertoire, soit à une étendue de ressource d’inscription d’application uniquement.

Vous pouvez créer des rôles personnalisés dans l'onglet [Rôles et administrateurs](https://portal.azure.com/) de la page de présentation d’Entra ID.

1. Sélectionnez **Entra ID** - **Rôles et administrateurs** - **Nouveau rôle personnalisé**.
2. Dans l'onglet **Notions de base**, indiquez un nom et une description pour le rôle, puis sélectionnez **Suivant**.
3. Sous l'onglet **Permissions**, sélectionnez les permissions nécessaires pour gérer les propriétés de base et les propriétés des informations d’identification des inscriptions d’applications.
4. Tout d’abord, entrez « informations d’identification » dans la barre de recherche et sélectionnez la permission `microsoft.directory/applications/credentials/update`.
5. Ensuite, entrez « de base » dans la barre de recherche, sélectionnez l’autorisation `microsoft.directory/applications/basic/update`, puis **Suivant**.
6. Sur l’onglet **Vérifier + Créer**, vérifiez les permissions, puis sélectionnez **Créer**.

Votre rôle personnalisé s’affiche dans la liste des rôles disponibles à attribuer.


## Exercice - Gérer les rôles d’utilisateurs

Vous devez attribuer des autorisations supplémentaires à l’un de vos administrateurs nouvellement créés. Dans cet exercice, vous allez créer un compte d'utilisateur à utiliser dans les exercices.

### Créer un compte Azure et ajouter des licences d'essai Entra ID Premium P2

Cet exercice, comme les autres de ce parcours d'apprentissage, exige un abonnement Azure. Utilisez celui dont vous disposez déjà, ou inscrivez-vous à un compte d'essai Azure. Si vous disposez déjà de votre propre abonnement Azure, vous pouvez ignorer cette tâche et passer à la suivante.

1. Dans un navigateur web, accédez au [portail Microsoft Azure](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
2. Faites défiler la page pour découvrir tous les avantages et les services gratuits disponibles.
3. Sélectionnez **Démarrer gratuitement**.
4. Utilisez l’Assistant pour vous inscrire à votre abonnement à la version d’évaluation d’Azure.
5. Vous avez besoin d'une licence Entra ID P2 pour effectuer certains exercices. Dans l'organisation que vous avez créée, recherchez et sélectionnez Entra ID.
6. Sélectionnez **Licences** dans le menu.
7. Dans le menu **Tâches rapides** sur la droite de la page Licences - Vue d’ensemble, sélectionnez **Obtenir un essai gratuit**
8. Sous Bien démarrer avec Entra ID, sélectionnez **Obtenir un essai gratuit pour Entra ID Premium**.
9. Dans le volet Activer, sous **Entra ID PREMIUM P2**, sélectionnez **Essai gratuit**, puis **Activer**.
10. Dans le menu de navigation, sélectionnez **Vue d’ensemble**.
11. Actualisez le navigateur jusqu'à ce qu’Entra ID Premium P2 s'affiche sous le nom de l'organisation. Cela peut prendre quelques minutes.
12. Il se peut que vous deviez vous déconnecter et vous reconnecter à Microsoft Azure si vous rencontrez des problèmes avec les fonctionnalités attendues qui ne sont pas disponibles.

### Ajouter un nouvel utilisateur

Créons maintenant un compte d’utilisateur.

1. Se connecter au [Centre d'administration Entra](https://entra.microsoft.com/) en tant qu'administrateur général
2. Dans le menu de gauche, développez la section **Identité**.
3. Dans le menu de navigation de gauche, sous **Utilisateurs**, sélectionnez **Tous les utilisateurs**, puis **Nouvel utilisateur**.
4. Créez un utilisateur à l’aide des informations suivantes :     **Paramètre**  **Valeur**     Nom d’utilisateur principal AdeleV   Pseudonyme de messagerie (vous devrez peut-être décocher la case *Dériver du nom principal de l'utilisateur*. AdeleV   Nom complet Adele Vance   Mot de passe Pass@word1
5. Sélectionnez **Créer**. L’utilisateur est maintenant créé et inscrit auprès de votre organisation.

### Attribuer un rôle à un utilisateur

En utilisant Entra ID, vous pouvez désigner des administrateurs limités pour gérer les tâches d'identité dans des rôles moins privilégiés. Les administrateurs peuvent se voir attribuer différentes responsabilités : ajouter ou changer des utilisateurs, attribuer des rôles d’administrateur, réinitialiser les mots de passe utilisateur, gérer les licences utilisateur et gérer les noms de domaine.

1. Dans Entra ID, sur l’écran Tous les utilisateurs, sélectionnez **Adele Vance**.
2. Dans la page **Profil de l’utilisateur**, sélectionnez **Rôles affectés**. La page **Rôles affectés** s’affiche.
3. Sélectionnez **Ajouter des affectations**, sélectionnez le rôle à attribuer à l’utilisateur (par exemple, *Administrateur d’application*), puis sélectionnez **Ajouter**.
4. Sélectionnez **+ Ajouter une attribution.**

Le rôle Administrateur d’application qui vient d’être attribué s’affiche dans la page **Rôles affectés** de l’utilisateur.

### Supprimer une attribution de rôle

Si vous devez supprimer l’attribution de rôle d’un utilisateur, vous pouvez également le faire à partir de la page **Rôles affectés**.

#### Pour supprimer une attribution de rôle d’un utilisateur

1. Dans Entra ID, sélectionnez **Utilisateurs – Tous les utilisateurs**, puis sélectionnez l'utilisateur dont l'attribution de rôle a été supprimée. Par exemple, *Adele Vance*.
2. Sélectionnez **Rôles affectés**, puis sélectionnez le nom du rôle que vous souhaitez supprimer : `Application Administrator`.
3. Tout à droite de l’écran, sélectionnez **Supprimer**. Sélectionnez ensuite l’option **Oui** quand il vous est demandé de confirmer.

Le rôle Administrateur d’application est supprimé de l’utilisateur et n’apparaît plus dans la page **Adele Vance – Rôles affectés**.


## Configurer la délégation à l’aide d’unités administratives

Les unités administratives sont des ressources Entra ID qui peuvent servir de conteneurs pour d'autres ressources Entra. Une unité administrative peut contenir seulement des utilisateurs, des groupes et des appareils.

Les unités administratives limitent les autorisations d’un rôle en fonction du service auquel il appartient au sein de l’organisation. Par exemple, les unités administratives vous permettent de déléguer le rôle Administrateur du support technique aux spécialistes du support régional : ils ne s’occupent alors que des utilisateurs situés dans la région dont ils ont la charge. Vous pouvez gérer des unités administratives en utilisant le portail Azure, des applets de commande et des scripts PowerShell, ou Microsoft Graph.

#### Qu’est-ce qu’une unité administrative ?

Dans Entra ID, dans un contexte mono-locataire, si vous attribuez à un utilisateur un rôle d’administrateur, il est désormais administrateur de chaque utilisateur du locataire. Pensez toujours au principe de sécurité du privilège minimal : c’est toujours la meilleure façon d’accorder des responsabilités d’administration. Les unités administratives sont des conteneurs créés pour résoudre ce problème dans Entra ID. Si vous voulez qu’un administrateur d’utilisateurs puisse gérer seulement un ensemble spécifique d’utilisateurs et de groupes, disons gérer seulement les utilisateurs du département Recherche d’un hôpital, vous pouvez configurer une unité administrative. Au sein de cette unité administrative, vous ajoutez les utilisateurs et les groupes de l’équipe de recherche. Vous ajoutez ensuite un utilisateur spécifique au rôle Administrateur d’utilisateurs de l’unité administrative, puis vous le nommez Admin-for-research. Admin-for-research est en mesure de gérer les utilisateurs de l’unité administrative, mais pas sur l’ensemble du locataire, ce qui permet d’atteindre le principe du privilège minimum.

#### Quels sont les rôles d’administrateur disponibles pour une unité administrative ?

Vous pouvez avoir des utilisateurs dans les rôles suivants pour gérer votre unité administrative :

- Administrateur d’authentification
- Administrateur du support technique
- Administrateur de licence
- Administrateur de mots de passe
- Administrateur d’utilisateurs

Notes

Si vous êtes familiarisé avec Active Directory local, cette fonctionnalité a été gérée en configurant des unités d’organisation dans votre annuaire et en ajoutant vos utilisateurs à l’unité d’organisation.

### Planifier vos unités administratives

Vous pouvez utiliser les unités administratives pour regrouper logiquement des ressources Entra. Une organisation dont les membres du service informatique sont répartis dans le monde entier peut créer des unités administratives pour définir des limites géographiques. Autre scénario : dans le cas d’une organisation multinationale composée de plusieurs sous-organisations fonctionnant de manière semi-autonome, une unité administrative peut représenter chacune de ces sous-organisations.

Les critères de création d’unités administratives sont guidés par les exigences uniques d’une organisation. Les unités administratives constituent une façon courante de définir la structure des services Microsoft 365. Nous vous recommandons de préparer vos unités administratives en pensant à leur utilisation dans les services Microsoft 365. Vous pouvez tirer le meilleur parti des unités administratives quand vous pouvez associer des ressources communes à Microsoft 365 sous une unité administrative.

Vous pouvez vous attendre à ce que la création d’unités administratives au sein de l’organisation passe par les étapes suivantes :

1. **Adoption initiale** : votre organisation va commencer à créer des unités administratives en fonction de critères initiaux et le nombre d’unités administratives va augmenter à mesure que les critères sont affinés.
2. **Nettoyage** : Une fois que les critères sont définis, les unités administratives qui ne sont plus nécessaires sont supprimées.
3. **Stabilisation** : La structure organisationnelle est définie et le nombre d’unités administratives ne va pas changer de façon significative à court terme.

### Déléguer l’administration dans Entra ID

Croissance des organisations et complexité vont de pair. Une réponse courante est de réduire une partie de la charge de travail de gestion des accès avec des rôles d’administrateur Entra. Vous pouvez attribuer le plus petit des privilèges aux utilisateurs afin qu’ils puissent accéder à leurs applications et effectuer leurs tâches. De nombreuses raisons peuvent amener une organisation à opter pour une administration plus décentralisée.

Dans Entra ID, vous pouvez déléguer les autorisations de création et de gestion d’applications en procédant ainsi :

- Restriction des utilisateurs autorisés à créer des applications et à gérer les applications qu’ils créent. Par défaut dans Entra ID, tous les utilisateurs peuvent inscrire des inscriptions d’application et gérer tous les aspects des applications qu’ils créent. Vous pouvez restreindre cela en octroyant cette autorisation seulement à des personnes sélectionnées.
- Attribution d’un ou plusieurs propriétaires à une application. Une manière simple d'accorder à quelqu'un la capacité de gérer tous les aspects de la configuration d’Entra ID pour une application spécifique.
- Attribution d’un rôle d’administrateur intégré qui autorise l’accès à la gestion de la configuration dans Entra ID pour toutes les applications. La méthode recommandée consiste à accorder aux experts informatiques la gestion des autorisations de configuration des applications, sans leur donner accès aux autres parties d’Entra ID, qui ne sont pas liées à cette configuration.
- Créez un rôle personnalisé pour définir des autorisations spécifiques. Attribuez ensuite le rôle à un utilisateur pour affecter un propriétaire limité. Vous pouvez aussi affecter au niveau de l’étendue de l’annuaire - toutes les applications - en tant qu’administrateur limité.

Lors de l’octroi de l’accès, utilisez une des méthodes ci-dessus pour deux raisons. Tout d’abord, la délégation de la possibilité d’effectuer des tâches administratives réduit la surcharge administrative. Deuxièmement, l’utilisation d’autorisations limitées améliore votre position de sécurité et réduit le risque d’accès non autorisé.

### Planifier la délégation

Le développement d’un modèle de délégation qui répond à vos besoins demande du travail. Le développement d’un modèle de délégation étant un processus de conception itératif, nous vous suggérons de suivre ces étapes :

- Définir les rôles dont vous avez besoin
- Déléguer l’administration des applications
- Accorder la possibilité d’inscrire des applications
- Déléguer l’appartenance des applications
- Développer un plan de sécurité
- Établir des comptes d’urgence
- Sécuriser vos rôles d’administrateur
- Rendre l’élévation de privilège temporaire

### Définir des rôles

Déterminez les tâches d’annuaire effectuées par les administrateurs et comment elles sont mappées aux rôles. Chaque tâche doit être évaluée du point de vue de la fréquence, de l’importance et de la difficulté. Ces critères sont des aspects vitaux de la définition de tâche, car ils déterminent si une autorisation doit être déléguée :

- Les tâches que vous effectuez de façon routinière, qui présentent un risque limité et qui sont très faciles à effectuer sont d’excellents candidats à la délégation.
- Les tâches que vous effectuez rarement mais qui présentent un risque potentiels pour l’organisation et nécessitent des niveaux élevés de compétences doivent faire l’objet d’une attention particulière avant d’être déléguées. Au lieu de cela, vous pouvez temporairement élever un compte au rôle requis ou réattribuer la tâche.

### Déléguer l’administration des applications

La prolifération d’applications au sein de votre organisation peut restreindre votre modèle de délégation. S’il fait peser la gestion de l’accès aux applications sur l’administrateur général, sa surcharge est susceptible d’augmenter au fil du temps. Si vous avez accordé aux personnes le rôle Administrateur général pour des éléments tels que la configuration d’applications d’entreprise, vous pouvez désormais les décharger vers les rôles moins privilégiés suivants. Cette action permet d’améliorer votre situation de sécurité et de réduire le risque d’erreurs malheureuses. Les rôles d’administrateur d’application les plus privilégiés sont les suivants :

- Le rôle **Administrateur d’application**, qui permet de gérer toutes les applications de l’annuaire : inscriptions, paramètres d’authentification unique, gestion des licences, affectations d’utilisateurs et de groupes, paramètres de proxy d’application et consentement. Il n’accorde pas la possibilité de gérer l’accès conditionnel.
- Le rôle **Administrateur d’application cloud**, qui accorde toutes les capacités de l’administrateur d’application, à ceci près qu’il n’accorde pas l’accès aux paramètres de proxy d’application (car il n’a aucune autorisation locale).

### Déléguer l’inscription des applications

Par défaut, tous les utilisateurs peuvent créer des inscriptions d’application. Pour accorder de manière sélective la possibilité de créer des inscriptions d’application :

- Définissez le paramètre **Les utilisateurs peuvent inscrire des applications** sur Non dans **Paramètres utilisateur**.
- Affectez l’utilisateur au rôle Développeur d’applications.

Pour accorder de manière sélective la possibilité d’autoriser une application à accéder aux données :

- Définissez **Les utilisateurs peuvent donner leur consentement aux applications qui accèdent à des données d’entreprise en leur nom** sur Non dans les **Paramètres utilisateur** sous Applications d’entreprise
- Affectez l’utilisateur au rôle Développeur d’applications.

Quand un développeur d’applications crée une inscription d’application, il est automatiquement ajouté en tant que premier propriétaire.

### Déléguer l’appartenance des applications

Pour affiner la délégation de l’accès aux applications, vous pouvez attribuer la propriété à des applications d’entreprise spécifiques. Vous améliorez la prise en charge existante de l’affectation des propriétaires d’inscription d’application. La propriété est affectée par application d’entreprise dans l’écran Applications d’entreprise. L’avantage est que les propriétaires peuvent gérer uniquement les applications d’entreprise qu’ils possèdent. Par exemple, vous pouvez affecter un propriétaire pour l’application Salesforce ; ce propriétaire peut ainsi gérer l’accès à Salesforce et sa configuration, à l’exclusion de toute autre application. Une application d’entreprise peut avoir de nombreux propriétaires, et un utilisateur peut être le propriétaire de nombreuses applications d’entreprise. Il existe deux rôles de propriétaire d’application :

- Le rôle **Propriétaire d’application d’entreprise** accorde la possibilité de gérer les applications d’entreprise détenues par l’utilisateur, y compris les paramètres d’authentification unique, les affectations d’utilisateurs et de groupes, et l’ajout d’autres propriétaires. Il n’accorde pas la possibilité de gérer les paramètres de proxy d’application ou l’accès conditionnel.
- Le rôle **Propriétaire d’inscription d’application** accorde la possibilité de gérer les inscriptions d’application pour l’application dont l’utilisateur est propriétaire, y compris le manifeste d’application et l’ajout d’autres propriétaires.

### Développer un plan de sécurité

Entra ID fournit un guide complet pour planifier et exécuter un plan de sécurité sur vos rôles d’administrateur Entra, [Sécurisation de l’accès privilégié pour les déploiements hybride et cloud](https://learn.microsoft.com/fr-fr/azure/active-directory/roles/security-planning).

### Établir des comptes d’urgence

Pour conserver l’accès à votre magasin de gestion d’identité quand un problème survient, préparez des comptes d’accès d’urgence comme indiqué dans [Créer des comptes d’administration de l’accès d’urgence](https://learn.microsoft.com/fr-fr/azure/active-directory/roles/security-emergency-access).

### Sécuriser vos rôles d’administrateur

Les attaquants qui prennent le contrôle de comptes privilégiés peuvent causer des dégâts considérables. Protégez donc toujours ces comptes en premier. Utilisez la fonctionnalité Paramètres de sécurité par défaut, disponible pour toutes les organisations Entra. Les paramètres de sécurité par défaut appliquent l’authentification multifacteur sur les comptes Entra privilégiés.


## Analyser les autorisations de rôle Entra

Qu’est-ce qu’une autorisation ? La définition de l’autorisation dans le dictionnaire est **le consentement ou l’autorisation d’effectuer une action spécifique**. Dans Entra ID, vous avez des autorisations pour chacune des opérations que vous pouvez effectuer. L’autorisation peut aller de l’affichage de vos paramètres à la possibilité de modifier votre configuration. Ensuite, passez à l’octroi d’autorisations pour ajouter ou supprimer des utilisateurs, etc. Il existe deux endroits principaux où l’autorisation peut être attribuée : au niveau de l’utilisateur ou du groupe. Elle finit toutefois au final par passer par l’utilisateur. Lorsque vous gérez les utilisateurs, vous disposez à la fois d’un utilisateur membre et d’un utilisateur invité. Les autorisations par défaut pour l’utilisateur invité sont légèrement inférieures à celles d’un utilisateur membre.

#### Exemple des autorisations par défaut pour des utilisateurs

| **Utilisateurs membres** | **Utilisateurs invités** |
|---|---|
| Énumérer la liste de tous les utilisateurs et contacts | Lire ses propres propriétés |
| Inviter des utilisateurs | Inviter des utilisateurs |
| Peut créer la sécurité et les groupes Microsoft 365 | Peut rechercher des groupes non masqués par nom |
| Inscrire de nouvelles applications | Lire les propriétés des applications inscrites et d’entreprise |

Remarque

Il s’agit simplement d’un petit sous-ensemble, afin de montrer les différences. Si vous souhaitez obtenir la liste complète, consultez les [autorisations utilisateur par défaut](https://learn.microsoft.com/fr-fr/azure/active-directory/fundamentals/users-default-permissions).

#### Contrôle des autorisations - ajouter et restreindre

Vous pouvez utiliser les **Paramètres utilisateur** dans le menu Gérer d’Entra ID pour restreindre ou contrôler les autorisations par défaut des utilisateurs par défaut. Vous pouvez également utiliser des rôles et des administrateurs pour ajouter de nouvelles autorisations à vos utilisateurs et groupes. Utilisez toujours le concept de privilège minimum et assurez-vous que les utilisateurs ont uniquement les droits dont ils ont besoin. Dans les paramètres utilisateur, vous pouvez restreindre la capacité de l’utilisateur à :

- Inscrire des applications
- Accéder au portail Azure
- Bloquer les connexions LinkedIn
- Gérer les paramètres de la collaboration externe

En ajoutant des rôles à un compte d’utilisateur ou à un groupe donné, vous pouvez ajouter des autorisations aux utilisateurs membres, aux utilisateurs invités et aux principaux de service. L’ajout de rôles donne des autorisations pour effectuer des activités spécifiques. Les actions sont limitées, ce qui autorise la règle de privilège minimum.

#### Exploration des autorisations disponibles

Si possible, vous souhaitez accorder uniquement les autorisations minimales dont un utilisateur a besoin. Veillez donc à savoir quelles autorisations sont accordées lorsque vous attribuez un rôle. Vous pouvez voir la liste des autorisations dans la description de chaque rôle. Pour ouvrir, lancez Entra ID, puis ouvrez l'écran **Rôles et administrateurs**. Sélectionnez ensuite un rôle, puis ouvrez sa page de description dans le menu de points de suspension (...). Selon le rôle que vous avez choisi, vous verrez un grand ou petit nombre d’autorisations. Deux ensembles d’autorisations :

- Autorisations des rôles
- Autorisations de lecture de base du principal de service et de l’invité


## Configurer et gérer des domaines personnalisés

Un nom de domaine fait partie de l'identifiant de nombreuses ressources Entra ID : nom d'utilisateur ou adresse e-mail d'un utilisateur, adresse d'un groupe, et parfois URI d'identification d'une application. Une ressource dans Entra ID peut inclure un nom de domaine appartenant à l'organisation qui contient la ressource. Seul un administrateur général peut gérer des domaines dans Entra ID.

### Définir le nom de domaine principal de votre organisation Entra

Lors de la création de l’organisation, le nom de domaine initial, par exemple « contoso.onmicrosoft.com », est également le nom de domaine principal.

Important

La personne qui crée le locataire est automatiquement définie comme administrateur général pour ce locataire. L’administrateur général peut ajouter des administrateurs au locataire. Lors de l’ajout de nouveaux administrateurs, utilisez toujours le principe du privilège minimum.

Le domaine principal est le nom de domaine par défaut pour un nouvel utilisateur lorsque vous créez un nouvel utilisateur. Le fait de définir un nom de domaine principal simplifie le processus permettant à un administrateur de créer des utilisateurs dans le portail. Pour modifier le nom de domaine principal, procédez comme suit :

1. Connectez-vous au [portail Azure](https://portal.azure.com/) avec un compte administrateur pour l’organisation.
2. Sélectionnez **Entra ID.**
3. Sélectionnez **Noms de domaine personnalisés**.
4. Sélectionnez le nom du domaine que vous souhaitez choisir comme domaine principal.
5. Sélectionnez la commande **Définir comme principal**. Confirmez votre choix lorsque vous y êtes invité.

Vous pouvez modifier le nom de domaine principal de votre organisation par n’importe quel domaine personnalisé vérifié qui n’est pas fédéré. La modification du domaine principal de votre organisation ne change pas le nom d’utilisateur des utilisateurs existants.

### Ajouter des noms de domaine personnalisés à votre organisation Entra

Vous pouvez ajouter jusqu’à 900 noms de domaine managé. Si vous configurez tous vos domaines pour la fédération avec Windows Server Active Directory, vous pouvez ajouter jusqu’à 450 noms de domaine dans chaque organisation.

### Ajouter des sous-domaines d’un domaine personnalisé

Si vous souhaitez ajouter un nom de sous-domaine, tel que « europe.contoso.com » à votre organisation, vous devez tout d’abord ajouter et vérifier le domaine racine, tel que « contoso.com ». Le sous-domaine est automatiquement vérifié par Entra ID. Pour voir le sous-domaine vérifié que vous avez ajouté, actualisez la liste des domaines dans le navigateur.

Si vous avez déjà ajouté un domaine contoso.com à une organisation Entra, vous pouvez également vérifier le sous-domaine europe.contoso.com dans une autre organisation Entra. Quand vous ajoutez le sous-domaine, vous êtes invité à ajouter un enregistrement TXT au fournisseur d’hébergement DNS.

### Que faire en cas de modification du bureau d’enregistrement DNS pour votre nom de domaine personnalisé ?

Si vous changez les registrars DNS, aucune tâche de configuration supplémentaire n'est nécessaire dans Entra ID. Vous pouvez continuer à utiliser le nom de domaine avec Entra ID sans interruption. Si vous utilisez votre nom de domaine personnalisé avec Microsoft 365, Intune ou d’autres services qui s’appuient sur des noms de domaine personnalisés dans Entra ID, consultez la documentation de ces services.

### Supprimer un nom de domaine personnalisé

Vous pouvez supprimer un nom de domaine personnalisé de votre Entra ID si votre organisation ne l'utilise plus, ou si vous devez l'utiliser avec un autre Entra ID.

Pour supprimer un nom de domaine personnalisé, vous devez d’abord vous assurer qu’aucune des ressources de votre organisation ne s’appuie sur le nom de domaine. Vous ne pouvez pas supprimer un nom de domaine de votre organisation si :

- L’utilisateur dispose d’un nom d’utilisateur, d’une adresse de messagerie ou d’une adresse de proxy qui incluent le nom de domaine.
- Le groupe dispose d’une adresse de messagerie ou d’une adresse de proxy qui incluent le nom de domaine.
- Toute application de votre ID Entra a un URI d’ID d’application qui inclut le nom de domaine.

Vous devez modifier ou supprimer une ressource de ce type dans votre organisation Entra avant de pouvoir supprimer le nom de domaine personnalisé.

#### Option ForceDelete

**ForceDelete** peut être utilisé pour supprimer un nom de domaine dans le Centre d'administration Entra ou en utilisant l'API Microsoft Graph. Ces options utilisent une opération asynchrone : toutes les références au nom de domaine personnalisé, comme « user@contoso.com », sont mises à jour vers le nom de domaine par défaut initial, comme « user@contoso.onmicrosoft.com ».

Pour appeler **ForceDelete** dans le portail Azure, le nom de domaine doit compter moins de 1000 références. Toutes les références dans lesquelles Exchange est le service d’approvisionnement doivent d’abord être mises à jour ou supprimées dans le Centre d’administration Exchange. Les groupes de sécurité activés pour Courrier Exchange et les listes distribuées sont incluses. En outre, l’opération **ForceDelete** échoue si l’un des énoncés suivants est vrai :

- Vous avez acheté un domaine par le biais des services d’abonnement de domaine Microsoft 365
- Vous êtes un partenaire administrant pour le compte d’une autre organisation cliente

Les actions suivantes sont effectuées dans le cadre de l’opération **ForceDelete** :

- Renommage des éléments UPN, EmailAddress et ProxyAddress des utilisateurs avec des références au nom de domaine personnalisé vers le nom de domaine par défaut initial.
- Renommage de l’élément EmailAddress des groupes avec des références au nom de domaine personnalisé vers le nom de domaine par défaut initial.
- Renommage des éléments identifierUris des applications avec des références au nom de domaine personnalisé vers le nom de domaine par défaut initial.

Une erreur est renvoyée quand :

- Le nombre d’objets à renommer est supérieur à 1 000
- L'une des applications à renommer est une application multilocataire


## Configurer les paramètres au niveau du locataire

Les paramètres au niveau du locataire sont des options de configuration qui s’appliquent à toutes les ressources au sein de votre locataire, comme le nom l’indique. Ces options pour l’ensemble des locataires sont définies à des emplacements spécifiques, pour contrôler l’apparence et la configuration de votre locataire et de ses membres. Les options de menu ci-dessous sont basées sur le Centre d'administration Entra.

Option pour l’ensemble des locataires

- **Propriétés du client**
  - Identité – Page de présentation – Propriétés
  - Où vous donnez le nom de votre répertoire et vous définissez des valeurs comme le contact principal

- **Paramètres utilisateur**
  - Identité – Utilisateurs – Paramètres utilisateur
  - Où vous définissez les droits globaux de vos utilisateurs, comme l’inscription des applications

- **Paramètres de collaboration externe**
  - Identité – I externe – Paramètres utilisateur – Gérer la collaboration externe
  - Où vous définissez quelles tâches les utilisateurs invités externes peuvent effectuer, comme inviter d’autres utilisateurs invités

### Configurer des paramètres utilisateur au niveau locataire

Dans Entra ID, tous les utilisateurs bénéficient d’un ensemble d’autorisations par défaut. L’accès d’un utilisateur se compose du type d’utilisateur, de ses attributions de rôles et de sa possession d’objets individuels. Dans Entra ID, il n’est possible de modifier les autorisations d’utilisateur par défaut que dans les paramètres utilisateur.

#### Utilisateurs membres et utilisateurs invités

Le jeu d’autorisations par défaut reçu varie selon que l’utilisateur est un membre natif du locataire (utilisateur membre) ou est invité depuis un autre annuaire en tant qu’invité Collaboration B2B (utilisateur invité).

- Les utilisateurs membres peuvent inscrire des applications, gérer leurs numéro de téléphone mobile et photo de profil, changer leur mot de passe et inviter des invités B2B. En outre, les utilisateurs peuvent lire toutes les informations d’annuaire (à quelques exceptions près).
- Les utilisateurs invités disposent d'autorisations d'annuaire limitées. Il peut gérer son propre profil, changer son propre mot de passe et récupérer des informations sur d’autres utilisateurs, groupes et applications. En revanche, il ne peut pas lire toutes les informations de l’annuaire. Par exemple, les utilisateurs invités ne peuvent pas énumérer la liste de tous les utilisateurs, groupes et autres objets d’annuaire. Les invités peuvent être ajoutés à un rôle d’administrateur, bénéficiant ainsi des autorisations de lecture et d’écriture complètes contenues dans le rôle. Les invités peuvent également inviter d’autres invités.

Les autorisations par défaut ci-dessous des utilisateurs membres peuvent être restreintes comme suit :

| **Permission** | **Explication du paramètre** |
|---|---|
| Les utilisateurs peuvent inscrire l’application | Par défaut, les utilisateurs membres peuvent inscrire des applications. |
|   | Définir cette option sur Non empêche les utilisateurs de créer des inscriptions d’applications. La capacité peut ensuite être redonnée à des personnes spécifiques en les ajoutant au rôle Développeur d’applications. |
| Limiter l’accès au portail d’administration Entra | En définissant cette option sur Non, les non-administrateurs peuvent utiliser le portail d'administration d’Entra pour lire et gérer les ressources d’Entra. Oui restreint l'accès de tous les non-administrateurs aux données d’Entra dans le portail d'administration. |
|   | Ce paramètre ne limite pas l'accès aux données Entra à l'aide de PowerShell ou d'autres clients comme Visual Studio. Lorsque ce paramètre est défini sur Oui, il permet d'accorder à un utilisateur spécifique non-administrateur la possibilité d'utiliser le portail d'administration d’Entra en lui attribuant tout rôle administratif notamment le rôle de lecteurs d'annuaire. |
|   | Ce rôle permet de lire les informations de base des annuaires, ce que les utilisateurs membres peuvent faire par défaut (les invités et les principaux de service ne le peuvent pas). |

#### Se connecter avec LinkedIn

Avec plus de 500 millions de membres dans le monde entier, LinkedIn est la source la plus vaste et la plus fiable d’identités professionnelles. Utilisez cette puissance pour améliorer l’expérience de connexion de vos sites et applications.

Utilisez la connexion avec LinkedIn pour :

- Réduire la friction et obtenir davantage de connexions en permettant aux membres de se connecter avec LinkedIn, sans avoir à créer un nouveau compte.
- Réduisez les coûts et le temps associés à l’implémentation de votre propre gestion des connexions, des identités et des profils, et de la gestion des mots de passe.
- Personnaliser vos sites et applications avec les derniers profils des membres.

#### Gérer les paramètres de sécurité par défaut

La gestion de la sécurité peut s’avérer ardue lorsque les attaques courantes liées aux identités, telles que la pulvérisation de mot de passe, la relecture et le hameçonnage, deviennent monnaie courante. Les paramètres de sécurité par défaut facilitent la protection de votre organisation contre ces attaques avec des paramètres de sécurité préconfigurés :

- Exiger de tous les utilisateurs qu'ils s'inscrivent à l'authentification multifacteur (MFA).
- Exigez des administrateurs qu’ils effectuent l’authentification multifacteur.
- En restreignant les protocoles d’authentification hérités.
- Exigez des utilisateurs qu’ils effectuent l’authentification multifacteur, lorsque cela est nécessaire.
- En protégeant des activités privilégiées, telles que l’accès au Portail Azure.

#### Disponibilité

Microsoft rend les **Paramètres de sécurité par défaut** disponibles pour tous. Le but est de s’assurer que toutes les organisations bénéficient d’un niveau de sécurité de base activé, sans coût supplémentaire.

### Configurer les options des utilisateurs externes

Ici, vous configurez les actions que les utilisateurs externes peuvent effectuer lorsqu’ils utilisent les ressources cloud de votre locataire.

- **Accès utilisateur invité** : les utilisateurs invités peuvent disposer de droits, par exemple pour travailler presque comme un utilisateur complet ou pour uniquement consulter leur propre contenu.
- **Paramètres d’invitation des invités** : qui peut inviter des personnes à rejoindre l’organisation, des invités eux-mêmes aux seuls administrateurs.
- **Libre-service pour les invités** : autoriser les invités à participer aux options en libre-service pour les utilisateurs.

### Configurer les propriétés du locataire pour le répertoire

Choisissez les valeurs de base qui définissent l'apparence de votre locataire dans Entra ID.

- **Nom** : nom convivial de votre locataire, à utiliser dans le portail Azure
- **Pays ou région** : emplacement de votre société principale et des centres de données Azure utilisés
- **Langue de la notification** : langue utilisée pour envoyer les notifications et les alertes
- **ID de locataire** : identificateur unique de votre locataire, utilisé par programmation
- **Contact technique** – Contact principal pour le locataire (par défaut, il s'agit de l'utilisateur qui a créé le locataire)
- **Contact mondial pour la confidentialité** : utilisateur ou alias à contacter pour les problèmes de confidentialité
- **URL de la déclaration de confidentialité** : lien vers une page web ou un fichier PDF contenant les règles de confidentialité de vos solutions cloud


## Exercice - Définition des propriétés au niveau du locataire

Votre objectif est de modifier le nom complet du locataire.

1. Accédez au [portail Azure](https://portal.azure.com/) et connectez-vous à l’aide d’un compte Administrateur pour l’annuaire.
2. Sélectionnez l'icône hamburger du menu **Afficher le portail**, puis sélectionnez **Entra ID**.
3. Dans le volet de navigation de gauche, dans la section Gérer, sélectionnez **Propriétés**.
4. Dans la zone **Nom**, modifiez le nom du locataire. Par exemple, Contoso Marketing Company peut être remplacé par Contoso Marketing Company 2.
5. Sélectionnez **Enregistrer** pour mettre à jour les propriétés du locataire.

#### Rechercher le pays / la région associé(e) à votre locataire

1. À l'écran **Entra ID**, dans la section Gérer, sélectionnez **Propriétés**.
2. Sous **Propriétés du locataire**, recherchez **Pays / région** et passez en revue les informations.  Important Le pays / la région est spécifié(e) lors de la création du locataire. Ce paramètre ne peut pas être modifié ultérieurement.

#### Rechercher l’emplacement associé à votre locataire

Le pays/la région est mentionné(e) dans la boîte de dialogue Propriétés d’Entra ID. Il en va de même pour les informations relatives à l'emplacement.

1. Dans l’écran **Propriétés**, sous **Propriétés du locataire**, recherchez l’**Emplacement** et passez en revue les informations.

#### Rechercher l’ID du locataire

Les abonnements Azure ont une relation d’approbation avec Entra ID. Entra ID est utilisé pour authentifier les utilisateurs, les services et les appareils dans le cadre de l'abonnement. Chaque abonnement est associé à un ID de locataire et il existe plusieurs façons de trouver l’ID de locataire pour votre abonnement.

1. À l'écran **Entra ID**, dans la section Gérer, sélectionnez **Propriétés**.
2. Sous **Propriétés du locataire**, localisez **ID du locataire**. ID de locataire est l’identificateur univoque de votre locataire.

#### Modifier le contact technique, ajouter vos informations de confidentialité, votre contact international chargé de la confidentialité et l’URL de la déclaration de confidentialité

Microsoft vous recommande vivement d’ajouter votre contact international chargé de la confidentialité et la déclaration de confidentialité de votre organisation, pour que vos employés internes et invités externes puissent consulter vos stratégies. Étant donné que les déclarations de confidentialité sont particulièrement créées et adaptées à chaque entreprise, nous vous recommandons vivement de contacter un conseil juridique à des fins d’assistance.

Notes

Pour plus d’informations sur l’affichage ou la suppression des données personnelles, consultez [Requêtes DSR (droits de la personne concernée) Azure](https://learn.microsoft.com/fr-fr/microsoft-365/compliance/gdpr-dsr-azure). Pour plus d’informations, consultez le [portail d’approbation de services](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

Vous ajoutez les informations de confidentialité de votre organisation dans la zone **Propriétés** d’Entra ID. Accéder à la zone Propriétés et ajouter vos informations de confidentialité :

1. À l'écran **Entra ID**, dans la section Gérer, sélectionnez **Propriétés**.

1. Ajoutez vos informations de confidentialité pour vos employés :

- **Contact technique**. Tapez l’adresse e-mail de la personne à contacter pour obtenir un support technique au sein de votre organisation.
- **Contact international chargé de la confidentialité**. Tapez l’adresse e-mail de la personne à contacter pour toute question concernant la confidentialité des données personnelles. Cette personne est également la personne que Microsoft contacte en cas de fuite de données. S’il n’y a aucune personne répertoriée ici, Microsoft contacte l’administrateur propriétaire du locataire.
- **URL de la déclaration de confidentialité**. Tapez le lien vers le document de votre organisation qui décrit la façon dont elle gère la confidentialité des données des utilisateurs internes et invités externes.

1. Sélectionnez **Enregistrer**.


## Contrôle des connaissances

Choisissez la meilleure réponse à chacune des questions ci-dessous.

### Contrôler vos connaissances


## Récapitulatif et ressources

Maintenant que vous avez passé en revue ce module, vous pouvez :

- Configurer et gérer les rôles Entra
- Configurer et gérer des domaines personnalisés.
- Évaluez les autorisations en fonction des attributions de rôles et des paramètres.
- Configurer la délégation à l’aide d’unités administratives.
- Configurez les paramètres à l’échelle du locataire.

### Ressources

Utilisez ces ressources pour approfondir vos connaissances.

- Pour en savoir plus sur les rôles qui gèrent les ressources Azure et sur ceux qui gèrent les ressources Entra, consultez [les rôles d’administrateur d’abonnement Classic, les rôles Azure et les rôles Entra](https://learn.microsoft.com/fr-fr/azure/role-based-access-control/rbac-and-directory-admin-roles).
- Pour plus d’informations sur les rôles, consultez [Comprendre les définitions de rôles Azure](https://learn.microsoft.com/fr-fr/azure/role-based-access-control/role-definitions).
- Pour plus d’informations sur l’utilisation de PIM, consultez [Privileged Identity Management](https://learn.microsoft.com/fr-fr/azure/active-directory/privileged-identity-management/).
- Les guides pas à pas suivants fournissent des informations sur la façon dont vous pouvez utiliser l’accès conditionnel pour configurer des stratégies équivalentes à ces stratégies activées par défaut de sécurité :
  - [Exiger l’authentification multifacteur pour les administrateurs](https://learn.microsoft.com/fr-fr/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa)
  - [Exiger l’authentification multifacteur pour la gestion Azure](https://learn.microsoft.com/fr-fr/azure/active-directory/conditional-access/howto-conditional-access-policy-azure-management)
  - [Bloquer l’authentification héritée](https://learn.microsoft.com/fr-fr/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)
  - [Exiger l’authentification multifacteur pour tous les utilisateurs](https://learn.microsoft.com/fr-fr/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa)
  - [Exiger l’inscription MFA](https://learn.microsoft.com/fr-fr/azure/active-directory/identity-protection/howto-identity-protection-configure-mfa-policy) : cela nécessite la fonctionnalité Entra Identity Protection, intégrée à Entra ID Premium P2.


---

# Créer, configurer et gérer des identités

_https://learn.microsoft.com/fr-fr/training/modules/create-configure-manage-identities/_


## Introduction

Transférer des charges de travail sur le cloud ne se résume pas à déplacer des serveurs, des sites web et des données. Les entreprises doivent réfléchir à la façon de sécuriser ces ressources en définissant des utilisateurs autorisés. Ensuite, les entreprises doivent s’assurer que les utilisateurs accèdent uniquement aux données dont ils ont besoin, qu’ils ne sont autorisés que pour les services mis à leur disposition et qu’ils effectuent uniquement les opérations qui leur sont autorisées. L’accès aux charges de travail basées sur le cloud est contrôlé de deux manières centralisées. Tout d’abord, en fournissant une identité définitive pour chaque utilisateur qu’il utilise pour chaque service. Deuxièmement, en veillant à ce que les employés et les fournisseurs aient suffisamment d’accès pour accomplir leur travail.

Entra ID, le service de gestion des identités et des accès basé sur le cloud Microsoft facilite la résolution de ces problèmes. Entra ID fournit une gestion des identités de bout en bout, notamment l’authentification unique et l’authentification multifacteur pour protéger vos utilisateurs et vos données. Dans ce module, vous allez découvrir les bases de la création, de la configuration et de la gestion des utilisateurs et des groupes d’utilisateurs. Vous apprenez également à gérer les licences et l’inscription des appareils.

### Objectifs d’apprentissage

Dans ce module, vous allez :

- Créer, configurer et gérer des utilisateurs
- Créer, configurer et gérer des groupes
- Gestion des licences
- Configurer et gérer l’inscription des appareils
- Explorer les attributs de sécurité personnalisés et l’approvisionnement automatique

### Prerequisites

- Compréhension de base de la gestion des identités
- Une expérience avec Active Directory est un atout.
- Expérience avec confiance zéro utile


## Créer, configurer et gérer des utilisateurs

Chaque utilisateur qui a besoin d’accéder aux ressources a besoin d’un compte d’utilisateur dans Entra ID. Un compte d’utilisateur contient toutes les informations nécessaires pour authentifier l’utilisateur pendant le processus d’authentification. Une fois authentifié, Entra ID génère un jeton d’accès pour autoriser l’utilisateur et déterminer les ressources auxquelles il peut accéder et ce qu’il peut faire avec ces ressources.

Vous utilisez le **Centre d’administration Entra** pour utiliser des objets utilisateur. N’oubliez pas que vous ne pouvez utiliser qu’un seul répertoire à la fois. Vous pouvez utiliser le panneau **Annuaire + Abonnement** pour changer de répertoires. Le centre d’administration dispose également d’un bouton **Changer de répertoire** dans la barre d’outils, ce qui permet de basculer facilement vers un autre répertoire disponible.

### Afficher les utilisateurs

Pour afficher les utilisateurs D’Entra, sélectionnez l’entrée **Utilisateurs** sous **Identité**, puis ouvrez la vue **Tous les utilisateurs** . Prenez une minute pour accéder au Centre d’administration et afficher vos utilisateurs. Notez la colonne **Type d’utilisateur** pour afficher les membres et les invités, comme le montre la figure suivante.

En règle générale, Entra ID définit les utilisateurs selon trois catégories :

- **Identités cloud** : ces utilisateurs existent uniquement dans l’ID Entra. Par exemple, ce sont les comptes d’administrateur et les utilisateurs que vous gérez vous-même. Leur source est **l’ID Entra** ou **l’annuaire Entra externe** si l’utilisateur est défini dans une autre instance Entra, mais a besoin d’accéder aux ressources d’abonnement contrôlées par ce répertoire. Quand ces comptes sont retirés de l’annuaire principal, ils sont supprimés.
- **Identités synchronisées dans l’annuaire** : ces utilisateurs existent dans un Active Directory local. Une activité de synchronisation permet à ces utilisateurs d’entrer dans l’ID Entra. **Entra Cloud Sync** est l’outil de synchronisation recommandé pour la plupart des organisations : il utilise un agent géré par le cloud léger et prend en charge plusieurs forêts déconnectées. **Entra Connect Sync** reste disponible pour des scénarios complexes tels que la synchronisation d’appareils ou les groupes avec plus de 50 000 membres. Leur source est **Windows Server AD**.
- **Utilisateurs invités** : ces utilisateurs existent en dehors de votre organisation. Par exemple, les comptes d’autres fournisseurs de cloud et comptes Microsoft. Leur source est **Utilisateur invité**. Ce type de compte est utile lorsque des fournisseurs externes ou des sous-traitants ont besoin d’accéder aux ressources de votre organisation. Une fois que le travail de ces collaborateurs est terminé, vous pouvez supprimer le compte et tous les accès associés.


## Exercice - attribuer des licences aux utilisateurs

**Besoins pour l'environnement d'exercice** : ce laboratoire suppose que vous disposez d'un tenant Entra de base avec des droits d'administrateur d'utilisateur minimum pour le terminer. Vous pouvez obtenir un abonnement d’essai gratuit pour [essayer Azure gratuitement](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).

### Créer un utilisateur dans l’ID Entra

Vous pouvez ignorer la création de cet utilisateur si vous avez créé le même utilisateur dans le module précédent.

1. Accédez au menu Identité dans le [Centre d’administration Entra](https://entra.microsoft.com/).
2. Dans le volet de navigation gauche, sous Sélectionner **Utilisateurs**, puis **Tous les utilisateurs.**
3. Dans la page Utilisateurs, dans le menu, sélectionnez + **Nouvel utilisateur** et **Créez un utilisateur**.
4. Créez un utilisateur à l’aide des informations suivantes :     **Setting**  **Value**     Nom d’utilisateur principal ChrisG   Name Chris Green   Prénom Chris   Nom Green   Password composez un mot de passe unique
5. Une fois terminé, vérifiez que le compte de Chris Green est affiché dans la liste **Tous les utilisateurs** .

### Créer un groupe de sécurité dans Entra ID

1. Accédez à l’écran du Centre d’administration Entra.
2. Dans le volet de navigation gauche, sous **Identité**, sélectionnez **Groupes** , puis **Tous les groupes**.
3. Dans l’écran Groupes, dans le menu, sélectionnez **Nouveau groupe**.
4. Créez un nouveau groupe à l’aide des informations suivantes :     **Setting**  **Value**     Type de groupe Security   Nom du groupe Marketing   Type d’appartenance Assigned   Owners Attribuer votre propre compte d’administrateur en tant que propriétaire du groupe   Members Chris Green
5. Une fois terminé, vérifiez que le groupe nommé **Marketing** est affiché dans la liste **Tous les groupes** .

### Attribuer une licence à un groupe

L’attribution de licences à des groupes est gérée via le Centre d’administration Microsoft 365.

1. Accédez au Centre d'administration Microsoft 365 sur [https://admin.microsoft.com](https://admin.microsoft.com).
2. Sélectionnez **Facturation** dans le menu de gauche.
3. Sélectionnez **Licences**.
4. Dans la liste des licences disponibles, sélectionnez-en une.
5. Sélectionnez **Groupes** dans la liste en haut de l’écran.
6. Dans la page Groupes, sélectionnez **+ Attribuer une licence**.
7. Recherchez et sélectionnez le groupe **Marketing** que vous avez créé précédemment.
8. Sélectionnez le bouton **Affecter** en bas de la boîte de dialogue.
9. Vous devez recevoir un message indiquant que les licences ont été correctement attribuées.

### Restaurer ou supprimer un utilisateur récemment supprimé avec l’ID Entra

Lorsque vous supprimez un utilisateur, son compte reste à l’état suspendu pendant 30 jours. Pendant ces 30 jours, le compte de l’utilisateur peut être restauré, avec l’ensemble de ses propriétés. Une fois cette fenêtre de 30 jours écoulée, le processus de suppression définitive est démarré automatiquement.

Vous pouvez afficher vos utilisateurs pouvant être restaurés, restaurer un utilisateur supprimé ou supprimer définitivement un utilisateur à l’aide de l’interface utilisateur Entra ID.

Important

Vous ne pouvez pas restaurer un utilisateur supprimé définitivement.

### Autorisations requises

Vous devez avoir l’un des rôles suivants pour restaurer ou supprimer définitivement des utilisateurs.

- Global administrator
- Support de niveau 1 partenaire
- Support de deuxième niveau des partenaires
- Administrateur d’utilisateur


## Exercice - Supprimer ou restaurer des utilisateurs supprimés

**Besoins pour l'environnement d'exercice** : ce laboratoire suppose que vous disposez d'un tenant Entra de base avec des droits d'administrateur d'utilisateur minimum pour le terminer. Vous pouvez obtenir un abonnement d’essai gratuit à [l’adresse Essayer Microsoft Azure gratuitement](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).

### Supprimer un utilisateur de l’ID Entra

1. Accédez au [Centre d’administration Entra](https://entra.microsoft.com/).
2. Dans le volet de navigation gauche, sous **Identité**, sélectionnez **Utilisateurs**.
3. Dans la liste **Utilisateurs** , activez la case à cocher permettant à un utilisateur de supprimer. Par exemple, sélectionnez **Chris Green**.  Tip La sélection d’utilisateurs dans la liste vous permet de gérer plusieurs utilisateurs en même temps. Si vous sélectionnez l’utilisateur, pour ouvrir la page de cet utilisateur, vous ne gérerez que cet utilisateur individuel.
4. Une fois le compte d’utilisateur sélectionné, dans le menu, sélectionnez **Supprimer l’utilisateur**.
5. Passez en revue la boîte de dialogue, puis sélectionnez **OK**.

### Restaurer un utilisateur supprimé.

Vous pouvez voir tous les utilisateurs qui ont été supprimés il y a moins de 30 jours. Ces utilisateurs peuvent être restaurés.

1. Dans la page Utilisateurs, dans le volet de navigation gauche, sélectionnez **Utilisateurs supprimés**.
2. Passez en revue la liste des utilisateurs supprimés et sélectionnez l’utilisateur que vous avez supprimé.  Important Par défaut, les comptes d’utilisateur supprimés sont supprimés définitivement de l’ID Entra automatiquement après 30 jours.
3. Dans le menu, sélectionnez **Restaurer l’utilisateur**.
4. Passez en revue la boîte de dialogue, puis sélectionnez **OK**.
5. Dans le volet de navigation gauche, sélectionnez **Tous les utilisateurs**.
6. Vérifiez que l’utilisateur a été restauré.


## Créer, configurer et gérer des groupes

Un groupe Entra permet de mieux organiser les utilisateurs, simplifiant ainsi la gestion de leurs autorisations. Les groupes permettent au propriétaire de la ressource (ou au propriétaire de l’annuaire Entra) d’attribuer un ensemble d’autorisations d’accès à tous les membres du groupe d’un seul coup, au lieu de fournir les droits un par un. Les groupes vous permettent de définir une limite de sécurité, puis d’ajouter et de supprimer des utilisateurs spécifiques pour accorder ou refuser l’accès avec un minimum d’effort. Mieux encore, Entra ID permet de définir l’appartenance en fonction de règles, telles que le service dans lequel un utilisateur travaille ou le titre du poste qu’il occupe.

Dans Entra ID, vous pouvez définir deux types de groupes.

- **Groupes de sécurité** : le type de groupes le plus courant et est utilisé pour gérer l’accès aux ressources partagées. Les membres d’un groupe de sécurité peuvent inclure des utilisateurs, des appareils et des principaux de service. Par exemple, vous pouvez créer un groupe de sécurité pour une stratégie de sécurité particulière. En procédant ainsi, vous pouvez accorder un ensemble d’autorisations à tous les membres en même temps, au lieu d’avoir à ajouter des autorisations à chaque membre individuellement. Cette option nécessite un administrateur Entra.
- **Groupes Microsoft 365** : offre des opportunités de collaboration en donnant aux membres l’accès à une boîte aux lettres partagée, un calendrier, des fichiers, un site SharePoint, etc. Cette option vous permet également d’accorder aux personnes extérieures à votre organisation l’accès au groupe. Cette option est disponible pour les utilisateurs et les administrateurs.

### Afficher les groupes disponibles

Vous pouvez afficher tous les groupes via l’élément **Groupes** sous **Identité** dans le Centre d’administration Entra. Un nouveau déploiement d’ID Entra n’a pas de groupes définis.

La deuxième caractéristique d’un groupe dont vous devez être conscient est le **type d’appartenance**. Cela spécifie comment les membres individuels sont ajoutés au groupe. Les trois types sont les suivants :

- **Affecté** : les membres sont ajoutés et gérés manuellement.
- **Utilisateur dynamique** : les utilisateurs sont ajoutés et supprimés automatiquement en fonction de règles qui évaluent les attributs utilisateur tels que le service, le titre du travail ou l’emplacement.
- **Appareil dynamique** : les appareils sont ajoutés et supprimés automatiquement en fonction des règles qui évaluent les attributs de l’appareil. S’applique uniquement aux groupes de sécurité ; Les groupes Microsoft 365 prennent en charge les utilisateurs dynamiques, mais pas les appareils dynamiques.

### Groupes dynamiques

Avec l’appartenance dynamique, Entra ID ajoute ou supprime automatiquement des utilisateurs ou des appareils d’un groupe en fonction des règles que vous définissez. Lorsque les attributs d’un membre changent (par exemple, un utilisateur passe dans un autre service), toutes les règles d’appartenance dynamique du locataire Azure AD sont réévaluées. L’utilisateur est alors ajouté aux groupes concernés ou en est supprimé.

L’appartenance dynamique nécessite une licence **Entra ID P1** (ou Intune pour l’Éducation pour les règles basées sur les appareils).

Par exemple, vous pouvez créer une règle qui ajoute automatiquement à un groupe de sécurité Marketing tous les utilisateurs dont l’attribut **Department** est égal à « Marketing », ce qui conserve l’appartenance à jour sans intervention manuelle.


## Exercice : Ajouter des groupes dans Entra ID

**Besoins pour l'environnement d'exercice** : ce laboratoire suppose que vous disposez d'un tenant Entra de base avec des droits d'administrateur d'utilisateur minimum pour le terminer. Vous pouvez obtenir un abonnement d’essai gratuit à [l’adresse Essayer Microsoft Azure gratuitement](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).

### Créer un groupe Microsoft 365 dans Entra ID

1. Accédez au [Centre d’administration Entra](https://entra.microsoft.com).
2. Dans le volet de navigation gauche, sous **Identité**, sélectionnez **Groupes**.
3. Sur la page Groupes, dans le menu, sélectionnez **Nouveau groupe**.
4. Créez un nouveau groupe à l’aide des informations suivantes :     **Paramètre**  **Valeur**     Type de groupe Microsoft 365   Nom du groupe Ventes Nord-Ouest   Type d’appartenance Attribué   Propriétaires Attribuer votre propre compte d’administrateur en tant que propriétaire du groupe   Membres Affecter un membre de ce groupe
5. Lorsque vous avez terminé, vérifiez que le groupe **Northwest Sales** est affiché dans la liste **Tous les groupes**.
6. Vous devez actualiser les **groupes Tous** quelques fois pour que le nouveau groupe s’affiche.


## Configurer et gérer l’inscription des appareils

Avec la prolifération des appareils de toutes formes et toutes tailles et du BYOD (apportez votre propre appareil), les professionnels de l’informatique sont confrontés à deux objectifs quelque peu contradictoires :

- Permettre aux utilisateurs finaux d’être productifs où et quand ils le veulent sur n’importe quel appareil
- Protéger les ressources de l’organisation

Pour protéger ces ressources, le personnel informatique doit tout d’abord gérer les identités des appareils. Le personnel informatique peut s’appuyer sur l’identité de l’appareil avec des outils tels que Microsoft Intune pour garantir le respect des normes de sécurité et de conformité. Entra ID active l’authentification unique sur des appareils, des applications et des services depuis n’importe où via ces appareils.

- Vos utilisateurs ont accès aux ressources de votre organisation dont ils ont besoin.
- Votre personnel informatique bénéficient des contrôles nécessaires pour sécuriser votre organisation.

### Appareils enregistrés auprès d’Entra

L’objectif des appareils inscrits auprès d’Entra est de fournir à vos utilisateurs un support pour des scénarios de BYOD ou d’appareils mobiles. Dans ces scénarios, un utilisateur peut accéder aux ressources contrôlées Entra ID de votre organisation à l’aide d’un appareil personnel.

| **Entra inscrit** | **Description** |
|---|---|
| Définition | Inscrit à Entra ID sans devoir utiliser un compte professionnel pour se connecter à l’appareil |
| Public visé en priorité | Applicable aux appareils BYOD (Bring Your Own Device) et mobiles |
| Propriété des appareils | Utilisateur ou organisation |
| Systèmes d’exploitation | Windows 10 ou version ultérieure, macOS 10.15 ou version ultérieure, iOS 15 ou version ultérieure, Android, Linux (Ubuntu 20.04/22.04/24.04 LTS, Red Hat Enterprise Linux 8/9 LTS) |
| Options de connexion de l’appareil | Informations d’identification locales de l’utilisateur final, Mot de passe, Windows Hello, Code confidentiel, Biométrie |
| Gestion des périphériques | Gestion des appareils mobiles (exemple : Microsoft Intune), Gestion des applications mobiles |
| Fonctionnalités clés | Authentification unique vers des ressources cloud, accès conditionnel lors de l’inscription dans Intune, accès conditionnel via une stratégie de protection des applications |

![Diagramme des appareils inscrits par Entra. Affiche un ordinateur portable et une cellule inscrits.](https://learn.microsoft.com../../wwl-sci/create-configure-manage-identities/media/azure-active-directory-registered-device.png)

Les appareils inscrits à Entra se connectent avec un compte local, tel qu’un compte Microsoft sur un appareil Windows 10 ou ultérieur. Ils disposent également d’un compte Entra attaché, qui donne accès aux ressources organisationnelles. L’accès aux ressources de l’organisation peut être limité davantage en fonction de ce compte Entra et des stratégies d’accès conditionnel appliquées à l’identité de l’appareil.

Les administrateurs peuvent sécuriser et contrôler davantage ces appareils inscrits auprès d’Entra à l’aide d’outils de GPM (gestion des périphériques mobiles) comme Microsoft Intune. Ces outils permettent d’appliquer les configurations requises par l’organisation, comme l’exigence du chiffrement du stockage, la complexité des mots de passe et la mise à jour des logiciels de sécurité.

L’inscription d’ID Entra peut être effectuée lors de l’accès à une application professionnelle pour la première fois ou manuellement à l’aide du menu Paramètres windows 10 ou Windows 11.

#### Scénarios pour les appareils inscrits

Un utilisateur membre de votre organisation souhaite accéder à des outils de messagerie, de déclaration de congés et d’inscription à des programmes d’avantages sociaux depuis son ordinateur domestique. Votre organisation dispose de ces outils derrière une stratégie d’accès conditionnel qui exige que l’accès se fasse à partir d’un appareil conforme à Intune. L’utilisateur ajoute son compte d’organisation et inscrit son PC personnel auprès d’Entra ID. Les stratégies Intune requises sont alors appliquées pour permettre à l’utilisateur d’accéder à ses ressources.

Un autre utilisateur souhaite accéder à son e-mail professionnel sur son téléphone Android personnel infecté par un kit racine. Votre entreprise a besoin d’un appareil conforme et a créé une stratégie de conformité Intune pour bloquer les appareils rootés. L’employé ne peut pas accéder aux ressources de l’organisation sur cet appareil.

### Appareils à jointure Entra

La jonction Entra est destinée aux organisations qui souhaitent adopter une approche cloud en priorité ou cloud uniquement. Toute organisation peut déployer des appareils joints Entra, quels que soient leur taille et leur secteur d’activité. Entra intégré permet d’accéder aux applications et aux ressources locales et cloud.

| **Joint à Entra** | **Description** |
|---|---|
| Définition | Joint uniquement à Entra ID nécessitant la connexion du compte d’organisation à l’appareil |
| Public visé en priorité | Approprié pour les organisations utilisant uniquement le cloud et pour les organisations hybrides |
| Propriété des appareils | Organisation |
| Systèmes d’exploitation | Tous les appareils Windows 10 et Windows 11 (à l’exception des éditions d’accueil) ; Machines virtuelles Windows Server 2019 et versions ultérieures dans Azure (Server Core non pris en charge) ; macOS 13 ou version ultérieure (préversion) |
| Gestion des périphériques | Gestion des périphériques mobiles (exemple : Microsoft Intune) |
| Fonctionnalités clés | Authentification unique pour les ressources cloud et locales, accès conditionnel, réinitialisation de mot de passe en libre-service et réinitialisation du code PIN Windows Hello |

Entra appareils joints sont connectés à l’aide d’un compte d’Entra organisationnel. L’accès aux ressources de l’organisation peut être limité davantage en fonction de ce compte Entra et des stratégies d’accès conditionnel appliquées à l’identité de l’appareil.

Les administrateurs peuvent sécuriser et contrôler davantage les appareils joints à Entra avec des outils GPM (gestion des périphériques mobiles) comme Microsoft Intune, ou, dans des scénarios de cogestion, avec Microsoft Endpoint Configuration Manager. Ces outils permettent d’appliquer les configurations requises par l’organisation, telles que le chiffrement du stockage, la complexité des mots de passe, ainsi que les installations et mises à jour de logiciels. Les administrateurs peuvent mettre des applications d’organisation à la disposition des appareils joints à Entra à l’aide de Configuration Manager.

La jonction Entra peut être effectuée à l’aide d’options en libre-service telles que l’expérience OOBE (Out of Box Experience), l’inscription en bloc ou Windows Autopilot.

Les appareils joints Entra peuvent conserver un accès avec authentification unique vers les ressources locales lorsqu’ils se trouvent sur le réseau de l’organisation. Les appareils joints à Entra s’authentifient auprès de serveurs locaux comme ceux pour des applications de fichiers, d’impression et autres.

#### Scénarios pour les appareils joints

Bien qu’Entra joint soit principalement destiné aux organisations qui n’ont pas d’infrastructure Windows Server Active Directory locale, vous pouvez certainement l’utiliser dans les scénarios où :

- Vous souhaitez passer à une infrastructure cloud avec Entra ID et un système de gestion des appareils mobiles comme Intune.
- Vous ne pouvez pas utiliser une jointure au domaine local, par exemple, si vous devez pouvoir contrôler des appareils mobiles tels que des tablettes et des téléphones.
- Vos utilisateurs ont principalement besoin d’accéder à Microsoft 365 ou d’autres applications SaaS intégrées à Entra ID.
- Vous souhaitez gérer un groupe d’utilisateurs dans Entra ID et non dans un répertoire Active Directory. Par exemple, ce scénario peut concerner les travailleurs saisonniers, les prestataires ou les étudiants.
- Vous souhaitez fournir des fonctionnalités de jointure aux travailleurs des succursales distantes avec une infrastructure locale limitée.

Vous pouvez configurer les appareils joints à Entra pour tous les appareils Windows 10 et Windows 11 à l’exception des éditions d’accueil.

L'objectif des appareils connectés à Entra est de simplifier :

- Déploiement de Windows sur des appareils appartenant au personnel
- Accès aux applications et ressources de l’organisation à partir de tout appareil Windows
- Gestion cloud des appareils professionnels
- Aux utilisateurs de se connecter à leurs appareils à partir de leurs comptes Entra ID ou Active Directory synchronisés professionnels ou scolaires.

![Diagramme des appareils joints à Entra connectés au cloud. Un ordinateur portable inscrit dans votre annuaire cloud.](https://learn.microsoft.com../../wwl-sci/create-configure-manage-identities/media/azure-active-directory-joined-device.png)

Entra Joined peut être déployé à l’aide de nombreuses méthodes différentes.

### Appareils hybrides joints à Entra

Depuis plus de dix ans, de nombreuses organisations utilisent la jonction de domaine à leur Active Directory local pour :

- Permettre aux services informatiques de gérer les appareils appartenant au personnel à partir d’un emplacement central.
- Permettre aux utilisateurs de se connecter à leurs appareils à partir de leurs comptes Active Directory professionnels ou scolaires.

En règle générale, les organisations disposant d’une empreinte locale s’appuient sur des méthodes de création d’images pour configurer les appareils. Elles utilisent souvent **Configuration Manager** ou une **stratégie de groupe** pour les gérer.

Si votre environnement a une empreinte AD locale et que vous souhaitez également bénéficier des fonctionnalités fournies par Entra ID vous pouvez implémenter des appareils hybrides joints à Entra. Il s’agit d’appareils joints à votre Active Directory local et inscrits auprès de votre répertoire Entra.

| **Hybrides joints à Entra** | **Description** |
|---|---|
| Définition | Joint à ad local et à Entra ID nécessitant un compte d’organisation pour se connecter à l’appareil |
| Public visé en priorité | Convient aux organisations hybrides disposant d’une infrastructure AD locale existante |
| Propriété des appareils | Organisation |
| Systèmes d’exploitation | Windows 10, Windows 11 (à l’exception des éditions d’accueil), Windows Server 2016, 2019 et 2022 |
| Options de connexion de l’appareil | Mot de passe ou Windows Hello Entreprise |
| Gestion des périphériques | Stratégie de groupe, Configuration Manager autonome ou cogestion avec Microsoft Intune |
| Fonctionnalités clés | Authentification unique pour les ressources cloud et locales, accès conditionnel, réinitialisation de mot de passe en libre-service et réinitialisation du code PIN Windows Hello |

![Diagramme du flux de processus des appareils joints à Entra hybrides. Un ordinateur portable est inscrit auprès d’un annuaire active directory local.](https://learn.microsoft.com../../wwl-sci/create-configure-manage-identities/media/azure-active-directory-hybrid-joined-device.png)

#### Scénarios pour les appareils joints hybrides

Utilisez des appareils joints hybrides Entra si :

- Vous disposez d’applications Win32 déployées sur ces appareils qui s’appuient sur l’authentification de l’ordinateur Active Directory.
- Vous souhaitez continuer à utiliser une Stratégie de groupe pour gérer la configuration des appareils.
- Vous souhaitez continuer à utiliser des solutions d’imagerie existantes pour déployer et configurer des appareils.

### Réécriture d'appareil – (plus pris en charge)

La réécriture d'appareil n’est plus prise en charge et n’est plus une approche recommandée pour les scénarios d'identité hybride. Il est remplacé par cloud **Kerberos Trust**, qui permet aux appareils joints à Entra et hybrides de s’authentifier auprès de ressources locales, sans réécrire les objets d’appareil dans Active Directory local.

Pour les organisations qui planifient de nouveaux déploiements hybrides, utilisez l’approbation Kerberos cloud pour activer l’authentification unique locale et Windows Hello Entreprise dans des environnements hybrides. Pour obtenir des conseils, consultez [Configurer Entra Kerberos pour l’authentification unique locale](https://learn.microsoft.com/fr-fr/entra/identity/authentication/howto-authentication-passwordless-security-key-on-premises) .


## Gestion des licences

Les services cloud payants Microsoft, comme Microsoft 365, Enterprise Mobility + Security, Dynamics 365 et d’autres produits similaires, requièrent des licences. Ces licences sont affectées à chaque utilisateur qui a besoin d’accéder à ces services. Pour gérer les licences, les administrateurs utilisent le [Centre d’administration Microsoft 365](https://admin.microsoft.com/) ou PowerShell et l’API Microsoft Graph. Entra ID est l’infrastructure sous-jacente qui prend en charge la gestion des identités de tous les services de cloud computing Microsoft. Entra ID stocke des informations sur les états d’affectation de licence pour les utilisateurs.

Sans licence basée sur un groupe, l’attribution de licences au niveau de l’utilisateur individuel rend la gestion à grande échelle difficile. Par exemple, un administrateur doit souvent écrire un script PowerShell complexe pour ajouter ou supprimer des licences utilisateur lors de modifications organisationnelles, comme l’arrivée ou le départ d’utilisateurs dans l’organisation ou dans un service. Ce script effectue des appels individuels au service cloud.

Pour relever ces défis, Entra ID inclut désormais des licences basées sur des groupes. Vous pouvez attribuer une ou plusieurs licences de produit à un groupe. Entra ID permet de garantir que les licences sont attribuées à tous les membres du groupe. Tous les nouveaux membres qui rejoignent le groupe se voient affecter les licences appropriées. Lorsqu’ils quittent le groupe, ces licences sont supprimées. Ceci élimine toute nécessité d’automatiser la gestion des licences avec PowerShell pour refléter les évolutions de la structure de l’organisation et des services utilisateur par utilisateur.

### Conditions requises pour la licence

Vous devez disposer de l’une des licences suivantes pour utiliser des licences basées sur des groupes :

- Abonnement payant ou d’essai pour Entra ID Premium P1 et versions ultérieures
- Édition payante ou d’essai Office 365 Entreprise E3 ou ultérieure

#### Nombre de licences requis

Pour tous les groupes auxquels une licence est attribuée, chaque membre unique doit également disposer d’une licence. Même si vous n’êtes pas obligé d’attribuer une licence à chaque membre du groupe, vous devez disposer de suffisamment de licences pour inclure tous les membres. Par exemple, si vous avez 1 000 membres uniques dans des groupes sous licence dans votre locataire, vous devez disposer d’au moins 1 000 licences pour respecter le contrat de licence.

### Features

Voici les principales fonctionnalités de la gestion des licences par groupe :

- Les licences peuvent être attribuées à n’importe quel groupe de sécurité dans Entra ID. Les groupes de sécurité peuvent être synchronisés à partir d’un site local à l’aide d’Entra Cloud Sync (recommandé) ou d’Entra Connect Sync. Vous pouvez également créer des groupes de sécurité directement dans l’ID Entra (également appelé groupes cloud uniquement) ou automatiquement via la fonctionnalité de groupe dynamique Entra.
- Lorsqu’une licence de produit est affectée à un groupe, l’administrateur peut désactiver un ou plusieurs plans de services dans le produit. En règle générale, cette affectation est effectuée lorsque l’organisation n’est pas encore prête à utiliser un service inclus dans un produit. Par exemple, l’administrateur peut affecter Microsoft 365 à un service, mais désactiver temporairement le service Viva Engage.
- Tous les services de cloud computing Microsoft nécessitant des licences au niveau des utilisateurs sont pris en charge. Cette prise en charge comprend tous les produits Microsoft 365, Enterprise Mobility + Security et Dynamics 365.
- Les licences basées sur les groupes sont actuellement disponibles uniquement via le [Centre d’administration Microsoft 365](https://admin.microsoft.com/).
- Entra ID gère automatiquement les modifications de licences qui résultent de modifications de l’appartenance aux groupes. En règle générale, les modifications de licence sont effectives quelques minutes après une modification d’appartenance.
- Un utilisateur peut être membre de plusieurs groupes dans lesquels des stratégies de licences sont spécifiées. Un utilisateur peut également disposer de licences affectées directement, en dehors de groupes. L’état utilisateur qui en résulte est une combinaison de toutes les licences de produits et services affectées. Si un utilisateur reçoit la même licence à partir de plusieurs sources, la licence n’est consommée qu’une seule fois.
- Dans certains cas, des licences ne peuvent pas être affectées à un utilisateur. Par exemple, il se peut qu’il n’y ait pas suffisamment de licences disponibles dans le locataire, ou que les services en conflit sont attribués en même temps. Les administrateurs ont accès aux informations sur les utilisateurs pour lesquels Entra ID n’a pas pu traiter entièrement les licences de groupe. Ils peuvent prendre des mesures correctives en fonction de ces informations.

Certains services Microsoft ne sont pas disponibles dans tous les emplacements. L’administrateur, avant d’attribuer une licence à un utilisateur, doit spécifier l’emplacement d’utilisation dans le profil utilisateur.

Pour l’affectation d’une licence à un groupe, tous les utilisateurs sans emplacement d’utilisation spécifié héritent de l’emplacement du répertoire. Si vous avez des utilisateurs dans plusieurs emplacements, nous vous recommandons de toujours définir l’emplacement d’utilisation dans le cadre de la création de votre utilisateur. L’emplacement d’utilisation permet de s’assurer que le résultat de l’attribution de licence est toujours correct et que les utilisateurs ne reçoivent pas de services dans des emplacements qui ne sont pas autorisés.


## Exercice - Modifier les affectations de licences de groupe

**Besoins pour l'environnement d'exercice** : ce laboratoire suppose que vous disposez d'un tenant Entra de base avec des droits d'administrateur d'utilisateur minimum pour le terminer. Vous pouvez obtenir un abonnement d’essai gratuit à [l’adresse Essayer Microsoft Azure gratuitement](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).

### Modifier une affectation de licence de groupe

1. Ouvrez [https://entra.microsoft.com](https://entra.microsoft.com) pour accéder au centre d’administration Entra.
2. Dans le volet de navigation de gauche, ouvrez **Groupes**.
3. Sélectionnez **Tous les groupes**, puis l’un des groupes disponibles.
4. Dans le volet de navigation de gauche, sous **Gérer**, sélectionnez **Licences**.

Vous voyez la liste des attributions de licences effectuées actuellement. Et vous constatez que vous devez utiliser le Centre d’administration Microsoft 365 pour effectuer les mises à jour.

1. Passez en revue les affectations actuelles, puis, dans le menu, sélectionnez **+ Affectations**.
2. Ouvrez [https://admin.microsoft.com](https://admin.microsoft.com) pour ouvrir le Centre d’administration Microsoft 365.
3. Sélectionnez **Facturation**. Sélectionnez Ensuite **Licences**.
4. Sélectionnez une licence disponible dans la liste.
5. Sélectionnez **Groupes** dans le menu situé en haut de la page.
6. Sélectionnez l’option **+ Attribuer des licences**.
7. Choisissez le groupe que vous examiniez précédemment dans Entra. Sélectionnez ensuite le bouton **Attribuer** en bas de la page.
8. Sur la page Licences du groupe, passez en revue la modification. Vous devriez voir la modification dans le centre d’administration Entra et le Centre d’administration Microsoft 365.

### Identifier et résoudre les problèmes d’affectation de licences pour un groupe dans Entra ID

La gestion des licences basées sur les groupes dans Entra ID introduit le concept d’utilisateurs en état d’erreur d’affectation de licence. Cette section explique les raisons pour lesquelles les utilisateurs peuvent se trouver dans cet état.

Lorsque vous affectez directement des licences à des utilisateurs individuels, sans recourir à une licence basée sur le groupe, l’opération d’affectation peut échouer. Par exemple, la cmdlet PowerShell `Set-MgUserLicense` peut échouer pour diverses raisons liées à la logique métier lorsque vous l’exécutez sur un objet utilisateur. Par exemple, il peut y avoir un nombre insuffisant de licences ou bien un conflit entre deux plans de service qui ne peuvent pas être affectés en même temps. Le problème vous est immédiatement signalé.

Lorsque vous utilisez une licence basée sur les groupes, les mêmes erreurs peuvent se produire, mais elles apparaissent en arrière-plan lorsque le service Entra attribue les licences. C’est pourquoi les erreurs ne peuvent pas vous être communiquées immédiatement. Au lieu de cela, elles sont enregistrées sur l’objet utilisateur et signalées par le biais du portail d’administration. L’intention initiale, qui consiste à attribuer une licence à l’utilisateur, est toujours conservée, mais est enregistrée dans un état d’erreur. Elle fera l’objet d’un examen et d’une résolution ultérieurs.

### Nombre insuffisant de licences

**Problème** : il n’existe pas suffisamment de licences disponibles pour l’un des produits spécifiés dans le groupe. Vous devez acheter des licences produit supplémentaires ou libérer des licences inutilisées par d’autres utilisateurs ou d’autres groupes.

Pour voir le nombre de licences disponibles, accédez à **Entra - Identité - Facturation**, puis **Licences** et **Tous les produits**.

Pour voir quels utilisateurs et quels groupes utilisent des licences, sélectionnez un produit. Sous **Utilisateurs sous licence**, vous voyez la liste de tous les utilisateurs auxquels des licences sont attribuées directement ou via un ou plusieurs groupes. Sous **Groupes sous licence** figurent tous les groupes auxquels sont attribuées des licences de produits.

**PowerShell :** Les applets de commande PowerShell signalent cette erreur comme *CountViolation*.

### Plans de service en conflit

**Problème** : l’un des produits spécifiés dans le groupe contient un plan de service qui est en conflit avec un autre plan de service déjà affecté à l’utilisateur via un autre produit. Certains plans de service sont configurés de sorte qu’ils ne puissent pas être attribués à l’utilisateur d’un autre plan de service lié.

Considérez l'exemple suivant. Un utilisateur possède une licence Office 365 Entreprise *E1* qui lui a été attribuée directement, avec tous les plans activés. L’utilisateur est ajouté à un groupe auquel le produit Office 365 Entreprise *E3* lui est attribué. Ce produit E3 contient des plans de service incompatibles avec les plans contenus dans E1. Par conséquent, l’attribution de la licence de groupe échoue avec l’erreur **Plans de service en conflit**. Dans cet exemple, les plans de service en conflit sont les suivants :

- SharePoint Online (Plan 2) est en conflit avec SharePoint Online (Plan 1).
- Exchange Online (Plan 2) est en conflit avec Exchange Online (Plan 1).

Pour résoudre ce conflit, vous devez désactiver deux des plans. Vous pouvez désactiver la licence E1 directement affectée à l’utilisateur. Sinon, vous devez modifier l’attribution de licence de l’ensemble du groupe et désactiver les plans dans la licence E3. Vous pouvez également supprimer la licence E1 de l'utilisateur si elle devient redondante dans le cadre de la licence E3.

Seul l’administrateur peut décider de la méthode à utiliser pour résoudre les problèmes de conflit de licences produit. Entra ID ne résout pas automatiquement les conflits de licences.

**PowerShell** : Les applets de commande PowerShell signalent cette erreur comme *MutuallyExclusiveViolation*.

### D’autres produits dépendent de cette licence

**Problème** : l’un des produits spécifiés dans le groupe contient un plan de service qui doit être activé pour un autre plan de service, dans un autre produit, pour fonctionner. Cette erreur se produit quand Entra ID tente de supprimer le plan de service sous-jacent. Par exemple, cela peut se produire lorsque vous supprimez l’utilisateur du groupe.

Pour résoudre ce problème, vous devez vérifier que le plan requis est toujours attribué aux utilisateurs par une autre méthode, ou que les services dépendants sont désactivés pour ces utilisateurs. Après cela, vous pouvez supprimer la licence de groupe sur ces utilisateurs.

**PowerShell** : Les applets de commande PowerShell signalent cette erreur comme *DependencyViolation*.

### L’emplacement d’utilisation n’est pas autorisé

**Problème** : Certains services Microsoft ne sont pas disponibles partout en raison de lois et réglementations locales. Avant de pouvoir attribuer une licence à un utilisateur, vous devez spécifier la propriété **Emplacement d’utilisation** pour l’utilisateur. Vous pouvez spécifier l’emplacement sous la section **Utilisateur**, **Profil** et **Modifier** dans le portail Azure.

Si Entra ID tente d’attribuer une licence de groupe à un utilisateur dont l’emplacement d’utilisation n’est pas pris en charge, il en résulte un échec et l’enregistrement d’une erreur pour cet utilisateur.

Pour résoudre ce problème, retirez du groupe sous licence les utilisateurs associés à des emplacements non pris en charge. Autrement, si les valeurs d’emplacement d’utilisation actuelles ne représentent pas l’emplacement réel des utilisateurs, modifiez-les : les licences seront attribuées correctement la prochaine fois (à condition que le nouvel emplacement soit pris en charge). Vous pouvez spécifier l’emplacement d’utilisation sous l’onglet **Propriétés** de l’utilisateur dans le [Centre d’administration Entra](https://entra.microsoft.com).

**PowerShell** : Les applets de commande PowerShell signalent cette erreur comme *ProhibitedInUsageLocationViolation*.

Remarque

Quand Entra ID attribue des licences de groupe, tous les utilisateurs sans emplacement d’utilisation spécifié héritent de l’emplacement de l’annuaire. Nous recommandons aux administrateurs de définir des valeurs d’emplacement d’utilisation correctes pour les utilisateurs avant d’utiliser la licence groupée afin de se conformer aux lois et réglementations locales.

### Adresses proxy en double

Si vous utilisez Exchange Online, certains comptes d’utilisateur de votre organisation risquent d’être erronément configurés avec la même valeur d’adresse proxy. Lorsque la fonction de licence basée sur un groupe tente d’affecter une licence à un tel utilisateur, l’opération échoue et le message « L'adresse proxy est déjà utilisée » s’affiche.

Une fois les problèmes d’adresse de proxy résolus pour les utilisateurs concernés, forcez le traitement des licences sur le groupe pour vérifier qu’elles peuvent maintenant être appliquées.

### Modification de l’e-mail Entra et de l’attribut ProxyAddresses

**Problème** : Lors de la mise à jour de l’attribution de licence sur un utilisateur ou un groupe, vous pouvez voir que l’e-mail Entra et l’attribut ProxyAddresses de certains utilisateurs sont modifiés.

La mise à jour d’attribution de licence sur un utilisateur entraîne le déclenchement du calcul de l’adresse proxy, ce qui peut modifier les attributs de l’utilisateur.

### LicenseAssignmentAttributeConcurrencyException dans les journaux d’audit

**Problème** : L’utilisateur rencontre l'exception LicenseAssignmentAttributeConcurrencyException lors de l’affectation de licence dans les journaux d’audit. Lorsque la gestion des licences basée sur les groupes tente d’affecter simultanément la même licence à un utilisateur, cette exception est enregistrée sur l’utilisateur. Cela se produit généralement lorsqu’un utilisateur est membre de plusieurs groupes avec la même licence affectée. Entra ID tente à nouveau de traiter la licence utilisateur et résoudra le problème. Il n’existe aucune action requise par le client pour résoudre ce problème.

### Plusieurs licences de produit affectées à un groupe

Vous pouvez attribuer plusieurs licences produit à un même groupe. Par exemple, vous pouvez attribuer Office 365 Entreprise E3 et Enterprise Mobility + Security à un groupe afin de faciliter l’activation de tous les services inclus pour les utilisateurs.

Entra ID tente d’attribuer toutes les licences spécifiées dans le groupe à chaque utilisateur. Si Entra ID ne peut pas affecter l’un des produits en raison de problèmes liés à la logique métier, il ne pourra pas non plus affecter les autres licences du groupe. Exemple : si le nombre de licences est insuffisant, ou en cas de conflit avec les autres services activés pour l’utilisateur.

Vous pouvez voir les utilisateurs pour lesquels l’attribution a échoué et vérifier les produits concernés.

### Quand un groupe sous licence est supprimé

Vous devez supprimer toutes les licences attribuées à un groupe pour pouvoir le supprimer. Toutefois, la suppression de licences de tous les utilisateurs du groupe peut prendre du temps. Il peut y avoir des échecs si l’utilisateur a une licence dépendante affectée. Si un utilisateur dispose d’une licence dépendante d’une autre licence, qui est supprimée en raison de la suppression d'un groupe, la licence attribuée à l’utilisateur est convertie d'héritée à directe.

Par exemple, prenons un groupe avec une licence Office 365 E3/E5 attribuée avec un plan de service Skype Entreprise activé. Imaginez que certains membres du groupe ont des licences d’audioconférence attribuées directement. Lorsque le groupe est supprimé, la gestion des licences basée sur un groupe tente de supprimer Office 365 E3/E5 de tous les utilisateurs. Comme l’audioconférence dépend de Skype Entreprise, pour tous les utilisateurs bénéficiant de l’audioconférence, la gestion des licences attribuées au groupe convertit les licences Office 365 E3/E5 en attributions de licence directes.

### Gérer les licences des produits avec des prérequis

Certains produits Microsoft Online que vous possédez peut-être sont des *modules complémentaires*. Les modules complémentaires nécessitent l’activation d’un plan de service préalable pour un utilisateur ou un groupe avant qu'une licence puisse leur être attribuée. Avec les licences basées sur les groupes, les plans de service prérequis et de module complémentaire doivent être présents dans le même groupe. Tous les utilisateurs ajoutés au groupe reçoivent ainsi le produit entièrement opérationnel. Considérez l’exemple suivant :

Microsoft Workplace Analytics est un produit additionnel. Il contient un plan de service unique portant le même nom. Ce plan de service peut uniquement être affecté à un utilisateur ou à un groupe, lorsque l’une des conditions requises suivantes est également assignée :

- Exchange Online (plan 1)
- Exchange Online (plan 2)

Si nous essayons d’affecter ce produit seul à un groupe, le portail renvoie un message de notification. Si nous sélectionnons les détails, le message d’erreur suivant s’affiche :

Échec de l’opération de licence. Assurez-vous que le groupe possède les services nécessaires avant d’ajouter ou de retirer un service dépendant. **Le service Microsoft Analyse du temps de travail nécessite Exchange Online (Plan 2) pour être activé**.

Pour attribuer cette licence de module complémentaire à un groupe, nous devons nous assurer que le groupe contient également le plan de service requis. Par exemple, nous pouvons mettre à jour un groupe existant qui contient déjà le produit Office 365 E3 complet, et lui ajouter le produit additionnel.

Il est également possible de créer un groupe autonome contenant uniquement les produits requis pour le fonctionnement du module additionnel. Il peut être utilisé pour fournir une licence uniquement aux utilisateurs sélectionnés pour le produit additionnel. Selon l’exemple précédent, vous devez attribuer les produits suivants au même groupe :

- Office 365 Enterprise E3, avec uniquement le plan de service Exchange Online (plan 2) activé
- Analytique de l’espace de travail Microsoft

Dorénavant, tout utilisateur ajouté à ce groupe utilise une licence de produit E3 et une licence de produit Workplace Analytics. Dans le même temps, ces utilisateurs peuvent être membres d’un autre groupe leur fournissant le produit E3 complet ; ils ne consommeront alors qu’une seule licence de ce produit.

Conseil

Vous pouvez créer plusieurs groupes pour chaque plan de service requis. Par exemple, si vos utilisateurs disposent d’Office 365 Enterprise E1 et d’Office 365 Enterprise E3, créez deux groupes pour accorder une licence Microsoft Workplace Analytics : l’un demandant E1 comme condition préalable, l’autre demandant E3. Cela vous permet de distribuer le module complémentaire aux utilisateurs E1 et E3 sans consommer plus de licences.

### Forcer le traitement des licences de groupe à résoudre des erreurs

Selon les étapes prises pour résoudre les erreurs, il peut être nécessaire de déclencher manuellement le traitement d’un groupe pour mettre à jour l’état utilisateur.

Par exemple, si vous avez libéré des licences en supprimant leurs affectations directes à des utilisateurs, déclenchez de nouveau le traitement des groupes qui avaient échoué à attribuer des licences complètes à tous leurs utilisateurs membres. Pour traiter à nouveau un groupe, accédez au volet correspondant, ouvrez **Licences**, puis sélectionnez le bouton **Retraiter** dans la barre d’outils.

### Forcer le traitement des licences d’utilisateur à résoudre des erreurs

Selon les étapes prises pour résoudre les erreurs, il peut être nécessaire de déclencher manuellement le traitement d’un utilisateur pour mettre à jour l’état de l’utilisateur.

Par exemple, après avoir résolu le problème d’adresse proxy en double pour un utilisateur affecté, vous devez déclencher le traitement de l’utilisateur. Pour retraiter un utilisateur , accédez au volet correspondant, ouvrez **Licences**, puis sélectionnez le bouton **Retraiter** dans la barre d’outils.

### Comment migrer des utilisateurs ayant des licences individuelles pour regrouper des licences

Des licences peuvent déjà être déployées pour les utilisateurs de l’organisation par attribution directe, c’est-à-dire à l’aide de scripts PowerShell ou d’autres outils qui attribuent des licences utilisateur individuelles. Avant de gérer les licences de votre organisation avec une licence basée sur le groupe, suivez ce plan de migration : il remplace en toute transparence les solutions existantes par une licence basée le groupe.

N’oubliez pas que vous devez éviter une situation dans laquelle la migration vers des licences basées sur un groupe entraîne la perte temporaire des licences affectées par les utilisateurs. Tout processus qui entraîne la suppression de licences doit être évité pour supprimer le risque que les utilisateurs perdent l’accès aux services et à leurs données.

#### Processus de migration recommandé

1. Votre gestion de l’attribution et de la suppression des licences utilisateur est actuellement automatisée (par exemple, avec PowerShell). Laissez-le fonctionner tel quel.
2. Créez un groupe de gestion des licences (ou choisissez les groupes existants à utiliser) et vérifiez que tous les utilisateurs requis sont ajoutés en tant que membres.
3. Attribuez les licences nécessaires à ces groupes. Vous devez refléter l’état de licence que votre procédure de gestion automatisée existante (par exemple, avec PowerShell) applique à ces utilisateurs.
4. Vérifiez que les licences sont appliquées à tous les utilisateurs de ces groupes. Pour ce faire, vérifiez l’état de traitement de chaque groupe, ainsi que les journaux d’audit.
  - Vous pouvez effectuer une vérification aléatoire de quelques utilisateurs individuels en examinant les détails de leur licence. Vous voyez qu’ils ont les mêmes licences attribuées « directement » et « héritées » à partir de groupes.
  - Vous pouvez exécuter un script PowerShell pour [vérifier les méthodes d’attribution des licences aux utilisateurs](https://learn.microsoft.com/fr-fr/azure/active-directory/enterprise-users/licensing-group-advanced).
  - Lorsque la même licence produit est attribuée à l’utilisateur à la fois directement et par le biais d’un groupe, une seule licence est employée par l’utilisateur. Par conséquent, aucune licence supplémentaire n’est nécessaire pour effectuer la migration.

5. Assurez-vous qu’aucune attribution de licence n’a échoué en vérifiant les utilisateurs en état d’erreur dans chaque groupe.

Envisagez de supprimer les affectations directes d’origine. Nous vous recommandons de le faire progressivement et de superviser d’abord le résultat sur une partie des utilisateurs. Si vous laissez les attributions directes d’origine sur les utilisateurs, ces derniers conservent les licences en question lorsqu’ils quittent leur groupe sous licence. Il ne s’agit pas nécessairement du comportement attendu.

#### exemple

Une organisation compte 1 000 utilisateurs. Tous les utilisateurs ont besoin de licences Office 365 Entreprise E3. Pour le moment, l’organisation dispose d’un script PowerShell qui s’exécute en local afin d’ajouter et de supprimer les licences des utilisateurs qui arrivent ou s’en vont. Néanmoins, l’organisation souhaite remplacer le script par une gestion des licences de groupes afin de pouvoir gérer les licences automatiquement avec Entra ID.

Voici ce à quoi le processus de migration peut ressembler :

1. À l’aide du portail Azure, affectez la licence Office 365 E3 au groupe **Tous les utilisateurs** dans Entra ID.
2. Vérifiez que l’affectation de licence est effectuée pour tous les utilisateurs. Accédez à la page du groupe, sélectionnez **Licences**, puis vérifiez l’état de traitement en haut de la page **Licences**.
  - Recherchez « Les dernières modifications de licence ont été appliquées à tous les utilisateurs » afin de confirmer la fin de l’opération.
  - Recherchez une notification en haut concernant les utilisateurs pour lesquels les licences n’ont pas été attribuées avec succès. Avons-nous manqué de licences pour certains utilisateurs ? Certains utilisateurs présentent-ils des plans de licence en conflit qui les empêchent d’hériter des licences de groupe ?

3. Vous devez vérifier quelques utilisateurs afin de veiller à ce qu’à la fois les licences directes et les licences de groupe leur soient bien appliquées. Accédez à la page de profil d’un utilisateur, sélectionnez Licences, puis examinez l’état des licences.

- Voici l’état utilisateur attendu lors de la migration :

1. Après avoir confirmé l’équivalence des licences directes et des licences de groupe, vous pouvez commencer à supprimer les licences directes des utilisateurs. Vous pouvez tester cette procédure en supprimant ces licences pour des utilisateurs individuels sur le portail, puis exécuter des scripts d’automatisation afin de les supprimer en bloc. Voici un exemple de même utilisateur avec les licences directes supprimées via le portail. L’état de licence reste inchangé, mais les attributions directes n’apparaissent plus.

### Modifier les attributions de licence pour un utilisateur ou un groupe dans Entra ID

Cette section décrit comment déplacer des utilisateurs et des groupes entre des plans de licences de services dans Entra ID. L’objectif est de s’assurer qu’il n’y a aucune perte de service ou de données pendant la modification de licence. Les utilisateurs doivent passer d’un service à l’autre sans interruption. Les étapes d’affectation d’un plan de licence décrites dans cette section font passer un utilisateur ou un groupe d’Office 365 E1 à Office 365 E3, mais elles s’appliquent à tous les plans de licences. Lorsque vous mettez à jour les attributions de licences pour un utilisateur ou un groupe, les suppressions d’attributions et les nouvelles affectations sont effectuées simultanément. Les utilisateurs ne perdent donc pas l’accès à leurs services pendant les modifications de licence et ne voient pas de conflits de licence entre les plans.

Avant de mettre à jour les affectations de licence, vérifiez que certaines hypothèses sont vraies pour tous les utilisateurs ou groupes à mettre à jour. Si les hypothèses ne se vérifient pas pour tous les utilisateurs dans un groupe, la migration risque d’échouer pour certains d’entre eux. Certains utilisateurs peuvent alors perdre leur accès aux services ou aux données. Assurez-vous que :

- Les utilisateurs disposent du plan de licence affecté à un groupe et hérité par l’utilisateur, mais pas affecté directement.
- Vous avez suffisamment de licences disponibles pour le plan de licence que vous affectez. Si vous n’avez pas assez de licences, certains utilisateurs risquent de ne pas se voir affecter le nouveau plan de licence. Vous pouvez vérifier le nombre de licences disponibles.
- Vérifiez toujours que les utilisateurs n’ont pas de licences de services affectées pouvant entrer en conflit avec la licence voulue ou empêcher la suppression de la licence actuelle. Par exemple, une licence d’un service comme Workplace Analytics ou Project Online, qui possède une dépendance vis-à-vis d’autres services.
- Si vous gérez des groupes sur site et les synchronisez dans Entra ID via Entra Connect, vous ajoutez ou supprimez des utilisateurs à l'aide de votre système sur site. La synchronisation des modifications avec Entra ID peut prendre un certain temps pour être récupérée par les licences de groupe.
- Si vous utilisez les adhésions à des groupes dynamiques Entra, vous ajoutez ou supprimez des utilisateurs en modifiant leurs attributs. Le processus de mise à jour des attributions de licence, lui, reste le même.


## Exercice - Modifier des affectations de licence utilisateur

**Besoins pour l'environnement d'exercice** : ce laboratoire suppose que vous disposez d'un tenant Entra de base avec des droits d'administrateur d'utilisateur minimum pour le terminer. Vous pouvez obtenir un abonnement d’essai gratuit à [l’adresse Essayer Microsoft Azure gratuitement](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).

### Créer un utilisateur dans l’ID Entra

1. Accédez au [Centre d’administration Entra](https://entra.microsoft.com).
2. Dans le volet de navigation gauche, sous **Identité**, sélectionnez **Utilisateurs**.
3. Dans la page Utilisateurs, dans le menu, sélectionnez **+ Nouvel utilisateur** , puis **Créez un utilisateur**.
4. Créez un utilisateur à l’aide des informations suivantes :     **Paramètre**  **Valeur**     Nom d’utilisateur DominiqueK   Nom Dominique Koch   Prénom Dominique   Nom Koch   Mot de passe Créer un mot de passe unique pour l’utilisateur   Emplacement d'utilisation Sélectionnez votre emplacement d’utilisation préféré
5. Une fois terminé, vérifiez que le compte de Dominique Koch est affiché dans la liste **Tous les utilisateurs** .

### Mettre à jour les attributions de licence utilisateur

L’attribution de licence à des utilisateurs individuels est gérée via le Centre d’administration Microsoft 365.

1. Ouvrez le [centre d’administration Microsoft 365](https://admin.microsoft.com).
2. Sélectionnez **Facturation**, puis **sélectionnez Licences**.
3. Sélectionnez une licence disponible dans la liste.
4. Sélectionnez **Utilisateurs sous licence** dans le menu en haut de la page.
5. Sélectionnez **+ Attribuer des licences**.
6. Recherchez et sélectionnez **Dominique Koch**, puis **sélectionnez Affecter** en bas de la page.
7. Une fois terminé, vérifiez que la licence est répertoriée sur le profil de Dominique Koch dans le centre d’administration Entra sous**Identité**>**Utilisateurs**> sélectionnez l'utilisateur >**Licences**.


## Créer des attributs de sécurité personnalisés

### Qu’est-ce qu’un attribut de sécurité personnalisé ?

Les attributs de sécurité personnalisés dans Entra ID sont des attributs spécifiques à l'entreprise (paires clé-valeur) que vous pouvez définir et attribuer aux objets Entra. Ces attributs peuvent être utilisés pour stocker des informations, classer des objets ou appliquer un contrôle d’accès affiné sur des ressources Azure spécifiques.

#### Pourquoi utiliser des attributs de sécurité personnalisés ?

- Étendre des profils utilisateur, par exemple en ajoutant le salaire horaire pour tous mes employés.
- Garantir que seuls les administrateurs peuvent voir l’attribut de salaire horaire dans les profils de mes employés.
- Classer des centaines ou des milliers d’applications pour créer facilement un inventaire filtrable à des fins d’audit.
- Accorder aux utilisateurs l’accès aux objets blob du Stockage Azure appartenant à un projet.

#### Que puis-je faire avec les attributs de sécurité personnalisés ?

- Définir des informations spécifiques à l’entreprise (attributs) pour votre locataire.
- Ajoutez des attributs de sécurité personnalisés aux utilisateurs d’Entra et aux applications d’entreprise (principaux de service).
- Gérez les objets Entra à l'aide d'attributs de sécurité personnalisés avec des requêtes et des filtres.
- Fournir la gouvernance des attributs afin que les attributs déterminent qui peut obtenir l’accès.

Les attributs de sécurité personnalisés **ne sont pas** pris en charge dans les demandes Entra Domain Services, les demandes de jeton SAML ou les demandes JWT (JSON Web Token).

#### Fonctionnalités des attributs de sécurité personnalisés

- Disponible pour l'ensemble des locataires
- Inclure une description
- Prendre en charge différents types de données : booléen, entier, chaîne
- Prendre en charge une valeur unique ou plusieurs valeurs
- Prendre en charge les valeurs de formulaire libre définies par l’utilisateur ou les valeurs prédéfinies
- Attribuer des attributs de sécurité personnalisés à des utilisateurs synchronisés d’annuaire d’une instance Active Directory locale


## Explorer la création automatique d’utilisateurs

![Diagramme du flux de processus pour l’approvisionnement automatique d’utilisateurs dans Entra ID. Provisionner automatiquement des utilisateurs et des groupes.](https://learn.microsoft.com../../wwl-sci/create-configure-manage-identities/media/automatic-user-provisioning.png)

#### Composants de SCIM (System for Cross-Domain Identity Management)

- **Système HCM** - Applications et technologies qui permettent le processus et les pratiques de gestion du capital humain. Elles prennent en charge et automatisent les processus RH tout au long du cycle de vie des employés.
- **Entra Provisioning Service** : utilise le protocole SCIM 2.0 pour l’approvisionnement automatique. Le service se connecte au point de terminaison SCIM de l’application. Il utilise ensuite le schéma d’objet utilisateur SCIM et les API REST pour automatiser l’approvisionnement et le déprovisionnement des utilisateurs et des groupes.
- **Entra ID** - Référentiel utilisateur utilisé pour gérer le cycle de vie des identités et leurs droits.
- **Système cible** : application ou système qui a un point de terminaison SCIM et fonctionne avec le provisionnement Entra pour activer l’approvisionnement automatique d’utilisateurs et de groupes.

#### Pourquoi utiliser SCIM ?

SCIM (System for Cross-domain Identity Management) est un protocole ouvert standard permettant d’automatiser l’échange d’informations d’identité d’utilisateur entre les domaines d’identité et les systèmes informatiques. SCIM garantit que les employés ajoutés au système HCM (Human Capital Management) disposent automatiquement de comptes créés dans Entra ID ou Windows Server Active Directory. Les attributs et profils utilisateur sont synchronisés entre les deux systèmes, la mise à jour ou la suppression d’utilisateurs en fonction de l’état de l’utilisateur ou du changement de rôle.

La clé consiste à maintenir vos systèmes d’identité à jour. Si un utilisateur peut être automatiquement déprovisionné de l’ID Entra dès qu’il est supprimé de vos systèmes RH, vous avez moins de soucis sur une violation possible.

#### Attribution entrante pilotée par les API

Tous les systèmes RH n’exposent pas de point de terminaison SCIM. Pour ces scénarios, l’ID Entra prend en charge le **provisionnement entrant piloté par l’API**, qui a atteint la disponibilité générale en mars 2024. Le système source n’a pas besoin d’envoyer les données via SCIM : tout outil d’automatisation ou script peut récupérer des données de main-d’œuvre dans n’importe quel système d’enregistrement et les envoyer à l’API de provisionnement Entra. Les sources de référence prises en charge incluent Workday, SAP SuccessFactors et tout système RH personnalisé intégré via l’API. Cette approche offre aux organisations la flexibilité nécessaire pour automatiser la gestion du cycle de vie des identités, quelles que soient les fonctionnalités d’intégration natives de leur plateforme RH.


## Évaluation du module

Choisissez la meilleure réponse à chacune des questions ci-dessous.

### Contrôler vos connaissances


## Résumé et ressources

Vous avez terminé ce module, vous pouvez :

- Créer, configurer et gérer des identités
- Créer, configurer et gérer des groupes
- Gestion des licences
- Configurer et gérer l’inscription des appareils
- Explorer les attributs de sécurité personnalisés et l’approvisionnement automatique de comptes

### Ressources

Utilisez ces ressources pour en savoir plus :

- [Démarrage rapide : Créer et affecter un compte d’utilisateur](https://learn.microsoft.com/fr-fr/entra/identity/enterprise-apps/add-application-portal-assign-users)
- [Créer des utilisateurs en bloc dans Entra ID](https://learn.microsoft.com/fr-fr/entra/identity/users/users-bulk-add)
- [Créer un groupe de base et ajouter des membres à l’aide de l’ID Entra](https://learn.microsoft.com/fr-fr/entra/fundamentals/how-to-manage-groups)
- [Créer ou mettre à jour un groupe d’appartenances dynamique dans Entra ID](https://learn.microsoft.com/fr-fr/entra/identity/users/groups-create-rule)
- [Qu’est-ce qu’Entra Cloud Sync ?](https://learn.microsoft.com/fr-fr/entra/identity/hybrid/cloud-sync/what-is-cloud-sync)
- [Gérer les demandes de licence](https://learn.microsoft.com/fr-fr/microsoft-365/commerce/licenses/manage-license-requests)
- [Attribuer des licences aux utilisateurs - Centre d’administration Microsoft 365](https://learn.microsoft.com/fr-fr/microsoft-365/admin/manage/assign-licenses-to-users)
- [Planifier le déploiement d’appareils Entra](https://learn.microsoft.com/fr-fr/entra/identity/devices/plan-device-deployment)
- [Concepts d’approvisionnement entrant pilotés par l’API](https://learn.microsoft.com/fr-fr/entra/identity/app-provisioning/inbound-provisioning-api-concepts)


---

# Implémenter et gérer des identités externes

_https://learn.microsoft.com/fr-fr/training/modules/implement-manage-external-identities/_


## Présentation

Pouvoir inviter des utilisateurs externes à utiliser vos ressources Azure est un grand avantage, mais cela doit être fait de manière sécurisée. Ce module vous montre comment mettre en place des scénarios de collaboration B2B sécurisés avec des utilisateurs extérieurs à votre organisation. Vous y gérez les paramètres de collaboration externe dans Entra ID et invitez des utilisateurs individuellement ou en bloc. Vous apprendrez également à gérer les comptes d’utilisateurs externes et à configurer les fournisseurs d’identité.

### Objectifs d’apprentissage

Dans ce module, vous allez :

- Gérer les paramètres de collaboration externe dans Entra ID.
- Inviter des utilisateurs externes (individuellement ou en bloc).
- Gérez les comptes d’utilisateur externes dans Entra ID.
- Configurer des fournisseurs d’identité (social et SAML/WS-fed).
- Explorez Vérification d’identité Entra.

### Prérequis

Aucun


## Description de l’accès invité et des comptes interentreprises

![Diagramme permettant aux utilisateurs externes de rejoindre votre tenant Entra en tant qu’utilisateur invité.](https://learn.microsoft.com../../wwl-sci/implement-manage-external-identities/media/guest-user-diagram.png)

#### Définition des utilisateurs invités

La collaboration B2B d’Entra est une caractéristique d’Entra External Identities, une composante d’Entra, qui vous permet d'inviter des utilisateurs à collaborer avec votre organisation. Azure AD B2B Collaboration vous permet de partager de manière sécurisée les applications et services de votre organisation avec des utilisateurs externes, tout en conservant le contrôle sur vos propres données d’entreprise. Collaborez de manière sécurisée avec des partenaires externes, grands ou petits, même s’ils ne disposent pas d’Entra ID ou d’un service informatique.

#### Comment les utilisateurs invités rejoignent votre locataire Entra

Un simple processus d’invitation et d’échange d’invitation permet à vos partenaires d’utiliser leurs propres informations d’identification pour accéder aux ressources de votre société. Vous pouvez également activer des flux d’utilisateur d’inscription libre-service pour permettre aux utilisateurs externes de s’inscrire à des applications ou des ressources. Une fois que l’utilisateur externe a accepté l’invitation ou terminé l’inscription, il est représenté dans votre répertoire sous la forme d’un objet utilisateur. Les objets utilisateur de collaboration B2B reçoivent généralement un type d’utilisateur « invité » et peuvent être identifiés par l’extension #EXT# dans leur nom d’utilisateur principal.

Les développeurs peuvent utiliser les API interentreprises d’Entra ID pour personnaliser le processus d'invitation ou créer des applications comme des portails d'inscription en libre-service.

#### B2B Collaboration

La collaboration B2B est une caractéristique d’Entra External Identities qui vous permet de collaborer avec des utilisateurs et des partenaires extérieurs à votre organisation. Avec B2B Collaboration, un utilisateur externe est invité à se connecter à votre organisation Entra à l’aide de ses propres informations d’identification. Il peut alors accéder aux applications et aux ressources que vous souhaitez partager avec lui. Un objet utilisateur est créé pour l’utilisateur de collaboration B2B dans le même répertoire que celui utilisé pour vos employés. Les objets utilisateurs de collaboration B2B ont des privilèges limités dans votre répertoire par défaut, et ils peuvent être gérés comme des employés, ajoutés à des groupes, etc.


## Gérer les collaborations externes

Entra External Identities est une caractéristique qui autorise l'accès à vos applications et ressources à des personnes extérieures à votre organisation. Vos partenaires, distributeurs, fournisseurs, vendeurs et autres utilisateurs invités peuvent « apporter leurs propres identités ». Ils se connectent avec leurs propres informations d’identification, qu’elles proviennent d’une identité numérique émise par une entreprise ou un gouvernement, ou d’une identité sociale non gérée telle que Google ou Facebook. Le fournisseur d’identité de l’utilisateur externe gère leur identité, et vous gérez l’accès à vos applications avec Entra ID afin de protéger vos ressources.

### Flux d’acceptation d’invitation

![Diagramme de l’acceptation d’une invitation externe pour rejoindre Entra comme invité.](https://learn.microsoft.com../../wwl-sci/implement-manage-external-identities/media/business-to-business-invitation-redemption.png)

1. Entra ID effectue une découverte basée sur l’utilisateur pour déterminer si l’utilisateur existe déjà dans un tenant (locataire) Entra managé. (Les comptes Entra non managés ne peuvent plus être utilisés pour l’acceptation d’invitation.) Si le nom d’utilisateur principal (UPN) de l’utilisateur correspond à la fois à un compte Entra existant et à un compte MSA personnel, l’utilisateur choisit le compte avec lequel il souhaite accepter l’invitation.
2. Si un administrateur a activé la fédération SAML/WS-Fed IdP, Entra ID compare le suffixe de domaine de l’utilisateur au domaine d’un fournisseur d’identité SAML/WS-Fed configuré, puis redirige l’utilisateur vers ce fournisseur d’identité préconfiguré.
3. Si un administrateur a activé la Fédération des services Google, Entra ID vérifie si le suffixe de domaine de l’utilisateur est gmail.com ou googlemail.com et le redirige vers Google.
4. Le processus d’acceptation vérifie si l’utilisateur dispose d’un MSA personnel. Si l’utilisateur a déjà un MSA existant, il se connecte avec son MSA existant.
5. Une fois que le répertoire de base de l’utilisateur est identifié, l’utilisateur est envoyé au fournisseur d’identité correspondant pour se connecter.
6. Si aucun annuaire de base n’est trouvé et que le code secret à usage unique par e-mail est activé pour les invités, un code secret est envoyé à l’utilisateur via l’e-mail invité. L’utilisateur récupère et entre ce code secret dans la page de connexion Entra.
7. Si aucun annuaire de base n’est trouvé et que le code secret à usage unique par e-mail est désactivé pour les invités, l’utilisateur est invité à créer un MSA consommateur avec l’e-mail invité. Nous prenons en charge la création d’un MSA avec des e-mails professionnels dans des domaines qui ne sont pas vérifiés dans Entra ID.
8. L’utilisateur, après s’être authentifié auprès du fournisseur d’identité approprié, est redirigé vers Entra ID pour terminer l’expérience de consentement.

### Scénarios d’identités externes

Entra External Identities est axé moins sur la relation d'un utilisateur avec votre organisation, et davantage sur la façon dont l'utilisateur souhaite se connecter à vos applications et ressources. Dans ce cadre, Entra ID prend en charge différents scénarios.

Un scénario de collaboration B2B permet d’inviter des utilisateurs externes dans votre propre locataire en tant qu’utilisateurs « invités ». Vous pouvez leur affecter des autorisations, et ils continuent d’utiliser leurs informations d’identification existantes (pour l’authentification). Les utilisateurs se connectent aux ressources partagées à l’aide d’un processus simple d’invitation et d’échange d’invitation, en utilisant leur compte professionnel ou scolaire, ou n’importe quel autre compte de messagerie. Vous pouvez également utiliser la gestion des droits d’utilisation Entra afin de configurer des stratégies qui vous aident à gérer l’accès pour les utilisateurs externes. Vous pouvez maintenant permettre aux utilisateurs externes de s’inscrire eux-mêmes à des applications grâce à la possibilité d’inscription autonome. L’expérience peut être personnalisée pour permettre l’inscription avec une identité professionnelle, scolaire ou sociale (par exemple, Google ou Facebook). Vous pouvez également collecter des informations sur l’utilisateur pendant le processus d’inscription.

La liste suivante identifie un exemple de scénario de collaboration B2B et détaille certaines des fonctionnalités qu’il fournit :

- Scénario principal : collaboration à l’aide d’applications Microsoft (Microsoft 365, Team, etc.) ou de vos propres applications (applications SaaS, applications personnalisées, etc.).
- Destiné à : collaboration avec des partenaires commerciaux d’organisations externes tels que des fournisseurs, des partenaires et des distributeurs. Les utilisateurs apparaissent en tant qu’utilisateurs invités dans votre annuaire.
- Fournisseurs d'identité pris en charge : les utilisateurs externes peuvent collaborer avec un compte professionnel ou scolaire, n’importe quelle adresse e-mail, un fournisseur d’identité basé sur SAML ou WS-Fed, Gmail ou Facebook.
- Gestion des utilisateurs externes : les utilisateurs externes sont gérés dans le même annuaire que les employés, mais sont généralement annotés en tant qu’utilisateurs invités. Les utilisateurs invités peuvent être gérés de la même façon que les employés, ajoutés aux mêmes groupes, etc.
- Authentification unique – L'authentification unique auprès de toutes les applications connectées à Entra est prise en charge. Par exemple, vous pouvez donner accès à des applications Microsoft 365 ou des applications locales, et à d’autres applications SaaS telles que Salesforce ou Workday.
- Stratégie de sécurité et conformité : gérée par l’organisation hôte ou qui invite (par exemple, avec des règles d’accès conditionnelles).
- Marque : la marque de l’organisation hôte (qui invite) est utilisée.

### Gérer les paramètres de collaboration externe dans Entra ID

Cette unité explique comment activer la collaboration B2B Entra. Nous découvrons ensuite la possibilité de déterminer qui peut convier des invités et de quelles autorisations les invités disposent.

Par défaut, tous les utilisateurs et invités de votre annuaire peuvent inviter des invités, même s’ils ne sont pas associés à un rôle d’administrateur. Les paramètres de collaboration externe vous permettent d’activer ou de désactiver les invitations d’invités pour différents types d’utilisateurs dans votre organisation. Vous pouvez également déléguer des invitations aux utilisateurs individuels, en leur attribuant des rôles qui leur permettent d’inviter des invités.

Entra ID offre la possibilité de limiter ce que peuvent voir les utilisateurs invités externes dans votre annuaire Entra. Par défaut, un niveau d’autorisation limité est attribué aux utilisateurs invités. Les invités ne peuvent pas répertorier les utilisateurs, les groupes ou d’autres ressources de répertoire, mais les invités peuvent voir l’appartenance à des groupes non masqués. Les administrateurs peuvent modifier le paramètre d’autorisations d’invités, ce qui vous permet de restreindre davantage l’accès invité, afin que les invités puissent uniquement afficher leurs propres informations de profil. Pour plus d’informations, consultez [Restriction des autorisations d’accès invité](https://learn.microsoft.com/fr-fr/entra/identity/users/users-restrict-guest-permissions).

### Configurer les paramètres de collaboration externe interentreprises

Avec la collaboration B2B (Business to Business) Entra, un administrateur client peut définir les stratégies d’invitation suivantes :

- Désactiver les invitations (aucun utilisateur externe ne peut être invité)
- Seuls les administrateurs et les utilisateurs du rôle Inviteur d’invités peuvent inviter
- Les administrateurs, le rôle Inviteur d’invités et les membres peuvent inviter (identique au paramètre ci-dessus, sauf que les membres invités peuvent également inviter des utilisateurs externes)
- Tous les utilisateurs, y compris les invités, peuvent inviter (comme le nom l’indique, tous les utilisateurs du locataire peuvent inviter des utilisateurs externes)

Par défaut, tous les utilisateurs, notamment les invités, peuvent inviter des invités.


## Exercice : Configurer la collaboration externe

### Configurer les paramètres de collaboration externe

1. Connectez-vous au [Centre d'administration Entra](https://entra.microsoft.com/) en tant qu'administrateur général.
2. Sélectionnez **Identité**.
3. Sélectionnez **Identités externes - Paramètres de collaboration externe**.
4. Sous **Accès utilisateur invité**, passez en revue les niveaux d'accès disponibles, puis sélectionnez **L'accès des utilisateurs invités est limité aux propriétés et aux membres de leurs propres objets de répertoire (le plus restrictif)**.

Remarque

- Les utilisateurs invités ont le même accès que les membres (le plus inclusif) : Cette option donne aux invités le même accès aux ressources Entra et aux données d’annuaire que les utilisateurs membres.
- Les utilisateurs invités accèdent de manière limitée aux propriétés et aux appartenance des objets d’annuaire : (Par défaut) Ce paramètre bloque les utilisateurs invités dans certaines tâches d’annuaire, comme l’énumération des utilisateurs, des groupes ou d’autres ressources d’annuaire. Les invités peuvent voir l’appartenance de tous les groupes non-participants.
- L’accès utilisateur invité est limité aux propriétés et aux appartenances de leurs propres objets d’annuaire (les plus restrictifs) : avec ce paramètre, les invités peuvent accéder uniquement à leurs propres profils. Les invités ne sont pas autorisés à voir les profils, les groupes ou les appartenances aux groupes d’autres utilisateurs.

1. Sous **Paramètres d’invitation d’invité**, marquez **Uniquement les utilisateurs avec des rôles d’administrateur spécifiques peuvent convier des utilisateurs invités**.
2. Convier des invités à collaborer déplace l’option la moins restrictive, permettant à tous de convier des invités, à l’option la moins restrictive, ne permettant à personne de convier des invités.
3. Toute personne de l’organisation peut convier des invités : cette option autorise tous les utilisateurs à convier des utilisateurs invités, y compris les utilisateurs, les administrateurs et même les autres utilisateurs invités.
4. Utilisateurs membres et utilisateurs auxquels des rôles d’administrateur spécifiques sont attribués : cette option n’autorise que les membres complets de l’organisation ou les membres des groupes d’administrateurs à convier des invités.
5. Seuls les utilisateurs auxquels des rôles d’administrateur spécifiques sont attribués : définir cette option afin d’autoriser uniquement les personnes avec des rôles d’administrateur spécifiques à convier des invités.
6. Personne dans l’organisation ne peut convier des invités : définir cette option afin de restreindre toutes les invitations d’utilisateurs invités par des membres.
7. Les utilisateurs du **rôle Inviteur** d’invités peuvent inviter des invités, si les utilisateurs administrateurs peuvent inviter un invité.

 12. Sous **restrictions de collaboration**, passez en revue les options disponibles et acceptez les paramètres par défaut.

Important

Vous pouvez créer une liste d’autorisation ou une liste de refus. Vous ne pouvez pas configurer les deux types de listes. Par défaut, les domaines qui ne sont pas dans la liste d’autorisation sont dans la liste de refus et vice versa. Vous ne pouvez créer qu’une seule stratégie par organisation. Vous pouvez mettre à jour la stratégie pour inclure plusieurs domaines ou vous pouvez supprimer la stratégie pour en créer une nouvelle. Le nombre de domaines que vous pouvez ajouter à une liste d’autorisation ou à une liste de refus n’est limité que par la taille de la stratégie. La taille maximale de la stratégie entière est de 25 Ko (25 000 caractères). Elle comprend la liste d’autorisation ou la liste de refus et tous les autres paramètres configurés pour d’autres fonctionnalités. Cette liste fonctionne indépendamment à partir des listes d’autorisation/de refus OneDrive et SharePoint Online. Si vous souhaitez restreindre le partage des fichiers individuels dans SharePoint Online, vous devez configurer une liste d’autorisation ou de refus pour OneDrive Entreprise et SharePoint Online. La liste ne s’applique pas aux utilisateurs externes qui ont échangé l’invitation. La liste est appliquée une fois configurée. Si l’invitation d’un utilisateur est en attente et que vous définissez une stratégie qui bloque son domaine, la tentative de l’utilisateur d’accepter l’invitation échoue.

1. Quand vous avez terminé, enregistrez les modifications.


## Inviter des utilisateurs externes : individuellement et en bloc

En tant qu’utilisateur affecté à l’un des rôles d’annuaire administrateur limité, vous pouvez utiliser le Portail Azure pour inviter des utilisateurs B2B Collaboration. Libre à vous de convier des utilisateurs invités à rejoindre le répertoire, un groupe ou une application. Une fois l’utilisateur invité par le biais de l’une de ces méthodes, son compte est ajouté à Entra ID et son type devient *invité*. L’utilisateur invité doit ensuite échanger son invitation pour accéder aux ressources. L’invitation d’un utilisateur n’expire pas.

![Diagramme montrant le déroulement de l’invitation d’un utilisateur invité à accéder à l’annuaire ; et comment l’utilisateur peut accéder aux ressources une fois qu’il dispose d’un accès.](https://learn.microsoft.com../../wwl-sci/implement-manage-external-identities/media/external-user-flow.png)

Après avoir ajouté un utilisateur invité dans le répertoire, vous pouvez envoyer à l’utilisateur invité un lien direct vers une application partagée, ou l’utilisateur invité peut sélectionner l’URL d’acceptation dans l’e-mail d’invitation. Assurez-vous que les paramètres de collaboration externe de votre organisation sont configurés de telle sorte que vous êtes autorisé à inviter des invités. Par défaut, tous les utilisateurs et les administrateurs peuvent inviter des invités. Mais les stratégies de collaboration externe de votre organisation peuvent être configurées pour empêcher certains types d’utilisateurs ou d’administrateurs d’inviter des invités.

### Comment procéder pour inviter des utilisateurs invités à accéder à une application ?

Une fois qu’un utilisateur invité a été ajouté au répertoire dans Entra ID, un propriétaire d’application peut lui envoyer un lien direct vers l’application qu’il souhaite partager. Les administrateurs Entra peuvent également configurer la gestion en libre-service pour les applications SAML ou de la galerie dans leur locataire Entra. Les propriétaires d’application peuvent ainsi gérer leurs propres utilisateurs invités, même si ces derniers n’ont pas encore été ajoutés au répertoire. Lorsqu’une application est configurée en libre-service, son propriétaire utilise le Panneau d’accès pour inviter un utilisateur invité, ou pour l’ajouter à un groupe ayant accès à l’application. La gestion des applications en libre-service pour la galerie et les applications basées sur SAML nécessite une configuration initiale par un administrateur, qui peut être résumée comme suit :

- Activer la gestion de groupes en libre-service pour votre abonné
- Créer un groupe à affecter à l’application et convertir l’utilisateur en propriétaire
- Configurer l’application pour le libre-service et affecter le groupe à l’application

### Comment inviter en bloc des utilisateurs d’Entra B2B Collaboration

Si vous utilisez la collaboration Entra B2B pour travailler avec des partenaires externes, vous pouvez inviter plusieurs utilisateurs invités dans votre organisation en même temps. Vous effectuez les étapes suivantes :

- Utiliser **Inviter des utilisateurs en bloc** pour préparer un fichier de valeurs séparées par des virgules (.csv) avec les informations de l’utilisateur et les préférences d’invitation
- Charger le fichier .csv sur l’ID Entra
- Vérifier que les utilisateurs ont été ajoutés à l’annuaire

#### Comprendre le modèle CSV

Téléchargez et remplissez le modèle CSV de chargement en bloc pour vous aider à inviter les utilisateurs invités d’Entra ID en bloc. Le modèle CSV que vous téléchargez peut se présenter comme dans l’exemple suivant :

#### Structure du modèle CSV

Ce modèle CSV s’ouvre toujours avec deux lignes de données existantes. Les lignes d’un modèle CSV téléchargé sont les suivantes :

- **Numéro de version** : La première ligne contenant le numéro de version doit être incluse dans le fichier CSV chargé.
- **En-têtes de colonne** : le format des en-têtes de colonne est **Nom d’élément**`[PropertyName]`**Obligatoire ou vide**. Par exemple : `Email address to invite [inviteeEmail] Required`. Certaines anciennes versions du modèle peuvent avoir de légères variations.
- **Exemples de lignes** : Nous avons inclus dans le modèle une ligne d’exemples de valeurs acceptables pour chaque colonne. Vous devez supprimer la ligne des exemples et la remplacer par vos propres entrées.

#### Conseils supplémentaires

- Les deux premières lignes du modèle chargé ne doivent pas être supprimées ni modifiées, sinon, le chargement ne pourra pas être traité.
- Les colonnes obligatoires sont listées en premier.
- Nous vous déconseillons d’ajouter des colonnes au modèle. Les colonnes que vous ajouterez seront ignorées et ne seront pas traitées.
- Nous vous recommandons de télécharger la version la plus récente du modèle CSV aussi souvent que possible.


## Exercice : ajouter des utilisateurs invités au répertoire

Dans cet exercice, vous devez ajouter des utilisateurs invités à l’annuaire.

1. Connectez-vous au [Centre d'administration d’Entra](https://entra.microsoft.com/) en tant qu'utilisateur auquel a été attribué un rôle d'administrateur limité ou le rôle d'invité.
2. Sélectionnez **Identité**
3. Sous **Utilisateurs**, sélectionnez **Tous les utilisateurs**.
4. Sélectionnez **Nouvel utilisateur – Inviter un utilisateur externe**.

1. Sur la page « Nouvel utilisateur », sélectionnez **Inviter l’utilisateur**, puis ajoutez vos informations d’utilisateur invité.
2. Les adresses e-mail de groupe ne sont pas prises en charge. Veuillez entrer des adresses e-mail individuelles. Certains fournisseurs de messagerie permettent aux utilisateurs d’ajouter un signe plus (+) et du texte à leurs adresses e-mail pour faciliter notamment le filtrage de la boîte de réception. Toutefois, Entra ID ne prend actuellement pas en charge les symboles plus dans les adresses e-mail. Pour éviter les problèmes de livraison, omettez le signe plus (+) et les caractères après celui-ci jusqu’au symbole @.
3. Lorsque vous avez terminé, sélectionnez **Inviter**.
4. Dans l’écran Utilisateurs, vérifiez que votre compte est listé et, dans la colonne **Type d’utilisateur**, vérifiez que **Invité** est affiché.

Après avoir envoyé l’invitation, le compte d’utilisateur est automatiquement ajouté au répertoire en tant qu’invité.


## Exercice : Inviter des utilisateurs en bloc

Utilisez cet exercice pour apprendre à inviter des utilisateurs invités en bloc.

1. Connectez-vous au [Centre d'administration d’Entra](https://entra.microsoft.com/) avec un compte d'administrateur d'utilisateurs de votre organisation.
2. Dans le volet de navigation, sélectionnez **Identity**.
3. Sous **Utilisateurs**, sélectionnez **Tous les utilisateurs**.
4. Sur l'écran Tous les utilisateurs, dans le menu, sélectionnez **Opérations en bloc – Invitation en bloc**.
5. Dans le Panneau utilisateurs d’invitation en bloc, sélectionnez **Télécharger** vers un exemple de modèle CSV avec les propriétés de l’invitation.
6. À l’aide d’un éditeur pour afficher le fichier CSV, passez en revue le modèle.

Remarque

- **Adresse e-mail à inviter** : l’utilisateur qui recevra une invitation.
- **URL de redirection** : URL vers laquelle l’utilisateur invité est transféré après avoir accepté l’invitation.

1. Ouvrez le modèle CSV et ajoutez une ligne pour chaque utilisateur invité. Les valeurs obligatoires sont les suivantes :
2. Enregistrez le fichier.
3. Dans la page Inviter des utilisateurs en bloc, sous **Chargez votre fichier .csv**, accédez au fichier. Quand vous sélectionnez le fichier, la validation du fichier .csv démarre.
4. Une fois le contenu du fichier validé, vous verrez **que le fichier est chargé avec succès**. Si des erreurs sont présentes, vous devez les corriger avant de pouvoir envoyer le travail.
5. Une fois votre fichier validé, sélectionnez **Envoyer** pour démarrer l’opération en bloc Azure qui ajoute les invitations.
6. Pour voir l’état du travail, sélectionnez **Afficher l’état de chaque opération**. Vous pouvez également sélectionner **Résultats de l’opération en bloc** dans la section Activité. Pour plus d’informations sur chaque élément de ligne au sein de l’opération en bloc, sélectionnez les valeurs sous les colonnes **Nombre de réussites**, **Nombre d’échecs** ou **Nombre total de requêtes**. Si des échecs se sont produits, les raisons sont affichées.
7. Une fois le travail terminé, vous recevez une notification indiquant que l’opération en bloc a réussi.


## Démonstration : gérer les utilisateurs invités dans Entra ID

[Lancer la démonstration](https://mslearn.cloudguides.com/guides/Manage%20Guest%20User%20Access%20in%20Azure%20AD%20for%20B2B%20Collaboration?azure-portal=true)

Dans ce guide interactif, découvrez comment gérer l’accès des utilisateurs invités dans Entra ID pour la collaboration interentreprises (B2B). Découvrez comment inviter des utilisateurs externes à collaborer, attribuer des ressources aux utilisateurs invités et créer des stratégies d’accès conditionnel pour sécuriser les données.


## Gérer les comptes d’utilisateur externes dans l’ID Entra

Les utilisateurs Entra B2B Collaboration sont ajoutés en tant qu'utilisateurs invités au répertoire et les autorisations des invités dans le répertoire sont restreintes par défaut. Votre entreprise a peut-être besoin que certains utilisateurs invités occupent des rôles avec davantage de privilèges dans votre organisation. Pour prendre la définition de rôles avec davantage de privilèges, les utilisateurs invités peuvent être ajoutés à n’importe quel rôle souhaité, en fonction des besoins de votre organisation.

### Ajouter un utilisateur B2B à un rôle

Microsoft recommande que les organisations utilisent la règle des privilèges minimum. Vous pouvez utiliser Privileged Identity Management (PIM) pour accorder l’accès aux utilisateurs B2B/invités.

### Propriétés clés d’un utilisateur Entra B2B Collaboration

#### UserType

Cette propriété indique la relation de l’utilisateur avec la location hôte. Cette propriété peut avoir deux valeurs :

- **Membre :** cette valeur indique un employé de l’organisation hôte et un utilisateur qui fait partie des effectifs de l’organisation. Par exemple, cet utilisateur ne peut accéder qu’à des sites internes. Il n’est pas considéré comme un collaborateur externe.
- **Invité :** cette valeur indique un utilisateur qui n’est pas considéré comme interne à l’entreprise, par exemple un collaborateur externe, un partenaire ou un client. Un tel utilisateur n’est pas censé recevoir de mémo interne du PDG ou bénéficier des avantages de la société, par exemple.  Notes La valeur UserType n’a aucun lien avec le mode de connexion de l’utilisateur, le rôle d’annuaire de l’utilisateur, etc. Cette propriété indique simplement la relation de l’utilisateur avec l’organisation hôte et permet à l’organisation d’appliquer des stratégies qui dépendent de cette propriété.

#### Identities

Cette propriété indique le fournisseur d’identité principal de l’utilisateur. Un utilisateur peut avoir plusieurs fournisseurs d’identité. Pour les voir, sélectionnez le lien à côté de la propriété Identities dans le profil utilisateur, ou interrogez la propriété identities via l’API Microsoft Graph.

| **Identité valeur de propriété** | **État de connexion** |
|---|---|
| Locataire externe d’Entra | Cet utilisateur est hébergé dans une organisation externe et s’authentifie à l’aide d’un compte Entra qui appartient à l’autre organisation. |
| Compte Microsoft | Cet utilisateur est hébergé dans un compte Microsoft et s’authentifie à l’aide d’un compte Microsoft. |
| {domaine de l’hôte} | Cet utilisateur s’authentifie à l’aide d’un compte Entra qui appartient à cette organisation. |
| google.com | Cet utilisateur dispose d’un compte Gmail et s’est inscrit en libre-service auprès de l’autre organisation. |
| facebook.com | Cet utilisateur dispose d’un compte Facebook et s’est inscrit en libre-service auprès de l’autre organisation. |
| mail | Cet utilisateur s'est inscrit à l'aide du code secret à usage unique d’Entra Email. |
| {URI de l’émetteur} | Cet utilisateur est hébergé dans une organisation externe qui n’utilise pas Entra ID comme fournisseur d’identité, mais un fournisseur d’identité SAML/WS-Fed. |

#### Des utilisateurs Entra B2B peuvent-ils être ajoutés en tant que membres plutôt qu’en tant qu’invités ?

En règle générale, un utilisateur Entra B2B est identique à un utilisateur invité. Par conséquent, un utilisateur Entra B2B Collaboration est ajouté par défaut en tant qu'utilisateur avec la propriété UserType = Invité. Toutefois, dans certains cas, l’organisation partenaire est un membre d’une organisation plus vaste à laquelle appartient également l’organisation hôte. Il est alors possible que l’organisation hôte veuille traiter les utilisateurs de l’organisation partenaire comme membres plutôt que comme invités. Utilisez les propriétés de l'utilisateur Entra pour changer un invité en membre.

#### Filtrer les utilisateurs invités dans l’annuaire

#### Convertir la propriété UserType

Les utilisateurs peuvent convertir la valeur Membre de la propriété UserType en valeur Invité, et inversement, en utilisant PowerShell. Toutefois, la propriété UserType représente la relation de l’utilisateur avec l’organisation. Vous ne devez donc changer cette propriété que si la relation de l’utilisateur avec l’organisation change. Si la relation de l’utilisateur change, les noms de principal d’utilisateur (UPN) doivent-ils changer ? L’utilisateur doit-il continuer à avoir accès aux mêmes ressources ? Une boîte aux lettres doit-elle être attribuée ? Nous déconseillons le changement de la valeur UserType à l’aide de PowerShell sous la forme d’une activité atomique. De plus, si cette propriété devient non modifiable par le biais de PowerShell, nous déconseillons l’utilisation d’une dépendance sur cette valeur.

### Supprimer des limitations pour les utilisateurs invités

Dans certains cas, vous souhaiterez peut-être donner aux utilisateurs invités des privilèges plus élevés. Vous pouvez ajouter un utilisateur invité à un rôle quelconque et même supprimer les restrictions d’utilisateur invité par défaut dans le répertoire afin d’attribuer à l’utilisateur les mêmes privilèges que les membres. Il est possible de désactiver les limitations par défaut afin qu’un utilisateur invité dans l’annuaire de la société ait les mêmes autorisations qu’un utilisateur membre. Supprimez la limitation dans les paramètres utilisateur dans le menu Entra ID.

### Groupes dynamiques et Entra B2B Collaboration

#### Qu'est-ce-que les groupes dynamiques ?

La configuration dynamique de l'appartenance à un groupe de sécurité pour Entra ID est disponible sur le [portail Azure](https://portal.azure.com/). Les administrateurs peuvent définir des règles pour remplir des groupes créés dans Entra ID, en fonction d’attributs utilisateur (par exemple, le userType, le département ou le pays/la région). Les membres peuvent être automatiquement ajoutés ou supprimés d’un groupe de sécurité en fonction de leurs attributs. Ces groupes permettent d’accorder l’accès à des applications ou à des ressources cloud (sites SharePoint, documents) et d’attribuer des licences à des utilisateurs.

La licence Entra ID Premium P1 ou P2 adaptée est nécessaire pour créer et utiliser des groupes dynamiques.


## Gestion des utilisateurs externes dans des charges de travail Microsoft 365

À l’instar d’Entra ID, Microsoft 365 peut inviter des utilisateurs dans l’annuaire à des fins de collaboration. Ces utilisateurs apparaissent comme externes dans la liste des utilisateurs. Ils ne possèdent pas de droits dans Microsoft 365. Toutefois, des droits de collaboration peuvent leur être accordés sur n’importe quelle charge de travail Microsoft 365. Les utilisateurs invités ont même la possibilité de recevoir des licences pour pouvoir effectuer des opérations spécifiques.

#### Options de collaboration externe dans Microsoft 365

Avec Microsoft 365, vos utilisateurs collaborent de différentes façons avec des personnes extérieures à votre organisation : partage de fichiers, invitation d’utilisateurs dans des équipes, réunions avec des participants externes et discussions avec des collaborateurs d’autres organisations. Le tableau suivant présente les principaux moyens d’accéder à vos ressources Microsoft 365 pour les personnes extérieures à votre organisation :

| **Activité** | **Type de compte** | **Paramètre par défaut** |
|---|---|---|
| Partage de fichiers et de dossiers authentifiés | Compte Invité | activé |
| Partage de site | Compte Invité | activé |
| Partage d’équipe | Compte Invité | activé |
| Canal partagé dans Teams | Compte Microsoft 365 externe existant | Désactivé |
| Conversations et réunions externes | Compte Microsoft 365 externe existant | activé |
| Participation à une réunion anonyme | Aucun | activé |
| Partage de fichiers et de dossiers non authentifiés | Aucun | activé |

Les personnes extérieures à votre organisation n’y ont pas accès, sauf si un utilisateur de votre organisation est à l’initiative de ces activités. Vous pouvez désactiver chaque paramètre dont vous ne souhaitez pas autoriser l’activité dans votre organisation.

#### Gouvernance et gestion

Comme avec n’importe quel compte dans Entra ID, vous devez les consulter et les gérer régulièrement. Configurez régulièrement des procédures pour valider tous les comptes d’utilisateurs, en particulier invités. Si un compte n’a pas besoin d’une fonctionnalité, supprimez-la. De même, supprimez les licences et les accès des utilisateurs, invités et membres pour lesquels ils ne sont plus nécessaires.

Outils permettant de gérer les utilisateurs invités Microsoft 365 :

- Centre d’administration Microsoft 365 : `https://admin.microsoft.com`
- Centre d’administration Entra : `https://entra.microsoft.com`
- Entra ID sur le portail Azure
- Script dans Microsoft Graph, PowerShell ou l’interface CLI
- La plupart des charges de travail Microsoft 365


## Exercice : Explorer les groupes dynamiques

L’objectif de cet exercice est de créer un groupe dynamique avec tous les utilisateurs en tant que membres.

1. Connectez-vous au [Centre d’administration Entra](https://entra.microsoft.com/) en utilisant un compte attribué au rôle d’administrateur d’utilisateurs dans le locataire.
2. Sélectionnez **Identité**.
3. Sous **Groupes**, sélectionnez **Tous les groupes**, puis **sélectionnez Nouveau groupe**.
4. Dans la page Nouveau groupe, sous **Type de groupe**, sélectionnez **Sécurité**.
5. Dans la zone **Nom du groupe**, entrez **Groupe dynamique de tous les utilisateurs de l'entreprise**.
6. Sélectionnez le menu **Type d’appartenance** , puis sélectionnez **Utilisateur dynamique**.
7. Sous **Membres de l’utilisateur** dynamique, sélectionnez **Ajouter une requête dynamique**.
8. Dans la zone de **syntaxe de règle** située à droite, sélectionnez **Modifier**.
9. Dans le volet Modifier la syntaxe de la règle, entrez l’expression suivante dans la zone **de syntaxe de règle** : user.objectId -ne null
10. Sélectionnez **OK**. La règle s’affiche dans la zone « Syntaxe de la règle ».

1. Sélectionnez **Enregistrer**. Le nouveau groupe dynamique inclut désormais les utilisateurs invités B2B, ainsi que les utilisateurs membres.
2. Dans la page Nouveau groupe, sélectionnez **Créer** pour créer le groupe.


## Implémenter et gérer l'identité vérifiée Entra

#### Qu’est-ce que l’ID vérifié Entra ?

Entra Verified ID protège votre organisation avec une solution d’identité fluide et décentralisée. Ce service vous permet d’émettre et de vérifier des informations d’identification. Pour les émetteurs, Entra ID fournit un service qu'ils peuvent personnaliser et utiliser pour émettre leurs propres justificatifs vérifiables. Pour les vérificateurs, le service fournit une API REST gratuite qui facilite la demande et l’acceptation de justificatifs vérifiables dans vos applications et services.

Nous utilisons des ID dans notre vie quotidienne. Nous avons des permis de conduire pour prouver que nous sommes capables de conduire une voiture. Les universités nous décernent des diplômes pour prouver que nous avons atteint un certain niveau d’étude. Nous utilisons des passeports pour prouver aux autorités qui nous sommes lorsque nous arrivons dans d’autres pays/régions. Le modèle de données décrit la manière dont nous pourrions gérer ces types de scénarios lorsque nous utilisons Internet, mais de façon sécurisée tout en respectant la vie privée de l’utilisateur. En résumé, les justificatifs vérifiables sont des objets de données constitués de revendications formulées par l’émetteur attestant des informations sur un sujet. Ces revendications sont identifiées par un schéma et incluent le DID, l’émetteur et le sujet. Le DID de l’émetteur créé une signature numérique en guise de preuve attestant de ces informations.

#### Déploiement du service d’ID vérifié Entra

Pour déployer le service d’ID vérifié Entra, vous avez besoin des éléments suivants :

- Locataire Azure avec un abonnement
- Une licence Entra ID Premium
- Connecté en tant qu’administrateur général
- Instance Azure Key Vault configurée

Pour configurer Vérification d’identité Entra, effectuez ces étapes :

1. Dans le portail Azure, recherchez des justificatifs vérifiables. Ensuite, sélectionnez Justificatifs vérifiables (préversion) .
2. Dans le menu de gauche, sélectionnez Démarrage.
3. Configurez votre organisation en fournissant les informations suivantes :     **Paramètre**  **Description de la valeur à entrer**     Nom de l’organisation Entrez un nom pour faire référence à votre entreprise dans le cadre des justificatifs vérifiables. Vos clients ne voient pas ce nom.   Domain Entrez un domaine ajouté à un point de terminaison de service dans votre identificateur décentralisé (DID). Le domaine est ce qui lie votre DID à un élément tangible que l’utilisateur peut connaître sur votre entreprise. Microsoft Authenticator et d’autres portefeuilles numériques utilisent ces informations pour s’assurer que votre DID est lié à votre domaine. Si le portefeuille peut vérifier le DID, il affiche un symbole vérifié. Dans le cas contraire, il informe l’utilisateur que des justificatifs ont été émis par une organisation qu’il n’a pas pu valider.   Coffre de clés Entrez le nom du coffre de clés de votre locataire.
4. Sélectionnez Enregistrer et créer un justificatif.

Notez qu’il s’agit uniquement des étapes générales nécessaires pour déployer le service d’ID vérifié Entra. Pour plus d’informations, consultez la liste d’articles ci-dessus.


## Configurer les fournisseurs d’identité

La fédération directe est désormais appelée **fédération de fournisseur d’identité (IdP) SAML/WS-Fed**. Vous pouvez configurer la fédération avec n’importe quelle organisation dont le fournisseur d’identité (IdP) prend en charge le protocole SAML 2.0 (Security Assertion Markup Language) ou WS-Fed (WS-Federation). Lorsque vous configurez la fédération IdP SAML/WS-Fed, les nouveaux utilisateurs invités de ce domaine se connectent à votre locataire Entra avec leur propre compte professionnel géré par le fournisseur d’identité, puis commencent à travailler avec vous. Il n’est pas nécessaire pour l’utilisateur invité de créer un compte Entra séparé.

### Quand un utilisateur invité est-il authentifié avec la fédération IdP SAML/WS-Fed ?

Une fois la fédération configurée avec le fournisseur d’identité SAML/WS-Fed de l’organisation, tous les nouveaux utilisateurs invités que vous invitez sont authentifiés à l’aide de ce fournisseur d’identité SAML/WS-Fed. Il est important de noter que configurer la fédération ne change pas la méthode d’authentification pour les utilisateurs invités qui ont déjà utilisé une invitation de votre part. Voici quelques exemples :

- Les utilisateurs invités ont déjà accepté des invitations de votre part, puis vous configurez plus tard la fédération avec le fournisseur d’identité SAML/WS-Fed de l’organisation. Ces utilisateurs invités continuent d’utiliser la même méthode d’authentification qu’ils utilisaient avant que vous configuriez la fédération.
- Vous configurez la fédération avec le fournisseur d’identité SAML/WS-Fed d’une organisation, puis invitez des utilisateurs, puis l’organisation partenaire passe à Entra ID. Les utilisateurs invités qui ont déjà accepté des invitations continuent d’utiliser le fournisseur d'identité SAML/WS-Fed, tant que la stratégie de fédération dans votre tenant (locataire) existe.
- Vous supprimez la fédération avec le fournisseur d’identité SAML/WS-Fed d’une organisation. Les utilisateurs invités qui utilisent actuellement le fournisseur d’identité SAML/WS-Fed ne peuvent pas se connecter.

Dans l’un de ces scénarios, vous pouvez mettre à jour la méthode d’authentification d’un utilisateur invité en réinitialisant l’état d’acceptation. La fédération IdP SAML/WS-Fed est liée aux espaces de noms de domaine, tels que contoso.com et fabrikam.com. Quand l’administrateur établit une fédération avec AD FS ou un fournisseur d’identité tiers, les organisations associent un ou plusieurs espaces de noms domaine à ces fournisseurs d’identité.

### Expérience de l’utilisateur final

Avec la fédération de fournisseur d’identité SAML/WS-Fed, les utilisateurs invités se connectent à votre client Entra à l’aide de leur propre compte professionnel. Lorsqu’ils accèdent à des ressources partagées, puis sont invités à se connecter, les utilisateurs sont redirigés vers leur fournisseur d’identité. Après s’être connectés, ils sont renvoyés vers Entra ID pour accéder aux ressources. Si la session Entra expire ou devient non valide et que l’authentification unique est activée pour le fournisseur d’identité fédéré, l’utilisateur bénéficie de l’authentification unique. Si la session de l’utilisateur fédéré est valide, l’utilisateur n’est pas invité à se reconnecter. Sinon, l’utilisateur est redirigé vers son IdP pour s’authentifier.

### Configuration de Security Assertion Markup Language 2.0

Entra B2B peut être configuré pour la fédération avec les fournisseurs d'identité qui utilisent le protocole SAML avec certaines exigences spécifiques indiquées ci-dessous.

Remarque

Vous pouvez associer plusieurs domaines à une configuration de fédération unique. Le domaine du partenaire peut être vérifié ou non vérifié par Entra.

#### Attributs et revendications requis Security Assertion Markup Language 2.0

Les tableaux suivants présentent la configuration requise pour les attributs spécifiques et les revendications qui doivent être configurés au niveau du fournisseur d’identité tiers. Pour configurer la fédération, les attributs suivants doivent être reçus dans la réponse SAML 2.0 du fournisseur d’identité. Ces attributs peuvent être configurés en liant le fichier XML du service d’émission de jeton de sécurité en ligne ou en les entrant manuellement. Vérifiez que la valeur correspond au cloud pour lequel vous configurez la fédération externe.

Attributs requis pour la réponse SAML 2.0 du fournisseur d’identité :

| **Attribut** | **Valeur d’un locataire de main-d’œuvre** | **Valeur d’un locataire externe** |
|---|---|---|
| AssertionConsumerService | `https://login.microsoftonline.com/login.srf` | `https://<tenantID>.ciamlogin.com/login.srf` |
| Public visé | `https://login.microsoftonline.com/<tenant ID>/` (recommandé). Les fédérations existantes qui utilisent le point de terminaison `urn:federation:MicrosoftOnline` global continuent de fonctionner, mais les nouvelles fédérations doivent utiliser le point de terminaison locataire. | `https://login.microsoftonline.com/<tenant ID>/` (recommandé). |
| Émetteur | L’URI de l’émetteur du fournisseur d’identité partenaire, par exemple `https://www.example.com/exk10l6w90DHM0yi...` | L’URI de l’émetteur du fournisseur d’identité partenaire, par exemple `https://www.example.com/exk10l6w90DHM0yi...` |

Revendications requises pour le jeton SAML 2.0 émis par le fournisseur d’identité :

| **Attribut** | **Valeur** |
|---|---|
| Format de NameID | `urn:oasis:names:tc:SAML:2.0:nameid-format:persistent` |
| adresse électronique | `https://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress` |

### Configuration de WS-Federation

Entra B2B peut être configuré pour la fédération avec les fournisseurs d'identité qui utilisent le protocole WS-Fed avec certaines exigences spécifiques indiquées ci-dessous. Actuellement, les deux fournisseurs WS-Fed qui ont été testés pour la compatibilité avec l’ID Entra sont AD FS et Shibboleth.

Le domaine du partenaire peut être vérifié ou non vérifié par Entra. Le domaine d’URL d’authentification passive du partenaire doit correspondre au domaine cible, ou à un hôte dans celui-ci. Sinon, le partenaire doit ajouter un enregistrement TXT DNS pour ce domaine afin d’activer la fédération.

#### Attributs et revendications requis pour WS-Federation

Les tableaux suivants présentent la configuration requise pour les attributs spécifiques et les revendications qui doivent être configurés au niveau du fournisseur d’identité WS-Fed tiers. Pour configurer la fédération, les attributs suivants doivent être reçus dans le message WS-Fed du fournisseur d’identité. Ces attributs peuvent être configurés en liant le fichier XML du service d’émission de jeton de sécurité en ligne ou en les entrant manuellement. Vérifiez que la valeur correspond au cloud pour lequel vous configurez la fédération externe.

Attributs requis dans le message WS-Fed du fournisseur d’identité :

| **Attribut** | **Valeur d’un locataire de main-d’œuvre** | **Valeur d’un locataire externe** |
|---|---|---|
| PassiveRequestorEndpoint | `https://login.microsoftonline.com/login.srf` | `https://<tenantID>.ciamlogin.com/login.srf` |
| Public visé | `https://login.microsoftonline.com/<tenant ID>/` (recommandé). Les fédérations existantes qui utilisent le point de terminaison `urn:federation:MicrosoftOnline` global continuent de fonctionner, mais les nouvelles fédérations doivent utiliser le point de terminaison locataire. | `https://login.microsoftonline.com/<tenant ID>/` (recommandé). |
| Émetteur | L’URI de l’émetteur du fournisseur d’identité partenaire, par exemple `https://www.example.com/exk10l6w90DHM0yi...` | L’URI de l’émetteur de l’IdP partenaire, par exemple `https://www.example.com/exk10l6w90DHM0yi...` |

Revendications requises pour le jeton WS-Fed émis par l’IdP :

| **Attribut** | **Valeur** |
|---|---|
| ImmutableID | `https://schemas.microsoft.com/LiveID/Federation/2008/05/ImmutableID` |
| adresse électronique | `https://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress` |

### Ajouter Google comme fournisseur d’identité pour les utilisateurs invités B2B

La fédération avec Google permet aux utilisateurs invités de se connecter à vos applications et ressources partagées avec leur propre compte Gmail, sans avoir besoin de créer un compte Microsoft.

Remarque

La fédération Google est conçue spécialement pour les utilisateurs Gmail. Pour fédérer avec les domaines G Suite, utilisez la [fédération directe](https://learn.microsoft.com/fr-fr/education/windows/configure-aad-google-trust).

### Quelle est l’expérience de l’utilisateur Google ?

Lorsque vous envoyez une invitation à des utilisateurs de Google Gmail, les utilisateurs invités doivent accéder à vos applications ou ressources partagées à l’aide d’un lien qui inclut le contexte locataire. Son expérience varie selon qu’il est ou non déjà connecté à Google :

- Les utilisateurs invités qui ne sont pas connectés à Google seront invités à le faire.
- Les utilisateurs invités déjà connectés à Google seront invités à choisir le compte qu’ils souhaitent utiliser. Il doit choisir le compte que vous avez utilisé pour l’inviter.

Les utilisateurs invités qui voient une erreur *header too long* (en-tête trop long) peuvent effacer leurs cookies ou ouvrir une fenêtre privée ou incognito, puis essayer de se reconnecter.

### Abandon de la prise en charge de la connexion via WebView

Google déprécie la prise en charge de la connexion à la vue web incorporée (à compter du 30 septembre 2021). Les utilisateurs de Google Gmail ne pourront pas se connecter si vos applications les authentifient avec une vue web intégrée et que vous utilisez la fédération Google avec Entra B2C ou Entra B2B pour les invitations d'utilisateurs externes ou l'inscription en libre-service.

Voici quelques scénarios connus ayant une incidence sur les utilisateurs de Gmail :

- Applications Microsoft (par exemple, Teams et Power Apps) sur Windows.
- Applications Windows qui utilisent le contrôle WebView, WebView2 ou l’ancien contrôle WebBrowser pour l’authentification. Ces applications doivent migrer vers l’utilisation du gestionnaire de comptes web (WAM).
- Applications Android utilisant l’élément d’interface utilisateur WebView.
- Applications iOS utilisant UIWebView/WKWebview.
- Applications utilisant la bibliothèque d’authentification Microsoft.

Ce changement n’affecte pas les types d’utilisateurs suivants :

- les applications web
- Microsoft 365 les services accessibles via un site web (par exemple, SharePoint en ligne, Office web apps et Teams application web)
- Applications mobiles utilisant des vues Web du système pour l’authentification (SFSafariViewController sur iOS, Custom Tabs sur Android).
- identités de Google Workspace, par exemple lorsque vous utilisez une fédération SAML avec Google Workspace.
- Applications Windows qui utilisent le gestionnaire de compte web (WAM) ou le répartiteur d’authentification web (WAB).

### Points de terminaison pour la connexion

Les utilisateurs invités de Google peuvent se connecter à vos applications multilocataires ou aux applications propriétaires de Microsoft via un point de terminaison commun, c’est-à-dire une URL d’application générale qui n’inclut pas le contexte de votre locataire. Pendant la connexion, l’utilisateur invité sélectionne les **options** de connexion, puis sélectionne **Se connecter à une organisation**. Ils entrent ensuite le nom de votre organisation et continuent de se connecter à l’aide de leurs informations d’identification Google.

Les utilisateurs invités Google peuvent également se servir des points de terminaison d’application qui incluent les informations de votre abonné, par exemple :

- `https://myapps.microsoft.com/?tenantid=<your tenant ID>`
- `https://myapps.microsoft.com/<your verified domain>.onmicrosoft.com`
- `https://portal.azure.com/<your tenant ID>`

Vous pouvez également donner aux utilisateurs invités Google un lien direct vers une application ou une ressource qui inclut vos informations de locataire, par exemple `https://myapps.microsoft.com/signin/X/<application ID>?tenantId=<your tenant ID>`.

#### Étape 1 : Configurer un projet de développeur Google

Tout d'abord, créer un projet dans la console des développeurs Google pour obtenir un ID client et une clé secrète client que vous pourrez ajouter plus tard à Entra ID.

1. Accédez aux API Google à l’adresse [https://console.developers.google.com](https://console.developers.google.com/) et connectez-vous avec votre compte Google. Nous vous recommandons d’utiliser un compte Google d’équipe partagé.
2. Acceptez les conditions d’utilisation du service si vous y êtes invité.
3. Créer un projet : dans le tableau de bord, sélectionnez **Créer un projet**, donnez un nom au projet (par exemple **Entra B2B**), puis sélectionnez **Créer** :

 4. Dans la page **API et services** , sélectionnez **Afficher** sous votre nouveau projet. 5. Sélectionnez **Accéder à la vue d’ensemble des API** sur la carte API. Sélectionnez **Écran d’autorisation OAuth**. 6. Sélectionnez **Externe**, puis **sélectionnez Créer**. 7. Dans **l’écran de consentement OAuth**, entrez un **nom d’application** :

 8. Faites défiler jusqu’à la section **Domaines autorisés** et entrez **microsoftonline.com** :

 9. Sélectionnez **Enregistrer**. 10. Sélectionnez **Les informations d’identification**. Dans le menu **Créer les informations d’identification**, sélectionnez **ID client OAuth** :

 11. Sous **Type d’application**, sélectionnez **Application web**. donnez à l'application un nom qui convient, comme **Entra B2B**. Sous **URI de redirection autorisés**, entrez les URI suivants :

- `https://login.microsoftonline.com`
- `https://login.microsoftonline.com/te/ tenant ID /oauth2/authresp` (où `https://login.microsoftonline.com/te/ tenant ID /oauth2/authresp` est votre ID de locataire dans Azure)

 12. Sélectionnez **Créer**. Copiez l’ID client et la clé secrète client. Vous les utiliserez lorsque vous ajouterez le fournisseur d’identité dans le portail Azure.

### Étape 2 : Configurer la fédération Google dans Entra ID

Maintenant vous définirez l’ID client Google et la clé secrète client. Pour cela, vous pouvez utiliser le portail Azure ou PowerShell. Pensez à tester votre configuration de fédération de Google en invitant vous-même. Utilisez une adresse Gmail et essayez de donner suite à l’invitation avec votre compte Google invité.

**Pour configurer la fédération de Google dans le portail Azure**

1. Accédez au [portail Azure](https://portal.azure.com/). Dans le volet gauche, sélectionnez **Entra ID**.
2. Sélectionnez **Identités externes**.
3. Sélectionnez **Tous les fournisseurs d’identité**, puis cliquez sur le bouton **Google**.
4. Entrez l’ID client et la clé secrète client obtenus précédemment. Sélectionnez **Enregistrer** :

### Comment supprimer la fédération de Google ?

Vous pouvez supprimer votre configuration de fédération de Google. Si vous le faites, les utilisateurs invités Google qui ont déjà utilisé leur invitation ne pourront plus se connecter. Mais vous pouvez leur donner accès à vos ressources à nouveau en les supprimant du répertoire et en les réinvitant.

**Pour supprimer la fédération Google dans Entra ID**

1. Accédez au [portail Azure](https://portal.azure.com/). Dans le volet gauche, sélectionnez **Entra ID**.
2. Sélectionnez **Identités externes**.
3. Sélectionnez **Tous les fournisseurs d’identité**.
4. Dans la ligne **Google**, sélectionnez le bouton représentant des points de suspension ( **...** ), puis choisissez **Supprimer**.

 5. Sélectionnez **Oui** pour confirmer la suppression.

### Ajouter Facebook en tant que fournisseur d’identité pour les identités externes

Vous pouvez ajouter Facebook à vos flux utilisateurs d’inscription en libre-service (préversion) afin que les utilisateurs puissent se connecter à vos applications en utilisant leurs propres comptes Facebook. Pour permettre aux utilisateurs de se connecter avec Facebook, vous devez activer l’inscription en libre-service pour votre locataire. Après avoir ajouté Facebook en tant que fournisseur d’identité, configurez un flux utilisateur pour l’application, puis sélectionnez Facebook comme l’une des options de connexion.

Remarque

Les utilisateurs peuvent uniquement utiliser leur compte Facebook pour s’inscrire via des applications utilisant l’inscription en libre-service et les parcours utilisateur. Les utilisateurs ne peuvent pas être invités à accepter leur invitation à l’aide d’un compte Facebook.

### Créer une application dans la console des développeurs Facebook

Pour utiliser un compte Facebook en tant que fournisseur d’identité, vous devez créer une application dans la console des développeurs Facebook. Si vous n’avez pas encore de compte Facebook, vous pouvez en créer un sur [https://www.facebook.com/](https://www.facebook.com/).

Remarque

Utilisez les URL suivantes aux étapes 9 et 16 ci-dessous.

- Dans **URL du site**, entrez l’adresse de votre application, par exemple `https://contoso.com`.
- Pour **URI de redirection OAuth valides**, entrez `https://login.microsoftonline.com/te/ tenant-id /oauth2/authresp`. Vous trouverez votre `tenant-ID` dans la page Vue d’ensemble d’Entra ID.

1. Connectez-vous à [Facebook pour les développeurs](https://developers.facebook.com/) avec les informations d’identification de votre compte Facebook.
2. Si ce n’est déjà fait, vous devez vous inscrire en tant que développeur Facebook. Sélectionnez **Prise en main** en haut à droite de la page, acceptez les politiques de Facebook et suivez la procédure d’inscription.
3. Sélectionnez **Mes applications**, puis **Créer une application**.
4. Entrez un **nom d’affichage** et une **adresse e-mail de contact** valide.
5. Sélectionnez **Créer un ID d'application**. Vous devez accepter les règles de la plateforme Facebook et effectuer une vérification de sécurité en ligne.
6. Sélectionnez **Paramètres**, puis **De base**.
7. Choisissez une **catégorie**, par exemple, Entreprise et pages. Cette valeur est requise par Facebook. Cependant, elle n'est pas utilisée pour Entra ID.
8. Au bas de la page, sélectionnez **Ajouter une plateforme**, puis sélectionnez **Site web**.
9. Dans **URL du site**, entrez l’URL appropriée (indiquée ci-dessus).
10. Dans **URL de la politique de confidentialité**, entrez l’URL de la page dans laquelle vous gérez les informations de confidentialité de votre application, par exemple `https://www.contoso.com`.
11. Sélectionnez **Enregistrer les modifications**.
12. En haut de la page, copiez la valeur de l’**ID de l’application**.
13. Sélectionnez **Afficher**, puis copiez la valeur **Clé secrète de l’application**. Vous avez besoin de ces deux valeurs pour configurer Facebook en tant que fournisseur d’identité dans votre client. **App Secret** est une information d’identification de sécurité essentielle.
14. Cliquez sur le signe plus en regard de la zone **PRODUITS**, puis sélectionnez **Configurer** sous **Connexion Facebook**.
15. Sous **Connexion Facebook**, sélectionnez **Paramètres**.
16. Dans **URI de redirection OAuth valides**, entrez l’URL appropriée (indiquée ci-dessus).
17. Sélectionnez **Enregistrer les modifications** en bas de la page.
18. Pour rendre votre application Facebook accessible à Entra ID, sélectionnez le sélecteur État dans le coin supérieur droit de la page, **activez-le** pour rendre l'application publique, puis sélectionnez **Changer de mode**. À ce stade, l’état doit passer de **Développement** à **Production**.

### Configuration d’un compte Facebook en tant que fournisseur d’identité

Vous devez maintenant définir l'ID et le secret du client Facebook, soit en les saisissant dans le Centre d'administration d’Entra, soit en utilisant PowerShell. Vous pouvez tester votre configuration Facebook en vous inscrivant via un flux d’utilisateurs sur une application prenant en charge l’inscription en libre-service.

#### Pour configurer la fédération Facebook sur l’écran Entra ID

1. Connectez-vous au [portail Azure](https://portal.azure.com/) en tant qu'administrateur général de votre locataire Entra.
2. Sous **Services Azure**, sélectionnez **Entra ID**.
3. Dans le menu de gauche, sélectionnez **Identités externes**.
4. Sélectionnez **Tous les fournisseurs d’identité**, puis **Facebook**.
5. Dans **ID client**, entrez l’**ID** de l’application Facebook que vous avez créée précédemment.
6. Dans **Clé secrète client**, entrez la **Clé secrète d’application** que vous avez consignée.

 7. Sélectionnez **Enregistrer**.

### Comment supprimer la Fédération Facebook ?

Vous pouvez supprimer votre configuration de fédération avec Facebook. Si vous le faites, les utilisateurs qui se sont inscrits via des flux d’utilisateurs avec leur compte Facebook ne pourront plus se connecter.

#### Pour supprimer la fédération Facebook dans Entra ID :

1. Accédez au [portail Azure](https://portal.azure.com/). Dans le volet gauche, sélectionnez **Entra ID**.
2. Sélectionnez **Identités externes**.
3. Sélectionnez **Tous les fournisseurs d’identité**.
4. Dans la ligne **Google**, sélectionnez le menu contextuel ( **...** ), puis **Supprimer**.
5. Sélectionnez **Oui** pour confirmer la suppression.


## Implémenter des contrôles d’accès interlocataires

Les organisations Entra peuvent utiliser les paramètres d’accès interlocataire des identités externes pour gérer leur collaboration avec d’autres organisations Entra ou clouds Microsoft. Ces paramètres vous offrent un contrôle précis sur la façon dont les organisations Entra externes coopèrent avec vous (**accès entrant**). Vous pouvez également maîtriser la manière dont vos utilisateurs travaillent avec des organisations Entra externes (**accès sortant**).

#### Gestion des paramètres entrants et sortants

Par défaut, la collaboration B2B avec d’autres organisations Entra est activée, et la connexion directe B2B est bloquée. Toutefois, les paramètres d’administration complets suivants vous permettent de gérer ces deux fonctionnalités.

| **Nom du paramètre d’accès interlocataire** | **Opérations gérées** |
|---|---|
| Paramètres d’accès sortant | Contrôlent si les utilisateurs peuvent accéder aux ressources d’une organisation externe. Applicables à tout le monde ou à des utilisateurs, groupes et applications individuels. |
| Paramètres d’accès entrant | Contrôlent si les utilisateurs des organisations Entra externes peuvent accéder aux ressources de l’organisation. Vous pouvez appliquer ces paramètres à tout le monde ou spécifier des utilisateurs, des groupes et des applications individuels. |
| Paramètres d’approbation (entrants) | Déterminent si les stratégies d’accès conditionnel approuvent l’authentification multifacteur (MFA, Multi-Factor Authentication). Vous pouvez également exiger un dispositif conforme et un appareil hybride joint à Entra. Enfin, autorisez ou limitez les utilisateurs d’une organisation externe s’ils ont déjà satisfait à ces exigences dans leurs locataires d’origine. |
| Connexion directe B2B | Configurez une relation d’approbation mutuelle avec une autre organisation Entra pour une collaboration fluide. Cette fonctionnalité fonctionne actuellement avec les canaux partagés Microsoft Teams. |

#### Configuration spécifique de l’organisation

Nous avons exploré les paramètres par défaut. Ils sont appliqués à toutes les connexions externes. Toutefois, vous pouvez également configurer des paramètres de collaboration propres à l’organisation. Sur l’écran **Contrôle d’accès interlocataire**, choisissez **Paramètres organisationnels**, puis ajoutez le locataire. Vous pouvez alors configurer les paramètres entrants et sortants.

#### Configuration propre au cloud Microsoft

Votre entreprise a des contrats publics qui doivent être reliés à Microsoft Azure Government ou à Microsoft Azure Chine. Utilisez les **Paramètres du cloud Microsoft** pour vous connecter aux paramètres de collaboration et les configurer.

#### Connexion directe B2B

La connexion directe B2B nécessite une relation d’approbation mutuelle entre deux organisations Entra pour autoriser l’accès aux ressources de l’autre. L’organisation de la ressource et l’organisation externe doivent activer mutuellement la connexion directe B2B dans leurs paramètres d’accès interlocataire. Lorsque la confiance est établie, l’utilisateur de la connexion directe B2B dispose d’un accès d’authentification unique aux ressources en dehors de son organisation en utilisant les informations d’identification de leur organisation Entra.

Actuellement, les fonctionnalités de la connexion directe B2B fonctionnent avec des canaux partagés Teams. Lorsque la connexion directe B2B est établie entre deux organisations, les utilisateurs d’une organisation peuvent créer un canal partagé dans Teams et y inviter un utilisateur de connexion directe B2B externe. Depuis Teams, l’utilisateur de la connexion directe B2B accède ensuite en toute transparence au canal partagé dans sa propre instance Teams, sans se connecter manuellement à l’organisation qui héberge ce canal.


## Contrôle des connaissances

Choisissez la meilleure réponse pour chacune des questions ci-dessous.

### Contrôle des connaissances


## Récapitulatif et ressources

Maintenant que vous avez passé en revue ce module, vous pouvez :

- Gérer les paramètres de collaboration externe dans Entra ID
- Inviter des utilisateurs externes (individuellement ou en bloc)
- Gérer les comptes d’utilisateur externes dans l’ID Entra
- Configurer les fournisseurs d’identité (social et SAML/WS-FED)
- Découvrir l’ID vérifié Entra

### Ressources

Utilisez ces ressources pour approfondir vos connaissances :

- [Documentation sur les identités externes](https://learn.microsoft.com/fr-fr/entra/external-id/)
- [Activer la collaboration externe B2B et gérer qui peut inviter des utilisateurs invités](https://learn.microsoft.com/fr-fr/entra/external-id/external-collaboration-settings-configure)
- [Qu’est-ce qu’un accès utilisateur invité dans l’ID Entra](https://learn.microsoft.com/fr-fr/entra/external-id/user-properties)
- [Configurer le service Vérification d’identité Entra](https://learn.microsoft.com/fr-fr/entra/verified-id/verifiable-credentials-configure-tenant)
- [Accès interlocataires avec Entra External Identities](https://learn.microsoft.com/fr-fr/entra/architecture/external-identity-deployment-architectures)


---

# Implémenter et gérer l’identité hybride

_https://learn.microsoft.com/fr-fr/training/modules/implement-manage-hybrid-identity/_


## Présentation

L’identité hybride permet aux entreprises d’avoir des solutions d’identité qui s’étendent sur des environnements locaux et basés sur le cloud. Cette fonctionnalité fournit des fonctionnalités d’authentification et d’autorisation unifiées aux ressources, quel que soit leur emplacement.

Les organisations ajoutent aujourd’hui une application cloud à leurs applications locales existantes, ce qui les rend hybrides. Ils doivent disposer de solutions d’identité qui authentifient et autorisent les utilisateurs à accéder aux applications et aux données sous-jacentes de manière sécurisée. Une solution Active Directory locale n’est pas suffisante ; l’extension vers le cloud avec l’ID Entra est nécessaire pour fournir une solution d’identité hybride.

Dans ce module, vous implémentez et gérez une solution d’identité hybride à l’aide d’Entra ID et d’Entra Connect. Vous découvrez comment utiliser la synchronisation de hachage de mot de passe (PHS) et l’authentification directe (PTA) pour vous assurer que vous disposez de la bonne méthode d’authentification pour vos besoins. Ensuite, vous explorez comment l’authentification unique (SSO) permet à vos utilisateurs d’accéder aux applications dont ils ont besoin lors de l’utilisation de méthodes d’accès sécurisées. Ensuite, vous voyez comment vous connecter à d’autres répertoires externes existants avec Active Directory services fédérés (ADFS). Enfin, vous découvrez comment Entra Connect Health surveille l’intégrité de votre solution d’identité et comment résoudre certaines erreurs de synchronisation courantes.

À la fin de ce module, vous pouvez implémenter et gérer une solution d’identité hybride.

### Objectifs d’apprentissage

Dans ce module, vous allez :

- Planifier, concevoir et implémenter Entra Connect
- Gérer Entra Connect
- Implémenter et gérer la synchronisation de hachage de mot de passe (PHS)
- Implémenter et gérer l’authentification directe (PTA)
- Implémenter et gérer l’authentification unique transparente (SSO transparente)
- Implémenter et gérer la fédération à l’exception des déploiements AD FS manuels
- Résoudre les erreurs de synchronisation
- Implémenter et gérer Entra Connect Health

### Conditions préalables

Aucun


## Planifier, concevoir et implémenter Entra Connect

Entra Connect est une solution qui relie une organisation locale Active Directory à votre ID Entra basé sur le cloud. Le service informatique peut synchroniser des identités locales vers Azure et garantir une identité cohérente sur les deux plateformes. Cette connexion permet des services tels que la synchronisation des hachages de mots de passe, l’authentification directe et l’authentification unique (SSO) transparente.

Entra est l’outil de Microsoft conçu pour vous permettre d’atteindre et de remplir vos objectifs en matière d’identité hybride. Il offre les fonctionnalités suivantes :

- Synchronisation : responsable de la création d’utilisateurs, de groupes et d’autres objets. Ensuite, assurez-vous que les informations d’identité de vos utilisateurs et groupes locaux correspondent au cloud. Cette synchronisation inclut également les hachages de mot de passe.
- Synchronisation de hachage de mot de passe : méthode de connexion qui synchronise un hachage du mot de passe AD local d’un utilisateur avec l’ID Entra.
- Authentification directe : méthode de connexion qui permet aux utilisateurs d’utiliser le même mot de passe local et dans le cloud, mais qui ne nécessite pas l’infrastructure supplémentaire d’un environnement fédéré.
- Intégration de fédération : la fédération est une partie facultative d’Entra Connect et peut être utilisée pour configurer un environnement hybride à l’aide d’une infrastructure AD FS locale. Elle offre également des fonctionnalités de gestion AD FS telles que le renouvellement de certificat et les déploiements de serveurs AD FS supplémentaires.
- Surveillance de la santé - Entra Connect-Health offre une surveillance efficace.

### Pourquoi utiliser Entra Connect ?

L’intégration de vos annuaires locaux avec Entra ID améliore la productivité de vos utilisateurs en leur fournissant une identité commune pour accéder aux ressources cloud et locales. Avec Entra Connect, les utilisateurs peuvent utiliser une identité unique pour accéder aux applications locales et aux services cloud tels que Microsoft 365. En outre, les organisations peuvent offrir une expérience de déploiement simple pour la synchronisation et la connexion à l’aide d’un seul outil. Entra Connect remplace les versions antérieures des outils d’intégration d’identité ; et est inclus dans votre abonnement Entra ID.

### Sélectionner une méthode d'authentification

L’identité est le nouveau plan de contrôle de la sécurité informatique, de sorte que l’authentification est la garde d’accès d’une organisation au nouveau monde cloud. Les organisations ont besoin d’un plan de contrôle d’identité qui renforce leur sécurité et protège leurs applications cloud contre les intrus. Lorsque la solution d’identité hybride Entra est votre nouveau plan de contrôle, l’authentification est la base de l’accès cloud. Choisir la méthode d’authentification appropriée est une première décision cruciale dans la configuration d’une solution d’identité hybride Entra. Pour choisir une méthode d’authentification, vous devez prendre en compte le temps, l’infrastructure existante, la complexité et le coût d’implémentation de votre choix. Ces facteurs sont différents pour chaque organisation et peuvent varier au fil du temps.

#### L'authentification du cloud

Lorsque vous choisissez cette méthode d’authentification, l’ID Entra gère le processus de connexion des utilisateurs. Lorsque vous couplez l’authentification unique transparente, les utilisateurs peuvent se connecter à des applications cloud sans avoir à entrer leurs informations d’identification. Avec l’authentification cloud, vous pouvez choisir parmi deux options :

**Synchronisation de hachage de mot de passe Entra (PHS)**. La façon la plus simple d’activer l’authentification pour les objets d’annuaire locaux dans Entra. Les utilisateurs peuvent utiliser le même nom d’utilisateur et le même mot de passe qu’ils utilisent localement sans avoir à déployer plus d’infrastructure.

- **Effort** : la synchronisation de hachage de mot de passe nécessite le moins d’efforts concernant le déploiement, la maintenance et l’infrastructure. Ce niveau d’effort s’applique généralement aux organisations qui n’ont besoin que de leurs utilisateurs pour se connecter à Microsoft 365, aux applications SaaS et à d’autres ressources basées sur les ID Entra. Quand elle est activée, la synchronisation de hachage de mot de passe fait partie du processus de synchronisation Entra Connect et s’exécute toutes les deux minutes.
- **Expérience utilisateur** : pour améliorer l’expérience de connexion des utilisateurs, déployez l’authentification unique transparente avec la synchronisation de hachage de mot de passe. L’authentification unique transparente élimine les invites inutiles lorsque les utilisateurs sont connectés.
- **Scénarios avancés** : si les organisations choisissent de le faire, il est possible d’utiliser des insights à partir d’identités avec des rapports Entra Identity Protection avec Entra ID Premium P2. Par exemple, le rapport sur les informations d’identification divulguées. Windows Hello Entreprise a des exigences spécifiques lorsque vous utilisez la synchronisation de hachage de mot de passe. Entra Domain Services nécessite la synchronisation de hachage de mot de passe pour créer des utilisateurs avec leurs informations d’identification d’entreprise dans le domaine managé.
- **Continuité de l’activité** : la synchronisation de hachage de mot de passe avec l’authentification cloud est hautement disponible, car il s’agit d’un service cloud qui s’adapte à tous les centres de données Microsoft. Pour éviter une panne prolongée de la synchronisation de hachage de mot de passe, déployez un deuxième serveur Entra Connect en mode intermédiaire, dans une configuration de secours.
- **Considérations :** Actuellement, la synchronisation de hachage de mot de passe n’applique pas immédiatement les modifications apportées aux états de compte local. Dans ce cas, un utilisateur a accès aux applications cloud jusqu’à ce que l’état du compte d’utilisateur soit synchronisé avec l’ID Entra. Les organisations peuvent vouloir surmonter cette limitation en exécutant un nouveau cycle de synchronisation après que les administrateurs effectuent des mises à jour en bloc vers des états de compte d’utilisateur locaux. Un exemple montre comment désactiver les comptes.

**Authentification directe (PTA) Entra**. Fournit une validation de mot de passe simple pour les services d’authentification Entra à l’aide d’un agent logiciel qui s’exécute sur un ou plusieurs serveurs locaux. Les serveurs valident les utilisateurs directement avec votre Active Directory local, ce qui garantit que la validation du mot de passe ne se produit pas dans le cloud. Cette méthode d’authentification convient pour les entreprises qui, pour des raisons de sécurité, requièrent l’application immédiate d’heures d’ouverture de session, de stratégies de mot de passe et d’états des comptes d’utilisateur locaux.

- **Effort** : pour l’authentification directe, vous avez besoin d’un ou plusieurs agents légers (nous vous recommandons trois) installés sur des serveurs existants. Ces agents doivent avoir accès à vos services de domaine Active Directory locaux, y compris à vos contrôleurs de domaine AD locaux. Ils ont besoin d’un accès sortant à Internet et d’un accès à vos contrôleurs de domaine. Pour cette raison, le déploiement des agents dans un réseau de périmètre n'est pas pris en charge.
- **Expérience utilisateur** : pour améliorer l’expérience de connexion des utilisateurs, déployez l’authentification unique transparente avec l’authentification directe. L’authentification unique transparente élimine les invites inutiles une fois que les utilisateurs se connectent.
- **Scénarios avancés** : l’authentification directe applique la stratégie de compte local au moment de la connexion. Par exemple, l’accès est refusé quand l’état d’un compte d’utilisateur local est désactivé, verrouillé ou que son mot de passe expire. L’accès peut également être refusé si la tentative de connexion tombe en dehors des heures où l’utilisateur est autorisé à se connecter.
- **Continuité de l’activité** : nous vous recommandons de déployer deux agents d’authentification directe supplémentaires. Ces extras sont ajoutés au premier agent sur le serveur Entra Connect. Ce déploiement garantit la haute disponibilité des demandes d’authentification. Lorsque vous avez déployé trois agents, un agent peut toujours échouer quand un autre agent est arrêté pour maintenance.
- **Considérations :** la synchronisation de hachage de mot de passe peut servir de méthode d’authentification de sauvegarde pour l’authentification directe, lorsqu’une défaillance locale importante empêche les agents de valider les informations d’identification d’un utilisateur. Le basculement vers la synchronisation de hachage de mot de passe ne se produit pas automatiquement et vous devez utiliser Entra Connect pour basculer manuellement la méthode de connexion.

#### Authentification fédérée

Avec cette méthode d’authentification, Entra ID remet le processus d’authentification à un système d’authentification approuvé distinct, tel que les services de fédération Active Directory (AD FS) locaux, qui valide le mot de passe de l’utilisateur. Le système d’authentification peut fournir d’autres exigences d’authentification avancées. Par exemple, l’authentification par carte à puce ou l’authentification multifacteur tierce.

- **Effort** : un système d’authentification fédéré s’appuie sur un système de confiance externe pour authentifier les utilisateurs. Certaines entreprises souhaitent réutiliser leur investissement de système fédéré existant avec leur solution d’identité hybride Entra. La maintenance et la gestion du système fédéré se trouvent en dehors du contrôle de l’ID Entra. Il en incombe à l’organisation d’utiliser le système fédéré pour vérifier qu’il est déployé de manière sécurisée et qu’il peut gérer la charge de l’authentification.
- **Expérience utilisateur** : l’expérience utilisateur de l’authentification fédérée dépend de l’implémentation des fonctionnalités, de la topologie et de la configuration de la batterie de serveurs de fédération. Certaines organisations ont besoin de cette flexibilité pour adapter et configurer l’accès à la batterie de serveurs de fédération en fonction de leurs exigences de sécurité. Par exemple, il est possible de configurer en interne des utilisateurs connectés et des appareils capables de connecter automatiquement les utilisateurs. Aucune information d’identification n’est donc demandée aux utilisateurs. Cette configuration fonctionne parce qu'ils se sont déjà connectés à leurs appareils. Si nécessaire, certaines fonctionnalités de sécurité avancées rendent le processus de connexion des utilisateurs plus difficile.
- **Scénarios avancés** : une solution d’authentification fédérée est requise lorsque les clients ont une exigence d’authentification qu’Entra ID ne prend pas en charge en mode natif.
  - Authentification nécessitant des cartes à puce ou des certificats.
  - Serveurs MFA locaux ou fournisseurs multifacteurs tiers nécessitant un fournisseur d’identité fédéré.
  - Authentification à l’aide de solutions d’authentification tierces.
  - Connexion nécessitant un sAMAccountName, par exemple DOMAINE\nomutilisateur, et non avec un nom d’utilisateur principal (UPN) comme user@domain.com.

- **Continuité de l’activité** : les systèmes fédérés nécessitent généralement un tableau à charge équilibrée de serveurs, appelé batterie de serveurs. Cette batterie de serveurs est configurée dans une topologie de réseau interne et de réseau de périmètre pour garantir la haute disponibilité des demandes d’authentification.
- **Considérations : Les systèmes fédérés** nécessitent généralement un investissement plus important dans l’infrastructure locale. La plupart des organisations choisissent cette option s’ils ont déjà un investissement de fédération local. Et qu’elles sont contraintes d’utiliser un fournisseur d’identité unique pour des raisons commerciales. La fédération est plus difficile à utiliser et à dépanner que les solutions d’authentification cloud.

### Diagrammes d’architecture

Les diagrammes suivants décrivent les composants d’architecture de haut niveau requis pour chaque méthode d’authentification que vous pouvez utiliser avec votre solution d’identité hybride Entra. Ils fournissent une vue d’ensemble pour vous aider à comparer les différences entre les solutions.

- Simplicité d’une solution de synchronisation de hachage de mot de passe :
- Configuration requise de l’agent d’authentification directe en utilisant deux agents pour la redondance :
- Composants requis pour la fédération dans votre périmètre et réseau interne de votre organisation :

### Recommendations

Votre système d’identité garantit l’accès de vos utilisateurs aux applications cloud et aux applications métier que vous migrez et rendez disponibles dans le cloud. Pour permettre aux utilisateurs autorisés de rester productifs et d'empêcher les acteurs malveillants d'accéder aux données sensibles de votre organisation, l'authentification contrôle l'accès aux applications.

Utilisez ou activez la synchronisation de hachage de mot de passe pour quelle méthode d’authentification vous choisissez, pour les raisons suivantes :

- **Haute disponibilité et récupération d’urgence** : l’authentification directe et la fédération s’appuient sur l’infrastructure locale. Pour l’authentification directe, l’empreinte locale inclut le matériel du serveur et la mise en réseau requises par les agents d’authentification directe. Pour la fédération, l’empreinte locale est encore plus grande. Il nécessite des serveurs dans votre réseau de périmètre pour les demandes d’authentification proxy et les serveurs de fédération internes. Pour éviter les points de défaillance uniques, déployez des serveurs redondants. Ensuite, les demandes d’authentification sont toujours serviceées si un composant échoue. L’authentification directe et la fédération s’appuient également sur les contrôleurs de domaine pour répondre aux demandes d’authentification, ce qui peut également échouer. Bon nombre de ces composants ont besoin d’une maintenance pour rester en bonne santé. Les pannes sont plus probables lorsque la maintenance n’est pas planifiée et implémentée correctement. Évitez les pannes en utilisant la synchronisation de hachage du mot de passe, car le service d'authentification cloud Entra est mis à l'échelle globalement et est toujours disponible.
- Survie de panne locale : une panne locale due à une **cyber-attaque** ou à une catastrophe peut avoir des conséquences importantes, des dommages de marque de réputation jusqu’à une organisation paralysée, incapable de traiter l’attaque. Récemment, de nombreuses organisations ont été victimes d’attaques contre des programmes malveillants, y compris des ransomwares ciblés, ce qui a provoqué l’arrêt de leurs serveurs locaux. Lorsque Microsoft aide les clients à traiter ces types d’attaques, il voit deux catégories d’organisations :
  - Les organisations qui ont activé la synchronisation de hachage de mot de passe, avec l’authentification fédérée ou directe changent leur authentification principale. Ils peuvent ensuite utiliser la synchronisation de hachage de mot de passe. Ils étaient de retour en ligne en quelques heures. En utilisant l’accès à la messagerie via Microsoft 365, ils ont travaillé pour résoudre les problèmes et accéder à d’autres charges de travail basées sur le cloud.
  - Les organisations qui n’ont pas précédemment activé la synchronisation de hachage de mot de passe ont dû recourir à des systèmes de messagerie de consommateurs externes non approuvés pour résoudre les problèmes. Dans ce cas, il leur a fallu des semaines pour restaurer leur infrastructure d’identité locale avant que les utilisateurs ne puissent se connecter à nouveau aux applications cloud.

- **Protection des identités** : l’une des meilleures façons de protéger les utilisateurs dans le cloud est Entra Identity Protection avec Entra Premium P2. Microsoft analyse continuellement Internet pour rechercher les listes d’utilisateurs et de mots de passe que les acteurs malveillants vendent et rendent disponibles sur le web sombre. Entra ID peut utiliser ces informations pour vérifier si l’un des noms d’utilisateur et mots de passe de votre organisation est compromis. Par conséquent, il est essentiel d’activer la synchronisation de hachage de mot de passe, quelle que soit la méthode d’authentification que vous utilisez, qu’elle soit fédérée ou directe. Les informations d’identification divulguées sont présentées sous forme de rapport. Utilisez ces informations pour bloquer ou forcer les utilisateurs à modifier leurs mots de passe lorsqu’ils essaient de se connecter avec des mots de passe divulguées.

### Concepts de conception d’Entra Connect

Cette section décrit les domaines à prendre en compte lors de la conception d’implémentation d’Entra Connect. Il s’agit d’une présentation approfondie de certains domaines et de ces concepts sont brièvement décrits dans d’autres documents.

### sourceAnchor

L’attribut sourceAnchor est défini en tant qu’ *attribut immuable pendant la durée de vie d’un objet*. Il identifie de façon univoque un objet comme étant le même objet local et dans Entra ID. L’attribut est également appelé **immuableId** et les deux noms sont utilisés interchangeables. L’attribut est utilisé pour les scénarios suivants :

- Quand un nouveau serveur de moteur de synchronisation est créé ou recréé après un scénario de récupération d’urgence, cet attribut lie les objets existants dans Entra ID à des objets locaux.
- Si vous passez d’une identité de cloud uniquement à un modèle d’identité synchronisé, alors cet attribut permet une correspondance exacte et concrète des objets existants dans Entra ID avec des objets locaux.
- Si vous utilisez la fédération, cet attribut avec **userPrincipalName** est utilisé dans la revendication pour identifier un utilisateur de manière unique.

La valeur de l’attribut doit respecter les règles suivantes :

- Moins de 60 caractères de longueur
  - Les caractères qui ne sont pas a-z, A-Z ou 0-9 sont encodés et comptés comme trois caractères

- Ne contient pas de caractère spécial : `\ ! # $ % & * + / = ? ^ { } | ~ > < ( ) ' ; : , [ ] " @ _`
- elle doit être globalement unique
- elle doit être une chaîne, un entier ou une valeur binaire
- Ne doit pas être basé sur le nom de l’utilisateur, car les noms peuvent changer
- Ne doit pas respecter la casse et doit éviter les valeurs qui varient selon la casse
- elle doit être assignée lorsque l’objet est créé.

Si vous disposez d’une seule forêt locale, l’attribut que vous devez utiliser est **objectGuid**. Vous pouvez également utiliser l’attribut objectGuid lorsque vous utilisez des paramètres express dans Entra Connect. Et également l’attribut utilisé par DirSync. Si vous avez plusieurs forêts et que vous ne déplacez pas d’utilisateurs entre des forêts et des domaines, **objectGUID** est un bon attribut à utiliser. Une autre solution consiste à choisir un attribut existant, dont vous êtes sûr qu’il ne changera pas. Les attributs couramment utilisés incluent **employeeID**. Si vous envisagez d’opter pour un attribut contenant des lettres, assurez-vous qu’il n’y a aucun risque de changement de la casse (majuscule ou minuscule) pour la valeur de l’attribut. Les attributs incorrects incluent ces attributs avec le nom de l’utilisateur. Une fois l’attribut sourceAnchor choisi, l’Assistant stocke les informations dans votre client Entra. Les informations seront utilisées dans le cadre d’une installation future d’Entra Connect.

### Connexion à Entra

Les paramètres de synchronisation de votre intégration d’annuaire local avec l’ID Entra peuvent affecter la façon dont l’utilisateur s’authentifie. Entra utilise userPrincipalName (UPN) pour authentifier l’utilisateur. Toutefois, lorsque vous synchronisez vos utilisateurs, vous devez choisir avec soin l’attribut à utiliser pour la valeur de userPrincipalName. Lorsque vous sélectionnez l’attribut fournissant la valeur d’UPN à utiliser dans Azure, vous devez vous assurer que :

- Les valeurs d’attribut sont conformes à la syntaxe UPN (RFC 822), le format username@domain
- Le suffixe des valeurs correspond à l’un des domaines personnalisés vérifiés dans Entra ID

Dans la configuration rapide, le choix supposé de l’attribut est userPrincipalName. Si l’attribut userPrincipalName ne contient pas la valeur que vos utilisateurs doivent se connecter à Azure, vous devez choisir **Installation personnalisée**.

#### État du domaine personnalisé et nom d’utilisateur principal

Vérifiez qu’il existe un domaine vérifié pour le suffixe UPN (User Principal Name). John est un utilisateur de contoso.com. Vous souhaitez que John utilise l’UPN john@contoso.com local pour vous connecter à Azure après avoir synchronisé les utilisateurs avec votre annuaire Entra contoso.onmicrosoft.com. Pour ce faire, vous devez ajouter et vérifier contoso.com comme domaine personnalisé dans Entra ID avant de commencer la synchronisation des utilisateurs. Si le suffixe UPN de John, par exemple contoso.com, ne correspond pas à un domaine vérifié dans Entra ID, l’outil remplace le suffixe UPN par contoso.onmicrosoft.com.

Certaines organisations ont des domaines non routables, comme contoso.local, ou de simples domaines à étiquette unique, comme contoso. Vous ne pouvez pas vérifier un domaine non routable. Entra Connect peut uniquement se synchroniser sur un domaine vérifié dans Entra ID. Lorsque vous créez un annuaire Entra, il crée un domaine routable qui devient le domaine par défaut de votre Entra ID, par exemple contoso.onmicrosoft.com. Par conséquent, il devient nécessaire de vérifier tous les autres domaines routables dans un scénario de ce type, si vous ne souhaitez pas effectuer de synchronisation avec le domaine par défaut onmicrosoft.com.

Entra Connect détecte si vous exécutez un environnement de domaine non routable, et vous avertit en temps utile si vous tentez de poursuivre la configuration rapide. Si vous utilisez un domaine non routable, il est probable que l’UPN, des utilisateurs, possède également un suffixe non routable. Par exemple, si vous exécutez sous contoso.local, Entra Connect vous suggère d’utiliser des paramètres personnalisés plutôt que d’utiliser des paramètres express. Avec les paramètres personnalisés, vous êtes en mesure de spécifier l’attribut à utiliser comme UPN pour la connexion à Azure une fois les utilisateurs synchronisés avec Entra ID.

### Topologies pour Entra Connect

Cette section décrit différentes topologies locales et Entra ID qui utilisent la synchronisation Entra Connect comme solution d’intégration principale. Elle inclut les configurations prises en charge et celles qui ne le sont pas.

| **Topologie commune** | **Description** |
|---|---|
| Forêt unique, locataire Entra unique | La topologie la plus courante est une forêt locale unique, avec un ou plusieurs domaines, et un locataire Entra unique. Pour l’authentification, la synchronisation de hachage de mot de passe est utilisée. Il s’agit de la seule topologie prise en charge par l’installation rapide d’Entra Connect. |
| Forêts multiples, locataire Entra unique | De nombreuses organisations possèdent des environnements comportant plusieurs forêts Active Directory locales. Il existe plusieurs raisons de déployer plus d’une forêt Active Directory locale. Par exemple : des modèles avec des forêts de ressources de comptes et la conséquence d’une fusion ou d’une acquisition. Lorsque vous avez plusieurs forêts, toutes les forêts doivent être accessibles par un seul serveur de synchronisation Entra Connect. Le serveur doit être joint à un domaine. Si nécessaire pour atteindre toutes les forêts, vous pouvez placer le serveur dans un réseau de périmètre (également appelé DMZ, zone démilitarisée et sous-réseau filtré). |
| Plusieurs forêts, un seul serveur de synchronisation et des utilisateurs sont représentés dans un seul annuaire | Dans cet environnement, toutes les forêts locales sont traitées comme des entités distinctes. Aucun utilisateur n’est présent dans une autre forêt. Chaque forêt a sa propre organisation Exchange et il n’existe pas de GALSync entre les forêts. Cette topologie peut se présenter suite à une fusion/acquisition ou dans une organisation où chaque division fonctionne indépendamment. Dans Entra ID, ces forêts sont dans la même organisation et s’affichent avec une liste d’adresses globale unifiée. Dans l'image précédente, chaque objet de chaque forêt est représenté une fois dans le métavers et agrégé dans le locataire cible. |
| Plusieurs forêts : maillage complet avec GALSync facultative | Une topologie de maillage complet permet aux utilisateurs et aux ressources de se trouver dans n’importe quelle forêt. En général, il existe des approbations bidirectionnelles entre les forêts. Si Exchange est présent dans plusieurs forêts, il peut (éventuellement) y avoir une solution GALSync locale. Chaque utilisateur est ensuite représenté en tant que contact dans toutes les autres forêts. GALSync est fréquemment implémentée via FIM 2010 ou MIM 2016. Entra Connect ne peut pas être utilisé pour galSync local. |
| Plusieurs forêts : forêt de ressources de comptes | Dans ce scénario, une (ou plusieurs) forêt de ressources approuve toutes les forêts de comptes. La forêt de ressources a généralement un schéma Active Directory étendu avec Exchange et Teams. Tous les services Exchange et Teams, ainsi que d’autres services partagés, se trouvent dans cette forêt. Les utilisateurs ont un compte d’utilisateur désactivé dans cette forêt et la boîte aux lettres est liée à la forêt de comptes. |
| Serveur de test | Entra Connect prend en charge l’installation d’un deuxième serveur en *mode intermédiaire*. Un serveur dans ce mode lit les données de tous les répertoires connectés, mais n’écrit rien dans les répertoires connectés. Il utilise le cycle de synchronisation normale et possède donc une copie des données d’identité à jour. |
| Plusieurs locataires Entra | Il existe une relation 1:1 entre un serveur de synchronisation Entra Connect et un locataire. Pour chaque locataire Entra, vous avez besoin d’une installation de serveur de synchronisation Entra Connect. Les instances de locataires AD sont isolées par conception. En d'autres termes, les utilisateurs d’une instance ne peuvent pas voir les utilisateurs dans l’autre instance. La séparation des utilisateurs est une configuration prise en charge. Sinon, vous devez utiliser le modèle de client unique Entra. |
| Chaque objet n'est utilisé qu'une seule fois dans un locataire Entra | Dans cette topologie, un serveur de synchronisation Entra Connect est connecté à chaque locataire. Les serveurs de synchronisation Entra Connect doivent être configurés pour le filtrage afin que chacun dispose d’un ensemble mutuellement exclusif d’objets sur lequel fonctionner. Vous pouvez, par exemple, étendre chaque serveur à un domaine ou une unité organisationnelle spécifique. |

### Facteurs impactant les composants Entra Connect

Le diagramme ci-dessous illustre l’architecture générale d’un moteur de provisionnement connecté à une seule forêt, mais la connexion à plusieurs forêts est également prise en charge. Cette architecture montre les interactions entre les divers composants.

![Diagramme de la façon dont les répertoires connectés et le moteur de provisionnement Entra Connect interagissent. Inclut des composants d’espace connecteur et de métaverse dans une base de données SQL.](https://learn.microsoft.com../../wwl-sci/implement-manage-hybrid-identity/media/azure-active-directory-connect-internal.png)

Le moteur de provisionnement se connecte à chaque forêt Active Directory et à Entra ID. Importer est le processus consistant à obtenir des informations de chaque annuaire. Exporter fait référence à la mise à jour des annuaires à partir du moteur de provisionnement. Synchroniser est l’opération qui évalue les règles de transfert des objets au sein du moteur d’approvisionnement.

Entra Connect utilise les zones de transit, les règles et les processus suivants pour effectuer la synchronisation entre Active Directory et Entra ID :

- **Espace connecteur (CS)** : les objets de chaque annuaire connecté (CD), les annuaires réels, sont d’abord mis en transit dans cet espace en attendant d’être traités par le moteur de provisionnement. Entra ID a son propre CS et chaque forêt à laquelle vous vous connectez aura son propre CS.
- **Métaverse (MV)** : les objets qui doivent être synchronisés sont créés ici en fonction des règles de synchronisation. Les objets doivent avoir été créés dans le métaverse afin de pouvoir ensuite remplir des objets et des attributs dans les autres annuaires connectés. Il y a un seul métaverse.
- **Règles de synchronisation** : elles déterminent quels objets seront créés (projetés) ou connectés (joints) à des objets dans la MV. Les règles de synchronisation déterminent également quelles valeurs d’attribut seront copiées ou transformées vers et à partir des annuaires.
- **Profils d’exécution** : ils regroupent les étapes de copie des objets et de leurs valeurs d’attribut entre les zones de transit et les annuaires connectés, selon les règles de synchronisation définies.

### Synchronisation Entra cloud

La synchronisation cloud Entra Connect est conçue pour atteindre des objectifs d’identité hybride pour la synchronisation des utilisateurs, des groupes et des contacts avec l’ID Entra. La synchronisation est effectuée à l’aide de **l’agent de provisionnement cloud** au lieu de l’application Entra Connect. Il peut être utilisé en même temps que la synchronisation Entra Connect et offre les avantages suivants :

- Prise en charge de la synchronisation avec un client Entra à partir d'un environnement de forêts Active Directory multiples et déconnectées : les scénarios courants incluent les fusions et les acquisitions. Les forêts AD de l’entreprise acquise sont isolées des forêts AD de la société mère. Les entreprises qui ont historiquement eu plusieurs forêts AD.
- Installation simplifiée avec des agents de provisionnement légers : les agents agissent comme un pont entre AD et Entra ID, avec toute la configuration de synchronisation gérée dans le cloud.
- Plusieurs agents d’approvisionnement peuvent être utilisés pour simplifier les déploiements à haute disponibilité, critiques pour les organisations qui s’appuient sur la synchronisation de hachage de mot de passe d’AD vers l’ID Entra.
- Prise en charge de grands groupes avec jusqu’à 500 membres. Nous vous recommandons d’utiliser uniquement le filtre d’étendue d’unités d’organisation pour synchroniser les grands groupes.

![Diagramme du flux de processus montrant les éléments Active Directory locaux tels que les utilisateurs et les groupes synchronisés dans le cloud par Cloud Sync.](https://learn.microsoft.com../../wwl-sci/implement-manage-hybrid-identity/media/azure-active-directory-cloud-sync.png)

Avec la synchronisation cloud Entra Connect, l’approvisionnement d’AD vers Entra ID est orchestré dans Microsoft Online Services. Il suffit à une organisation de déployer, dans son environnement sur site ou hébergé par IaaS, un agent léger qui agit comme un pont entre Entra ID et AD. La configuration d’approvisionnement est stockée et gérée dans le cadre du service. Rappelez-vous que la synchronisation s’exécute toutes les 2 minutes.


## Implémenter et gérer la synchronisation de hachage de mot de passe (PHS)

### Fonctionnement de la synchronisation de hachage de mot de passe

La synchronisation de hachage de mot de passe est l’une des méthodes de connexion utilisées pour accomplir l’identité hybride. Entra Connect synchronise un hachage d’un hachage du mot de passe d’un utilisateur entre une instance Active Directory locale et une instance Entra basée sur le cloud.

![Diagramme montrant la façon dont Entra Connect passe un code de hachage de mot de passe pour un utilisateur entre un environnement local et le cloud.](https://learn.microsoft.com../../wwl-sci/implement-manage-hybrid-identity/media/password-hash-sync-architecture.png)

Active Directory Domain Services stocke les mots de passe sous la forme d’une représentation de valeur de hachage du mot de passe utilisateur réel. Une valeur de hachage est un résultat d’une fonction mathématique unidirectionnel (algorithme de hachage). Il n’existe aucune méthode pour retrouver la version en texte brut du mot de passe à partir du résultat d’une fonction unidirectionnelle. Pour synchroniser votre mot de passe, Entra Connect extrait le hachage de votre mot de passe à partir de l'instance locale d'Active Directory. Un traitement de sécurité supplémentaire est appliqué au hachage du mot de passe avant sa synchronisation avec le service d’authentification Entra. Les mots de passe sont synchronisés pour chaque utilisateur et par ordre chronologique.

Le flux de données réel du processus de synchronisation du hachage de mot de passe est similaire à celui de la synchronisation des données de l’utilisateur. Cependant, les mots de passe sont synchronisés plus fréquemment que la fenêtre de synchronisation d’annuaire standard pour d’autres attributs. Le processus de hachage de synchronisation de mot de passe s’exécute toutes les deux minutes. Vous ne pouvez pas modifier la fréquence de ce processus. Quand vous synchronisez un mot de passe, il remplace le mot de passe cloud existant.

La première fois que vous activez la fonctionnalité de synchronisation de hachage de mot de passe, elle effectue une synchronisation initiale des mots de passe de tous les utilisateurs concernés. Vous ne pouvez pas définir explicitement un sous-ensemble de mots de passe utilisateur que vous souhaitez synchroniser pendant la première synchronisation. Une fois la synchronisation initiale terminée, vous pouvez configurer une **synchronisation de hachage de mot de passe sélective** pour les prochaines synchronisations.

S’il existe plusieurs connecteurs, il est possible de désactiver la synchronisation de hachage de mot de passe pour certains connecteurs, mais pas d’autres. Lorsque vous modifiez un mot de passe local, le mot de passe mis à jour est synchronisé, plus souvent en quelques minutes. La fonctionnalité de synchronisation de hachage de mot de passe tente automatiquement d’effectuer à nouveau les tentatives de synchronisation ayant échoué. Si une erreur se produit lors d’une tentative de synchronisation de mot de passe, une erreur est enregistrée dans l’Observateur d’événements.

### Activer la synchronisation de hachage de mot de passe

La synchronisation de hachage de mot de passe est activée automatiquement si vous installez Entra Connect avec la **configuration rapide**. Si vous utilisez des paramètres personnalisés lors de l’installation d’Entra Connect, la synchronisation de hachage de mot de passe est disponible dans la page de connexion utilisateur.

### Synchronisation de hachage de mot de passe et standard de traitement des informations fédérales

Si votre serveur est verrouillé selon la norme Federal Information Processing Standard (FIPS), MD5 est désactivé.

**Pour activer MD5 pour la synchronisation de hachage de mot de passe, procédez comme suit :**

1. Accédez à `%programfiles%\Azure A D Sync\Bin`.
2. Ouvrez miiserver.exe.config.
3. Accédez au nœud configuration/runtime (à la fin du fichier).
4. Ajoutez le nœud suivant : `<enforceFIPSPolicy enabled="false"/>`
5. Enregistrez vos modifications.

Pour référence, cet extrait de code indique ce que vous devez obtenir :

```
   <configuration>
      <runtime>
        <enforceFIPSPolicy enabled="false"/>
      </runtime>
   </configuration>
```

### Utilisation de PingFederate

Configurez PingFederate avec Entra Connect pour configurer la fédération avec le domaine que vous souhaitez connecter. Les prérequis suivants sont obligatoires :

- PingFederate 8.4 ou version ultérieure.
- Certificat TLS/SSL pour le nom du service de fédération que vous envisagez d’utiliser (par exemple, sts.contoso.com).

Après avoir choisi de configurer la fédération à l’aide de PingFederate dans AD Connect, vous êtes invité à vérifier le domaine que vous souhaitez fédérer. Sélectionnez le domaine dans le menu déroulant.

Configurez PingFederate en tant que serveur de fédération pour chaque domaine Azure fédéré. Sélectionnez Ensuite Exporter les paramètres pour partager ces informations avec votre administrateur PingFederate. L’administrateur du serveur de fédération met à jour la configuration et fournit l’URL du serveur PingFederate et le numéro de port afin qu’Entra Connect puisse vérifier les paramètres de métadonnées.


## Implémenter et gérer l’authentification directe (PTA)

L’authentification directe Entra permet à vos utilisateurs de se connecter aux applications sur site et aux applications cloud à l’aide des mêmes mots de passe. L’authentification directe connecte les utilisateurs en validant leurs mots de passe directement sur Active Directory local.

### Activer la fonctionnalité

Activez l’authentification directe via [Entra Connect](https://learn.microsoft.com/fr-fr/azure/active-directory/hybrid/whatis-hybrid-identity).

Si vous installez Entra Connect pour la première fois, choisissez le [chemin d’installation personnalisé](https://learn.microsoft.com/fr-fr/azure/active-directory/hybrid/how-to-connect-install-custom). Dans la page de **connexion de l’utilisateur** , choisissez **l’authentification directe** comme **méthode** d’authentification. Une fois l’opération terminée, un agent d’authentification directe est installé sur le même serveur qu’Entra Connect. La fonctionnalité d’authentification directe est également activée sur votre locataire.

Si vous avez déjà installé Entra Connect à l’aide de l’installation rapide ou du chemin d’installation personnalisé, sélectionnez la tâche **Modifier la connexion de l'utilisateur** sur Entra Connect, puis sélectionnez **Suivant**. Sélectionnez ensuite **l’authentification directe** comme méthode de connexion. Une fois l’opération terminée, un agent d’authentification directe est installé sur le même serveur qu’Entra Connect et la fonctionnalité est activée sur votre locataire.

Important

L’authentification directe est une fonctionnalité au niveau du locataire. L'activation affecte l'authentification des utilisateurs sur tous les domaines managés de votre tenant. Si vous passez des services de fédération Active Directory (AD FS) à l’authentification directe, vous devez attendre au moins 12 heures avant d’arrêter votre infrastructure AD FS. Ce délai d'attente permet aux utilisateurs de continuer à se connecter à Exchange ActiveSync pendant la transition.


## Explorer l’authentification directe et l’authentification unique transparente

L’authentification unique transparente Entra (SSO transparente) connecte automatiquement les utilisateurs à partir de leurs bureaux d’entreprise connectés au réseau. L’authentification unique transparente offre à vos utilisateurs un accès facile aux applications cloud sans avoir besoin d’autres composants locaux.

L’authentification unique transparente peut être combinée avec la synchronisation de hachage de mot de passe et l’authentification directe. L’authentification unique transparente n’est pas applicable aux services de fédération Active Directory (AD FS).

### Principaux avantages

- Expérience utilisateur exceptionnelle
  - Les utilisateurs sont automatiquement connectés aux applications locales et basées sur le cloud.
  - Les utilisateurs n’ont pas à saisir leur mot de passe à plusieurs reprises.

- Facile à déployer & administrer
  - Aucun composant local supplémentaire n’est nécessaire pour que cela fonctionne.
  - Fonctionne avec n’importe quelle méthode d’authentification cloud : synchronisation de hachage de mot de passe ou authentification directe.
  - Peut être déployé pour tout ou partie de vos utilisateurs à l’aide d’une stratégie de groupe.

### Fonctionnement des connexions dans un navigateur web avec l’authentification unique transparente

Le flux de connexion dans un navigateur web est le suivant :

1. Un utilisateur tente d’accéder à une application web (par exemple, Outlook Web App - `https://outlook.office365.com/owa/`) à partir d’un appareil d’entreprise joint à un domaine du réseau de l’entreprise.
2. Si l’utilisateur n’est pas encore connecté, l’utilisateur est redirigé vers la page de connexion Entra.
3. L'utilisateur saisit son nom d'utilisateur sur la page de connexion Entra.
4. En utilisant JavaScript en arrière-plan, Entra ID défie le navigateur, via une réponse 401 non autorisée, de fournir un ticket Kerberos.
5. Le navigateur demande à son tour un ticket d’Active Directory pour le compte d’ordinateur AZUREADSSOACC (qui représente l’ID Entra).
6. Active Directory localise le compte d’ordinateur et retourne un ticket Kerberos au navigateur chiffré avec le secret du compte d’ordinateur.
7. Le navigateur transmet le ticket Kerberos qu'il a acquis depuis Active Directory vers Entra ID.
8. Entra ID déchiffre le ticket Kerberos, qui inclut l'identité de l'utilisateur connecté à l'appareil d'entreprise, à l'aide de la clé précédemment partagée.
9. Après l’évaluation, l’ID Entra retourne un jeton à l’application ou demande à l’utilisateur d’effectuer des preuves supplémentaires, telles que l’authentification multifacteur.
10. Si l’utilisateur parvient à se connecter, il peut accéder à l’application.

### Comment fonctionne la connexion sur un client natif avec l’authentification unique transparente ?

Le flux de connexion sur un client natif est le suivant :

1. Un utilisateur tente d’accéder à une application native (par exemple, le client Outlook) à partir d’un appareil d’entreprise joint à un domaine du réseau de l’entreprise.
2. Si l’utilisateur n’est pas déjà connecté, l’application native récupère le nom d’utilisateur de l’utilisateur à partir de la session Windows de l’appareil.
3. L'application envoie le nom d'utilisateur à Entra ID et récupère le point de terminaison WS-Trust MEX de votre locataire. Ce point de terminaison WS-Trust est utilisé exclusivement par la fonctionnalité d’authentification unique transparente et n’est pas une implémentation générale du protocole WS-Trust sur l’ID Entra.
4. L’application interroge ensuite le point de terminaison WS-Trust MEX pour savoir si le point de terminaison d’authentification intégrée est disponible. Le point de terminaison d'authentification intégré est exclusivement utilisé par la fonctionnalité SSO transparente.
5. Si l’étape 4 réussit, un challenge Kerberos est émis.
6. Si l'application parvient à récupérer le ticket Kerberos, elle le transmet au point de terminaison d'authentification intégré Entra.
7. Entra ID déchiffre le ticket Kerberos et le valide.
8. Entra ID connecte l'utilisateur et émet un jeton SAML à l'application.
9. L’application soumet ensuite le jeton SAML au point de terminaison du jeton Entra ID OAuth2.
10. Entra ID valide le jeton SAML et émet un jeton d’accès, un jeton d’actualisation pour la ressource spécifiée et un jeton d’ID à l’application.
11. L’utilisateur peut alors accéder aux ressources de l’application.


## Implémenter et gérer la fédération

La fédération peut utiliser une ferme Active Directory sur site, nouvelle ou existante, dans Windows Server 2012 R2 (ou version ultérieure). Entra Connect permet alors aux utilisateurs de se connecter aux ressources Entra à l'aide de leur mot de passe sur site.

![Diagramme de fédération entre l’ID Local et Entra. Affiche les utilisateurs en mesure de se connecter aux ressources locales et cloud avec une connexion partagée unique.](https://learn.microsoft.com../../wwl-sci/implement-manage-hybrid-identity/media/sc300-federation-flow-diagram.png)

La fédération est un ensemble de domaines qui ont établi une confiance. Le niveau de confiance varie, mais il inclut généralement l’authentification et presque toujours l’autorisation. Une fédération classique peut inclure plusieurs organisations qui ont établi une confiance pour un accès partagé à un ensemble de ressources.

Vous pouvez fédérer votre environnement local avec l’ID Entra et utiliser cette fédération pour l’authentification et l’autorisation. Cette méthode de connexion garantit que toutes les authentifications utilisateur se produisent localement. Cette méthode permet aux administrateurs d’implémenter des niveaux plus rigoureux de contrôle d’accès. La fédération avec AD FS et PingFederate est disponible.

Avec la connexion fédérée, vos utilisateurs peuvent se connecter aux services Entra avec leurs mots de passe locaux. Bien qu’ils soient sur le réseau d’entreprise, ils n’ont même pas besoin d’entrer leurs mots de passe. En utilisant l’option de fédération avec AD FS, vous pouvez déployer une batterie de serveurs nouvelle ou existante avec AD FS dans Windows Server 2012 R2 ou version ultérieure. Si vous choisissez de spécifier une batterie de serveurs existante, Entra Connect configure l’approbation entre votre batterie de serveurs et l’ID Entra afin que vos utilisateurs puissent se connecter.

### Condition requise pour déployer la fédération avec AD FS et Entra Connect

Pour le déploiement sur une batterie de serveurs AD FS, vous avez besoin des éléments suivants :

- Informations d’identification de l’administrateur local sur vos serveurs de fédération.
- Informations d’identification de l’administrateur local sur tous les serveurs de groupe de travail (et non joints à un domaine) sur lesquels vous envisagez de déployer le rôle proxy d’application web.
- Ordinateur sur lequel vous exécutez l’Assistant : il doit pouvoir se connecter, à l’aide de la gestion à distance de Windows, aux autres machines sur lesquelles vous souhaitez installer AD FS ou le proxy d’application web.

### Configurer votre fédération à l’aide d’Entra Connect pour se connecter à une batterie de serveurs AD FS

**Spécifiez les serveurs AD FS** : spécifiez les serveurs où vous souhaitez installer AD FS. Vous pouvez ajouter un ou plusieurs serveurs selon vos besoins de capacité. Avant la configuration, joignez tous les serveurs AD FS à Active Directory. Cette étape n’est pas requise pour les serveurs Proxy d’application Web. Microsoft recommande d’installer un seul serveur AD FS pour les déploiements de test et pilote. Ensuite, ajoutez et déployez d’autres serveurs pour répondre à vos besoins de mise à l’échelle en réexécutant Entra Connect après la configuration initiale.

**Spécifiez les serveurs proxy d’application web** : spécifiez vos serveurs proxy d’application web. Le serveur Proxy d’application Web est déployé dans votre réseau de périmètre, face à l’extranet. Il prend en charge les demandes d’authentification provenant de l’extranet. Vous pouvez ajouter un ou plusieurs serveurs selon vos besoins de capacité. Ensuite, ajoutez et déployez d’autres serveurs pour répondre à vos besoins de mise à l’échelle en réexécutant Entra Connect après la configuration initiale.

**Spécifiez le compte de service pour le service AD FS** : le service AD FS a besoin d’un compte de service de domaine pour authentifier les utilisateurs et rechercher des informations utilisateur dans Active Directory. Il prend en charge deux types de compte de service :

- Compte de service administré du groupe
- Compte d’utilisateur de domaine

**Sélectionnez le domaine Entra que vous souhaitez fédérer** : utilisez la page du domaine Entra pour configurer la relation de fédération entre AD FS et Entra ID. Ici, vous configurez AD FS pour fournir des jetons de sécurité à Entra ID. Vous configurez également Entra ID pour approuver les jetons de cette instance d’AD FS. Cette page vous permet de configurer un seul domaine durant l’installation initiale. Vous pouvez configurer ultérieurement des domaines supplémentaires en réexécutant Entra Connect.

### Outils Entra Connect pour gérer votre fédération

Vous pouvez effectuer différentes tâches liées à AD FS dans Entra Connect avec une intervention utilisateur minimale à l’aide de l’Assistant Entra Connect. Même une fois que vous avez terminé d’installer Entra Connect en exécutant l’Assistant, vous pouvez réexécuter l’Assistant pour effectuer d’autres tâches. Par exemple, l’Assistant permet de réparer la relation de confiance avec Microsoft 365, de fédérer avec Entra ID en utilisant un ID de connexion alternatif et d’ajouter un serveur AD FS Web Application Proxy (WAP).

**Réparer l’approbation** - Vous pouvez utiliser Entra Connect pour vérifier l’intégrité actuelle de l’approbation AD FS et Entra ID et prendre les mesures appropriées pour réparer l’approbation.

**Fédérer avec Entra ID à l’aide d’AlternateID** : il est recommandé de conserver le nom d’utilisateur principal local (UPN) et le nom principal d’utilisateur cloud. Nous vous recommandons de configurer un AUTRE ID de connexion si l’UPN local utilise un domaine non routable (par exemple Contoso.local), ou s’il ne peut pas être modifié en raison des dépendances d’application locales. Un AUTRE ID de connexion vous permet de configurer une expérience de connexion où les utilisateurs peuvent se connecter avec un attribut autre que leur UPN, tel que le courrier électronique. Le choix du nom d’utilisateur principal dans Entra ID Connect est défini par défaut sur l’attribut userPrincipalName dans Active Directory. Si vous choisissez un autre attribut pour le nom d’utilisateur principal et que vous fédérerez à l’aide d’AD FS, Entra Connect configure AD FS pour un AUTRE ID de connexion.

**Ajouter un domaine fédéré** : il est facile d’ajouter un domaine à fédérer avec l’ID Entra à l’aide d’Entra Connect. Entra Connect ajoute le domaine de la fédération et modifie les règles de revendication pour identifier correctement l’émetteur lorsque plusieurs domaines sont fédérés avec Entra ID.

En plus d'« Ajouter un serveur AD FS » et d'« Ajouter un serveur proxy d'application Web AD FS ».

### Écriture différée de l’appareil

La réécriture d’appareil est utilisée pour activer l’accès conditionnel basé sur l’appareil pour les appareils protégés par AD FS. Cet accès conditionnel offre une sécurité et une assurance supplémentaires que l’accès aux applications n’est accordé qu’aux appareils approuvés. L’écriture différée des appareils active cette sécurité en synchronisant tous les appareils inscrits dans Azure sur le Active Directory local. Lors de la configuration, les opérations suivantes sont effectuées pour préparer la forêt AD :

- S’ils n’existent pas déjà, créez et configurez de nouveaux conteneurs et objets sous : **CN=Device Registration Configuration,CN=Services,CN=Configuration,[forest dn]**.
- S’ils n’existent pas déjà, créez et configurez de nouveaux conteneurs et objets sous **: CN=RegisteredDevices,[domain-dn]**. Les objets d’appareil seront créés dans ce conteneur.
- Définissez les autorisations nécessaires sur le compte Entra Connector pour gérer les appareils sur votre Active Directory.


## Résoudre les erreurs de synchronisation

Des erreurs peuvent survenir lors de la synchronisation des données d'identité entre Windows Server Active Directory (AD DS) et Entra ID. Cet article présente une vue d’ensemble des différents types d’erreur de synchronisation, certains des scénarios à l’origine de ces erreurs ainsi que les solutions possibles. Cette section inclut les types d’erreurs courants, mais ne couvre pas toutes les erreurs possibles.

Avec la dernière version d’Entra Connect, un rapport sur les erreurs de synchronisation est disponible dans le [Portail Azure](https://aka.ms/aadconnecthealth), comme élément d’Entra Connect Health pour synchronisation.

Entra Connect effectue 3 types d’opérations à partir des répertoires dont il assure la synchronisation : importation, exportation et synchronisation. Les erreurs peuvent se produire dans toutes les opérations. Cette section se concentre principalement sur les erreurs survenues lors de l'exportation vers Entra ID.

### Erreurs lors de l’exportation vers Entra ID

La section suivante décrit les différents types d'erreurs de synchronisation qui peuvent survenir lors de l'exportation vers Entra ID à l'aide du connecteur Entra. Ce connecteur peut être identifié par le format de nom `contoso.onmicrosoft.com`. Les erreurs lors de l’exportation vers Entra ID indiquent que l’opération (ajouter, mettre à jour, supprimer, etc.) tentée par Entra Connect (moteur de synchronisation) sur le répertoire Entra a échoué.

### Erreurs d’incohérence de données

#### InvalidSoftMatch

**Description**

- Lorsque Entra Connect (moteur de synchronisation) demande au répertoire d'ajouter ou de mettre à jour des objets, Entra ID fait correspondre l'attribut **sourceAnchor** de l'objet entrant à l'attribut **immutableId** des objets dans Entra ID. Cette correspondance est appelée **Correspondance dure**.
- Lorsque Entra ID **ne trouve aucun** objet dont l’attribut **immutableId** correspond à l’attribut **sourceAnchor** de l’objet entrant, il n’approvisionne pas immédiatement un nouvel objet. Il utilise d’abord les attributs ProxyAddresses et UserPrincipalName pour trouver une correspondance. Cette correspondance est appelée **Correspondance réversible**. Le Soft Match fait correspondre les objets déjà présents dans Entra ID aux nouveaux objets ajoutés/mis à jour pendant la synchronisation, qui représentent la même entité (utilisateurs, groupes) dans les locaux de l'entreprise.
- **L’erreur InvalidSoftMatch** se produit lorsque la correspondance dure ne trouve aucun objet correspondant **ET** qu’une correspondance réversible en trouve un, mais dont l’*immutableId* diffère du *SourceAnchor* de l’objet entrant. Cela suggère que l’objet correspondant a été synchronisé avec un autre objet à partir d’Active Directory local.

En d’autres termes, pour que la correspondance réversible fonctionne, l’objet à mettre en correspondance réversible ne doit avoir aucune valeur pour *immutableId*. Si un objet dont l’ensemble *immutableId* a une valeur échoue en dur, mais répond aux critères de correspondance réversible, l’opération entraîne une erreur de synchronisation InvalidSoftMatch.

Le schéma de répertoire Entra n’autorise pas deux objets ou plus à avoir la même valeur que les attributs suivants. (Il ne s’agit pas d’une liste exhaustive.)

- ProxyAddresses
- Nom Principal de l'Utilisateur
- onPremisesSecurityIdentifier
- Identifiant d'objet (ObjectId)

La fonctionnalité [Duplicate Attribute Resiliency d’Entra Attribute](https://learn.microsoft.com/fr-fr/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency) est également en cours de déploiement comme comportement par défaut d’Entra ID. Elle permettra de réduire le nombre d'erreurs de synchronisation observées par Entra Connect (ainsi que par d'autres clients de synchronisation). En effet, elle rendra Entra ID plus résilient dans sa façon de traiter les attributs ProxyAddresses et UserPrincipalName dupliqués et présents dans les environnements AD locaux. Cette fonctionnalité ne corrige pas les erreurs de duplication. Par conséquent, les données doivent toujours être corrigées. Elle permet par ailleurs d'approvisionner de nouveaux objets dont l'approvisionnement est autrement bloqué en raison de valeurs dupliquées dans Entra ID. Cela réduit également le nombre d’erreurs de synchronisation retournées au client de synchronisation. Si cette fonctionnalité est activée pour votre locataire, vous ne verrez pas les erreurs de synchronisation InvalidSoftMatch observées lors de l’approvisionnement de nouveaux objets.

**Exemples de scénarios pour InvalidSoftMatch**

- Deux objets ou plus avec la même valeur pour l’attribut ProxyAddresses existent dans Active Directory local. Un seul est provisionné dans Entra ID.
- Deux objets ou plus ayant la même valeur pour l’attribut userPrincipalName existent dans Active Directory local. Un seul est provisionné dans Entra ID.
- Un objet a été ajouté dans Active Directory local avec la même valeur de l'attribut ProxyAddresses que celle d'un objet existant dans le répertoire Entra. L’objet ajouté localement n’est pas configuré dans le répertoire Entra.
- Un objet a été ajouté dans Active Directory local avec la même valeur de l'attribut userPrincipalName que celle d'un compte d’Entra ID. L’objet n’est pas provisionné dans Entra ID.
- Un compte synchronisé a été déplacé de la forêt A vers la forêt B. Entra Connect (moteur de synchronisation) utilisait l'attribut ObjectGUID pour calculer le SourceAnchor. Une fois la forêt déplacée, la valeur de SourceAnchor est différente. Synchronisation impossible du nouvel objet (à partir de la forêt B) et de l'objet existant dans Entra ID.
- Un objet synchronisé a été accidentellement supprimé d'Active Directory local, puis un nouvel objet a été créé dans Active Directory pour la même entité (par exemple un utilisateur), sans suppression du compte dans Entra ID. Le nouveau compte ne parvient pas à se synchroniser avec l’objet Entra existant.
- Entra Connect a été désinstallé et réinstallé. Pendant la réinstallation, un autre attribut a été choisi comme SourceAnchor. Tous les objets précédemment synchronisés ont arrêté la synchronisation avec l’erreur InvalidSoftMatch.

**Exemple de cas :**

1. **Bob Smith** est un utilisateur synchronisé dans Entra ID à partir d'Active Directory local de *contoso.com*
2. **UserPrincipalName** de Bob Smith est défini sur **bobs@contoso.com**.
3. **"abcdefghijklmnopqrstuv=="** est le **SourceAnchor** calculé par Entra Connect à l'aide de l'**objectGUID** de Bob Smith provenant d'Active Directory, qui est l'**immutableId** de Bob Smith dans Entra ID.
4. Bob a également les valeurs suivantes pour l’attribut **proxyAddresses** :

- smtp : bobs@contoso.com
- smtp : bob.smith@contoso.com
- **Smtp: bob@contoso.com**

1. Un nouvel utilisateur, **Bob Taylor**, est ajouté à Active Directory local.
2. **UserPrincipalName** de Bob Taylor est défini sur **bobt@contoso.com**.
3. **"abcdefghijkl0123456789==""** est le **sourceAnchor** calculé par Entra Connect à l'aide de l'**objectGUID** de Bob Taylor provenant d'Active Directory local. L'objet de Bob Taylor n'a PAS encore été synchronisé avec Entra ID.
4. Bob Taylor a les valeurs suivantes pour l’attribut proxyAddresses

- smtp : bobt@contoso.com
- smtp : bob.taylor@contoso.com
- **Smtp: bob@contoso.com**

1. Lors de la synchronisation, Entra Connect reconnaîtra l'ajout de Bob Taylor dans Active Directory local et demandera à Entra ID d'effectuer la même modification.
2. Entra ID effectuera au préalable une correspondance matérielle (hard match). Autrement dit, il cherche s’il existe un objet dont immutableId est égal à « abcdefghijkl0123456789== ». La correspondance matérielle échouera, car aucun autre objet d’Entra ID n'aura cet immutableId.
3. Entra ID tentera alors d'effectuer une correspondance logicielle avec Bob Taylor. Autrement dit, il cherche s’il existe un objet dont proxyAddresses est égal aux trois valeurs, y compris smtp : bob@contoso.com
4. Entra ID trouvera l'objet de Bob Smith conforme aux critères de correspondance logicielle. Mais cet objet a la valeur immutableId = « abcdefghijklmnopqrstuv== ». qui indique que cet objet a été synchronisé à partir d’un autre objet depuis Active Directory local. Par conséquent, Entra ID ne peut pas correspondre de manière réversible à ces objets et génère une erreur de synchronisation **InvalidSoftMatch**.

**Comment corriger l’erreur InvalidSoftMatch**

La raison la plus fréquente de l'erreur InvalidSoftMatch : deux objets avec un SourceAnchor différent (immutableId) présentent la même valeur pour les attributs ProxyAddresses et/ou UserPrincipalName, utilisés pendant le processus de correspondance logicielle sur Entra ID. Correction de la correspondance souple invalide

1. Identifiez les proxyAddresses dupliqués, userPrincipalName ou une autre valeur d’attribut qui provoque l’erreur. Identifiez également les deux objets ou plus impliqués dans le conflit. Le rapport généré par [Entra Connect Health pour synchronisation](https://learn.microsoft.com/fr-fr/azure/active-directory/hybrid/how-to-connect-health-sync) peut vous aider à identifier les deux objets.
2. Identifiez l’objet qui doit conserver la valeur dupliquée, et celui qui ne doit pas la conserver.
3. Supprimez la valeur dupliquée de l’objet qui ne doit pas avoir cette valeur. Vous devez apporter la modification dans le répertoire de provenance de l’objet. Dans certains cas, vous devez supprimer l’un des objets en conflit.
4. Si vous avez effectué la modification dans l'AD local, laissez Entra Connect synchroniser la modification.

Les rapports d’erreurs de synchronisation dans Entra Connect Health pour la synchronisation sont mis à jour toutes les 30 minutes et incluent les erreurs de la dernière tentative de synchronisation.

Remarque

ImmutableId, par définition, ne doit pas changer dans la durée de vie de l’objet. Entra Connect n’a peut-être pas été configuré en tenant compte de certains scénarios de la liste ci-dessus. Il peut alors calculer, pour l’objet AD, une valeur de SourceAnchor différente de celle de l’objet Entra existant que vous souhaitez continuer à utiliser, alors que les deux représentent la même entité (même utilisateur/groupe/contact, etc.).

#### ObjectTypeMismatch

**Description**

Lorsque Entra ID tente de mettre en correspondance réversible deux objets, ces objets peuvent être de « type d’objet » différent (l’utilisateur, le groupe, le contact, etc.) tout en ayant les mêmes valeurs pour les attributs utilisés pour effectuer la correspondance réversible. Comme la duplication de ces attributs n’est pas autorisée dans Entra, l’opération peut entraîner une erreur de synchronisation « ObjectTypeMismatch ».

**Exemples de scénarios d’erreur ObjectTypeMismatch**

- Un groupe de sécurité avec messagerie activée est créé dans Microsoft 365. L'administrateur ajoute un nouvel utilisateur ou contact dans l'AD local (qui n'est pas encore synchronisé avec Entra ID) avec la même valeur pour l'attribut ProxyAddresses que celle du groupe Microsoft 365.

**Exemple de scénario**

1. L’administrateur crée un groupe de sécurité avec messagerie activée dans Microsoft 365 pour le service fiscal et fournit une adresse e-mail en tant que tax@contoso.com. Ce groupe est assigné à la valeur d’attribut ProxyAddresses de **smtp : tax@contoso.com**
2. Un nouvel utilisateur rejoint Contoso.com et un compte est créé pour l’utilisateur local avec proxyAddress en tant que **smtp : tax@contoso.com**
3. Lorsque Entra Connect synchronisera le nouveau compte d'utilisateur, il recevra l'erreur « ObjectTypeMismatch. »

**Comment corriger l’erreur ObjectTypeMismatch**

La raison la plus courante de l’erreur ObjectTypeMismatch est que deux objets de type différent (Utilisateur, Groupe, Contact, etc.) ont un attribut ProxyAddresses de la même valeur. Pour corriger ObjectTypeMismatch :

1. Identifiez la valeur proxyAddresses (ou autre attribut) dupliquée qui provoque l’erreur. Identifiez également les deux objets ou plus impliqués dans le conflit. Le rapport généré par [Entra Connect Health pour synchronisation](https://learn.microsoft.com/fr-fr/azure/active-directory/hybrid/how-to-connect-health-sync) peut vous aider à identifier les deux objets.
2. Identifiez l’objet qui doit conserver la valeur dupliquée, et celui qui ne doit pas la conserver.
3. Supprimez la valeur dupliquée de l’objet qui ne doit pas avoir cette valeur. Vous devez apporter la modification dans le répertoire de provenance de l’objet. Dans certains cas, vous devez supprimer l’un des objets en conflit.
4. Si vous avez effectué la modification dans l'AD local, laissez Entra Connect synchroniser la modification. Le rapport d'erreur de synchronisation dans Entra Connect Health pour synchronisation est mis à jour toutes les 30 minutes et comprend les erreurs reçues lors de la dernière tentative de synchronisation.

### Attributs en double

#### La Valeur de l'Attribut Doit Être Unique

#### Descriptif

Le schéma Entra n’autorise pas à donner à deux objets ou plus la même valeur pour les attributs suivants. En d'autres termes, chaque objet d’Entra ID est contraint de disposer d'une valeur unique de ces attributs à une instance donnée.

- ProxyAddresses
- Nom Principal de l'Utilisateur

Si Entra Connect ajoute un nouvel objet, ou met à jour un objet existant, avec une valeur pour les attributs ci-dessus déjà assignée à un autre objet dans Entra ID, l'opération entraîne l'erreur de synchronisation « AttributeValueMustBeUnique. »

#### Scénarios possibles :

La valeur dupliquée est affectée à un objet déjà synchronisé, qui est en conflit avec un autre objet synchronisé.

#### Exemple de cas :

1. **Bob Smith** est un utilisateur synchronisé dans Entra ID à partir d'Active Directory local de contoso.com
2. **UserPrincipalName** de Bob Smith sur site est défini sur **bobs@contoso.com**.
3. Bob a également les valeurs suivantes pour l’attribut **proxyAddresses** :

- smtp : bobs@contoso.com
- smtp : bob.smith@contoso.com
- **Smtp: bob@contoso.com**

1. Un nouvel utilisateur, **Bob Taylor**, est ajouté à Active Directory local.
2. **UserPrincipalName** de Bob Taylor est défini sur **bobt@contoso.com**.
3. **Bob Taylor** a les valeurs suivantes pour l’attribut **ProxyAddresses** i. smtp : bobt@contoso.com ii. smtp : bob.taylor@contoso.com
4. La synchronisation de l'objet de Bob Taylor avec Entra ID a réussi.
5. L’administrateur a décidé de mettre à jour l’attribut **ProxyAddresses** de Bob Taylor avec la valeur suivante : i. **smtp : bob@contoso.com**
6. Entra ID essaiera de mettre à jour l'objet de Bob Taylor avec la valeur ci-dessus. Cette opération échouera avec l'erreur « AttributeValueMustBeUnique. », car la valeur ProxyAddresses est déjà attribuée à Bob Smith.

#### Comment corriger l’erreur AttributeValueMustBeUnique

La raison la plus courante pour l’erreur AttributeValueMustBeUnique est que deux objets avec des valeurs immutableId SourceAnchor différentes ont la même valeur pour les attributs ProxyAddresses et/ou UserPrincipalName. Pour corriger l’erreur AttributeValueMustBeUnique

1. Identifiez les valeurs proxyAddresses, userPrincipalName ou d’autres valeurs d’attribut dupliquées à l’origine de l’erreur. Identifiez également les deux objets ou plus impliqués dans le conflit. Le rapport généré par [Entra Connect Health pour synchronisation](https://learn.microsoft.com/fr-fr/azure/active-directory/hybrid/how-to-connect-health-sync) peut vous aider à identifier les deux objets.
2. Identifiez l’objet qui doit conserver la valeur dupliquée, et celui qui ne doit pas la conserver.
3. Supprimez la valeur dupliquée de l’objet qui ne doit pas avoir cette valeur. Vous devez apporter la modification dans le répertoire de provenance de l’objet. Dans certains cas, vous devez supprimer l’un des objets en conflit.
4. Si vous avez effectué la modification dans l'AD local, laissez Entra Connect synchroniser cette modification pour que l'erreur soit corrigée.

### Échecs de validation de données

#### ÉchecDeLaValidationDesDonnéesIdentitaires

#### Descriptif

Entra ID applique diverses restrictions sur les données elles-mêmes avant d’autoriser l’écriture des données dans le répertoire. Ces restrictions permettent de garantir que les utilisateurs finaux bénéficient de la meilleure expérience possible lors de l’utilisation des applications qui dépendent de ces données.

#### Scénarios

La valeur d’attribut UserPrincipalName comporte des caractères non valides/non pris en charge. b. L’attribut UserPrincipalName ne suit pas le format requis.

#### Comment corriger l’erreur IdentityDataValidationFailed

Vérifiez que l’attribut userPrincipalName a des caractères pris en charge et un format requis.

#### FederatedDomainChangeError

#### Descriptif

Ce cas génère une erreur de synchronisation **« FederatedDomainChangeError »** lorsque le suffixe de UserPrincipalName d’un utilisateur d’un domaine fédéré est remplacé par un autre domaine fédéré.

#### Scénarios

Pour un utilisateur synchronisé, le suffixe UserPrincipalName a été remplacé d’un domaine fédéré à un autre domaine fédéré en local. Par exemple, *UserPrincipalName = bob@contoso.com* a été remplacé par *UserPrincipalName = bob@fabrikam.com*.

#### Exemple :

1. Bob Smith, un compte pour Contoso.com, est ajouté en tant qu’utilisateur dans Active Directory avec UserPrincipalName bob@contoso.com
2. Bob passe à une autre division de Contoso.com appelée Fabrikam.com et leur UserPrincipalName est remplacé par bob@fabrikam.com
3. Les domaines contoso.com et fabrikam.com sont des domaines fédérés avec Entra ID.
4. Le userPrincipalName de Bob n’est pas mis à jour et génère une erreur de synchronisation « FederatedDomainChangeError ».

### LargeObject

#### Descriptif

Lorsqu'un attribut dépasse la limite de taille, de longueur ou de nombre fixée par le schéma Entra, l'opération de synchronisation génère l'erreur de synchronisation **LargeObject** ou **ExceededAllowedLength**. Cette erreur se produit généralement pour les attributs suivants

- certificat utilisateur
- userSMIMECertificate
- thumbnailPhoto
- proxyAddresses

#### Scénarios possibles

1. L’attribut userCertificate de Bob stocke trop de certificats attribués à Bob. Celles-ci incluent des certificats plus anciens et expirés. La limite matérielle est de 15 certificats.
2. L’attribut userSMIMECertificate de Bob stocke trop de certificats attribués à Bob. Celles-ci incluent des certificats plus anciens et expirés. La limite matérielle est de 15 certificats.
3. thumbnailPhoto de Bob définie dans Active Directory est trop grande pour être synchronisée dans Entra ID.
4. Pendant la population automatique de l’attribut ProxyAddresses dans Active Directory, un objet présente trop d’adresses ProxyAddresses affectées.

#### Guide pratique pour corriger

Vérifiez que l’attribut à l’origine de l’erreur se trouve dans la limitation autorisée.

### Conflit de rôle d’administrateur

#### Descriptif

Un **conflit de rôle d’administrateur existant** se produit sur un objet utilisateur lors de la synchronisation lorsque cet objet utilisateur dispose des éléments suivants :

- autorisations d’administration et
- le même UserPrincipalName qu'un objet Entra existant

Entra Connect n’est pas autorisé à établir une correspondance approximative d’un objet utilisateur d’un répertoire Entra local avec un objet utilisateur dans Azure AD auquel un rôle d’administration est attribué.

#### Guide pratique pour corriger

Pour résoudre ce problème, procédez de la manière suivante :

1. Supprimez le compte Entra (propriétaire) de tous les rôles d’administrateur.
2. **Supprimez en dur** l’objet mis en quarantaine dans le cloud.
3. Le prochain cycle de synchronisation s’occupera de la mise en correspondance réversible de l’utilisateur local avec le compte cloud (étant donné que l’utilisateur cloud n’est plus une disponibilité générale globale).
4. Restaurez les appartenances aux rôles pour le propriétaire.

Remarque

Vous pouvez à nouveau attribuer le rôle administratif à l'objet utilisateur existant une fois que la correspondance logicielle entre l'objet utilisateur local et l'objet utilisateur Entra est terminée.


## Mettre en œuvre Entra Connect Health

Entra Connect Health assure la surveillance de votre infrastructure d’identité locale. Il vous permet de maintenir une connexion fiable à Microsoft 365 et Microsoft Online Services. Cette fiabilité est obtenue en fournissant des fonctionnalités de supervision pour vos composants d’identité clés. En outre, il rend les points de données clés sur ces composants facilement accessibles.

Ces informations sont toutes présentées dans le [portail Entra Connect Health](https://aka.ms/aadconnecthealth). Utilisez le portail Entra Connect Health pour voir les alertes, la supervision des performances, l’analytique des utilisations et d’autres informations. Entra Connect Health prend en compte l’intégrité des composants d’identité clé, le tout à un seul endroit.

![Diagramme d’Entra Connect Health. Montre comment Entra Connect est géré.](https://learn.microsoft.com../../wwl-sci/implement-manage-hybrid-identity/media/azure-active-directory-connect-health-2.png)

L’utilisation de la fonctionnalité Entra Connect Health nécessite une licence Entra ID Premium P1.

### Installation de l’agent Entra Connect Health

Cette section fournit des instructions pour l’installation et la configuration des agents Entra Connect Health.

### Spécifications

- Entra ID Premium est installé.
- Vous êtes administrateur général dans Entra ID.
- L’agent Entra Connect Health est installé sur chaque serveur cible.
- Les points de terminaison de service Azure ont une connectivité sortante.
- La connectivité sortante est basée sur les adresses IP.
- L’inspection TLS pour le trafic sortant est filtrée ou désactivée.
- Les ports de pare-feu sur le serveur exécutent l’agent.
  - L’agent nécessite l’ouverture des ports de pare-feu suivants afin qu’il puisse communiquer avec les points de terminaison du service Entra Connect Health :
    - Port TCP 443
    - Port TCP 5671

  - La version la plus récente de l’agent ne requiert pas le port 5671. Procédez à une mise à niveau vers la dernière version pour que seul le port 443 soit requis.

- PowerShell version 4.0 ou ultérieure est installé.
- FIPS (Federal Information Processing Standard) est désactivé.

### Installer l’agent

Téléchargez et installez l’agent Entra Connect Health à partir du Centre de téléchargement.

### Installer l’agent pour le service de fédération Active Directory

Remarque

Votre serveur de fédération Active Directory (AD FS) doit être différent de votre serveur de synchronisation. N’installez pas l’agent AD FS sur votre serveur de synchronisation.

Avant d’installer l’agent, assurez-vous que le nom d’hôte de votre serveur AD FS est unique et qu’il n’existe pas dans le service AD FS. Pour démarrer l’installation de l’agent, double-cliquez sur le fichier *.exe* que vous avez téléchargé. Dans la première fenêtre, sélectionnez **Installer**.

Une fois l’installation terminée, sélectionnez **Configurer maintenant**.

Une fenêtre PowerShell s’ouvre pour démarrer le processus d’inscription de l’agent. Lorsque vous y êtes invité, connectez-vous à l’aide d’un compte d’ID Entra qui dispose des autorisations nécessaires pour inscrire l’agent. Par défaut, le compte d’administrateur général dispose d’autorisations.

Une fois connecté, PowerShell continue. Une fois l’opération terminée, vous pouvez fermer PowerShell. La configuration est terminée.

À ce stade, les services d’agent doivent démarrer automatiquement pour permettre à l’agent de charger en toute sécurité les données requises dans le service cloud.

Si vous n’avez pas rempli tous les prérequis, les avertissements s’affichent dans la fenêtre PowerShell. Veillez à remplir les exigences avant d’installer l’agent. La capture d’écran suivante montre un exemple de ces avertissements.

Pour vérifier que l’agent a été installé, recherchez les services suivants sur le serveur. Si vous avez terminé la configuration, ils doivent déjà être en cours d’exécution. Dans le cas contraire, ils sont arrêtés tant que la configuration n’est pas terminée.

- Service Diagnostics d’Entra Connect Health AD FS
- Service d'aperçus d’Entra Connect Health AD FS
- Service d'analyse d’Entra Connect Health AD FS

### Installer l’agent pour Sync

L’agent Entra Connect Health for Sync est installé automatiquement dans la dernière version d’Entra Connect. Pour utiliser Entra Connect for Sync, téléchargez la dernière version d’Entra Connect et installez-la.

Pour vérifier que l’agent a été installé, recherchez les services suivants sur le serveur. Si vous avez terminé la configuration, les services doivent déjà être en cours d’exécution. Dans le cas contraire, ils sont arrêtés tant que la configuration n’est pas terminée.

- Entra Connect Health Sync Insights Service
- Entra Connect Health Sync Monitoring Service

Remarque

N’oubliez pas que vous devez avoir Entra ID Premium pour utiliser Entra Connect Health. Si vous n’avez pas Entra ID Premium, vous ne pouvez pas terminer la configuration dans le portail Azure.


## Gérer Entra Health

Cette section décrit différentes opérations que vous pouvez effectuer à l'aide d’Entra Connect Health.

### Activer les notifications par e-mail

Vous pouvez configurer le service Entra Connect Health Service pour qu’il envoie des notifications par courrier électronique quand des alertes indiquent que votre infrastructure d’identité présente un défaut d’intégrité. Cela se produit lorsqu’une alerte est générée et lorsqu’elle est résolue.

Note

Les notifications par e-mail sont activées par défaut.

#### Pour activer les notifications par e-mail Entra Connect Health

1. Ouvrez la boîte de dialogue **Alertes** pour le service pour lequel vous souhaitez recevoir une notification par e-mail.
2. Dans la barre d’action, sélectionnez **Paramètres de notification**.
3. Placez le commutateur de notifications par e-mail sur la position **ON**.
4. Cochez la case si vous souhaitez que tous les administrateurs généraux reçoivent des notifications par e-mail.
5. Si vous souhaitez recevoir des notifications par e-mail à d’autres adresses, indiquez-les dans la zone **Destinataires d’e-mail supplémentaires**. Pour supprimer une adresse e-mail de cette liste, sélectionnez l’entrée, puis **Supprimer**.
6. Pour finaliser les modifications, sélectionnez **Enregistrer**. Les modifications prennent effet uniquement après l’enregistrement.

Note

En cas de problème de traitement des demandes de synchronisation dans notre service principal, ce service envoie un e-mail de notification à l’adresse de messagerie du contact administratif de votre locataire, avec les détails de l’erreur. Des clients nous ont signalé que le volume de ces messages est parfois trop important, ce qui nous permet de modifier la façon dont nous les envoyons.

Au lieu d’envoyer un message pour chaque erreur de synchronisation à chaque fois que cela se produit, nous enverrons une synthèse quotidienne de toutes les erreurs renvoyées par le service principal. Cela permet aux clients de traiter ces erreurs de manière plus efficace et de réduire le nombre de messages d’erreur dupliqués.

### Supprimer une instance de serveur ou de service

Note

La licence Entra ID Premium est nécessaire pour les étapes de suppression.

Dans certains cas, vous pouvez souhaiter retirer un serveur de la surveillance. Voici ce que vous devez savoir pour supprimer un serveur du service Entra Connect Health.

Quand vous supprimez un serveur, tenez compte des points suivants :

- Cette action arrête la collecte des données de ce serveur. Ce serveur est retiré du service de surveillance. Après l’exécution de cette action, vous n’avez plus accès aux nouvelles alertes, ni aux données de surveillance et d’analytique de l’utilisation pour ce serveur.
- Cette action ne désinstalle pas l’Agent d’intégrité de votre serveur. Si vous n’avez pas désinstallé l’agent d’intégrité avant d’exécuter cette étape, il est possible que des erreurs associées à l’agent d’intégrité s’affichent sur le serveur.
- Cette action ne supprime pas les données déjà collectées à partir de ce serveur. Les données sont supprimées conformément à la stratégie de conservation des données Azure.
- Après avoir effectué cette opération, si vous souhaitez recommencer à surveiller le même serveur, vous devez désinstaller puis réinstaller l’agent d’intégrité sur ce serveur.

#### Supprimer un serveur du service Entra Connect Health

Note

La licence Entra ID Premium est nécessaire pour les étapes de suppression.

Entra Connect Health pour Active Directory Federation Services (AD FS) et Entra Connect (Sync) :

1. Ouvrez l’écran **Serveur** dans la boîte de dialogue **Liste des serveurs** en sélectionnant le nom du serveur à supprimer.
2. Dans l’écran **Serveur**, dans la barre d’action, sélectionnez **Supprimer**.

1. Confirmez en tapant le nom du serveur dans la zone de confirmation.
2. Sélectionnez **Supprimer**.

Entra Connect Health pour Entra Domain Services :

1. Ouvrez le tableau de bord **Contrôleurs de domaine**.
2. Sélectionnez le contrôleur de domaine à supprimer.
3. Dans la barre d’action, sélectionnez **Supprimer les éléments sélectionnés**.
4. Confirmez l’action pour supprimer le serveur.
5. Sélectionnez **Supprimer**.

#### Supprimer une instance de service d’Entra Connect Health Service

Dans certains cas, vous souhaiterez supprimer une instance de service. Voici ce que vous devez savoir pour supprimer une instance de service du service Entra Connect Health.

Quand vous supprimez une instance de service, tenez compte des points suivants :

- Cette action supprime l’instance de service active du service de surveillance.
- Cette action ne supprime pas et ne désinstalle pas l’agent d’intégrité des serveurs qui étaient surveillés dans le cadre de cette instance de service. Si vous n’avez pas désinstallé l’agent d’intégrité avant d’exécuter cette étape, il est possible que des erreurs associées à l’agent d’intégrité s’affichent sur les serveurs.
- Toutes les données de cette instance de service sont supprimées conformément à la stratégie de conservation des données Azure.
- Après avoir effectué cette opération, si vous souhaitez commencer à surveiller le service, vous devez désinstaller puis réinstaller l’agent d’intégrité sur tous les serveurs. Après avoir effectué cette opération, si vous souhaitez recommencer à surveiller le même serveur, vous devez désinstaller, réinstaller puis inscrire l’agent d’intégrité sur ce serveur.

#### Pour supprimer une instance de service d’Entra Connect Health Service

1. À partir de l’écran **Liste des services**, ouvrez la boîte de dialogue **Service** en sélectionnant l’identificateur de service (nom de batterie) que vous souhaitez supprimer.
2. Dans l’écran **Service** , dans la barre d’actions, sélectionnez **Supprimer**.

1. Confirmez en tapant le nom du service dans la boîte de confirmation (par exemple : sts.contoso.com).
2. Sélectionnez **Supprimer**.

### Gérer l’accès avec Access Control basé sur un rôle Azure

Le contrôle d’accès en fonction du rôle Azure (Azure RBAC) pour Entra Connect Health fournit un accès aux utilisateurs et aux groupes. Azure RBAC attribue des rôles aux utilisateurs et groupes concernés, et fournit un mécanisme pour partager les responsabilités d’administration au sein de votre annuaire. Toujours le principe du privilège minimum lors de l’attribution d’un accès.

#### Rôles

Entra Connect Health prend en charge les rôles intégrés suivants :

| **Role** | **Permissions** |
|---|---|
| Propriétaire | Les propriétaires peuvent *gérer l’accès* (par exemple, affecter un rôle à un utilisateur ou à un groupe), *afficher toutes les informations* (par exemple, afficher des alertes) à partir du portail et *modifier les paramètres* (par exemple, envoyer des notifications par courrier électronique) au sein d’Entra Connect Health. Par défaut, les administrateurs généraux Entra reçoivent ce rôle et ne peuvent pas être modifiés. |
| Collaborateur | Les contributeurs peuvent *afficher toutes les informations* (par exemple, afficher des alertes) à partir du portail et *modifier les paramètres* (par exemple, envoyer des notifications par courrier électronique) au sein d’Entra Connect Health. |
| Lecteur | Les lecteurs peuvent *afficher toutes les informations* (par exemple, afficher des alertes) à partir du portail au sein d’Entra Connect Health. |

Tous les autres rôles, comme Administrateurs de l’accès utilisateur ou Utilisateurs DevTest Labs, n’ont aucun impact sur l’accès au sein d’Entra Connect Health, même s’ils sont disponibles au cours de l’utilisation du portail.

#### Étendue d’accès

Entra Connect Health prend en charge la gestion de l’accès à deux niveaux :

- **Toutes les instances de service** : il s’agit du chemin recommandé dans la plupart des cas. Il contrôle l’accès pour toutes les instances de service (par exemple, une batterie de serveurs AD FS) parmi tous les types de rôle surveillées par Entra Connect Health.
- **Instance de service** : dans certains cas, vous devrez peut-être séparer l’accès en fonction des types de rôles ou d’une instance de service. Dans ce cas, vous pouvez gérer l’accès au niveau de l’instance de service.

L’autorisation est accordée si un utilisateur final a accès au niveau Annuaire ou Instance de service.

#### Autoriser les utilisateurs ou les groupes à accéder à Entra Connect Health

Les étapes suivantes montrent comment autoriser l’accès.

**Étape 1 : Sélectionner l’étendue d’accès appropriée**

Pour autoriser l’accès d’un utilisateur au niveau *de toutes les instances de service* dans Entra Connect Health, ouvrez l’écran principal dans Entra Connect Health.

**Étape 2 : Ajouter des utilisateurs et des groupes et attribuer des rôles**

1. Dans la section **Configurer** , sélectionnez **Utilisateurs**.

1. Sélectionnez **Ajouter**.
2. Dans le volet **Sélectionner un rôle** , sélectionnez un rôle (par exemple, **Propriétaire**).

1. Tapez le nom ou l’identificateur du groupe ou de l’utilisateur cible. Vous pouvez sélectionner un ou plusieurs utilisateurs ou groupes en même temps. Sélectionnez **Sélectionner**.

1. Cliquez sur **OK**.
2. Une fois l’affectation de rôle terminée, les utilisateurs et les groupes apparaissent dans la liste.

Les utilisateurs et les groupes répertoriés ont désormais accès, en fonction des rôles qui leur sont affectés.

- La fonctionnalité Inviter des utilisateurs n’est pas prise en charge dans Entra Connect Health.

**Étape 3 : Partager l’emplacement avec des utilisateurs ou des groupes**

1. Une fois les autorisations affectées, un utilisateur peut accéder à Entra Connect Health à [cette adresse](https://aka.ms/aadconnecthealth).
2. Sur l’écran, l’utilisateur peut épingler l’écran ou différentes parties du tableau de bord. Sélectionnez l’icône **Épingler au tableau de bord**.

#### Supprimer des utilisateurs ou des groupes

Vous pouvez supprimer un utilisateur ou un groupe ajoutés à Entra Connect Health et à RBAC Azure. Sélectionnez l’utilisateur ou le groupe avec l’action secondaire, puis sélectionnez **Supprimer**.

### Diagnostiquer et corriger les erreurs de synchronisation d’attribut en double

### Aperçu

Allant plus loin dans la mise en évidence des erreurs de synchronisation, Entra Connect Health permet la correction en libre-service des erreurs. Il résout les erreurs de synchronisation d’attribut en double et corrige les objets qui sont orphelins à partir d’Entra ID. La fonctionnalité de diagnostic présente les avantages suivants :

- Elle fournit une procédure de diagnostic qui limite les erreurs de synchronisation d’attribut en double. Elle fournit également des correctifs spécifiques.
- Elle applique un correctif pour des scénarios dédiés à partir d’Entra ID pour résoudre l’erreur en une seule étape.
- Aucune mise à niveau ou configuration n’est nécessaire pour activer cette fonctionnalité.

### Problèmes

#### Un scénario courant

Quand des erreurs de synchronisation de **QuarantinedAttributeValueMustBeUnique** et de **AttributeValueMustBeUnique** se produisent, il est courant de voir un conflit de**UserPrincipalName** ou de **Proxy Addresses** dans Entra ID. Vous pouvez résoudre les erreurs de synchronisation en mettant à jour l’objet source en conflit à partir du côté local. L’erreur de synchronisation est résolue après la prochaine synchronisation. Par exemple, cette image indique que deux utilisateurs ont un conflit de leur **UserPrincipalName**. Les deux sont **Joe.J@contoso.com**. Les objets en conflit sont mis en quarantaine dans Entra ID.

![Diagramme des scénarios courants de diagnostic d’erreur de synchronisation. Emplacement le plus probable où voir les erreurs.](https://learn.microsoft.com../../wwl-sci/implement-manage-hybrid-identity/media/identity-fix-common-case.png)

#### Scénario d’objet orphelin

Parfois, vous pouvez constater qu’un utilisateur existant perd **l’ancre source**. La suppression de l’objet source s’est produite dans Active Directory local. Mais le changement de signal de suppression n’a jamais été synchronisé avec Entra ID. Cette perte se produit pour des raisons comme des problèmes de moteur de synchronisation ou une migration de domaine. Quand le même objet est restauré ou recréé, un utilisateur existant doit logiquement être l’utilisateur à synchroniser à partir de **l’ancre source**.

Quand un utilisateur existant est un objet cloud uniquement, vous pouvez également voir l’utilisateur en conflit synchronisé avec Entra ID. L’utilisateur ne peut pas être mis en correspondance avec l’objet existant lors de la synchronisation. Il n’existe aucun moyen direct pour remapper **l’ancre source**.

Par exemple, l’objet existant dans Entra ID conserve la licence de Joe. Un objet nouvellement synchronisé avec une autre **ancre source** se produit dans un état d’attribut dupliqué dans Entra ID. Les changements apportés à Joe sur Active Directory local ne sont pas appliqués à l’utilisateur d’origine de Joe (objet existant) dans Entra ID.

### Étapes de diagnostic et de dépannage dans Connect Health

La fonctionnalité de diagnostic prend en charge les objets utilisateur avec les attributs dupliqués suivants :

| **Nom de l’attribut** | **Types d’erreurs de synchronisation** |
|---|---|
| Nom Principal de l'Utilisateur | QuarantinedAttributeValueMustBeUnique ou AttributeValueMustBeUnique |
| ProxyAddresses | QuarantinedAttributeValueMustBeUnique ou AttributeValueMustBeUnique |
| SipProxyAddress | AttributeValueMustBeUnique |
| OnPremiseSecurityIdentifier | AttributeValueMustBeUnique |

Important

Pour accéder à cette fonctionnalité, une autorisation **Contributeur** à partir d’Azure RBAC est requise.

Suivez les étapes à partir du portail Azure pour affiner les détails des erreurs de synchronisation et fournir des solutions plus spécifiques :

![Digramme des étapes de diagnostic d’erreur de synchronisation. Utilisez ces étapes pour atteindre une résolution.](https://learn.microsoft.com../../wwl-sci/implement-manage-hybrid-identity/media/identity-fix-steps.png)

À partir du portail Azure, effectuez quelques étapes pour identifier des scénarios de réparation spécifiques :

1. Vérifiez la colonne **État du diagnostic**. L’état indique s’il existe un moyen de corriger une erreur de synchronisation directement à partir d’Entra ID. En d’autres termes, il existe un flux de résolution des problèmes pour cibler l’erreur et essayer de la corriger.

| **État** | **Qu’est-ce que cela signifie ?** |
|---|---|
| Non démarré | Vous n’avez pas visité ce processus de diagnostic. Selon le résultat du diagnostic, il existe un éventuel moyen de résoudre l’erreur de synchronisation directement à partir du portail. |
| Correction manuelle requise | L’erreur ne correspond pas aux critères des correctifs disponibles dans le portail. Soit les types d’objets en conflit ne sont pas des utilisateurs, soit vous avez déjà parcouru les étapes de diagnostic et aucune résolution n’était disponible à partir du portail. Dans ce dernier cas, un correctif à partir du côté local est toujours l’une des solutions. |
| Synchronisation en attente | Un correctif a été appliqué. Le portail attend le prochain cycle de synchronisation pour effacer l’erreur. |

1. Sélectionnez le bouton **Diagnostiquer** situé sous les détails de l’erreur. Vous allez répondre à quelques questions et identifier les détails de l’erreur de synchronisation. Les réponses aux questions permettent d’identifier un cas d’objet orphelin.
2. Si un bouton **Fermer** s’affiche à la fin des diagnostics, aucun correctif rapide n’est disponible à partir du portail, d’après les réponses que vous avez données. Reportez-vous à la solution indiquée à la dernière étape. Les correctifs disponibles en local sont toujours les solutions. Sélectionnez le bouton **Fermer**. L’état de l’erreur de synchronisation actuelle passe à **Correction manuelle requise**. L’état reste inchangé pendant le cycle de synchronisation en cours.
3. Une fois qu’un cas d’objet orphelin est identifié, vous pouvez résoudre les erreurs de synchronisation d’attribut en double directement à partir du portail. Pour déclencher le processus, sélectionnez le bouton **Appliquer le correctif**. L’état de l’erreur de synchronisation en cours est mis à jour pour devenir **En attente de synchronisation**.
4. Après le cycle de synchronisation suivant, l’erreur doit être supprimée de la liste.


## Évaluation du module

Choisissez la meilleure réponse à chacune des questions ci-dessous.

### Vérifiez vos connaissances


## Résumé et ressources

Maintenant que vous avez passé en revue ce module, vous pouvez :

- Planifier, concevoir et implémenter Entra Directory Connect (AADC), y compris la synchronisation de hachage de mot de passe (PHS), l’authentification directe (PTA), l’authentification unique transparente (SSO transparente) et la fédération
- Gérer Entra Directory Connect (AADC)
- Gérer la synchronisation de hachage de mot de passe (PHS)
- Gérer l’authentification directe (PTA)
- Gérer l’authentification unique transparente (Seamless SSO)
- Gérer la fédération en excluant les déploiements ADFS manuels
- Résolution des problèmes de synchronisation
- Implémenter et gérer Entra Connect Health

### Ressources

- [Qu’est-ce que l’identité hybride avec l’ID Entra ?](https://learn.microsoft.com/fr-fr/azure/active-directory/hybrid/whatis-hybrid-identity)
- [Intégrer une forêt AD unique à l’aide du hachage de mot de passe](https://learn.microsoft.com/fr-fr/azure/active-directory/hybrid/tutorial-password-hash-sync)
- [Documentation sur l’identité hybride](https://learn.microsoft.com/fr-fr/azure/active-directory/hybrid/)
- [Entra Connect - Configurer l’autorisation de compte de connecteur AD DS](https://learn.microsoft.com/fr-fr/azure/active-directory/hybrid/how-to-connect-configure-ad-ds-connector-account)
