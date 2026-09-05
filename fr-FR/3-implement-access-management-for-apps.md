# Implémenter la gestion des accès pour les applications

> SC-300 — learning path 3/4
> https://learn.microsoft.com/fr-fr/training/paths/implement-access-management-for-apps/

## Modules

- **Planifier et concevoir l’intégration des applications d’entreprise pour l’authentification unique** (10 units)
- **Implémenter et surveiller l’intégration des applications d’entreprise pour l’authentification unique** (10 units)
- **Implémenter l’inscription d’application** (11 units)
- **Inscrire des applications à l’aide d’Entra ID** (9 units)


---

# Planifier et concevoir l’intégration des applications d’entreprise pour l’authentification unique

_https://learn.microsoft.com/fr-fr/training/modules/plan-design-integration-of-enterprise-apps-for-sso/_


## Présentation

Dans ce module, vous découvrez les applications utilisées dans votre environnement. Ensuite, vous concevez et implémentez des rôles de gestion des accès et de gestion des applications. En outre, vous configurez des applications SaaS préintégrates (galerie).

### Objectifs d’apprentissage

Dans ce module, vous allez :

- Découvrez les applications en utilisant la fonction de découverte d'applications de Defender pour Cloud Apps.
- Concevoir et implémenter la gestion des accès pour les applications.
- Concevoir et implémenter des rôles de gestion des applications.
- Configurez les applications SaaS préintégrées (galerie).
- Explorez les connecteurs d’application et les applications OAuth.

### Conditions préalables

- Expérience d’utilisation solide des centres d’administration au sein de Microsoft Cloud.
- Expérience avec l’utilisation d’applications dans le cloud


## Découvrez les applications à l'aide du rapport d'applications Microsoft Defender pour Cloud Apps et Active Directory Federation Services.

Pour commencer à apprendre à protéger les applications cloud, vous devez d’abord découvrir ce que cloud Access Security Broker (CASB) est. Découvrez ensuite l’implémentation Microsoft de CASB.

**CASB** - Cloud Access Security Broker - Un point d’application de stratégie de sécurité, local ou cloud, placé entre les consommateurs et les fournisseurs de services cloud. Il combine et interjecte des stratégies de sécurité d’entreprise à mesure que les ressources cloud sont accessibles.

**MDCA** - Microsoft Defender pour Cloud Apps - Implémentation Microsoft d’un service CASB pour protéger les données, les services et les applications avec des stratégies d’entreprise. Il fournit des services de création de rapports et d’analytique supplémentaires

### Microsoft Defender for Cloud Apps (Protection pour Applications Cloud de Microsoft)

Le passage au cloud augmente la flexibilité des employés et des services informatiques. Toutefois, il présente également de nouveaux défis et complexités pour assurer la sécurité de votre organisation. Pour tirer pleinement parti des applications et des services cloud, une équipe informatique doit trouver le bon équilibre entre faciliter l’accès et garder le contrôle de façon à protéger les données critiques. Microsoft Defender for Cloud Apps (MDCA) est une solution Cloud Access Security Broker (CASB). Elle prend en charge divers modes de déploiement : collecte de journaux, connecteurs d’API et proxy inverse. Il offre une visibilité complète, un contrôle sur le déplacement des données et des capacités analytiques sophistiquées pour identifier et combattre les cybermenaces dans l’ensemble de vos services cloud Microsoft et tiers. Microsoft Defender pour Cloud Apps s’intègre en mode natif à des solutions Microsoft de pointe et est conçu avec des professionnels de la sécurité à l’esprit. Il offre un déploiement simple, une gestion centralisée et des fonctionnalités d’automatisation innovantes. Microsoft Defender for Cloud Apps est une solution inter-SaaS complète qui offre une visibilité approfondie, des contrôles de données renforcés et une protection améliorée contre les menaces pour les applications cloud. Cloud Discovery, une fonctionnalité de Microsoft Defender pour Cloud Apps, vous permet d’obtenir une visibilité sur l’informatique fantôme en découvrant les applications cloud en cours d’utilisation.

#### Architecture

Microsoft Defender pour Cloud Apps intègre la visibilité à votre cloud en :

- en utilisant Cloud Discovery pour mapper et identifier votre environnement cloud et les applications cloud utilisées par votre organisation ;
- Sanctionner et annuler l’autorisation des applications dans votre cloud.
- en utilisant des connecteurs faciles à déployer qui tirent parti des API de fournisseurs pour améliorer la visibilité et la gouvernance des applications auxquelles vous vous connectez ;
- en utilisant une protection du contrôle d’application par accès conditionnel pour obtenir une visibilité en temps réel et contrôler l’accès et les activités effectuées au sein de vos applications cloud ;
- Vous aider à garder un contrôle continu en définissant et en affinant continuellement les politiques.   ![Diagramme de l’architecture Microsoft Defender pour Cloud Apps. Comment les applications sont trouvées et gérées.](https://learn.microsoft.com../../wwl-sci/plan-design-integration-of-enterprise-apps-for-sso/media/proxy-architecture.png)

#### Découverte du Cloud

Cloud Discovery utilise vos journaux de trafic pour découvrir et analyser dynamiquement les applications cloud que votre organisation utilise. Pour créer un rapport instantané de l’utilisation du cloud de votre organisation, chargez manuellement les fichiers de journal à partir de vos pare-feu ou proxies pour analyse. Pour configurer des rapports continus, utilisez les collecteurs de journaux Microsoft Defender for Cloud Apps afin de transférer régulièrement vos journaux.

**Passer en revue le tableau de bord Cloud Discovery**

L’administrateur doit d’abord passer en revue les informations du tableau de bord Cloud Discovery pour obtenir une image générale de vos applications Cloud Discovery. Rechercher :

- Examinez d’abord l’utilisation globale de l’application cloud dans votre organisation dans la vue d’ensemble de l’utilisation générale.
- Ensuite, explorez un niveau plus en détail pour voir quelles sont les principales catégories utilisées dans votre organisation pour chacun des différents paramètres d’utilisation. Vous pouvez voir quelle part de cette utilisation est imputable aux applications Sanction.
- Aller encore plus loin et voir toutes les applications dans une catégorie spécifique dans l’onglet Applications découvertes.
- Vous pouvez voir les principaux utilisateurs et adresses IP sources pour identifier les utilisateurs les plus dominants des applications cloud de votre organisation.
- Vérifiez comment les applications découvertes sont réparties en fonction de l’emplacement géographique (selon leur siège social) dans la carte du siège de l’application.
- Enfin, n’oubliez pas de passer en revue le score de risque de l’application découverte dans la vue d’ensemble des risques de l’application. Vérifiez l’état des alertes de découverte pour voir le nombre d’alertes ouvertes que vous devez examiner.

**Filtrage des applications découvertes**

- **Étiquette d’application** : indiquez si l’application a été approuvée ou non approuvée, ou n’a pas été étiquetée. En outre, vous pouvez créer une balise personnalisée pour votre application, puis l’utiliser pour filtrer des types d’applications spécifiques.
- **Applications et domaines** : vous permet de rechercher des applications ou applications spécifiques utilisées dans des domaines spécifiques.
- **Catégories** : le filtre des catégories, situé à gauche de la page, vous permet de rechercher des types d’applications en fonction des catégories d’applications. Les exemples de catégories incluent les applications de réseau social, les applications de stockage cloud et les services d’hébergement. Vous pouvez sélectionner plusieurs catégories à la fois, ou une seule catégorie, puis appliquer les filtres de base et avancés en haut.
- **Facteur de risque de conformité** : recherchez des normes, une certification et une conformité spécifiques que l’application peut respecter (HIPAA, ISO 27001, SOC 2, PCI-DSS, etc.).
- **Facteur de risque général** : recherchez des facteurs de risque généraux tels que la popularité des consommateurs, les paramètres régionaux du centre de données, etc.
- **Score de risque** : permet aux applications de filtrer par score de risque afin que vous puissiez vous concentrer sur, par exemple, examiner uniquement les applications à haut risque. Vous pouvez également remplacer le score de risque défini par Microsoft Defender pour Cloud Apps. Pour plus d’informations, consultez Utilisation du score de risque.
- **Facteur de risque de sécurité** : vous permet de filtrer en fonction de mesures de sécurité spécifiques (telles que le chiffrement au repos, l’authentification multifacteur, etc.).
- **Utilisation** : active le filtrage en fonction des statistiques d’utilisation de cette application. Utilisation telle que les applications avec moins ou plus d’un nombre spécifié de chargements de données, les applications dont le nombre est supérieur ou inférieur à un nombre spécifié d’utilisateurs.
- **Facteur de risque juridique** : permet de filtrer en fonction de toutes les réglementations et stratégies en place pour garantir la protection et la confidentialité des données des utilisateurs de l’application. Par exemple, citons les applications cloud sécurisées prêtes pour le client, DMCA et la stratégie de rétention des données.

#### Sanction et annulation de l’approbation d’une application

Vous pouvez utiliser Microsoft Defender pour Cloud Apps pour sanctionner ou annuler des applications de votre organisation à l’aide du *catalogue d’applications cloud*. L’équipe Microsoft d’analystes dispose d’un catalogue étendu et en constante croissance de plus de 16 000 applications cloud classées et notées en fonction des normes du secteur. Utilisez le catalogue d’applications cloud pour évaluer le risque pour vos applications cloud en fonction des certifications réglementaires, des normes du secteur et des meilleures pratiques. Ensuite, personnalisez les scores et les pondérations de différents paramètres en fonction des besoins de votre organisation. En fonction de ces scores, Microsoft Defender pour Cloud Apps surveille le risque d’une application. Le scoring est basé sur plus de 80 facteurs de risque susceptibles d’affecter votre environnement.

### Services de fédération d'Active Directory

Si vous disposez d’un répertoire local qui contient des comptes d’utilisateur, vous disposez probablement de nombreuses applications auxquelles les utilisateurs s’authentifient. Chacune de ces applications est configurée pour permettre aux utilisateurs d’accéder à l’aide de leurs identités. Les utilisateurs peuvent également s’authentifier directement auprès de votre annuaire Active Directory local. Active Directory Federation Services (AD FS) est un service d’identité local basé sur des normes. AD FS étend la possibilité d’utiliser la fonctionnalité d’authentification unique (SSO) entre les partenaires professionnels approuvés sans que les utilisateurs se connectent séparément à chaque application - fédération. De nombreuses organisations ont des applications SaaS (Software as a Service) ou des applications métier personnalisées fédérées directement à AD FS, ainsi que des applications Microsoft 365 et Entra ID.

Pour renforcer la sécurité des applications, votre objectif est de disposer d’un ensemble unique de contrôles d’accès et de stratégies dans vos environnements locaux et cloud.

De nombreuses organisations utilisent AD FS pour fournir l’authentification unique aux applications cloud. Déplacer vos applications AD FS vers Entra ID pour l’authentification offre des avantages significatifs, en particulier en matière de gestion des coûts, de gestion des risques, de productivité, de conformité et de gouvernance. Toutefois, comprendre quelles applications sont compatibles avec Entra ID et identifier des étapes de migration spécifiques peut prendre beaucoup de temps.

Parfois, l’organisation peut utiliser d’autres fournisseurs d’identité locaux ou cloud, tels que SiteMinder, Oracle Access Manager, PingFederate, etc. La plupart d’entre eux sont des installations locales. Certains fournisseurs de cloud, tels que Okta et OneLogin, offrent des services similaires.

Le rapport d’activité des applications AD FS dans le portail Azure vous permet d’identifier rapidement les applications que vous pouvez migrer vers l’ID Entra. Il évalue la compatibilité de toutes les applications AD FS avec Entra ID, recherche tout problème éventuel et fournit des instructions sur la préparation d’applications individuelles pour la migration. Avec le rapport d’activité de l’application AD FS, vous pouvez découvrir les applications AD FS et étendre votre migration. Le rapport d’activité de l’application AD FS répertorie toutes les applications AD FS de votre organisation qui ont eu un utilisateur actif connecté au cours des 30 derniers jours. Les données d’activité sont disponibles pour les utilisateurs auxquels l’un de ces rôles d’administrateur est attribué : lecteur général/administrateur, lecteur de rapport, lecteur de sécurité, administrateur d’application ou administrateur d’application cloud.

### Types d’applications à migrer

La migration de l’authentification de votre application vers l’ID Entra est optimale, car elle vous offre un plan de contrôle unique pour la gestion des identités et des accès.

Il existe deux types d’applications à migrer :

1. Applications SaaS, qui sont achetées par l’organisation.
2. Applications métier développées par l’organisation et non destinées à être utilisées par d’autres entreprises. Vos applications peuvent utiliser des protocoles modernes ou hérités pour l’authentification. La plupart des applications SaaS utilisent des protocoles d’authentification modernes et fournissent des conseils sur la façon d’activer l’authentification unique. Envisagez d’abord de migrer des applications qui utilisent des protocoles d’authentification modernes (tels que SAML et Open ID Connect). Ces applications peuvent être reconfigurées pour s’authentifier auprès d’Entra ID via un connecteur intégré dans notre galerie d’applications ou en inscrivant l’application dans Entra ID. Intégrez des applications à l’aide de protocoles plus anciens à l’aide du [proxy d’application](https://learn.microsoft.com/fr-fr/azure/active-directory/manage-apps/what-is-application-proxy) et/ou des services de domaine Entra.

### Découvrir les applications AD FS pouvant être migrées

Le rapport d’activité de l’application AD FS est disponible dans le portail Azure sous Entra **Utilisation et aperçus**. Le rapport d’activité d’application AD FS analyse chaque application AD FS pour déterminer si elle peut être migrée as-is ou après examen.

1. Connectez-vous au portail Azure avec un rôle d’administrateur qui a accès aux données d’activité d’application AD FS (administrateur, lecteur de rapport, lecteur de sécurité, administrateur d’application ou administrateur d’application cloud).
2. Sélectionnez **l’ID Entra**, puis sélectionnez **Applications d’entreprise**.
3. Sous **Activité**, sélectionnez **Utilisation et insights**, puis sélectionnez **l’activité d’application AD FS** pour ouvrir la liste de toutes les applications AD FS de votre organisation.
4. Pour chaque application dans la liste d’activités de l’application AD FS, affichez **l’état de migration** :

- **Prêt à migrer** signifie que la configuration de l’application AD FS est entièrement prise en charge dans l’ID Entra et peut être migrée as-is.
- **La révision des besoins** signifie que certains des paramètres de l’application peuvent être migrés vers l’ID Entra, mais vous devez passer en revue les paramètres qui ne peuvent pas être migrés as-is.
- **Les étapes supplémentaires requises** signifient que l’ID Entra ne prend pas en charge certains paramètres de l’application, de sorte que l’application ne peut pas être migrée dans son état actuel.


## Configurer des connecteurs sur des applications

Les connecteurs d'applications utilisent les API des fournisseurs d'applications pour permettre une meilleure visibilité et un meilleur contrôle par Microsoft Defender pour les applications cloud sur les applications auxquelles vous vous connectez. Microsoft Defender pour Cloud Apps (MDCA) utilise les API fournies par le fournisseur de cloud. Toutes les communications entre Defender for Cloud Apps et les applications connectées sont chiffrées à l’aide du protocole HTTPS. Chaque service a sa propre infrastructure et ses propres limitations d’API, telles que la limitation, les limites d’API, les fenêtres d’API de décalage dynamique du temps, etc. Microsoft Defender for Cloud Apps travaillé avec les services pour optimiser l’utilisation des API et fournir les meilleures performances. Compte tenu des différentes limitations imposées aux API, Defender pour Cloud Apps utilise la capacité autorisée. Certaines opérations, telles que l'analyse de tous les fichiers du locataire, nécessitent de nombreuses API, elles sont donc réparties sur une période plus longue. Attendez-vous à ce que certaines politiques s'exécutent pendant plusieurs heures ou plusieurs jours.

### Prise en charge de plusieurs instance

Defender for Cloud Apps prend en charge plusieurs instances de la même application connectée. Par exemple, si vous avez plusieurs instances de Salesforce (une pour les ventes, une pour le marketing), vous pouvez connecter les deux à Defender pour Cloud Apps. Vous pouvez gérer les différentes instances à partir de la même console pour créer des stratégies granulaires et une investigation plus approfondie. Cette prise en charge s’applique uniquement aux applications connectées à l’API, et non aux applications cloud découvertes ou aux applications connectées par proxy.

### Fonctionnement

Defender for Cloud Apps est déployé avec des privilèges d’administrateur système pour autoriser l’accès complet à tous les objets de votre environnement. Le flux App Connector est le suivant :

1. Defender for Cloud Apps analyse et enregistre les autorisations d’authentification.
2. Defender for Cloud Apps demande la liste des utilisateurs. La première fois que la requête est effectuée, cela peut prendre un certain temps jusqu’à la fin de l’analyse.
3. Une fois la demande de l’utilisateur terminée, Defender for Cloud Apps analyse régulièrement les utilisateurs, les groupes, les activités et les fichiers. Toutes les activités seront disponibles après la première analyse complète.

Les connexions peuvent prendre un certain temps en fonction de la taille du locataire, du nombre d’utilisateurs et du nombre de fichiers à analyser. Selon l’application à laquelle vous vous connectez, la connexion d’API active les éléments suivants :

- **Informations de compte** : visibilité sur les utilisateurs, les comptes, les informations de profil, l’état (suspendu, actif, désactivé) et les privilèges.
- **Piste d’audit** : visibilité des activités utilisateur, des activités d’administration, des activités de connexion.
- **Gouvernance des comptes** - Possibilité de suspendre les utilisateurs, révoquer des mots de passe, etc.
- **Autorisations d’application** : visibilité des jetons émis et de leurs autorisations.
- **Gouvernance des autorisations d’application** : possibilité de supprimer des jetons.
- Analyse des **données** : analyse des données non structurées à l’aide de deux processus -periodically (toutes les 12 heures) et en temps réel (déclenchée chaque fois qu’une modification est détectée).
- **Gouvernance des données** : possibilité de mettre en quarantaine les fichiers, y compris les fichiers dans la corbeille et de remplacer les fichiers.


## L’exercice implémente la gestion des accès pour les applications

### Créer un compte Azure et ajouter des licences d’essai Entra ID Premium P2

Cet exercice, comme les autres de ce parcours d'apprentissage, exige un abonnement Azure. Utilisez celui dont vous disposez déjà, ou inscrivez-vous à un compte d'essai Azure. Si vous disposez déjà de votre propre abonnement Azure, vous ignorez cette tâche et passez à la suivante.

1. Dans un navigateur web, accédez au [portail d’abonnement gratuit Azure](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
2. Faites défiler la page pour découvrir tous les avantages et les services gratuits disponibles.
3. Sélectionnez **Démarrer gratuitement**.
4. Utilisez l’Assistant pour souscrire à votre abonnement d’essai gratuit Azure.
5. Vous avez besoin d'une licence Entra ID P2 pour effectuer certains exercices. Dans l'organisation que vous avez créée, recherchez et sélectionnez **Entra ID**.
6. Dans le menu de navigation gauche, sélectionnez **Prise en main**.
7. Sous Bien démarrer avec Entra ID, sélectionnez **Obtenir un essai gratuit pour Entra ID Premium**.
8. Dans le volet Activer, sous **Entra ID PREMIUM P2**, sélectionnez **Essai gratuit**, puis **Activer**.
9. Dans le menu de navigation, sélectionnez **Vue d’ensemble**.
10. Actualisez le navigateur jusqu’à ce qu’Entra ID Premium P2 s’affiche sous le nom de l’organisation. Cela prend quelques minutes.
11. Vous devez vous déconnecter et vous reconnecter à Microsoft Azure si vous rencontrez des problèmes avec les fonctionnalités attendues qui ne sont pas disponibles.

### Ajouter une application à votre locataire Entra

Ici, vous ajoutez une application Entreprise que vous pouvez utiliser pour l’exercice.

1. Connectez-vous au [Centre d'administration Entra](https://entra.microsoft.com/) à l'aide d'un compte administrateur général.
2. Ouvrez le menu du portail, puis sélectionnez **Identité**.
3. Dans le **menu Identité**, sous **Applications**, sélectionnez **Applications d’entreprise**.
4. Dans le volet **Applications d’entreprise** , sélectionnez **+ Nouvelle application**.
5. Dans la page **Parcourir la galerie Entra** , dans la zone **Application de recherche** , entrez **GitHub**.
6. Dans les résultats, sélectionnez **GitHub Enterprise Cloud – Compte Entreprise**.
7. Dans **GitHub Enterprise Cloud – Compte Entreprise**, passez en revue les paramètres, puis sélectionnez **Créer**.
8. Une fois le compte créé, vous êtes redirigé vers l’écran **GitHub Enterprise Cloud – Compte Entreprise** .

### Affecter des utilisateurs à une application

Attribuez votre compte d’administrateur à l’application récemment ajoutée.

1. Dans l’écran **GitHub Enterprise Cloud – Compte Entreprise** , dans la page **Vue d’ensemble** , sous **Bien démarrer**, sélectionnez **1. Affecter des utilisateurs et des groupes**. Vous pouvez également sélectionner **Utilisateurs et groupes** dans le volet de navigation gauche, sous **Gérer**.
2. Dans la page **Utilisateurs et groupes** , dans le menu, sélectionnez **+Ajouter un utilisateur/groupe**.
3. Dans la boîte de dialogue **Ajouter une affectation** , sélectionnez **Utilisateurs et groupes**.
4. Dans le volet **Utilisateurs et groupes** , sélectionnez votre compte d’administrateur, puis **sélectionnez**.
5. Sélectionnez **Attribuer**.


## Concevoir et implémenter des rôles de gestion des applications

Cette unité explique comment utiliser des autorisations accordées par des rôles personnalisés dans Entra ID pour répondre à vos besoins de gestion des applications. Dans Entra ID, vous pouvez déléguer les autorisations de création et de gestion des applications en :

- Restriction des utilisateurs autorisés à créer des applications et à gérer les applications qu’ils créent.
- Attribuer un ou plusieurs propriétaires à une application. L’attribution de propriétaires est un moyen simple d’accorder à quelqu’un la possibilité de gérer tous les aspects de la configuration d’ID Entra pour une application spécifique.
- Attribution d’un rôle d’administrateur intégré qui autorise l’accès à la gestion de la configuration dans Entra ID pour toutes les applications. Les rôles intégrés sont la méthode recommandée pour confier aux experts informatiques la gestion des autorisations de configuration d’application étendues, sans leur donner accès aux autres parties de l’ID Entra, non liées à la configuration de l’application.
- Création d’un rôle personnalisé définissant des autorisations spécifiques, puis attribution à une personne au niveau d'une seule application, en tant que propriétaire limité, ou au niveau de l'annuaire (toutes les applications), en tant qu'administrateur restreint.

Il est important de considérer l’octroi de l’accès à l’aide de l’une des méthodes ci-dessus pour deux raisons. Tout d’abord, la délégation de la possibilité d’effectuer des tâches d’administration réduit la charge de l’administrateur général. Deuxièmement, l’utilisation d’autorisations limitées améliore votre position de sécurité et réduit le risque d’accès non autorisé.

### Restreindre qui peut créer des applications

Dans Entra ID, tous les utilisateurs peuvent inscrire des inscriptions d’application et gérer tous les aspects des applications qu’ils créent. Tout le monde peut également donner son consentement aux applications qui accèdent aux données de l’entreprise en leur nom. Vous pouvez choisir d’accorder ces autorisations de manière sélective en définissant les commutateurs globaux sur « Non » et en ajoutant les utilisateurs sélectionnés au rôle Développeur d’applications.

#### Pour désactiver la capacité par défaut de créer des enregistrements d’applications ou de consentir aux applications

1. Connectez-vous à votre organisation Entra avec un compte qui est éligible au rôle Administrateur général dans votre organisation Entra.
2. Définissez un ou plusieurs des paramètres suivants :
  - Dans la page **Paramètres utilisateur** de votre organisation, réglez le paramètre **les utilisateurs peuvent inscrire des applications** sur Non. Cela désactive la possibilité par défaut pour les utilisateurs de créer des inscriptions d’applications.
  - Dans les **paramètres utilisateur** des applications d’entreprise, configurez si les utilisateurs peuvent ajouter des applications de galerie à mon application ou si les applications Office 365 apparaissent dans le portail Office.
  - Dans les paramètres **consentement et autorisations** pour les applications d’entreprise, définissez les **utilisateurs peuvent donner leur consentement aux applications qui accèdent aux données de l’entreprise en leur nom** sur Non. Cela désactive la possibilité par défaut pour les utilisateurs de donner leur consentement aux applications accédant aux données de l’entreprise en leur nom.

#### Accorder des autorisations individuelles pour créer des applications et donner leur consentement lorsque la capacité par défaut est désactivée

Attribuez le rôle Développeur d’applications pour accorder la possibilité de créer des enregistrements d’applications lorsque le paramètre **Les utilisateurs peuvent inscrire des applications** est défini sur Non. Ce rôle octroie aussi l’autorisation de donner son consentement en son propre nom lorsque le paramètre **Les utilisateurs peuvent autoriser les applications à accéder aux données de l’entreprise en leur nom** est défini sur Non. En tant que comportement système, lorsqu’un utilisateur crée une inscription d’application, il est automatiquement ajouté en tant que premier propriétaire. Les autorisations de propriété permettent à l’utilisateur de gérer tous les aspects d’une inscription d’application ou d’une application d’entreprise qu’il possède.

### Assigner les propriétaires de l’application

L’attribution de propriétaires est un moyen simple d’accorder la possibilité de gérer tous les aspects de la configuration d’ID Entra pour une inscription d’application spécifique ou une application d’entreprise. En tant que comportement système, lorsqu’un utilisateur crée une inscription d’application, il est automatiquement ajouté en tant que premier propriétaire. Les autorisations de propriété permettent à l’utilisateur de gérer tous les aspects d’une inscription d’application ou d’une application d’entreprise qu’il possède. Le propriétaire d’origine peut être supprimé et d’autres propriétaires peuvent être ajoutés.

#### Propriétaires d’applications d’entreprise

En tant que propriétaire, un utilisateur peut gérer la configuration spécifique à l’organisation de l’application d’entreprise, telle que la configuration de l’authentification unique, l’approvisionnement et les affectations d’utilisateurs. Un propriétaire peut également ajouter ou supprimer des propriétaires. Contrairement aux administrateurs généraux, les propriétaires ne peuvent gérer que les applications d’entreprise qu’ils possèdent.

Dans certains cas, les applications d’entreprise créées à partir de la galerie d’applications incluent à la fois une application d’entreprise et une inscription d’application. Lorsque cela est vrai, l’ajout d’un propriétaire à l’application d’entreprise ajoute automatiquement le propriétaire à l’inscription d’application correspondante en tant que propriétaire.

#### Pour attribuer un propriétaire à une application d'entreprise

1. Connectez-vous à votre organisation Entra avec un compte éligible pour l’administrateur d’application ou l’administrateur d’application cloud de l’organisation.
2. Dans la page **Inscriptions** d’applications pour l’organisation, sélectionnez une application pour ouvrir la page Vue d’ensemble de l’application.
3. Sélectionnez **Propriétaires** pour afficher la liste des propriétaires de l’application.
4. Sélectionnez **Ajouter** pour sélectionner un ou plusieurs propriétaires à ajouter à l’application.

Important

Les utilisateurs et les principaux de service peuvent être propriétaires d’enregistrements d’applications. Seuls les utilisateurs peuvent être propriétaires d’applications d’entreprise. Les groupes ne peuvent pas être attribués en tant que propriétaires de l’un ou l’autre.

Les propriétaires peuvent ajouter des informations d’identification à une application et utiliser ces informations d’identification pour emprunter l’identité de l’application. L’application dispose de plus d’autorisations que le propriétaire. Il s’agit donc d’une élévation de privilèges par rapport à ce que le propriétaire a accès en tant qu’utilisateur ou principal de service. Selon les autorisations de l’application, un propriétaire d’application peut potentiellement créer ou mettre à jour des utilisateurs ou d’autres objets lors de l’emprunt d’identité de l’application.

### Affecter des rôles d’administrateur d’application intégrés

Entra ID a un ensemble de rôles d’administrateur intégrés pour accorder l’accès à la gestion de la configuration dans Entra ID pour toutes les applications. Ces rôles sont la méthode recommandée pour confier aux experts informatiques la gestion des autorisations de configuration d’application étendues, sans leur donner accès aux autres parties de l’ID Entra, non liées à la configuration de l’application.

- Administrateur d’application : Les utilisateurs dans ce rôle peuvent créer et gérer tous les aspects des applications d’entreprise, des inscriptions d’application et des paramètres de proxy d’application. Ce rôle accorde également la possibilité de donner son consentement aux autorisations déléguées et aux autorisations d’application, à l’exclusion de Microsoft Graph. Les utilisateurs affectés à ce rôle ne sont pas ajoutés en tant que propriétaires lors de la création de nouvelles inscriptions d’applications ou d’applications d’entreprise.
- Administrateur d’application cloud Les utilisateurs dans ce rôle ont les mêmes autorisations que celles du rôle Administrateur d’application, sans la possibilité de gérer le proxy d’application. Les utilisateurs affectés à ce rôle ne sont pas ajoutés en tant que propriétaires lors de la création de nouvelles inscriptions d’applications ou d’applications d’entreprise.  Important Les administrateurs d’applications et les administrateurs d’applications Cloud peuvent ajouter des informations d’identification à une application et utiliser ces informations d’identification pour emprunter l’identité de l’application. L'application dispose d'autorisations qui constituent une élévation de privilèges par rapport aux autorisations du rôle d'administrateur. Selon les autorisations de l’application, un administrateur de l’un de ces rôles peut potentiellement créer ou mettre à jour des utilisateurs ou d’autres objets lors de l’emprunt d’identité de l’application. Aucun rôle n’accorde la possibilité de gérer les paramètres d’accès conditionnel.

### Créer et affecter un rôle personnalisé

La création de rôles personnalisés et l’attribution de rôles personnalisés sont des étapes distinctes :

- Créez une *définition de rôle* personnalisée et ajoutez-y des autorisations à partir d’une liste prédéfinie. Il s’agit des mêmes autorisations que celles utilisées dans les rôles intégrés.
- Créez une *attribution de rôle* pour attribuer le rôle personnalisé.

Cette séparation vous permet de créer une définition de rôle unique, puis de l’affecter plusieurs fois à différentes *étendues*. Un rôle personnalisé peut être attribué à l'échelle de l'organisation ou pour un seul objet Entra. Un exemple de portée d’objet est l’enregistrement d’une seule application. Toutefois, avec différentes étendues, un administrateur peut affecter la même définition de rôle à une personne sur toutes les inscriptions d’application de l’organisation, et à une autre sur une seule application ou des inscriptions d’application spécifiques.

Conseils lors de la création et de l’utilisation de rôles personnalisés pour la délégation de la gestion d’applications :

- Les rôles personnalisés accordent uniquement l’accès dans l’écran d’inscription d’application le plus actuel du Centre d’administration Entra. Ils n'accordent pas d'accès à l'écran d'enregistrement des applications héritées.
- Les rôles personnalisés n’accordent pas l’accès au portail Entra ID lorsque le paramètre **d’utilisateur Restreindre l’accès au portail d’administration d’ID Entra** est défini sur Oui.
- Pour les inscriptions d’applications à laquelle l’utilisateur a accès, les attributions de rôles s’affichent uniquement dans l’onglet **Toutes les applications** de la page **d’inscription d’application** . Ils ne s’affichent pas sous l’onglet **Applications détenues** .


## Exercice : créer un rôle personnalisé pour gérer l’inscription d’application

Créez un rôle personnalisé qui peut être utilisé pour accorder l’accès pour gérer les inscriptions d’applications.

1. Connectez-vous au [Centre d’administration Entra](https://entra.microsoft.com/) à l’aide d’un compte Administrateur.
2. Ouvrez le menu du portail, puis sélectionnez **Identité**.
3. Dans le menu **Identité** , ouvrez le menu **Rôles et administrateurs** , puis sélectionnez **Rôles et administrateurs.**
4. Dans l’écran **Rôles et administrateurs** , dans le menu, sélectionnez **Nouveau rôle personnalisé.**
5. Dans la boîte de dialogue **Nouveau rôle personnalisé** , sous l’onglet **Informations de base** , dans la zone nom, entrez **Mon rôle d’application personnalisé**.
6. Passez en revue les options restantes, puis sélectionnez **Suivant**.
7. Sous l’onglet **Autorisations** , passez en revue les autorisations disponibles.
8. Dans la zone **Rechercher par nom d’autorisation ou description** , entrez les informations d’identification.
9. Dans les résultats, sélectionnez **Gérer** les autorisations, puis sélectionnez **Suivant**.
10. Passez en revue les modifications, puis sélectionnez **Créer.**


## Configurer des applications SaaS de galerie préintégrées

Comme vous le savez, Entra ID dispose d’une galerie qui contient des milliers d’applications préintégrées. De nombreuses applications utilisées par votre organisation sont probablement déjà dans la galerie. Une fois une application ajoutée à votre locataire Entra, vous pouvez configurer ses propriétés, gérer l’accès utilisateur et configurer l’authentification unique, afin que les utilisateurs se connectent à l’application avec leurs informations d’identification Entra. Cette unité vous montre comment configurer les propriétés de l’application.

### Configurer les propriétés d’application (application)

Pour modifier les propriétés de l’application :

1. Dans le menu Identité du centre d’administration Entra, sélectionnez **Applications d’entreprise**. Ensuite, recherchez et sélectionnez l’application que vous souhaitez configurer.
2. Dans la section **Gérer**, sélectionnez **Propriétés** pour ouvrir le volet **Propriétés** à des fins de modification.
3. Prenez un moment pour comprendre les options disponibles. Les options disponibles dépendent de la façon dont l’application est intégrée à l’ID Entra. Par exemple, une application qui utilise l’authentification unique basée sur SAML aura des champs tels que *l’URL d’accès utilisateur* , alors qu’une application qui utilise l’OIDC n’utilise pas l’authentification unique basée sur OIDC. Les applications **ajoutées via l’ID Entra - Les inscriptions d’applications** sont par défaut des applications basées sur OIDC. Celles ajoutées **via l’ID Entra - Les applications d’entreprise** peuvent utiliser n’importe quelle norme d’authentification unique. Toutes les applications auront des champs pour la configuration lorsqu’une application s’affiche et peut être utilisée. Ces champs sont les suivants :
  - **Activé pour que les utilisateurs se connectent ?** détermine si les utilisateurs affectés à l’application peuvent se connecter.
  - **Attribution d’utilisateur requise ?** détermine si les utilisateurs qui ne sont pas affectés à l’application peuvent se connecter.
  - **Visible pour les utilisateurs ?** détermine si les utilisateurs affectés à une application la voient dans [Mes applications](https://myapps.microsoft.com/) et le lanceur d’applications Microsoft 365. (Voir le menu gaufre dans le coin supérieur gauche d’un site web Microsoft 365.)

4. Lorsque vous avez terminé, sélectionnez **Enregistrer**

### Utiliser un logo personnalisé

1. Pour utiliser un logo personnalisé :
2. Créez un logo de 215 à 215 pixels et enregistrez-le au format .png.
3. Dans le centre d’administration Entra, sélectionnez **Applications d’entreprise**. Ensuite, recherchez et sélectionnez l’application que vous souhaitez configurer.
4. Dans la section **Gérer**, sélectionnez **Propriétés** pour ouvrir le volet **Propriétés** à des fins de modification.
5. Sélectionnez l’icône pour charger le logo.
6. Ensuite, vous avez terminé, sélectionnez **Enregistrer**.

### Ajouter des notes

Vous pouvez utiliser le champ notes pour ajouter toutes les informations pertinentes pour la gestion de l’application.

1. Dans le centre d’administration Entra, sélectionnez **Applications d’entreprise**. Ensuite, recherchez et sélectionnez l’application que vous souhaitez configurer.
2. Dans la section **Gérer**, sélectionnez **Propriétés** pour ouvrir le volet **Propriétés** à des fins de modification.
3. Mettez à jour le champ Notes, sélectionnez **Enregistrer**.


## Implémenter et gérer des stratégies pour les applications OAuth

Outre l’examen existant des applications OAuth connectées à votre environnement, vous pouvez définir des stratégies d’autorisation afin d’obtenir des notifications automatisées lorsqu’une application OAuth répond à certains critères. Par exemple, vous pouvez être alerté automatiquement lorsqu’il existe des applications qui nécessitent un niveau d’autorisation élevé et qui ont été autorisées par plus de 50 utilisateurs. Les stratégies d’application OAuth vous permettent d’examiner les autorisations demandées par chaque application et les utilisateurs qui les ont autorisés pour Office 365 et d’autres applications OAuth. Vous pouvez également marquer ces autorisations comme approuvées ou interdites. Si vous les marquez comme interdites, l’application d’entreprise correspondante est désactivée.

### Créer une stratégie d’application OAuth

1. Lancez **Microsoft Defender pour Cloud Apps** à l’adresse [https://security.microsoft.com](https://security.microsoft.com).
2. Faites défiler le menu vers la gauche jusqu’à ce que vous accédiez à la section **Applications cloud** .
3. Sélectionnez **les applications OAuth**.
4. Filtrez les applications en fonction de vos besoins.

- Par exemple, vous pouvez afficher toutes les applications qui demandent l’autorisation de modifier des calendriers dans votre boîte aux lettres.

1. Sélectionnez la **nouvelle stratégie** dans le bouton de recherche.
2. Vous pouvez utiliser le filtre **Community** pour savoir si l’autorisation d’accès à cette application est courante, peu courante ou rare.
  - Ce filtre peut être utile si une de vos application est rare et si elle demande l’autorisation avec un niveau de gravité élevé, ou si elle demande l’autorisation à de nombreux utilisateurs.

3. Vous pouvez définir la stratégie en fonction des appartenances aux groupes des utilisateurs qui ont autorisé les applications.

- Par exemple, un administrateur peut définir une stratégie qui révoque les applications rares demandant des autorisations élevées, mais uniquement si l’utilisateur qui a accordé ces autorisations est membre du groupe Administrateurs.

#### Stratégies de contrôle

Vous pouvez également créer la stratégie en sélectionnant **Contrôle** suivi des **stratégies**. Sélectionnez Ensuite **Créer une stratégie** suivie de **la stratégie d’application OAuth**.


## Évaluation des modules

Choisissez la meilleure réponse pour chacune des questions.

### Vérifiez vos connaissances


## Récapitulatif et ressources

Après avoir terminé ce module, vous pouvez :

- Découvrez les applications à l’aide de la découverte d’applications dans le rapport d’application Microsoft Defender ou Active Directory.
- Concevoir et implémenter la gestion des accès pour les applications.
- Concevoir et implémenter des rôles de gestion des applications.
- Configurez les applications SaaS préintégrées (galerie).
- Explorez les connecteurs d’application et les applications OAuth.

### Ressources

Utilisez ces ressources pour approfondir vos connaissances :

- [Qu’est-ce que l’authentification unique dans Entra ID ?](https://learn.microsoft.com/fr-fr/entra/identity/enterprise-apps/what-is-single-sign-on)
- [Applications connectées avec Microsoft Defender pour Cloud Apps](https://learn.microsoft.com/fr-fr/defender-cloud-apps/enable-instant-visibility-protection-and-governance-actions-for-your-apps)
- [Démarrage rapide : Activer l’authentification unique pour une application d’entreprise](https://learn.microsoft.com/fr-fr/entra/identity/enterprise-apps/add-application-portal-setup-sso)
- [Créer des stratégies pour contrôler les applications OAuth](https://learn.microsoft.com/fr-fr/defender-cloud-apps/app-permission-policy)


---

# Implémenter et surveiller l’intégration des applications d’entreprise pour l’authentification unique

_https://learn.microsoft.com/fr-fr/training/modules/implement-monitor-integration-of-enterprise-apps-for-sso/_


## Présentation

Dans ce module, vous allez apprendre à implémenter des personnalisations de jetons et à implémenter et à configurer des paramètres de consentement. Vous allez également apprendre à intégrer des applications locales à l’aide du proxy d’application Entra, ainsi qu’à intégrer des applications saaS (software as a service) personnalisées pour l’authentification unique (SSO). Enfin, vous allez découvrir comment implémenter l’approvisionnement d’utilisateurs d’applications et surveiller et auditer l’accès aux applications d’entreprise intégrées Entra ID.

### Objectifs d’apprentissage

Dans ce module, vous allez :

- Implémenter des personnalisations de jetons
- Implémenter et configurer les paramètres de consentement
- Intégrer des applications locales à l’aide du proxy d’application Entra
- Intégrer des applications SaaS personnalisées pour l’authentification unique
- Mettre en œuvre le provisionnement des utilisateurs d'application
- Créer et gérer des collections d’applications
- Surveiller et auditer l’accès aux applications d’entreprise intégrées Entra ID

### Conditions préalables

- Gestion des utilisateurs et des administrateurs dans l’ID Entra
- Expérience de configuration de l’accès conditionnel


## Implémenter des personnalisations de jetons

Vous pouvez spécifier la durée de vie d’un jeton émis par la plateforme d’identités Microsoft. Vous pouvez en outre définir des durées de vie de jetons pour toutes les applications de votre organisation, pour une application multilocataire (plusieurs organisations) ou pour un principal de service spécifique. Dans Entra ID, un objet de stratégie représente un ensemble de règles appliquées à des applications individuelles ou à toutes les applications d’une organisation. Chaque type de stratégie comporte une structure unique avec un ensemble de propriétés qui sont ensuite appliquées aux objets auxquels elles sont affectées.

Vous pouvez désigner une stratégie comme stratégie par défaut pour votre organisation. La stratégie est appliquée à toutes les applications de l’organisation tant qu’elle n’est pas remplacée par une stratégie pourvue d’une priorité plus élevée. Vous pouvez également affecter une stratégie à des applications spécifiques. L’ordre de priorité varie par type de stratégie.

### Configurer la gestion des sessions d’authentification avec l’accès conditionnel

Dans les déploiements complexes, les organisations peuvent avoir besoin de limiter les sessions d’authentification. Ces scénarios complexes peuvent inclure :

- L’accès aux ressources à partir d’un appareil non géré ou partagé.
- L’accès à des informations sensibles depuis un réseau externe.
- Utilisateurs à impact élevé.
- Des applications métier critiques.

Les contrôles d’accès conditionnel permettent de créer des stratégies qui ciblent des cas d’usage particuliers au sein de votre organisation, sans affecter tous les utilisateurs.

Pour plus d’informations, consultez le lien dans les ressources à la fin de ce module.

### Personnaliser des jetons pour l’ID Entra

| **Durée de vie des jetons d’accès et d’ID** | **Durée de vie des jetons d’actualisation (jours)** | **Durée de vie de la fenêtre glissante des jetons d’actualisation** | **Durée de vie (jours)** |
|---|---|---|---|
| Durée de vie du jeton du porteur OAuth 2.0 et du jeton d’ID | Période maximale avant laquelle un jeton d’actualisation peut être utilisé pour acquérir un nouveau jeton d’accès | Type de fenêtre glissante du jeton d’actualisation | Une fois la période écoulée, l’utilisateur est forcé de se réauthentifier |

![Diagramme de la durée de vie du jeton d’actualisation : le jeton est valide pour une durée spécifiée et le jeton d’accès doit être actualisé avant son expiration.](https://learn.microsoft.com../../wwl-sci/implement-monitor-integration-of-enterprise-apps-for-sso/media/token-customize-timeline.png)

### Configurer des revendications facultatives dans le cadre de votre jeton

Les développeurs d’applications peuvent utiliser des revendications facultatives dans leurs applications d’ID Entra pour spécifier les revendications souhaitées dans les jetons envoyés à leur application.

Vous pouvez utiliser des revendications facultatives pour :

- Sélectionnez d’autres revendications à inclure dans des jetons pour votre application.
- Modifiez le comportement de certaines revendications retournées par la plateforme d’identités Microsoft dans les jetons.
- Ajoutez des revendications personnalisées d’accès pour votre application.

Bien que les revendications facultatives soient prises en charge dans les jetons au format v1.0, v2.0 et SAML, elles révèlent leur pleine valeur surtout lors de la transition de v1.0 à v2.0. L’un des objectifs de la plateforme d’identités Microsoft est de réduire les tailles de jetons pour garantir des performances optimales par les clients. Ainsi, plusieurs revendications précédemment incluses dans les jetons d’accès et d’ID ne sont plus présentes dans les jetons v2.0 et doivent être demandées spécifiquement pour chaque application.

## Implémenter et configurer les paramètres de consentement

Intégrez vos applications à la plateforme d’identités Microsoft : les utilisateurs se connectent avec leur compte professionnel ou scolaire et accèdent aux données de l’organisation, ce qui vous permet de fournir des expériences riches basées sur les données.

Pour qu’une application puisse accéder aux données de l’organisation, un utilisateur doit accorder les autorisations d’application pour le faire. Les différentes autorisations ont trait à des niveaux d’accès différents. Par défaut, tous les utilisateurs peuvent donner leur consentement aux applications pour les autorisations qui ne nécessitent pas le consentement de l’administrateur. Par exemple, par défaut, un utilisateur peut donner son consentement pour autoriser une application à accéder à sa boîte aux lettres. Toutefois, ils ne peuvent pas consentir à autoriser l’accès sans entrave à une application pour lire et écrire dans tous les fichiers de votre organisation.

En permettant aux utilisateurs d’accorder aux applications l’accès aux données, ils peuvent facilement acquérir des applications utiles et être productifs. Toutefois, dans certaines situations, cette configuration peut représenter un risque s’il n’est pas soigneusement surveillé et contrôlé.

Important

Des applications malveillantes peuvent tenter d’inciter les utilisateurs à leur accorder l’accès aux données de votre organisation. Pour réduire ce risque, il est recommandé d’autoriser le consentement de l’utilisateur uniquement pour les applications publiées par un [éditeur vérifié](https://learn.microsoft.com/fr-fr/azure/active-directory/develop/publisher-verification-overview).

### Paramètres de consentement de l’utilisateur

Les stratégies de consentement de l’application décrivent les conditions qui doivent être remplies avant qu’une application puisse être consentée. Ces stratégies peuvent inclure des conditions sur l’application demandant l’accès et les autorisations demandées par l’application.

En choisissant les stratégies de consentement d’application qui s’appliquent à tous les utilisateurs, vous définissez les limites : quand les utilisateurs finaux peuvent accorder leur consentement aux applications, et quand ils doivent demander l’examen et l’approbation de l’administrateur.

- **Désactiver le consentement de l’utilisateur** : les utilisateurs ne peuvent pas accorder d’autorisations aux applications. Les utilisateurs peuvent continuer à se connecter aux applications auxquelles ils ont déjà consenti, ou qui ont été consenties par les administrateurs en leur nom. En revanche, ils ne peuvent plus consentir à de nouvelles autorisations ni à de nouvelles applications en leur propre nom. Seuls les utilisateurs qui ont reçu un rôle d’annuaire qui incluent l’autorisation d’accorder le consentement pourront donner leur consentement à de nouvelles applications.
- **Les utilisateurs peuvent donner leur consentement aux applications à partir de [serveurs de publication vérifiés](https://learn.microsoft.com/fr-fr/azure/active-directory/develop/publisher-verification-overview)ou de votre organisation, mais uniquement pour les autorisations que vous choisissez** : tous les utilisateurs peuvent uniquement consentir aux applications publiées par un éditeur vérifié et aux applications inscrites dans votre locataire. Les utilisateurs ne peuvent donner leur consentement qu’aux autorisations que vous avez classifiées en tant que `low impact`. Vous devez [classer les autorisations](https://learn.microsoft.com/fr-fr/azure/active-directory/manage-apps/configure-permission-classifications) pour choisir les autorisations auxquelles les utilisateurs sont autorisés à donner leur consentement.
- **Les utilisateurs peuvent donner leur consentement à toutes les applications** : cette option leur permet de consentir à toute autorisation d’une application qui ne nécessite pas le consentement de l’administrateur.
- **Stratégie de consentement d’application personnalisée** : pour plus d’options sur les conditions régissant le consentement des utilisateurs, [créez des stratégies de consentement d’application personnalisées](https://learn.microsoft.com/fr-fr/azure/active-directory/manage-apps/manage-app-consent-policies) et configurez-les pour qu’elles s’appliquent au consentement de l’utilisateur.

### Consentement progressif basé sur les risques

Le consentement renforcé basé sur les risques permet de réduire l’exposition des utilisateurs aux applications malveillantes qui font des requêtes de consentement illicites. Si Microsoft détecte une demande de consentement de l’utilisateur final risquée, la demande devra être approuvée par un administrateur à la place. Cette fonctionnalité est activée par défaut, mais elle entraîne uniquement un changement de comportement lorsque le consentement de l’utilisateur final est activé.

Lorsqu’une demande de consentement à risque est détectée, l’invite de consentement affiche un message indiquant que l’approbation de l’administrateur est nécessaire. Si le flux de travail de demande de consentement administrateur est activé, l’utilisateur peut envoyer la demande à un administrateur pour une révision plus approfondie directement à partir de l’invite de consentement. S’il n’est pas activé, le message suivant s’affiche :

- **AADSTS90094 :** nécessite l’autorisation d’accéder aux ressources de votre organisation que seul un administrateur peut accorder. Demandez à un administrateur de vous accorder une autorisation d’accès à cette application avant de l’utiliser.

Dans ce cas, un événement d’audit est également enregistré avec une catégorie **d’ApplicationManagement**, un type d’activité de **consentement à l’application** et une raison d’état de **l’application à risque détectée.**

Important

Les administrateurs doivent évaluer attentivement toutes les demandes de consentement avant d’approuver une demande, en particulier lorsque Microsoft a détecté un risque.


## Intégrer des applications locales avec le proxy d’application Entra

**Qu’est-ce que le Proxy d’application ?** Le Proxy d’application est une fonctionnalité d’Entra ID qui permet aux utilisateurs d’accéder à des applications web locales à partir d’un client distant. Le proxy d’application inclut à la fois le service proxy d’application qui s’exécute dans le cloud et le connecteur proxy d’application qui s’exécute sur un serveur local. Entra ID, le service Proxy d'application et le connecteur Proxy d’application fonctionnent ensemble pour transmettre en toute sécurité le jeton de connexion utilisateur Entra ID à l'application Web.

Le proxy d’application pour Entra ID fournit un accès à distance sécurisé aux applications web locales. Après une authentification unique à Entra ID, les utilisateurs peuvent accéder aux applications cloud et locales par le biais d’une URL externe ou un portail d’applications interne. Par exemple, Application Proxy peut fournir un accès à distance et une authentification unique aux applications Bureau à distance, SharePoint, Teams, Tableau, Qlik et aux applications métier (LOB).

Proxy d’application fonctionne avec les ressources suivantes :

- Applications web qui utilisent [l’authentification Windows intégrée](https://learn.microsoft.com/fr-fr/azure/active-directory/manage-apps/application-proxy-configure-single-sign-on-with-kcd) pour l’authentification.
- Applications web qui utilisent l’accès basé sur des formulaires ou basé sur l'en-tête.
- API web que vous souhaitez exposer à des applications enrichies sur différents appareils.
- Applications hébergées derrière une [passerelle Remote Desktop](https://learn.microsoft.com/fr-fr/azure/active-directory/manage-apps/application-proxy-integrate-with-remote-desktop-services).
- Applications clientes enrichies intégrées à la bibliothèque d’authentification Microsoft (MSAL).

Le proxy d’application est l’outil recommandé pour permettre aux utilisateurs distants d’accéder aux ressources internes. Le proxy d’application remplace la nécessité d’un réseau privé virtuel (VPN) ou d’un proxy inverse. Il n’est pas destiné aux utilisateurs internes sur le réseau d’entreprise. Ces utilisateurs qui utilisent inutilement le proxy d’application peuvent ralentir les performances de manière inattendue et indésirable.

### Fonctionnement de Proxy d’application

Le diagramme suivant montre comment Entra ID et Application Proxy fonctionnent ensemble pour fournir une authentification unique aux applications locales.

![Diagramme du flux de processus du proxy d’application Entra. Une configuration réussie s’affiche.](https://learn.microsoft.com../../wwl-sci/implement-monitor-integration-of-enterprise-apps-for-sso/media/azure-app-proxxy.png)

1. Une fois que l'utilisateur a accédé à l'application par l'intermédiaire d'un point de terminaison, il est dirigé vers la page de connexion d’Entra.
2. Après la connexion, Entra ID envoie un jeton à l'appareil client de l'utilisateur.
3. Le client envoie le jeton au service Proxy d’application qui récupère le nom d’utilisateur principal (UPN) et le nom de sécurité principal (SPN) du jeton. Le proxy d'application envoie ensuite la requête au connecteur de proxy d'application.
4. Si vous avez configuré l’authentification unique, le connecteur effectue toute authentification supplémentaire requise pour le compte de l’utilisateur.
5. Le connecteur envoie la requête à l’application locale.
6. La réponse est envoyée à l’utilisateur par le biais du connecteur et du service Proxy d’application.

### Ajouter une application locale pour l’accès à distance via le proxy d’application dans Entra ID

Lancez ce guide interactif pour en savoir plus sur l’activation de l’authentification Windows intégrée sur les applications locales avec le proxy d’application Entra - **[Activer le guide interactif d’authentification Windows intégrée](https://mslearn.cloudguides.com/guides/Provide%20secure%20remote%20access%20to%20on-premises%20applications%20with%20Azure%20AD%20Application%20Proxy)**


## Intégrer des applications SaaS personnalisées pour l’authentification unique

![Diagramme de l’ID Entra étant le fournisseur d’authentification unique pour les applications cloud. Les utilisateurs et les utilisateurs externes se connectent à l’ID Entra, puis se connectent aux applications cloud.](https://learn.microsoft.com../../wwl-sci/implement-monitor-integration-of-enterprise-apps-for-sso/media/app-single-sign-on.png)

- Vous pouvez utiliser Entra ID comme système d’identité pour n’importe quelle application. De nombreuses applications sont déjà préconfigurées et peuvent être configurées avec un effort minimal. Ces applications préconfigurées sont publiées dans la galerie d’applications Entra ID.
- Vous pouvez configurer manuellement la plupart des applications pour l’authentification unique si elles ne se trouvent pas déjà dans la galerie. Entra ID fournit plusieurs options d’authentification unique. Authentification unique SAML et authentification unique OIDC.

En fait, les applications peuvent déléguer la maintenance de leurs propres informations de nom d’utilisateur et de mot de passe à un fournisseur d’identité centralisé, l’ID Entra comme exemple. La délégation de l’authentification et de l’autorisation permet des scénarios tels que des stratégies d’accès conditionnel qui nécessitent qu’un utilisateur se trouve dans un emplacement spécifique ou nécessite une authentification multifacteur. L’utilisation de l’authentification unique (SSO), permet à un utilisateur de se connecter une fois, puis de se connecter automatiquement à toutes les applications web qui partagent le même répertoire centralisé.

La plateforme d’identités Microsoft simplifie l’autorisation et l’authentification pour les développeurs d’applications en fournissant une identité en tant que service. Elle prend en charge les protocoles standard tels que OAuth 2.0 et OpenID Connect, et propose des bibliothèques open source pour différentes plateformes, pour vous aider à commencer à coder rapidement. Elle permet aux développeurs de créer des applications qui se connectent à toutes les identités Microsoft, et d’obtenir des jetons pour appeler Microsoft Graph, d'autres API Microsoft ou des API créées par les développeurs.

La liste suivante est une brève comparaison des différents protocoles utilisés par la plateforme d’identités Microsoft.

- **OAuth et OpenID Connect** : OAuth est utilisé pour l’autorisation et OpenID Connect (OIDC) est utilisé pour l’authentification. OpenID Connect est basé sur OAuth 2.0, ce qui signifie que la terminologie et le flux sont similaires entre les deux. Vous pouvez même authentifier un utilisateur à l’aide d’OpenID Connect et obtenir l’autorisation d’accéder à une ressource protégée que l’utilisateur possède à l’aide d’OAuth 2.0 dans une requête.
- **OAuth et SAML** : OAuth est utilisé pour l’autorisation et le langage SAML (Security Assertion Markup Language) est utilisé pour l’authentification.
- **OpenID Connect et SAML** : OpenID Connect et SAML sont utilisés pour authentifier un utilisateur et sont utilisés pour activer l’authentification unique. L’authentification SAML est couramment utilisée avec des fournisseurs d’identité tels que les services de fédération Active Directory (ADFS) fédérés à Entra ID et sont donc fréquemment utilisés dans les applications d’entreprise. OpenID Connect est couramment utilisé pour les applications qui se trouvent uniquement dans le cloud, telles que les applications mobiles, les sites web et les API web.

Si vous avez une application que vous souhaitez intégrer à l’ID Entra pour fournir l’expérience d’authentification unique pour vos utilisateurs, consultez l’article ClaimsXRay dans Entra ID avec l’extension d’annuaire, lié ci-dessous :

[ClaimsXRay dans Entra ID avec Extension d'annuaire](https://techcommunity.microsoft.com/t5/core-infrastructure-and-security/claimsxray-in-azuread-with-directory-extension/ba-p/1505737)


## Implémenter le provisionnement d’utilisateurs basé sur l’application

Dans Entra ID, le terme approvisionnement d’applications fait référence à la création automatique d’identités et de rôles utilisateur dans les applications [SaaS](https://azure.microsoft.com/overview/what-is-saas/) (Cloud) auxquelles les utilisateurs ont besoin d’accéder. Outre la création d’identités utilisateur, l’approvisionnement automatique inclut la maintenance et la suppression des identités utilisateur au fur et à mesure que l’état ou les rôles changent. Un scénario courant consiste à approvisionner un utilisateur Entra dans des applications telles que [Dropbox](https://learn.microsoft.com/fr-fr/azure/active-directory/saas-apps/dropboxforbusiness-provisioning-tutorial), [Salesforce](https://learn.microsoft.com/fr-fr/azure/active-directory/saas-apps/salesforce-provisioning-tutorial), [ServiceNow](https://learn.microsoft.com/fr-fr/azure/active-directory/saas-apps/servicenow-provisioning-tutorial), etc.

![Diagramme du flux de processus pour l’approvisionnement. Vous pouvez automatiser et régir le processus d’approvisionnement.](https://learn.microsoft.com../../wwl-sci/implement-monitor-integration-of-enterprise-apps-for-sso/media/provision-overview.png)

Cette fonctionnalité vous permet d’effectuer les actions suivantes.

- **Automatiser l’approvisionnement** : créez automatiquement de nouveaux comptes dans les systèmes appropriés pour les nouvelles personnes lorsqu’elles rejoignent une équipe ou une organisation.
- **Automatiser le déprovisionnement** : désactivez automatiquement les comptes dans les systèmes appropriés lorsque les personnes quittent une équipe ou une organisation.
- **Synchronisez les données entre les systèmes :** maintenez les identités des applications et des systèmes à jour en fonction des modifications apportées à l’annuaire ou au système de ressources humaines.
- **Groupes de provisionnement** : provisionnement d’un groupe pour les applications qui les prennent en charge.
- **Régir l’accès :** Surveiller et auditer ceux à qui l'accès a été attribué dans les applications.
- **Déployer en toute transparence dans les scénarios « brown field » :** faites correspondre les identités existantes entre les systèmes et facilitez l’intégration, même lorsque les utilisateurs existent déjà dans le système cible.
- **Utiliser une personnalisation riche :** tirez parti des mappages d’attributs personnalisables qui définissent les données utilisateurs qui doivent circuler entre le système source et le système cible.
- **Obtenir des alertes pour les événements critiques :** le service d’approvisionnement fournit des alertes pour les événements critiques. Il permet aussi une intégration de Log Analytics, où vous définissez des alertes personnalisées adaptées aux besoins de votre entreprise.

### Provisionnement manuel ou automatique

Les applications de la galerie Entra ID prennent en charge l’approvisionnement manuel ou automatique.

- L’approvisionnement manuel signifie qu’il n’existe pas encore de connecteur d’approvisionnement Entra automatique pour l’application. Les comptes d’utilisateur doivent être créés manuellement. Par exemple, l’ajout d’utilisateurs directement dans le portail d’administration de l’application ou le chargement d’une feuille de calcul avec les détails du compte d’utilisateur. Consultez la documentation fournie par l’application ou contactez le développeur de l’application pour déterminer les mécanismes disponibles.
- Cela signifie automatiquement qu’un connecteur de provisionnement Entra a été développé pour cette application. Suivez le tutoriel d’installation pour configurer l’approvisionnement de l’application.

Dans la galerie Entra ID, les applications qui prennent en charge l’approvisionnement automatique sont désignées par une icône **d’approvisionnement** .

Le mode d’approvisionnement pris en charge par une application est également visible sous l’onglet **Approvisionnement** une fois que vous avez ajouté l’application à vos **applications d’entreprise**.

### Système de gestion des identités inter-domaines

Pour aider à automatiser l’approvisionnement et le déprovisionnement, les applications exposent les API propriétaires d’utilisateurs et de groupes. Toutefois, chaque application tente d’effectuer les mêmes actions, telles que la création ou la mise à jour d’utilisateurs, l’ajout d’utilisateurs à des groupes ou le déprovisionnement des utilisateurs. Pourtant, chacune de ces actions simples est implémentée légèrement différemment : chemins de point de terminaison différents, méthodes différentes pour spécifier les informations utilisateur et schéma différent pour représenter chaque élément d’informations.

Pour relever ces défis, la spécification SCIM (System for Cross-domain Identity Management) fournit un schéma utilisateur commun pour aider les utilisateurs à se déplacer dans, hors et autour des applications. SCIM devient la norme pour l’approvisionnement. Utilisé conjointement avec des normes de fédération telles que SAML ou OpenID Connect, il fournit aux administrateurs une solution de bout en bout, basée sur des normes, pour la gestion des accès.

### Créer un système pour le point de terminaison de la gestion des identités inter-domaines et configurer l'approvisionnement des utilisateurs avec Entra ID

En tant que développeur d’applications, vous pouvez approvisionner automatiquement les utilisateurs et les groupes entre votre application et Entra ID grâce à l’API de gestion des utilisateurs SCIM (System for Cross-Domain Identity Management). La spécification SCIM fournit un schéma utilisateur commun pour l’approvisionnement. Utilisé conjointement avec les normes de fédération telles que SAML ou OpenID Connect, SCIM offre aux administrateurs une solution de bout en bout, basée sur des normes, pour la gestion des accès.

SCIM est une définition standardisée de deux points de terminaison : un point de terminaison /Users et un point de terminaison /Groups. Il utilise des verbes REST (Representational State Transfer) courants pour créer, mettre à jour et supprimer des objets, ainsi qu’un schéma prédéfini pour les attributs courants : nom de groupe, nom d’utilisateur, prénom, nom et e-mail. Les applications proposant une API REST SCIM 2.0 peuvent réduire ou éliminer les difficultés liées à l’utilisation d’une API de gestion des utilisateurs propriétaires. Par exemple, tout client SCIM conforme sait comment effectuer une requête HTTP POST avec un objet JSON à l'endpoint /Users pour créer une nouvelle entrée utilisateur. Au lieu d’avoir besoin d’une API légèrement différente pour les mêmes actions de base, les applications conformes à la norme SCIM peuvent tirer instantanément parti des clients, outils et code préexistants.

![Diagramme de l'identifiant Entra avec l'approvisionnement des utilisateurs partageant des données avec des applications externes.](https://learn.microsoft.com../../wwl-sci/implement-monitor-integration-of-enterprise-apps-for-sso/media/system-for-cross-domain-identity-management-provision-overview.png)

Le schéma d’objet utilisateur standard et les API REST pour la gestion définie dans SCIM 2.0 permettent aux fournisseurs d’identité et aux applications de s’intégrer les uns aux autres plus facilement. Les développeurs d’applications qui créent un point de terminaison SCIM peuvent s’intégrer à n’importe quel client conforme À SCIM sans avoir à effectuer de travail personnalisé. Au lieu de commencer à partir de zéro et de créer l’implémentation entièrement par vous-même, vous pouvez vous appuyer sur un certain nombre de bibliothèques SCIM open source publiées par la communauté SCIM.


## Surveiller et auditer l’accès aux applications d’entreprise intégrées Entra

Avec les rapports d’ID Entra, vous pouvez obtenir les informations nécessaires pour déterminer la façon dont votre environnement fonctionne. Avec le rapport d’utilisation et d’insights, vous pouvez obtenir une vue centrée sur l’application de vos données de connexion et trouver des réponses aux questions suivantes :

- Quelles sont les principales applications utilisées dans l’organisation ?
- Quelles sont les applications affichant le plus d’échecs de connexion ?
- Quelles sont les principales erreurs de connexion pour chaque application ?

### Accès au rapport d’utilisation et d’insights

1. Accédez au [Centre d’administration Entra](https://entra.microsoft.com/).
2. Sélectionnez le menu Identité, puis sélectionnez **Applications** et choisissez **Applications d’entreprise**.
3. Dans la section **Activité** , sélectionnez **Utilisation et insights** pour ouvrir le rapport.

### Utiliser le rapport

Le rapport d’utilisation et d’insights affiche la liste des applications ayant enregistré une ou plusieurs tentatives de connexion. Vous pouvez le trier par nombre de connexions réussies, de connexions ayant échoué et par taux de réussite.

La sélection de **voir plus** en bas de la liste vous permet d’afficher davantage d’applications sur la page. Vous pouvez sélectionner la plage de dates afin d’afficher toutes les applications utilisées dans cette plage.

Vous pouvez également définir le focus sur une application spécifique. Sélectionnez **afficher l’activité de connexion** pour afficher l’activité de connexion au fil du temps pour l’application et les erreurs principales.

Lorsque vous sélectionnez un jour dans le graphique d’utilisation des applications, vous obtenez une liste détaillée des activités de connexion pour l’application.

### Journaux d’audit

Les journaux d’audit Entra fournissent des enregistrements des activités du système pour la conformité. Les utilisateurs des rôles Administrateur de sécurité, Lecteur de sécurité, Lecteur de rapport, Lecteur général ou Administrateur peuvent accéder à leurs données. Pour accéder au rapport d’audit, sélectionnez **Journaux d’audit** dans la section **Supervision** de **Entra ID**.

Un journal d’audit a une vue de liste par défaut qui affiche :

- date et heure de l’occurrence
- le service qui a enregistré l’occurrence
- la catégorie et le nom de l’activité (quoi)
- l’état de l’activité (réussite ou échec)
- la cible
- l’initiateur/intervenant d’une activité (qui)

Vous pouvez personnaliser le mode Liste en cliquant sur **Colonnes** dans la barre d’outils.

Cela vous permet d’afficher d’autres champs ou de supprimer des champs déjà affichés.

Sélectionnez un élément dans la vue sous forme de liste pour obtenir des informations plus détaillées.

### Journaux d’audit d’applications d’entreprise

Les rapports d’audit basés sur les applications vous permettent d’obtenir des réponses aux questions telles que :

- Quelles applications ont été ajoutées ou mises à jour ?
- Quelles applications ont été supprimées ?
- Le principal de service d’une application a-t-il changé ?
- Les noms des applications ont-ils été modifiés ?
- Qui a donné son consentement à une application ?

Si vous souhaitez consulter les données d’audit associées à vos applications, vous pouvez trouver une vue filtrée sous **Journaux d’audit** dans la section **Activité** de l’écran **Applications d’entreprise**. Dans ce point d’entrée, **Applications d’entreprise** est présélectionné comme **Type d'application**.

## Créer et gérer des collections d’applications

Vos utilisateurs peuvent utiliser le portail Mes applications pour afficher et démarrer les applications cloud auxquelles ils ont accès. Par défaut, toutes les applications auxquelles un utilisateur peut accéder sont répertoriées sur une seule page. Pour mieux organiser cette page pour vos utilisateurs, si vous disposez d’une licence Entra ID Premium P1 ou P2, vous pouvez configurer des collections. Avec une collection, vous pouvez regrouper des applications associées (par exemple, par rôle de travail, tâche ou projet). Ensuite, ils s’affichent sous un onglet distinct pour faciliter l’utilisation. Une collection applique essentiellement un filtre aux applications auxquelles un utilisateur peut déjà accéder, de sorte que l’utilisateur voit uniquement ces applications dans la collection qui lui ont été affectées.

### Créer et administrer une collection d’applications

Les collections d’administration sont gérées via le portail Azure. Par exemple, si vous affectez des utilisateurs ou des groupes en tant que propriétaire, ils peuvent uniquement gérer la collection via le portail Azure.

1. Ouvrez le Centre d’administration Entra et connectez-vous en tant qu’administrateur.
2. Accédez à **Identity**, puis ouvrez le menu **Applications** , puis sélectionnez **Applications d’entreprise**.
3. Sous **Gérer**, sélectionnez **Lanceurs d’applications**.
4. Sélectionnez **Nouvelle collection**.

- Dans la page Nouvelle collection, entrez un nom pour la collection (nous vous recommandons de ne pas utiliser « collection » dans le nom. Entrez ensuite une description.

1. Sélectionnez **l’onglet Applications**. Sélectionnez **+ Ajouter une application** pour ouvrir la page Ajouter des applications.

- Sélectionnez toutes les applications que vous souhaitez ajouter à la collection ou utilisez la zone de recherche pour rechercher des applications.

1. Lorsque vous avez fini d’ajouter des applications, sélectionnez **Ajouter**.

- La liste des applications sélectionnées s’affiche. Vous pouvez utiliser les flèches pour modifier l’ordre des applications dans la liste.

1. Sélectionnez **l’onglet Propriétaires**. Sélectionnez **+ Ajouter des utilisateurs et des groupes** pour ouvrir la page Ajouter des utilisateurs et des groupes
2. Sélectionnez les utilisateurs ou les groupes auxquels vous souhaitez attribuer la propriété.
3. Une fois que vous avez fini de sélectionner les utilisateurs et groupes, choisissez **Sélectionner**.
4. Sélectionnez Vérifier + créer. Les propriétés de la nouvelle collection apparaissent.

### Portail Mes applications

Vous pouvez également utiliser le portail [Mes applications](https://myapps.microsoft.com) (`https://myapps.microsoft.com`) pour ajouter des collections d’applications. Mes applications est un portail Web utilisé pour gérer et lancer des applications dans Entra ID. Pour travailler avec des applications dans Mes applications, utilisez un compte d’organisation dans Entra ID et obtenez l’accès accordé par l’administrateur Entra. Mes applications sont séparées du portail Azure et ne nécessitent pas que les utilisateurs disposent d’un abonnement Azure ou d’un abonnement Microsoft 365.

Les utilisateurs accèdent au portail Mes applications pour :

- découvrir les applications auxquelles ils ont accès ;
- Demander de nouvelles applications que l'organisation prend en charge pour le libre-service
- créer des collections personnelles d’applications ;
- gérer l’accès aux applications.

Par défaut, toutes les applications sont répertoriées sur une seule page. Les collections permettent de regrouper des applications associées, puis de les présenter sous un onglet distinct, ce qui les rend plus faciles à trouver. Par exemple, vous pouvez utiliser des collections pour créer des regroupements logiques d’applications pour des rôles de travail, des tâches, des projets, et autres ressources spécifiques. Chaque application à laquelle un utilisateur a accès apparaît dans la collection d’applications par défaut. Un utilisateur peut toutefois supprimer des applications de la collection.

#### Créer une collection à l’aide du portail Mes applications

Procédez comme suit pour créer une collection.

1. Ouvrez le **portail [Mes applications](https://myapps.microsoft.com)**.
2. Sélectionnez les points de suspension (...) dans l’écran des applications.
3. Choisissez **Gérer les regroupements.**
4. Sélectionnez **Créer une collection.**
5. Sélectionnez l’option **+ Ajouter des applications** pour ajouter toutes les applications souhaitées dans la collection.
6. Après avoir sélectionné vos applications, sélectionnez le bouton **Ajouter des applications sélectionnées** .
7. Donnez un nom à la collection et choisissez **Créer une collection**.


## Contrôle des connaissances

Choisissez la meilleure réponse à chacune des questions ci-dessous.

### Vérifiez vos connaissances


## Résumé et ressources

Après avoir terminé ce module, vous pouvez :

- Implémenter des personnalisations de jetons
- Implémenter et configurer les paramètres de consentement
- Intégrer des applications locales à l’aide du proxy d’application Entra
- Intégrer des applications SaaS personnalisées pour le SSO (authentification unique)
- Mettre en œuvre le provisionnement des utilisateurs d'application
- Créer et gérer des collections d’applications
- Surveiller et auditer l’accès/l’authentification aux applications d’entreprise intégrées Entra ID

### Ressources

Utilisez ces ressources pour en savoir plus.

- [ClaimsXRay dans Entra ID avec Extension d'annuaire](https://techcommunity.microsoft.com/t5/core-infrastructure-and-security/claimsxray-in-azuread-with-directory-extension/ba-p/1505737)
- [Configurer la gestion des sessions d’authentification](https://learn.microsoft.com/fr-fr/entra/identity/conditional-access/howto-conditional-access-session-lifetime)
- [Vue d’ensemble du portail Mes applications](https://learn.microsoft.com/fr-fr/entra/identity/enterprise-apps/myapps-overview)
- [Créer des collections sur le portail Mes applications](https://learn.microsoft.com/fr-fr/entra/identity/enterprise-apps/access-panel-collections)


---

# Implémenter l’inscription d’application

_https://learn.microsoft.com/fr-fr/training/modules/implement-app-registration/_


## Présentation

Dans ce module, vous planifiez votre stratégie d’inscription d’application métier, implémentez les inscriptions d’applications et configurez les autorisations d’application.

### Objectifs d’apprentissage

Dans ce module, vous allez découvrir les points suivants :

- Planifier votre stratégie d’inscription d’application métier.
- Implémentez les enregistrements d’applications.
- Configurez les autorisations d’application.
- Établissez et gérez un processus de gouvernance des applications.

### Conditions préalables

- Expérience à l’aide des portails d’administration Microsoft Cloud.
- Expérience précédente avec les applications cloud et locales.


## Planifier votre stratégie d’inscription d’application métier

Cette unité explique pourquoi les applications s’intègrent à Entra ID. Ajoutez des applications à Entra ID pour appliquer un ou plusieurs des services qu'il fournit, notamment :

- L’authentification et l’autorisation de l’application.
- L’authentification et l’autorisation de l’utilisateur.
- L’authentification unique (SSO) à l’aide de la fédération ou du mot de passe.
- La configuration et la synchronisation de l’utilisateur.
- Le contrôle d’accès basé sur les rôles : utilisez le répertoire pour définir les rôles d’application, afin d’effectuer des vérifications d’autorisation basées sur les rôles dans une application.
- Les services d’autorisation OAuth : utilisés par Microsoft 365 et d’autres applications Microsoft pour autoriser l’accès aux API/ressources.
- La publication et le proxy d’applications : publiez une application sur Internet à partir d’un réseau privé.
- Attributs d'extension du schéma d'annuaire : Élargissez le schéma des objets « principal de service » et « utilisateur » pour stocker des données supplémentaires dans Entra ID.

Il existe deux représentations d'applications dans Entra ID : les [objets d'application](https://learn.microsoft.com/fr-fr/entra/identity-platform/app-objects-and-service-principals) et les principaux de service. Les deux sections suivantes expliquent ces représentations, ainsi que la façon dont elles interagissent les unes avec les autres dans le Portail Azure.

### À quoi correspondent les objets d’application et d’où viennent-ils ?

Vous pouvez gérer des objets d’application dans le portail Azure via Inscriptions d’application. Les objets d’application définissent et décrivent l’application à Entra ID, ce qui permet à votre fournisseur d’identité de savoir comment émettre des jetons pour l’application en fonction de ses paramètres. L’objet d’application existe uniquement dans son répertoire de base, même s’il s’agit d’une application multilocataire prenant en charge des principaux de service dans d’autres répertoires. L’objet d’application inclut les éléments suivants (ainsi que d’autres informations non mentionnées ici) :

- Nom, logo et éditeur
- URI de redirection
- Secrets (clés symétriques et/ou asymétriques utilisées pour authentifier l’application)
- Dépendances d’API (OAuth)
- API/ressources/étendues publiées (OAuth)
- Rôles d'application (RBAC)
- Configuration et métadonnées de l’authentification unique
- Configuration et métadonnées du déploiement de l'utilisateur
- Configuration et métadonnées du proxy

Vous pouvez créer des objets d’application par le biais de plusieurs chemins d’opérations, notamment :

- Via les inscriptions d’application dans le portail Azure.
- Créer une nouvelle application à l'aide de Visual Studio et la configurer pour utiliser l'authentification Entra
- Lorsqu’un administrateur ajoute une application à partir de la galerie d’applications (ce qui crée également un principal de service).
- En utilisant l’API Microsoft Graph ou PowerShell pour créer une application.
- De nombreuses autres voies, y compris diverses expériences de développeur dans Azure et des expériences d'explorateur d'API dans les centres de développeurs.

### À quoi correspondent les principaux de service et d’où proviennent-ils ?

Vous pouvez gérer les principaux de service dans le portail Azure via les Applications d’entreprise. Les principaux services régissent une application qui se connecte à Entra ID et peuvent être considérés comme l'instance de l'application dans votre répertoire. Pour une application donnée, le principal de service peut avoir au maximum un objet d’application, inscrit dans un annuaire de base. Il peut aussi avoir un ou plusieurs objets de principal de service, qui représentent les instances de l’application dans tous les annuaires où elle agit.

Le principal de service peut inclure :

- Une référence à un objet d’application via la propriété d’ID d’application.
- Des enregistrements des attributions de rôle de l’application de l’utilisateur local et du groupe.
- Des enregistrements des autorisations de l’utilisateur local et de l’administrateur accordées à l’application.
  - Par exemple : autorisation pour l’application d’accéder à un e-mail d’utilisateur particulier.

- Des enregistrements des stratégies locales, y compris une stratégie d’accès conditionnel.
- Des enregistrements des paramètres locaux alternatifs pour une application.
  - Revendication des règles de transformation.
  - Mappages d'attributs (déploiement de l'utilisateur).
  - Rôles d’application spécifiques de l’annuaire (si l’application prend en charge les rôles personnalisés).
  - Logo ou nom spécifique de l’annuaire.

Comme les objets d’application, les principaux de service peuvent être créés via plusieurs chemins d’accès, notamment :

- Lorsque les utilisateurs se connectent à une application tierce intégrée à Entra ID.
  - Lors de la connexion, les utilisateurs sont invités à autoriser l’application à accéder à leur profil et à effectuer d’autres actions. Dès que la première personne donne son consentement, le principal de service représentant l’application est ajouté à l’annuaire.

- Lorsque les utilisateurs se connectent aux services en ligne de Microsoft comme Microsoft 365.
  - Lorsque vous vous abonnez à Microsoft 365 ou commencez une version d’évaluation, un ou plusieurs principaux de service sont créés dans l’annuaire. Ils représentent les différents services utilisés pour transmettre toutes les fonctionnalités associées à Microsoft 365.
  - Certains services de Microsoft 365 tels que SharePoint créent des principaux de service sur une base continue, afin de sécuriser les communications entre les composants, y compris les flux de travail.

- Lorsqu’un administrateur ajoute une application à partir de la galerie d’applications (cette opération crée également un objet d’application sous-jacent).
- Ajoutez une application pour utiliser le proxy d’application Entra.
- Connectez une application pour l’authentification unique à l’aide de SAML ou de l’authentification unique par mot de passe.
- Par programmation via l’API Microsoft Graph ou PowerShell.

### Quel est le lien entre les objets d’application et les principaux de service ?

Une application possède un objet d’application dans son répertoire de départ. Un ou plusieurs principaux de service le référencent, dans chacun des répertoires où elle s’exécute (y compris le répertoire de démarrage de l’application).

![Diagramme de la relation entre les objets d’application et les principaux de service.](https://learn.microsoft.com../../wwl-sci/implement-app-registration/media/how-apps-added-azure-active-directory.png)

Dans le schéma ci-dessus, Microsoft gère deux annuaires en interne (représentés à gauche), qu’il utilise pour publier des applications :

- Une pour Microsoft Apps (annuaire de services Microsoft).
- Un pour des applications tierces préintégrées (répertoire de la galerie d’applications).

Les fournisseurs/éditeurs d'applications qui s'intègrent à Entra ID doivent avoir un répertoire de publication (représenté à droite en tant que « Répertoire SaaS »).

Les applications que vous ajoutez (représentées en tant que « (vos) applications » dans le schéma) incluent :

- Les applications que vous avez développées (intégrées à Entra ID).
- Les applications que vous avez connectées pour l’authentification unique.
- Les applications que vous avez publiées en utilisant le proxy d’application Entra.

#### Remarques et exceptions aux principaux de service

Tous les principaux de service ne pointent pas vers un objet d’application. Lors de la création d’Entra ID, les services fournis aux applications étaient plus limités et le principal de service suffisait à établir l'identité d'une application. Le principal du service d'origine était plus proche en termes de forme du compte de service Windows Server Active Directory. Pour cette raison, il est toujours possible de créer des principaux de service via diverses méthodes, telles que l’utilisation de PowerShell, sans créer en premier un objet d’application. L’API Microsoft Graph requiert un objet d’application avant de pouvoir créer un principal de service.

Actuellement, toutes les informations décrites ci-dessus sont exposées par programmation. Les éléments suivants sont uniquement disponibles dans l'interface utilisateur :

- Revendication des règles de transformation
- Mappages d'attributs (déploiement de l'utilisateur)

Pour plus d’informations détaillées sur le principal de service et les objets d’application, consultez la documentation de référence sur l’API Microsoft Graph :

- Application
- Principal de service

### Ajout d’une nouvelle inscription d’application

![Diagramme de la relation entre les objets d’application et les principaux de service, avec focus sur le flux du processus.](https://learn.microsoft.com../../wwl-sci/implement-app-registration/media/register-new-app.png)

**Flux du processus du diagramme**

1. L’utilisateur demande à inscrire une application : un jeton de demande est émis.
2. Le point de terminaison d’autorisation renvoie une authentification.
3. L’utilisateur consent à ce que l’application soit inscrite.
4. Le service est créé à partir de l’application
5. Le jeton est retourné à l’utilisateur.

### Qui a l'autorisation d'ajouter des applications à mon instance Entra ?

Vous pouvez attribuer des rôles tels que l’administrateur d’application et l’administrateur d’applications cloud pour effectuer ces tâches. Vous **devez vous rappeler** que, par défaut, tous les utilisateurs de votre annuaire ont des droits pour enregistrer les objets d’application qu’ils développent. Ils décident aussi des applications qu’ils partagent/auxquelles ils donnent accès à leurs données organisationnelles par le biais du consentement. Lorsque le premier utilisateur de votre annuaire se connecte à une application, et donne son consentement, cela crée un principal de service. Sinon, les informations d’octroi de consentement sont stockées sur le principal de service existant.

Permettre aux utilisateurs d’inscrire des applications et de donner leur consentement peut, à première vue, sembler inquiétant, mais n’oubliez pas les points suivants :

- Les applications sont capables de tirer parti de Windows Server Active Directory pour l’authentification utilisateur depuis de nombreuses années sans que l’application ait besoin d’être inscrite ou enregistrée dans l’annuaire. Désormais, l’organisation disposera d’une visibilité améliorée sur le nombre précis d’applications qui utilisent l’annuaire, et pour quelles raisons.
- La délégation de ces responsabilités aux utilisateurs supprime le besoin d’avoir un processus de publication et d’inscription des applications piloté par un administrateur. Avec les services de fédération Active Directory (AD FS), un administrateur a probablement dû ajouter une application en tant que partie de confiance pour le compte de ses développeurs. Maintenant, les développeurs peuvent se déployer eux-mêmes (libre-service).
- La connexion des utilisateurs à des applications à l’aide de leur compte d’organisation à des fins professionnelles est un point positif. Par la suite, s’ils quittent l’organisation, ils perdront automatiquement l’accès au compte qu’ils utilisaient pour cette application.
- Il est bon de disposer d'un enregistrement permettant de savoir avec quelle application les données ont été partagées. Les données sont plus que jamais transportables, et il est utile de disposer d’un enregistrement précisant qui a partagé quelles données, et à l’aide de quelles applications.
- Les propriétaires d’API qui utilisent Entra ID pour OAuth décident en détail des autorisations que les utilisateurs sont en mesure d’accorder aux applications et des autorisations nécessitant un administrateur pour les confirmer. Seuls les administrateurs peuvent donner leur consentement pour des étendues plus larges et des autorisations plus importantes. Le consentement de l’utilisateur se limite aux propres fonctionnalités et données de celui-ci.
- Lorsqu’un utilisateur ajoute ou autorise une application à accéder à ses données, l’événement peut être audité. Vous pouvez afficher les rapports d’audit dans le Portail Azure pour déterminer la façon dont une application a été ajoutée à l’annuaire.

Deux paramètres vous permettent de désactiver ces capacités, si vous souhaitez toujours empêcher les utilisateurs de votre annuaire d’inscrire des applications et de se connecter à des applications sans l’approbation d’un administrateur :

Pour empêcher les utilisateurs de donner leur consentement pour leur propre compte :

- Dans le portail Azure, accédez à la section Paramètres utilisateur sous Applications d’entreprise.
- Définissez le paramètre **Les utilisateurs peuvent autoriser les applications à accéder aux données de l’entreprise en leur nom** sur **Non**.  Notes Si vous décidez de désactiver le consentement de l’utilisateur, un administrateur devra donner son consentement pour chaque nouvelle application qu’un utilisateur utilisera.

Pour empêcher les utilisateurs d’inscrire leurs propres applications :

- Dans le portail Azure, accédez à la section Paramètres utilisateur sous Entra ID.
- Définissez le paramètre **Les utilisateurs peuvent inscrire des applications** sur **Non**.

### Location dans Entra ID

Entra organise des objets comme des utilisateurs et des applications dans des groupes appelés *tenants*. Les locataires permettent à un administrateur de définir des stratégies sur les utilisateurs au sein de l’organisation et les applications appartenant à l’organisation pour répondre à leurs stratégies de sécurité et opérationnelles.

#### Qui peut accéder à votre application ?

Lorsqu’il s’agit de développer des applications, les développeurs peuvent choisir de configurer leur application pour être monolocataire ou multilocataire lors de l’inscription d’application dans le portail Microsoft Azure.

- Les applications mono-locataires ne sont disponibles que dans le locataire dans lequel elles ont été inscrites, également appelé leur locataire de base.
- Les applications multilocataires sont à la disposition des utilisateurs dans leur tenant de base et d’autres tenants.

Dans le Portail Azure, vous pouvez configurer votre application pour qu’elle soit unique ou multilocataire en définissant l’audience comme suit :

**Accès à des applications spécifiques**

| **Audience** | **Monolocataire/multilocataire** | **Qui peut se connecter** |
|---|---|---|
| Comptes dans cet annuaire uniquement | Locataire unique | Tous les comptes d’utilisateur et d’invité dans votre annuaire peuvent utiliser votre application ou API. *Utilisez cette option si votre audience cible est interne à votre organisation.* |
| Comptes dans n’importe quel répertoire Entra | Multi-locataire | Tous les utilisateurs et invités avec un compte professionnel ou scolaire Microsoft peuvent utiliser votre application ou API. Cela inclut les établissements scolaires et les entreprises qui utilisent Microsoft 365. *Utilisez cette option si votre audience cible est constituée de clients d’entreprise ou du secteur éducatif.* |
| Comptes dans n’importe quel répertoire Entra et des comptes Microsoft personnels (tels que Skype, Xbox, Outlook.com) | Multi-locataire | Tous les utilisateurs avec un compte professionnel, scolaire, ou personnel Microsoft, peuvent utiliser votre application ou API. Cela inclut les établissements scolaires et les entreprises qui utilisent Microsoft 365, ainsi que les comptes personnels utilisés pour se connecter à des services tels que Xbox et Skype. *Utilisez cette option pour cibler l’ensemble plus large de comptes Microsoft.* |

#### Meilleures pratiques pour les applications multilocataires

La création d’excellentes applications multilocataires peut s’avérer difficile en raison du nombre de stratégies différentes que les administrateurs informatiques peuvent définir dans leurs tenants. Si vous choisissez de créer une application multilocataire, suivez ces meilleures pratiques :

- Testez votre application dans un locataire dans lequel des stratégies d’accès conditionnel sont configurées.
- Suivez le principe de moindre accès utilisateur pour vous assurer que votre application demande uniquement des autorisations dont elle a réellement besoin.
- Fournissez les noms et descriptions appropriés de toutes les autorisations que vous exposez dans le cadre de votre application. Cela permet aux utilisateurs et administrateurs de savoir ce qu’ils sont autorisés à faire quand ils tentent d’utiliser les API de votre application. Pour plus d’informations, consultez la section des meilleures pratiques dans le guide des autorisations.


## Implémenter l’inscription d’application

Chaque application pour laquelle vous souhaitez que la plateforme d’identités Microsoft effectue une gestion des identités et des accès (IAM) doit être inscrite. Inscrivez une application dans le portail Azure afin que la plateforme d’identités Microsoft puisse fournir des services d’authentification et d’autorisation pour votre application et ses utilisateurs. L’inscription établit une relation d’approbation entre votre application et le fournisseur d’identité, la plateforme d’identités Microsoft. C’est vrai pour une application cliente, comme une application web ou mobile, comme pour une API web qui sauvegarde une application cliente.


## Inscrire une application

L’inscription de votre application établit une relation d’approbation entre votre application et la plateforme d’identités Microsoft. L’approbation est unidirectionnelle : votre application approuve la plateforme d’identités Microsoft, et non le contraire.

1. Connectez-vous au [Centre d’administration Entra](https://entra.microsoft.com/) à l’aide d’un compte Administrateur.
2. Ouvrez le menu du portail, puis sélectionnez **Identité**.
3. Dans le menu **Identité**, sous **Applications**, sélectionnez **Inscriptions d’applications.**
4. Dans la page **Inscriptions d’applications**, dans le menu, sélectionnez **+ Nouvelle inscription**.
5. Dans la boîte de dialogue **Inscrire une application**, inscrivez une application nommée **Demo App** en utilisant les valeurs par défaut. Vous n’avez pas besoin d’entrer l’URI de redirection.
6. Une fois terminé, vous serez redirigé vers l’écran de **Demo app**.

### Ajouter un URI de redirection

Un URI de redirection est l’emplacement où la plateforme d’identités Microsoft redirige le client d’un utilisateur et envoie des jetons de sécurité après authentification. Dans une application web de production, par exemple, l’URI de redirection est souvent un point de terminaison public sur lequel votre application s’exécute. Pendant le développement, il est courant d’ajouter également le point de terminaison dans lequel vous exécutez votre application localement.

Pour ajouter et modifier des URI de redirection pour vos applications inscrites, vous devez configurer leurs paramètres de plateforme.

### Configurer des paramètres de plateforme

Les paramètres de chaque type d’application, dont les URI de redirection, sont configurés dans **Configurations de plateforme** dans le Portail Azure. Certaines plateformes, comme le **web** et les **applications monopages**, nécessitent de spécifier manuellement un URI de redirection. Pour les autres plateformes, comme les plateformes mobiles et de bureau, vous pouvez sélectionner des URI de redirection générés automatiquement quand vous configurez leurs autres paramètres.

Pour configurer des paramètres d’application en fonction de la plateforme ou de l’appareil ciblé :

1. Sélectionnez votre application dans les **Inscriptions d’applications** dans le Portail Azure.
2. Sous **Gérer**, sélectionnez **Authentification**.
3. Sous **Configurations de plateformes**, sélectionnez **Ajouter une plateforme**.
4. Dans **Configurer des plateformes**, sélectionnez la vignette correspondant à votre type d’application (plateforme) pour configurer ses paramètres.      **Plateforme** **Paramètres de configuration**     Le Web Entrez un **URI de redirection** pour votre application, qui est l’emplacement où la plateforme d’identités Microsoft redirige le client d’un utilisateur et envoie des jetons de sécurité après authentification. Sélectionnez cette plateforme pour les applications web standard qui s’exécutent sur un serveur.   Application monopage Entrez un **URI de redirection** pour votre application, qui est l’emplacement où la plateforme d’identités Microsoft redirige le client d’un utilisateur et envoie des jetons de sécurité après authentification. Sélectionnez cette plateforme si vous générez une application web côté client dans JavaScript ou avec un framework comme Angular, Vue.js, React.js ou Blazor WebAssembly.   iOS/macOS Entrez l'**ID d’ensemble** d'applications, qui se trouve dans XCode dans *Info.plist* ou « Paramètres du build ». Un URI de redirection est généré pour vous lorsque vous spécifiez un ID d’ensemble.   Android Entrez le **nom du package** d’application, que vous trouverez dans le fichier AndroidManifest.xml, puis générez et entrez le **code de hachage de la signature**. Un URI de redirection est généré pour vous lorsque vous spécifiez ces paramètres.   Applications de bureau et mobiles Sélectionnez l’un des **URI de redirection suggérés** ou spécifiez un **URI de redirection personnalisé**. Pour les applications de bureau, nous vous recommandons : https://login.microsoftonline.com/common/oauth2/nativeclientSélectionner cette plateforme pour les applications mobiles qui n’utilisent pas la dernière bibliothèque d’authentification Microsoft (MSAL) ou qui n’utilisent pas de répartiteur. Sélectionnez également cette plateforme pour les applications de bureau.
5. Sélectionnez **Configurer** pour effectuer la configuration de la plateforme.

### Ajouter des informations d’identification

Les informations d’identification sont utilisées par les applications clientes confidentielles qui accèdent à une API web. Les applications web, les autres API web ou les applications de type service et démon sont des exemples de clients confidentiels. Les informations d’identification permettent à votre application de s’authentifier de façon autonome, sans qu’aucune interaction utilisateur ne soit nécessaire au moment de l’exécution.

Vous pouvez ajouter des certificats et des secrets clients (une chaîne) en tant qu’informations d’identification à votre inscription d’application cliente confidentielle.

### Ajouter un certificat

Parfois appelés *clé publique*, les certificats sont le type d’informations d’identification recommandé, car ils fournissent un niveau d’assurance plus élevé qu’un secret client. Lors de l’utilisation d’un certificat public approuvé, vous pouvez ajouter le certificat à l’aide de la fonctionnalité « Certificats et secrets ». Votre certificat doit être un fichier de type : `.cer`, `.pem`, `.crt`.

### Ajouter une clé secrète client

Le secret client, également appelé *mot de passe d’application*, est une valeur de chaîne que votre application peut utiliser à la place d’un certificat pour s’identifier. Il est le plus facile des deux types d’informations d’identification à utiliser. Il est souvent utilisé pendant le développement, mais il est considéré comme moins sécurisé qu’un certificat. Vous devez utiliser des certificats dans vos applications qui s’exécutent en production.

1. Sélectionnez votre application dans les **Inscriptions d’applications** dans le Portail Azure.
2. Sélectionnez **Certificats et secrets**, puis **Nouveau secret client**.
3. Ajoutez une description pour votre clé secrète client.
4. Sélectionnez une durée.
5. Sélectionnez **Ajouter**.
6. **Enregistrez la valeur du secret** pour une utilisation dans le code de votre application cliente. Une fois que vous avez quitté cette page, elle *ne s’affiche plus*.

### Inscrire l’API web

Pour fournir un accès délimité aux ressources de votre API web, vous devez d’abord inscrire l’API auprès de la plateforme d’identités Microsoft.

1. Effectuez les étapes ci-dessus.
2. Ignorez les sections **Ajouter un URI de redirection** et **Configurer les paramètres de plateforme**. Vous n’avez pas besoin de configurer un URI de redirection pour une API web, car aucun utilisateur n’est connecté de manière interactive.
3. Ignorez la section **Ajouter des informations d’identification** pour le moment. Votre API a besoin de ses propres informations d’identification uniquement si elle accède à une API en aval. Ce scénario n’est pas abordé dans cet article.

Une fois votre API web inscrite, vous êtes prêt à ajouter les étendues que le code de votre API peut utiliser pour fournir une autorisation précise aux consommateurs de cette dernière.

### Ajouter une étendue

Le code d’une application cliente demande l’autorisation d’effectuer des opérations définies par votre API web en transmettant un jeton d’accès avec ses demandes à la ressource protégée (l’API web). Votre API web effectue ensuite l’opération demandée uniquement si le jeton d’accès qu’elle reçoit contient les étendues (également appelées « autorisations d’application ») requises pour l’opération.

Tout d’abord, effectuez les étapes suivantes pour créer un exemple d’étendue nommé « Employees.Read.All » :

1. Connectez-vous au portail Azure.
2. Si vous avez accès à plusieurs locataires, utilisez le filtre **Répertoire + abonnement** dans le menu du haut pour sélectionner le locataire contenant l’inscription de votre application cliente.
3. Sélectionnez **Entra ID**, puis **Inscriptions d'applications**, puis sélectionnez l'inscription d'application de votre API.
4. Sélectionnez **Exposer une API**, puis **Ajouter une étendue**.
5. Vous êtes invité à définir un **URI d’ID d’application** si vous n’en avez pas encore configuré un. L’URI d’ID d’application, qui doit être globalement unique, fait office de préfixe pour les étendues que vous référencerez dans le code de votre API. Vous pouvez utiliser la valeur par défaut fournie, qui se présente sous la forme `api://`, ou spécifier un URI plus lisible comme `https://contoso.com/api`.
6. Spécifiez ensuite les attributs de l’étendue dans le volet **Ajouter une étendue**. Pour cette procédure pas à pas, vous pouvez utiliser les exemples de valeurs ou spécifier les vôtres.    **Champ** **Description** **Exemple**     Nom de l’étendue Nom de votre étendue. Une convention d’affectation de noms d’étendue courante est resource.operation.constraint. Employees.Read.All   Qui peut donner son consentement L’administrateur détermine si cette étendue peut être consentie par des utilisateurs ou si le consentement d’un administrateur est nécessaire. Sélectionnez Administrateurs uniquement pour des autorisations à privilèges élevés. Administrateurs et utilisateurs   Nom d’affichage du consentement de l’administrateur Courte description de l’objectif de l’étendue que seuls les administrateurs verront. Accès en lecture seule aux enregistrements des employés   Description du consentement de l’administrateur Description plus détaillée de l’autorisation accordée par l’étendue que seuls les administrateurs verront. Autorisez l’application à avoir un accès en lecture seule à toutes les données de l’employé.   Nom d’affichage du consentement de l’utilisateur Courte description de l’objectif de l’étendue. Affichée aux utilisateurs uniquement si vous définissez *Qui peut donner son consentement sur Administrateurs et utilisateurs*. Accès en lecture seule à vos enregistrements sur les employés   Description du consentement de l’utilisateur Description plus détaillée de l’autorisation accordée par l’étendue. Affichée aux utilisateurs uniquement si vous définissez *Qui peut donner son consentement sur Administrateurs et utilisateurs*. Autorisez l’application à avoir un accès en lecture seule à vos données sur l’employé.
7. Définissez l’**État** sur **Activé**, puis sélectionnez **Ajouter une étendue**.
8. (Facultatif) Pour supprimer les demandes de consentement des utilisateurs de votre application pour les étendues que vous avez définies, vous pouvez *pré-autoriser* l’application cliente à accéder à votre API web. Pré-autorisez *uniquement* les applications clientes que vous approuvez, car vos utilisateurs n’auront pas la possibilité de refuser le consentement.
  1. Sous **Applications clientes autorisées**, sélectionnez **Ajouter une application cliente.**
  2. Entrez l’**ID d’application (client)** de l’application cliente que vous souhaitez pré-autoriser. Par exemple celui d’une application web que vous avez inscrite précédemment.
  3. Sous **Étendues autorisées**, sélectionnez les étendues pour lesquelles vous souhaitez supprimer les invites de consentement, puis sélectionnez **Ajouter une application**.
  4. Si vous avez effectué cette étape facultative, l’application cliente est désormais une application cliente préautorisée, et les utilisateurs ne sont pas invités à donner leur consentement quand ils s’y connectent.

#### Ajouter une étendue nécessitant un consentement administrateur

Ajoutez ensuite un autre exemple d’étendue nommé « Employees.Write.All » auquel seuls les administrateurs peuvent donner leur consentement. Les étendues qui nécessitent le consentement de l’administrateur donnent généralement accès à des opérations avec des privilèges plus élevés. Elles servent souvent à des applications clientes qui s’exécutent en tant que services back-end, ou en tant que démons qui ne connectent pas un utilisateur de manière interactive.

Pour ajouter l’exemple d’étendue « Employees.Write.All », effectuez les étapes décrites ci-dessus, puis spécifiez ces valeurs dans le volet **Ajouter une étendue** :

| **Champ** | **Exemple de valeur** |
|---|---|
| Nom de l’étendue | Employees.Write.All |
| Qui peut donner son consentement | Administrateurs uniquement |
| Nom d’affichage du consentement de l’administrateur | Accès en écriture aux enregistrements des employés |
| Description du consentement de l’administrateur | Autorisez l’application à avoir un accès en écriture à toutes les données de l’employé. |
| Nom d’affichage du consentement de l’utilisateur | Aucune (laisser vide) |
| Description du consentement de l’utilisateur | Aucune (laisser vide) |

#### Vérifier les étendues exposées

Si vous avez correctement ajouté les deux exemples d’étendues décrits dans les sections précédentes, ils apparaissent dans le volet **Exposer une API** de l’inscription d’application de votre API web, comme sur cette image :

Comme indiqué dans l’image, la chaîne complète d’une étendue est la concaténation de l’**URI d’ID d’application** de votre API web et du **Nom de l’étendue**.

Par exemple, si l’URI d’ID d’application de votre API web est `https://contoso.com/api` et si le nom de l’étendue est Employees.Read.All, l’étendue complète est :

`https://contoso.com/api/Employees.Read.All`

#### Utilisation des étendues exposées

Ensuite, vous allez configurer l’inscription d’une application cliente avec un accès à votre API web et les étendues que vous avez définies en suivant les étapes ci-dessus.

Une fois qu’une inscription d’application cliente est autorisée à accéder à votre API web, la plateforme d’identités Microsoft peut émettre un jeton d’accès OAuth 2.0 pour le client. Quand le client appelle l’API web, il présente un jeton d’accès dont la revendication d’étendue (scp) est définie sur les autorisations que vous avez spécifiées dans l’inscription d’application du client.

Vous pouvez exposer des étendues supplémentaires ultérieurement si nécessaire. Considérez que votre API web peut exposer plusieurs étendues associées à plusieurs opérations. Votre ressource peut contrôler l’accès à l’API web lors de l’exécution, en évaluant la ou les revendications de l’étendue (scp) dans le jeton d’accès OAuth 2.0 qu’elle reçoit.

#### Ce qui se passe en coulisses

- L’inscription d’application est créée dans le locataire d’accueil
- L'application est instanciée avec un principal de sécurité dans Entra ID
- Le principal de sécurité reçoit le consentement du premier utilisateur ou de l’administrateur, en fonction de la configuration de l’API exposée
- Le principal de sécurité reçoit le jeton de sécurité quand l’utilisateur accède à l’application et utilise l’API


## Configurer l’autorisation pour une application

Les administrateurs devront configurer les autorisations et le consentement dans le point de terminaison de la plateforme d’identités Microsoft.

Les applications qui s’intègrent à la Plateforme d’identités Microsoft suivent un modèle d’autorisation permettant aux utilisateurs et aux administrateurs de contrôler l’accès aux données. L’implémentation de ce modèle d’autorisation a été mise à jour sur le point de terminaison de la Plateforme d’identités Microsoft : elle modifie la façon dont une application doit interagir avec cette plateforme. Cette unité couvre les concepts de base de ce modèle d’autorisation, notamment les étendues, les autorisations et le consentement.

### Étendues et autorisations

La plateforme d’identités Microsoft implémente le protocole d’autorisation OAuth 2.0, méthode par laquelle une application tierce peut accéder aux ressources hébergées sur le web pour le compte d’un utilisateur. Toute ressource hébergée sur le web qui s’intègre à la plateforme d’identités Microsoft a un identificateur de ressource ou *un URI d’ID d’application*. Par exemple, les ressources hébergées sur le web de Microsoft sont les suivantes :

- Microsoft Graph : `https://graph.microsoft.com`
- API de messagerie Microsoft 365 : `https://outlook.office.com`
- Azure Key Vault : `https://vault.azure.net`

Il en va de même pour toutes les ressources tierces qui ont été intégrées à la plateforme d’identités Microsoft. Ces ressources peuvent également définir un ensemble d’autorisations à utiliser pour diviser la fonctionnalité de cette ressource en fragments plus réduits. Par exemple, Microsoft Graph dispose d’autorisations définies pour les tâches telles que :

- Lisez le calendrier d’un utilisateur.
- Écrivez dans le calendrier d’un utilisateur.
- Envoyer du courrier en tant qu’utilisateur.

Lorsque l’application définit ces types d’autorisations, la ressource a un contrôle précis sur ses données et la façon dont les fonctionnalités d’API sont exposées. Une application tierce peut demander ces autorisations aux utilisateurs et aux administrateurs qui doivent approuver la demande avant que l’application puisse accéder aux données ou agir au nom d’un utilisateur. L’organisation de développement d’applications peut répartir les fonctions des ressources dans des jeux d’autorisations plus petits. Les développeurs créent alors des applications tierces qui demandent uniquement les autorisations spécifiques dont elles ont besoin pour effectuer leur fonction. Les utilisateurs et les administrateurs peuvent savoir exactement quelles données l’application a accès, et ils peuvent être plus confiants qu’il ne se comporte pas avec une intention malveillante. Les développeurs doivent toujours respecter le concept de privilège minimum, en demandant uniquement les autorisations dont ils ont besoin pour que leurs applications fonctionnent.

Dans OAuth 2.0, ces types d’autorisations sont appelés *scopes*. Elles sont également souvent *appelées autorisations*. Une autorisation est représentée dans la plateforme d’identités Microsoft sous forme de valeur de chaîne. En suivant l’exemple Microsoft Graph, la valeur de chaîne pour chaque autorisation est la suivante :

- Lire le calendrier d’un utilisateur à l’aide de Calendars.Read
- Écrire dans le calendrier d’un utilisateur à l’aide de Calendars.ReadWrite
- Envoyer du courrier en tant qu’utilisateur à l’aide de Mail.Send

Généralement, une application peut demander ces autorisations en spécifiant les étendues dans les demandes dirigées vers le point de terminaison d’autorisation de la plateforme d’identités Microsoft. Toutefois, certaines autorisations à privilège élevé peuvent uniquement être accordées par le biais du consentement administrateur et demandées/accordées à l’aide du point de terminaison de consentement administrateur.

### Types d’autorisations

La plateforme d’identités Microsoft prend en charge deux types **d’autorisations : les autorisations déléguées** et **les autorisations d’application**.

- **Les autorisations déléguées** sont utilisées par les applications qui ont un utilisateur connecté présent. Pour ces applications, l’utilisateur ou un administrateur consent aux autorisations que l’application demande, et l’application est autorisée à agir en tant qu’utilisateur connecté lors d’appels à la ressource cible. Certaines autorisations déléguées peuvent être accordées par des utilisateurs non administratifs, mais certaines autorisations avec privilèges supérieurs nécessitent le consentement de l’administrateur. Pour savoir quels rôles d’administrateur peuvent consentir aux autorisations déléguées, consultez autorisations de rôle d’administrateur dans Entra ID.
- **Les autorisations d’application** sont utilisées par les applications qui s’exécutent sans utilisateur connecté présent ; par exemple, les applications qui s’exécutent en tant que services ou démons en arrière-plan. Seul un administrateur peut consentir aux permissions d’application.

*Les autorisations effectives* sont celles que votre application aura lors de l’exécution de demandes à la ressource cible. Il est important de comprendre la différence entre les autorisations déléguées et d’application accordées à votre application et ses autorisations effectives lors des appels à la ressource cible.

- Pour les autorisations déléguées, les *autorisations effectives* de votre application sont l’intersection la moins privilégiée des autorisations déléguées que l’application a accordées (via le consentement) et les privilèges de l’utilisateur actuellement connecté. Votre application ne peut jamais avoir plus de privilèges que l’utilisateur connecté. Dans les organisations, les privilèges de l’utilisateur connecté sont déterminés par la stratégie ou par l’appartenance à un ou plusieurs rôles d’administrateur. Pour savoir quels rôles d’administrateur peuvent consentir aux autorisations déléguées, consultez autorisations de rôle d’administrateur dans Entra ID.
- Par exemple, supposons que votre application a reçu l’autorisation déléguée *User.ReadWrite.All* . Cette autorisation permet nominalement à votre application de lire et mettre à jour le profil de chaque utilisateur dans une organisation. Si l’utilisateur connecté est administrateur d’application, votre application pourra mettre à jour le profil de chaque utilisateur de l’organisation. Toutefois, si l’utilisateur connecté n’est pas dans un rôle d’administrateur, votre application pourra mettre à jour uniquement le profil de l’utilisateur connecté. Il ne pourra pas mettre à jour les profils d’autres utilisateurs de l’organisation, car l’utilisateur auquel il est autorisé à agir au nom de ne dispose pas de ces privilèges.
- Pour les autorisations d’application, les *autorisations effectives* de votre application sont le niveau complet de privilèges implicites par l’autorisation. Par exemple, une application disposant de l’autorisation *User.ReadWrite.All* peut mettre à jour le profil de chaque utilisateur de l’organisation.

### Étendues OpenId Connect

L’implémentation de la plateforme d’identités Microsoft d’OpenID Connect a quelques étendues bien définies qui sont également hébergées sur Microsoft Graph : openid, e-mail, profil et offline_access. Les étendues « adress » et « phone » d’OpenID Connect ne sont pas prises en charge.

En demandant les étendues OIDC et un jeton, vous obtiendrez un jeton pour appeler le point de terminaison UserInfo.

#### Openid

Si une application effectue la connexion à l’aide d’OpenID Connect, elle doit demander le scope 'openid'. L’étendue openid s’affiche sur la page de consentement du compte professionnel en tant qu’autorisation `sign you in`. Sur la page de consentement de compte Microsoft personnel, elle s’affiche en tant qu’autorisation « Afficher votre profil et vous connecter aux applications et services à l’aide de votre compte Microsoft ». Avec cette autorisation, une application peut recevoir un identificateur unique pour l'utilisateur sous la forme de l'attribut sub. Il donne également à l’application l’accès au point de terminaison UserInfo. L’étendue « openid » peut être utilisée sur le point de terminaison de jeton de la plateforme d’identité Microsoft pour acquérir des jetons d’ID, qui peuvent être utilisés par l’application pour l’authentification.

#### Messagerie électronique

L’étendue « email » peut être utilisée avec l’étendue « openid » ainsi que d’autres. Elle permet à l’application d’accéder à l’adresse de messagerie principale de l’utilisateur sous la forme de la revendication « email ». La mention d'adresse e-mail est incluse dans un jeton uniquement si une adresse e-mail est associée au compte utilisateur, ce qui n'est pas toujours le cas. Si elle utilise l’étendue « email », votre application doit être préparée à faire face à l’éventualité où la revendication « email » n’existerait pas dans le jeton.

#### profil

L’étendue « profile » peut être utilisée avec l’étendue « openid » ainsi que d’autres. Il permet à l’application d’accéder à une quantité substantielle d’informations sur l’utilisateur. Les informations auxquelles il peut accéder comprennent, sans s’y limiter, le prénom, le nom, le nom d’utilisateur préféré et l’ID d’objet de l’utilisateur. Pour obtenir la liste complète des revendications de profil disponibles dans le `id_tokens` paramètre d’un utilisateur spécifique, consultez la `id_tokens` référence.

#### accès hors ligne

L’étendue offline_access donne à votre application l’accès aux ressources pour le compte de l’utilisateur pendant une période prolongée. Dans la page de consentement, cette étendue s’affiche sous la forme de l’autorisation « Maintenir l’accès aux données à laquelle vous avez accordé l’accès ». Lorsqu’un utilisateur approuve l’étendue `offline_access`, votre application peut recevoir les jetons d’actualisation du point de terminaison des jetons de la plateforme d’identités Microsoft. Les jetons d’actualisation sont de longue durée. Votre application peut obtenir de nouveaux jetons d’accès lorsque les plus anciens arrivent à expiration.

Sur la plateforme d’identité de Microsoft (requêtes adressées au point de terminaison v 2.0), votre application doit demander explicitement à l’étendue « offline_access » de recevoir les jetons d’actualisation. Cela signifie que lorsque vous échangez un code d’autorisation dans le flux de code d’autorisation OAuth 2.0, vous recevrez uniquement un jeton d’accès à partir du point de terminaison /token. Le jeton d’accès est valide pendant une courte durée, généralement expiré en une heure. À ce stade, votre application doit rediriger l’utilisateur vers le point de terminaison /authorize pour obtenir un nouveau code d’autorisation. Pendant ce réacheminement, en fonction du type d’application, l’utilisateur peut devoir entrer à nouveau ses informations d’identification ou accepter une nouvelle fois les autorisations.

Remarque

Lorsque vous utilisez une application monopage (SPA), le jeton d’actualisation est toujours fourni.

Remarque

Cette autorisation apparaît sur tous les écrans de consentement aujourd’hui, même pour les flux qui ne fournissent pas de jeton d’actualisation ( *le flux implicite*). Il s’agit de couvrir les scénarios où un client peut commencer dans le flux implicite, puis passer au flux de code où un jeton d’actualisation est attendu.

### Demande de consentement de l’utilisateur individuel

Dans une demande d’autorisation OpenID Connect ou OAuth 2.0, une application peut demander les autorisations dont elle a besoin à l’aide du paramètre de requête d’étendue. Lorsqu’un utilisateur se connecte à une application, l’application envoie une demande d’autorisation. Le paramètre d’étendue est une liste séparée par l’espace des autorisations déléguées demandées par l’application. Chaque autorisation est indiquée en ajoutant la valeur d’autorisation à l’identificateur de la ressource (URI d’ID d’application). Dans l’exemple de demande, l’application a besoin d’une autorisation déléguée pour lire le calendrier de l’utilisateur et envoyer du courrier en tant qu’utilisateur.

Une fois que l’utilisateur entre ses informations d’identification, le point de terminaison de la plateforme d’identités Microsoft recherche un enregistrement correspondant du consentement de l’utilisateur. Le point de terminaison de la plateforme d’identités Microsoft demande à l’utilisateur d’accorder les autorisations demandées s’il n’a consenti à aucune d’elles par le passé, et qu’aucun administrateur n’y a consenti pour le compte de l’ensemble de l’organisation.

Remarque

À ce stade, deux autorisations sont automatiquement incluses dans le consentement initial d’une application : offline_access (« Maintenir l’accès aux données auxquelles vous avez accordé l’accès ») et user.read (« Connectez-vous et lisez votre profil »). Ces autorisations sont généralement requises pour les fonctionnalités d’application appropriées. offline_access donne à l’application l’accès aux jetons d’actualisation, critiques pour les applications natives et web. user.read donne accès à la sous-revendication, ce qui permet au client ou à l’application d’identifier correctement l’utilisateur au fil du temps et d’accéder aux informations utilisateur rudimentaires.

Lorsque l’utilisateur approuve la demande d’autorisation, le consentement est enregistré et l’utilisateur n’a pas à consentir à nouveau sur les connexions suivantes à l’application.

### Demande de consentement pour un locataire entier

Souvent, lorsqu’une organisation achète une licence ou un abonnement pour une application, l’organisation souhaite configurer de manière proactive l’application à utiliser par tous les membres de l’organisation. Dans le cadre de cette procédure, un administrateur peut autoriser l’application à agir au nom de n’importe quel utilisateur au sein du locataire. Si l’administrateur accorde le consentement pour l’ensemble du locataire, les utilisateurs de l’organisation ne voient pas de page de consentement pour l’application. En outre, les applications doivent utiliser le point de terminaison de consentement administrateur pour demander des autorisations d’application.


## Accorder le consentement administrateur au niveau locataire à des applications

Pour les applications développées par votre organisation, ou inscrites directement dans votre locataire Entra, vous pouvez accorder le consentement administrateur au niveau locataire depuis « Inscriptions d'applications » dans le Portail Azure.

Avertissement

Le fait d’accorder le consentement administrateur au niveau locataire à une application permettra à l’application et à l’éditeur de l'application d’accéder aux données de votre organisation. Examinez attentivement les autorisations demandées par l’application avant d’accorder le consentement.

Pour accorder le consentement administrateur à l’échelle des locataires, vous devez vous connecter en tant qu’utilisateur autorisé à donner son consentement au nom de l’organisation. Cela inclut l’administrateur de rôle privilégié. Un utilisateur peut également être autorisé à accorder un consentement à l’échelle des locataires s’il reçoit un rôle d’annuaire personnalisé qui inclut l’autorisation d’accorder des autorisations aux applications.

1. Dans un exercice précédent, vous avez créé une application nommée Demo App. Si nécessaire, dans Microsoft Azure, accédez à **l’ID Entra** , puis **aux inscriptions** d’applications, puis à l’application de démonstration.
2. Dans l’écran **de l’application de démonstration** , recherchez et copiez et enregistrez chaque **ID d’application (client)** et les valeurs **d’ID d’annuaire (locataire)** afin de pouvoir les utiliser ultérieurement.
3. Dans le volet de navigation gauche, sous **Gérer**, sélectionnez **autorisations d’API**.
4. Sous **Autorisations configurées**, sélectionnez **Accorder le consentement de l’administrateur**.
5. Passez en revue la boîte de dialogue, puis sélectionnez **Oui.**

Avertissement

L’octroi du consentement administrateur au niveau du locataire via des inscriptions d’applications révoque toutes les autorisations accordées précédemment à l’ensemble du locataire. Les autorisations précédemment accordées par les utilisateurs pour leur propre compte ne seront pas affectées.

### Accorder le consentement administrateur dans des applications d’entreprise

Vous pouvez accorder le consentement administrateur au niveau locataire via Applications d’entreprise si l’application a déjà été approvisionnée dans votre locataire.

1. Dans Microsoft Azure, accédez à **l’ID Entra**, aux **applications d’entreprise**, puis **à l’application de démonstration**.
2. Dans l’écran **De démonstration de l’application** , dans le volet de navigation gauche, sous **Sécurité,** sélectionnez **Autorisations.**
3. Sous **Autorisations**, sélectionnez **Accorder le consentement de l’administrateur.**
4. Lorsque vous y êtes invité, connectez-vous à l’aide de votre compte Administrateur de rôle privilégié.
5. Dans la boîte de dialogue **Autorisations demandées** , passez en revue les informations, puis sélectionnez **Accepter**.

### Construire l’URL pour accorder le consentement de l’administrateur au niveau du locataire

Lorsque vous accordez le consentement administrateur au niveau du locataire par l’une des méthodes décrites ci-dessus, une fenêtre s’ouvre à partir du Portail Azure pour demander ce consentement. Si vous connaissez l’ID client de l’application (également appelé ID d’application), vous pouvez générer la même URL pour accorder le consentement administrateur au niveau locataire.

1. L’URL de consentement administrateur à l’échelle du locataire suit le format suivant : `https://login.microsoftonline.com/{tenant-id}/adminconsent?client_id={client-id}`, où :
  - `{client-id}` est l’ID client de l’application (également appelé ID d’application).
  - `{tenant-id}` est l’ID de locataire de votre organisation ou un nom de domaine vérifié.

2. Comme toujours, examinez attentivement les autorisations demandées par une application avant d’accorder le consentement.

### Autorisations restreintes aux administrateurs

Certaines autorisations à privilèges élevés dans l’écosystème Microsoft peuvent être définies sur *restreintes par l’administrateur*. Voici quelques exemples de ce type de permissions :

- Lire les profils complets de tous les utilisateurs à l’aide de User.Read.All
- Écrire des données dans le répertoire d’une organisation à l’aide de Directory.ReadWrite.All
- Lire tous les groupes dans le répertoire d’une organisation à l’aide de Groups.Read.All

Si un utilisateur consommateur peut accorder à une application l’accès à ce type de données, les utilisateurs d’organisation sont limités lorsqu’il s’agit d’octroyer l’accès au même jeu de données d’entreprise sensibles. Si votre application requiert l’une de ces autorisations auprès d’un utilisateur de l’organisation, ce dernier recevra un message d’erreur indiquant qu’il n’est pas autorisé à donner son consentement pour les permissions de votre application.

Si votre application requiert l’accès aux étendues restreintes aux administrateurs pour les organisations, demandez l’autorisation directement à un administrateur d’entreprise, également à l’aide du point de terminaison de consentement de l’administrateur décrit ci-dessous.

Si l’application demande des autorisations déléguées à privilèges élevés et qu’un administrateur les accorde via le point de terminaison de consentement de l’administrateur, le consentement vaut pour tous les utilisateurs du locataire.

Si l’application demande des autorisations d’application et qu’un administrateur accorde ces autorisations via le point de terminaison de consentement de l’administrateur, cette attribution n’est pas attribuée pour le compte d’un utilisateur spécifique. L’application cliente reçoit les autorisations directement. Ces types d’autorisations sont uniquement utilisés par les services démon et d’autres applications non interactives qui s’exécutent en arrière-plan.

### Utilisation du point de terminaison de consentement administrateur

Remarque

Une fois le consentement accordé par l’administrateur à l’aide du point de terminaison de consentement administrateur, l’opération est terminée : les utilisateurs n’ont aucune action supplémentaire à effectuer. Après avoir accordé le consentement administrateur, les utilisateurs peuvent obtenir un jeton d’accès grâce au flux d’authentification standard. Le jeton d’accès en question aura toutes les autorisations nécessaires.

Lorsqu’un administrateur d’entreprise utilise votre application et qu’il est dirigé vers le point de terminaison autorisé, la plateforme d’identité Microsoft détecte son rôle. Elle lui demande alors s’il souhaite donner son consentement, pour les autorisations que vous avez demandées, au nom de l’intégralité du locataire. Toutefois, un point de terminaison de consentement de l’administrateur dédié existe également : utilisez-le pour demander proactivement qu’un administrateur accorde son autorisation pour le compte de l’intégralité du locataire. Vous devez également utiliser ce point de terminaison pour demander des permissions d’application (qui ne peuvent pas être demandées à l’aide du point de terminaison autorisé).

Si vous suivez ces étapes, votre application peut demander des autorisations pour tous les utilisateurs d’un locataire, notamment les étendues restreintes aux administrateurs. Il s’agit d’une opération à privilèges élevés qui ne doit être effectuée que si cela est nécessaire pour votre scénario.

#### Demander les autorisations dans le portail d’inscription de l’application

Les applications sont en mesure de noter les autorisations dont elles ont besoin (autorisations déléguées et d'application) dans le portail d’inscription des applications. Il est ainsi possible d’utiliser l’étendue « /.default » et l’option « Accorder un consentement administrateur » du portail Azure. En général, il est recommandé de veiller à ce que les autorisations définies de manière statique pour une application donnée constituent un sur-ensemble des autorisations qui seront demandées de façon dynamique/incrémentielle.

#### Configuration de la liste des autorisations demandées de manière statique pour une application

1. Accédez à votre application dans l’environnement Inscriptions d’applications du portail Microsoft Azure ou créez une application, si ce n’est pas déjà fait.
2. Recherchez la section **Autorisations d’API** , puis sélectionnez **Ajouter une autorisation**.
3. Sélectionnez **Microsoft Graph** dans la liste des API disponibles, puis ajoutez les autorisations requises par votre application.
4. **Enregistrez** l’inscription de l’application.

### Recommandé : connectez l’utilisateur à votre application

En général, lorsque vous créez une application qui utilise le point de terminaison de consentement de l’administrateur, l’application doit disposer d’une page ou vue dans laquelle l’administrateur peut approuver ses autorisations. Cette page peut faire partie du flux d’inscription de l’application, des paramètres de l’application ou d’un flux de connexion dédié. Dans de nombreux cas, il est judicieux pour l’application d’afficher la vue de « connexion » uniquement après qu’un utilisateur se soit connecté avec un compte Microsoft professionnel ou scolaire.

Lorsque vous connectez l’utilisateur à votre application, vous pouvez identifier l’organisation à laquelle l’administrateur appartient, avant de lui demander d’approuver les autorisations nécessaires. Même si cela n’est pas strictement nécessaire, cela peut vous aider à créer une expérience plus intuitive pour les utilisateurs de l’organisation. Pour connecter l’utilisateur, suivez les tutoriels sur le protocole de la plateforme d’identités Microsoft.

### Utilisation des autorisations

Une fois que l’utilisateur accepte les autorisations pour votre application, cette dernière peut acquérir des jetons d’accès représentant l’autorisation de votre application à accéder, dans une certaine capacité, à une ressource. Un jeton d’accès peut être utilisé pour une ressource uniquement, mais l’encodage de ce jeton comporte les informations relatives à toutes les autorisations octroyées pour cette ressource à votre application. Lorsque vous êtes prêt à demander des autorisations auprès de l’administrateur de votre organisation, vous pouvez rediriger l’utilisateur vers le *point de terminaison de consentement de l’administrateur* de la plateforme d’identités Microsoft. Les sauts de ligne sont uniquement destinés à la lisibilité.

```
GET https://login.microsoftonline.com/\{tenant\}/v2.0/adminconsent?

client_id=00001111-aaaa-2222-bbbb-3333cccc4444

state=12345

redirect_uri=http://localhost/myapp/permissions

scope=

    https://graph.microsoft.com/calendars.read

    https://graph.microsoft.com/mail.send
```

| **Paramètre** | **Condition** | **Description** |
|---|---|---|
| locataire | Obligatoire | Le client d’annuaire auquel vous souhaitez demander l’autorisation. Peut être fourni au format GUID ou sous forme de nom convivial OU référencé de manière générique avec des organisations comme indiqué dans l’exemple. N’utilisez pas « common », car les comptes personnels ne peuvent pas fournir le consentement de l’administrateur, sauf dans le contexte d’un locataire. Pour garantir une meilleure compatibilité avec les comptes personnels qui gèrent les locataires, utilisez l’ID de locataire, dans la mesure du possible. |
| client_id | Obligatoire | L'**ID d'application (client)** que le portail Azure, via l'expérience d'enregistrement des applications, a affecté à votre application. |
| redirect_uri | Obligatoire | L'URI de redirection où vous souhaitez que la réponse soit envoyée pour être gérée par votre application. Il doit correspondre exactement à l’un des URI de redirection que vous avez inscrits dans le portail d’inscription des applications. |
| état | Nos recommandations | Une valeur incluse dans la requête, qui sera également renvoyée dans la réponse de jeton. Il peut s’agir d’une chaîne du contenu de votre choix. Utilisez l’état pour encoder les informations sur l’état de l’utilisateur dans l’application avant la requête d’authentification, comme la page ou la vue sur laquelle ou laquelle il était positionné. |
| portée | Obligatoire | Définit l’ensemble des autorisations demandées par l’application. Il peut s’agir d’étendues statiques (utilisant /.default) ou dynamiques. Cela peut inclure les étendues OIDC (openid, profile, email). |

À ce stade, Entra ID nécessite qu’un administrateur client se connecte pour terminer la demande. L’administrateur est invité à approuver toutes les autorisations que vous avez demandées dans le paramètre « scope ».


## Implémenter l’autorisation d’application

**Les rôles d’application** sont utilisés pour attribuer des autorisations aux utilisateurs. Vous définissez des rôles d’application à l’aide du portail Azure. Lorsqu'un utilisateur se connecte à l'application, Entra ID émet une demande de rôles pour chaque rôle attribué à l'utilisateur individuellement et en fonction de son appartenance à un groupe.

Il existe deux façons de déclarer des rôles d’application à l’aide du portail Azure :

- Interface Rôles d’application, puis Aperçu
- Éditeur de manifeste d’application


## Exercice : ajouter des rôles à une application et recevoir des jetons

Vous pouvez déclarer des rôles d’application à l’aide de l’interface utilisateur des rôles d’application.

Important

La fonctionnalité d’interface utilisateur du portail des rôles d’application est en préversion publique. Cette préversion est fournie sans contrat de niveau de service et n’est pas recommandée pour les charges de travail de production. Certaines fonctionnalités peuvent ne pas être prises en charge ou avoir des fonctionnalités contraintes.

Pour créer un rôle d’application à l’aide de l’interface utilisateur du portail Azure :

1. Connectez-vous au [Centre d’administration Entra](https://entra.microsoft.com/) à l’aide d’un compte Administrateur.
2. Ouvrez le menu du portail, puis sélectionnez **Identité**.
3. Dans le menu **Identité** , sous **Applications,** sélectionnez **Inscriptions d’applications**.
4. Sélectionnez **Rôles d’application**, puis **Créer un rôle d’application**.
5. Dans le volet **Créer un rôle d’application**, dans la zone **Nom d’affichage**, entrez **Rédacteur de sondage**.
6. Sous **Autoriser les types de membres**, sélectionnez **Utilisateur/Groupes**.
7. Dans la zone **Valeur** , entrez **Survey.Create**.
8. Dans la zone **Description**, entrez **les rédacteurs peuvent créer des enquêtes**.
9. Notez que la description est un champ obligatoire.
10. Vérifiez que le **rôle d'application à activer** est sélectionné, puis sélectionnez **Appliquer.**

### Affecter des utilisateurs et des groupes à des rôles

Une fois que vous avez ajouté des rôles d’application dans votre application, vous pouvez affecter des utilisateurs et des groupes aux rôles. Affectez des utilisateurs et des groupes à des rôles via l’interface utilisateur du portail ou par programmation à l’aide de [Microsoft Graph](https://learn.microsoft.com/fr-fr/graph/api/user-post-approleassignments). Lorsque les utilisateurs assignés aux différents rôles d’application se connectent à l’application, leurs jetons portent les rôles qui leur ont été attribués dans la revendication « roles ».

Pour affecter des utilisateurs et des groupes à des rôles à l’aide du portail Azure :

1. Connectez-vous au [centre d’administration Entra](https://entra.microsoft.com/).
2. Dans le menu de navigation Identité à gauche, ouvrez **Applications** sélectionnez **Applications d’entreprise.**
3. Dans la liste **Toutes les applications** , sélectionnez **Application de démonstration**.
4. Cette application a été créée dans un exercice précédent.
5. Sous **Gérer**, sélectionnez **Utilisateurs et groupes.**
6. Dans le menu, sélectionnez **+ Ajouter un utilisateur/groupe.**
7. Dans la boîte de dialogue **Ajouter une affectation** , sélectionnez **Utilisateurs et groupes**.
8. Une liste d’utilisateurs et de groupes de sécurité s’affiche. Vous pouvez rechercher un utilisateur ou un groupe spécifique, ainsi que sélectionner plusieurs utilisateurs et groupes qui apparaissent dans la liste.
9. Une fois que vous avez sélectionné des utilisateurs et des groupes, sélectionnez **Sélectionner**.
10. Lorsque vous utilisez l’attribution **de rôle Sélectionner un rôle** , tous les rôles que vous avez définis pour l’application sont affichés.
11. Choisissez un rôle, puis sélectionnez **Sélectionner**.
12. Appuyez sur **Attribuer** pour terminer l’attribution des utilisateurs et des groupes à l’application.
13. Vérifiez que les utilisateurs et les groupes ajoutés figurent dans la liste **Utilisateurs et groupes**.


## Gérer et surveiller l’application à l’aide de la gouvernance des applications

Les cyberattaques sont devenues de plus en plus sophistiquées pour exploiter les applications que vous avez déployées dans vos infrastructures locales et cloud. Les cyberattaques établissent un point de départ pour l’escalade de privilèges, le mouvement latéral et l’exfiltration de vos données. Pour comprendre les risques potentiels et arrêter ces types d’attaques, vous devez obtenir une visibilité claire sur la posture de conformité des applications de votre organisation. Ensuite, vous devez rechercher quand une application présente des comportements anormales et pour répondre lorsque ces comportements présentent des risques pour votre environnement, vos données et vos utilisateurs.

La fonctionnalité complémentaire de gouvernance des applications à Defender pour Cloud Apps assure la sécurité et la gestion des stratégies pour les applications compatibles OAuth qui accèdent aux données Microsoft 365 via les API Microsoft Graph. La gouvernance des applications offre une visibilité, une correction et une gouvernance complètes sur la façon dont ces applications et leurs utilisateurs accèdent, utilisent et partagent vos données sensibles stockées dans Microsoft 365. Elle s’appuie pour cela sur des insights actionnables et sur des alertes et des actions de stratégie automatisées.

La gouvernance des applications vous offre des fonctionnalités complètes :

- **Insights** : consultez une vue de toutes les applications tierces pour la plateforme Microsoft 365 dans votre locataire sur un tableau de bord unique. Vous pouvez voir l’état et les activités d’alerte de toutes les applications et y réagir ou y répondre.
- **Gouvernance** : créez des stratégies proactives ou réactives pour les modèles d’application et les comportements utilisateur. Elles protègent vos utilisateurs contre l’utilisation d’applications non conformes ou malveillantes et limitent l’accès des applications à risque à vos données.
- **Détection** : soyez alerté et averti lorsqu’il existe des anomalies dans l’activité de l’application et quand des applications non conformes, malveillantes ou risquées sont utilisées.
- **Correction** : en plus des fonctionnalités de correction automatique, utilisez des contrôles de correction en temps opportun pour répondre aux détections anormales d’activité des applications.

### Activer la synchronisation de Defender pour cloud Apps

Pour activer la synchronisation de la gouvernance des applications avec Defender pour Cloud Apps, procédez comme suit :

1. Vérifiez qu’Office 365 est connecté dans Defender pour Cloud Apps.
2. Vérifiez que les applications d’ID Entra Office 365 sont activées.
3. Accédez à votre portail Defender for Cloud Apps : `https://portal.cloudappsecurity.com`
4. Sélectionnez l’icône d’engrenage (coin supérieur droit) et sélectionnez Paramètres.
5. Sous Protection contre les menaces, sélectionnez Gouvernance des applications.
6. Sélectionnez Activer l’intégration de la gouvernance des applications, puis sélectionnez Enregistrer. Pour vérifier que l’intégration avec Defender for Cloud Apps est active, recherchez les stratégies de gouvernance des applications répertoriées ci-dessous afin qu'elles apparaissent dans Defender for Cloud Apps. Les nouvelles stratégies peuvent prendre quelques minutes pour apparaître une fois l’intégration activée.
  - Réputation de l’application OAuth Microsoft 365
  - Détection d’hameçonnage OAuth Microsoft 365
  - Gouvernance des applications OAuth Microsoft 365


## Évaluation du module

Choisissez la meilleure réponse à chacune des questions ci-dessous.

### Vérifiez vos connaissances


## Résumé et ressources

Maintenant que vous avez passé en revue ce module, vous pouvez :

- Planifier votre stratégie d’inscription d’application métier.
- Implémentez les enregistrements d’applications.
- Configurez les autorisations d’application.
- Établissez et gérez un processus de gouvernance des applications.

### Ressources

Pour explorer avec plus de profondeur, utilisez ces ressources :

- [Module complémentaire de gouvernance des applications à Defender pour Cloud Apps](https://learn.microsoft.com/fr-fr/defender-cloud-apps/app-governance-manage-app-governance)
- [Configurer des stratégies de durée de vie de session adaptative](https://learn.microsoft.com/fr-fr/entra/identity/conditional-access/howto-conditional-access-session-lifetime)


---

# Inscrire des applications à l’aide d’Entra ID

_https://learn.microsoft.com/fr-fr/training/modules/register-apps-use-microsoft-entra-id/_


## Présentation

L’enregistrement des applications dans Entra ID est le processus permettant au système d’identité de reconnaître les applications utilisées. De cette façon, vous pouvez confirmer que l’utilisateur a accès à l’application et que l’application a accès à toutes les ressources nécessaires. Vous assurez la sécurité et la confidentialité des utilisateurs, des applications et de vos données.

### Scénario

Imaginez que vous êtes un développeur d’applications qui souhaite créer une application qui nécessite l’authentification et l’autorisation. Vous souhaitez vous assurer que seuls les utilisateurs autorisés peuvent accéder à l’application et que l’application peut accéder aux ressources nécessaires.

En inscrivant votre application avec l’ID Entra, vous pouvez fournir une configuration d’identité pour votre application qui lui permet de s’intégrer à la plateforme d’identités Microsoft. Ce processus d’inscription active plusieurs fonctionnalités clés :

- **Personnalisation personnalisée** : personnalisez la personnalisation de votre application dans la boîte de dialogue de connexion. Cette personnalisation est importante, car la connexion est la première expérience qu’un utilisateur a avec votre application.
- **Configuration du locataire** : choisissez entre l’application monolocataire (votre organisation) ou l’application multilocataire (accepter les comptes d’autres locataires). Vous pouvez également autoriser des comptes Microsoft personnels ou des comptes sociaux à partir de LinkedIn, Google, et ainsi de suite.
- **Gestion des autorisations** : demander des autorisations d’étendue, telles que l’étendue user.read, qui accorde l’autorisation de lire le profil de l’utilisateur connecté. Définissez des étendues qui contrôlent l’accès à votre API web.
- **Authentification sécurisée** : configurer des méthodes d’authentification sécurisées. Certaines applications clientes confidentielles peuvent contenir des informations d’identification de manière sécurisée, comme les applications web avec des serveurs principaux approuvés. Pour celles-ci, utilisez des secrets client, des certificats ou des alternatives modernes telles que des identités managées, pour une sécurité renforcée.

### Objectifs d’apprentissage

- Avantages de l’inscription d’une application.
- Applications monolocataires et multilocataire.
- Que se passe-t-il lorsqu’une application est inscrite.
- Relation entre les objets application et les principaux de service.

### Objectifs

L’objectif de ce module est de vous apprendre à inscrire votre application avec l’ID Entra, puis comment la configurer pour l’intégrer à la plateforme d’identités Microsoft. Découvrez comment personnaliser l'image de marque de votre application dans la fenêtre de connexion. Explorez ensuite comment demander des autorisations d’étendue et comment partager un secret avec la plateforme d’identités Microsoft qui prouve l’identité de l’application. Enfin, découvrez les applications monolocataires et les applications multilocataires, les objets d’application et les objets de principal de service, ainsi que la relation entre elles.


## Planifier une inscription d’application

L’inscription des applications dans Entra ID consiste à faire en sorte que votre système d’identité sache quelles applications sont utilisées. Vous pouvez confirmer que l’utilisateur a accès à l’application et que l’application a accès à toutes les ressources nécessaires. L’inscription des applications garantit la sécurité et la confidentialité des utilisateurs, des applications et de vos données.

### Avantages de l’inscription d’une application

Lorsque vous inscrivez votre application avec l’ID Entra, vous fournissez une configuration d’identité pour votre application qui lui permet de s’intégrer à la plateforme d’identités Microsoft. L’inscription de l’application vous permet également de :

- Personnaliser la boîte de dialogue de connexion avec la marque de votre application.
  - La personnalisation est importante, car la connexion est la première expérience qu’un utilisateur a avec votre application.

- Décidez si vous souhaitez autoriser les utilisateurs à se connecter uniquement s’ils appartiennent à votre organisation.
  - La connexion à votre propre organisation est appelée application monolocataire.
  - Vous pouvez autoriser les utilisateurs à se connecter à l’aide de n’importe quel compte professionnel ou scolaire, appelé application mutualisée.
  - Vous pouvez également autoriser des comptes Microsoft personnels ou un compte social à partir de LinkedIn, Google, et ainsi de suite.

- Demander des autorisations d’étendue.
  - Par exemple, vous pouvez demander l’étendue « user.read », qui accorde l’autorisation de lire le profil de l’utilisateur connecté.

- Définissez une étendue qui définit l’accès à votre API web.
  - En règle générale, lorsqu’une application souhaite accéder à votre API, elle doit demander des autorisations aux étendues que vous définissez.

- Partagez un secret avec la plateforme d’identités Microsoft qui prouve l’identité de l’application.
  - L’utilisation d’un secret est pertinente dans le cas où l’application est une application cliente confidentielle. Une application cliente confidentielle est une application qui peut contenir des informations d’identification de manière sécurisée, comme un client web. Un serveur principal approuvé est requis pour stocker les informations d’identification.

#### Applications monolocataires et multilocataires

Comme le nom l’indique, une application inscrite en tant qu’application monolocataire n’est disponible que pour les utilisateurs et les ressources de ce locataire spécifique. Pour les applications inscrites en tant qu’applications mutualisées, les utilisateurs de différents locataires peuvent accéder aux applications. Le scénario multilocataire doit être utilisé intentionnellement si nécessaire. Dans le scénario multilocataire, un objet principal de service est créé dans le répertoire pour chaque locataire dont l’application a des utilisateurs. La création du principal de service se produit au moment de l’inscription de l’application dans le locataire source et pendant la première authentification utilisateur dans d’autres locataires. Lorsqu’ils développent des applications, les développeurs peuvent choisir de configurer leur application pour qu’elle soit soit monoutilisateur, soit mutualisée lors de l’inscription de l’application dans le centre d'administration Entra.

- Les applications à locataire unique sont disponibles uniquement dans le locataire dans lequel elles ont été inscrites, également connu sous le nom de locataire d'origine.
- Les applications multi-locataires sont accessibles aux utilisateurs dans leur locataire de base et d’autres locataires.

Dans le Centre d’administration Entra, vous pouvez configurer votre application pour qu’elle soit locataire unique ou multilocataire en définissant l’audience comme suit.

| **Audience** | **Monolocataire/multilocataire** | **Qui peut se connecter** |
|---|---|---|
| Comptes dans ce répertoire uniquement | Monolocataire | Tous les comptes d’utilisateur et d’invité de votre annuaire peuvent utiliser votre application ou VOTRE API. |
| Comptes dans n’importe quel répertoire Entra | Multi-locataire | Tous les utilisateurs et invités disposant d’un compte professionnel ou scolaire de Microsoft peuvent utiliser votre application ou VOTRE API. Access inclut les écoles et les entreprises qui utilisent Microsoft 365. |
| Comptes dans n’importe quel annuaire Entra et comptes Microsoft personnels (tels que Skype, Xbox, Outlook.com) | Multi-locataire | Tous les utilisateurs disposant d’un compte professionnel ou scolaire ou personnel Microsoft peuvent utiliser votre application ou VOTRE API. Il inclut les écoles et les entreprises qui utilisent Microsoft 365 ainsi que des comptes personnels utilisés pour se connecter à des services tels que Xbox et Skype. |

### Que se passe-t-il lorsqu’une application est inscrite

Une fois l’application inscrite, elle reçoit un identificateur unique qu’elle partage avec la plateforme d’identités Microsoft lorsqu’elle demande des jetons. Si l’application est une application cliente confidentielle, elle partage le secret ou la clé publique selon que des certificats ou des secrets ont été utilisés.

Important

Depuis août 2024, les nouvelles applications reçoivent des jetons d’accès v2 par défaut (au lieu de v1) pour améliorer la sécurité. Cette modification affecte la façon dont les jetons sont mis en forme et les revendications qu’ils contiennent.

Il existe deux représentations d’applications dans Entra ID :

- **Objets d’application** : bien qu’il existe des exceptions, les objets d’application peuvent être considérés comme la définition d’une application.
- Les **principaux de service** : ils peuvent être considérés comme une instance d’une application. En règle générale, les principaux de service référencent un objet d’application, et un objet d’application peut être référencé par plusieurs principaux de service sur plusieurs annuaires.

La plateforme d’identités Microsoft représente des applications à l’aide d’un modèle qui remplit deux fonctions principales. Tout d’abord, la plateforme d’identité identifie l’application par les protocoles d’authentification qu’elle prend en charge. Ensuite, il fournit tous les identificateurs, URL, secrets et informations associées nécessaires à l’authentification.

Plateforme d’identités Microsoft :

- Contient toutes les données requises pour prendre en charge l’authentification au moment de l’exécution.
- Contient toutes les données pour décider des ressources auxquelles une application peut avoir besoin d’accéder, et dans quelles circonstances une demande donnée doit être remplie.
- Fournit une infrastructure pour implémenter l’approvisionnement de l’application au sein du locataire de son développeur et de tout autre locataire Entra.
- Gère le consentement de l'utilisateur lors de la demande de jeton et facilite l'approvisionnement dynamique d'applications entre différentes entités locataires.

Le consentement est le processus d’octroi d’une autorisation de propriétaire de ressource pour une application cliente d’accéder aux ressources protégées, sous des autorisations spécifiques, au nom du propriétaire de la ressource. Entra permet aux utilisateurs et aux administrateurs d’accorder ou de refuser dynamiquement le consentement de l’application pour accéder aux ressources en leur nom. En fin de compte, les administrateurs peuvent décider quelles applications sont autorisées à faire et quels utilisateurs peuvent utiliser des applications spécifiques, ainsi que la façon dont les ressources d’annuaire sont accessibles.


## Explorer des objets d’application et des principaux de service

Une fois l’inscription de l’application terminée, vous disposez d’une instance globale unique de l’application (l’objet d’application) qui se trouve dans votre locataire ou répertoire domestique. Vous disposez également d’un ID global unique pour votre application (l’ID d’application/client). Dans le Centre d’administration Entra, vous pouvez ensuite ajouter des secrets ou des certificats et des périmètres pour que votre application fonctionne, personnaliser l'apparence de votre application dans la fenêtre de connexion.

Si vous inscrivez une application dans le Centre d’administration Entra, un objet d’application et un objet principal de service sont automatiquement créés dans votre locataire domestique. Si vous inscrivez/créez une application à l’aide des API Microsoft Graph, la création de l’objet principal de service est une étape distincte.

Note

**Meilleure pratique en matière de sécurité** : Pour l’authentification des applications (identités de charge de travail), Microsoft recommande d’utiliser des certificats au lieu de mots de passe pour renforcer la sécurité. Pour les charges de travail Azure, les identités managées sont l’approche recommandée, car elles éliminent la nécessité de gérer entièrement les informations d’identification.

### Objet application

Une application Entra est définie par son objet d’application, qui réside dans le locataire Entra où l’application a été inscrite (appelée locataire « accueil » de l’application). Un objet d’application est utilisé comme modèle ou blueprint pour créer un ou plusieurs objets de principal de service. Un principal de service est créé dans chaque locataire dans lequel l’application est utilisée. Comme pour une classe de programmation orientée objet, l’objet application a des propriétés statiques qui sont appliquées à tous les principaux de service créés (ou instances d’application).

L’objet application décrit trois aspects d’une application :

- Comment le service peut émettre des jetons pour accéder à l’application
- Ressources auxquelles l’application peut avoir besoin d’accéder
- Actions que l’application peut effectuer

L’objet d’application peut inclure (mais pas limité à) :

- Nom, logo et éditeur
- URI de redirection
- Identifiants d'authentification
  - Certificats (recommandés pour une sécurité renforcée)
  - Secrets client (mots de passe : utiliser uniquement lorsque les certificats ne sont pas réalisables)

- Dépendances d’API (OAuth)
- API/ressources/étendues publiées (OAuth)
- Rôles d’application
- Métadonnées et configuration de l’authentification unique (SSO)
- Configuration et métadonnées de l’attribution d’utilisateurs
- Configuration et métadonnées du proxy

### Objet principal de service

Pour accéder aux ressources sécurisées par un locataire Entra, l’entité qui requiert l’accès doit être représentée par un principal de sécurité. Cette exigence est vraie pour les utilisateurs (principal utilisateur) et les applications (principal de service). Le principal de sécurité définit la stratégie d’accès et les autorisations pour l’utilisateur ou l’application du locataire Entra. Cela permet d’activer les fonctionnalités principales, telles que l’authentification de l’utilisateur/application pendant la connexion et l’autorisation pendant l’accès aux ressources. Les types de principaux de service :

- **Application** : le principal de service est la représentation locale, ou l’instance d’application, d’un objet d’application global dans un seul locataire ou répertoire. Dans ce cas, un principal de service est une instance concrète créée à partir de l’objet d’application et hérite de certaines propriétés de cet objet d’application. Lorsqu’une application est autorisée à accéder aux ressources d’un locataire, un objet principal de service est créé.
- **Identité managée** (recommandé pour les charges de travail Azure) : le principal de service est utilisé pour représenter une identité managée. Les identités managées éliminent la nécessité pour les développeurs de gérer les informations d’identification, de réduire les risques de sécurité et de surcharge opérationnelle. Les identités managées fournissent une identité pour les applications à utiliser lors de la connexion aux ressources qui prennent en charge l’authentification Entra. Une identité managée est l’approche recommandée pour les applications hébergées par Azure.
- **Hérité** : le principal de service représente une application héritée, qui est une application créée avant l’introduction des inscriptions d’applications ou une application créée par le biais d’expériences héritées. Un service principal hérité peut avoir des identifiants, des noms de service principal, des URL de réponse et d’autres propriétés. Les entités de service héritées doivent être migrées vers des enregistrements d'applications modernes lorsque cela est possible.

Le service principal peut inclure :

- Une référence à un objet d’application via la propriété d’ID d’application
- Enregistrements des attributions de rôles applicatifs aux utilisateurs locaux et aux groupes
- Enregistrements des autorisations d’utilisateur et d’administrateur locales accordées à l’application
- Des enregistrements des stratégies locales, y compris une stratégie d’accès conditionnel
- Enregistrements des autres paramètres locaux d’une application

### Relation entre les objets d’application et les entités de service

L’objet d’application est la représentation globale de votre application à utiliser sur tous les locataires, et le principal de service est la représentation locale à utiliser dans un locataire spécifique. L’objet d’application sert de modèle à partir duquel les propriétés courantes et par défaut sont dérivées pour une utilisation dans la création d’objets de principal de service correspondants. Un objet d’application a :

- Relation un-à-un avec l’application logicielle
- Une relation un-à-plusieurs avec ses objets de principal de service correspondants

Un principal de service doit être créé dans chaque locataire où l’application est utilisée, ce qui lui permet d’établir une identité pour la connexion et/ou l’accès aux ressources sécurisées par le locataire. Une application à locataire unique n’a qu’un seul principal de service (dans son locataire de base), créé et pouvant être utilisé pendant l’inscription de l’application. Une application mutualisée dispose également d’un principal de service créé dans chaque locataire où un utilisateur de ce locataire a consenti à son utilisation.

### Gestion des objets d’application et des principaux de service

Ayez toujours une stratégie de gestion et un processus pour maintenir vos principes de service.

#### Conséquences des modifications et suppressions

Toutes les modifications apportées à votre objet d'application sont reflétées dans son objet principal de service dans le locataire d'origine de l'application uniquement. En d’autres termes :

- La suppression d’un objet d’application supprime également son objet principal de service de locataire d’accueil
- Toutefois, la restauration de l’objet d’application via le Centre d’administration Entra ne restaure pas son principal de service correspondant
- Les principaux de service dans d’autres locataires (pour les applications mutualisées) restent indépendants de l’objet d’application du locataire domestique

#### Recherche de principaux de service

Pour trouver les principaux de service associés à un objet d’application dans le Centre d’administration Entra, accédez à la vue d’ensemble de l’inscription de l’application, puis sélectionnez **Application managée dans l’annuaire local**.

Important

Lorsque vous travaillez avec des identités de charge de travail (identités non humaines telles que des applications), tenez toujours compte des implications de sécurité de la gestion des informations d’identification. Préférez les identités managées pour les ressources Azure dans la mesure du possible.


## Créer des inscriptions d’applications

Ce module démontre l'enregistrement d'une application dans Entra ID à l'aide d'une application à page unique (SPA). Pour inscrire une application à page unique dans la plateforme d’identités Microsoft, procédez comme suit. Le processus est simple et ne nécessite que quelques informations.

Note

Cet exemple utilise une application monopage, mais le processus d’inscription principal est similaire pour d’autres types d’applications (applications web, applications mobiles, etc.). Les principales différences sont dans les étapes de configuration spécifiques à la plateforme.

### Créer l'enregistrement de l'application

  Les étapes sont basées sur le Centre d’administration Entra :

1. Connectez-vous au [Centre d’administration Entra](https://entra.microsoft.com/) avec les autorisations appropriées (au moins le rôle Développeur d’applications).
2. Sous le menu **Identité** , développez le menu **Applications** .
3. Sélectionnez **Inscriptions d’applications**, puis **Nouvelle inscription**.
4. Entrez un **nom** pour votre application. Les utilisateurs de votre application peuvent voir ce nom et vous pouvez le modifier ultérieurement.
5. Choisissez les **types de comptes pris en charge** pour l’application. Pour la plupart des applications monolocataires, sélectionnez « Comptes dans cet annuaire organisationnel uniquement ». N’entrez PAS d’URI de redirection à ce stade.
6. Sélectionnez **Inscrire** pour créer l’inscription de l’application.

Important

Enregistrez **l’ID d’application (client)** et **l’ID d’annuaire (locataire)** dans la page Vue d’ensemble, car vous aurez besoin de ces valeurs pour configurer votre code d’application.

### Configurer la plateforme d’applications Single-Page

Procédez comme suit pour ajouter un URI de redirection pour une application qui utilise MSAL.js 2.0 ou version ultérieure. MSAL.js 2.0+ prend en charge le flux de code d’autorisation avec preuve de clé pour l'échange de code (PKCE) et le partage de ressources d'origine croisée (CORS). Cela offre une sécurité renforcée par rapport au flux d’octroi implicite hérité.

1. Dans le **Centre d’administration Entra**, sélectionnez l’inscription d’application que vous avez créée à l’étape précédente.
2. Sous **Gérer**, sélectionnez **Authentification**.
3. Sélectionnez **+ Ajouter une plateforme**.
4. Sous **Applications web**, sélectionnez la vignette **d’application monopage** .
5. Sous **URI de redirection**, entrez un URI de redirection (par exemple, `http://localhost:3000/` pour le développement local).
6. Ne cochez **pas** l’une ou l’autre case sous **Octroi implicite et flux hybrides** : les modèles hérités ne sont plus recommandés.
7. Sélectionnez **Enregistrer** pour terminer l’ajout de l’URI de redirection.

Note

**Remarque de sécurité** : La configuration de la plateforme SPA active automatiquement le flux de code d'autorisation avec PKCE. PKCE est plus sécurisé que le flux d’octroi implicite hérité. Les autorités de service modernes doivent utiliser cette approche.

### Inscription terminée

L’inscription de votre application monopage (SPA) est terminée. Vous avez configuré un URI de redirection vers lequel le client est redirigé et tous les jetons de sécurité sont envoyés. Configurer votre URI de redirection à l’aide de la tuile d'application monopage dans le volet **Ajouter une plateforme** prépare votre inscription d’application à prendre en charge le flux d'autorisation par code avec PKCE et CORS.

**Étapes suivantes :**

- Configurer des autorisations d’API si votre application doit accéder à Microsoft Graph ou à d’autres API
- Ajoutez des certificats ou des secrets client si votre type d'application les requiert (pas nécessaire pour les applications à page unique utilisant le flux de code d'autorisation)
- Tester votre configuration avec votre code d’application

Note

**Bonne pratique** : les nouvelles inscriptions d’applications sont masquées par défaut pour les utilisateurs. Lorsque vous êtes prêt à permettre aux utilisateurs de voir l’application sur leur page Mes applications, activez-la via les **applications d’entreprise** , puis **les propriétés**, et définissez la valeur de **Visible pour les utilisateurs ?** sur **Oui**.


## Configurer l’authentification d’application

Les paramètres de chaque type d’application, y compris les URI de redirection, sont configurés dans les **configurations de plateforme** dans le Centre d’administration Entra. Certaines plateformes, telles que les applications **web** et **monopage**, vous obligent à spécifier manuellement un URI de redirection. Pour d’autres plateformes, telles que **mobile et bureau**, vous pouvez sélectionner parmi les URI de redirection générés pour vous lorsque vous configurez leurs autres paramètres.

Important

La configuration spécifique à la plateforme garantit que votre application utilise le flux d’authentification et les paramètres de sécurité appropriés pour chaque environnement cible.

Pour configurer les paramètres d’application en fonction de la plateforme ou de l’appareil que vous ciblez, procédez comme suit :

1. Ouvrez le **Centre d’administration Entra**, puis, sous **Applications**, sélectionnez **Inscriptions d’applications**.
2. Sélectionnez votre application.
3. Sous **Gérer**, sélectionnez **Authentification**.
4. Sous **Configurations de la** plateforme, sélectionnez **Ajouter une plateforme**.
5. Sous **Configurer des plateformes**, sélectionnez la vignette de votre type d’application (plateforme) pour configurer ses paramètres.          **Plateforme**  **Paramètres de configuration**     Le Web Entrez un **URI de redirection** pour votre application web côté serveur. Cet URI est l’emplacement où la plateforme d’identités Microsoft redirige les utilisateurs et envoie des jetons de sécurité après l’authentification. Vous pouvez également configurer des URL de déconnexion de canal frontal et des paramètres de jeton.   Application à page unique Entrez un **URI de redirection** pour votre application JavaScript côté client (Angular, React, Vue.jsou Blazor WebAssembly). Utilise le flux de code d’autorisation avec la clé de preuve pour l’échange de code (PKCE) pour renforcer la sécurité. Vous pouvez également configurer des URL de déconnexion de front-channel.   iOS / macOS Entrez **l’ID de bundle d’application**. Recherchez-le dans **les paramètres de build** ou dans Xcode dans *Info.plist*. Un URI de redirection est généré automatiquement pour vous.   Android Entrez le **nom du package** d’application (trouvé dans *AndroidManifest.xml*) et générez le **hachage signature**. Un URI de redirection est généré automatiquement pour vous.   Applications de bureau et mobiles Sélectionnez les **URI de redirection** suggérés ou spécifiez **des URI de redirection personnalisés**. Pour les applications de bureau avec navigateur incorporé : `https://login.microsoftonline.com/common/oauth2/nativeclient`. Pour les applications de bureau avec navigateur système : `http://localhost`. Choisissez en fonction des exigences de votre bibliothèque d’authentification.
6. Sélectionnez **Configurer** pour terminer la configuration de la plateforme.

Note

**Remarque de sécurité** : chaque type de plateforme a des exigences de sécurité spécifiques. Les applications monopage utilisent automatiquement le flux de code d’autorisation avec PKCE, tandis que les applications web peuvent utiliser différents flux de travail en fonction de votre configuration.

#### URI de redirection

Un URI de redirection (également appelé URL de réponse) est l’emplacement où le serveur d’autorisation envoie l’utilisateur, une fois que l’application a correctement autorisé et accordé un code d’autorisation ou un jeton d’accès. Le serveur d’autorisation envoie le code ou le jeton à l’URI de redirection. Il est donc important que vous inscriviez l’emplacement qui convient dans le cadre du processus d’inscription de l’application.

**Exigences de sécurité critiques :** Le modèle d’application Entra spécifie ces restrictions pour les URI de redirection :

- **Exigence HTTPS** : les URI de redirection doivent commencer par le schéma `https`. Il existe des exceptions pour les URI de redirection localhost pendant le développement.
- **Sensibilité à la casse** : les URI de redirection sont sensibles à la casse et doivent respecter la casse du chemin d’URL de l'application qui s'exécute.
- **Gestion des slashes finaux** :
  - Les URI de redirection non configurés avec un segment de chemin d’accès sont renvoyés avec un slash final (`/`) dans la réponse.
  - Les URI de redirection qui contiennent un segment de chemin ne sont pas complétées par une barre oblique à la fin dans la réponse.

- **Caractères** spéciaux : les URI de redirection ne prennent pas en charge ces caractères spéciaux : `! $ ' ( ) , ;`

Note

**Bonne pratique** : testez toujours vos URI de redirection dans un environnement de développement avant de le déployer en production pour garantir la gestion et la sécurité des jetons appropriées.


## Configurez les autorisations d’API

La plateforme d’identités Microsoft met en œuvre le protocole d’autorisation OAuth 2.0. OAuth 2.0 est une méthode par le biais de laquelle une application externe peut accéder aux ressources hébergées sur le web pour le compte d’un utilisateur. Toute ressource hébergée sur le web qui s’intègre à la plateforme d’identités Microsoft a un identificateur de ressource ou **un URI d’ID d’application**. Il en va de même pour toutes les ressources externes intégrées à la plateforme d’identités Microsoft.

Toutes ces ressources peuvent également définir un ensemble **d’autorisations** (également **appelées étendues**) qui peuvent être utilisées pour diviser les fonctionnalités de cette ressource en blocs plus petits. Par exemple, Microsoft Graph dispose des autorisations nécessaires pour effectuer les tâches suivantes (entre autres) :

- Lire le calendrier d’un utilisateur
- Écrire dans le calendrier d’un utilisateur
- Envoyer des messages en tant qu’utilisateur

**Avantages de sécurité :** En raison de ces types de définitions d’autorisation, la ressource a un contrôle précis sur ses données et la façon dont les fonctionnalités d’API sont exposées. Une application externe peut demander ces autorisations aux utilisateurs et aux administrateurs, qui doivent approuver la demande avant que l’application puisse accéder aux données ou agir au nom d’un utilisateur. Quand la fonctionnalité d’une ressource est segmentée en petits ensembles d’autorisations, les applications externes peuvent être créées pour demander uniquement les autorisations dont elles ont besoin pour effectuer leur fonction.

**Principe du privilège minimum :** les utilisateurs et les administrateurs savent exactement à quelles données l’application peut accéder, et les administrateurs peuvent être plus confiants quant à l’absence d’intention malveillante de l’application. Les développeurs doivent toujours demander des **privilèges minimum**, en demandant uniquement les autorisations dont ils ont besoin pour que leurs applications fonctionnent.

### Configurez les autorisations d’API

Configurez **les autorisations déléguées** à Microsoft Graph pour que votre application cliente effectue des opérations pour le compte de l’utilisateur connecté, par exemple lire son e-mail ou modifier son profil. Par défaut, les utilisateurs de votre application cliente sont invités à se connecter pour donner leur consentement aux autorisations déléguées configurées pour celle-ci.

Important

Les autorisations déléguées fonctionnent pour le compte de l’utilisateur connecté, ce qui signifie que l’application ne peut accéder qu’aux données auxquelles l’utilisateur lui-même peut accéder. Cela fournit une couche de sécurité supplémentaire au-delà des autorisations de l’application.

1. Connectez-vous au **Centre d’administration Entra**.
2. Sélectionnez **Applications** , **inscriptions d’applications**, puis votre application cliente.
3. Sélectionnez **des autorisations d’API** , puis **ajoutez une autorisation**>**Microsoft Graph**.
4. Sélectionnez **Autorisations déléguées**. Microsoft Graph expose de nombreuses autorisations, avec celles les plus couramment utilisées affichées en haut de la liste.
5. Sous **Sélectionner des autorisations**, sélectionnez les autorisations suivantes :     **Autorisation**  **Description**  **Cas d'utilisation**     Messagerie électronique Afficher l’adresse e-mail des utilisateurs Afficher l’e-mail de l’utilisateur dans l’interface utilisateur de l’application   accès hors ligne Maintenir l’accès aux données que vous lui avez donnés Activer les jetons d’actualisation pour l’accès à long terme   openid Connecter les utilisateurs Authentification de base (obligatoire pour la connexion)   profil Afficher le profil de base des utilisateurs Afficher le nom de l’utilisateur et les informations de profil de base
6. Sélectionnez **Ajouter des autorisations** pour terminer le processus.

Note

Il s’agit des étendues **OpenID Connect** de base couramment demandées par la plupart des applications. Vous pouvez avoir besoin d’autorisations supplémentaires en fonction des exigences de votre application spécifiques.

**Consentement de** l’administrateur : en tant qu’administrateur, vous pouvez accorder le consentement au nom de tous les utilisateurs de votre organisation, ce qui élimine la nécessité d’un consentement individuel de l’utilisateur. Le consentement administrateur est utile pour les applications organisationnelles où l’approbation de l’administrateur est préférée ou requise par la politique.


## Créer des rôles d’application

**Les rôles d’application** sont une fonctionnalité puissante que vous pouvez et devez configurer lors de l’exécution d’une inscription d’application. Un rôle d’application est une revendication personnalisée qui peut être appliquée aux utilisateurs, groupes ou applications. La revendication apparaît dans le jeton généré lorsqu’un utilisateur s’authentifie pour une application. Les données de rôle d’application dans le jeton peuvent ensuite être utilisées dans l’application à des fins d’autorisation.

**Principaux avantages :**

- **Alternative aux déclarations de groupe** : les rôles d'application remplacent les groupes pour l'autorisation. Ils évitent les problèmes de dépassement de groupe et n'exigent pas de licence Entra ID P1.
- **Autorisation affinée** : permet un contrôle précis sur ce que les utilisateurs peuvent faire au sein de votre application
- **Code simplifié** : votre application peut rechercher des revendications de rôle spécifiques au lieu de mapper des groupes à des autorisations

Pour tirer parti de cette fonctionnalité, vous définissez des rôles d’application qui autorisent les utilisateurs et les groupes en tant que types de membres. Comme indiqué dans l’écran suivant, sélectionnez **Utilisateurs/Groupes** pour les **types de membres autorisés** lors de la création de rôles d’application.

### Affichage des rôles d’application dans les jetons

Une fois que l’administrateur de l’application a créé des rôles d’application dans l’inscription de votre application, les administrateurs informatiques peuvent affecter des utilisateurs et des groupes à ces rôles. Votre application reçoit une **revendication de rôles** dans des jetons (jetons d’ID pour les applications, jetons d’accès pour les API). Elle contient tous les rôles attribués par l’utilisateur connecté, comme indiqué dans l’exemple de jeton suivant :

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

### Meilleures pratiques pour les rôles d’application

**Définissez toujours un rôle d’utilisateur de référence :** Lorsque vous créez des rôles d’application qui autorisent les utilisateurs et les groupes en tant que membres, définissez toujours un rôle d’utilisateur de référence sans autorisations élevées. Lorsqu’une configuration d’application d’entreprise nécessite une affectation, seuls les utilisateurs ayant une affectation directe à une application ou une appartenance à un groupe affecté à l’application peuvent utiliser l’application.

**Conditions requises pour l’affectation :** Lorsqu’un utilisateur ou un groupe est affecté à l’application, l’un des rôles d’application définis doit faire partie de l’affectation. Si votre application a des rôles élevés (par exemple, « administrateur ») pour l’application, tous les utilisateurs et groupes reçoivent automatiquement le rôle d’administrateur, qui enfreint le principe du privilège minimum.

**Approche recommandée :** définissez un rôle de base (par exemple, « utilisateur » ou « lecteur »). Les utilisateurs et les groupes affectés à l’application peuvent alors recevoir ce rôle d’utilisateur de base, ce qui garantit les niveaux d’accès appropriés.

### Avantages de l’utilisation de rôles d’application

**Évitez les revendications de dépassement de groupe :** En plus d’éviter les revendications de dépassement de groupe, les rôles d’application offrent plusieurs avantages par rapport à l’autorisation basée sur un groupe traditionnel.

**Logique d’autorisation simplifiée :** Un autre avantage clé n’est pas nécessaire de mapper entre des groupes ou des noms et leur signification dans votre application. Par exemple, votre code peut simplement rechercher la revendication de rôle « administrateur ». L'alternative consistant à itérer à travers les groupes dans les revendications des groupes et à déterminer les ID de groupe auxquels accorder les fonctionnalités d'administration.

**Meilleure sécurité et facilité de maintenance :**

- **Intention claire** : les noms de rôles tels que « administrateur », « éditeur » et « visionneuse » sont plus descriptifs que les GUID de groupe
- **Complexité réduite** : il n’est pas nécessaire de gérer les mappages d’ID de groupe dans le code de votre application
- **Meilleure portabilité** : les rôles d’application peuvent être facilement répliqués dans différents environnements


## Évaluation du module

Choisissez la meilleure réponse à chacune des questions ci-dessous.

### Vérifiez vos connaissances


## Résumé

L’inscription d’applications dans Entra ID est le processus fondamental d’établissement d’une configuration d’identité pour votre application au sein de la plateforme d’identités Microsoft. Ce processus garantit l’intégration sécurisée et assure un contrôle précis sur l’authentification et l’autorisation.

### Résultats clés de l’apprentissage

Dans ce module, vous avez appris à :

**Planifier et configurer l’inscription d’application :**

- Comprendre la relation entre les objets d’application et les principaux de service
- Choisissez les types de comptes pris en charge appropriés (locataire unique ou locataires multiples)
- Planifier les exigences de sécurité et les flux d’authentification

**Implémenter l’authentification moderne :**

- Configurer des applications à page unique à l’aide du flux de code d’autorisation avec Proof Key for Code Exchange (PKCE)
- Configurer les paramètres d’authentification spécifiques à la plateforme
- Implémenter des modèles d’URI de redirection sécurisés

**Gérer les autorisations et l'authentification de l’API :**

- Configurer des autorisations déléguées en suivant le principe du privilège minimum
- Comprendre la différence entre les autorisations déléguées et les autorisations d’application
- Implémenter des flux de travail de consentement appropriés

**Fonctionnalités de sécurité avancées :**

- Créer et gérer des rôles d’application pour une autorisation affinée
- Concevoir des rôles d’utilisateur de référence pour éviter l’escalade des privilèges
- Implémenter l’authentification basée sur des certificats sur les secrets client

### Bonnes pratiques de sécurité abordées

**Flux d’authentification moderne :**

- Flux de code d’autorisation avec PKCE pour une sécurité renforcée
- Gestion et validation des jetons appropriées
- Gestion des informations d’identification sécurisées (certificats préférés aux secrets)

**Access Control :**

- Principe du privilège minimum dans les demandes d’autorisation
- Contrôle d’accès en fonction du rôle à l’aide de rôles d’application
- Séparation appropriée entre les autorisations de l’utilisateur et de l’application

**Workload Identity Security :**

- Identités managées comme approche recommandée pour les charges de travail Azure
- Sécuriser la gestion des entités de service
- Authentification basée sur des certificats pour une sécurité renforcée

### Terminologie et outils modernes

Ce module a mis en évidence la terminologie et les outils actuels d’Entra ID :

- **Centre d’administration Entra** en tant qu’interface de gestion principale
- **Identités de charge de travail** pour la gestion des identités non humaines
- Relation entre **objets d’application** et **principaux de service**
- **PKCE** et **CORS** pour la sécurité des applications web modernes

En implémentant ces pratiques, vous pouvez vous assurer que vos applications s’intègrent en toute sécurité à la plateforme d’identités Microsoft tout en suivant les normes de sécurité actuelles et les meilleures pratiques.
