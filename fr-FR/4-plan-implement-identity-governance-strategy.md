# Planifier et implémenter une stratégie de gouvernance des identités

> SC-300 — learning path 4/4
> https://learn.microsoft.com/fr-fr/training/paths/plan-implement-identity-governance-strategy/

## Modules

- **Planifier et implémenter la gestion des droits d’utilisation** (10 units)
- **Planifier, implémenter et gérer la révision d’accès** (10 units)
- **Planifier et implémenter un accès privilégié** (11 units)
- **Surveiller et gérer Entra ID** (9 units)


---

# Planifier et implémenter la gestion des droits d’utilisation

_https://learn.microsoft.com/fr-fr/training/modules/plan-implement-entitlement-management/_


## Présentation

De nouveaux utilisateurs ou utilisateurs externes qui rejoignent votre site ont besoin d’affectations d’accès pour Azure solutions. Lorsque les utilisateurs attendent des ressources, vous risquez de perdre leur engagement et leur productivité. Découvrez comment faire en sorte que les utilisateurs accèdent à votre site et à vos ressources. Dans ce module, vous allez apprendre à fournir l’accès approprié à vos utilisateurs, à créer des révisions pour cet accès et plus encore.

### Objectifs d’apprentissage

À la fin de ce module, vous pourrez :

- Définir des catalogues.
- Définir des packages d’accès.
- Planifier, mettre en œuvre et gérer les droits.
- Implémenter et gérer les conditions d’utilisation.
- Gérez le cycle de vie des utilisateurs externes dans les paramètres Gouvernance des identités Entra.
- Configurez et gérez les organisations connectées.
- Passez en revue les droits par utilisateur.

### Prérequis

Aucun.


## Définir des packages d’accès

### Pourquoi utiliser la gestion des droits d’utilisation ?

Les entreprises souvent font face à des défis lorsqu’il leur faut gérer l’accès des employés aux ressources, notamment :

- Les utilisateurs ne connaissent pas l’accès dont ils ont besoin et même s’ils le connaissent, ils peuvent rencontrer des difficultés pour trouver les personnes habilitées à approuver leur accès
- Après avoir localisé une ressource et obtenu l'accès correspondant, les utilisateurs y ont accès plus longtemps que nécessaire à des fins professionnelles

Ces problèmes sont complexes pour les utilisateurs qui ont besoin d'un accès à partir d'une autre organisation, tels que les utilisateurs externes issus d'organisations de la chaîne logistique ou d'autres partenaires commerciaux. Par exemple, la gestion des droits d’utilisation Entra aide les organisations à garantir que chacun accède aux répertoires appropriés et que tous les accès utilisateur sont gérés de manière cohérente.

Cette vidéo fournit une vue d’ensemble de la gestion des droits d’utilisation et de son intérêt :

**Regardez cette vidéo pour en savoir plus sur la gestion des droits d’utilisation Entra**

### À quoi sert la gestion des droits d'utilisation ?

Les fonctionnalités de gestion des droits d’utilisation sont les suivantes :

| **Fonctionnalité de gestion des droits d’utilisation** | **Description et valeur** |
|---|---|
| Déléguer à des non-administrateurs la possibilité de créer des packages d’accès. | Ces packages d’accès contiennent des ressources que les utilisateurs peuvent demander ; les gestionnaires délégués de package d’accès ont la possibilité de définir des stratégies avec des règles pour lesquelles les utilisateurs peuvent demander quelles personnes doivent approuver leur accès et quand l’accès expire. |
| Sélectionner les organisations connectées dont les utilisateurs peuvent demander l’accès. | Lorsqu’un utilisateur, qui n’est pas encore dans votre annuaire demande l’accès, et qu’il est approuvé, il est automatiquement invité dans votre annuaire, et l’accès lui est affecté. Lorsque son accès expire, s’il n’a pas d’autres affectations de package d’accès, son compte B2B dans votre annuaire peut être automatiquement supprimé. |

### Abrégé de terminologie

Avant d’explorer la gestion des droits d’utilisation et sa documentation en détail, vous devez connaître les termes ci-dessous. N’hésitez pas à nous faire référence à cette liste à tout moment au cours de ce cours.

| **Terme** | **Description** |
|---|---|
| package d'accès | Bundle de ressources dont une équipe ou un projet a besoin et qui est régi par des stratégies. Un package d’accès est toujours contenu dans un catalogue. Vous créez un package d’accès pour un scénario dans lequel les utilisateurs doivent demander l’accès. |
| demande d’accès | Demande d’accès aux ressources dans un package d’accès. Cette demande transite généralement par un flux d’approbation. Si elle est approuvée, l’utilisateur demandeur reçoit une affectation de package d’accès. |
| affectation | L’affectation d’un package d’accès à un utilisateur garantit que l’utilisateur dispose de tous les rôles de ressources de ce package d’accès. Les affectations de package d’accès ont généralement une durée limite avant leur expiration. |
| catalogue | Conteneur de ressources connexes et de packages d’accès. Les catalogues sont utilisés pour la délégation, si bien que les non-administrateurs peuvent créer leurs propres packages d’accès. Les propriétaires de catalogue peuvent ajouter les ressources qu’ils possèdent à un catalogue. |
| créateur de catalogue | Regroupement d’utilisateurs autorisés à créer des catalogues. Lorsqu’un utilisateur non-administrateur, autorisé à être créateur de catalogue, crée un catalogue, il devient automatiquement le propriétaire de ce catalogue. |
| organisation connectée | Un répertoire ou un domaine Entra externe avec lequel vous entretenez une relation. Les utilisateurs provenant d’une organisation connectée peuvent être spécifiés dans une stratégie comme étant autorisés à demander l’accès. |
| policy | Ensemble de règles définissant le cycle de vie d’un accès, telles que le mode d’accès des utilisateurs, les approbateurs et la durée d’accès par le biais d’une affectation. Une stratégie est liée à un package d’accès. Par exemple, un package d’accès peut avoir deux stratégies de demande d’accès : l’une pour les employés, l’autre pour les utilisateurs externes. |
| resource | Ressource (un groupe Office, un groupe de sécurité, une application ou un site SharePoint Online, par exemple) dotée d’un rôle pour lequel un utilisateur peut obtenir des autorisations. |
| répertoire de ressources | Répertoire comprenant une ou plusieurs ressources à partager. |
| rôle de ressource | Collection d’autorisations associées à une ressource et définies par elle. Un groupe a deux rôles : membre et propriétaire. Les sites SharePoint ont généralement trois rôles, mais peuvent avoir des rôles personnalisés supplémentaires. Les applications peuvent avoir plusieurs rôles personnalisés. |

### Que sont les packages d’accès et quelles ressources gérer avec eux ?

La gestion des droits d’utilisation introduit, dans Entra ID, le concept de *package d’accès*. Un package d’accès regroupe toutes les ressources avec l’accès dont un utilisateur a besoin pour travailler sur un projet ou accomplir sa tâche. Les packages d’accès permettent de régir l’accès de vos employés et utilisateurs internes en dehors de votre organisation. Vous pouvez gérer l’accès des utilisateurs aux ressources suivantes avec la gestion des droits d’utilisation :

- Appartenance à des groupes de sécurité Entra.
- Appartenance des groupes et équipes Microsoft 365.
- Affectation aux applications d’entreprise Entra, y compris aux applications SaaS et aux applications à intégration personnalisée qui prennent en charge la fédération/l’authentification unique et/ou le provisionnement.
- Appartenance des sites SharePoint Online.

Vous pouvez également contrôler l'accès à d'autres ressources qui dépendent des groupes de sécurité Entra ou des groupes Microsoft 365. Par exemple, vous pouvez accorder :

- Des licences pour Microsoft 365 en utilisant un groupe de sécurité dans un package d’accès et en configurant la Gestion des licences par groupe pour ce groupe.
- Un accès pour gérer des ressources Azure en utilisant un groupe de sécurité dans un package d’accès et en créant une attribution de rôle Azure pour ce groupe.
- Un accès pour gérer des rôles Entra en utilisant des groupes attribuables à des rôles dans un package d’accès et en attribuant un rôle à ce groupe.

### Comment contrôler qui a accès ?

Avec un **package d’accès**, un administrateur ou un gestionnaire délégué de package d’accès liste les ressources (groupes, applications et sites) et les rôles dont les utilisateurs ont besoin pour ces ressources.

Les packages d’accès incluent également une ou plusieurs *stratégies*. Une stratégie définit les règles ou barrières mises en place pour l’affectation d’un package d’accès. Chaque stratégie garantit que seuls les utilisateurs appropriés peuvent demander l’accès, que leur requête a des approbateurs, et que leur accès à ces ressources est limité dans le temps et expire s’il n’est pas renouvelé.

Dans chaque stratégie, un administrateur ou un gestionnaire de package d’accès définit trois éléments : les utilisateurs existants éligibles à la demande d’accès, le processus d’approbation ou de refus d’accès, et la durée de l’accès d’un utilisateur.

### Quand utiliser des packages d’accès ?

Les packages d’accès ne remplacent pas d’autres mécanismes d’attribution d’accès. Ils sont particulièrement indiqués dans les cas suivants :

- Les employés ont besoin d’un accès limité dans le temps pour une tâche particulière. Par exemple, la gestion de licences par groupe et un groupe dynamique permettent de vérifier que tous les employés disposent d’une boîte aux lettres Exchange Online. Les packages d’accès couvrent ensuite les situations où les employés ont besoin d’un accès supplémentaire, par exemple pour lire les ressources d’un service à partir d’un autre service.
- Accès qui nécessite l’approbation du responsable d’un employé ou d’autres personnes désignées.
- Les services souhaitent gérer leurs propres stratégies d’accès à leurs ressources sans implication informatique.
- Deux organisations ou plus collaborent sur un projet et, par conséquent, plusieurs utilisateurs d'une organisation devront être amenés via Entra B2B pour accéder aux ressources d'une autre organisation.

Le diagramme suivant montre un exemple des différents éléments en matière de gestion des droits d'utilisation :

![Diagramme de vue d’ensemble de la gestion des droits d’utilisation. Flux de processus et composants du droit.](https://learn.microsoft.com../../wwl-sci/plan-implement-entitlement-management/media/entitlement-management-overview.png)

Dans **le package d'accès 1**, il n’y a qu’un seul groupe en tant que ressource. L’accès est défini par une stratégie qui autorise un ensemble d’utilisateurs du répertoire à demander un accès. Le **package d’accès 2** comprend un groupe, une application et un site SharePoint Online en tant que ressources. L’accès est défini par deux stratégies différentes. La première stratégie autorise un ensemble d’utilisateurs du répertoire à demander un accès. La seconde stratégie permet aux utilisateurs d'un répertoire externe de demander un accès.


## Exercice : création et gestion d’un catalogue de ressources avec une gestion des droits d’utilisation d’Entra

### Créer un compte Azure et ajouter des licences d’essai Entra ID Premium P2

Les tâches de cet exercice nécessitent un abonnement Azure. Vous trouverez également les exercices de ce parcours d’apprentissage nécessitant un abonnement Azure. Si vous n'en avez pas encore, vous pouvez vous inscrire à un compte d'essai Azure. Si vous avez déjà votre propre abonnement Azure, vous pouvez ignorer cette tâche.

1. Dans un navigateur web, accédez au [portail Microsoft Azure](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
2. Faites défiler la page pour découvrir tous les avantages et les services gratuits disponibles.
3. Sélectionnez **Démarrer gratuitement**.
4. Utilisez l’Assistant pour souscrire à votre abonnement d’essai gratuit Azure.
5. Vous avez besoin d’une licence Entra ID P2 pour effectuer certains des exercices. Dans l'organisation que vous avez créée, recherchez et sélectionnez **Entra ID**.
6. Dans le menu de navigation gauche, sélectionnez **Prise en main**.
7. Sous Bien démarrer avec Entra ID, sélectionnez **Obtenir un essai gratuit pour Entra ID Premium**.
8. Dans le volet Activer, sous **Entra ID PREMIUM P2**, sélectionnez **Essai gratuit**, puis **Activer**.
9. Dans le menu de navigation, sélectionnez **Vue d’ensemble**.
10. Actualisez le navigateur jusqu’à ce qu’Entra ID Premium P2 s’affiche sous le nom de l’organisation. Cela prend quelques minutes.
11. L’activation de la licence prend quelques minutes. Vous devez vous déconnecter et vous reconnecter à Microsoft Azure. Essayez de redémarrer si vous rencontrez des problèmes avec des fonctionnalités qui ne sont pas disponibles alors qu’elles devraient l’être.

### Créer un catalogue

Un catalogue est un conteneur de ressources et de packages d’accès. Vous créez un catalogue lorsque vous souhaitez regrouper des ressources et packages d’accès liés. La personne qui crée le catalogue en devient le premier propriétaire. Un propriétaire de catalogue peut ajouter d’autres propriétaires de catalogue.

1. Connectez-vous au [Centre d’administration Entra](https://entra.microsoft.com/) en tant qu’administrateur.
  - Abonnement Entra ID Premium P1, P2, EMS E3 ou EMS E5.
  - Si vous n’avez pas l’un de ces abonnements, vous pouvez obtenir Entra ID Premium ou activer la version d’évaluation d’Entra ID Premium.
  - Un des comptes d’administrateur suivants pour le répertoire que vous souhaitez configurer :
    - Administrateur de la sécurité
    - Administrateur de l’accès conditionnel

2. Dans l’écran d’accueil de **Entra ID**, sélectionnez **Gouvernance des identités**.
3. Dans le menu de gauche, sous **Gestion des droits d'utilisation**, sélectionnez **Catalogues**.
4. Dans le menu supérieur, sélectionnez **+Nouveau catalogue**.
5. Dans le volet Nouveau catalogue, dans la zone **Nom** , entrez **Marketing**.
6. Dans la zone **Description**, entrez **Pour les utilisateurs du service marketing**. Les utilisateurs verront ces informations dans les détails d’un package d’accès.
7. **Activé pour les utilisateurs externes** permet aux utilisateurs des répertoires externes sélectionnés d’être en mesure de demander des packages d’accès dans ce catalogue. Aucune modification ne sera apportée à ce paramètre.
8. Sous **Activé, sélectionnez Non**. Vous pouvez choisir d’activer le catalogue pour un usage immédiat. Vous pouvez le désactiver si vous envisagez de l’indexer ou de le garder indisponible. Dans le cadre de cet exercice, il n’est pas nécessaire d’activer le catalogue.
9. Sélectionnez Créer.

### Ajouter des ressources à un catalogue

Pour inclure des ressources dans un package d’accès, les ressources doivent exister dans un catalogue. Les types de ressources que vous pouvez ajouter sont des groupes, des applications et des sites SharePoint Online. Les groupes peuvent être des groupes Microsoft 365 ou des groupes de sécurité Entra créés sur le cloud. Pour les applications, il peut s’agir d’applications d’entreprise Entra, ce qui comprend les applications SaaS et vos propres applications fédérées à Entra ID. Pour les sites, il peut s’agir de sites ou de collection de sites SharePoint Online.

1. Dans l’écran Gouvernance des identités, si nécessaire, sélectionnez **Catalogues**.
2. Dans la liste **Catalogues**, sélectionnez **Marketing**.
3. Dans le volet de navigation de gauche, sous **Gérer**, sélectionnez **Ressources**.
4. Dans le menu, sélectionnez + **Ajouter des ressources**.
5. Dans l’écran Ajouter des ressources au catalogue, passez en revue les options disponibles.
6. Vous n’avez peut-être pas sélectionné de ressources dans des groupes et des équipes, des applications ou des sites SharePoint. Pour ajouter une ressource au catalogue, sélectionnez une catégorie de ressources, puis sélectionnez une ressource dans cette catégorie. Pour cet exercice, vous pouvez choisir n’importe quelle ressource disponible.
7. Lorsque vous avez terminé, sélectionnez **Ajouter**. Ces ressources peuvent désormais être incluses dans des packages d’accès du catalogue.

### Ajouter plus de propriétaires de catalogue

L’utilisateur qui a créé un catalogue devient le premier propriétaire de catalogue. Pour déléguer la gestion d’un catalogue, vous ajoutez des utilisateurs au rôle de propriétaire de catalogue. Ainsi, les responsabilités de la gestion du catalogue sont mieux partagées.

1. Dans le catalogue marketing, dans le menu de navigation de gauche, sélectionnez Rôles et administrateurs. Au besoin, dans le portail Azure, accédez à **Entra ID**, **Gouvernance des identités**, puis **Catalogues** et sélectionnez **Marketing**.
2. Dans le menu supérieur, passez en revue les rôles disponibles, puis sélectionnez **+ Ajouter un propriétaire**.
3. Dans le volet Sélectionner un membre, sélectionnez votre compte administrateur, puis sélectionnez **Sélectionner**.
4. Examinez le rôle qui vient d’être ajouté dans la liste rôles et administrateurs.

### Modifier un catalogue

Vous pouvez modifier le nom et la description d’un catalogue. Les utilisateurs verront ces informations dans les détails d’un package d’accès.

1. Dans l’écran Marketing, dans le volet de navigation de gauche, sélectionnez **Vue d’ensemble**.
2. Dans le menu du haut, sélectionnez **Modifier**.
3. Vérifiez le paramètre et, sous **Propriétés** dans le champ **Activé**, sélectionnez **Oui**.
4. Sélectionnez **Enregistrer**.

### Supprimer un catalogue

Vous pouvez supprimer un catalogue, mais seulement s’il ne contient pas de packages d’accès.

1. Dans la page Vue d’ensemble du Catalogue marketing, dans le menu supérieur, sélectionnez Supprimer.
2. Dans la boîte de dialogue Supprimer, passez en revue les informations, puis sélectionnez **Oui**.


## Configurer la gestion des droits d’utilisation

Il existe plusieurs façons de configurer la gestion des droits d’utilisation pour votre organisation. Toutefois, si vous venez de commencer, il est utile de comprendre les scénarios courants pour les administrateurs, les propriétaires de catalogue, les gestionnaires de package d’accès, les approbateurs et les demandeurs.

- Déléguer
  - Administrateur : Déléguer la gestion des ressources.
  - Créateur de catalogue : Déléguer la gestion des ressources.
  - Propriétaire du catalogue : déléguer la gestion des ressources.
  - Propriétaire du catalogue : déléguer la gestion des packages d’accès via l’attribution du rôle gestionnaire de package d’accès.

- Régir l’accès aux utilisateurs de votre organisation
- Gestionnaire de package d’accès : autoriser les employés de votre organisation à demander l’accès aux ressources.
- Demandeur : demander l’accès aux ressources.
- Approbateur : approuver des demandes de ressources.
- Demandeur : affichez les ressources auxquelles vous avez déjà accès.
- Régir l’accès pour les utilisateurs externes à votre organisation
  - Administrateur : Collaborez avec une organisation partenaire externe.
  - Gestionnaire de package Access : Collaborez avec une organisation partenaire externe.
  - Demandeur : Demander l’accès aux ressources en tant qu’utilisateur externe.
  - Approbateur : approuver des demandes de ressources.
  - Demandeur : affichez les ressources auxquelles vous avez déjà accès.

- Gestion quotidienne
  - Gestionnaire de package Access : mettez à jour les ressources d’un projet.
  - Gestionnaire de package Access : mettez à jour la durée d’un projet.
  - Gestionnaire de package d’accès : mettez à jour la façon dont l’accès est approuvé pour un projet.
  - Gestionnaire de package Access : Mettez à jour les personnes d’un projet.
  - Gestionnaire de package d’accès : affectez directement des utilisateurs spécifiques à un package d’accès.

- Affectations et rapports
  - Administrateur : affichez qui a des affectations à un package d’accès.
  - Administrateur : affichez les ressources affectées aux utilisateurs.

### Administration par programmation

Vous pouvez également gérer les packages d’accès, les catalogues, les stratégies, les demandes et les affectations à l’aide de Microsoft Graph. Un utilisateur dans un rôle approprié avec une application disposant de l’autorisation déléguée `EntitlementManagement.ReadWrite.All` peut appeler [l’API de gestion des droits d’utilisation](https://learn.microsoft.com/fr-fr/graph/tutorial-access-package-api).


## Exercice : ajouter un rapport d’acceptation des conditions d’utilisation.

### Quelles sont les conditions d’utilisation de la gestion des droits d’utilisation

Les politiques de conditions d'utilisation d’Entra utilisent le format PDF pour présenter le contenu. Le fichier PDF peut contenir n'importe quel contenu, tel que des documents de contrats existants, ce qui vous permet de collecter les accords des utilisateurs finaux lors de la connexion des utilisateurs. Pour prendre en charge les utilisateurs sur les appareils mobiles, il est recommandé d’utiliser une taille de police de 24 points dans le fichier PDF. N’oubliez pas que les documents PDF des conditions d’utilisation peuvent contenir un contrat de licence utilisateur final (CLUF). L’utilisateur doit l’accepter avant d’accéder aux ressources en fonction de ses paramètres de droit d’utilisation.

### Ajouter des conditions d’utilisation

Une fois que vous avez finalisé votre document de conditions d’utilisation, utilisez la procédure suivante pour l’ajouter.

1. Connectez-vous au [Centre d'administration Entra](https://entra.microsoft.com/) en tant qu'administrateur général.
2. Ouvrez **Gouvernance des ID**.
3. Dans le menu de navigation de gauche, ouvrez Gestion des droits d'utilisation, puis, sous **Conditions d'utilisation**, sélectionnez **Conditions d'utilisation**.
4. Dans la page Conditions d’utilisation, dans le menu supérieur, sélectionnez **+ Nouvelles conditions**.
5. Dans la zone **Nom**, entrez **Conditions d’utilisation du test**. Définissez le nom des conditions d’utilisation dans le Centre d’administration.
6. Dans la zone **Nom d’affichage**, entrez **Conditions d’utilisation de contoso**. Le titre que les utilisateurs voient quand ils se connectent.
7. Cochez la **case du document Conditions d'utilisation**, recherchez votre PDF de conditions d’utilisation finalisé et sélectionnez-le. Pour cet exercice, vous pouvez choisir n'importe quel PDF. Une autre option consiste à utiliser Microsoft Word pour créer un document de conditions d’utilisation, puis à l’enregistrer au format PDF.
8. Sélectionnez la langue de votre document Conditions d’utilisation. L’option de langue vous permet de charger plusieurs conditions d’utilisation, chacune dans une langue différente. La version des conditions d’utilisation qu’un utilisateur final voit est basée sur ses préférences de navigateur.
9. Pour obliger les utilisateurs finaux à afficher les conditions d’utilisation avant de les accepter, **définissez Exiger que les utilisateurs étendent les conditions d’utilisation** sur **On**.
10. Pour exiger que les utilisateurs finaux acceptent vos conditions d’utilisation sur chaque appareil auquel ils accèdent, **définissez Exiger que les utilisateurs consentent sur chaque appareil** sur **Activé**. Les utilisateurs doivent installer d'autres applications si cette option est activée.  Avertissement Le consentement sur chaque appareil nécessite que les utilisateurs enregistrent chaque appareil avec l'ID Entra avant d’obtenir l’accès.
11. Si vous voulez faire expirer les consentements pour les conditions d’utilisation selon une planification, définissez **Faire expirer les consentements** sur **Activé**. Lorsque la valeur est on, deux paramètres de planification supplémentaires sont affichés.
12. Utilisez les paramètres **Expiration commençant le** et **Fréquence** pour spécifier la planification régissant l’expiration des conditions d’utilisation. Le tableau suivant présente deux exemples de paramètres et leur résultat :    **Expire à partir du** **Fréquence** **Résultat**     Date du jour Tous les mois À compter d’aujourd’hui, les utilisateurs doivent accepter les conditions d’utilisation et les accepter à nouveau chaque mois.   Date future Tous les mois À compter d’aujourd’hui, les utilisateurs doivent accepter les conditions d’utilisation. Quand la date future survient, les consentements expirent. Les utilisateurs doivent alors réaccepter les conditions d’utilisation chaque mois.    Par exemple, si vous définissez l’expiration à compter du **1er janvier** et la fréquence **mensuelle, voici** comment les expirations peuvent se produire pour deux utilisateurs :    **Utilisateur** **Date d’acceptation initiale** **Première date d’expiration** **Deuxième date d’expiration** **Troisième date d’expiration**     Alice 1er janvier 1er février 1er mars 1er avril   Bob 15 janvier 1er février 1er mars 1er avril
13. Utilisez le paramètre **Durée avant nouvelle acceptation requise (jours)** pour spécifier le nombre de jours au bout duquel l’utilisateur doit réaccepter les conditions d’utilisation. Ce paramètre permet aux utilisateurs de suivre leur propre planification. Par exemple, si vous définissez la durée sur **30** jours, voici comment les expirations peuvent se produire pour deux utilisateurs :    **Utilisateur** **Date d’acceptation initiale** **Première date d’expiration** **Deuxième date d’expiration** **Troisième date d’expiration**     Alice 1er janvier 31 janvier 2 mars 1er avril   Bob 15 janvier 14 février 16 mars 15 avril
14. Sous **Accès conditionnel**, sélectionnez **Stratégie personnalisée**.    **Modèle** **Description**     Stratégie personnalisée Sélectionnez les utilisateurs, les groupes et les applications auxquels les conditions d’utilisation s’appliquent.   Créer la stratégie d’accès conditionnel plus tard Les conditions d’utilisation apparaissent dans la liste des contrôles d’octroi lors de la création d’une stratégie d’accès conditionnel.
15. Lorsque vous avez terminé, sélectionnez **Créer**.
16. Lorsque les conditions d’utilisation sont créées, vous êtes redirigé vers la page de stratégie d’accès conditionnel. Dans la page, dans la zone **Nom**, entrez **Appliquer les conditions d’utilisation**.
17. Sous **Affectations**, sélectionnez **Utilisateurs et groupes**.
18. Dans l’onglet inclure, activez la case à cocher **Utilisateurs et groupes**.
19. Dans le volet Sélectionner, sélectionnez un compte que vous souhaitez utiliser pour tester la stratégie des conditions d’utilisation. Si vous choisissez votre compte d’administrateur, comme toutes les stratégies d’accès conditionnel, vérifiez que vous disposez d’un autre compte disposant d’autorisations suffisantes pour modifier la stratégie d’accès conditionnel. Vous devez vous assurer que votre compte d’administrateur n’est pas verrouillé si la stratégie d’accès conditionnel entraîne un résultat indésirable.
20. Sélectionnez **Applications ou actions cloud**.
21. Sélectionnez **Toutes les applications Cloud**.
22. Sous **Contrôles d’accès**, sélectionnez **Accorder**.
23. Dans le volet Grant, sélectionnez **Test des conditions d’utilisation**, puis sélectionnez **Sélectionner**.
24. Sous **Activer une stratégie**, sélectionnez **Activé**.
25. Lorsque vous avez terminé, sélectionnez **Créer**.
26. Si vous avez choisi d’utiliser votre propre compte, vous pouvez actualiser votre navigateur. Vous êtes invité à vous reconnecter. Lorsque vous vous connectez, vous devez à nouveau accepter les conditions d’utilisation.

### Afficher le rapport des personnes acceptées et refusées

L’écran de conditions d’utilisation indique le nombre d’utilisateurs qui ont accepté et refusé. Ce nombre, ainsi que le nom des personnes ayant accepté ou refusé, sont stockés pour toute la durée de vie des conditions d’utilisation.

1. Dans Microsoft Azure, dans **Gouvernance des identités**, puis **Conditions d’utilisation**, recherchez vos conditions d’utilisation.
2. Cliquez sur les chiffres situés sous **Accepté**et **Refusé** pour voir qui a accepté et qui a refusé les conditions d’utilisation.
3. Dans cet exercice, vous pouvez ne pas avoir de conditions d'utilisation acceptées ou refusées. Dans l’exemple suivant, la valeur **acceptée** a été sélectionnée. Vous pouvez voir les informations des utilisateurs signalés pour ceux qui ont accepté les conditions d’utilisation.
4. Pour afficher l’historique d’un utilisateur individuel, sélectionnez les points de suspension à droite du nom d’utilisateur, puis **Affichez l’historique**.
5. Le volet Afficher l’historique présente l’historique des acceptations, des refus et des expirations.

### À quoi ressemblent les conditions d’utilisation pour les utilisateurs

1. Une fois les conditions d’utilisation créées et appliquées, les utilisateurs qui sont concernés voient la page des conditions d’utilisation.
2. Les utilisateurs peuvent afficher les conditions d’utilisation et, si nécessaire, utiliser les boutons pour effectuer un zoom avant ou arrière.
3. Sur les appareils mobiles, les conditions d’utilisation s’affichent comme dans l’exemple suivant.

#### Comment les utilisateurs peuvent consulter leurs conditions d’utilisation

Les utilisateurs peuvent consulter et voir les conditions d’utilisation qu’ils ont acceptées à l’aide de la procédure suivante.

1. Accédez à [https://myaccount.microsoft.com](https://myapps.microsoft.com/), puis connectez-vous à l’aide de votre compte d’utilisateur.
2. Sur la page vue d’ensemble, sélectionnez AFFICHER LES PARAMÈTRES ET LA CONFIDENTIALITÉ.
3. Dans la page Paramètres et confidentialité, sélectionnez l’onglet **Confidentialité** .
4. Sous **l’avis de l’organisation**, vous pouvez passer en revue les conditions d’utilisation que vous avez acceptées.

### Modifier les détails des conditions d’utilisation

Vous pouvez modifier certains détails des conditions d’utilisation, mais il n’est pas possible de modifier un document existant. La procédure suivante explique comment modifier les détails.

1. Connectez-vous au [Centre d'administration Entra](https://entra.microsoft.com/) en tant qu'administrateur général.
2. Ouvrez la gouvernance des ID et sélectionnez **Gestion des droits d'utilisation**.
3. Dans le menu de navigation de gauche, sous **Conditions d’utilisation**, sélectionnez **Conditions d’utilisation**.
4. Sélectionnez les conditions d’utilisation à modifier.
5. Dans le menu du haut, sélectionnez **Modifier**.
6. Dans le volet Modifier les conditions d’utilisation, vous pouvez changer les éléments suivants :
  - **Nom** : nom interne du toU qui n’est pas partagé avec les utilisateurs finaux.
  - **Nom d'affichage** – nom que les utilisateurs finaux peuvent voir lors de l’affichage des CGU.
  - **Exiger que les utilisateurs étendent les conditions d’utilisation** : défini **sur On** force l’utilisation définitive pour développer le document de conditions d’utilisation avant de l’accepter.
  - **Mettez à jour un document des conditions d’utilisation existantes**.
  - Vous pouvez ajouter une langue à des conditions d’utilisation existantes. Vous pouvez modifier d’autres paramètres, par exemple demander aux utilisateurs de donner leur consentement sur chaque appareil et faire expirer les consentements. Vous pouvez également définir la durée avant la réacceptation, ou une stratégie d’accès conditionnel. Vous devez créer de nouvelles conditions d’utilisation.

7. Lorsque vous avez terminé, sélectionnez **Enregistrer** pour enregistrer vos paramètres.

### Mettre à jour un document des conditions d’utilisation existantes

Vous pouvez être amené à mettre à jour le document de conditions d'utilisation.

1. Sélectionnez les conditions d’utilisation à modifier.
2. Sélectionnez **Modifier les conditions**.
3. Dans le tableau **Options de langue**, identifiez les conditions d’utilisation que vous souhaitez mettre à jour, puis, dans la colonne **Action**, sélectionnez **Mettre à jour**.
4. Dans le volet Mettre à jour les conditions d’utilisation de la version, vous pouvez télécharger une nouvelle version du document sur les conditions d’utilisation.
5. Il existe également une option à bascule **Exiger une nouvelle acceptation** si vous souhaitez obliger les utilisateurs à accepter cette nouvelle version la prochaine fois qu’ils se connectent. Si vous n’avez pas besoin que vos utilisateurs réacceptent, leur consentement précédent reste actif. Seuls les nouveaux utilisateurs qui n’ont pas consenti avant ou dont le consentement expire voir la nouvelle version.
6. Une fois que vous avez téléchargé votre nouveau pdf et que vous avez décidé de le réaccepter, sélectionnez **Ajouter**.
7. Vous voyez maintenant la version la plus récente sous la colonne Document.


## Exercice : gérer le cycle de vie des utilisateurs externes avec la gouvernance des identités Entra

### Gérer le cycle de vie des utilisateurs externes dans les paramètres de Gouvernance des ID Entra

Vous pouvez choisir ce qui se passe lorsqu’un utilisateur externe ne dispose plus d’attributions de package d’accès, alors qu’il avait été invité à accéder à votre annuaire par le biais d’une demande de package d’accès en cours d’approbation. Cela peut se produire si l’utilisateur abandonne toutes les attributions de package d’accès, ou si l’attribution de son dernier package d’accès arrive à expiration. Par défaut, quand un utilisateur externe n’a plus d’attributions de package d’accès, il ne peut pas se connecter à votre annuaire. Au bout de 30 jours, son compte d’utilisateur invité est supprimé de votre annuaire.

1. Connectez-vous au Centre d’administration Entra en tant qu’administrateur. Un compte avec l’administrateur d’utilisateurs est requis pour effectuer ces tâches.
2. Ouvrez **Gouvernance des ID**.
3. Dans le menu de navigation de gauche, sous **Gestion des droits d’utilisation**, sélectionnez **Paramètres**.
4. Dans le menu du haut, sélectionnez **Modifier**.
5. Dans la section **Gérer le cycle de vie des utilisateurs externes**, sélectionnez les différents paramètres pour les utilisateurs externes. Si, lorsqu’un utilisateur externe perd sa dernière attribution aux packages d’accès, vous souhaitez l’empêcher de se connecter à cet annuaire, définissez **Empêcher l'utilisateur externe de se connecter à cet annuaire** sur **Oui**. Si un utilisateur est bloqué de se connecter à l’annuaire, l’utilisateur ne peut pas demander à nouveau le package d’accès ou demander un autre accès dans ce répertoire. Ne configurez pas leur blocage de la connexion s’ils devront ultérieurement demander l’accès à d’autres packages d’accès.
6. Si, lorsqu’un utilisateur externe perd sa dernière attribution aux packages d’accès, vous souhaitez supprimer son compte d’utilisateur invité dans ce répertoire, définissez **Supprimer l’utilisateur externe**sur **Oui**.  Remarque La gestion des droits d'utilisation supprime uniquement les comptes qui ont été invités par l’intermédiaire de la gestion des droits d'utilisation. Un utilisateur est également bloqué pour se connecter. L’utilisateur est supprimé de ce répertoire même si cet utilisateur a été ajouté aux ressources de ce répertoire qui n’ont pas accès aux affectations de package. Si l’invité était présent dans ce répertoire avant de recevoir des attributions de package d’accès, il sera conservé. Toutefois, si l’invité a été invité par le biais d’une attribution de package d’accès, il sera toujours supprimé.
7. Si vous souhaitez supprimer le compte d’utilisateur invité du répertoire, vous pouvez définir le nombre de jours avant sa suppression. Pour supprimer le compte d’utilisateur invité dès qu’il perd la dernière attribution à un package d’accès, définissez **Nombre de jours avant la suppression de l’utilisateur externe de cet annuaire** sur **0**.
8. Si vous avez apporté des modifications, sélectionnez **Enregistrer**.


## Configurer et gérer des organisations connectées

Avec la gestion des droits d’utilisation Entra, vous pouvez collaborer avec des personnes extérieures à votre organisation. Si vous collaborez fréquemment avec des utilisateurs dans un répertoire ou domaine externe, vous pouvez les ajouter en tant qu'organisation connectée. Cet article explique comment ajouter une organisation connectée afin de permettre aux utilisateurs extérieurs à votre organisation de demander des ressources dans votre annuaire.

### Qu’est-ce qu’une organisation connectée ?

Une organisation connectée est une autre organisation avec laquelle vous avez une relation. Pour que les utilisateurs de cette organisation puissent accéder à vos ressources, telles que vos sites SharePoint Online ou vos applications, vous avez besoin d’une représentation de ces utilisateurs dans ce répertoire. Dans la plupart des cas, les utilisateurs de cette organisation ne figurent pas déjà dans votre répertoire Entra : la gestion des droits vous permet de les y importer si nécessaire.

La gestion des droits d’utilisation vous permet de spécifier les utilisateurs qui forment une organisation connectée de trois façons. Il peut s’agir :

- les utilisateurs dans un autre répertoire Entra (depuis n'importe quel cloud Microsoft),
- les utilisateurs d'un autre répertoire non Entra configuré pour la fédération directe, ou
- les utilisateurs d'un autre répertoire non Entra, dont les adresses e-mail ont toutes le même nom de domaine en commun.

### Ajouter une organisation connectée

Pour ajouter un répertoire ou un domaine externe en tant qu'organisation connectée, suivez les instructions de cette section. **Rôle requis :** Administrateur de gouvernance des identités ou administrateur d’utilisateurs

1. Dans le **Centre d’administration Entra**, sélectionnez **Gouvernance des ID**, puis sélectionnez **Gestion des droits d’utilisation**.
2. Dans le volet gauche, sélectionnez **Organisations connectées**, puis **sélectionnez + Ajouter une organisation connectée**.
3. Sélectionnez l’onglet **Informations de base** , puis entrez un nom complet et une description pour l’organisation.
  - L’état est automatiquement défini sur Configuré lorsque vous créez une organisation connectée. Pour plus d’informations sur les propriétés d’état, consultez Propriétés d’état des organisations connectées.

4. Sélectionnez l’onglet **Répertoire + domaine** , puis **sélectionnez Ajouter un répertoire + domaine**.
  - Le volet Sélectionner des annuaires et des domaines s’ouvre.

5. Dans la zone de recherche, entrez un nom de domaine pour rechercher le répertoire ou le domaine Entra. Veillez à entrer le nom de domaine complet.
  - Confirmez que le nom de l’organisation et le type d’authentification sont corrects.

6. Sélectionnez **Ajouter** pour ajouter le répertoire ou le domaine Entra. Vous ne pouvez ajouter qu'un seul répertoire ou domaine par organisation connectée.
7. Une fois le répertoire ou le domaine ajouté, cliquez sur Sélectionner.
  - L’organisation apparaît dans la liste.

8. Sélectionnez l’onglet Sponsors, puis ajoutez des **sponsors** facultatifs pour cette organisation connectée.
  - Les commanditaires sont des utilisateurs internes ou externes déjà présents dans votre répertoire. Les commanditaires constituent le point de contact pour la relation avec cette organisation connectée.
  - Lorsque vous sélectionnez Ajouter/Supprimer, un volet s’ouvre dans lequel vous pouvez choisir des commanditaires internes ou externes. Le volet affiche une liste non filtrée d’utilisateurs et de groupes dans votre annuaire.

9. Sélectionnez l’onglet **Vérifier + créer** , passez en revue les paramètres de votre organisation, puis sélectionnez **Créer**.


## Passer en revue les droits par utilisateur

Dans la gestion des droits d'utilisation Entra, vous pouvez voir qui a été affecté aux packages d’accès, ainsi que leur stratégie et leur état. Si un package d’accès a une stratégie appropriée, vous pouvez également affecter directement l’utilisateur à un package d’accès. Cet article explique comment afficher, ajouter et supprimer des affectations pour des packages d’accès.

### Gouvernance

Comme l’exigent les règles **Confiance Zéro**, vous passez régulièrement en revue vos packages de droits d’utilisation. Le système intègre des outils pour prendre en charge cette révision.

### Afficher les utilisateurs qui ont une affectation

**Rôle requis**

- Administrateur Identity Governance
- Administrateur d’utilisateurs
- Propriétaire de catalogue
- Gestionnaire de package d’accès
- Gestionnaire d'attribution de package d'accès

Procédez comme suit pour passer en revue les affectations :

1. Dans le Centre d'administration Entra, sélectionnez **Gouvernance des ID**, puis **gestion des droits d'utilisation**.
2. Dans le menu de gauche, sélectionnez **Packages d’accès**, puis ouvrez le package d'accès.
3. Sélectionnez Affectations pour afficher une liste des affectations actives.
4. Sélectionnez une affectation spécifique pour voir plus de détails.
5. Pour afficher une liste des affectations dont les rôles de ressources n’étaient pas correctement provisionnés, sélectionnez le filtre d’état puis **Livraison en cours**.
  - Vous pouvez voir des détails supplémentaires sur les erreurs de remise en recherchant la requête correspondante de l'utilisateur sur la page Requêtes.

6. Pour voir les affectations expirées, sélectionnez le filtre d’état puis **Expiré**.
7. Pour télécharger un **fichier CSV** contenant la liste filtrée, sélectionnez **Télécharger**.

### Passer en revue les affectations avec PowerShell

Vous pouvez effectuer une requête dans PowerShell pour obtenir la liste des affectations par utilisateur. Cela peut vous aider à écrire des scripts et à automatiser les tâches de gestion.

PowerShell

```
Connect-MgGraph -Scopes "EntitlementManagement.Read.All"
Select-MgProfile -Name "beta"
$accesspackage = Get-MgEntitlementManagementAccessPackage -DisplayNameEq "Marketing Campaign"
$assignments = Get-MgEntitlementManagementAccessPackageAssignment -AccessPackageId $accesspackage.Id -ExpandProperty target -All -ErrorAction Stop
$assignments | ft Id,AssignmentState,TargetId,{$_.Target.DisplayName}
```

### Supprimer une affectation

Si vous identifiez une affectation obsolète, prenez les mesures qui s’imposent. Vous pouvez supprimer une affectation qu’un utilisateur ou un administrateur ont demandée précédemment.

1. Dans le Centre d'administration Entra, sélectionnez **Gouvernance des ID**, puis **gestion des droits d'utilisation**.
2. Dans le menu de gauche, sélectionnez **Packages d’accès**, puis ouvrez le package d'accès.
3. Dans le menu de gauche, sélectionnez **Affectations**.
4. Cochez la case en regard de l’utilisateur dont vous souhaitez supprimer l’affectation du package d’accès.
5. Sélectionnez le bouton **Supprimer** en haut du volet gauche.


## Évaluation du module

Choisissez la meilleure réponse à chacune des questions ci-dessous.

### Contrôle des connaissances


## Récapitulatif et ressources

Maintenant que vous avez passé en revue ce module, vous pouvez :

- Définir des catalogues.
- Définir des packages d’accès.
- Planifier, implémenter et gérer des droits d’utilisation.
- Implémenter et gérer les conditions d’utilisation.
- Gérez le cycle de vie des utilisateurs externes dans les paramètres de Gouvernance des ID Entra.
- Configurez et gérez l’organisation connectée.
- Passez en revue les droits d’utilisation par utilisateur.

Dans ce module, vous avez appris à gérer les autorisations et l’accès pour vos utilisateurs internes et externes afin de protéger la sécurité des informations de votre entreprise. Grâce aux exercices pratiques, vous avez créé un compte Azure, créé et géré un catalogue de ressources, ajouté des conditions d’utilisation et des rapports d’acceptation, et géré le cycle de vie des utilisateurs externes. Grâce à cette nouvelle connaissance, vous pouvez désormais implémenter un accès privilégié au sein de votre organisation.

### Ressources

Utilisez ces ressources pour approfondir vos connaissances.

- FAQ [https://learn.microsoft.com/azure/active-directory/conditional-access/terms-of-use](https://learn.microsoft.com/fr-fr/azure/active-directory/conditional-access/terms-of-use)
- [Qu’est-ce que la gestion des droits d’utilisation d’Entra ?](https://learn.microsoft.com/fr-fr/azure/active-directory/governance/entitlement-management-overview)
- [Scénarios courants dans la gestion des droits d’utilisation d’Entra](https://learn.microsoft.com/fr-fr/azure/active-directory/governance/entitlement-management-scenarios)
- [Examen des affectations dans la gestion des droits d’utilisation Entra](https://learn.microsoft.com/fr-fr/azure/active-directory/governance/entitlement-management-access-package-assignments)
- [Ajouter une organisation connectée dans la gestion des droits d’utilisation D’Entra](https://learn.microsoft.com/fr-fr/azure/active-directory/governance/entitlement-management-organization)


---

# Planifier, implémenter et gérer la révision d’accès

_https://learn.microsoft.com/fr-fr/training/modules/plan-implement-manage-access-review/_


## Présentation

À mesure que votre organisation se développe, la gestion de qui a accès à quoi devient difficile. Les employés modifient les rôles, les invités accumulent les autorisations dont ils n’ont plus besoin et les affectations privilégiées persistent longtemps après la fin d’un projet. Sans processus systématique d’examen et de recertification de l’accès, votre environnement accumule les risques et les résultats d’audit suivent rapidement.

Les révisions d’accès Entra vous donnent un moyen structuré de gérer la dérive des accès des utilisateurs. Ils vous permettent de planifier des révisions périodiques des appartenances aux groupes, des attributions d’applications et des attributions de rôles privilégiées. Le résultat est ensuite automatisé : l’accès refusé par les réviseurs est supprimé, sans suivi manuel.

Dans ce module, vous planifiez et implémentez des révisions d’accès dans Entra ID Governance. Vous découvrez pourquoi les révisions d’accès concernent la posture de sécurité de votre organisation. Vous apprenez à les créer et à les configurer pour différents types de ressources, et comment surveiller et automatiser leurs résultats. Vous explorez également l’Agent de révision d’accès, qui utilise l’IA pour guider les réviseurs dans le processus directement dans Microsoft Teams.

### Objectifs d’apprentissage

À la fin de ce module, vous pouvez :

- Planifier des révisions d’accès.
- Créer des révisions d’accès pour les groupes et les applications.
- Surveiller les résultats de la révision d’accès.
- Créez et gérez des programmes de révision d’accès.
- Automatiser les tâches de gestion de la révision d’accès.
- Configurer des révisions d’accès récurrentes.
- Décrivez l’Agent de révision d’accès et comment il aide les réviseurs à terminer les révisions d’accès.

### Conditions préalables

- Connaissance de la création et de la gestion des accès des utilisateurs Entra

Note

Certaines fonctionnalités des révisions d’accès nécessitent un abonnement **Entra ID Governance** ou **Entra Suite** . Certaines fonctionnalités fonctionnent avec un abonnement Entra ID P2. Confirmez votre licence avant le déploiement.


## Planifier des révisions d’accès

### Qu’est-ce qu’une révision d’accès ?

Une **révision d’accès** est, comme son nom l’indique, une révision planifiée des besoins d’accès, des droits et de l’historique de l’accès utilisateur. Les révisions d’accès permettent de s’assurer que les bonnes personnes ont le droit d’accéder aux ressources appropriées. Elles permettent de limiter les risques d’accès en protégeant, en surveillant et en auditant l’accès aux ressources critiques tout en garantissant la productivité des employés et des partenaires. Les révisions d’accès sont une fonctionnalité de gouvernance des ID Entra et nécessitent un abonnement **Entra ID Governance** ou **Entra Suite** . Certaines fonctionnalités fonctionnent avec un abonnement Entra ID P2.

Tenez compte des besoins de votre organisation pour déterminer la stratégie de déploiement des révisions d’accès dans votre environnement.

### Impliquer les parties prenantes appropriées

Lorsque des projets technologiques échouent, cela est généralement dû à des attentes qui ne correspondent pas, aux résultats et aux responsabilités réels. Pour éviter un tel cas de figure, prenez soin de faire appel aux bonnes parties prenantes et à clarifier les rôles du projet. Pour les révisions d’accès, incluez des représentants des équipes suivantes au sein de votre organisation :

- **L’administration informatique** gère votre infrastructure informatique et administre vos investissements cloud et vos applications SaaS (Software as a service). Cette équipe examine l’accès privilégié à l’infrastructure et aux applications, planifie les révisions d’accès sur les groupes figurant sur la liste d'exceptions et veille à ce que l’accès programmatique via les entités de service soit régi.
- **Les équipes de sécurité** garantissent que le plan répond aux exigences de sécurité de l’organisation et applique la confiance zéro. Cette équipe réduit les risques, applique l’accès avec des privilèges minimum et utilise des outils pour maintenir une vue centralisée de qui a accès à quoi.
- Les **équipes de développement** créent et entretiennent des applications pour votre organisation. Cette équipe contrôle qui peut accéder aux composants dans les ressources SaaS, PaaS et IaaS et gère les groupes utilisés pour le développement d’applications internes.
- **Les unités commerciales** gèrent des projets et possèdent des applications. Cette équipe examine et approuve ou refuse l’accès aux groupes et applications pour les utilisateurs internes et externes.
- **La gouvernance d’entreprise** garantit que l’organisation suit la stratégie interne et respecte les réglementations.  Note Pour les révisions nécessitant des évaluations manuelles, veillez à planifier les réviseurs et cycles de révision adéquats qui répondent à vos besoins en matière de stratégie et de conformité. Si les cycles de révision sont trop fréquents ou qu’il y a trop peu de réviseurs, la qualité est perdue et trop ou trop peu de personnes y ont accès.

### Qu’est-ce qu’Entra ID Governance ?

Entra ID Governance vous permet d’équilibrer le besoin de votre organisation pour la sécurité et la productivité des employés avec les processus et la visibilité appropriés. Il fournit des fonctionnalités qui garantissent que les bonnes personnes ont le droit d’accéder aux ressources appropriées. Elles vous aident aussi à atténuer les risques d’accès en protégeant, en surveillant et en auditant l’accès aux ressources critiques, tout en garantissant la productivité des employés et des partenaires commerciaux.

Identity Governance offre aux organisations la possibilité d’effectuer des tâches complètes vis-à-vis des employés, des partenaires et des fournisseurs, pour différents services et applications en local comme dans le cloud. Plus précisément, il est destiné à aider les organisations à répondre à ces quatre questions clés :

- Quels utilisateurs doivent pouvoir accéder à quelles ressources ?
- Que font les utilisateurs de cet accès ?
- Des contrôles organisationnels efficaces sont-ils disponibles pour gérer l’accès ?
- Des auditeurs peuvent-ils vérifier que les contrôles fonctionnent ?

### Prévoir un pilote

Nous encourageons les clients à tester initialement les révisions d’accès avec un petit groupe et à cibler des ressources non critiques. Cette phase pilote vous aide à ajuster les processus et les communications en fonction des besoins, et à renforcer la capacité des utilisateurs et des réviseurs à répondre aux exigences de conformité et de sécurité.

Dans votre pilote, nous vous recommandons d’effectuer les tâches suivantes :

- Commencez par les révisions dont les résultats ne sont pas appliqués automatiquement, et vous pourrez en contrôler les implications.
- Assurez-vous que tous les utilisateurs disposent d’adresses e-mail valides figurant dans Entra ID et qu’ils reçoivent des communications par e-mail pour prendre les mesures appropriées.
- Documentez tout accès supprimé dans le cadre du pilote au cas où vous devriez le restaurer rapidement.
- Analysez les journaux d’audit pour vous assurer que tous les événements sont correctement audités.

#### Quels types de ressources peuvent être révisés ?

Une fois que vous avez intégré les ressources de votre organisation à Entra ID (telles que les utilisateurs, les applications et les groupes), elles peuvent être gérées et révisées.

Les cibles classiques à réviser sont les suivantes :

- Accès utilisateur aux applications intégrées à l’ID Entra pour l’authentification unique (par exemple SaaS, métier).
- Appartenances aux groupes (synchronisées avec Entra ID ou créées dans Entra ID / Microsoft 365, notamment Microsoft Teams).
- Package d’accès qui regroupe les ressources (groupes, applications et sites) en un seul package pour gérer l’accès.
- Rôles Entra et rôles de ressources Azure tels que définis dans Privileged Identity Management (PIM).
- Ressources de données personnalisées (préversion) : droits d’accès gérés via des types de ressources externes connectés à Entra ID Governance.

#### Qui crée et gère les révisions d’accès ?

Le rôle administratif requis pour créer, gérer ou lire une révision d’accès dépend du type de ressource examiné.

| **Type de ressource** | **Créer et gérer les révisions d’accès (créateurs)** | **Lecture des résultats de la révision d’accès** |
|---|---|---|
| Groupe ou application | Administrateur général | Administrateur général |
|   | Administrateur d'utilisateurs | Lecteur mondial |
|   | Administrateur Identity Governance | Administrateur d’utilisateurs |
|   | Administrateur de rôle privilégié (n’effectue la révision que pour les groupes Entra assignables) | Administrateur de la gouvernance des identités |
|   | Propriétaire de groupe | Administrateur de rôle privilégié |
|   |   | Lecteur de sécurité |
|   |   | Propriétaire de groupe |
| Rôle Entra | Administrateur général |   |
|   | Administrateur de rôle privilégié | Administrateur général |
|   |   | Lecteur mondial |
|   |   | Administrateur d’utilisateurs |
|   |   | Administrateur de rôle privilégié |
|   |   | Lecteur de sécurité |
| Rôles de ressources Azure | Administrateur général | Administrateur général |
|   | Administrateur de l'accès utilisateur | Administrateur de l'accès utilisateur |
|   | Propriétaire de la ressource | Propriétaire de la ressource |
|   |   | Lecteur (pour la ressource) |
| Package d’accès | Administrateur général | Administrateur général |
|   | Administrateur d'utilisateurs |   |
|   | Administrateur de la Gouvernance de l'Identité | Lecteur mondial |
|   |   | Administrateur d’utilisateurs |
|   |   | Administrateur Identity Governance |
|   |   | Lecteur de sécurité |

#### Qui passe en revue l’accès à la ressource ?

Le créateur de la révision d’accès détermine, lors de sa création, qui en assurera l’exécution. Ce paramètre ne peut pas être modifié une fois la révision démarrée. Les réviseurs sont représentés par trois personnages :

- Les propriétaires de la ressource, qui sont les propriétaires d’entreprise de la ressource.
- Un ensemble de délégués sélectionnés individuellement, tels que choisis par l’administrateur des révisions d’accès.
- Les utilisateurs finaux qui attestent eux-mêmes leurs besoins en matière d’accès continu.

Lorsque l’administrateur crée une révision d’accès, les administrateurs peuvent choisir un ou plusieurs réviseurs. Tous les réviseurs peuvent démarrer et effectuer une révision, en choisissant d’octroyer aux utilisateurs un accès continu à une ressource ou en les supprimant.

#### Composants d’une révision d’accès

Avant d’implémenter vos révisions d’accès, vous devez planifier les types de révisions pertinents pour votre organisation. Pour ce faire, vous devrez prendre des décisions commerciales sur ce que vous souhaitez examiner et les actions à entreprendre en fonction de ces révisions.

Pour créer une stratégie de révision d’accès, vous devez disposer des informations suivantes :

- Quelles ressources doivent être consultées ?
- Quel est l’utilisateur dont l’accès est examiné ?
- Quelle est la fréquence de la révision ?
- Qui effectue la révision ?
- Comment ces personnes seront-elles informées de la révision ?
- Quels sont les délais à respecter pour la révision ?
- Quelles actions automatiques doivent être appliquées en fonction de la révision ?
- Que se passe-t-il si le réviseur ne répond pas à temps ?
- Quelles actions manuelles sont exécutées en fonction de la révision ?
- Quelles communications doivent être envoyées en fonction des actions effectuées ?

**Exemple de plan de révision d’accès**

| **Composant** | **Valeur** |
|---|---|
| Ressources à réviser | Accès à Microsoft Dynamics |
| Fréquence de révision | Mensuel |
| Qui effectue la révision | Responsables de programme du groupe d’entreprise Dynamics |
| Notification | Envoyez un e-mail 24 heures avant l'examen à l'adresse e-mail alias Dynamics-Pms |
|   | Assurer l'engagement et l'achèvement des évaluateurs en incluant un message personnalisé aux évaluateurs. |
| Durée | 48 heures à partir de la notification |
| Actions automatiques | Supprimer l'accès de tout compte n'ayant pas de connexion interactive dans les 90 jours en retirant l'utilisateur du groupe de sécurité dynamics-access. |
|   | *Exécuter des actions si la révision n’est pas effectuée dans les temps* |
| Actions manuelles | Si vous le souhaitez, les réviseurs procèdent à l’approbation des suppressions avant l’action automatisée |
| Communications | Envoyer un e-mail aux utilisateurs internes (membres) qui ont été supprimés, expliquant qu'ils ont été retirés et comment récupérer l'accès. |

### Planifier des révisions d’accès pour les packages d’accès

Les packages d’accès peuvent considérablement simplifier votre stratégie de gouvernance et de révision d’accès. Un package d’accès regroupe toutes les ressources avec l’accès dont un utilisateur a besoin pour travailler sur un projet ou accomplir sa tâche. Par exemple, vous pouvez créer un package d’accès qui comprend toutes les applications dont les développeurs de votre organisation ont besoin, ou toutes les applications auxquelles les utilisateurs externes doivent avoir accès. Un administrateur ou un gestionnaire délégué de package d’accès regroupe ensuite les ressources (groupes ou applications) et les rôles dont les utilisateurs ont besoin pour ces ressources.

Lors de la création d’un package d’accès, vous pouvez créer une ou plusieurs stratégies d’accès. Elles définissent les conditions auxquelles les utilisateurs peuvent demander un package d’accès, le processus d’approbation et la fréquence à laquelle une personne doit redemander l’accès. Les révisions d’accès sont configurées lors de la création ou de la modification d’une stratégie de package d’accès.

### Planifier des révisions d’accès pour les groupes

Outre les packages d’accès, la révision de l’appartenance à un groupe est la méthode la plus efficace pour régir l’accès. Nous vous recommandons d’attribuer l’accès aux ressources via des groupes de sécurité ou des groupes Microsoft 365, et d’ajouter des utilisateurs à ces groupes pour qu’ils en obtiennent l’accès.

Un groupe peut se voir accorder l’accès à toutes les ressources appropriées. Vous pouvez attribuer au groupe un accès à des ressources individuelles ou à un package d’accès qui regroupe des applications et d’autres ressources. Grâce à cette méthode, vous pouvez réviser l’accès au groupe plutôt que l’accès d’un individu à chaque application.

Appartenance au groupe examinée par :

- Administrateurs
- Propriétaires de groupe
- La capacité de révision est déléguée à certains utilisateurs lors de la création de la révision.
- Membres du groupe, en attestant d’eux-mêmes

#### Propriété de groupe

Nous recommandons aux propriétaires de groupes de réviser leur appartenance, car ils sont les mieux placés pour savoir qui a besoin d’un accès. La propriété des groupes diffère selon le type de groupe.

- Les groupes créés dans Microsoft 365 et Entra ID ont un ou plusieurs propriétaires bien définis. Dans la plupart des cas, ces propriétaires font de parfaits réviseurs pour leurs propres groupes, car ils savent qui doit y avoir accès. Par exemple, Microsoft Teams utilise les groupes Microsoft 365 comme modèle d’autorisation sous-jacent pour accorder aux utilisateurs l’accès aux ressources qui se trouvent dans SharePoint, Exchange, OneNote ou d’autres services Microsoft 365. Le créateur de l’équipe devient automatiquement propriétaire et doit être responsable d’attester l’appartenance de ce groupe.
- Les groupes créés manuellement dans le portail du centre d’administration Entra ou par le biais d’un script via Microsoft Graph peuvent ne pas nécessairement avoir des propriétaires définis. Nous vous recommandons de les définir via le portail d’administration dans la section « Propriétaires » du groupe ou via Graph.
- Les groupes qui sont synchronisés à partir du service Active Directory local ne peuvent pas avoir de propriétaire dans Entra ID. Lors de la création d’une révision d’accès, vous devez sélectionner les personnes qui sont les plus aptes à décider de leur appartenance.  Note Nous vous recommandons de définir des stratégies d’entreprise qui encadrent la création des groupes. La propriété et la responsabilité du groupe sont ainsi claires pour une révision régulière de ses membres.

#### Examiner l’appartenance des groupes d’exclusion dans les politiques d’accès conditionnel

Il peut arriver que les stratégies d’accès conditionnel conçues pour sécuriser votre réseau ne s’appliquent pas à tous les utilisateurs. Par exemple, une stratégie d’accès conditionnel qui autorise uniquement les utilisateurs à se connecter à partir du réseau de l’entreprise ne peut pas s’appliquer à l’équipe de vente, qui voyage beaucoup. Dans ce cas, les membres de l’équipe de vente seraient placés dans un groupe, et ce groupe serait exclu de la stratégie d’accès conditionnel.

#### Réviser les appartenances aux groupes des utilisateurs externes

Pour minimiser le travail manuel et les erreurs potentielles associées, envisagez d’utiliser des groupes dynamiques pour attribuer l’appartenance à un groupe en fonction des attributs d’un utilisateur. Vous souhaitez créer un ou plusieurs groupes dynamiques pour les utilisateurs externes. Le commanditaire interne peut agir en tant qu'examinateur de l’appartenance au groupe.

#### Réviser l’accès aux groupes locaux

Les révisions d'accès ne peuvent pas modifier l'appartenance des groupes que vous synchronisez à partir de votre site local avec Entra Connect. Avec les groupes synchronisés, la source d’autorité est locale. Vous pouvez toujours utiliser les révisions d’accès pour planifier et gérer régulièrement des révisions de groupes locaux. Les réviseurs prennent des mesures dans le groupe local. Cette stratégie permet de garder les révisions d’accès comme outil pour toutes les révisions. Vous pouvez utiliser les résultats d’une révision d’accès sur les groupes locaux et les traiter plus avant. Les données sont disponibles dans un fichier CSV ou dans Microsoft Graph.

### Planifier des révisions d’accès pour les applications

Lorsque vous révisez l’accès à une application, vous révisez l’accès des employés et des identités externes aux informations et aux données contenues dans l’application. Choisissez de réviser une application lorsque vous avez besoin de savoir qui a accès à une application spécifique, plutôt qu’à un package d’accès ou à un groupe.

Nous vous recommandons de planifier des révisions d’applications dans les scénarios suivants :

- Les utilisateurs bénéficient d’un accès direct à l’application (en dehors d’un groupe ou d’un package d’accès).
- L’application expose des informations critiques ou sensibles.
- L’application a des exigences de conformité spécifiques dont vous devez attester.
- Vous soupçonnez un accès inapproprié.

#### Réviseurs pour une application

Les révisions d’accès peuvent porter sur les membres d’un groupe ou sur les utilisateurs qui ont été assignés à une application. Les applications dans Entra ID n'ont pas nécessairement de propriétaire. Par conséquent, l'option de sélection du propriétaire de l'application en tant que réviseur n'est pas possible. Vous pouvez en outre étendre la portée d’une révision pour n’examiner que les utilisateurs invités affectés à l’application, plutôt que d’examiner tous les accès.

### Planification de la révision des rôles d’Entra ID et des ressources Azure

Privileged Identity Management (PIM) simplifie la gestion (par les entreprises) des accès privilégiés aux ressources dans Entra ID. Cela permet de conserver la liste des rôles privilégiés, à la fois dans l’ID Entra et les ressources Azure, plus petits et augmente la sécurité globale du répertoire.

Les révisions d’accès permettent aux réviseurs d’attester si les utilisateurs doivent toujours appartenir à un rôle. Tout comme les révisions d’accès pour les packages d’accès, les révisions des rôles Entra et des ressources Azure sont intégrées à l’expérience de l’utilisateur administrateur PIM. Nous vous recommandons de réviser régulièrement les attributions de rôle suivantes :

- Administrateur général
- Administrateur d'utilisateurs
- Administrateur d’authentification privilégié
- Administrateur de l’accès conditionnel
- Administrateur de la sécurité
- Tous les rôles Administration de service Microsoft 365 et Dynamics

### Déployer des révisions d’accès

Après avoir préparé une stratégie et un plan de révision de l’accès aux ressources intégrées à l’ID Entra, déployez et gérez les révisions à l’aide des ressources répertoriées.

#### Réviser des packages d’accès

Pour réduire le risque d’un accès obsolète, les administrateurs peuvent activer les révisions périodiques des utilisateurs qui ont des affectations actives à un package d’accès. Vous pouvez créer des révisions d’accès, effectuer des révisions d’accès pour d’autres personnes affectées à un package d’accès ou effectuer une auto-révision du package d’accès affecté.

#### Réviser des groupes et des applications

Les besoins d'accès des employés et des invités aux groupes et applications évoluent probablement au fil du temps. Afin de réduire les risques associés aux attributions d’accès obsolètes, les administrateurs peuvent créer des révisions d’accès pour les membres de groupes ou pour l’accès aux applications.

Vous pouvez créer des révisions d’accès pour les membres d’un groupe ou un accès aux applications, et effectuer ces révisions pour les membres d’un groupe ou les utilisateurs ayant accès à une application. Vous pouvez aussi autoriser les membres à réviser leur propre accès à un groupe ou à une application, afficher les révisions d’accès et prendre des mesures pour les groupes locaux avec PowerShell.

#### Réviser les rôles d’Entra

Pour réduire les risques associés aux attributions de rôles obsolètes, vous devez régulièrement réviser l’accès aux rôles privilégiés Entra.

#### Examiner les rôles de ressource Azure

Pour réduire les risques associés aux attributions de rôles obsolètes, vous devez régulièrement examiner l'accès aux rôles privilégiés des ressources Azure.

### Utiliser l’API des révisions d’accès

Les méthodes de révision d’accès dans l’API Microsoft Graph sont disponibles à la fois pour les applications et les utilisateurs. Lors de l’exécution de scripts dans le contexte de l’application, le compte qui exécute l’API (le principal du service) doit obtenir l’autorisation « AccessReview.Read.All » pour interroger les informations de révision d’accès.

Les tâches les plus courantes à automatiser à l’aide de l’API Graph pour les révisions d’accès sont les suivantes :

- Créer et démarrer une révision d’accès.
- Terminer manuellement une révision d’accès avant sa fin planifiée.
- Répertorier toutes les révisions d’accès en cours d’exécution et leur état.
- Consulter l’historique d’une série de révisions et les décisions et actions prises à chaque révision
- Collecter les décisions d’une révision d’accès.
- Collecter les décisions des révisions terminées où le réviseur a pris une décision différente de celle recommandée par le système  Note Pour créer de nouvelles requêtes de l’API Graph destinées à l’automatisation, nous vous recommandons Graph Explorer. Vous pouvez générer et explorer vos requêtes Graph avant de les placer dans des scripts et du code. Cela peut vous aider à itérer rapidement votre requête afin d’obtenir exactement les résultats que vous recherchez, sans changer le code de votre script.

### Surveiller les révisions d’accès

Les activités de révisions d'accès sont enregistrées et disponibles dans les journaux d'audit d’Entra. Vous pouvez filtrer les données d’audit par catégorie, type d’activité et plage de dates. Voici un exemple de requête :

| **Catégorie** | **Stratégie** |
|---|---|
| Type d’activité | Créer une révision d’accès |
|   | Mettre à jour une révision d’accès |
|   | Révision d’accès terminée |
|   | Supprimer une révision d’accès |
|   | Approuver la décision |
|   | Refuser la décision |
|   | Réinitialiser la décision |
|   | Appliquer la décision |
| Plage de dates | Sept jours |

Pour les requêtes plus avancées et l’analyse des révisions d’accès, ainsi que pour le suivi des modifications et l’achèvement des révisions, nous vous recommandons d’exporter vos journaux d’audit Entra vers Azure Log Analytics ou Azure Event Hubs. Lorsque les journaux sont stockés dans Azure Log Analytics, vous pouvez utiliser le puissant langage d’analytique et créer vos propres tableaux de bord.

### Planifier les communications

La communication est essentielle à la réussite de tout nouveau processus métier. Communiquez de manière proactive aux utilisateurs comment et quand leur expérience change et comment obtenir du support s’ils rencontrent des problèmes.

**Communiquer les évolutions de responsabilité** : les révisions d’accès permettent de transférer la responsabilité de la révision et de la décision relative au maintien de l’accès aux propriétaires métier. Le découplage des décisions d’accès de l’équipe informatique permet de prendre des décisions plus précises en matière d’accès. Il s’agit d’un changement culturel dans l’obligation de rendre des comptes et la responsabilité du propriétaire des ressources. Communiquez cette modification de manière proactive et assurez-vous que les propriétaires des ressources sont formés et en mesure d’utiliser les informations pour prendre de bonnes décisions.

Il est clair que le service informatique souhaite rester en contrôle pour toutes les décisions d’accès liées à l’infrastructure et les attributions de rôles privilégiées.

**Personnaliser la communication par e-mail** : lorsque vous planifiez une révision, vous nommez les utilisateurs qui effectuent cette révision. Ces réviseurs reçoivent ensuite une notification par e-mail des nouvelles révisions qui leur sont attribuées et des rappels avant l’expiration d’une révision affectée.

Les administrateurs peuvent choisir d’envoyer cette notification soit à mi-chemin avant l’expiration de la révision, soit un jour avant son expiration.

L’e-mail envoyé aux réviseurs peut être personnalisé de façon à inclure un message bref personnalisé qui les encourage à agir sur la révision. Nous vous recommandons d’utiliser l’autre texte pour :

- Incluez un message personnel aux réviseurs, afin qu’ils comprennent qu’ils sont envoyés par votre service de conformité ou informatique.
- Incluez un lien hypertexte ou une référence à des informations internes sur les attentes de la révision et d’autres documents de référence ou de formation.
- Inclure un lien vers des instructions sur la façon d’effectuer une auto-révision de l’accès.

Lorsque vous sélectionnez Démarrer la révision, les réviseurs sont dirigés vers le portail MyAccess pour les révisions d’accès aux groupes et aux applications. Le portail leur donne une vue d’ensemble de tous les utilisateurs qui ont accès à la ressource révisée, ainsi que des recommandations système basées sur les dernières informations de connexion et d’accès.

### De combien de licences avez-vous besoin ?

Une licence Entra ID Premium P2 est requise pour chaque membre ou utilisateur invité qui :

- Est affecté en tant que réviseur
- Effectue une auto-révision
- Un propriétaire de groupe réalise-t-il une révision d’accès
- Un propriétaire d'application est en train de réaliser une révision d'accès

Les licences ne sont pas requises pour les utilisateurs disposant des rôles Administrateur général ou Administrateur utilisateur qui configurent des révisions d’accès, configurent des paramètres ou appliquent des décisions de révision.

Les licences Entra ID Premium P2 ne sont pas requises pour les administrateurs généraux ou les administrateurs d’utilisateurs qui configurent les révisions d’accès, configurent les paramètres ou appliquent les décisions des révisions.


## Créer des révisions d’accès pour les groupes et les applications

L’accès aux groupes et aux applications pour les employés et les invités change au fil du temps. Pour réduire le risque associé aux attributions d'accès obsolètes, les administrateurs peuvent utiliser Entra ID pour créer des révisions d'accès pour les membres du groupe ou l'accès aux applications. Si vous devez régulièrement passer en revue les accès, vous pouvez aussi créer des révisions d’accès périodiques.

### Prérequis

- Entra ID Governance ou Entra Suite (Entra ID Premium P2 fournit des fonctionnalités limitées)
- Administrateur de gouvernance des identités ou administrateur général

### Créer une ou plusieurs révisions d’accès

1. Connectez-vous au [centre d’administration d’Entra](https://entra.microsoft.com) en tant qu’**administrateur de la gouvernance des identités** au minimum.
2. Accédez à **Gouvernance d’ID**>**Revues d’accès**.
3. Sélectionnez **Nouvelle révision d’accès** pour créer une révision d’accès.
4. Dans l’écran du modèle Révisions d’accès, sélectionnez **Vérifier l’accès à un type de ressource**.
5. Dans la zone **Sélectionner les éléments à réviser** , sélectionnez la ressource que vous souhaitez examiner.
6. Si vous avez sélectionné **Teams + Groupes**, vous avez deux options :
  - **Tous les groupes Microsoft 365 avec des utilisateurs invités**. Sélectionnez cette option si vous souhaitez créer des révisions périodiques sur tous vos utilisateurs invités dans tous vos groupes Microsoft Teams et Microsoft 365 dans votre organisation. Vous pouvez choisir d’exclure certains groupes en sélectionnant **Sélectionner des groupes à exclure**.
  - **Sélectionner les équipes + groupes**. Sélectionnez cette option si vous souhaitez spécifier un ensemble fini d’équipes ou de groupes à examiner. Une liste de groupes à choisir apparaît sur le côté de l’écran.

7. Si vous avez sélectionné **Applications**, sélectionnez une ou plusieurs applications.
8. Sélectionnez une étendue pour la révision. Les options disponibles sont :  Si vous examinez l’appartenance au groupe, vous pouvez également cibler uniquement les utilisateurs inactifs. Dans la section **Étendue Utilisateurs** , sélectionnez **Utilisateurs inactifs (au niveau du locataire)** et spécifiez le nombre de jours inactifs (jusqu’à 730 jours).
  - **Utilisateurs invités uniquement**. Limite la révision aux utilisateurs invités Entra B2B dans votre annuaire.
  - **Tout le monde**. Limite la révision à tous les objets utilisateur associés à la ressource.  Note Si vous avez sélectionné **tous les groupes Microsoft 365 avec des utilisateurs invités**, votre seule option consiste à passer en revue **les utilisateurs invités uniquement**.

9. Sélectionnez **Suivant : Révisions**.
10. Dans la section **Sélectionner les réviseurs**, sélectionnez une ou plusieurs personnes pour effectuer les révisions d’accès. Vous pouvez choisir :
  - **Propriétaire(s) du groupe** (disponible uniquement lors de l’exécution d’une révision sur une équipe ou un groupe)
  - **Utilisateur(s) ou groupe(s) sélectionné(s)** .
  - **Les utilisateurs passent en revue leur propre accès**
  - **Gestionnaires d’utilisateurs**. Si vous choisissez **Gestionnaires d’utilisateurs** ou **propriétaires de groupe**, vous pouvez également spécifier un réviseur de secours. Les réviseurs de secours sont sollicités pour effectuer une révision lorsque l’utilisateur ne dispose pas de responsable dans l’annuaire ou lorsque le groupe n’a pas de propriétaire.

11. Dans la section **Spécifier la périodicité de la révision**, vous pouvez spécifier une fréquence **hebdomadaire, mensuelle, trimestrielle, semestrielle ou annuelle**. Vous spécifiez ensuite une **durée**, qui définit la durée pendant laquelle une révision est ouverte pour l’entrée des réviseurs. Par exemple, la durée maximale d’une révision mensuelle est de 27 jours, ce qui permet d’éviter le chevauchement des révisions. Vous pouvez raccourcir cette durée pour vous assurer que la contribution de vos réviseurs est prise en compte plus tôt. Ensuite, vous pouvez sélectionner une **date de début** et une **date de fin**.
12. Sélectionnez **Suivant : Paramètres**.
13. Dans **Paramètres une fois l’opération terminée**, vous pouvez spécifier ce qui se produit une fois la révision terminée.      Si vous voulez supprimer automatiquement l’accès pour les utilisateurs qui ont été refusés, définissez **Appliquer automatiquement les résultats à la ressource** sur **Activer**. Si vous voulez appliquer manuellement les résultats quand la révision est terminée, cliquez sur **Désactiver**. Utilisez la liste **Si les réviseurs ne répondent pas** pour spécifier ce qui se passe pour les utilisateurs qui ne sont pas vérifiés par le réviseur au cours de la révision. Ce paramètre ne modifie pas les utilisateurs qui ont été examinés manuellement. Si la décision finale des réviseurs est Refuser, l’accès de l’utilisateur est supprimé.  Utilisez l’action à appliquer aux utilisateurs **invités** refusés pour spécifier ce qui arrive aux utilisateurs invités s’ils sont refusés.
  - Aucune modification : laisser l’accès de l’utilisateur inchangé
  - Supprimer l’accès : supprimer l’accès de l’utilisateur
  - Approuver l’accès : approuver l’accès de l’utilisateur
  - Accepter les recommandations : accepter la recommandation du système sur le refus ou l’approbation de la prolongation de l’accès de l’utilisateur

  - **Supprimer l’appartenance de l’utilisateur à la ressource** supprime l’accès de l’utilisateur refusé au groupe ou à l’application en cours de révision. L'authentification du locataire continue de fonctionner.
  - **Bloquer la connexion de l’utilisateur pendant 30 jours, puis supprimer l’utilisateur du locataire** empêche les utilisateurs refusés de se connecter au locataire, quel que soit leur accès à d’autres ressources. En cas d’erreur ou si un administrateur décide de réactiver l’accès d’un utilisateur, il peut le faire dans les 30 jours suivant la désactivation de l’utilisateur. S’il n’y a aucune action effectuée sur les comptes d’utilisateur désactivés, ils sont supprimés du locataire.
  - L’action à appliquer sur les utilisateurs invités refusés n’est pas configurable sur les révisions dont la portée est plus large que celle des utilisateurs invités. Elle n’est pas non plus configurable pour les révisions de tous les groupes Microsoft 365 avec des utilisateurs invités. Lorsqu’elle n’est pas configurable, l’option par défaut de suppression de l’appartenance de l’utilisateur à la ressource est utilisée sur les utilisateurs refusés.

14. Dans la section **Activer les décideurs de révision** , choisissez si votre réviseur reçoit des recommandations pendant le processus de révision.
15. Dans la section **Paramètres avancés**, vous pouvez choisir les options suivantes :
  - Définissez **Justification obligatoire** sur **Activer** afin d’exiger que le réviseur indique un motif d’approbation.
  - Définissez **Notifications par e-mail** sur **Activer** pour qu’Entra ID envoie des notifications par e-mail aux réviseurs quand une révision d’accès commence et aux administrateurs quand une révision s’achève.
  - Définissez **Rappels** sur **Activer** pour qu’Entra ID envoie des rappels concernant les révisions d’accès en cours aux réviseurs qui n’ont pas terminé leur révision. Ces rappels sont à mi-chemin de la période de révision.
  - Le contenu de l’e-mail envoyé aux réviseurs est généré automatiquement en fonction des détails de révision, tels que le nom de révision, le nom de la ressource et la date d’échéance. Si vous devez communiquer des informations supplémentaires, telles que des instructions supplémentaires ou des informations de contact, spécifiez ces détails dans le **contenu supplémentaire de la section de messagerie du réviseur** . Les informations que vous entrez sont incluses dans les e-mails d’invitation et de rappel envoyés aux réviseurs affectés.
  - Sélectionnez **Access Review Agent (préversion)** pour permettre aux réviseurs de terminer la révision d’accès dans Microsoft Teams à l’aide du langage naturel, des insights et des recommandations. Cette option nécessite davantage de configuration. Pour plus d’informations, consultez l’unité de l’agent de révision d’accès.

16. Sélectionnez **Suivant : Vérifier + Créer**.
17. Nommez la révision d’accès. Si vous le souhaitez, vous pouvez fournir une description de cette révision. Le nom et la description sont montrés aux évaluateurs.
18. Vérifiez les informations, puis sélectionnez **Créer**.

### Démarrer la révision d’accès

Une fois que vous avez spécifié les paramètres d’une révision d’accès, sélectionnez **Démarrer**. La révision d’accès apparaît dans votre liste avec un indicateur de son état.

Par défaut, Entra ID envoie un e-mail aux réviseurs peu de temps après le début de la révision. Si vous choisissez de ne pas laisser Entra ID envoyer l'e-mail, assurez-vous d'informer les réviseurs qu'une révision d'accès les attend. Vous pouvez leur montrer les instructions relatives à la révision d’accès aux groupes ou aux applications. Si votre révision s’adresse à des invités qui doivent réviser leur propre accès, donnez-leur des instructions sur la méthode à suivre pour réviser leur accès à des groupes ou à des applications.

Si vous avez attribué des invités comme réviseurs et qu’ils n’ont pas accepté l’invitation, ils ne reçoivent pas d’e-mail des examens d’accès, car ils doivent d’abord accepter l’invitation.

### Tableau de l’état de la révision d’accès

| **État** | **Définition** |
|---|---|
| NotStarted | La révision a été créée, la détection des utilisateurs est en attente de démarrage. |
| Initialisation | La détection des utilisateurs est en cours pour identifier tous les utilisateurs faisant partie de la révision. |
| Démarrage en cours | La révision démarre. Si les notifications par e-mail sont activées, des e-mails sont envoyés aux réviseurs. |
| En cours | Révision démarrée. Si les notifications par e-mail sont activées, les e-mails sont envoyés aux réviseurs. Les réviseurs peuvent soumettre des décisions jusqu’à la date d’échéance. |
| En cours de complétion | La révision est en cours de finalisation et les e-mails sont en train d'être envoyés au propriétaire de la révision. |
| Révision automatique | La révision se fait dans le cadre d’une phase de vérification du système. Le système enregistre des décisions pour les utilisateurs qui n’ont pas été révisés en fonction de recommandations ou de décisions préconfigurées. |
| Révisé automatiquement | Les décisions sont enregistrées par le système pour tous les utilisateurs qui n’ont pas été examinés. La révision est prête à passer à l’étape **Applying** si l’application automatique est activée. |
| Appliquer | L’accès n’est pas modifié pour les utilisateurs qui ont été approuvés. |
| Appliqué | Les utilisateurs refusés, le cas échéant, sont supprimés de la ressource ou du répertoire. |
| Échec | La révision n’a pas pu progresser. Cette erreur peut être liée à la suppression du locataire, à une modification des licences ou à d'autres changements internes au niveau du locataire. |

### Créer des révisions via des API

Vous pouvez également créer des révisions d’accès avec des API. Ce que vous faites pour gérer les révisions d’accès des groupes et des utilisateurs d’applications dans le Centre d’administration Entra peut également être effectuée à l’aide des API Microsoft Graph.


## Créer et configurer des révisions d’accès par programmation

Les révisions d'accès Entra sont une caractéristique de la gouvernance des ID Entra. Les révisions d’accès permettent de s’assurer que les bonnes identités ont les droits d’accès pour les ressources appropriées dans l’organisation. Les révisions d'accès peuvent être implémentées par programme à l'aide de l'API des révisions d'accès dans Microsoft Graph.

Pour créer une révision d’accès à l’aide de Graph, appelez l’API Graph pour créer une définition de planification de révision d’accès. L’appelant doit être un utilisateur disposant au moins du rôle **Administrateur de gouvernance** des identités avec une application disposant de l’autorisation déléguée `AccessReview.ReadWrite.All` ou d’une application disposant de l’autorisation `AccessReview.ReadWrite.All` d’application.

Vous pouvez également créer une révision d’accès dans PowerShell avec le cmdlet `New-MgIdentityGovernanceAccessReviewDefinition` à partir des cmdlets Microsoft Graph PowerShell pour le module Identity Governance.

L’API des révisions d’accès dans Microsoft Graph permet aux organisations d’auditer et d’attester l’accès aux ressources de l’organisation auquel les identités sont affectées. Par exemple, l’accès à un site SharePoint contenant des coordonnées de clients. En utilisant l’API des révisions d’accès, les organisations peuvent vérifier et attester l’accès à ces groupes et, par extension, aux ressources.

### API Révision d’accès pour les groupes de sécurité

Ce module d’apprentissage ne recrée pas la méthode pas à pas pour utiliser l’API. Pour obtenir ces informations, consultez l’article [Passez en revue l’accès aux groupes de sécurité à l’aide des API de révision d’accès.](https://learn.microsoft.com/fr-fr/graph/tutorial-accessreviews-securitygroup) Pour passer en revue l’accès invité dans les groupes Microsoft 365 via l’API, consultez [Révision de l’accès aux groupes Microsoft 365 à l’aide des API de révision d’accès](https://learn.microsoft.com/fr-fr/graph/tutorial-accessreviews-m365group). Voici les étapes générales qui doivent être effectuées.

1. Créer une révision d’accès pour le groupe de sécurité
2. Répertorier les instances de la révision d’accès
3. Vérifier qui a été contacté pour la révision
4. Obtenir les décisions
5. Effectuer soi-même l’attestation d’une décision d’accès en attente
6. Confirmer les décisions et l’état de la révision d’accès
7. Nettoyer les ressources

À chaque étape, vous pouvez utiliser l’API pour créer la révision d’accès, l’affecter, vérifier les résultats et agir sur ces informations.


## Surveiller les résultats de la révision d’accès

Entra ID simplifie la manière dont les entreprises gèrent l’accès aux groupes et aux applications avec les révisions d’accès Entra. D’autres services Microsoft en ligne, comme Microsoft 365, peuvent également être gérés avec des révisions d’accès Entra.

### Effectuer une révision d’accès à l’aide de Mes applications

Vous pouvez démarrer le processus de révision d’accès à partir de l’e-mail de notification ou en accédant directement au site.

1. **E-mail** :
2. Sélectionnez le lien **Démarrer la révision** pour ouvrir la révision d’accès.
3. **Si vous n’avez pas reçu l’e-mail**, vous trouverez les révisions d’accès en attente en procédant comme suit :
  1. Connectez-vous au portail My Access à [https://myaccess.microsoft.com](https://myaccess.microsoft.com/).
  2. Sélectionnez **Révisions d’accès** dans le menu de gauche pour afficher la liste des révisions d’accès en attente qui vous sont affectées.  Important Si aucune révision d’accès n’apparaît, il n’y a pas de révisions d’accès à effectuer pour cette organisation et aucune action n’est nécessaire pour l’instant.
  3. Sélectionnez le nom de la révision d’accès que vous souhaitez effectuer.

Une fois que vous avez ouvert la révision d’accès, vous voyez les noms des utilisateurs qui doivent avoir leur accès examiné.

Il y a deux manières d’approuver ou de refuser l’accès :

- Vous pouvez approuver ou refuser l’accès pour un ou plusieurs utilisateurs manuellement en choisissant l’action appropriée pour chaque demande d’utilisateur.
- Vous pouvez accepter les recommandations du système.

#### Approuver ou refuser l’accès pour un ou plusieurs utilisateurs

1. Passez en revue la liste des utilisateurs pour décider s’il faut approuver ou refuser leur accès permanent.
  - Pour approuver ou refuser l’accès pour un seul utilisateur, sélectionnez le cercle en regard de son nom.
  - Pour approuver ou refuser l’accès pour plusieurs utilisateurs, sélectionnez les cercles en regard de chaque utilisateur.

2. Sélectionnez **Approuver** ou **Refuser** dans la barre.  Remarque Si vous ne savez pas, vous pouvez sélectionner « Je ne sais pas », et l'utilisateur conserve son accès, et votre choix est enregistré dans les journaux d'audit.
3. L'administrateur de la révision d'accès peut vous demander de motiver votre décision dans le champ **Motif**.
  - Même si une raison n’est pas requise, vous pouvez toujours fournir une raison pour votre décision et les informations que vous incluez sont disponibles pour d’autres réviseurs.

4. Une fois que vous avez spécifié l’action à entreprendre, sélectionnez **Enregistrer**.
  - Si un utilisateur se voit refuser l’accès, il n’est pas supprimé immédiatement. Ils sont supprimés lorsque la période de révision se termine ou lorsqu’un administrateur arrête la révision si [l’application](https://learn.microsoft.com/fr-fr/azure/active-directory/governance/complete-access-review) automatique est activée.
  - S’il existe plusieurs réviseurs, la dernière réponse envoyée est enregistrée. Prenons un exemple où un administrateur désigne deux réviseurs : Alice et Bob. Alice ouvre la révision d’accès en premier et approuve la demande d’accès d’un utilisateur. Avant la fin de la période de révision, Bob ouvre la révision d’accès et refuse l’accès sur la demande précédemment approuvée par Alice. La dernière décision qui refuse l’accès est la réponse enregistrée.

#### Approuver ou refuser l’accès selon les recommandations

Pour rendre les révisions d’accès plus faciles et plus rapides pour vous, nous fournissons également des suggestions que vous pouvez accepter en une seule sélection. Le système génère des recommandations à l’aide de deux méthodes :

- **Aucune connexion dans les 30 jours** : Il est recommandé de refuser les utilisateurs qui ne se sont pas connectés au cours des 30 derniers jours. La dernière date de connexion de l’utilisateur s’affiche en même temps que la recommandation.
- **Valeur aberrante par rapport aux homologues :**si un utilisateur ne dispose pas des mêmes droits d'accès que ses homologues, le système recommande de refuser l'accès, en fonction de la distance moyenne qui le sépare d’eux dans la hiérarchie de l'organisation.

Pour accepter les recommandations :

1. Sélectionnez un ou plusieurs utilisateurs, puis sélectionnez **Accepter les recommandations** dans la barre. Ou, pour accepter des recommandations pour tous les utilisateurs non révisés, assurez-vous qu’aucun utilisateur n’est sélectionné, puis sélectionnez **Accepter les recommandations** sur la barre supérieure.
2. Sélectionnez **Envoyer** pour confirmer.


## Automatiser les tâches de gestion de la révision d’accès

Vous pouvez choisir d’avoir la suppression d’accès automatisée en définissant l’application automatique des **résultats à la ressource** pour **activer**. Une fois la révision terminée et terminée, les utilisateurs non approuvés par le réviseur sont automatiquement supprimés de la ressource ou conservés avec un accès continu. La suppression d’accès peut signifier la suppression de l’appartenance à leur groupe, de leur assignation d'application ou la révocation de leur droit d’accéder à un rôle privilégié.

### Accepter les recommandations

Les recommandations sont affichées aux réviseurs dans le cadre de l’expérience du réviseur et indiquent la dernière connexion d’une personne au locataire ou au dernier accès à une application. Ces informations aident les réviseurs à prendre la décision appropriée en matière d’accès. La sélection de « Suivre les recommandations » permet de prendre en compte les recommandations issues de l’analyse des accès. À la fin d’une révision d’accès, le système applique automatiquement ces recommandations aux utilisateurs auxquels les réviseurs n’ont pas répondu.

Les recommandations sont basées sur les critères de la révision d’accès. Par exemple, si vous configurez la révision pour supprimer l’accès sans connexion pendant 30 jours, elle recommande de supprimer tous les utilisateurs qui correspondent à ce critère. Cela s’applique à la fois aux connexions interactives et non interactives. Les recommandations peuvent également être basées sur l’analyse hors **norme de pair** ( si un utilisateur n’a pas le même accès que d’autres personnes dans leur structure de création de rapports, le système recommande le déni. Microsoft travaille continuellement à l’amélioration des recommandations.

### Réviser l’accès des utilisateurs invités

Utilisez les révisions d’accès pour examiner et nettoyer les identités des partenaires des organisations externes. La configuration d’une révision par partenaire peut satisfaire aux exigences de conformité.

Les identités externes peuvent être autorisées à accéder aux ressources de l’entreprise par le biais de l’une des actions suivantes :

- Ajouté à un groupe.
- Invitée dans Teams.
- Affectée à une application d’entreprise ou à un package d’accès.
- Assignation d'un rôle privilégié dans Entra ID ou dans un abonnement Azure.

Cet [exemple de script](https://github.com/microsoft/access-reviews-samples/tree/master/ExternalIdentityUse) indique où les identités externes invitées dans l'organisation sont utilisées. Vous pouvez voir l’appartenance à un groupe, les attributions de rôles et les attributions d’applications des utilisateurs externes dans Entra ID. Le script n’affiche aucune attribution en dehors d’Entra ID, tel que l’attribution directe des droits aux ressources SharePoint, sans l’utilisation de groupes.

Lorsque vous créez une révision d’accès pour des groupes ou des applications, vous pouvez choisir de laisser le réviseur se concentrer sur **Toute personne ayant un accès**, ou sur **Utilisateurs invités uniquement**. En sélectionnant uniquement les utilisateurs invités, les réviseurs sont fournis une liste ciblée d’identités externes d’Entra B2B qui ont accès à la ressource.


## Configurer des révisions d’accès récurrentes

Les révisions d’accès peuvent être définies de manière récurrente. Nommez votre révision d’accès, sélectionnez une date de début, une fréquence et une durée, puis indiquez quand la série se termine : **Jamais**, une date de fin spécifique ou un nombre défini d’occurrences. Les réviseurs sont avertis au début de chaque révision. Les réviseurs peuvent approuver ou refuser l’accès avec une interface conviviale et avec l’aide de recommandations intelligentes.

Pourquoi les révisions d’accès périodiques sont-elles importantes ? En raison de la gestion du cycle de vie. Tout ce qui commence doit avoir une date de fin. Entre le début et la fin, nous devons vérifier que les autorisations sont bien ce qu’elles doivent être. Ni trop, ni trop peu. Nous demandons aussi régulièrement à un propriétaire si tout est bien toujours comme il le souhaite. Avec la périodicité, nous nous assurons que cette vérification est effectuée régulièrement.

Une fois qu’une série de révisions périodiques démarre, vous pouvez mettre à jour ses paramètres ou réviseurs à tout moment. Lors de la mise à jour, vous pouvez appliquer des modifications uniquement à l’instance **actuelle** (révision active) ou à la **série** (toutes les périodicités futures). Par exemple, si un réviseur quitte l’organisation, mettez à jour la série afin de le remplacer pour toutes les révisions futures. Si vous devez uniquement ajuster les paramètres de la révision en cours, mettez à jour l’instance actuelle à la place.


## Explorer l’agent de révision d’accès dans Entra

Historiquement, les révisions d’accès sont un processus manuel qui peut entraîner des erreurs et des erreurs potentielles. Les réviseurs n’ont pas toujours accès aux enregistrements et aux données pour prendre des décisions de révision et n’ont souvent pas suffisamment de temps pour terminer la révision. Que se passe-t-il s’il y avait un agent qui pouvait aider à la tâche ?

### Agent de révision d'accès dans Entra

Permettre à vos réviseurs de prendre des décisions d’accès rapides et précises. L’agent de révision d’accès avec Entra ID Governance fournit des insights et des recommandations afin que les réviseurs puissent effectuer leur travail par le biais d’une conversation simple, directement dans Microsoft Teams.

#### Fonctionnement de l’agent

L’agent de révision d’accès procède à une analyse proactive des révisions d’accès actives dans votre locataire Azure AD. L’agent analyse ensuite les révisions identifiées en collectant des insights supplémentaires et génère une recommandation (approuver/refuser). La recommandation inclut également un résumé de justification pour chaque décision. L’agent guide les réviseurs, en langage naturel, par le biais du processus de révision dans Microsoft Teams. À mesure que l’agent le guide tout au long de la révision, le réviseur peut examiner le raisonnement derrière les recommandations, poser des questions dans le contexte de l’examen lui-même et prendre enfin sa propre décision éclairée. La recommandation des agents (approuver/refuser) pour chaque décision s’appuie sur un mécanisme de scoring déterministe alimenté par plusieurs signaux.

##### L’agent prend en compte les signaux suivants :

- **Inactivité de l’utilisateur** : si l’utilisateur s’est connecté (récemment)
- **Affiliation de l’utilisateur à groupe** : si l’utilisateur a une faible affiliation avec d’autres utilisateurs disposant de cet accès
- **Compte activé** : si le compte de l’utilisateur est activé (propriété accountEnabled)
- **État de l’emploi** : si l’emploi de l’utilisateur s’est terminé (propriété employeeLeaveDateTime)
- **Historique des flux de travail de cycle de vie** : si un flux de travail de déplacement a été exécuté pour l’utilisateur au cours des 30 derniers jours
- **Décisions des révisions précédentes** : pour les révisions périodiques, les décisions des itérations de révision précédentes sont prises en compte
- **Historique des demandes d’accès** : pour les révisions d’affectation de package d’accès, l’historique des demandes et des approbations est pris en compte.

#### Prerequisites

Pour utiliser l’Agent de révision d’accès dans Entra, vous avez besoin des éléments suivants :

- Licences Entra ID Governance *ou* Entra Suite.
- Intégration à Security Copilot avec au moins une unité de calcul de sécurité (SCU).
- Les administrateurs doivent avoir au moins tous les rôles suivants pour configurer et gérer l’agent dans le Centre d’administration Entra :
  - Administrateur de gouvernance des identités
  - Administrateur de workflows de cycle de vie
  - Contributeur de Copilot de sécurité dans Security Copilot

- Pour que les réviseurs utilisent l’agent de révision d’accès, ils doivent avoir accès à Microsoft Teams et doivent disposer d’une révision d’accès active affectée. Ils doivent avoir le rôle attribué : Contributeur Security Copilot

#### Limites

Une fois les agents démarrés, ils ne peuvent pas être arrêtés ou suspendus. L'exécution peut prendre quelques minutes. Nous vous recommandons d’exécuter l’agent à partir du Centre d’administration Entra.

### Activation de l’agent de révision d’accès

1. Avec un compte qui a au moins tous les rôles suivants, connectez-vous au Centre d’administration Entra :
  - Administrateur de gouvernance des identités
  - Administrateur de workflows de cycle de vie
  - Contributeur Copilot de sécurité

2. Dans la nouvelle page d’accueil, sélectionnez Accéder aux agents à partir de la carte de notification de l’agent.
  - Vous pouvez également sélectionner Agents dans le menu de navigation de gauche.

3. Sélectionnez Afficher les détails de la vignette Agent de révision d’accès.
4. Sélectionnez Démarrer l’agent pour lancer votre première exécution.
  - Un message indiquant que « L'agent démarre son premier cycle » apparaît dans le coin supérieur droit. Le premier cycle peut prendre quelques minutes.

### Activer l’agent de révision d’accès pour les révisions d’accès de groupe et d’application existantes

Pour mettre à jour une révision d’accès existante pour l’agent de révision d’accès, procédez comme suit :

1. Connectez-vous au Centre d’administration Entra en tant qu’administrateur de gouvernance des identités au moins.
2. Accédez à **Gouvernance des ID**, puis **Révisions d'accès**.
3. Sélectionnez la révision d’accès à prendre en charge par l’agent.
4. Dans la page vue d’ensemble de la révision d’accès, sélectionnez **Paramètres** sous **Gérer** (révision ponctuelle) ou **Paramètres** sous **Série** (révision périodique).
5. Sous Paramètres avancés, cochez la case sur le paramètre qui indique Access Review Agent (préversion).
6. Sélectionnez Enregistrer.


## Évaluation du module

Choisissez la meilleure réponse à chacune des questions ci-dessous.

### Vérifiez vos connaissances


## Récapitulatif et ressources

Une fois ce module terminé, vous pouvez :

- Planifier des révisions d’accès.
- Créer des révisions d’accès pour les groupes et les applications.
- Surveiller les résultats de la révision d’accès.
- Créez et gérez des programmes de révision d’accès.
- Automatiser les tâches de gestion de la révision d’accès.
- Configurer des révisions d’accès récurrentes.
- Utilisez l’Agent de révision d’accès pour terminer les révisions d’accès à l’aide du langage naturel dans Microsoft Teams.

Dans ce module, vous avez appris à préparer et à effectuer des révisions d’accès. Les révisions d’accès sont essentielles à la sécurité de votre organisation et à la façon de les configurer de façon récurrente.

### Ressources

Utilisez ces ressources pour approfondir vos connaissances.

- [Qu’est-ce que les révisions d’accès ?](https://learn.microsoft.com/fr-fr/entra/id-governance/access-reviews-overview)
- [Gérer l’accès utilisateur et invité avec révisions d’accès](https://learn.microsoft.com/fr-fr/entra/id-governance/manage-access-review)
- [Passer en revue votre accès aux ressources avec Entra Access Reviews](https://learn.microsoft.com/fr-fr/entra/id-governance/self-access-review)
- [Vue d’ensemble de l’API révision d’accès](https://learn.microsoft.com/fr-fr/entra/id-governance/create-access-review#create-an-access-review-programmatically)
- [Agent de révision d’accès](https://learn.microsoft.com/fr-fr/entra/id-governance/access-review-agent)
- [Passer en revue l’accès aux groupes de sécurité grâce aux API de révision d'accès](https://learn.microsoft.com/fr-fr/graph/tutorial-accessreviews-securitygroup)


---

# Planifier et implémenter un accès privilégié

_https://learn.microsoft.com/fr-fr/training/modules/plan-implement-privileged-access/_


## Présentation

Pour renforcer la sécurité de votre solution de Azure, vous devez vous assurer que les rôles d’administration sont protégés et gérés. Découvrez comment utiliser Privileged Identity Management (PIM) pour protéger vos données et ressources. Dans ce module, vous allez apprendre à créer une stratégie d’accès. Ensuite, vous configurez et affectez des rôles et des ressources PIM, et gérez les comptes d’accès d’urgence.

### Objectifs d’apprentissage

À la fin de ce module, vous pouvez :

- Définissez une stratégie d’accès privilégié pour les utilisateurs administratifs (ressources, rôles, approbations, seuils).
- Configurez PIM pour les rôles Azure.
- Configurez PIM pour les ressources Azure.
- Attribuer des rôles.
- Gérer les demandes PIM.
- Analysez l’historique et les rapports d’audit PIM.
- Créez et gérez des comptes d’accès d’urgence.
- Configurer des groupes d’accès privilégiés

Les organisations souhaitent réduire le nombre de personnes qui ont accès à des informations ou ressources sécurisées. La réduction de l’accès réduit le risque qu’un acteur malveillant obtienne cet accès. Il peut également empêcher un utilisateur autorisé d’affecter par inadvertance une ressource sensible. Toutefois, les utilisateurs doivent toujours effectuer des opérations privilégiées dans les applications Entra ID, Azure, Microsoft 365 ou SaaS. Les organisations peuvent accorder aux utilisateurs un accès privilégié juste-à-temps aux ressources Azure. Ensuite, vous pouvez suivre et gérer la nécessité de surveiller ce que font ces utilisateurs avec leurs privilèges d’administrateur.

### Conditions préalables

Aucun


## Définir une stratégie d’accès privilégié pour les utilisateurs administratifs

### Qu’est-ce que Privileged Identity Management (PIM) ?

PIM est un service dans Entra ID, pour gérer l’accès aux ressources privilégiées. PIM vous permet de gérer, contrôler et surveiller l’accès aux ressources importantes de votre organisation. Ces ressources incluent celles d’Entra ID, Azure et d’autres services Microsoft Online, tels que Microsoft 365 ou Microsoft Intune.

### Que fait PIM ?

PIM fournit une activation de rôle basée sur le temps et basée sur l’approbation pour accéder aux ressources. Cela permet d’atténuer les risques d’autorisations d’accès excessives, inutiles ou incorrectes sur les ressources dont vous vous souciez. Les principales fonctionnalités de PIM sont les suivantes :

- Fournir un accès privilégié juste-à-temps aux ressources Entra ID et Azure
- Attribuer un accès limité à l’heure aux ressources à l’aide des dates de début et de fin
- Exiger l’approbation pour activer des rôles privilégiés
- Appliquer l’authentification multifacteur Azure pour activer n’importe quel rôle
- Utiliser la justification pour comprendre pourquoi les utilisateurs activent
- Recevoir des notifications lorsque des rôles privilégiés sont activés
- Effectuer des révisions d’accès pour garantir que les utilisateurs ont toujours besoin de rôles
- Télécharger l’historique d’audit pour l’audit interne ou externe

Avant de déployer PIM dans votre organisation, suivez les instructions et comprenez les concepts de cette section. Cela vous aidera à créer un plan adapté aux exigences d’identité privilégiée de votre organisation.

Remarque

PIM nécessite une licence Premium P2.

### Identifier vos parties prenantes

La section suivante vous aide à identifier toutes les parties prenantes impliquées dans le projet. Vous regardez qui a besoin d’approuver, de réviser ou de rester informé. Il inclut des tables distinctes pour le déploiement de PIM pour les rôles Entra et PIM pour les rôles Azure. Ajoutez des parties prenantes au tableau suivant selon les besoins de votre organisation.

SO = Approbation sur ce projet

R = Passer en revue ce projet et apporter des commentaires

I = Informé de ce projet

#### Parties prenantes : Gestion des identités privilégiées pour les rôles Entra

| **Name** (Nom) | **Rôle** | **Action** |
|---|---|---|
| Nom et e-mail | **'architecte d’identité ou administrateur général Azure** : représentant de l’équipe de gestion des identités chargé de définir comment aligner cette modification avec l’infrastructure principale de gestion des identités de votre organisation. | SO/R/I |
| Nom et e-mail | **propriétaire du service ou gestionnaire de lignes** : représentant des propriétaires informatiques d’un service ou d’un groupe de services. Ils sont essentiels pour prendre des décisions et aider à déployer PIM pour leur équipe. | SO/R/I |
| Nom et e-mail | **propriétaire de la sécurité** : représentant de l’équipe de sécurité qui peut approuver que le plan répond aux exigences de sécurité de votre organisation. | SO/R |
| Nom et e-mail | **responsable du support informatique / support technique** - représentant de l’organisation de support informatique qui peut fournir des commentaires sur la prise en charge de ce changement du point de vue du support technique. | R/I |
| Nom et e-mail pour les utilisateurs pilotes | **utilisateurs de rôle privilégié** : groupe d’utilisateurs pour lesquels la gestion des identités privilégiées est implémentée. Ils devront savoir comment activer leurs rôles une fois PIM implémenté. | I |

#### Parties prenantes : Gestion des Identités Privilégiées pour les rôles dans Azure

| **Name** (Nom) | **Rôle** | **Action** |
|---|---|---|
| Nom et e-mail | **propriétaire de l’abonnement/de la ressource** : représentant des propriétaires informatiques de chaque abonnement ou ressource pour lequel vous souhaitez déployer PIM. | SO/R/I |
| Nom et e-mail | **propriétaire de la sécurité** : représentant de l’équipe de sécurité qui peut approuver que le plan répond aux exigences de sécurité de votre organisation. | SO/R |
| Nom et e-mail | **responsable du support informatique / support technique** - représentant de l’organisation de support informatique qui peut fournir des commentaires sur la prise en charge de ce changement du point de vue du support technique. | R/I |
| Nom et e-mail pour les utilisateurs pilotes | **utilisateurs de rôle Azure** : groupe d’utilisateurs pour lesquels la gestion des identités privilégiées est implémentée. Ils devront savoir comment activer leurs rôles une fois PIM implémenté. | I |

### Commencer à utiliser Privileged Identity Management

Dans le cadre du processus de planification, préparez PIM en suivant notre article « Commencer à utiliser Privileged Identity Management ». PIM vous donne accès à certaines fonctionnalités conçues pour faciliter votre déploiement.

Si votre objectif est de déployer PIM pour les ressources Azure, suivez notre article « Découvrir les ressources Azure à gérer dans Privileged Identity Management ». Seuls les propriétaires d’abonnements et de groupes d’administration peuvent mettre ces ressources sous gestion par PIM. Une fois sous gestion, la fonctionnalité PIM est accessible aux propriétaires à tous les niveaux, y compris le groupe d’administration, l’abonnement, le groupe de ressources et la ressource. Si vous êtes administrateur général et que vous tentez de déployer PIM pour vos ressources Azure, vous pouvez élever l’accès pour gérer tous les abonnements Azure. Cela vous donne accès à toutes les ressources Azure de l’annuaire pour la découverte. Toutefois, nous vous conseillons d’obtenir l’approbation de chacun de vos propriétaires d’abonnements avant de gérer leurs ressources avec PIM.

### Appliquer le principe du privilège minimum

Il est important de vous assurer que vous avez appliqué le principe des privilèges minimum dans votre organisation pour votre ID Entra et vos rôles Azure.

#### Planifier la délégation du moindre privilège

Pour les rôles Entra, les organisations attribuent couramment le rôle Administrateur général à un certain nombre d’administrateurs, alors que la plupart n’ont besoin que d’un ou deux rôles d’administrateur spécifiques et moins puissants. Avec un grand nombre d’administrateurs généraux ou d’autres rôles à privilèges élevés, il est difficile de suivre de près vos attributions de rôles privilégiés.

Suivez ces étapes pour implémenter le principe de privilège minimum pour vos rôles Entra.

1. Comprendre la granularité des rôles en lisant et en comprenant les rôles d’administrateur Entra disponibles. Vous et votre équipe devez également référencer des rôles d’administrateur par tâche d’identité dans l’ID Entra, ce qui explique le rôle le moins privilégié pour des tâches spécifiques.
2. Répertoriez qui a des rôles privilégiés dans votre organisation. Vous pouvez utiliser PIM Discovery et Insights (version préliminaire) pour réduire votre exposition.
3. Pour tous les administrateurs généraux de votre organisation, découvrez pourquoi ils ont besoin du rôle. Supprimez-les ensuite du rôle Administrateur général et attribuez des rôles intégrés ou des rôles personnalisés avec des privilèges inférieurs à l’intérieur de l’ID Entra. Pour l’instant, Microsoft n’a qu’environ 10 administrateurs disposant du rôle Administrateur général.
4. Pour tous les autres rôles Entra, passez en revue la liste des affectations, identifiez les administrateurs qui n’ont plus besoin du rôle et supprimez-les de leurs attributions.

Pour automatiser les deux dernières étapes, vous pouvez utiliser les révisions d’accès dans PIM. En suivant les étapes décrites dans « Démarrer une révision d’accès pour les rôles Entra dans Privileged Identity Management », vous pouvez configurer une révision d’accès pour chaque rôle d’ID Entra comptant un ou plusieurs membres.

Définissez les réviseurs sur **Membres (soi-même)**. Tous les utilisateurs du rôle recevront un e-mail leur demandant de confirmer qu’ils ont besoin de l’accès. En outre, activez **Exiger une raison d’approbation** dans les paramètres avancés afin que les utilisateurs doivent indiquer pourquoi ils ont besoin du rôle. En fonction de ces informations, vous pouvez supprimer les utilisateurs des rôles inutiles ou les déléguer à des rôles d’administrateur plus précis.

Les revues d’accès s’appuient sur les e-mails pour informer les utilisateurs qu'ils doivent examiner leur accès aux rôles. Si vous avez des comptes privilégiés qui n’ont pas d’e-mails liés, veillez à remplir le champ de messagerie secondaire sur ces comptes.

#### Planifier la délégation de rôles des ressources Azure

Pour les abonnements et ressources Azure, vous pouvez configurer un processus de révision d’accès similaire pour passer en revue les rôles dans chaque abonnement ou ressource. L’objectif de ce processus est de réduire les affectations propriétaire et administrateur d’accès utilisateur attachées à chaque abonnement ou ressource et de supprimer les affectations inutiles. Toutefois, les organisations délèguent souvent ces tâches au propriétaire de chaque abonnement ou ressource, car elles ont une meilleure compréhension des rôles spécifiques (en particulier des rôles personnalisés).

Si vous avez le rôle Administrateur général et que vous tentez de déployer PIM pour les rôles Azure dans votre organisation, vous pouvez élever l’accès pour gérer tous les abonnements Azure, ce qui vous donne accès à chacun d’eux. Vous pouvez ensuite trouver chaque propriétaire d’abonnement et travailler avec eux pour supprimer les attributions inutiles et réduire l’attribution du rôle de propriétaire.

Les utilisateurs disposant du rôle Propriétaire pour un abonnement Azure peuvent également utiliser les révisions d’accès pour les ressources Azure, afin d’auditer et de supprimer des attributions de rôles inutiles, comme dans le processus décrit précédemment pour les rôles Entra.

### Décider quelles attributions de rôles doivent être protégées par Privileged Identity Management

Après le nettoyage des attributions de rôle privilégié dans votre organisation, vous devez choisir les rôles à protéger avec Privileged Identity Management.

Si un rôle est protégé par PIM, les utilisateurs éligibles qui lui sont affectés doivent élever pour utiliser les privilèges accordés par le rôle. Le processus d’élévation peut également inclure l’obtention de l’approbation, l’utilisation d’Azure Multifactor Authentication et la raison pour laquelle ils sont activés. PIM peut également suivre les élévations via les notifications et les journaux d’événements d’audit PIM et Entra.

Choisir les rôles à protéger avec PIM peut être difficile et sera différent pour chaque organisation. Cette section fournit nos meilleures pratiques pour les rôles Entra et les rôles Azure.

#### Rôles Entra

Il est important de hiérarchiser la protection des rôles Entra qui disposent des autorisations les plus importantes. En fonction des modèles d’utilisation parmi tous les clients PIM, les 10 principaux rôles Entra gérés par PIM sont les suivants :

- Administrateur général
- Administrateur de sécurité
- Administrateur d’utilisateurs
- Administrateur Exchange
- Administrateur SharePoint
- Administrateur Intune
- Lecteur de sécurité
- Administrateur de service
- Administrateur de facturation
- Administrateur Skype Entreprise  Conseil Microsoft vous recommande de gérer d’abord tous vos administrateurs généraux et administrateurs de sécurité à l’aide de PIM : ce sont les utilisateurs qui peuvent faire le plus de mal lorsqu’ils sont compromis.

Il est important de prendre en compte les données et autorisations les plus sensibles pour votre organisation. Par exemple, certaines organisations souhaitent protéger leur rôle d’administrateur Power BI ou d’administrateur Teams à l’aide de PIM, car ces rôles peuvent accéder aux données et modifier les flux de travail principaux.

S’il existe des rôles auxquels les utilisateurs invités sont affectés, ils sont vulnérables aux attaques.

Conseil

Microsoft vous recommande de gérer tous les rôles avec des utilisateurs invités à l’aide de PIM pour réduire les risques associés aux comptes d’utilisateurs invités compromis.

Les rôles de lecteur, comme le lecteur d’annuaire, le lecteur du centre de messages et le lecteur de sécurité, sont parfois considérés comme moins importants que d’autres, car ils n’ont pas d’autorisation d’écriture. Toutefois, nous avons certains clients qui protègent également ces rôles, car les attaquants ayant accès à ces comptes peuvent être en mesure de lire des données sensibles, y compris des données personnelles. Prenez ce risque en considération lorsque vous décidez si vous souhaitez que les rôles de lecteur de votre organisation soient gérés à l’aide de PIM.

#### Rôles Azure

Lorsque vous décidez quelles attributions de rôles doivent être gérées à l’aide de PIM pour les ressources Azure, vous devez d’abord identifier les abonnements/ressources qui sont les plus essentiels pour votre organisation. Voici quelques exemples d’abonnements/ressources suivants :

- Ressources qui hébergent les données les plus sensibles.
- Les ressources dont dépendent les principales applications client.

Si vous êtes administrateur général et que vous avez des difficultés à décider quels abonnements et ressources sont les plus importants, contactez les propriétaires d’abonnements de votre organisation pour rassembler la liste des ressources gérées par chaque abonnement. Ensuite, collaborez avec les propriétaires d’abonnements pour regrouper les ressources en fonction du niveau de gravité dans le cas où elles sont compromises (faible, moyenne, élevée). Hiérarchisez la gestion des ressources avec PIM en fonction de ce niveau de gravité.

Conseil

Microsoft vous recommande de travailler avec les propriétaires d'abonnements/ressources des services critiques pour configurer le flux de travail PIM pour tous les rôles au sein d'abonnements/ressources sensibles.

PIM pour les ressources Azure prend en charge les comptes de service à durée limitée. Vous devez traiter exactement les comptes de service de la même façon que vous traitez un compte d’utilisateur standard.

Pour les abonnements/ressources qui ne sont pas aussi critiques, vous n’aurez pas besoin de configurer PIM pour tous les rôles. Toutefois, vous devez toujours protéger les rôles Propriétaire et Administrateur d’accès utilisateur avec PIM.

Conseil

Microsoft vous recommande de gérer les rôles propriétaire et les rôles Administrateur d’accès utilisateur de tous les abonnements/ressources à l’aide de PIM.

### Décider s’il faut utiliser un groupe pour attribuer des rôles

L’attribution d’un rôle à un groupe plutôt qu’à des utilisateurs individuels est une décision stratégique. Lors de la planification, envisagez d’attribuer un rôle à un groupe pour gérer les attributions de rôles lorsque :

- De nombreux utilisateurs sont affectés à un rôle.
- Vous souhaitez déléguer l’attribution du rôle.

#### De nombreux utilisateurs sont affectés à un rôle

Suivre manuellement qui est affecté à un rôle et gérer ses attributions en fonction de leur besoin peut prendre du temps. Pour affecter un groupe à un rôle, créez d’abord un groupe assignable à un rôle, puis attribuez le groupe comme éligible à un rôle. Cette action soumet tous les membres du groupe au même processus d’activation que les utilisateurs individuels qui sont éligibles pour accéder au rôle. Les membres du groupe activent leurs affectations au groupe individuellement à l’aide de la requête d’activation et du processus d’approbation Privileged Identity Management. Le groupe n’est pas activé. Il s’agit simplement de l’appartenance au groupe de l’utilisateur.

#### Vous souhaitez déléguer l’attribution du rôle

Un propriétaire de groupe peut gérer l’appartenance à un groupe. Pour les groupes assignables aux rôles d’ID Entra, seuls l’administrateur de rôle privilégié, l’administrateur général et les propriétaires de groupe peuvent gérer l’appartenance au groupe. Lorsqu’un administrateur ajoute de nouveaux membres au groupe, le membre accède aux rôles auxquels le groupe est affecté, que l’affectation soit éligible ou active. Utilisez les propriétaires de groupes pour déléguer la gestion de l’appartenance à un groupe pour un rôle affecté afin de réduire l’étendue des privilèges requis.

Conseil

Microsoft vous recommande de placer les groupes auxquels un rôle Entra ID peut être attribué sous la gestion de PIM. Une fois qu’un groupe assignable à un rôle est géré par PIM, il s’agit d’un groupe d’accès privilégié. Utilisez PIM pour exiger que les propriétaires de groupes activent leur attribution de rôle Propriétaire avant de pouvoir gérer l’appartenance au groupe.

### Déterminer quelles attributions de rôles doivent être permanentes ou éligibles

Une fois que vous avez choisi la liste des rôles à gérer par PIM, vous devez décider quels utilisateurs doivent obtenir le rôle éligible par rapport au rôle actif permanent. **Les rôles actifs permanents sont les rôles normaux attribués via l'ID Entra et les ressources Azure, tandis que les rôles éligibles peuvent uniquement être attribués dans PIM.**

Microsoft vous recommande de n’avoir aucune attribution active en permanence pour les rôles Entra et les rôles Azure, hormis les deux comptes d’accès d’urgence recommandés, qui doivent avoir le rôle permanent Administrateur général.

Même si nous recommandons zéro administrateur permanent, il est parfois difficile pour les organisations d’y parvenir immédiatement. Les éléments à prendre en compte lors de la prise de cette décision sont les suivants :

- Fréquence d’élévation : si l’utilisateur a uniquement besoin de l’affectation privilégiée une seule fois, il ne doit pas avoir l’affectation permanente. En revanche, si l’utilisateur a besoin du rôle pour son travail quotidien et que l’utilisation de PIM réduirait considérablement sa productivité, il peut être considéré comme étant permanent.
- Cas spécifiques à votre organisation : la personne qui reçoit le rôle éligible peut venir d’une équipe distante ou être un cadre de haut rang, au point que la communication et l’application du processus d’élévation deviennent difficiles. Elle peut alors être considérée comme permanente.  Conseil Microsoft vous recommande de configurer des révisions d’accès périodiques pour les utilisateurs disposant d’attributions de rôles permanentes.

### Configurez vos paramètres de gestion des identités privilégiées

Avant d’implémenter votre solution PIM, il est recommandé de rédiger vos paramètres PIM pour chaque rôle privilégié que votre organisation utilise. Cette section contient quelques exemples de paramètres PIM pour des rôles particuliers ; ils sont à des fins de référence uniquement et peuvent être différents pour votre organisation. Chacun de ces paramètres est expliqué en détail avec les recommandations de Microsoft après les tables.

#### Paramètres de gestion des identités privilégiées pour les rôles Entra

| **Paramètre** | **Administrateur global** | Administrateur Exchange | **administrateur du support technique** |
|---|---|---|---|
| Exiger l’authentification multifacteur ; vérification en deux étapes | Oui | Oui | Non |
| Notification | Oui | Oui | Non |
| Ticket d’incident | Oui | Non | Oui |
| Exiger l’approbation | Oui | Non | Non |
| Approbateur | Autres administrateurs généraux | Aucun | Aucun |
| Durée d’activation | 1 heure | 2 heures | 8 heures |
| Administrateur permanent | Comptes d’accès d’urgence | Aucun | Aucun |

#### Paramètres Privileged Identity Management pour les rôles Azure

| **Paramètre** | **Propriétaire des abonnements critiques** | **Administrateur de l’accès utilisateur des abonnements moins critiques** | **Contributeur de Machine Virtuelle** |
|---|---|---|---|
| Exiger l’authentification multifacteur ; vérification en deux étapes | Oui | Oui | Non |
| Notification | Oui | Oui | Oui |
| Exiger l’approbation | Oui | Non | Non |
| Approbateur | Autres propriétaires de l’abonnement | Aucun | Aucun |
| Durée d’activation | 1 heure | 1 heure | 3 heures |
| Administrateur actif | Aucun | Aucun | Aucun |
| Expiration active | n/a | n/a | n/a |

Le tableau suivant décrit chacun des paramètres.

| **Paramètre** | **Description** |
|---|---|
| Rôle | Nom du rôle pour lequel vous définissez les paramètres. |
| Exiger l’authentification multifacteur ; vérification en deux étapes | Indique si l’utilisateur éligible doit effectuer l’authentification multifacteur ; Vérification en deux étapes avant d’activer le rôle. |
|   | **Microsoft recommande d’appliquer l’authentification multifacteur** ; Vérification en deux étapes pour tous les rôles d’administrateur, en particulier si les rôles ont des utilisateurs invités. |
| Notification | Si la valeur est true, l’administrateur général, l’administrateur de rôle privilégié et l’administrateur de sécurité de l’organisation recevront une notification par e-mail lorsqu’un utilisateur éligible active le rôle. |
|   | Certaines organisations n’ont pas d’adresse e-mail liée à leurs comptes d’administrateur. Pour obtenir ces notifications par e-mail, définissez une autre adresse e-mail afin que les administrateurs reçoivent ces e-mails. |
| Ticket d’incident | Indique si l’utilisateur éligible doit enregistrer un numéro de ticket d’incident lors de l’activation de son rôle. Ce paramètre permet à une organisation d’identifier chaque activation avec un numéro d’incident interne pour atténuer les activations indésirables. |
|   | **Microsoft recommande** de tirer parti des numéros de tickets d'incidents pour intégrer PIM à votre système interne. Cette méthode peut être utile pour les approbateurs qui ont besoin de contexte pour l’activation. |
| Exiger l’approbation | Indique si l’utilisateur éligible doit obtenir l’approbation pour activer le rôle. |
|   | **Microsoft recommande** de configurer l’approbation pour les rôles avec le plus d’autorisations. En fonction des modèles d’utilisation de tous les clients PIM, Administrateur général, Administrateur utilisateur, Administrateur Exchange, Administrateur de sécurité et Administrateur de mot de passe sont les rôles les plus courants avec approbation requise. |
| Approbateur | Si l’approbation est requise pour activer le rôle éligible, répertoriez les personnes qui doivent approuver la demande. Par défaut, PIM définit l’approbateur sur tous les utilisateurs qui sont des administrateurs de rôles privilégiés, qu’ils soient permanents ou éligibles. |
|   | Si un utilisateur est éligible à la fois pour un rôle Entra et pour un approbateur du rôle, il ne sera pas en mesure de s’approuver lui-même. |
|   | **Microsoft recommande** de choisir des approbateurs en tant qu'utilisateurs qui connaissent le mieux le rôle et ses utilisateurs fréquents plutôt qu'un administrateur global. |
| Durée de l’activation | Durée d’activation d’un utilisateur dans le rôle avant son expiration. |
| Administrateur permanent | Liste des utilisateurs qui seront des administrateurs permanents pour ce rôle (qui n'auront jamais besoin d'être activés). |
|   | **Microsoft recommande** que vous n'ayez aucun administrateur permanent pour tous les rôles, à l'exception des administrateurs globaux. |
| Administrateur actif | Pour les ressources Azure, l’administrateur actif est la liste des utilisateurs qui n’auront jamais à activer pour utiliser le rôle. Cette liste n’est pas appelée administrateur permanent comme dans les rôles Entra, car vous pouvez définir une heure d’expiration pour laquelle l’utilisateur perdra ce rôle. |
| Expiration active | Les attributions de rôles actives pour les rôles Azure expirent après la durée configurée. Vous pouvez choisir entre 15 jours, 1 mois, 3 mois, 6 mois, 1 an ou actif définitivement. |
| Expiration admissible | Les attributions de rôles éligibles pour les rôles Azure expirent après cette durée. Vous pouvez choisir entre 15 jours, 1 mois, 3 mois, 6 mois, 1 an ou éligible définitivement. |


## Configurer Privileged Identity Management pour les ressources Azure

À l’aide d’Entra PIM, vous pouvez améliorer la protection de vos ressources Azure. Ceci est utile pour :

- Organisations qui utilisent déjà PIM pour protéger les rôles Entra.
- Les propriétaires d’abonnements et de groupes d’administration qui tentent de sécuriser des ressources de production.

Lorsque vous configurez PIM pour les ressources Azure pour la première fois, vous devez découvrir et sélectionner les ressources à protéger avec PIM. Il n’existe aucune limite au nombre de ressources que vous pouvez gérer avec PIM. Toutefois, nous vous recommandons de commencer par vos ressources de production les plus critiques.

### Découvrir les ressources

1. Connectez-vous au Centre d’administration Entra.
2. Ouvrez **Entra Privileged Identity Management**.
3. Si c’est la première fois que vous utilisez PIM pour des **ressources Azure**, vous voyez s’afficher un volet **Découvrir les ressources**.
4. Si un autre administrateur de votre organisation gère déjà des ressources Azure dans PIM, vous verrez une liste des ressources actuellement gérées.
5. Sélectionnez **Découvrir des ressources** pour lancer l'expérience de découverte.
6. Dans la page **Découverte**, utilisez **filtre d’état des ressources** et sélectionnez le type de ressource pour filtrer les groupes d’administration ou les abonnements auxquels vous avez l’autorisation d’écriture. Le plus simple est probablement de commencer avec **Tous**. Vous pouvez rechercher et sélectionner des ressources de groupe d’administration ou d’abonnement à gérer dans PIM. Lorsque vous gérez un groupe d’administration ou un abonnement dans PIM, vous pouvez également gérer ses ressources enfants.  Remarque Lorsque vous ajoutez une nouvelle ressource Azure enfant à un groupe d’administration géré par PIM, vous pouvez mettre la ressource enfant sous gestion en la recherchant dans PIM.
7. Sélectionnez les ressources non managées que vous souhaitez gérer.
8. Sélectionnez **Gérer la ressource** pour commencer à gérer les ressources sélectionnées.
9. Si vous voyez un message pour confirmer l’intégration de la ressource sélectionnée pour la gestion, sélectionnez **Oui**


## Exercice de configuration de Privileged Identity Management pour les rôles Entra

### Configurer les paramètres de rôle Entra

#### Ouvrir les paramètres de rôle

Suivez ces étapes pour ouvrir les paramètres d’un rôle Entra.

1. Connectez-vous au centre d’administration Entra  en tant qu’administrateur client.
2. Recherchez, puis sélectionnez **Entra Privileged Identity Management.**
3. Dans l’écran Privileged Identity Management, dans la navigation de gauche, sélectionnez **rôles Entra.**
4. Dans la page Démarrage rapide, dans le volet de navigation gauche, sélectionnez **Paramètres.**
5. Passez en revue la liste des rôles, puis, dans la **Recherche par nom de rôle**, entrez **Compliance**.
6. Dans les résultats, sélectionnez **Administrateur de conformité**.
7. Passez en revue les informations détaillées sur les paramètres de rôle.

#### Exiger l’approbation pour l’activation

Si vous définissez plusieurs approbateurs, l’approbation se termine dès qu’un d’eux approuve ou refuse. Vous ne pouvez pas exiger l’approbation d’au moins deux utilisateurs. Pour exiger l’approbation d’activer un rôle, procédez comme suit.

1. Dans la page détails du paramètre de rôle, dans le menu supérieur, sélectionnez **Modifier**.
2. Dans le paramètre Modifier le rôle – Écran Administrateur de conformité, cochez la case **Exiger l’approbation pour activer**.
3. Sélectionnez **Sélectionner des approbateurs**.
4. Dans le volet Sélectionner un membre, sélectionnez votre compte d’administrateur, puis sélectionnez **Sélectionner**.
5. Une fois que vous avez configuré les paramètres de rôle, sélectionnez **Mettre à jour** pour enregistrer vos modifications.


## Exercice d’attribution de rôles Entra dans Privileged Identity Management

Avec l’ID Entra, un administrateur général peut effectuer des attributions de rôle d’administrateur Entra permanentes. Ces attributions de rôles peuvent être créées à l’aide du portail Azure ou à l’aide de commandes PowerShell.

Le service Entra Privileged Identity Management (PIM) permet également aux administrateurs de rôles privilégiés d’effectuer des attributions de rôles d’administrateur permanents. En outre, les administrateurs de rôles privilégiés peuvent rendre les utilisateurs éligibles pour les rôles d’administrateur Entra. Un administrateur éligible peut activer le rôle quand il en a besoin, puis ses autorisations expirent une fois qu’ils ont terminé.

### Attribuer un rôle

Suivez ces étapes pour rendre un utilisateur éligible à un rôle d’administrateur Entra.

1. Connectez-vous au centre d’administration Entra  en tant qu’administrateur client.
2. Recherchez, puis sélectionnez **Entra Privileged Identity Management.**
3. Dans l’écran Privileged Identity Management, dans la navigation de gauche, sélectionnez **rôles Entra.**
4. Sur la page Démarrage rapide, dans le volet de navigation de gauche, sélectionnez **Rôles.**
5. Dans le menu supérieur, sélectionnez **+ Ajouter des affectations.**
6. Dans le volet Ajouter des affectations, sous l’onglet **Appartenance**, passez en revue les paramètres.
7. Sélectionnez le menu **Sélectionner le rôle**, puis **Administrateur de conformité**. Vous pouvez utiliser le filtre **Rechercher un rôle par nom** pour vous aider à localiser un rôle.
8. Sous **Sélectionner des membres**, sélectionnez **Aucun membre sélectionné**.
9. Dans le volet Sélectionner un membre, sélectionnez votre compte d’administrateur, puis sélectionnez **Sélectionner**.
10. Dans l’écran Ajouter des affectations, sélectionnez **Suivant**.
11. Sous l’onglet Paramètres , sous **type d’affectation**, passez en revue les options disponibles. Pour cette tâche, utilisez le paramètre par défaut.
  - Les attributions éligibles nécessitent que le membre du rôle effectue une action pour utiliser le rôle. Les actions peuvent inclure l’exécution d’une vérification de l’authentification multifacteur (MFA), la fourniture d’une justification métier ou la demande d’approbation auprès d’approbateurs désignés.
  - Les affectations actives ne nécessitent pas que le membre effectue une action pour utiliser le rôle. Les membres affectés comme actifs ont toujours les privilèges attribués au rôle.

12. Passez en revue les paramètres restants, puis sélectionnez **Affecter**.

### Activer vos rôles Entra

Lorsque vous devez assumer un rôle Entra, vous pouvez demander l’activation en ouvrant **Mes rôles** dans Privileged Identity Management.

1. Dans l’écran Privileged Identity Management, dans le menu de navigation de gauche, sélectionnez **Mes rôles.**
2. Dans le volet Mes rôles, passez en revue la liste des affectations éligibles.
3. Dans la ligne du rôle Administrateur de conformité, sélectionnez **Activer**.
4. Dans le volet Activer – Administrateur de conformité, sélectionnez **vérification supplémentaire requise,** puis suivez les instructions pour fournir une vérification de sécurité supplémentaire. Vous devez vous authentifier une seule fois par session.
5. Une fois la vérification de sécurité terminée, dans le volet Activer – Administrateur de conformité, dans la zone **Motif**, entrez la justification de l’activation de ce rôle.
6. Sélectionnez **Activer**.

### Attribuer un rôle avec une étendue restreinte

Pour certains rôles, l’étendue des autorisations accordées peut être limitée à une seule unité d’administration, un principal de service ou une application. Cette procédure est un exemple si vous attribuez un rôle qui a l’étendue d’une unité administrative.

1. Dans l’écran Privileged Identity Management, dans le volet de navigation de gauche, sélectionnez **Rôles Entra**.
2. Dans le volet Rôles, dans le menu supérieur, sélectionnez **+ Ajouter des affectations.**
3. Dans l’écran Ajouter des affectations, sélectionnez le menu **Sélectionner le rôle**, puis sélectionnez **administrateur d'utilisateur.**
4. Sélectionnez le menu de type d'étendue  et passez en revue les options disponibles. Pour l’instant, vous allez utiliser le type d’étendue **Directory**.  Conseil Accédez à [Gérer les unités administratives dans Entra ID](https://learn.microsoft.com/fr-fr/azure/active-directory/roles/administrative-units) pour trouver plus d’informations sur le type d’étendue de l’unité administrative.
5. Similaire à l’attribution d’un rôle sans étendue restreinte. Ajoutez des membres et terminez les options de paramètres. Pour l’instant, sélectionnez **Annuler**.

### Mettre à jour ou supprimer une attribution de rôle existante

Suivez ces étapes pour mettre à jour ou supprimer une attribution de rôle existante.

1. Dans l’écran Ouvrir Entra Privileged Identity Management, puis Rôles Entra, dans le volet de navigation de gauche, sélectionnez **Attributions**.
2. Dans la liste **Affectations**, pour l’Administrateur de la conformité, passez en revue les options de la colonne **Action** .
3. Sélectionnez **mettre à jour** et passez en revue les options disponibles dans le volet Paramètres d’appartenance. Une fois terminé, fermez le volet.
4. Sélectionnez **Supprimer**.
5. Dans la boîte de dialogue **Supprimer**, passez en revue les informations, puis sélectionnez **Oui**.


## Exercice pour assigner des rôles de ressources Azure dans la Gestion des Identités Privilégiées

### Attribuer des rôles de ressources Azure

Entra Privileged Identity Management (PIM) peut gérer les rôles de ressources Azure intégrés, ainsi que les rôles personnalisés, notamment (mais pas limité à) :

- Propriétaire
- Administrateur de l’accès utilisateur
- Contributeur
- Administrateur de sécurité
- Gestionnaire de sécurité

Suivez ces étapes pour rendre un utilisateur éligible à un rôle de ressource Azure.

1. Connectez-vous au centre d’administration Entra  en tant qu’administrateur client.
2. Recherchez, puis sélectionnez **Entra Privileged Identity Management.**
3. Dans le menu Privileged Identity Management, dans le volet de navigation gauche, sélectionnez **ressources Azure.**
4. Dans le menu supérieur, sélectionnez **Découvrir les ressources**.
5. Dans l’écran Ressources Azure – Découverte, sélectionnez votre abonnement, puis, dans le menu supérieur, sélectionnez **Gérer la ressource**.
6. Dans la boîte de dialogue **Intégration de la ressource sélectionnée pour la gestion**, passez en revue les informations, puis sélectionnez **OK**.
7. Une fois l’intégration terminée, fermez les ressources Azure – Écran découverte.
8. Dans l’écran ressources Azure, sélectionnez la ressource que vous venez d’ajouter.
9. Dans le menu de navigation de gauche, sous **Gérer**, sélectionnez **Rôles** pour afficher la liste des rôles pour les ressources Azure.
10. Dans le menu supérieur, sélectionnez + **Ajouter des tâches**.
11. Dans la boîte de dialogue **Ajouter des affectations**, sélectionnez le menu **Sélectionner un rôle**, puis sélectionnez **Contributeur du service gestion des API.**
12. Sous **Sélectionner des membres**, sélectionnez **Aucun membre sélectionné**.
13. Dans le volet Sélectionner un membre ou un groupe, sélectionnez un compte à partir de votre organisation qui sera affecté au rôle.
14. Sélectionnez **puis suivant**.
15. Dans l'onglet **Paramètres**, sous **Type d'affectation**, sélectionnez **Éligible**.
  - Les attributions **éligibles** exigent des membres qu’ils effectuent une action pour utiliser ce rôle. Les actions peuvent inclure l’exécution d’une vérification de l’authentification multifacteur (MFA), la fourniture d’une justification métier ou la demande d’approbation auprès d’approbateurs désignés.
  - Les attributions de membres **actifs** n’exigent pas des membres qu’ils effectuent une action pour utiliser ce rôle. Les membres affectés comme actifs ont toujours les privilèges attribués au rôle.

16. Spécifiez une durée d’affectation en modifiant les dates et heures de début et de fin.
17. Lorsque vous avez terminé, sélectionnez **Attribuer**.
18. Une fois la nouvelle attribution de rôle créée, une notification d’état s’affiche.

### Mettre à jour ou supprimer une attribution de rôle de ressource existante

Suivez ces étapes pour mettre à jour ou supprimer une attribution de rôle existante.

1. Ouvrez **Entra Privileged Identity Management**.
2. Sélectionnez **Ressources Azure**.
3. Sélectionnez la ressource que vous souhaitez gérer pour ouvrir sa page de vue d’ensemble.
4. Sous **Gérer**, sélectionnez **Attributions**.
5. Sous l’onglet **Rôles éligibles**, dans la colonne Action, passez en revue les options disponibles.
6. Sélectionnez **Supprimer**.
7. Dans la boîte de dialogue **Supprimer**, passez en revue les informations, puis sélectionnez **Oui**.


## Planifier et configurer des groupes d’accès privilégiés

Dans Privileged Identity Management (PIM), vous pouvez désormais attribuer l’éligibilité à l’appartenance ou à la propriété des groupes d’accès privilégiés. Vous pouvez affecter des rôles intégrés d’ID Entra aux groupes cloud et utiliser PIM pour gérer l’éligibilité et l’activation des membres du groupe et des propriétaires. Avec la préversion des groupes d’accès privilégié, vous pouvez accorder aux administrateurs spécifiques à une charge de travail un accès rapide à plusieurs rôles avec une seule requête juste-à-temps.

**Exemple** : vos **administrateurs Office de niveau 0** peuvent avoir besoin d’un accès juste-à-temps à **l’administrateur Exchange**, à **l’administrateur Office**, à **l’administrateur Teams** et aux rôles **d’administrateur de recherche** pour examiner minutieusement les incidents quotidiennement.

Vous pouvez créer un groupe assignable de rôles appelé « Administrateurs Office de niveau 0 », puis le rendre éligible à l’attribution des quatre rôles mentionnés précédemment (ou de tous les rôles intégrés Entra). Ensuite, vous l’activez pour l’accès privilégié dans la section Activité du groupe. Une fois activé pour l’accès privilégié, vous pouvez affecter vos administrateurs et propriétaires au groupe. Lorsque les administrateurs élèvent le groupe aux rôles, votre personnel dispose des autorisations des quatre rôles Entra.

### Exiger des stratégies différentes pour chaque groupe assignable de rôle

Certaines organisations utilisent des outils comme Entra business-to-business (B2B) collaboration pour inviter leurs partenaires en tant qu’invités à leur organisation Entra. Au lieu d’utiliser une seule stratégie juste-à-temps pour toutes les attributions à un rôle privilégié, vous pouvez créer deux groupes d’accès privilégié différents avec leurs propres stratégies. Vous pouvez appliquer des exigences moins strictes à vos employés de confiance, et des exigences plus strictes, comme un flux de travail d'approbation, à vos partenaires lorsqu'ils demandent l'activation dans le rôle qui leur est attribué.

## Analyser l’historique et les rapports d’audit Privileged Identity Management

Avec PIM, vous pouvez afficher l’activité, les activations et l’historique d’audit pour les membres et les propriétaires de groupe d’accès privilégié au sein de votre organisation Entra.

Si votre organisation a externalisé des fonctions de gestion à un fournisseur de services qui utilise [la gestion des ressources déléguées Azure](https://learn.microsoft.com/fr-fr/azure/lighthouse/concepts/azure-delegated-resource-management), les attributions de rôles autorisées par ce fournisseur n’apparaîtront pas ici.

Suivez ces étapes pour afficher l’historique d’audit des groupes d’accès privilégiés.

### Afficher l’historique d’audit des ressources

### **L’audit des ressources** vous donne une vue de toutes les activités associées à vos groupes d’accès privilégiés.

1. Ouvrez **Entra Privileged Identity Management**.
2. Sélectionnez **Groupes**.
3. Sélectionnez le groupe d’accès privilégié pour lequel vous souhaitez afficher l’historique d’audit.
4. Sous **Activité**, sélectionnez **Audit des ressources**.
5. Filtrez l’historique à l’aide d’une date prédéfinie ou d’une plage personnalisée.

### Afficher mon audit

**Mon audit** vous permet d’afficher votre activité de rôle personnel pour un groupe d’accès privilégié.

1. Ouvrez **Entra Privileged Identity Management**.
2. Sélectionnez **Groupes**.
3. Sélectionnez le groupe d’accès privilégié pour lequel vous souhaitez afficher l’historique d’audit.
4. Sous **Activité**, sélectionnez **Mon audit**.
5. Filtrez l’historique à l’aide d’une date prédéfinie ou d’une plage personnalisée.


## Créer et gérer des comptes d’accès d’urgence

Il est important que vous empêchez d’être verrouillé accidentellement hors de votre ID Entra. Avec l’ID Entra, vous ne pouvez pas vous connecter ni activer le compte d’un autre utilisateur en tant qu’administrateur. Vous pouvez atténuer le risque d’absence accidentelle d’accès administratif. Le secret, créez au moins deux comptes d’accès d’urgence  dans votre organisation.

Les comptes d’accès d’urgence sont hautement privilégiés et ne sont pas attribués à des personnes spécifiques. Les comptes d’accès d’urgence sont réservés aux situations d'urgence ou de « dernière chance » où les comptes administratifs habituels ne peuvent pas être utilisés. Nous vous recommandons de restreindre l’accès au compte d’urgence. Utilisez les comptes uniquement quand il est nécessaire.

Cet article fournit des instructions pour la gestion des comptes d’accès d’urgence dans Entra ID.

### Pourquoi utiliser un compte d’accès d’urgence

Une organisation peut avoir besoin d’utiliser un compte d’accès d’urgence dans les situations suivantes :

- Les comptes d’utilisateur sont fédérés et la fédération n’est actuellement pas disponible en raison d’une panne de réseau cellulaire ou d’une panne de fournisseur d’identité. Par exemple, si l’hôte du fournisseur d’identité dans votre environnement est tombé en panne, les utilisateurs risquent de ne pas pouvoir se connecter lorsque l’ID Entra redirige vers son fournisseur d’identité.
- Les administrateurs sont inscrits via l’authentification multifacteur Entra. Tous leurs appareils individuels ne sont pas disponibles ou le service n’est pas disponible. Les utilisateurs peuvent ne pas pouvoir terminer l’authentification multifacteur pour activer un rôle. Par exemple, une panne de réseau cellulaire empêche les personnes de répondre aux appels téléphoniques ou de recevoir des sms. Surtout quand ces méthodes d’authentification sont les deux seuls mécanismes d’authentification qu’ils ont inscrits.
- La personne disposant de l’accès administrateur général le plus récent a quitté l’organisation. Entra ID empêche la suppression du dernier compte d’administrateur général, mais il n’empêche pas le compte d’être supprimé ou désactivé localement. L’une ou l’autre situation peut rendre l’organisation incapable de récupérer le compte.
- Des circonstances imprévues telles qu’une urgence naturelle en cas de catastrophe naturelle, pendant lesquelles un téléphone mobile ou d’autres réseaux peuvent être indisponibles.

### Créer des comptes d’accès d’urgence

Créez deux comptes d’accès d’urgence ou plus. Ces comptes doivent être des comptes cloud uniquement qui utilisent le domaine .onmicrosoft.com et qui ne sont pas fédérés ou synchronisés à partir d’un environnement local.

Lorsqu’un administrateur configure des comptes d’urgence, les exigences suivantes doivent être remplies :

- Les comptes d’accès d’urgence ne doivent pas être associés à un utilisateur individuel de l’organisation. Vérifiez que vos comptes ne sont pas connectés à des téléphones mobiles fournis par les employés, à des jetons matériels qui voyagent avec des employés individuels, ni à d’autres informations d’identification spécifiques aux employés. Cette précaution couvre les cas où un employé individuel est inaccessible lorsque les informations d’identification sont nécessaires. Tous les appareils inscrits doivent être conservés à un emplacement connu et sécurisé. Ces emplacements ont besoin de plusieurs moyens de communication avec l’ID Entra.
- Le mécanisme d’authentification utilisé pour un compte d’accès d’urgence doit être distinct. Séparez-le de celui utilisé par vos autres comptes d’administration, y compris d’autres comptes d’accès d’urgence. Par exemple, si votre connexion administrateur normale se fait via une authentification multifacteur sur site, un autre mécanisme d'authentification multifacteur serait utilisé. Toutefois, si l’authentification multifacteur est votre principale partie de l’authentification pour vos comptes d’administration, envisagez une approche différente pour les comptes d’urgence. Essayez des éléments tels que l’utilisation de l’accès conditionnel avec un fournisseur MFA tiers via des contrôles personnalisés.
- L'appareil ou les informations d'identification ne doivent pas expirer ou faire partie du processus automatisé d'effacement en raison d'un manque d'utilisation.
- Vous devez rendre l’attribution de rôle Administrateur général permanente pour vos comptes d’accès d’urgence.

#### Exclure au moins un compte de l’authentification multifacteur basée sur un téléphone

Pour réduire le risque d’une attaque résultant d’un mot de passe compromis, Entra ID vous recommande d’exiger l’authentification multifacteur pour tous les utilisateurs individuels. Ce groupe comprend les administrateurs et tous les autres (par exemple, les agents financiers) dont le compte compromis aurait une occasion importante de causer des dommages.

Toutefois, au moins l’un de vos comptes d’accès d’urgence ne doit pas avoir le même mécanisme d’authentification multifacteur que vos autres comptes d’urgence. Cela inclut des solutions d’authentification multifacteur tierces. Vous avez peut-être une stratégie d’accès conditionnel qui exige l’authentification multifacteur pour chaque administrateur d’Entra ID et des autres applications SaaS (Software as a Service). Excluez alors les comptes d’accès d’urgence de cette exigence et configurez un autre mécanisme à la place. En outre, vous devez vous assurer que les comptes n’ont pas de stratégie d’authentification multifacteur par utilisateur.

#### Exclure au moins un compte des stratégies d’accès conditionnel

Lors d’une urgence, vous ne souhaitez pas qu’une stratégie bloque potentiellement votre accès pour résoudre un problème. Au moins un compte d’accès d’urgence doit être exclu de toutes les stratégies d’accès conditionnel.

### Conseils de fédération

Les organisations qui utilisent ad Domain Services et ADFS, ou un fournisseur d’identité similaire, pour fédérer à Entra ID disposent d’une autre option : configurer un compte d’accès d’urgence dont la revendication MFA peut être fournie par ce fournisseur d’identité. Par exemple, le compte d’accès d’urgence peut être soutenu par un certificat et une paire de clés, comme celle stockée sur une carte à puce. Lorsque cet utilisateur est authentifié auprès d’AD, ADFS peut fournir une revendication à Entra ID indiquant que l’utilisateur a satisfait aux exigences de l’authentification multifacteur. Même avec cette approche, les organisations doivent toujours avoir des comptes d’accès d’urgence basés sur le cloud si la fédération ne peut pas être établie.

### Surveiller les journaux de connexion et d’audit

Les organisations doivent surveiller l’activité de connexion et de journal d’audit à partir des comptes d’urgence et déclencher des notifications à d’autres administrateurs. Lorsque vous surveillez l’activité sur les comptes de secours, vous pouvez vérifier si ces comptes sont utilisés uniquement pour les tests ou les urgences réelles. Vous pouvez utiliser Azure Log Analytics pour surveiller les journaux de connexion et déclencher des alertes à vos administrateurs par e-mail et SMS lorsque les comptes de dernier recours se connectent.

### Valider régulièrement les comptes

Lorsque vous entraînez les membres du personnel à utiliser des comptes d’accès d’urgence et que vous validez les comptes d’accès d’urgence, effectuez au minimum les étapes suivantes à intervalles réguliers :

- Assurez-vous que le personnel de surveillance de la sécurité est conscient que l’activité de vérification des comptes est en cours.
- Assurez-vous que le processus d'urgence pour utiliser ces comptes est documenté et à jour.
- Assurez-vous que les administrateurs et les agents de sécurité qui peuvent avoir besoin d’effectuer ces étapes pendant une urgence sont formés sur le processus.
- Mettez à jour les informations d’identification de vos comptes d’accès d’urgence, en particulier les mots de passe. Vérifiez ensuite que ces comptes peuvent se connecter et effectuer des tâches administratives.
- Assurez-vous que les utilisateurs n’ont pas inscrit l’authentification multifacteur ou la réinitialisation de mot de passe en libre-service (SSPR) sur l’appareil ou les détails personnels de chaque utilisateur.
- Si les comptes sont inscrits pour l’authentification multifacteur sur un appareil, pour une utilisation lors de la connexion ou de l’activation du rôle, assurez-vous que cet appareil est accessible à tous les administrateurs susceptibles d’en avoir besoin lors d’une urgence. Vérifiez également que l’appareil peut communiquer via au moins deux chemins réseau qui ne partagent pas de mode d’échec commun. Par exemple, l’appareil peut communiquer avec Internet par le biais du réseau sans fil d’une installation et d’un réseau de fournisseurs de cellules.

Ces étapes doivent être effectuées à intervalles réguliers et pour les modifications clés :

- Au moins tous les 90 jours
- Lorsqu’il y a eu un changement récent dans le personnel informatique, tel qu’un changement d’emploi, un départ ou un nouvel employé
- Lorsque les abonnements Entra dans l’organisation ont changé


## Évaluation du module

Choisissez la meilleure réponse à chacune des questions ci-dessous.

### Contrôler vos connaissances


## Résumé et ressources

Maintenant que vous avez passé en revue ce module, vous pouvez :

- Définissez une stratégie d’accès privilégié pour les utilisateurs administratifs (ressources, rôles, approbations, seuils).
- Configurez PIM pour les rôles Entra.
- Configurez PIM pour les ressources Azure.
- Attribuer des rôles.
- Gérer les demandes PIM.
- Analysez l’historique et les rapports d’audit PIM.
- Créez et gérez des comptes d’accès d’urgence.
- Configurer des groupes d’accès privilégiés

Dans ce module, vous avez appris à développer une stratégie d’accès privilégié. Cela inclut des étapes telles que l’identification des parties prenantes, la détermination des attributions de rôles et l’identification des groupes à attribuer des rôles. Vous avez attribué des rôles Entra dans PIM et appris à analyser l’historique et les rapports d’audit. Avec cette nouvelle connaissance, vous pouvez désormais implémenter un accès privilégié dans votre organisation.

### Ressources

Pour en savoir plus sur ces rubriques, consultez ces liens.

- [Élever l’accès pour gérer tous les abonnements Azure](https://learn.microsoft.com/fr-fr/azure/role-based-access-control/elevate-access-global-admin)
- [Révisions d’accès pour les ressources Azure](https://learn.microsoft.com/fr-fr/azure/active-directory/privileged-identity-management/pim-resource-roles-start-access-review)
- [Comptes d’accès d’urgence](https://learn.microsoft.com/fr-fr/azure/active-directory/roles/security-emergency-access)
- [Fonctionnalités de gestion pour les groupes d’accès privilégié](https://learn.microsoft.com/fr-fr/azure/active-directory/privileged-identity-management/groups-features)


---

# Surveiller et gérer Entra ID

_https://learn.microsoft.com/fr-fr/training/modules/monitor-maintain-azure-active-directory/_


## Présentation

Les journaux d'audit et de diagnostic d’Entra ID fournissent une vue détaillée de la façon dont les utilisateurs accèdent à votre solution Azure. Découvrez comment surveiller, dépanner et analyser les données de connexion.

### Objectifs d’apprentissage

À la fin de ce module, vous pouvez :

- Analyser et examiner les journaux de connexion pour résoudre les problèmes d’accès.
- Examinez et surveillez les journaux d’audit Entra.
- Activez et intégrez les journaux de diagnostic Entra avec Log Analytics/Microsoft Sentinel.
- Exporter les journaux de connexion et d’audit vers une SIEM tierce.
- Examinez les activités Entra à l’aide de Log Analytics/Microsoft Sentinel, en excluant l’utilisation de KQL.
- Analysez des classeurs et des rapports Entra.
- Surveillez la posture de sécurité avec le score d'identité sécurisée.
- configurer les notifications.

### Prérequis

Aucun


## Analyser et examiner les journaux de connexion pour résoudre les problèmes d’accès

L'architecture de génération de rapports dans Entra ID se compose des composants suivants :

- **Activité**
  - **Connexions** : Il s’agit d’informations sur l’utilisation des applications managées et les activités de connexion des utilisateurs.
  - **Journaux d’audit** : Fournissent des informations sur les activités du système liées aux utilisateurs et à la gestion des groupes, les applications gérées et les activités de répertoire.
  - **Les journaux de provisionnement** : ils permettent aux clients de superviser l’activité du service de provisionnement, par exemple la création d’un groupe dans ServiceNow ou l’importation d’un utilisateur à partir de Workday.

- **Sécurité**
  - **Connexions risquées** : Une connexion risquée signale une tentative de connexion par une personne qui n’est pas le propriétaire légitime d’un compte d’utilisateur.
  - **Utilisateurs avec indicateur de risque** : Un utilisateur à risque indique qu’un compte d’utilisateur est susceptible d’avoir été compromis.

#### Qui peut accéder aux données ?

- Utilisateurs dans les rôles Administrateur de sécurité, Lecteur de sécurité ou Administrateur, Lecteur général et Lecteur de rapport
- Tous les utilisateurs (non administrateurs) peuvent accéder à leurs propres connexions

#### De quelle licence Entra avez-vous besoin pour accéder à l'activité de connexion ?

Le rapport relatif à l’activité de connexion est disponible dans toutes les éditions d’Entra ID, mais également accessible par l’API Microsoft Graph.

### Rapport de connexions

Le rapport de connexions des utilisateurs permet de répondre aux questions suivantes :

- Quel est le modèle de connexion d’un utilisateur ?
- Combien d’utilisateurs se sont connectés au cours d’une semaine ?
- Quel est l’état de ces connexions ?

Dans le menu du Portail Azure, sélectionnez **Entra ID** ou recherchez et sélectionnez **Entra ID** dans n’importe quelle page.

Sous **Surveillance**, sélectionnez **Connexions** pour ouvrir le Rapport de connexions.

Deux heures peuvent s'écouler avant que les enregistrements de connexion n'apparaissent dans le portail.

Important

Le rapport des connexions montre seulement les connexions interactives, c’est-à-dire les connexions où un utilisateur se connecte manuellement avec son nom d’utilisateur et son mot de passe. Les connexions non interactives, comme l’authentification de service à service, n’apparaissent pas dans le rapport des connexions.

Un journal de connexions comporte un affichage de liste par défaut qui indique :

- Date de la connexion
- Utilisateur associé
- L’application à laquelle l’utilisateur s’est connecté
- État de la connexion
- État de la détection de risque
- État de l’exigence de l’authentification multifacteur (MFA)

Vous pouvez personnaliser la vue de liste en sélectionnant Colonnes dans la barre d’outils.

La boîte de dialogue Colonnes vous permet d’accéder aux attributs sélectionnables. Dans un rapport de connexion, vous ne pouvez pas avoir de champs qui contiennent plusieurs valeurs pour une demande de connexion donnée sous forme de colonne. C’est par exemple le cas pour les détails d’authentification, les données d’accès conditionnel et l’emplacement réseau.

Sélectionnez un élément dans la vue sous forme de liste pour obtenir des informations plus détaillées.

Les clients peuvent maintenant résoudre les problèmes de stratégies d’accès conditionnel grâce à tous les rapports de connexion. Lorsqu’un administrateur sélectionne l’onglet Accès conditionnel pour obtenir un rapport de connexion, les clients peuvent examiner l’état de l’accès conditionnel. Ils consultent aussi en détail les stratégies applicables à la connexion et les résultats de chacune. Pour en savoir plus, consultez le [Forum aux questions sur les informations de l’accès conditionnel dans toutes les connexions](https://learn.microsoft.com/fr-fr/azure/active-directory/reports-monitoring/reports-faq).

### Filtrer les activités de connexion

Commencez par réduire les données signalées jusqu’au niveau qui vous convient. Ensuite, filtrez les données de connexions en utilisant le champ de date comme filtre par défaut. Entra ID fournit une large gamme de filtres supplémentaires que vous pouvez définir :

**ID de demande** : ID de la demande qui vous intéresse.

**Utilisateur** : nom ou nom d’utilisateur principal (UPN) de l’utilisateur qui vous intéresse.

**Application** : nom de l’application cible.

**État** – État de la connexion qui vous intéresse :

- Réussite
- Défaillance
- Interrompue

**Adresse IP** : adresse IP de l’appareil utilisé pour se connecter à votre locataire.

**Emplacement** : emplacement à partir duquel la connexion a été établie :

- Ville
- État/Province
- Pays/région

**Ressource** : nom du service utilisé pour la connexion.

**ID de ressource** : ID du service utilisé pour la connexion.

**Application cliente** – Type de l’application cliente utilisée pour se connecter à votre locataire :

| **Name** (Nom) | **Authentification moderne** | **Description** |
|---|---|---|
| SMTP authentifié |   | Utilisé par les clients POP et IMAP pour envoyer des e-mails. |
| Découverte automatique |   | Utilisé par les clients Outlook et EAS pour rechercher des boîtes aux lettres dans Exchange Online et s’y connecter. |
| Exchange ActiveSync |   | Ce filtre affiche toutes les tentatives de connexion où le protocole EAS a été utilisé. |
| Navigateur | Oui | Affiche toutes les tentatives de connexion d’utilisateurs à l’aide de navigateurs web. |
| Exchange ActiveSync |   | Affiche toutes les tentatives de connexion d’utilisateurs avec des applications clientes utilisant Exchange ActiveSync pour se connecter à Exchange Online. |
| Exchange Online PowerShell |   | Utilisé pour se connecter à Exchange Online à l’aide de PowerShell à distance. Si vous bloquez l’authentification de base pour Exchange Online PowerShell, vous devez utiliser le module Exchange Online PowerShell pour vous connecter. |
| Exchange Web Services |   | Interface de programmation utilisée par Outlook, Outlook pour Mac et des applications tierces. |
| IMAP4 |   | Un client de messagerie hérité qui utilise IMAP pour récupérer le courrier électronique. |
| MAPI sur HTTP |   | Utilisé par Outlook 2010 et versions ultérieures. |
| Applications mobiles et clients de bureau | Oui | Affiche toutes les tentatives de connexion d’utilisateurs à l’aide d’applications mobiles et de clients de bureau. |
| Carnet d’adresses hors connexion |   | Copie des collections de listes d’adresses téléchargées et utilisées par Outlook. |
| Outlook Anywhere (RPC sur HTTP) |   | Utilisé par Outlook 2016 et versions antérieures. |
| Service Outlook |   | Utilisé par l’application Courrier et Calendrier pour Windows 10. |
| POP3 |   | Un client de messagerie hérité qui utilise POP3 pour récupérer le courrier électronique. |
| Reporting Web Services |   | Utilisé pour récupérer des données de rapports dans Exchange Online. |
| Autres clients |   | Affiche toutes les tentatives de connexion d’utilisateurs où l’application cliente n’est pas incluse ou connue. |

**Système d’exploitation** : le système d’exploitation s’exécutant sur l’appareil a utilisé l’authentification auprès de votre locataire.

**Navigateur de l’appareil** : Si la connexion a été lancée à partir d’un navigateur, ce champ vous permet de filtrer par nom de navigateur.

**ID de corrélation** : ID de corrélation de l’activité.

**Accès conditionnel** : état des règles d’accès conditionnel appliquées.

- **Non appliqué** : aucune stratégie n’est appliquée à l’utilisateur et à l’application lors de la connexion.
- **Réussite** : une ou plusieurs stratégies d’accès conditionnel sont appliquées à l’utilisateur et à l’application (mais pas nécessairement les autres conditions) lors de la connexion.
- **Échec** : la connexion a satisfait à la condition d’utilisateur et d’application d’au moins une stratégie d’accès conditionnel, et les contrôles d’octroi ne sont pas satisfaits ou ne sont pas configurés pour bloquer l’accès.

### Télécharger les activités de connexion

Sélectionnez l’option **Télécharger** pour créer un fichier CSV ou JSON des 250 000 enregistrements les plus récents. Commencez par **Télécharger des connexions** si vous souhaitez utiliser les données en dehors du portail Azure.

Important

Le nombre d'enregistrements que vous pouvez télécharger est limité par les [politiques de rétention de rapport Entra ID](https://learn.microsoft.com/fr-fr/azure/active-directory/reports-monitoring/reference-reports-data-retention).

### Raccourcis vers les données de connexions

Entra ID et le Portail Azure vous offrent d’autres points d’entrée pour accéder aux données de connexions :

- Identity Protection dans Entra ID – Sécurité – Identity Protection
- Utilisateurs
- Groupes
- Applications d’entreprise

#### Données des connexions des utilisateurs dans Identity Protection

Le graphique des connexions des utilisateurs figurant sur la page de présentation **Identity Protection** affiche les agrégations hebdomadaires des connexions. La période par défaut est de 30 jours.

Lorsque vous sélectionnez un jour dans le graphique des connexions, vous obtenez une liste détaillée des activités de connexion correspondantes.

Chaque ligne de la liste des activités de connexion affiche :

- Qui s’est connecté ?
- Quelle application a été la cible de la connexion ?
- Quel est l’état de la connexion ?
- Quel est l’état MFA de la connexion ?

Lorsque l’administrateur sélectionne un lien, vous obtenez plus d’informations sur l’opération de connexion :

- Identifiant utilisateur
- Utilisateur
- Nom d’utilisateur
- ID d’application
- Application
- Client
- Emplacement
- Adresse IP
- Date
- MFA obligatoire
- État de la connexion  Remarque Les adresses IP sont émises de manière à ce qu’il n’existe aucun lien définitif entre une adresse IP et l’emplacement physique de l’ordinateur qui l’utilise. Le mappage des adresses IP est également compliqué parce que les fournisseurs mobiles et les VPN émettent des adresses IP à partir de pools centraux, souvent très éloignés de l’endroit où l’appareil client est réellement utilisé. Pour le moment, la conversion de l’adresse IP en emplacement physique reste la meilleure solution pour les suivis, les données de registre, les recherches inversées et les autres informations des rapports Entra.

Sur la page **Utilisateurs**, vous obtenez une vue d’ensemble complète de toutes les connexions des utilisateurs en sélectionnant **Connexions** dans la section **Activité**.

### Utilisation des applications gérées

En disposant d’une vue centrée sur les applications de vos données de connexion, vous pouvez répondre aux questions telles que :

- Qui utilise mes applications ?
- Quelles sont les trois principales applications dans mon organisation ?
- Comment fonctionne mon application la plus récente ?

Le point d’entrée de ces données correspond aux trois principales applications de votre organisation. Les données sont contenues dans le rapport sur les 30 derniers jours dans la section **Vue d’ensemble** sous **Applications d’entreprise**.

Les graphiques d’utilisation des applications affiche les agrégations hebdomadaires des connexions pour vos trois principales applications au cours d’une période donnée. La valeur par défaut de cette période est de 30 jours.

Si vous le souhaitez, vous pouvez définir la focalisation sur une application spécifique.

Lorsque vous sélectionnez un jour dans le graphique d’utilisation des applications, vous obtenez une liste détaillée des activités de connexion.

L’option **Connexions** vous fournit une vue d’ensemble complète de tous les événements de connexion à vos applications.

### Journaux d’activité Microsoft 365

Vous pouvez consulter les journaux d’activité Microsoft 365 dans le centre d’administration Microsoft 365. Les journaux d’activité de Microsoft 365 et d’Entra partagent un nombre important de ressources de l’annuaire. Seul le centre d’administration Microsoft 365 fournit une vue complète des journaux d’activité d’Microsoft 365.

Vous pouvez également accéder par programme aux journaux d’activité de Microsoft 365 en utilisant les API de gestion Microsoft 365.


## Examiner et surveiller les journaux d’audit Entra

Les journaux d’audit Entra fournissent des enregistrements des activités du système pour la conformité. Pour accéder au rapport d’audit, sélectionnez **Journaux d’audit** dans la section **Supervision** de **Entra ID**.

Un journal de connexions comporte un affichage de liste par défaut qui indique :

- Date et heure de l’événement
- Service qui a enregistré l’occurrence
- Catégorie et nom de l’activité (*laquelle*)
- État de l’activité (réussite ou échec)
- Cible
- Initiateur/intervenant d’une activité (qui)

Vous pouvez personnaliser le mode Liste en cliquant sur **Colonnes** dans la barre d’outils.

Les colonnes personnalisées vous permettent d’afficher d’autres champs ou de supprimer des champs déjà affichés.

Sélectionnez un élément dans la vue sous forme de liste pour obtenir des informations plus détaillées.

### Filtrage des journaux d’audit

Vous pouvez filtrer les données d’audit des champs suivants :

- Service
- Category
- Activité
- Statut
- Cible
- Initié par (intervenant)
- Plage de dates

Le filtre **Service** vous permet de sélectionner les services suivants dans une liste déroulante :

- Tous
- Expérience utilisateur microsoft Entra Management
- Révisions d’accès
- Approvisionnement des comptes
- Application Proxy (Proxy d’application)
- Méthodes d’authentification
- Business to Customer (B2C)
- Accès conditionnel
- Annuaire principal
- Gestion des droits d’utilisation
- Authentification hybride
- Protection de l’identité
- Utilisateurs invités
- Service MIM
- MyApps
- Privileged Identity Management (PIM)
- Gestion des groupes en libre-service
- Gestion des mots de passe en libre-service
- Conditions d’utilisation

Le filtre **Catégorie** vous permet de sélectionner un des filtres suivants :

- Tous
- Unité administrative
- ApplicationManagement
- Authentification
- Autorisation
- Contact
- Appareil
- DeviceConfiguration
- DirectoryManagement
- EntitlementManagement
- GroupManagement
- KerberosDomain
- KeyManagement
- Étiquette
- Autres
- PermissionGrantPolicy
- Stratégie
- ResourceManagement
- RoleManagement
- UserManagement

Le filtre **Activité** est basé sur la catégorie et le type de ressource d’activité que vous choisissez. Vous pouvez sélectionner une activité spécifique que vous souhaitez voir ou toutes les choisir.

Vous pouvez récupérer la liste de toutes les activités d’audit en utilisant l’API Graph : `https://graph.windows.net/<tenantdomain>/activities/auditActivityTypesV2?api-version=beta`

Le filtre **État** vous permet de filtrer en fonction de l’état d’une opération d’audit. L’état peut être l’une des valeurs suivantes :

- Tous
- Succès
- Échec

Le filtre **Cible** vous permet de rechercher une cible donnée par début de nom ou de nom d’utilisateur principal (UPN). Le nom et le nom d'utilisateur principal cibles sont sensibles à la casse.

Le filtre **Initié par** vous permet de définir le début du nom d’un intervenant ou du nom d’utilisateur principal (UPN). Le nom et le nom d'utilisateur principal sont sensibles à la casse.

Le filtre de **plage de dates** vous permet de définir une période pour les valeurs retournées `data.Possible` :

- 7 jours
- 24 heures
- Custom

Lorsque vous sélectionnez une plage personnalisée, vous pouvez configurer une heure de début et une heure de fin.

Vous pouvez également télécharger les données filtrées, jusqu’à 250 000 enregistrements, en sélectionnant le bouton **Télécharger**. Vous pouvez télécharger les journaux d’activité au format CSV ou JSON. Le nombre d’enregistrements que vous pouvez télécharger est limité par les stratégies de rétention de rapport Entra.

### Raccourcis de journaux d’audit

Outre **l’ID Entra**, le portail Azure vous fournit deux autres points d’entrée pour auditer les données :

- Utilisateurs et groupes
- Applications d’entreprise

#### Journaux d’audit des utilisateurs et des groupes

Les rapports d’audit basés sur les utilisateurs et les groupes vous permettent d’obtenir des réponses aux questions telles que :

- Quels types de mises à jour ont été appliqués aux utilisateurs ?
- Combien d’utilisateurs ont été modifiés ?
- Combien de mots de passe ont été modifiés ?
- Qu’a fait un administrateur dans un répertoire ?
- Quels sont les groupes qui ont été ajoutés ?
- Existe-t-il des groupes comportant des modifications d’adhésion ?
- Les propriétaires d’un groupe ont-ils été modifiés ?
- Quelles licences ont été affectées à un groupe ou à un utilisateur ?

Si vous souhaitez simplement consulter les données d’audit connexes aux utilisateurs, vous pouvez filtrer l’affichage dans **Journaux d’audit** dans la section **Surveillance** de l’onglet **Utilisateurs**. La catégorie présélectionnée de ce point d'entrée est **UserManagement**.

Si vous souhaitez simplement consulter les données d’audit connexes aux groupes, vous pouvez filtrer l’affichage dans **Journaux d’audit** dans la section **Surveillance** de l’onglet **Groupes**. La catégorie présélectionnée de ce point d'entrée est **GroupManagement**.

#### Journaux d’audit d’applications d’entreprise

Les rapports d’audit basés sur les applications vous permettent d’obtenir des réponses aux questions telles que :

- Quelles applications ont été ajoutées ou mises à jour ?
- Quelles applications ont été supprimées ?
- Le principal de service d’une application a-t-il été modifié ?
- Les noms des applications ont-ils été modifiés ?
- Qui a donné son consentement à une application ?

Si vous souhaitez consulter les données d’audit associées à vos applications, vous pouvez trouver une vue filtrée sous **Journaux d’audit** dans la section **Activité** de l’écran **Applications d’entreprise**. Dans ce point d’entrée, **Applications d’entreprise** est présélectionné comme **Type d'application**.

### Journaux d’activité Microsoft 365

Vous pouvez consulter les journaux d’activité Microsoft 365 dans le centre d’administration Microsoft 365. Même si les journaux d’activité Microsoft 365 et Entra partagent de nombreuses ressources d’annuaire, seul le Centre d’administration Microsoft 365 fournit une vue complète des journaux d’activité Microsoft 365. Vous pouvez également accéder par programme aux journaux d’activité de Microsoft 365 en utilisant les API de gestion Microsoft 365.


## Exercice : connexion de données d’Entra ID à Microsoft Sentinel

Dans cette unité, nous examinons ce qu’est Microsoft Sentinel ?

Un système de gestion des informations et des événements de sécurité (SIEM) agrège et analyse l'activité. Un outil d'orchestration de la sécurité, d'automatisation et de remédiation (SOAR) collecte les données sur les menaces de sécurité et y réagit. Microsoft Sentinel est à la fois un outil SIEM natif Cloud scalable et une solution SOAR. Microsoft Sentinel vous offre une vue d’ensemble de l’organisation, ce qui réduit le stress lié aux attaques de plus en plus sophistiquées, aux volumes croissants d’alertes et aux longs délais de résolution.

- Collectez des données à l’échelle du cloud sur l’ensemble des utilisateurs, des appareils, des applications et des infrastructures, locaux et dans plusieurs clouds.
- Détectez les menaces non détectées précédemment et réduisez les faux positifs en vous appuyant sur l’analytique et les systèmes de renseignement sur les menaces fournis par Microsoft.
- Investiguez les menaces en utilisant l’intelligence artificielle et recherchez les activités suspectes à grande échelle en profitant des années de travail que Microsoft a consacrées à la cybersécurité.
- Répondez aux incidents rapidement avec une orchestration et une automatisation intégrées des tâches courantes.

### Prérequis

- Une licence Entra ID P1 ou P2 est nécessaire pour ingérer des journaux de connexion dans Microsoft Sentinel. Toute licence Entra ID (gratuite/O365/P1/P2) suffit pour ingérer les autres types de journaux. Des frais supplémentaires par gigaoctet peuvent s'appliquer pour Azure Monitor (analytique des journaux d'activité) et Microsoft Sentinel.
- Le rôle Contributeur Microsoft Sentinel doit être attribué à votre utilisateur sur l’espace de travail.
- Votre utilisateur doit se voir attribuer le rôle d’administrateur de sécurité sur le locataire à partir duquel vous souhaitez diffuser les journaux.
- Votre utilisateur doit disposer d’autorisations en lecture et en écriture sur les paramètres de diagnostic Entra pour pouvoir consulter l’état de la connexion.

### Créer et ajouter un espace de travail Microsoft Sentinel

Utilisez ces instructions si vous n’avez pas encore d’espace de travail disponible pour Microsoft Sentinel.

1. Connectez-vous au [portail Microsoft Azure](https://portal.azure.com/) en tant qu’administrateur de locataires.
2. Recherchez et sélectionnez **Microsoft Sentinel**.
3. Dans l’écran Espaces de travail Microsoft Sentinel, dans le menu, sélectionnez **+ Ajouter**. Si vous disposez déjà d’un espace de travail Microsoft Sentinel, vous pouvez le sélectionner et passer à la tâche suivante.
4. Dans l’écran Ajouter Microsoft Sentinel à un espace de travail, sélectionnez **Créer un espace de travail**.
5. Pour créer un espace de travail Log Analytics, fournissez les informations suivantes :    **Paramètre** **Valeur**     Abonnement Utiliser votre abonnement actif.   groupe de ressources Utilisez un groupe de ressources existant ou créez-en un.   Nom Laboratoire-espace de travail-vosinitialesetdate.    L'espace de travail doit être une valeur unique globale.   Niveau tarifaire Paiement à l'utilisation
6. Lorsque vous avez terminé, sélectionnez votre nouvel espace de travail, puis sélectionnez **Ajouter** pour ajouter l’espace de travail à Microsoft Sentinel.

### Connectez-vous à Entra ID

Vous pouvez utiliser un connecteur Microsoft Sentinel intégré pour collecter des données à partir d’Entra ID et les diffuser en continu dans Microsoft Sentinel. Le connecteur vous permet d’envoyer en streaming des [journaux de connexion](https://learn.microsoft.com/fr-fr/azure/active-directory/reports-monitoring/concept-sign-ins) et des [journaux d’audit](https://learn.microsoft.com/fr-fr/azure/active-directory/reports-monitoring/concept-audit-logs).

1. Dans Microsoft Sentinel, dans le menu de navigation à gauche, sous **Configuration**, sélectionnez **Connecteurs de données**.
2. Dans la liste des **Connecteurs de données**, sélectionnez **Entra ID**, puis **Ouvrir la page du connecteur**.
3. Sous **Configuration**, cochez les cases **Journaux de connexion Entra** et **Journaux d'audit**, puis sélectionnez **Appliquer les modifications**.
4. Fermez la page du connecteur Entra ID.


## Exporter les journaux vers un système de gestion des événements et des informations de sécurité tiers

Depuis l’introduction d’Azure Monitor, des Strides significatives ont été apportés pour consolider les services Azure sur un pipeline de journalisation unique. La plupart des principaux services Azure, y compris Azure Resource Manager et Microsoft Defender pour le cloud, ont été intégrés à Azure Monitor et produisent des journaux de sécurité pertinents.

Le processus d’intégration a également été simplifié avec des fonctionnalités clés telles que les outils SIEM : routage des données vers Azure Event Hubs et activation de plusieurs paramètres de diagnostic par ressource. Le travail en vol facilite l’installation et la gestion du routage des journaux dans les environnements Azure volumineux.

Azure est également partenaire des principaux partenaires SIEM pour créer des connecteurs qui obtiennent les données d’Azure Monitor dans ces outils. Ces connecteurs consomment les données qui sont routées vers Azure Event Hubs par Azure Monitor. Il s’agit d’une approche simple, scalable et gérable pour la transmission des données de journal à une application externe, et donc de l’approche recommandée par Microsoft pour l’intégration d’Azure aux outils SIEM.

Nous avons continué à prendre en charge les clients qui utilisent l’outil Azure Log Integration (AzLog) pour s’intégrer à ces mêmes SIEM. AzLog a été initialement publié pour aider les clients à naviguer dans le processus complexe de consolidation, de traduction et de transfert des journaux d’un large éventail de services Azure vers un outil SIEM. À l’époque, Azure Monitor n’existait pas et il y avait très peu de normalisation en ce qui concerne la façon dont les services Azure exposaient les données de journal aux clients. Certaines données vidées dans un compte de stockage, d’autres à exposer une API, etc.

### Recommandations en matière d’intégration

Le tableau ci-dessous indique ce que vous devez faire en fonction des outils SIEM que vous utilisez et de l’état actuel de l’intégration. Seuls les outils SIEM qui étaient officiellement pris en charge par AzLog sont inclus ci-dessous.

| **Outil SIEM** | **Intégrateur de journaux en cours d’utilisation** | **Examen des options d’intégration SIEM en cours** |
|---|---|---|
| Splunk | Commencez à effectuer une migration vers le module complémentaire Azure Monitor pour Splunk. | Utilisez le module complémentaire Azure Monitor pour Splunk. |
| IBM QRadar | Commencez la migration vers Microsoft Azure DSM et le protocole Microsoft Azure Event Hubs, qui sont disponibles au téléchargement sur le site web du support IBM. | Utilisez Microsoft Azure DSM et le protocole Microsoft Azure Event Hubs, qui sont disponibles au téléchargement sur le site web du support IBM. Vous pouvez en savoir plus sur l’intégration à Azure. |
| ArcSight | Le connecteur intelligent ArcSight d’Azure Event Hubs est disponible dans la collection de connecteurs intelligents ArcSight. |   |

### Guide d’intégration

Aujourd’hui, les fonctionnalités d’intégration SIEM d’Azure Monitor ne peuvent pas faire tout ce que l’outil Azure Log Integration peut faire. Voici notre feuille de route pour traiter les lacunes connues entre ce que vous pourriez faire avec Azure Log Integration et ce que vous pouvez accomplir avec Azure Monitor.

**Journaux Entra** : les journaux Entra sont le seul type de journal directement intégré à AzLog, sans être encore disponibles dans Azure Monitor.

**Intégrer les journaux des machines virtuelles Azure** : AzLog a fourni l’option permettant d’intégrer les journaux du système d’exploitation invité de votre machine virtuelle Azure (par exemple, les événements de sécurité Windows) avec SELECT Siems. Azure Monitor comprend des agents disponibles pour Linux et Windows. Ces agents sont capables de router les journaux du système d’exploitation vers Azure Event Hubs, cependant, l’intégration de bout en bout aux outils SIEM est une tâche conséquente.

**Configuration de bout en bout** : AzLog a un script qui automatise la configuration de bout en bout des sources de journaux. Azure Monitor offre déjà la possibilité de générer un script pour la création de paramètres de diagnostic. En complément, nous travaillons avec l’équipe Azure Policy pour fournir une activation transparente via des stratégies de Gestionnaire des ressources, qui garantissent que les données de journal sont acheminées à partir de toutes les sources.

**Intégration à d’autres outils Siem** : AzLog a fourni une fonctionnalité générique permettant d’envoyer des journaux Azure standardisés au format JSON sur disque. Alors que les autres outils SIEM n’étaient pas officiellement pris en charge par AzLog, cela offrait un moyen d’obtenir facilement des données de journal dans des outils tels que LogRhythm. Notre recommandation pour les clients qui utilisent AzLog pour ces outils est de collaborer avec le producteur de cet outil pour fournir une intégration Azure Monitor Event Hubs.

La sécurité de votre environnement Azure est toujours prioritaire pour l’équipe Azure, à la fois dans la conception de la plateforme Azure et dans les fonctionnalités que nous vous proposons pour sécuriser vos propres ressources sur cette plateforme. Le déplacement de l’intégration SIEM vers Azure Monitor est une étape vers laquelle vous pouvez sécuriser vos applications sur Azure à l’échelle.


## Analyser des classeurs et des rapports Entra

Le rapport d’utilisation et d’insights vous fournit une vue centrée sur les applications de vos données de connexion. Vous y trouverez des réponses aux questions suivantes :

- Quelles sont les principales applications dans mon organisation ?
- Quelles sont les applications affichant le plus d’échecs de connexion ?
- Quelles sont les principales erreurs de connexion pour chaque application ?

### Prérequis

Pour accéder aux données du rapport d’utilisation et d’insights, vous avez besoin des éléments suivants :

- Un locataire Entra.
- Licence Entra ID P1 ou P2.
- Un utilisateur dans les rôles Administrateur de sécurité, Lecteur de sécurité ou Lecteur de rapport.

De plus, tous les utilisateurs (non administrateurs) peuvent accéder à leurs propres connexions.

### Accès au rapport d’utilisation et d’insights

1. Accédez au portail Azure.
2. Sélectionnez l’annuaire approprié, puis **Entra ID** et choisissez **Applications d’entreprise**.
3. Dans la section **Activité**, sélectionnez **Utilisation et insights** pour ouvrir le rapport.

### Utiliser le rapport

Le rapport d’utilisation et d’insights affiche la liste des applications ayant enregistré une ou plusieurs tentatives de connexion. Vous pouvez le trier selon le nombre de connexions réussies, de connexions échouées, et le taux de réussite.

L’option **Charger plus** en bas de la liste vous permet d’afficher d’autres applications sur la page. Vous pouvez sélectionner la plage de dates afin d’afficher toutes les applications utilisées dans cette plage.

Vous pouvez également définir le focus sur une application spécifique. Sélectionnez **Voir l'activité de connexion** afin d’afficher l’activité de connexion dans le temps pour l’application, ainsi que les principales erreurs.

Lorsque vous sélectionnez un jour dans le graphique d’utilisation des applications, vous obtenez une liste détaillée des activités de connexion pour l’application.

## Surveiller la posture de sécurité avec le score d'identité sécurisée

Le degré de sécurisation Identity Secure Score est un pourcentage qui indique dans quelle mesure vous respectez les suggestions de meilleures pratiques de Microsoft en matière de sécurité. Chaque action d’amélioration du score d’identité sécurisée est adaptée à votre configuration spécifique.

Le score vous aide à :

- Mesurez objectivement votre posture de sécurité d'identité
- Planifier les améliorations à apporter à la sécurité des identités
- Évaluer la réussite de vos améliorations

Vous pouvez accéder au degré de sécurisation et aux informations correspondantes dans le tableau de bord du degré de sécurisation Identity Secure Score. Ce tableau de bord présente les informations suivantes :

- Score sécurisé pour votre identité
- Graphique de comparaison qui situe votre degré de sécurisation Identity Secure Score par rapport aux autres locataires de tailles similaires et du même secteur d’activité
- Graphique de tendance montrant toute modification apportée au score de sécurisation de votre identité au fil du temps
- Liste des améliorations possibles

La mise en œuvre des actions d’amélioration vous offre les possibilités suivantes :

- Améliorez votre posture de sécurité et votre score
- Tirez profit des fonctionnalités dont dispose votre entreprise dans le cadre de vos investissements d’identité

### Comment puis-je obtenir mon score de sécurité ?

Le degré de sécurisation Identity Secure Score est disponible avec toutes les éditions d’Entra ID. Les organisations peuvent consulter leur score d'identité sécurisée en procédant comme suit :

1. Portail Azure.
2. ID Entra.
3. Sécurité.
4. Score de sécurité de l'identité.

### Comment les contrôles sont-ils notés ?

Les contrôles peuvent être évalués de deux manières. Certains sont évalués de façon binaire - vous obtenez 100 % du score si vous disposez de la fonctionnalité ou du paramètre configuré conformément à notre recommandation. Les autres scores sont calculés sous forme de pourcentage de la configuration totale. Par exemple, la recommandation d’amélioration peut indiquer que vous obtiendrez un maximum de 10,71 % en protégeant tous vos utilisateurs avec l’authentification multifacteur. Si seuls 5 utilisateurs sur 100 sont protégés, vous obtiendrez un score partiel autour de 0,53 % (5 protégés / 100 au total * 10,71 % maximum = 0,53 % de score partiel).

### Comment dois-je interpréter mon score ?

Votre score s’améliore lorsque vous configurez des fonctionnalités de sécurité suggérées ou mettez en œuvre des tâches liées à la sécurité (par exemple, la lecture de rapports). Certaines actions sont évaluées dans le cadre d'une mise en œuvre partielle, par exemple lorsque vous activez l'authentification multifacteur (MFA) pour vos utilisateurs. Votre degré de sécurisation représente de façon directe les services de sécurité Microsoft que vous utilisez. N’oubliez pas que vous devez trouver le juste équilibre entre sécurité et facilité d’utilisation. Tous les contrôles de sécurité comportent un composant relatif à l'affectation de l'utilisateur. Les contrôles dont le verrouillage par l'utilisateur est léger ne devraient avoir que peu ou pas d'effet sur les opérations quotidiennes de vos utilisateurs.


## Évaluation du module

Choisissez la meilleure réponse à chacune des questions ci-dessous.

### Vérifiez vos connaissances


## Récapitulatif et ressources

Une fois que vous avez implémenté une solution d’identité dans Azure, vous devez la surveiller. Il existe plusieurs outils dans Microsoft Sentinel pour enregistrer des fichiers afin de soutenir votre organisation dans ce processus.

Maintenant que vous avez passé en revue ce module, vous pouvez :

- Analyser et examiner les journaux de connexion pour résoudre les problèmes d’accès.
- Examinez et surveillez les journaux d’audit Entra.
- Activez et intégrez les journaux de diagnostic d’Entra à Log Analytics et Microsoft Sentinel.
- Exporter les journaux de connexion et d’audit vers une SIEM tierce.
- Examinez les activités Entra à l’aide de Log Analytics/Microsoft Sentinel, en excluant l’utilisation de KQL.
- Analysez des classeurs et des rapports Entra.
- Surveillez la posture de sécurité avec le score d'identité sécurisée.
- configurer les notifications.

Dans ce module, vous avez appris à surveiller et à gérer votre Entra ID en analysant tous les types de journaux.

Pour aller plus loin, consultez les articles suivants :

- [Présentation de Microsoft Sentinel](https://learn.microsoft.com/fr-fr/azure/sentinel/overview)
- [Connecteurs de données Microsoft Sentinel](https://learn.microsoft.com/fr-fr/azure/sentinel/connect-data-sources)
- [Langage de requête Kusto dans Microsoft Sentinel](https://learn.microsoft.com/fr-fr/kusto/query)
- [Score de sécurisation des identités dans Entra ID](https://learn.microsoft.com/fr-fr/entra/identity/monitoring-health/concept-identity-secure-score)
