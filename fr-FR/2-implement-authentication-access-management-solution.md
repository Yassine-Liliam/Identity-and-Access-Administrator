# Implémenter une solution de gestion des accès et des authentifications

> SC-300 — learning path 2/4
> https://learn.microsoft.com/fr-fr/training/paths/implement-authentication-access-management-solution/

## Modules

- **Sécurisez les utilisateurs Microsoft Entra avec l’authentification multifacteur** (6 units)
- **Gérer l’authentification des utilisateurs** (12 units)
- **Planifier, implémenter et administrer l’accès conditionnel** (13 units)
- **Gérer Microsoft Entra Identity Protection** (11 units)
- **Implémenter le Gestionnaire d’accès pour des ressources Azure** (10 units)
- **Déployer et configurer Accès global sécurisé Microsoft Entra** (10 units)


---

# Sécurisez les utilisateurs Microsoft Entra avec l’authentification multifacteur

_https://learn.microsoft.com/fr-fr/training/modules/secure-aad-users-with-mfa/_


## Présentation

Imaginez que vous êtes ingénieur sécurité d’une grande usine de fabrication. Votre entreprise honore plusieurs gros contrats avec des sociétés de matériel électronique grand public connues, dont Microsoft. Les clients vous envoient leurs conceptions confidentielles, que vous stockez ensuite dans votre infrastructure Azure. Nombreux sont les hackers qui rêveraient de mettre la main sur ces créations nouvelle génération. C’est votre travail pour les protéger.

Vous avez beaucoup travaillé pour renforcer votre réseau et vous assurer que seules les personnes autorisées ont accès aux données du client. Il y a toujours un gros trou à protéger : les comptes d’utilisateur. Ce module décrit l’une des meilleures façons d’empêcher les utilisateurs non autorisés d’accéder via un nom d’utilisateur et un mot de passe, qui est l’authentification multifacteur.

### Objectifs d’apprentissage

Dans ce module, vous avez :

- En savoir plus sur l’authentification multifacteur Microsoft Entra (MFA).
- Créez un plan pour déployer l’authentification multifacteur Microsoft Entra.
- Activez l’authentification multifacteur Microsoft Entra pour les utilisateurs et les applications spécifiques.

### Prérequis

- Connaissance de base du portail Azure
- Connaissance de base de Microsoft Entra ID


## Qu’est-ce que l’authentification multifacteur Microsoft Entra ?

La protection de vos ressources cloud est l’un des principaux objectifs des groupes de sécurité. L’un des moyens les plus courants qu’emploient les utilisateurs non autorisés pour obtenir un accès aux systèmes consiste à se procurer un nom d’utilisateur et un mot de passe valide. Azure peut contribuer à réduire ce risque grâce à plusieurs fonctionnalités de Microsoft Entra ID, notamment :

- **Règles de complexité des mots de passe** : Ces règles obligent les utilisateurs à générer des mots de passe plus difficiles à deviner.
- **Règles d’expiration des mots de passe** : Vous pouvez forcer les utilisateurs à changer leurs mots de passe régulièrement, et à les empêcher d’utiliser des mots de passe déjà utilisés.
- **Réinitialisation de mot de passe en libre-service (SSPR)** : Cette approche permet aux utilisateurs de réinitialiser leur mot de passe s’ils l’oublient sans faire appel au service informatique.
- **Protection Microsoft Entra ID** : Pour aider à protéger les identités de votre organisation, vous pouvez configurer des stratégies basées sur les risques qui répondent automatiquement aux comportements à risque. Ces stratégies peuvent automatiquement bloquer des comportements ou déclencher une action corrective, notamment exiger un changement de mot de passe.
- **Protection par mot de passe Microsoft Entra** : Vous pouvez bloquer les mots de passe couramment utilisés et compromis via une liste de mots de passe interdits globale.
- **Verrouillage intelligent Microsoft Entra** : Le verrouillage intelligent neutralise les hackers qui essaient de deviner vos mots de passe ou d’utiliser des méthodes de force brute pour rentrer dans vos systèmes. Il reconnaît les connexions provenant d’utilisateurs validés et les traite différemment de celles des hackers et autres sources inconnues.
- **Proxy d’application Microsoft Entra** : Vous pouvez provisionner un accès distant avec une sécurité renforcée pour les applications web locales.
- **Authentification unique (SSO)** : Vous pouvez activer l’accès par l’authentification unique à vos applications, notamment à des milliers d’applications SaaS pré-intégrées.
- **Microsoft Entra Connect** : Créez et gérez une seule identité pour chaque utilisateur sur toute l’entreprise hybride pour assurer une synchronisation des utilisateurs, des groupes et des appareils.

Toutes ces approches sont géniales pour dissuader toute personne de *deviner* un mot de passe ou d’utiliser une attaque par force brute. Toutefois, les mots de passe sont parfois obtenus en utilisant l’ingénierie sociale ou des pratiques de sécurité physiques médiocres, comme le fait d’écrire votre mot de passe sur un post-it sous votre clavier ! Dans ces cas, ces fonctionnalités n’arrêtent pas l’intrusion. Les administrateurs de la sécurité souhaitent plutôt se tourner vers *L’authentification multifacteur Microsoft Entra*.

### Qu’est-ce que l’authentification multifacteur Microsoft Entra ?

L’authentification multifacteur (MFA) Microsoft Entra offre une sécurité supplémentaire pour vos identités en exigeant au moins deux éléments pour une authentification complète.

Ces éléments se répartissent en trois catégories :

- **Quelque chose que vous connaissez** : il pourrait s’agir d’un mot de passe ou de la réponse à une question de sécurité.
- **Quelque chose que vous possédez** : il pourrait s’agir d’une application mobile qui reçoit une notification ou un d’appareil de génération de jetons.
- **Quelque chose que vous êtes** : en général, il s’agit d’une propriété biométrique, comme la détection du visage ou des empreintes digitales utilisée sur de nombreux appareils mobiles.

![Image conceptuelle des parties de MFA.](https://learn.microsoft.commedia/2-mfa-example.png)

L’utilisation de l’authentification multifacteur Microsoft Entra améliore la sécurité de l’identité en limitant l’impact de l’exposition des mots de passe. Pour s’authentifier entièrement, un pirate malveillant a également besoin d’un deuxième facteur, tel que le téléphone, l’empreinte digitale ou le visage de l’utilisateur. L’authentification multifacteur devrait toujours être activée, car il s’agit du moyen le plus efficace d’empêcher une connexion non autorisée.

L’authentification multifacteur Microsoft Entra est la solution de vérification en deux étapes Microsoft. L’authentification multifacteur Microsoft Entra contribue à sécuriser l'accès aux données et aux applications tout en répondant à la demande de l'utilisateur d'un processus d'authentification simple. Il offre une authentification forte pour diverses méthodes de vérification : appels téléphoniques, envoi de SMS ou vérification sur application mobile.

La sécurité de l'authentification multifacteur Microsoft Entra repose sur son approche en couches. La demande de plusieurs facteurs d’authentification constitue une grande difficulté pour les hackers. Même si un hacker réussit à apprendre le mot de passe de l’utilisateur, cela ne sert à rien s’il n’a pas l’appareil de confiance. Si l’utilisateur perd l’appareil, la personne qui le trouve ne peut pas l’utiliser sans le mot de passe de l’utilisateur.

### Comment obtenir l’authentification multifacteur ?

L’authentification multifacteur est fournie avec les offres suivantes :

- **Microsoft Entra ID P1 ou P2** ou **Microsoft 365 Business** : Ces deux offres prennent en charge l’authentification multifacteur Microsoft Entra à l’aide de [paramètres de sécurité par défaut](https://learn.microsoft.com/fr-fr/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) qui exigent l’authentification multifacteur.
- Les licences **Microsoft Entra ID Gratuites** ou **Microsoft 365** autonome : Ces deux types de licences utilisent des [paramètres de sécurité par défaut](https://learn.microsoft.com/fr-fr/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) pour imposer une authentification multifacteur aux utilisateurs et aux administrateurs.


## Planifiez votre déploiement de l’authentification multifacteur

Avant de démarrer à déployer l’authentification multifacteur Microsoft Entra, vous devez décider de plusieurs choses.

Tout d’abord, déployez MFA par vague. Commencez avec un petit groupe d’utilisateurs pilotes pour évaluer la complexité de votre environnement et identifier les problèmes de configuration ou les applications ou appareils non pris en charge. Élargissez ce groupe au fur et à mesure et évaluez les résultats après chaque passage jusqu’à ce que l’intégralité de votre entreprise soit incluse.

Ensuite, veillez à créer un plan de communication complet. L’authentification multifacteur Microsoft Entra a plusieurs exigences d’interaction avec l’utilisateur, notamment un processus d’inscription. Informez les utilisateurs de chaque étape. Indiquez-leur ce qu’ils doivent faire, les dates importantes et comment obtenir des réponses aux questions en cas de problèmes. Microsoft fournit des [modèles de communication](https://www.microsoft.com/download/details.aspx?id=57600&WT.mc_id=rss_alldownloads_all), notamment des affiches et des modèles d’e-mail, pour vous aider à rédiger vos communications.

### Stratégies d’authentification multifacteur Microsoft Entra

L’authentification multifacteur Microsoft Entra est appliquée avec des stratégies d’*accès conditionnel*. Les stratégies d’accès conditionnel sont des instructions `IF-THEN`. Si (*IF*) un utilisateur souhaite accéder à une ressource, alors (*THEN*) il doit effectuer une action. Par exemple, un responsable de la paie souhaite accéder à l’application de paie et doit effectuer une authentification multifacteur pour ce faire. Les autres demandes d’accès courantes qui peuvent nécessiter MFA sont :

- Si une application cloud spécifique est accessible.
- Si un utilisateur accède à un réseau spécifique.
- Si un utilisateur accède à une application cliente spécifique.
- Si un utilisateur inscrit un nouvel appareil.

### Décider des méthodes d’authentification prises en charge

Quand vous activez l’authentification multifacteur Microsoft Entra, vous pouvez choisir les méthodes d’authentification que vous voulez rendre disponibles. Vous devez toujours prendre en charge plusieurs méthodes afin que les utilisateurs disposent d’une option de secours au cas où leur méthode principale ne serait pas disponible. Vous pouvez choisir parmi les méthodes suivantes :

| Méthode | Description |
|---|---|
| **Code de vérification d’une application mobile**. | Une application d’authentification mobile telle que l’application Microsoft Authenticator peut être utilisée pour récupérer un code de vérification OATH qui est ensuite entré dans l’interface de connexion. Ce code change toutes les 30 secondes et l’application fonctionne même si la connectivité est limitée. Cette approche ne fonctionne pas en Chine sur les appareils Android. |
| **Notification sur l’application mobile** | Azure peut envoyer une notification Push à une application d’authentification mobile telle que Microsoft Authenticator. L’utilisateur peut sélectionner la notification Push et vérifier la connexion. |
| **Appel à un téléphone** | Azure peut appeler un numéro de téléphone fourni. L’utilisateur approuve alors l’authentification en se servant du clavier. Cette méthode est préférée pour les sauvegardes. |
| **Clé de sécurité FIDO2** | Les clés de sécurité FIDO2 sont une méthode d’authentification sans mot de passe basée sur des normes qui ne peuvent pas être usurpées. Ces clés sont généralement des périphériques USB, mais elles peuvent également utiliser les technologies Bluetooth ou NFC. |
| **Windows Hello Entreprise** | Windows Hello Entreprise remplace les mots de passe par une authentification à deux facteurs forte sur les appareils. Cette authentification se compose d’un type d’informations d’identification utilisateur qui sont liées à un appareil, et utilise un code biométrique ou un code PIN. |
| **Jetons OATH** | Les jetons OATH peuvent être des applications logicielles telles que l’application Microsoft Authenticator et d’autres applications d’authentification. Ils peuvent également être des jetons matériels que les clients peuvent acheter auprès de différents fournisseurs. |

Les administrateurs peuvent activer une ou plusieurs de ces options. Les utilisateurs peuvent ensuite choisir de prendre en charge chaque méthode d’authentification qu’ils souhaitent utiliser.

### Sélection d’une méthode d’authentification

Enfin, vous devez décider comment les utilisateurs inscrivent les méthodes qu’ils auront sélectionnées. L’approche la plus simple consiste à utiliser *Microsoft Entra ID Protection*. Si votre organisation a des licences pour la Protection des identités, vous pouvez la configurer pour inviter les utilisateurs à s’inscrire à la MFA la prochaine fois qu’ils se connectent.

Vous pouvez également inviter les utilisateurs à s’inscrire à la MFA lorsqu’ils essaient d’utiliser une application ou un service qui demande une authentification multifacteur. Enfin, vous pouvez procéder à l’inscription avec une stratégie d’accès conditionnel appliquée à un groupe Azure contenant tous les utilisateurs de votre organisation. Cette approche nécessite d’intervenir manuellement pour vérifier régulièrement le groupe et supprimer des utilisateurs inscrits. Pour obtenir des scripts utiles pour automatiser une partie de ce processus, consultez [Planifier un déploiement de l’authentification multifacteur Microsoft Entra](https://learn.microsoft.com/fr-fr/azure/active-directory/authentication/howto-mfa-getstarted#enforcing-registration).


## Exercice : activer l’authentification multifacteur Microsoft Entra

Vous pouvez passer en revue les étapes de base nécessaires à la configuration et à l’activation de l’authentification multifacteur Microsoft Entra avec des stratégies conditionnelles. *Gardez en tête qu’un vrai déploiement nécessite une grande réflexion et une planification importante*. Assurez-vous d’évaluer les liens de la documentation à la fin de ce module avant d’activer l’authentification multifacteur dans vos environnements.

Important

Pour cet exercice, vous avez besoin de Microsoft Entra ID P1 ou P2. Vous pouvez utiliser un [essai gratuit de 30 jours](https://azure.microsoft.com/trial/get-started-active-directory/) pour essayer cette fonctionnalité ou simplement lire les instructions ci-dessous pour comprendre le flux.

### Configurer des options d’authentification multifacteur

1. Connectez-vous au [portail Azure](https://portal.azure.com/) à l’aide d’un compte d’administrateur d’authentification.
2. Recherchez **l'ID Microsoft Entra** et accédez au tableau de bord Microsoft Entra ID.
3. Sélectionnez **Sécurité** dans le menu de gauche.
4. Sous le menu **Gérer**, sélectionnez **Authentification multifacteur**. Vous trouvez ici des options pour l’authentification multifacteur.
5. Sous **Configurer**, sélectionnez **Paramètres informatiques supplémentaires de l’authentification multifacteur**. Dans la page obtenue, vous pouvez voir toutes les options MFA pour Azure sous **Paramètres du service**.      Ici, vous pouvez activer ou désactiver les *mots de passe d’application*, ce qui permet aux utilisateurs de créer des mots de passe uniques de compte pour les applications qui ne prennent pas en charge l’authentification multifacteur. Cette fonctionnalité permet à l’utilisateur de s’authentifier avec son identité Microsoft Entra en utilisant un mot de passe différent propre à cette application.

### Configurer les règles d’accès conditionnel pour la MFA

Examinez ensuite comment configurer des règles de la stratégie d’accès conditionnel afin que les utilisateurs invités utilisent l’authentification multifacteur pour accéder à des applications spécifiques sur votre réseau.

1. Revenez au Portail Azure, puis sélectionnez **Microsoft Entra ID**>**Sécurité**>**Accès conditionnel**.
2. Dans le menu supérieur, sélectionnez **Créer une stratégie**.
3. Nommez votre stratégie, par exemple *Tous les invités*.
4. Sous **Utilisateurs**, sélectionnez **0 utilisateur et groupe sélectionné**.
  1. Sous **Inclure**, choisissez **Sélectionner les utilisateurs et les groupes**.
  2. Sélectionnez utilisateurs et groupes, puis choisissez **Sélectionner**.

5. Sous **Ressources cibles**, sélectionnez **Aucune ressource cible sélectionnée**.
  1. Sélectionnez **Applications cloud**.
  2. Sous **Inclure**, choisissez **Sélectionner les applications**.
  3. Sous **Sélectionner**, choisissez **Aucun**. Sélectionnez les applications dans les options de droite, puis choisissez **Sélectionner**.

6. Sous **Conditions**, sélectionnez **0 condition sélectionnée**.
  1. Sous **Emplacements**, sélectionnez **Non configuré**.
  2. Sous **Configurer**, sélectionnez **Oui**, puis **N’importe quel emplacement**.

7. Sous **Accorder**, sélectionnez **0 contrôle sélectionné**.
  1. Assurez-vous que **Accorder l’accès** est sélectionné.
  2. Sélectionnez l’option **Exiger l’authentification multifacteur** et choisissez **Sélectionner**. Cette option applique l’authentification multifacteur.

8. Définissez l’option **Activer la stratégie** sur **Activée**, puis sélectionnez **Créer**.

L’authentification multifacteur est maintenant activée pour vos applications sélectionnées. La prochaine fois qu’un utilisateur ou un invité tente de se connecter à cette application, il va être invité à s’inscrire à l’authentification multifacteur.


## Configurer des méthodes d’authentification multifacteur

Comme nous l’avons vu précédemment dans ce module, il est recommandé d’autoriser les utilisateurs à sélectionner plusieurs méthodes d’authentification au cas où leur méthode principale ne serait pas disponible.

Quand un utilisateur se connecte pour la première fois à un service qui exige MFA, il est invité à spécifier sa méthode d’authentification multifacteur préférée, comme indiqué dans la capture d’écran suivante :

Conseil

Si vous avez suivi l’exercice précédent et activé MFA pour un compte et une application, vous pouvez essayer d’accéder à cette application avec le compte d’utilisateur spécifié. Vous devez voir le flux précédent.

Une fois l’inscription effectuée, chaque fois que l’utilisateur se connecte à un service ou une application qui exige MFA, le processus de connexion Azure l’invite à entrer les informations d’authentification, comme le montre l’image suivante :

### Méthodes d’authentification Azure

Comme vous l’avez vu précédemment, l’administrateur peut configurer plusieurs méthodes d’authentification. Certaines d’entre elles prennent aussi en charge la réinitialisation de mot de passe en libre-service (SSPR) qui permet aux utilisateurs de réinitialiser leur mot de passe en fournissant une deuxième forme d’authentification. Vous pouvez coupler ce service avec l’authentification multifacteur Microsoft Entra pour faciliter le fardeau du personnel informatique.

Le tableau suivant liste les méthodes d’authentification et les services qui peuvent les utiliser.

| Méthode d’authentification | Services |
|---|---|
| **Mot de passe** | Authentification multifacteur Microsoft Entra et SSPR |
| **Questions de sécurité** | SSPR |
| **Adresse e-mail** | SSPR |
| **Windows Hello Entreprise** | Authentification multifacteur Microsoft Entra et SSPR |
| **Clé de sécurité FIDO2** | Authentification multifacteur Microsoft Entra et SSPR |
| **Application Microsoft Authenticator** | Authentification multifacteur Microsoft Entra et SSPR |
| **Jetons matériels OATH** | Authentification multifacteur Microsoft Entra et SSPR |
| **Jeton logiciel OATH** | Authentification multifacteur Microsoft Entra et SSPR |
| **SMS** | Authentification multifacteur Microsoft Entra et SSPR |
| **Appel vocal** | Authentification multifacteur Microsoft Entra et SSPR |
| **Mots de passe d’application** | Authentification multifacteur Microsoft Entra dans certains cas |

#### Mot de passe

Cette méthode est la seule que vous ne pouvez pas désactiver.

#### Questions de sécurité

Cette méthode est disponible uniquement pour les comptes non administratifs qui utilisent la réinitialisation de mot de passe en libre-service.

- Azure stocke les questions de sécurité de façon privée et très sécurisée sur un objet utilisateur dans l’annuaire. Seuls les utilisateurs peuvent répondre aux questions et uniquement lors de l’inscription. Un administrateur ne peut pas lire ni changer les questions ou les réponses d’un utilisateur.
- Azure fournit 35 questions prédéfinies, toutes traduites et localisées en fonction des paramètres régionaux du navigateur.
- Vous pouvez personnaliser les questions à l’aide de l’interface administrative. Azure les affiche dans la langue entrée. La longueur maximale est de 200 caractères.

#### Adresse e-mail

Cette méthode est disponible uniquement dans SSPR. Nous vous recommandons d’éviter d’utiliser un compte e-mail dont l’accès n’exige pas le mot de passe Microsoft Entra de l’utilisateur.

#### Windows Hello Entreprise

Windows Hello Entreprise fournit une authentification biométrique fiable et entièrement intégrée qui repose sur la reconnaissance faciale ou la correspondance des empreintes digitales. Windows Hello Entreprise, les clés de sécurité FIDO2 et Microsoft Authenticator sont des solutions sans mot de passe.

#### Clés de sécurité FIDO2

Les clés de sécurité FIDO2 sont une méthode d’authentification sans mot de passe basée sur des normes qu’il est impossible d’hameçonner. Elles peuvent se présenter dans n’importe quel facteur de forme. Fast Identity Online (FIDO) est une norme ouverte d’authentification sans mot de passe.

Les utilisateurs peuvent enregistrer, puis sélectionner une clé de sécurité FIDO2 dans l’interface de connexion en tant que principal moyen d’authentification. Ces clés de sécurité FIDO2 sont généralement des périphériques USB, mais elles peuvent également utiliser les technologies Bluetooth ou NFC.

Les utilisateurs peuvent se servir de leurs clés de sécurité FIDO2 pour se connecter à leurs appareils Windows 10 Microsoft Entra ID ou joints à Microsoft Entra hybride. Ils peuvent bénéficier de l’authentification unique sur leurs ressources cloud et locales. Les utilisateurs peuvent également se connecter aux navigateurs pris en charge.

#### Application Microsoft Authenticator

Cette méthode est disponible pour Android et iOS. Les utilisateurs peuvent [inscrire leur application mobile ici](https://aka.ms/mfasetup).

- L’application Microsoft Authenticator permet d’empêcher tout accès non autorisé aux comptes. Elle envoie une notification qui permet d’arrêter les transactions frauduleuses sur votre smartphone ou tablette. Les utilisateurs voient la notification et confirment ou refusent la demande.
- Les utilisateurs peuvent faire appel à l’application Microsoft Authenticator ou à une autre application tierce comme jeton logiciel pour générer un code de vérification OATH. Après avoir entré le nom d’utilisateur et le mot de passe, les utilisateurs entrent le code fourni par l’application sur l’écran de connexion. Le code de vérification fournit une deuxième forme d’authentification. Les utilisateurs peuvent également configurer l’application Microsoft Authenticator afin qu’elle leur envoie une notification Push qu’ils sélectionnent et approuvent pour se connecter.

#### Jetons matériels OATH

**OATH** est un standard ouvert qui spécifie le mode de génération des codes de mot de passe à usage unique. Microsoft Entra ID prend en charge l’utilisation des jetons OATH-TOTP `SHA-1` de 30 secondes ou 60 secondes. Les clients peuvent obtenir ces jetons auprès du fournisseur de leur choix. Les clés secrètes sont limités à 128 caractères, ce qui n’est probablement pas compatible avec tous les jetons.

#### Jetons logiciels OATH

Les jetons logiciels OATH sont généralement des applications telles que l’application Microsoft Authenticator et d’autres applications d’authentification. Microsoft Entra ID génère la clé secrète, ou la valeur de départ, qui est entrée dans l’application et utilisée pour générer chaque code OTP.

#### SMS

Azure envoie un code de vérification à un téléphone mobile par SMS. L’utilisateur doit entrer le code dans le navigateur pendant une période de temps spécifique pour continuer.

#### Appel vocal

Azure utilise un système vocal automatisé pour appeler le numéro et le propriétaire utilise le clavier pour confirmer l’authentification. Cette option n’est pas disponible pour le niveau Microsoft Entra Gratuit/Essai.

#### Mot de passe des applications

Certaines applications qui ne sont pas des navigateurs ne prennent pas en charge l’authentification multifacteur Microsoft Entra. Si les utilisateurs sont activés pour l’authentification multifacteur Microsoft Entra et qu’ils essaient d’utiliser des applications hors navigateur, ils ne peuvent pas s’authentifier. Un mot de passe d’application permet aux utilisateurs de continuer à s’authentifier.

### Surveillance de l’adoption

Microsoft Entra ID propose une vue**Utilisation & Insights** dans la section **Supervision** où vous pouvez surveiller l’activité des méthodes d’authentification. À partir de là, vous pouvez voir l’adoption de MFA et SSPR :

En plus des chiffres d’inscription d’ensemble, vous pouvez voir si les inscriptions ont réussi ou échoué par méthode d’authentification. Cet état de fait vous permet de comprendre les méthodes d’authentification que vos utilisateurs ont le plus inscrites et celles qui sont les plus faciles à inscrire. Ces données sont calculées sur la base des 30 derniers jours des journaux d’audit des expériences d’inscription des informations de sécurité et d’inscription SSPR.

Vous pouvez aller plus dans le détail et voir les dernières informations d’audit des inscriptions pour chaque utilisateur en cliquant sur le graphique.

Vous pouvez également en savoir plus sur l’utilisation de SSPR dans votre organisation en consultant l’onglet **Utilisation** de la vue principale, comme montré dans l’image suivante :

### Contrôle des connaissances


## Résumé

Avec l’authentification multifacteur Microsoft Entra, vous pouvez être sûr que, quand des utilisateurs se connectent pour accéder à vos données et systèmes confidentiels, ils sont ceux qu’ils disent qu’ils sont. Microsoft Entra ID vous permet de créer des stratégies pour vous assurer que des applications spécifiques sont protégées, tout en permettant à d’autres systèmes plus ouverts de rester plus faciles à pénétrer. De plus, vous pouvez utiliser d’autres services, tels que Microsoft Entra ID Protection et Azure Smart Lockout, pour protéger intégralement la surface d’exposition de vos identités.

### Pour aller plus loin

Pour en savoir plus sur des sujets que nous avons examinés dans ce module, consultez les liens suivants vers la documentation.

- [Qu’est-ce que Microsoft Entra ID Protection ?](https://learn.microsoft.com/fr-fr/entra/id-protection/overview-identity-protection)
- [Planifier un déploiement d’authentification multifacteur Microsoft Entra](https://learn.microsoft.com/fr-fr/azure/active-directory/authentication/howto-mfa-getstarted)
- [Réinitialiser votre mot de passe professionnel ou scolaire à l’aide des informations de sécurité](https://support.microsoft.com/account-billing/reset-your-work-or-school-password-using-security-info-23dde81f-08bb-4776-ba72-e6b72b9dda9e)


---

# Gérer l’authentification des utilisateurs

_https://learn.microsoft.com/fr-fr/training/modules/manage-user-authentication/_


## Présentation

L’une des principales fonctionnalités d’une plateforme d’identités consiste à vérifier, ou authentifier, les informations d’identification quand l’utilisateur se connecte à un appareil, à une application ou à un service. Dans Microsoft Entra ID, l'authentification ne se limite pas à la vérification d'un nom d'utilisateur et d'un mot de passe. Pour améliorer la sécurité et réduire le recours à l’assistance du support technique, l’authentification Microsoft Entra comprend les composants suivants :

- Réinitialisation du mot de passe en libre-service
- Authentification multifacteur
- Intégration hybride pour répercuter les changements de mot de passe vers l’environnement local
- Intégration hybride afin d’appliquer des stratégies de protection par mot de passe pour un environnement local
- Authentification sans mot de passe
- Authentification sur des machines virtuelles

Ce module examine ces composants et explique comment planifier, mettre en œuvre et gérer l'authentification utilisateur dans Microsoft Entra ID.

### Objectifs d’apprentissage

Dans ce module, vous allez :

- Administrer les méthodes d’authentification (FIDO2/sans mot de passe).
- Implémenter une solution d’authentification basée sur Windows Hello Entreprise.
- Configurer et déployer la réinitialisation du mot de passe en libre-service.
- Déployez et gérez la protection par mot de passe et les verrouillages intelligents.
- Implémentez l’authentification Kerberos et basée sur un certificat.
- Configurer l'authentification utilisateur Microsoft Entra pour les machines virtuelles.


## Administrer les méthodes d’authentification FIDO2 et sans mot de passe

Dans le cadre de l'expérience de connexion pour les comptes dans Microsoft Entra ID, les utilisateurs peuvent vérifier leur identité de plusieurs manières. Par le passé, un nom d’utilisateur et un mot de passe étaient les moyens les plus courants pour qu’un utilisateur fournisse des informations d’identification. Grâce aux fonctionnalités d'authentification et de sécurité modernes de Microsoft Entra ID, ce mot de passe de base peut être complété ou remplacé par des méthodes d'authentification plus sécurisées.

Les méthodes d’authentification sans mot de passe telles que Windows Hello, les clés de sécurité FIDO2 et l’application Microsoft Authenticator permettent les événements de connexion les plus sécurisés.

L'authentification multifacteur renforce la sécurité par rapport à l'utilisation d'un simple mot de passe lors de la connexion. L’utilisateur peut être invité à fournir d’autres formes d’authentification. L’utilisateur peut être amené à répondre à une notification Push, ou entrer un code issu d’un jeton logiciel ou matériel. Enfin, l’utilisateur devra peut-être répondre à un appel téléphonique ou à un SMS.

Simplifiez l’expérience d’intégration de l’utilisateur en vous inscrivant à la fois pour l’authentification MFA et pour la réinitialisation de mot de passe en libre-service (SSPR). Microsoft vous recommande d’activer l’enregistrement des informations de sécurité combinées. Pour la résilience, nous vous recommandons de demander aux utilisateurs de s’inscrire à plusieurs méthodes d’authentification. Lorsqu’une méthode n’est pas disponible pour un utilisateur lors d’une connexion ou SSPR, il peut choisir de s’authentifier avec une autre méthode.

#### Robustesse et sécurité des méthodes d’authentification

Lorsque vous déployez des caractéristiques comme l'authentification multifacteur dans votre organisation, révisez les méthodes d'authentification disponibles. Optez pour des méthodes qui remplissent ou dépassent vos exigences en termes de sécurité, de facilité d’utilisation et de disponibilité. Dans la mesure du possible, utilisez des méthodes d’authentification avec le niveau de sécurité le plus élevé.

Le tableau suivant décrit les considérations relatives à la sécurité pour les méthodes d’authentification disponibles. La disponibilité indique que l’utilisateur est en mesure d’utiliser la méthode d’authentification, et ne se réfère pas à la disponibilité du service dans Microsoft Entra ID :

![Diagramme d'une grille XY qui montre les inconvénients d'un côté à l'autre et la sécurité faible à la sécurité élevée de haut en bas.](https://learn.microsoft.com../../wwl-sci/manage-user-authentication/media/authentication-method-strength-security.png)

| **Méthode d’authentification** | **Sécurité** | **Usage** | **Disponibilité** |
|---|---|---|---|
| Windows Hello Entreprise | Élevé | Élevé | Élevé |
| L'application Microsoft Authenticator | Élevé | Élevé | Élevé |
| Clé de sécurité FIDO2 | Élevé | Élevé | Élevé |
| Jetons matériels OATH (aperçu) | Moyen | Moyen | Élevé |
| Jetons logiciels OATH | Moyen | Moyen | Élevé |
| SMS | Moyen | Élevé | Moyen |
| Voix | Moyen | Moyen | Moyen |
| Mot de passe | Faible | Élevé | Élevé |

Conseil

Pour plus de flexibilité et de facilité d’utilisation, nous vous recommandons d’utiliser l’application Microsoft Authenticator. Cette méthode d’authentification offre une expérience utilisateur optimale, ainsi que plusieurs modes (authentification sans mot de passe, notifications push MFA et codes OATH, notamment).

#### Fonctionnement de chaque méthode d’authentification

Certaines méthodes d’authentification peuvent être utilisées comme facteur principal lorsque vous vous connectez à une application ou à un appareil. Un bon exemple d’authentification principale est l’utilisation d’une clé de sécurité FIDO2 ou d’un mot de passe. Les autres méthodes d’authentification ne sont disponibles qu’en tant que facteur secondaire. Par exemple, lorsque vous utilisez l'authentification multifacteur ou SSPR.

Le tableau suivant décrit quand une méthode d’authentification peut être utilisée lors d’un événement de connexion :

| **Méthode** | **Authentification principale** | **Authentification secondaire** |
|---|---|---|
| Windows Hello Entreprise | Oui | MFA |
| L'application Microsoft Authenticator | Oui (aperçu) | MFA et SSPR |
| Clé de sécurité FIDO2 | Oui | MFA |
| Jetons matériels OATH (aperçu) | Non | MFA et SSPR |
| Jetons logiciels OATH | Non | MFA et SSPR |
| SMS | Oui (aperçu) | MFA et SSPR |
| Appel vocal | Non | MFA et SSPR |
| Mot de passe | Oui |   |

Toutes ces méthodes d’authentification peuvent être configurées dans le portail Azure, et de plus en plus à l’aide des API REST Microsoft Graph bêta.

Remarque

Dans Microsoft Entra ID, un mot de passe constitue souvent l’une des méthodes d’authentification principales. Vous ne pouvez pas désactiver la méthode d’authentification par mot de passe. Si vous utilisez un mot de passe comme facteur d'authentification principal, renforcez la sécurité des événements de connexion à l'aide de l'authentification multifacteur.

Les méthodes de vérification suivantes peuvent être utilisées dans certains scénarios :

- Mots de passe d'application – Utilisés pour les anciennes applications qui ne prennent pas en charge l'authentification moderne et peuvent être configurés pour l'authentification multifacteur par utilisateur.
- Questions de sécurité : utilisées uniquement pour SSPR.
- Adresse e-mail : utilisée uniquement pour SSPR.

### Qu’est-ce que FIDO2

L’Alliance FIDO (Fast Identity Online) permet de promouvoir les spécifications d’authentification ouvertes et de réduire l’utilisation de mots de passe comme forme d’authentification. FIDO2 est la dernière spécification incorporant la spécification d’authentification web (WebAuthn). Les utilisateurs peuvent enregistrer, puis sélectionner une clé de sécurité FIDO2 dans l’interface de connexion en tant que principal moyen d’authentification. Ces clés de sécurité FIDO2 sont généralement des périphériques USB, mais elles peuvent également utiliser le Bluetooth ou le NFC. Avec un périphérique matériel gérant l’authentification, la sécurité d’un compte augmente car il n’existe aucun mot de passe qui pourrait être exposé ou deviné. Les clés de sécurité FIDO2 peuvent être utilisées pour accéder à leurs appareils Microsoft Entra ID ou Microsoft Entra hybrides connectés à Windows 10 ou 11 et obtenir une signature unique pour leurs ressources cloud et locales. Les utilisateurs peuvent également se connecter aux navigateurs pris en charge. Les clés de sécurité FIDO2 constituent une excellente solution pour les entreprises qui sont très sensibles à la sécurité ou ayant des scénarios ou des employés qui ne sont pas prêts à ou capables d’utiliser leur téléphone comme deuxième facteur.

- Les clés de sécurité FIDO2 sont une méthode d’authentification sans mot de passe basée sur une spécification impossible à hameçonner. Elles peuvent exister sous n’importe quel format.
- Fast Identity Online (FIDO) est une spécification ouverte pour l’authentification sans mot de passe
- FIDO permet aux utilisateurs et aux organisations de tirer profit de la spécification pour se connecter à leurs ressources sans nom d’utilisateur ni mot de passe, à l’aide d’une clé de sécurité externe ou d’une clé de plateforme intégrée à un appareil

### Activer la méthode de clé de sécurité FIDO2

1. Connectez-vous au Centre d'administration Microsoft Entra.
2. Accédez à **Protection** - **Méthodes d’authentification** - **Stratégie de méthode d'authentification**.
3. Sous la méthode **Clé de sécurité FIDO2**, choisissez les options suivantes :
  - **Activer** - Oui ou Non
  - **Cible** - Tous les utilisateurs ou les utilisateurs sélectionnés

4. **Enregistrez** la configuration.

#### Gérer l’inscription des utilisateurs et les clés de sécurité FIDO2

1. Accédez à **[https://myprofile.microsoft.com](https://myprofile.microsoft.com)**.
2. Connectez-vous si vous ne l’avez pas déjà fait.
3. Sélectionnez **Informations de sécurité**.
4. Si l'utilisateur a déjà enregistré au moins une méthode d'authentification multifacteur, il peut immédiatement enregistrer une clé de sécurité FIDO2.
5. S’ils n’ont pas au moins une méthode d’authentification multifacteur inscrite, ils doivent en ajouter un.
6. Ajoutez une clé de sécurité FIDO2 en sélectionnant **Ajouter une méthode** et en choisissant **Clé de sécurité**.
7. Choisissez **Périphérique USB** ou **Appareil NFC**.
8. Préparez votre clé et choisissez **Suivant**.
9. Une boîte apparaîtra et demandera à l'utilisateur de créer/saisir un code PIN pour votre clé de sécurité, puis d'effectuer le geste requis pour la clé, soit biométrique, soit tactile.
10. L’utilisateur revient à l’expérience d’inscription combinée et est invité à fournir un nom explicite pour la clé, afin de pouvoir l’identifier s’il en possède plusieurs. Sélectionnez **Suivant**.
11. Sélectionnez **Terminé** pour terminer la procédure.

#### Connectez-vous avec des informations d'identification sans mot de passe

Dans l’exemple ci-dessous, un utilisateur a déjà approvisionné sa clé de sécurité FIDO2. L’utilisateur peut choisir de se connecter sur le web avec sa clé de sécurité FIDO2 dans un navigateur pris en charge par Windows 10 version 1903 ou ultérieure, ou Windows 11.

### Configuration requise pour le déploiement cloud uniquement

- Windows 10 version 1511 ou ultérieure, ou Windows 11
- Compte Microsoft Azure
- Microsoft Entra ID
- Authentification multifacteur
- Gestion moderne - *en option,* Microsoft Intune ou gestion des appareils mobiles (MDM) tierce prise en charge
- Abonnement Microsoft Entra ID Premium - *facultatif*, nécessaire pour l'inscription automatique MDM lorsque l'appareil rejoint Microsoft Entra ID


## Explorer l’application Authenticator et les jetons OATH

L'application Microsoft Entra Authenticator fournit un niveau de sécurité supplémentaire pour votre compte Microsoft Entra ID professionnel ou scolaire, ou pour votre compte Microsoft. Elle est disponible pour Android et iOS. Avec l’application Microsoft Authenticator, les utilisateurs peuvent s’authentifier sans mot de passe lors de la connexion, ou comme option de vérification supplémentaire lors de la réinitialisation de mot de passe en libre-service ou d’événements d’authentification multifacteur.

Les utilisateurs peuvent recevoir une notification par le biais de l'application mobile leur permettant d'accepter ou de refuser. Ils peuvent également utiliser l'application Authenticator pour générer un code de vérification OATH pouvant être saisi dans une interface de connexion. Si vous activez à la fois la notification et le code de vérification, les utilisateurs s’enregistrant sur l’application Authenticator peuvent utiliser une des deux méthodes pour vérifier leur identité.

### Application Microsoft Authenticator

L’application Authenticator offre un niveau élevé de sécurité et évite à l’utilisateur de devoir fournir un mot de passe lors de la connexion. L’application Authenticator peut aider à empêcher tout accès non autorisé aux comptes et à arrêter les transactions frauduleuses. Une notification Push est envoyée à votre smartphone ou tablette pour une sécurité supplémentaire. Les utilisateurs voient la notification et, si elle est légitime, sélectionnent Vérifier. Sinon, ils peuvent sélectionner Refuser.

L'application Authenticator peut être utilisée comme jeton logiciel pour générer un code de vérification OATH. Après avoir saisi votre nom d’utilisateur et votre mot de passe, vous entrez le code fourni par l’application Authenticator dans l’interface de connexion. Le code de vérification fournit un deuxième formulaire d’authentification. Les utilisateurs peuvent combiner jusqu'à cinq jetons matériels OATH ou des applications d'authentification, comme l'application Authenticator, configurées pour une utilisation à tout moment.

### Ouvrir des jetons d’authentification (OATH)

Les mots de passe à usage unique et durée définie (TOTP) OATH forment une norme ouverte qui spécifie le mode de génération des codes de mot de passe (OTP) à usage unique. Les mots de passe à usage unique et durée définie OATH peuvent être implémentés à l’aide de logiciels ou de matériels permettant de générer des codes. L’identifiant Microsoft Entra ne prend pas en charge les HOTP OATH, une norme de génération de code différente. Les jetons logiciels OATH sont généralement des applications telles que l’application Microsoft Authenticator et d’autres applications d’authentification. Microsoft Entra ID génère la clé secrète, ou la valeur de départ, qui est entrée dans l’application et utilisée pour générer chaque code OTP.

L’application Authenticator génère automatiquement des codes lorsqu’elle est configurée pour effectuer des notifications push, afin que l’utilisateur dispose d’une sauvegarde, même si son appareil n’a pas de connectivité. Les applications tierces qui utilisent les TOTP OATH pour générer des codes peuvent également être utilisées.


## Implémenter une solution d’authentification basée sur Windows Hello Entreprise

Dans Windows 10, Windows Hello Entreprise remplace les mots de passe par une authentification à deux facteurs forte sur les PC et appareils mobiles. Cette authentification se compose d’un nouveau type d’informations d’identification utilisateur qui sont liées à un appareil et utilise un code biométriques ou un code PIN. Windows Hello Entreprise permet aux utilisateurs de s’authentifier auprès d’un compte Active Directory ou Microsoft Entra.

Windows Hello résout les problèmes de mot de passe suivants :

- Les mots de passe forts peuvent être difficiles à mémoriser et les utilisateurs réutilisent souvent les mots de passe sur plusieurs sites.
- Les violations de serveur peuvent exposer des informations d’identification réseau symétriques (mots de passe).
- Les mots de passe sont soumis à des attaques par relecture.
- Les utilisateurs peuvent exposer par inadvertance leur mot de passe en raison des attaques par hameçonnage.

![Diagramme du flux de processus pour le fonctionnement de l’authentification dans Windows Hello.](https://learn.microsoft.com../../wwl-sci/manage-user-authentication/media/authentication-flow.png)

### Fonctionnement de Windows Hello Entreprise : Points clés

- Les informations d’identification Windows Hello sont basées sur un certificat ou une paire de clés asymétrique. Les informations d’identification Windows Hello peuvent être liées à l’appareil, et le jeton obtenu à l’aide des informations d’identification est également lié à l’appareil.
- Le fournisseur d'identité (par exemple, Active Directory, Microsoft Entra ID ou un compte Microsoft) valide l'identité de l'utilisateur et mappe la clé publique Windows Hello à un compte d'utilisateur lors de l'étape d'inscription.
- Les clés peuvent être générées au format matériel (TPM 1.2 ou 2.0 pour les entreprises et TPM 2.0 pour les consommateurs) ou logiciel, selon la stratégie appliquée.
- L’authentification à deux facteurs est la combinaison d'une clé ou d'un certificat associé à un appareil. à quelque chose que l’utilisateur seul connaît (un code confidentiel) ou à quelque chose qui caractérise l’utilisateur (biométrie). Le mouvement Windows Hello est propre à chaque appareil et n’est pas partagé avec le serveur. Les modèles biométriques sont stockés localement sur un appareil. Le PIN n’est jamais stocké ou partagé.
- La clé privée ne quitte jamais un appareil lors de l’utilisation du module TPM. Le serveur d’authentification dispose d’une clé publique mappée au compte d’utilisateur lors de la procédure d’inscription.
- Les entrées de code PIN et les gestes biométriques déclenchent l’utilisation par Windows 10 de la clé privée pour signer par chiffrement les données envoyées au fournisseur d’identité. Le fournisseur d’identité vérifie l’identité de l’utilisateur et authentifie l’utilisateur.
- Les comptes personnels (comptes Microsoft) et d’entreprise (Active Directory ou Microsoft Entra ID) utilisent un conteneur unique pour les clés. Toutes les clés sont séparées par les domaines des fournisseurs d’identité pour assurer la confidentialité des utilisateurs.
- Les clés de certificat privées peuvent être protégées par le conteneur Windows Hello et le mouvement Windows Hello.

### Création de groupes de sécurité

Windows Hello Entreprise utilise plusieurs groupes de sécurité pour simplifier le déploiement et la gestion.

Important

Si votre environnement comporte un ou plusieurs contrôleurs de domaine Windows Server 2016 dans le domaine sur lequel vous déployez Windows Hello entreprise, ignorez le groupe de sécurité Create the KeyCredentials Admins. Les domaines qui incluent des contrôleurs de domaine Windows Server 2016 utilisent le groupe KeyAdmins, qui est créé lors de l’installation du premier contrôleur de domaine Windows Server 2016.

#### Créer le groupe de sécurité KeyCredential Admins

Microsoft Entra Connect synchronise la clé publique sur l’objet utilisateur créé lors de l’approvisionnement. Vous attribuez des autorisations d’écriture et de lecture à ce groupe pour l’attribut Active Directory. Cela garantit que le service Microsoft Entra Connect peut ajouter et supprimer des clés dans le cadre de son workflow habituel.

1. Connectez-vous à un contrôleur de domaine ou à un poste de travail de gestion avec des identifiants équivalents à celui d’un *administrateur de domaine*.
2. Ouvrez **Utilisateurs et ordinateurs Active Directory**.
3. Sélectionnez **Affichage** puis **Fonctionnalités avancées**.
4. Développez le nœud de domaine dans le volet de navigation.
5. Cliquez avec le bouton droit sur le conteneur **Utilisateurs**. Sélectionnez **Nouveau**. Sélectionnez **Groupe**.
6. Tapez **Keycredential Admins** dans la zone de texte **Nom du groupe** .
7. Sélectionnez **OK**.

#### Créer le groupe de sécurité des Utilisateurs de Windows Hello pour Entreprise

Le groupe Utilisateurs de Windows Hello Entreprise est utilisé pour faciliter le déploiement de Windows Hello Entreprise en plusieurs phases. Vous attribuez des autorisations de stratégie de groupe et de modèle de certificat à ce groupe pour simplifier le déploiement en ajoutant les utilisateurs au groupe. Cela fournit aux utilisateurs les autorisations appropriées pour configurer Windows Hello Entreprise et s’inscrire au certificat d’authentification Windows Hello Entreprise.

1. Connectez-vous à un contrôleur de domaine ou à un poste de travail de gestion avec des identifiants équivalents à celui d’un *administrateur de domaine*.
2. Ouvrez **Utilisateurs et ordinateurs Active Directory**.
3. Sélectionnez **Affichage** puis **Fonctionnalités avancées**.
4. Développez le nœud de domaine dans le volet de navigation.
5. Cliquez avec le bouton droit sur le conteneur **Utilisateurs**. Sélectionnez **Nouveau**. Sélectionnez **Groupe**.
6. Saisissez **Utilisateurs Windows Hello Entreprise** dans la zone de texte **Nom du groupe**.
7. Sélectionnez **OK**.

### Processeur de sécurité Microsoft Pluton

![Diagramme de la nouvelle puce CPU Microsoft Pluton sur la carte mère en regard des puces CPU et TPM.](https://learn.microsoft.com../../wwl-sci/manage-user-authentication/media/pluton.png)

Aujourd’hui, le cœur de la sécurité du système d’exploitation réside, sur la plupart des PC, dans une puce distincte du processeur, appelée « module de plateforme sécurisée » (TPM). Le TPM est un composant matériel permettant de stocker de façon sécurisée les clés et les mesures qui vérifient l’intégrité du système. Les TPM sont pris en charge dans Windows depuis plus de dix ans et alimentent de nombreuses technologies critiques, telles que Windows Hello et BitLocker. L’efficacité du TPM à exécuter des tâches de sécurité critiques a poussé les attaquants à innover. Ceci est très courant dans le cas d’une personne malveillante qui vole des données ou obtient temporairement un accès physique à un PC. Ces techniques d’attaque sophistiquées ciblent le canal de communication entre l’UC et le TPM, qui est généralement une interface de bus. Cette interface bus permet au processeur principal et au processeur de sécurité de partager des informations. Elle permet également aux attaquants de voler ou de modifier les informations en transit à l’aide d’une attaque physique.

La conception de Pluton supprime le potentiel d'attaque de ce canal de communication en intégrant la sécurité directement dans le processeur. Les PC Windows qui utilisent l’architecture Pluton émuleront d’abord un module TPM. Cette émulation fonctionne avec les spécifications TPM et les API existantes. Enfin, cela permettra aux clients de bénéficier immédiatement de la sécurité améliorée pour les fonctionnalités Windows qui reposent sur le module TPM. C’est le cas, par exemple, de BitLocker et de System Guard. Les appareils Windows avec Pluton utilisent le processeur de sécurité Pluton pour protéger les informations d’identification, les identités des utilisateurs, les clés de chiffrement et les données personnelles. Aucune de ces informations ne peut être supprimée de Pluton, même si un attaquant a installé un logiciel malveillant ou a une possession physique complète du PC.

- Construit en collaboration avec AMD, Intel, Qualcomm et d'autres.
- Clé cryptographique matérielle de sécurité (SHACK).
- Mise à jour/remplacement de la puce du TPM, que les pirates apprennent à pirater.
- Basé sur la technologie novatrice dans Azure Sphere et la sécurité Xbox.


## Excercice de configuration et de déploiement de la réinitialisation du mot de passe en libre-service

La réinitialisation de mot de passe en libre-service (SSPR) de Microsoft Entra permet aux utilisateurs de modifier ou de réinitialiser leur mot de passe, sans intervention d'un administrateur ou d'un service d'assistance. Si le compte d’un utilisateur est verrouillé ou si ce dernier oublie son mot de passe, il peut suivre des invites afin de se débloquer et de reprendre son travail. Cette fonctionnalité réduit les appels au support technique et la perte de productivité quand l’utilisateur ne parvient pas à se connecter à son appareil ou à une application.

### Avantages de la réinitialisation de mot de passe en libre-service

L’utilisateur et l’organisation profitent de nombreux avantages en activant la réinitialisation de mot de passe en libre-service :

- Les utilisateurs peuvent réinitialiser leur propre mot de passe, sans perte de productivité
- Aucune intervention de l’administrateur ou du service informatique : cela permet au service informatique de se concentrer sur de plus gros problèmes

Licences requises :

- Comptes basés sur le cloud – Un utilisateur doit être inscrit à la réinitialisation de mot de passe en libre-service et disposer d'une licence Microsoft Entra ID Premium P1 ou P2, ou d'une licence Microsoft 365 Business standard est requise.
- Comptes locaux – Un utilisateur doit être inscrit à la réinitialisation de mot de passe en libre-service et disposer d'une licence Microsoft Entra ID Premium P1 ou P2, ou d'une licence Microsoft 365 Business Premium.

### Activer la réinitialisation du mot de passe en libre-service

Étapes de base permettant d’activer la réinitialisation du mot de passe en libre-service :

1. Connectez-vous au portail Azure à l’aide d’un compte disposant d’autorisations d’administrateur général.
2. Recherchez et sélectionnez Microsoft Entra ID, puis sélectionnez Réinitialisation de mot de passe dans le menu de gauche.
3. Dans la page Propriétés, sous l’option Réinitialisation du mot de passe en libre-service, sélectionnez Sélectionner un groupe
4. Recherchez et sélectionnez votre groupe Microsoft Entra, comme SSPR-Test-Group, puis choisissez Sélectionner.
5. Afin d’activer SSPR pour le groupe choisi, sélectionnez Enregistrer.

### Ajouter un nouvel utilisateur

Créer un compte d’utilisateur qui sera ajouté à un groupe de sécurité.

1. Dans l'organisation Microsoft Entra que vous avez créée, sous **Gérer**, sélectionnez **Utilisateurs**, puis **Nouvel utilisateur**.
2. Le volet Utilisateur s’affiche. Saisissez les valeurs suivantes :
  - Nom d’utilisateur : MonicaT
  - Nom : Monica Thompson

3. Sélectionnez **Afficher le mot de passe** , puis copiez-le quelque part pour référence ultérieure.
4. Sélectionnez **Create** (Créer).

### Créer un groupe

Vous voulez d’abord déployer SSPR sur un ensemble limité d’utilisateurs pour vérifier que votre configuration SSPR fonctionne comme prévu. Nous allons créer un groupe de sécurité pour le déploiement limité et ajouter un utilisateur au groupe.

1. Connectez-vous au [centre d’administration Microsoft Entra](https://entra.microsoft.com/) avec un compte administrateur général.
2. Ouvrez le menu du portail, puis sélectionnez **Identité**.
3. Dans le menu Identité, sélectionnez **Groupes**, puis **+ Nouveau groupe**.
4. Créez un nouveau groupe à l’aide des informations suivantes :    **Paramètre** **Valeur**     Type de groupe Sécurité   Nom du groupe SSPRTesters   Description du groupe Testeurs du déploiement de SSPR   Type d’appartenance Attribué   Membres Monica Thompson
5. Sélectionnez **Créer.**

### Activer la réinitialisation du mot de passe en libre-service

Activez SSPR pour le groupe.

1. Revenez à l'écran du Centre d'administration Microsoft Entra.
2. Sous **Protection**, sélectionnez **Réinitialisation de mot de passe**.  Important Si la page de réinitialisation du mot de passe affiche toujours le message Obtenir une version d’évaluation Premium gratuite pour utiliser cette fonctionnalité, attendez quelques minutes, puis actualisez la page.
3. Dans la boîte de dialogue Réinitialisation du mot de passe de la page **Propriétés**, sous **Réinitialisation du mot de passe en libre-service activée**, sélectionnez **Sélectionné**.
4. Sélectionnez **Sélectionner un groupe**.
5. Dans le volet Stratégie de réinitialisation de mot de passe par défaut, sélectionnez le groupe **SSPRTesters** .
6. Dans la boîte de dialogue Réinitialisation du mot de passe de la page **Propriétés**, sélectionnez **Enregistrer**.
7. Sous **Gérer**, sélectionnez et passez en revue les valeurs par défaut pour les paramètres **Méthodes d’authentification**, **Inscription**, **Notifications**et **Personnalisation** .

### S’inscrire à la réinitialisation de mot de passe en libre-service

Maintenant que la configuration SSPR est terminée, inscrivez un numéro de téléphone mobile pour l’utilisateur que vous avez créé.

1. Ouvrez un autre navigateur ou ouvrez une session de navigateur InPrivate ou Incognito, puis accédez à [https://aka.ms/ssprsetup](https://aka.ms/ssprsetup). Cela permet de s’assurer que vous serez invité à vous authentifier comme utilisateur.
2. Connectez-vous en tant que `MonicaT@organization-domain-name.onmicrosoft.com` avec le mot de passe que vous avez noté précédemment. Remplacez nom de domaine de l’organisation par votre nom de domaine.
3. Lorsque vous êtes invité à mettre à jour votre mot de passe, entrez un nouveau mot de passe de votre choix. Veillez à enregistrer le nouveau mot de passe.
4. Dans la boîte de dialogue **Informations supplémentaires requises** , sélectionnez **Suivant**.
5. Dans la page Protéger votre compte, activez l’option **Téléphone** ou sélectionnez le lien **Je veux configurer une autre méthode**.
6. Dans cet exemple, vous allez utiliser l’option Téléphone. Entrez les détails de votre téléphone mobile.
7. Sélectionnez **M’envoyer un code par SMS**.
8. Quand vous recevez le code sur votre téléphone mobile, entrez-le dans la zone de texte.
9. Une fois votre téléphone inscrit, sélectionnez Suivant, puis sélectionnez Terminé.
10. Fermez le navigateur. Vous n’avez pas besoin d’aller jusqu’au bout du processus de connexion.

### Tester la réinitialisation de mot de passe en libre-service

Vérifions maintenant si l’utilisateur peut réinitialiser son mot de passe.

1. Ouvrez un autre navigateur ou ouvrez une session de navigateur InPrivate ou Incognito, puis accédez à [https://aka.ms/sspr](https://aka.ms/sspr). Cela permet de s’assurer que vous serez invité à vous authentifier comme utilisateur.
2. Dans la zone **E-mail, téléphone ou Skype**, entrez `MonicaT@organization-domain-name.onmicrosoft.com`, puis sélectionnez Suivant. Remplacez nom de domaine de l’organisation par votre nom de domaine.
3. Dans l’écran Saisie du mot de passe, sélectionnez **Mot de passe oublié**.
4. Dans la page Récupérer dans votre compte, renseignez les informations demandées, puis sélectionnez **Suivant**.
5. Dans la tâche **Étape de vérification 1** , sélectionnez **envoyer un SMS à mon téléphone mobile** ou **Appeler mon téléphone mobile**, entrez votre numéro de téléphone, puis sélectionnez **Texte**.
6. Entrez votre code de vérification, puis sélectionnez **Suivant**.
7. À l’étape Choisir un nouveau mot de passe, entrez un mot de passe et confirmez votre nouveau mot de passe.
8. Lorsque vous avez terminé, sélectionnez **Terminer**.
9. Connectez-vous en tant que **Monica** avec le mot de passe que vous avez créé.
10. Entrez votre code de vérification, puis vérifiez que vous pouvez terminer le processus de connexion.
11. Lorsque vous avez terminé, fermez votre navigateur.


## Déployer et gérer la protection par mot de passe

Les utilisateurs créent souvent des mots de passe basés sur des mots locaux courants, par exemple une école, une équipe de sport ou une personne célèbre. Ces mots de passe sont faciles à deviner et offrent une faible protection contre les attaques par dictionnaire. Pour appliquer des mots de passe forts au sein de votre organisation, la protection par mot de passe Microsoft Entra fournit une liste globale et personnalisée de mots de passe interdits. Toute demande de changement de mot de passe échoue si le mot de passe correspond à une entrée de la liste personnalisée de mots de passe interdits.

La protection par mot de passe Microsoft Entra est conçue dans le respect des principes suivants :

- Les contrôleurs de domaine ne doivent jamais communiquer directement avec Internet.
- Aucun nouveau port réseau n’est ouvert sur les contrôleurs de domaine.
- Aucune modification du schéma AD DS n’est requise. Le logiciel utilise le conteneur AD DS et les objets de schéma serviceConnectionPoint existants.
- Aucun niveau fonctionnel minimal du domaine ou de la forêt AD DS (DFL/FFL) n’est requis.
- Le logiciel ne crée pas de compte ni n’en exige dans les domaines AD DS qu’il protège.
- Les mots de passe utilisateur en texte clair ne quittent jamais le contrôleur de domaine, que ce soit pendant les opérations de validation de mot de passe ou à tout autre moment.
- Le logiciel n’est pas dépendant d’autres fonctionnalités de Microsoft Entra. Par exemple, la synchronisation du hachage du mot de passe (PHS) de Microsoft Entra n’est ni liée à Microsoft Entra Password Protection ni requise pour cette fonctionnalité.
- Le déploiement incrémentiel est pris en charge, sous réserve que la stratégie de mot de passe soit appliquée uniquement à l’endroit où l’agent du contrôleur de domaine est installé.

### Créer un compte Azure et ajouter des licences d'essai Microsoft Entra ID Premium P2

Les tâches de cet exercice et les exercices de ce parcours d'apprentissage exigent que vous disposiez déjà d'un abonnement Azure que vous pouvez utiliser ou que vous vous inscriviez à un compte d'essai Azure. Si vous disposez déjà de votre propre abonnement Azure, vous pouvez ignorer cette tâche et passer à la suivante.

1. Dans un navigateur web, accédez au [portail Azure](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
2. Faites défiler la page pour découvrir tous les avantages et les services gratuits disponibles.
3. Sélectionnez **Démarrer gratuitement**.
4. Utilisez l’assistant pour vous inscrire à l’offre d’essai Azure.
5. Vous avez besoin d'une licence Microsoft Entra P2 pour effectuer certains exercices. Dans l'organisation que vous avez créée, recherchez et sélectionnez **Microsoft Entra ID**.
6. Dans le menu de navigation gauche, sélectionnez **Prise en main**.
7. Sous Bien démarrer avec Microsoft Entra, sélectionnez **Obtenir un essai gratuit pour Microsoft Entra Premium**.
8. Dans le volet Activer, sous **Microsoft Entra Premium P2**, sélectionnez **Essai gratuit**, puis **Activer**.
9. Dans le menu de navigation, sélectionnez **Vue d’ensemble**.
10. Actualisez le navigateur jusqu'à ce que Microsoft Entra Premium P2 s'affiche sous le nom de l'organisation. Cela peut prendre quelques minutes.
11. Il se peut que vous deviez vous déconnecter et vous reconnecter à Microsoft Azure si vous rencontrez des problèmes avec les fonctionnalités attendues qui ne sont pas disponibles.

### Comment fonctionne la protection par mot de passe Microsoft Entra

Les composants locaux de la protection par mots de passe Microsoft Entra fonctionnent comme suit :

1. Chaque instance du service proxy Microsoft Entra Password Protection se signale auprès des contrôleurs de domaine de la forêt en créant un objet *serviceConnectionPoint* dans Active Directory.
2. Chaque service de l’agent du contrôleur de domaine pour la protection par mot de passe Microsoft Entra crée également un objet *serviceConnectionPoint* dans Active Directory. Cet objet est principalement utilisé pour la création de rapports et les diagnostics.
3. Le service de l’agent du contrôleur de domaine est chargé d’initier le téléchargement d’une nouvelle stratégie de mot de passe à partir de Microsoft Entra. La première étape consiste à localiser un service proxy de protection par mot de passe Microsoft Entra en recherchant dans la forêt des objets *serviceConnectionPoint* du proxy.
4. Quand un service proxy disponible est trouvé, l’agent du contrôleur de domaine envoie une demande de téléchargement de stratégie de mot de passe à ce service proxy. Le service proxy envoie à son tour la requête à Microsoft Entra, puis renvoie la réponse au service DC Agent.
5. Une fois que le service DC Agent a reçu une nouvelle stratégie de mot de passe de Microsoft Entra, il stocke la stratégie dans un dossier dédié à la racine du partage du dossier *sysvol* de son domaine. Le service DC Agent surveille également ce dossier afin de détecter si des stratégies plus récentes y sont répliquées depuis d’autres services DC Agent du domaine.
6. Le service DC Agent demande toujours une nouvelle stratégie au démarrage du service. Après démarrage, le service de l’agent du contrôleur de domaine vérifie toutes les heures l’âge de la stratégie en vigueur disponible localement. Si la stratégie a plus d’une heure, l’agent du contrôleur de domaine demande à Microsoft Entra une nouvelle stratégie via le service proxy, comme décrit précédemment. Si la stratégie actuelle date de moins d’une heure, l’agent DC continue d’utiliser cette stratégie.
7. Lorsque des événements de modification de mot de passe sont reçus par un contrôleur de domaine, la stratégie mise en cache est utilisée pour déterminer si le nouveau mot de passe est accepté ou rejeté.

Pour protéger votre environnement services de domaine Active Directory (AD DS) local, vous pouvez installer et configurer la protection par mot de passe Microsoft Entra pour qu’elle fonctionne avec votre contrôleur de domaine local. Cette unité explique comment installer et inscrire le service proxy de protection par mot de passe Microsoft Entra et l’agent du contrôleur de domaine de protection par mot de passe Microsoft Entra dans votre environnement local.

### Stratégie de déploiement

Le diagramme suivant montre comment les composants de base de la protection par mot de passe Microsoft Entra opèrent ensemble dans un environnement Active Directory local :

![Diagramme montrant comment les composants Protection par mot de passe de Microsoft Entra fonctionnent de concert.](https://learn.microsoft.com../../wwl-sci/manage-user-authentication/media/azure-active-directory-password-protection.png)

Nous vous recommandons de commencer les déploiements en mode *audit*. Le mode audit est la configuration initiale par défaut où il est possible de continuer à définir des mots de passe. Les mots de passe qui seraient bloqués sont enregistrés dans le journal des événements. Après avoir déployé les serveurs proxy et les agents du contrôleur de domaine en mode audit, supervisez l’impact qu’aura la stratégie de mot de passe sur les utilisateurs lors de l’application de la stratégie.

Au cours de l’étape d’audit, de nombreuses organisations découvrent les situations suivantes :

- Elles doivent améliorer les processus opérationnels existants pour utiliser des mots de passe plus sécurisés.
- Les utilisateurs utilisent souvent des mots de passe non sécurisés.
- Elles doivent informer les utilisateurs des modifications de sécurisation à venir et de la façon de choisir des mots de passe plus sécurisés.

Il est également possible que la validation de mot de passe plus fort affecte l’automatisation de votre déploiement de contrôleur de domaine Active Directory existant. Nous vous recommandons d’effectuer au moins une promotion et une régression de contrôleur de domaine au cours de l’évaluation de la période d’audit afin de faciliter la détection de problèmes tels que les mots de passe faible qui empêchent la promotion et la régression.

Une fois que la fonctionnalité a été exécutée en mode audit pendant une période raisonnable, vous pouvez basculer la configuration de *Audit* à *Appliquer* pour exiger des mots de passe plus sécurisés. Durant cette période, il est recommandé d’exercer une surveillance supplémentaire.

Important

La protection par mot de passe Microsoft Entra peut uniquement valider les mots de passe pendant les opérations de changement ou de définition de mot de passe. Les mots de passe qui ont été acceptés et stockés dans Active Directory avant le déploiement de la protection par mot de passe Microsoft Entra ne sont jamais validés et continuent de fonctionner en l’état. Au fil du temps, tous les utilisateurs et comptes finissent par utiliser des mots de passe validés par la protection par mot de passe Microsoft Entra à mesure que les mots de passe existants arrivent à expiration. Les comptes configurés avec l’option « Le mot de passe n’expire jamais » ne sont pas concernés.

#### Considérations relatives aux forêts multiples

Il n’y a aucune exigence supplémentaire pour déployer la protection par mot de passe Microsoft Entra dans plusieurs forêts.

Chaque forêt est configurée indépendamment. Chaque proxy de protection par mot de passe Microsoft Entra ne peut prendre en charge que les contrôleurs de domaine de la forêt à laquelle il est joint.

Le logiciel de protection par mot de passe Microsoft Entra figurant dans une forêt donnée n’a pas connaissance des logiciels de protection par mot de passe déployés dans d’autres forêts, quelles que soient les configurations d’approbation Active Directory.

#### Considérations relatives au contrôleur de domaine en lecture seule

Les événements de modification ou de définition de mot de passe ne sont pas traités ou conservés sur les contrôleurs de domaine en lecture seule (RODC). Au lieu de cela, ils sont transférés vers des contrôleurs de domaine accessibles en écriture. Vous n’êtes pas obligé d’installer le logiciel de l’agent DC de protection par mot de passe Microsoft Entra sur les RODC.

Par ailleurs, il n’est pas possible d’exécuter le service proxy de protection par mot de passe Microsoft Entra sur un contrôleur de domaine en lecture seule.

#### Considérations relatives à la haute disponibilité

La principale préoccupation pour la protection par mot de passe est la disponibilité des serveurs proxy de protection par mot de passe Microsoft Entra lorsque les contrôleurs de domaine dans une forêt essaient de télécharger de nouvelles stratégies ou d’autres données à partir d’Azure. Chaque agent DC Microsoft Entra Password Protection utilise un algorithme simple de type round-robin lorsqu’il détermine quel serveur proxy appeler. L’agent ignore les serveurs proxy qui ne répondent pas.

Pour la plupart des déploiements Active Directory totalement connectés avec réplication saine de l’état de l’annuaire et du dossier sysvol, deux serveurs proxy de protection par mot de passe Microsoft Entra suffisent pour garantir la disponibilité. Cette configuration entraîne un téléchargement en temps voulu des nouvelles stratégies et d’autres données. Si vous le souhaitez, vous pouvez déployer des serveurs proxy de protection par mot de passe Microsoft Entra supplémentaires.

La conception du logiciel de l’agent DC de protection par mot de passe Microsoft Entra atténue les problèmes habituels associés à la haute disponibilité. L’agent DC de protection par mot de passe Microsoft Entra gère un cache local de la stratégie de mot de passe la plus récemment téléchargée. Même si tous les serveurs proxy inscrits deviennent indisponibles, les agents DC de protection par mot de passe Microsoft Entra continuent d’appliquer leur stratégie de mot de passe mis en cache.

Une fréquence de mise à jour raisonnable pour les stratégies de mot de passe dans un déploiement à grande échelle se compte généralement en jours, pas en heures, ni moins. Par conséquent, les pannes brèves des serveurs proxy ne posent pas de problèmes pour la protection par mot de passe Microsoft Entra.

### Conditions requises pour le déploiement

Les licences requises pour la protection des mots de passe Active Directory sont les suivantes :

| **Utilisateurs** | **Protection par mot de passe Microsoft Entra avec une liste générale de mots de passe interdits** | **Protection par mot de passe Microsoft Entra avec une liste personnalisée de mots de passe interdits** |
|---|---|---|
| Utilisateurs du cloud uniquement | Microsoft Entra Gratuit | Microsoft Entra Premium P1 ou P2 |
| Utilisateurs synchronisés à partir d’une instance AD DS locale | Microsoft Entra Premium P1 ou P2 | Microsoft Entra Premium P1 ou P2 |

Les principales exigences suivantes s’appliquent :

- Vous avez besoin d'un compte disposant des privilèges d'administrateur de domaine Active Directory dans le domaine racine de la forêt pour inscrire la forêt Windows Server Active Directory auprès de Microsoft Entra.
- Le service de distribution de clés doit être activé sur tous les contrôleurs de domaine figurant dans le domaine qui exécutent Windows Server 2012. Par défaut, ce service est activé via un déclenchement manuel.
- Une connectivité réseau doit exister entre au moins un contrôleur de domaine dans chaque domaine et au moins un serveur hébergeant le service proxy pour la protection par mot de passe Microsoft Entra. Cette connectivité doit autoriser le contrôleur de domaine à accéder au port 135 du mappeur de point de terminaison RPC et au port du serveur RPC sur le service proxy.
  - Par défaut, le port du serveur RPC est un port RPC dynamique, mais il peut être configuré pour utiliser un port statique.

- Toutes les machines où le service proxy de protection par mot de passe Microsoft Entra est installé doivent avoir un accès réseau aux points de terminaison suivants :

| **Point de terminaison** | **Objectif** |
|---|---|
| `https://login.microsoftonline.com` | Demandes d’authentification |
| `https://enterpriseregistration.windows.net` | Fonctionnalité de protection par mot de passe Microsoft Entra |

#### Agent DC de protection par mot de passe Microsoft Entra

Les conditions suivantes s’appliquent à l’agent DC de protection de mot de passe Microsoft Entra :

- Tous les ordinateurs sur lesquels le logiciel de l’agent DC de protection par mot de passe Microsoft Entra sera installé doivent exécuter Windows Server 2012 R2 ou version ultérieure.
  - Le domaine ou la forêt Active Directory n’a pas besoin d’être au niveau fonctionnel de domaine (DFL) ou au niveau fonctionnel de forêt (FFL) de Windows Server 2012 R2. Aucun niveau fonctionnel de domaine (DFL) ni de forêt (FFL) minimal n’est requis pour le logiciel de l’agent DC ou le logiciel de proxy à exécuter.

- Tous les ordinateurs qui exécutent l’agent dc de protection par mot de passe Microsoft Entra doivent avoir installé .NET 4.7.2.
- Les domaines Active Directory qui exécutent le service de l'agent DC de protection par mot de passe Microsoft Entra doivent utiliser la réplication du système de fichiers distribué (DFSR) pour la réplication sysvol.

#### Service proxy de protection des mots de passe Microsoft Entra

Les exigences suivantes s’appliquent au service proxy de protection par mot de passe Microsoft Entra :

- Toutes les machines où le service proxy de protection par mot de passe Microsoft Entra est installé doivent exécuter Windows Server 2012 R2 ou version ultérieure.  Remarque Le déploiement du service proxy de protection par mot de passe Microsoft Entra est une exigence obligatoire pour le déploiement de la protection par mot de passe Microsoft Entra, même si le contrôleur de domaine peut avoir une connectivité Internet sortante directe.
- Tous les ordinateurs sur lesquels le service proxy de protection par mot de passe Microsoft Entra sera installé doivent avoir .NET 4.7.2 installé.
- Toutes les machines qui hébergent le service proxy de protection par mot de passe Microsoft Entra doivent être configurées pour autoriser les contrôleurs de domaine à se connecter au service proxy. Cette capacité est contrôlée par le biais de l’affectation du privilège « Accéder à cet ordinateur à partir du réseau ».
- Toutes les machines qui hébergent le service proxy de protection par mot de passe Microsoft Entra doivent être configurées pour autoriser le trafic HTTP TLS 1.2 sortant.
- Un compte *d’administrateur général* est requis pour inscrire le service proxy de protection par mot de passe Microsoft Entra pour la première fois dans un locataire donné. Les inscriptions de proxy et de forêt ultérieures peuvent utiliser un compte disposant au minimum du rôle *Administrateur de sécurité*.
- L’accès réseau doit être activé pour l’ensemble des ports et des URL spécifiés dans les procédures de configuration de l’environnement proxy d’application.  Avertissement Le proxy de protection par mot de passe et le proxy d'application Microsoft Entra installent différentes versions du service du programme de mise à jour de l'agent Microsoft Entra Connect. En conséquence, les instructions renvoient au contenu du proxy d'application. Ces différentes versions sont incompatibles lorsqu’elles sont installées côte à côte. Cela empêche le service de mise à jour de l’agent de contacter Azure pour les mises à jour logicielles. Vous ne devez donc jamais installer le proxy de protection par mot de passe Microsoft Entra et le proxy d’application sur la même machine.

### Télécharger les logiciels requis

Deux programmes d’installation sont nécessaires pour un déploiement local de la protection par mot de passe Microsoft Entra :

- Agent DC de protection par mot de passe Microsoft Entra (*AzureADPasswordProtectionDCAgentSetup.msi*)
- Proxy de protection par mot de passe Microsoft Entra (*AzureADPasswordProtectionProxySetup.exe*)

### Installer et configurer le service proxy

Le service proxy de protection par mot de passe Microsoft Entra se trouve généralement sur un serveur membre au sein de votre environnement AD DS local. Une fois l'installation terminée, le service proxy de protection par mot de passe Microsoft Entra communique avec Microsoft Entra pour garder une copie des listes générale et personnalisée de mots de passe interdits pour votre locataire Microsoft Entra.

### Installez le service d’agent DC

Pour installer le service de l’agent DC de protection par mot de passe Microsoft Entra, exécutez le package `AzureADPasswordProtectionDCAgentSetup.msi`.

Vous pouvez automatiser l’installation du logiciel à l’aide de procédures MSI standard, comme illustré dans l’exemple suivant :

```console

msiexec.exe /i AzureADPasswordProtectionDCAgentSetup.msi /quiet /qn /norestart
```

Vous pouvez omettre l’indicateur `/norestart` si vous préférez que le programme d’installation redémarre automatiquement la machine.

L’installation ou la désinstallation du logiciel nécessitent un redémarrage. Cette exigence découle du fait que les DLL de filtrage de mots de passe ne sont chargées ou déchargées que par un redémarrage.

L’installation de la protection par mot de passe Microsoft Entra locale est terminée une fois que le logiciel de l’agent du contrôleur de domaine est installé sur un contrôleur de domaine et que cet ordinateur est redémarré. Aucune configuration supplémentaire n'est nécessaire ou possible. Les événements de changement de mot de passe sur les contrôleurs de domaine locaux utilisent les listes de mots de passe interdits configurées dans Microsoft Entra.

Conseil

Vous pouvez installer l’agent DC de protection par mot de passe Microsoft Entra sur une machine qui n’est pas encore un contrôleur de domaine. Dans ce cas, le service démarre et s’exécute, mais reste inactif jusqu’à ce que la machine soit promue en tant que contrôleur de domaine.

### Mise à niveau du service proxy

Le service proxy de protection par mot de passe Microsoft Entra prend en charge la mise à niveau automatique. La mise à niveau automatique utilise le service du programme de mise à jour de l’agent Microsoft Entra Connect, installé côte à côte avec le service proxy. La mise à niveau automatique est activée par défaut et peut être activée ou désactivée à l’aide de l’applet de commande `Set-AzureADPasswordProtectionProxyConfiguration`.

Pour connaître le paramétrage actuel, vous pouvez utiliser l’applet de commande `Get-AzureADPasswordProtectionProxyConfiguration`. Nous recommandons de laisser la mise à niveau automatique activée en permanence.

La cmdlet `Get-AzureADPasswordProtectionProxy` peut être utilisée pour interroger la version du logiciel de tous les serveurs proxy de protection par mot de passe Microsoft Entra actuellement installés dans une forêt.

#### Processus de mise à niveau manuelle

Une mise à niveau manuelle s’accomplit en exécutant la dernière version du programme d’installation du logiciel `AzureADPasswordProtectionProxySetup.exe`. La dernière version du logiciel est disponible dans le Centre de téléchargement Microsoft.

Vous n’avez pas besoin de désinstaller la version actuelle du service proxy de protection par mot de passe Microsoft Entra, car le programme d’installation effectue une mise à niveau sur place. Aucun redémarrage n’est nécessaire lors de la mise à niveau du service proxy. Vous pouvez automatiser la mise à niveau du logiciel à l’aide de procédures MSI standard, par exemple `AzureADPasswordProtectionProxySetup.exe /quiet`.

### Mise à niveau de l’agent DC

Quand une version plus récente du logiciel de l’agent DC de protection par mot de passe Microsoft Entra est disponible, la mise à niveau s’effectue en exécutant la dernière version du package logiciel `AzureADPasswordProtectionDCAgentSetup.msi`. La dernière version du logiciel est disponible dans le Centre de téléchargement Microsoft.

Il n’est pas nécessaire de désinstaller la version actuelle du logiciel de l’agent DC, car le programme d’installation effectue une mise à niveau sur place. Un redémarrage est toujours requis lors de la mise à niveau du logiciel de l’agent DC. Cette exigence est due à un comportement de base de Windows.

Vous pouvez automatiser la mise à niveau du logiciel à l’aide de procédures MSI standard, par exemple `msiexec.exe /i AzureADPasswordProtectionDCAgentSetup.msi /quiet /qn /norestart`.

Vous pouvez omettre l'indicateur `/norestart` si vous préférez que le programme d’installation redémarre automatiquement l’ordinateur.

L’applet de commande `Get-AzureADPasswordProtectionDCAgent` peut être utilisée pour obtenir la version du logiciel de tous les agents DC Microsoft Entra Password Protection actuellement installés dans une forêt.


## Configurer des seuils de verrouillage intelligent

Le verrouillage intelligent permet d'éviter que des acteurs malveillants essaient de deviner les mots de passe de vos utilisateurs ou utilisent des méthodes de force brute pour rentrer dans vos systèmes. Le verrouillage intelligent peut reconnaître les connexions provenant d’utilisateurs validés et les traiter différemment de celles des attaquants et autres sources inconnues. Le verrouillage intelligent empêche les attaquants de pénétrer dans le système, tout en permettant à vos utilisateurs d’accéder à leurs comptes et de travailler.

### Fonctionnement du verrouillage intelligent

Par défaut, le verrouillage intelligent empêche les tentatives de connexion au compte pendant une minute après 10 tentatives infructueuses. Le compte est à nouveau verrouillé après chaque échec de connexion suivant, pendant une minute à la première, puis plus longtemps lors des tentatives suivantes. Afin de minimiser les moyens dont dispose un attaquant pour contourner ce comportement, nous ne divulguons pas le rythme auquel la période de verrouillage s’allonge au fil des tentatives de connexion infructueuses.

Le verrouillage intelligent suit les trois derniers hachages de mots de passe incorrects afin d’éviter d’incrémenter le compteur de verrouillages pour le même mot de passe. Si un utilisateur entre plusieurs fois le même mot de passe incorrect, le compte n'est pas verrouillé.

Les déploiements fédérés utilisant AD FS 2016 et AD FS 2019 peuvent bénéficier d’avantages similaires à ceux fournis par l’utilisation du verrouillage extranet et du verrouillage intelligent extranet AD FS.

Le verrouillage intelligent est activé en permanence pour les clients Microsoft Entra ID disposant des paramètres par défaut qui offrent la combinaison idéale de sécurité et de facilité d'utilisation. Pour personnaliser les paramètres de verrouillage intelligent avec des valeurs spécifiques à votre organisation, vos utilisateurs ont besoin d'une licence Microsoft Entra ID Premium P1 ou d'une licence de niveau supérieur.

L’utilisation du verrouillage intelligent ne garantit pas qu’un véritable utilisateur n’est jamais verrouillé. Lorsque le verrouillage intelligent verrouille un compte d'utilisateur, nous mettons tout en œuvre pour ne pas verrouiller le véritable utilisateur. Le service de verrouillage veille à ce que des personnes mal intentionnées n’aient pas accès au compte d’un véritable utilisateur. Les considérations suivantes s'appliquent :

- Chaque centre de données Microsoft Entra effectue le suivi des verrous indépendamment. Un utilisateur dispose d’un nombre de tentatives de (`threshold\_limit * datacenter\_count`) s’il atteint chaque centre de données.
- Le verrouillage intelligent utilise un *emplacement familier* par opposition à un *emplacement inconnu* pour faire la différence entre une personne mal intentionnée et le véritable utilisateur. Les emplacements familiers et inconnus disposent tous deux de compteurs de verrouillages distincts.

Le verrouillage intelligent peut être intégré aux déploiements hybrides à l’aide de la synchronisation du hachage de mot de passe ou de l’authentification directe, en vue d’empêcher les comptes Active Directory Domain Services (AD DS) locaux d’être verrouillés par les attaquants. En définissant les stratégies de verrouillage intelligent nécessaires dans Microsoft Entra ID, vous pouvez bloquer les attaques avant même qu’elles atteignent l’instance AD DS locale.

Lorsque l’administrateur configure l’authentification directe, les considérations suivantes s’appliquent :

- Le seuil de verrouillage de Microsoft Entra est inférieur au seuil de verrouillage de compte AD DS. Définissez les valeurs de sorte que le seuil de verrouillage de compte AD DS soit au moins deux ou trois fois supérieur au seuil de verrouillage Microsoft Entra.
- La durée de verrouillage Microsoft Entra doit être définie comme plus longue que celle du verrouillage de compte AD DS. La durée est définie en secondes, tandis que la durée d'AD est définie en minutes.

Si vous souhaitez, par exemple, que la durée du verrouillage intelligent soit supérieure à celle de l'AD DS, Microsoft Entra ID devra être défini sur 120 secondes (2 minutes) alors que l'AD local est défini sur 1 minute (60 secondes). Si vous souhaitez que le seuil de verrouillage soit de 5, le seuil de verrouillage de l'AD local doit être de 10. Cette configuration garantit que le verrouillage intelligent empêche le verrouillage de vos comptes AD locaux par des attaques par force brute sur vos comptes Microsoft Entra.


## Exercice – gérer les valeurs de verrouillage intelligentes de Microsoft Entra

### Gérer les valeurs de verrouillage intelligent de Microsoft Entra

En fonction des exigences de votre organisation, vous pouvez personnaliser les valeurs du verrouillage intelligent Microsoft Entra. Pour personnaliser les paramètres de verrouillage intelligent en vue de répondre aux besoins de votre organisation, vos utilisateurs doivent disposer d'une licence Microsoft Entra ID Premium P1 ou plus élevée.

1. Connectez-vous au [centre d’administration Microsoft Entra](https://entra.microsoft.com/) avec un compte administrateur général.
2. Ouvrez le menu du portail, puis sélectionnez **Protection**.
3. Dans le menu Protection, sélectionnez **Méthodes d'authentification**.
4. Dans le menu Méthodes d'authentification, sélectionnez **Protection par mot de passe**.
5. Dans les paramètres de protection par mot de passe, dans la zone **Durée du verrouillage en secondes**, définissez la valeur sur 120.
6. En regard de **Mode**, sélectionnez **Appliqué**.
7. Enregistrez vos modifications.

Remarque

Lorsque le seuil de verrouillage intelligent est déclenché, le message suivant s'affiche en cas de verrouillage du compte :

Votre compte est temporairement verrouillé pour éviter toute utilisation non autorisée. Réessayez plus tard. Si le problème persiste, contactez votre administrateur.


## Implémenter l'authentification Kerberos et basée sur un certificat dans Microsoft Entra ID

Vous pouvez fournir l’authentification unique pour les applications locales publiées via le proxy d’application. Les applications sont sécurisées avec l’authentification Windows intégrée. L’accès à ces applications nécessitent un ticket Kerberos. Le proxy d’application utilise la délégation Kerberos contrainte (KCD) pour prendre en charge ces applications. Vous pouvez activer l’authentification unique sur vos applications avec l’authentification Windows intégrée. Donnez aux connecteurs de proxy d’application l’autorisation dans Active Directory d’emprunter l’identité des utilisateurs. Les connecteurs utilisent cette autorisation pour envoyer et recevoir des jetons en leur nom.

#### Flux de processus d’authentification Kerberos

![Diagramme du flux de processus pour l’authentification Kerberos dans Microsoft Entra ID. La description complète du processus se trouve dans le contenu.](https://learn.microsoft.com../../wwl-sci/manage-user-authentication/media/kerberos-authentication.png)

1. L’utilisateur entre l’URL pour accéder à l’application locale via le proxy d’application.
2. Le proxy d’application redirige la demande vers les services d’authentification de Microsoft Entra pour effectuer la pré-authentification. À ce stade, Microsoft Entra ID applique les stratégies d’authentification et d’autorisation applicables, comme l’authentification multifacteur. Si l’utilisateur est validé, Microsoft Entra ID crée un jeton et l’envoie à l’utilisateur.
3. L’utilisateur transmet le jeton au proxy d’application.
4. Le proxy d’application valide le jeton et y récupère le nom d’utilisateur principal (UPN), puis le connecteur obtient l’UPN et le nom de principal du service (SPN) via un canal sécurisé doublement authentifié.
5. Le connecteur effectue une négociation de délégation Kerberos contrainte avec l’instance locale d’Active Directory, en empruntant l’identité de l’utilisateur pour obtenir un jeton Kerberos pour l’application.
6. Active Directory envoie le jeton Kerberos de l’application au connecteur.
7. Le connecteur envoie la demande d’origine au serveur d’applications, en utilisant le jeton Kerberos reçu d’Active Directory.
8. L’application envoie la réponse au connecteur, qui est ensuite retournée au service de proxy d’application et enfin à l’utilisateur.

#### Vérifiez que votre environnement est prêt

Avant de commencer avec l’authentification unique pour les applications avec l’authentification Windows intégrée, assurez-vous que votre environnement est prêt à l’aide des configurations et paramètres suivants :

- Vos applications, comme les applications web SharePoint, sont configurées pour utiliser l’authentification Windows intégrée.
- Toutes vos applications disposent de noms principaux de service.
- Le serveur exécutant le connecteur et le serveur exécutant l’application sont joints au domaine.
- Le serveur exécutant le connecteur est autorisé à lire l’attribut TokenGroupsGlobalAndUniversal pour les utilisateurs.


## Configurer l'authentification utilisateur Microsoft Entra pour les machines virtuelles

Les organisations peuvent désormais améliorer la sécurité des machines virtuelles Windows et Linux dans Azure en y intégrant l’authentification Microsoft Entra. Vous pouvez maintenant utiliser Microsoft Entra ID comme plateforme d’authentification principale pour vous connecter à :

- Windows Server 2022, 2025 ou version ultérieure installée avec Expérience de bureau.
- Windows 11 24H2 ou version ultérieure.
- Machine virtuelle Linux.

Vous pouvez ensuite contrôler et appliquer de manière centralisée les stratégies d’accès conditionnel et d’accès en fonction du rôle qui autorisent ou refusent l’accès aux machines virtuelles.

#### Avantages

- Utilisez les informations d’identification Microsoft Entra pour vous connecter aux machines virtuelles Windows dans Azure.
- Réduisez la dépendance aux comptes administrateur locaux.
- Stratégies portant sur la complexité et la durée de vie du mot de passe qui sont configurées pour votre Microsoft Entra ID.
- Configurez des stratégies d’accès conditionnel pour exiger l’authentification multifacteur et d’autres signaux comme utilisateur à risque ou connexion à risque.

#### Configurer la connexion à Microsoft Entra pour les machines virtuelles Windows

Pour utiliser la connexion Microsoft Entra sur une machine virtuelle Windows dans Azure, vous devez :

- Commencer par activer l’option de connexion Microsoft Entra pour votre machine virtuelle Windows.
- Configurer ensuite les attributions de rôles Azure pour les utilisateurs autorisés à se connecter à la machine virtuelle.

#### Configurer la connexion à Microsoft Entra pour les machines virtuelles Linux

Vous pouvez activer la connexion Microsoft Entra pour toutes les distributions Linux prises en charge mentionnées en utilisant le portail Azure. Par exemple, pour créer une machine virtuelle Ubuntu Server 18.04 LTS dans Azure avec authentification Microsoft Entra ID :

1. Connectez-vous au portail Azure à l’aide d’un compte disposant d’un accès pour créer des machines virtuelles, puis sélectionnez + Créer une ressource.
2. Sélectionnez **Créer** sous Ubuntu Server 18.04 LTS dans la vue Populaire.
3. Sous l’onglet Gestion, cochez la case pour activer `Login with Microsoft Entra ID`.
4. Assurez-vous qu’une identité managée attribuée par le système est vérifiée.
5. Terminez la configuration de la machine virtuelle Linux.


## Évaluation du module

Choisissez la meilleure réponse à chacune des questions ci-dessous.

### Vérifiez vos connaissances


## Récapitulatif et ressources

Maintenant que vous avez parcouru ce module, vous devez être capable de :

- Administrer les méthodes d’authentification (FIDO2/sans mot de passe).
- Implémenter une solution d’authentification basée sur Windows Hello Entreprise.
- Configurer et déployer la réinitialisation du mot de passe en libre-service.
- Déployez et gérez la protection par mot de passe et les verrouillages intelligents.
- Implémentez l’authentification Kerberos et basée sur un certificat.
- Configurer l'authentification utilisateur Microsoft Entra ID sur les machines virtuelles

### Ressources

Pour en savoir plus sur les idées que nous avons vues dans ce module, consultez les liens suivants vers la documentation.

- [Activer l'inscription combinée des informations de sécurité dans Microsoft Entra ID](https://learn.microsoft.com/fr-fr/entra/identity/authentication/howto-registration-mfa-sspr-combined)
- [Créer une politique de gestion du contrôle d'accès résiliente dans Microsoft Entra ID](https://learn.microsoft.com/fr-fr/entra/identity/authentication/concept-resilient-controls)
- [Vue d’ensemble de Windows Hello Entreprise](https://learn.microsoft.com/fr-fr/windows/security/identity-protection/hello-for-business/)
- [Application Microsoft Authenticator](https://learn.microsoft.com/fr-fr/entra/identity/authentication/concept-authentication-authenticator-app)
- [Options d’authentification sans mot de passe pour Microsoft Entra ID](https://learn.microsoft.com/fr-fr/entra/identity/authentication/how-to-plan-prerequisites-phishing-resistant-passwordless-authentication)
- [Méthodes d’authentification dans Microsoft Entra ID - Jetons OATH](https://learn.microsoft.com/fr-fr/entra/identity/authentication/concept-authentication-oath-tokens)
- [Configurer et activer les utilisateurs pour l'authentification par SMS à l'aide de Microsoft Entra ID](https://learn.microsoft.com/fr-fr/entra/identity/authentication/howto-authentication-sms-signin)
- [Activer la protection par mot de passe Microsoft Entra localement](https://learn.microsoft.com/fr-fr/entra/identity/authentication/howto-password-ban-bad-on-premises-deploy)
- [Authentification unique à l’aide de Kerberos pour les applications Proxy d’application](https://learn.microsoft.com/fr-fr/entra/identity/app-proxy/how-to-configure-sso)


---

# Planifier, implémenter et administrer l’accès conditionnel

_https://learn.microsoft.com/fr-fr/training/modules/plan-implement-administer-conditional-access/_


## Présentation

L’accès conditionnel offre une granularité précise de contrôle sur les utilisateurs et les identités qui peuvent effectuer des activités spécifiques, accéder aux ressources et garantir la sécurité des données et des systèmes. Avec l’introduction du contrôle des identités pour Microsoft Entra, désormais étendu aux agents IA, vous appliquez les mêmes principes Confiance nulle aux identités d'agents que ceux que vous appliquez aux utilisateurs et aux identités de charge de travail.

### Objectifs d’apprentissage

Dans ce module, vous allez découvrir les points suivants :

- Planifier et implémenter les paramètres de sécurité par défaut.
- Planifier des stratégies d’accès conditionnel.
- Implémenter des contrôles et des affectations de stratégie d’accès conditionnel (ciblage, applications et conditions).
- Tester et résoudre les problèmes des stratégies d’accès conditionnel.
- Implémenter des contrôles d’application.
- Implémenter la gestion des sessions.
- Configurez l’évaluation continue de l’accès.
- Identifiez comment les identités d’agent sont protégées à l’aide de l’accès conditionnel.


## Planifier les paramètres de sécurité par défaut

La gestion de la sécurité peut s’avérer ardue lorsque les attaques courantes liées aux identités, telles que la pulvérisation de mot de passe, la relecture et le hameçonnage, deviennent monnaie courante. Les paramètres de sécurité par défaut fournissent des paramètres par défaut sécurisés que Microsoft gère pour le compte des organisations afin de garantir la sécurité des clients jusqu’à ce que les organisations soient prêtes à gérer leur propre histoire de sécurité des identités. Les paramètres de sécurité par défaut fournissent des paramètres de sécurité préconfigurés, tels que :

- Exiger que tous les utilisateurs s’inscrivent pour l’authentification multifacteur.
- Exigez des administrateurs qu’ils effectuent l’authentification multifacteur.
- En restreignant les protocoles d’authentification hérités.
- Exigez des utilisateurs qu’ils effectuent l’authentification multifacteur, lorsque cela est nécessaire.
- En protégeant des activités privilégiées, telles que l’accès au Portail Azure.

### Disponibilité

Les paramètres par défaut de sécurité Microsoft sont accessibles à tout le monde. Le but est de s’assurer que toutes les organisations bénéficient d’un niveau de sécurité de base activé, sans coût supplémentaire. Si votre locataire a été créé le 22 octobre 2019 ou après, les valeurs par défaut de sécurité pourraient déjà être activées. Pour protéger tous les utilisateurs, les valeurs par défaut de sécurité sont activées sur tous les nouveaux locataires lors de la création.

Pour activer ou désactiver les paramètres de sécurité par défaut, connectez-vous au [centre d’administration Microsoft Entra](https://entra.microsoft.com) en tant qu’administrateur d’accès conditionnel, puis accédez aux**propriétés**> de > Entra, puis sélectionnez **Gérer les paramètres de sécurité par défaut**.

#### À qui cela s’adresse-t-il ?

| **Qui doit utiliser les paramètres par défaut de sécurité ?** | **Qui ne doit pas utiliser les paramètres par défaut de sécurité ?** |
|---|---|
| Les organisations qui souhaitent augmenter leur niveau de sécurité, mais ne savent pas comment ou par où commencer | Les organisations utilisant des stratégies d’accès conditionnel pour regrouper les signaux, prendre des décisions et appliquer des stratégies organisationnelles |
| Les organisations utilisant le niveau gratuit de licences Microsoft Entra ID | Organisation avec licences Microsoft Entra ID Premium |
|   | Les organisations avec des exigences de sécurité complexes qui justifient l’utilisation de l’accès conditionnel |

### Stratégies appliquées

#### Inscription à l’authentification multifacteur unifiée

Tous les utilisateurs de votre locataire doivent s’inscrire à l’authentification multifacteur (MFA) à l’aide de l’application Microsoft Authenticator. L’inscription est requise immédiatement : il n’y a pas de période de grâce. Lorsque les utilisateurs se connectent une fois que les paramètres de sécurité par défaut sont activés, ils sont invités à s’inscrire avant de pouvoir accéder à n’importe quelle ressource. L’invite MFA utilise la correspondance de nombres, où les utilisateurs entrent un chiffre affiché à l’écran dans l’application Microsoft Authenticator, ce qui aide à prévenir les attaques de fatigue MFA.

#### Protection des administrateurs

Les utilisateurs disposant d’un accès privilégié augmentent souvent l’accès à votre environnement. En raison de l’importance de ces comptes, vous devez leur accorder une attention particulière. Une méthode courante pour améliorer la protection de comptes privilégiés consiste à demander une forme de vérification de compte plus stricte pour se connecter. Dans Microsoft Entra ID, vous pouvez obtenir une vérification plus élevée des comptes en exigeant l’authentification multifacteur.

Une fois l’inscription avec l’authentification multifacteur terminée, les rôles d’administrateur Microsoft Entra suivants sont requis pour effectuer une autre authentification chaque fois qu’ils se connectent :

- Administrateur général
- Administrateur d’application
- Administrateur d’authentification
- Administrateur de la stratégie d’authentification
- Administrateur de facturation
- Administrateur d’applications cloud
- Administrateur de l’accès conditionnel
- Administrateur Exchange
- Administrateur du support technique
- Administrateur de la Gouvernance de l'Identité
- Administrateur de mots de passe
- Administrateur d’authentification privilégié
- Administrateur de rôle privilégié
- Administrateur de la sécurité
- Administrateur SharePoint
- Administrateur d'utilisateurs

#### Protection de tous les utilisateurs

Nous avons tendance à considérer que les comptes administrateur sont les seuls qui nécessitent des couches d’authentification supplémentaires. Les administrateurs ont largement accès à des informations sensibles et peuvent modifier des paramètres à l’échelle d’un abonnement. Pourtant, les attaquants ciblent souvent les utilisateurs finaux.

Une fois que ces personnes malveillantes ont accès, elles peuvent demander l’accès aux informations privilégiées pour le compte du détenteur du compte d’origine. Elles peuvent même télécharger l’annuaire entier pour effectuer une attaque par hameçonnage sur l’ensemble de votre organisation.

Une méthode courante pour améliorer la protection de tous les utilisateurs consiste à demander une forme de vérification de compte plus stricte, telle que l’authentification multifacteur, pour tous. Une fois que les utilisateurs ont terminé l’inscription à l’authentification multifacteur, ils sont invités à fournir une authentification supplémentaire chaque fois que nécessaire. Cette fonctionnalité protège toutes les applications inscrites avec Microsoft Entra ID, y compris les applications SaaS.

#### Blocage de l’authentification héritée

Pour permettre à vos utilisateurs d’accéder facilement à vos applications cloud, Microsoft Entra ID prend en charge différents protocoles d’authentification, notamment l’authentification héritée. L’*authentification héritée* est une requête d’authentification effectuée par :

- Les clients Office qui n'utilisent pas l'authentification moderne (par exemple, un client Office 2010). L’authentification moderne englobe des clients qui implémentent des protocoles, tels que OAuth 2.0, pour prendre en charge des fonctionnalités telles que l’authentification multifacteur et les cartes à puce. L’authentification héritée ne prend généralement en charge que des mécanismes moins sécurisés, tels que les mots de passe.
- Client utilisant des protocoles de messagerie tels que IMAP, SMTP ou POP3.

Aujourd’hui, la plupart des tentatives de connexion compromettantes proviennent de l’authentification héritée. L’authentification héritée ne prend pas en charge l’authentification multifacteur. Même si une stratégie d’authentification multifacteur est activée sur votre annuaire, un attaquant peut s’authentifier à l’aide d’un protocole plus ancien et contourner l’authentification multifacteur.

Lorsque les paramètres de sécurité par défaut sont activés dans votre locataire, toutes les demandes d’authentification effectuées par un protocole hérité sont bloquées. Les paramètres par défaut de sécurité bloquent l’authentification de base Exchange Active Sync.


## Exercice - Utiliser les paramètres de sécurité par défaut

Dans cet exercice, essayez d’activer les paramètres de sécurité par défaut.

Remarque

Les valeurs par défaut de sécurité sont activées sur les nouveaux abonnements. Vous pouvez donc passer en revue le processus d’activation et de désactivation.

Pour activer les paramètres de sécurité par défaut dans votre répertoire :

1. Accédez au [Centre d’administration Microsoft Entra](https://entra.microsoft.com/) et connectez-vous en tant qu’administrateur de sécurité ou administrateur d’accès conditionnel.
2. Sélectionnez l’icône hamburger du menu Afficher le portail, puis Identité – Vue d’ensemble.
3. Dans le volet de navigation de gauche, dans la section Gérer, sélectionnez **Propriétés**.
4. En bas de la boite de dialogue Propriétés, sélectionnez **Gérer les paramètres de sécurité par défaut**.
5. Affectez la valeur **Oui** à **Activer les paramètres de sécurité par défaut** à l’aide du bouton bascule.
6. Sélectionnez **Enregistrer**.

#### Désactivation des paramètres de sécurité par défaut

Les organisations choisissant d’implémenter des stratégies d’accès conditionnel qui remplacent les paramètres de sécurité par défaut doivent désactiver les paramètres de sécurité par défaut.

Pour désactiver les paramètres de sécurité par défaut dans votre répertoire :

1. Accédez au [portail Azure](https://portal.azure.com/) et connectez-vous à l’aide d’un compte Administrateur pour l’annuaire.
2. Sélectionnez l’icône hamburger du menu Afficher le portail, puis Microsoft Entra ID.
3. En bas de la boite de dialogue Propriétés, sélectionnez **Gérer les paramètres de sécurité par défaut**.
4. Définissez **Activer les paramètres de sécurité par défaut** sur **Non** à l’aide du bouton bascule.
5. Sélectionnez **Enregistrer**.


## Planifier les stratégies d’accès conditionnel

La planification de votre déploiement d’accès conditionnel joue un rôle capital dans la réussite de la stratégie d’accès de votre organisation pour les applications et les ressources.

Dans un monde où la mobilité et le cloud sont la priorité, vos utilisateurs accèdent, en tous lieux, aux ressources de votre organisation depuis un large éventail d’appareils et d’applications. Ainsi, s’attacher exclusivement au contrôle des personnes accédant à une ressource ne suffit plus. Vous devez également tenir compte de l’endroit où l’utilisateur se trouve, de l’appareil qui est utilisé, de la ressource à laquelle il accède, et bien plus encore.

La fonctionnalité Accès conditionnel Microsoft Entra analyse des signaux, comme l’utilisateur, l’appareil et la localisation, afin d’automatiser les décisions et d’appliquer les stratégies d’accès propres à l’organisation pour la ressource. Vous pouvez utiliser des stratégies d’accès conditionnel pour appliquer des contrôles d’accès tels que l’authentification multifacteur (MFA). Les stratégies d’accès conditionnel vous permettent d’inviter des utilisateurs à l’authentification multifacteur lorsque cela est nécessaire pour la sécurité et à ne pas le leur demander lorsque cela n’est pas nécessaire.

![Diagramme illustrant le fonctionnement de l'accès conditionnel. Le fournisseur d'identité centralisé vérifie les règles avant l'octroi de l'accès.](https://learn.microsoft.com../../wwl-sci/plan-implement-administer-conditional-access/media/conditional-access-overview-how-it-works.png)

Bien que les paramètres de sécurité par défaut garantissent un niveau de sécurité De base, votre organisation a besoin de plus de souplesse que celle offerte par les paramètres de sécurité par défaut. Vous pouvez utiliser l’autorité de certification pour personnaliser les valeurs par défaut de sécurité avec plus de granularités et configurer de nouvelles stratégies qui répondent à vos besoins.

#### Avantages

Les avantages du déploiement de l’accès conditionnel sont les suivants :

- Augmentez la productivité : interrompez uniquement les utilisateurs avec une condition de connexion telle que l’authentification multifacteur lorsqu’un ou plusieurs signaux le justifient. Les stratégies d’accès conditionnel vous permettent de contrôler le moment auquel les utilisateurs sont invités à utiliser l’authentification multifacteur, quand l’accès est bloqué et quand les utilisateurs doivent utiliser un appareil de confiance.
- Gérer les risques : l’automatisation de l’évaluation des risques avec des conditions de stratégie signifie que les connexions à risque sont à la fois identifiées et corrigées ou bloquées. Le couplage de l’accès conditionnel à Identity Protection, qui détecte les anomalies et les événements suspects, vous permet de cibler le moment où l’accès aux ressources est bloqué ou contrôlé.
- Répondre à la conformité et à la gouvernance : l’accès conditionnel vous permet d’auditer l’accès aux applications, de présenter des conditions d’utilisation pour le consentement et de restreindre l’accès en fonction des stratégies de conformité.
- Gérer les coûts : le déplacement des stratégies d’accès vers l’ID Microsoft Entra réduit la dépendance vis-à-vis des solutions personnalisées ou locales pour l’autorité de certification et leurs coûts d’infrastructure.
- Confiance zéro : l’accès conditionnel vous permet de passer à un environnement de confiance zéro.

### Comprendre les composants des stratégies d’accès conditionnel

Les stratégies d’accès conditionnel sont des instructions de type si-alors : si une affectation est remplie, alors appliquer ces contrôles d’accès. Lorsque l’administrateur configure des politiques d’AC, les conditions sont *appelées affectations*. Les stratégies d’accès conditionnel vous permettent d’appliquer des contrôles d’accès aux applications de votre organisation, en fonction de certaines affectations.

Les affectations définissent les utilisateurs et les groupes qui doivent être concernés par la stratégie, les applications cloud ou les actions auxquelles la stratégie s’applique, ainsi que les conditions dans lesquelles la stratégie s’applique. Les paramètres de contrôle d’accès octroient ou bloquent l’accès à différentes applications cloud et peuvent permettre des expériences limitées dans des applications cloud spécifiques.

Questions courantes sur les affectations, les contrôles d’accès et les contrôles de session :

- Utilisateurs et groupes : quels utilisateurs et groupes seront inclus ou exclus de la stratégie ? Cette stratégie peut-elle inclure tous les utilisateurs, groupes d’utilisateurs particuliers, rôles d’annuaire ou utilisateurs externes ?
- Applications cloud ou actions : à quelles applications la stratégie s’applique-t-elle ? Quelles actions de l’utilisateur seront soumises à cette stratégie ?
- Conditions : quelles plateformes d’appareils seront incluses ou exclues de la stratégie ? Quels sont les emplacements approuvés de l’organisation ?
- Contrôles d’accès : voulez-vous octroyer l’accès aux ressources en implémentant des exigences telles que l’authentification multifacteur, des appareils marqués comme conformes ou des appareils à jointure hybride Microsoft Entra ?
- Contrôles de session : voulez-vous contrôler l’accès aux applications cloud en implémentant des exigences telles que des autorisations ou des contrôles d’application par accès conditionnel ?

Avec l’introduction de Identifiant d’assistant Microsoft Entra, les identités d’agent sont désormais des principes de premier ordre dans Microsoft Entra ID. Comme les utilisateurs ou les principaux de service, les agents peuvent être ciblés par des stratégies d’accès conditionnel, ce qui vous permet d’appliquer les mêmes contrôles Confiance Zéro aux agents IA que vous appliquez aux identités humaines. Vous traitez les identités d'agent de la même manière que vous traitez les identités de charge de travail : définissez des politiques selon le type d'identité, appliquez les contrôles d'accès appropriés et excluez les agents d'urgence ou de confiance si nécessaire.

#### Émission de jetons d’accès

Les jetons d’accès permettent aux clients d’appeler de manière sécurisée des API web protégées et ils sont utilisés par les API web pour effectuer l’authentification et l’autorisation. Selon la spécification OAuth, les jetons d'accès sont des chaînes opaques sans format défini. Certains fournisseurs d’identité (IDP) utilisent des GUID. D’autres utilisent des objets BLOB chiffrés. La plateforme d’identités Microsoft utilise un large éventail de formats de jeton d’accès en fonction de la configuration de l’API qui accepte le jeton.

Il est important de comprendre comment les jetons d’accès sont émis.

![Diagramme de l'émission d'un jeton d'accès pour l'accès conditionnel et de son utilisation.](https://learn.microsoft.com../../wwl-sci/plan-implement-administer-conditional-access/media/access-policy-token-issuance.png)

Remarque

Si aucune affectation n’est requise et qu’aucune stratégie d’accès conditionnel n’est appliquée, le comportement par défaut consiste à émettre un jeton d’accès.

Par exemple, imaginons une stratégie dans laquelle :

SI l’utilisateur est dans le groupe 1, ALORS forcer MFA sur l’accès à l’application 1.

SI un utilisateur n’est pas dans le groupe 1 tente d’accéder à l’application, LA condition **« if »** est remplie et un jeton est émis. L’exclusion d’utilisateurs hors du groupe 1 nécessite une stratégie distincte qui permet de bloquer tous les autres utilisateurs.

### Suivre les bonnes pratiques

L’infrastructure d’accès conditionnel vous offre une grande flexibilité de configuration. Toutefois, une grande flexibilité implique également que vous examiniez soigneusement chaque stratégie de configuration avant de la mettre en œuvre, afin d’éviter des résultats indésirables.

#### Configurer des comptes d’accès d’urgence

Si votre stratégie est mal configurée, elle peut verrouiller les organisations à l’extérieur du Portail Azure. Vous pouvez pallier le verrouillage accidentel d’administrateurs en créant quelques comptes d’accès d’urgence dans votre organisation. Vous en apprendrez davantage sur les comptes d’accès d’urgence plus loin dans ce cours.

#### Configurer le mode Rapport seul

Il peut ne pas être aisé de prévoir le nombre et les noms des utilisateurs concernés par des initiatives de déploiement courantes, comme :

- Le blocage de l’authentification héritée.
- L’obligation d’utiliser MFA.
- L’implémentation de stratégies de connexion à risque.

Le mode Rapport uniquement permet aux administrateurs d’évaluer les stratégies d’accès conditionnel avant de les activer dans leur environnement.

#### Exclure les pays depuis lesquels vous n’espérez jamais aucune connexion

Microsoft Entra ID vous permet de créer des emplacements nommés. Créez un emplacement nommé qui comprend tous les pays à partir desquels vous n’escomptez jamais qu’une connexion se produise. Créez ensuite une stratégie pour toutes les applications qui bloquent la connexion à partir de cet emplacement nommé. **Veillez à exempter vos administrateurs de cette stratégie**.

### Stratégies courantes

Quand vous planifiez votre solution de stratégie d’accès conditionnel, déterminez si vous devez créer des stratégies pour obtenir les résultats suivants.

- **Exiger l’authentification multifacteur.** Les cas d’usage courants incluent l’exigence de MFA par les administrateurs, pour des applications spécifiques, pour tous les utilisateurs ou à partir d’emplacements réseau non fiables.
- **Répondre aux comptes potentiellement compromis.** Trois stratégies par défaut peuvent être activées : exiger que tous les utilisateurs s’inscrivent à l’authentification multifacteur, exiger une modification de mot de passe pour les utilisateurs à haut risque et exiger l’authentification multifacteur pour les utilisateurs avec un risque de connexion moyen ou élevé.
- **Exigez des appareils gérés.** L’augmentation du nombre d’appareils pris en charge pour accéder aux ressources cloud permet d’améliorer la productivité de vos utilisateurs. Il est probable que vous ne souhaitiez pas que des appareils dont le niveau de protection est inconnu puissent accéder à certaines ressources de votre environnement. Pour ces ressources, exigez que les utilisateurs y accèdent uniquement au moyen d’un appareil géré.
- **Exigez des applications clientes approuvées.** Les employés utilisent leurs appareils mobiles pour des tâches à la fois personnelles et professionnelles. Pour les scénarios BYOD, vous devez décider si vous voulez gérer l’appareil entièrement, ou seules les données qu’il contient. Si vous gérez uniquement les données et les accès, vous pouvez exiger des applications cloud approuvées qui peuvent protéger vos données d’entreprise.
- **Bloquer l’accès.** Le blocage de l’accès remplace toutes les autres affectations pour un utilisateur et a la possibilité d’empêcher l’ensemble de votre organisation de se connecter à votre locataire. Il peut être utilisé, par exemple, lorsque vous migrez une application vers l’ID Microsoft Entra, mais que vous n’êtes pas prêt à vous y connecter. Vous pouvez également empêcher certains emplacements réseau d’accéder à vos applications cloud ou empêcher des applications utilisant l’authentification héritée d’accéder aux ressources de votre locataire.  Important Si vous créez une stratégie pour bloquer l’accès de tous les utilisateurs, veillez à exclure de la stratégie les comptes d’accès d’urgence, et éventuellement tous les administrateurs.

### Générer et tester les stratégies

À chaque étape de votre déploiement, assurez-vous que les évaluations effectuées donnent les résultats attendus.

Lorsque de nouvelles stratégies sont prêtes, déployez-les en phases dans l’environnement de production :

- Indiquez aux utilisateurs finaux les changements internes.
- Commencez par un petit ensemble d’utilisateurs et vérifiez que la stratégie se comporte comme prévu.
- Quand vous étendez une stratégie à davantage d’utilisateurs, continuez à exclure tous les administrateurs. De cette façon, au moins une personne a accès à la stratégie si un changement est nécessaire.
- N’appliquez une stratégie à tous les utilisateurs qu’après l’avoir testée minutieusement. Vérifiez que vous disposez au moins d’un compte administrateur auquel une stratégie ne s’applique pas.

#### Créer des utilisateurs de test

Créez un ensemble d’utilisateurs de test qui reflète les utilisateurs de votre environnement de production. La création d’utilisateurs de test vous permet de vérifier que vos stratégies fonctionnent comme prévu avant d’impacter les utilisateurs réels, et de risquer d’interrompre leur accès aux applications et aux ressources.

Certaines organisations ont des locataires de test dans ce but. Toutefois, il peut être difficile de recréer toutes les conditions et les applications dans un locataire de test pour tester intégralement le résultat d’une stratégie.

#### Créer un plan de test

Le plan de test est important pour comparer les résultats attendus et les résultats réels. Vous devez toujours avoir un objectif avant de tester quelque chose. Le tableau suivant décrit des exemples de cas de test. Ajustez les scénarios et les résultats attendus en fonction de la configuration de vos stratégies d’accès conditionnel.

| **Nom de la stratégie** | **Scénario** | **Résultat attendu** |
|---|---|---|
| Exiger l’authentification multifacteur | L’utilisateur autorisé se connecte à l’application quand il est dans un emplacement approuvé / au bureau | L’utilisateur n’est pas invité à utiliser l’authentification multifacteur. L’utilisateur dispose d’un droit d’accès. L’utilisateur se connecte à partir d’un emplacement approuvé. Vous pouvez choisir d’exiger l’authentification multifacteur dans ce cas. |
| Exiger l’authentification multifacteur | L’utilisateur autorisé se connecte à l’application quand il n’est pas dans un emplacement approuvé / au bureau | L’utilisateur est invité à utiliser l’authentification multifacteur et peut se connecter |
| Exiger l’authentification multifacteur (pour les administrateurs) | L’administrateur général se connecte à l’application | L’administrateur est invité à utiliser l’authentification multifacteur |
| Connexions risquées | L’utilisateur se connecte à l’application à l’aide d’un navigateur non approuvé | L’utilisateur est invité à utiliser l’authentification multifacteur |
| Gestion des périphériques | L’utilisateur autorisé tente de se connecter à partir d’un appareil autorisé | Accès accordé |
| Gestion des périphériques | L’utilisateur autorisé tente de se connecter à partir d’un appareil non autorisé | Accès bloqué |
| Changement de mot de passe pour les utilisateurs à risque | L’utilisateur autorisé tente de se connecter avec des informations d’identification compromises (connexion à risque élevé) | L’utilisateur est invité à changer le mot de passe ou l’accès est bloqué selon votre stratégie |

### Conditions de licence

- Microsoft Entra ID gratuit – Aucun accès conditionnel
- Abonnement gratuit à Office 365 : Aucun accès conditionnel
- Microsoft Entra ID Premium 1 (ou Microsoft 365 E3 et versions ultérieures) : travail avec accès conditionnel basé sur des règles standard
- Microsoft Entra ID Premium 2 : Accès conditionnel et vous pouvez également utiliser les options de connexion risquée, d’utilisateurs à risque et de connexion basée sur les risques (à partir d’Identity Protection)


## Implémenter les contrôles et les attributions de la stratégie d'accès conditionnel

L’accès conditionnel est une fonctionnalité avancée de l’ID Microsoft Entra qui vous permet de spécifier des stratégies détaillées qui contrôlent qui peuvent accéder à vos ressources. À l’aide de l’accès conditionnel, vous pouvez protéger vos applications en limitant l’accès des utilisateurs en fonction de signaux tels que l’appartenance au groupe, la conformité des appareils, l’emplacement réseau et les risques de connexion.

### Créer une stratégie d’accès conditionnel

Il s’agit d’un guide abrégé de création d’une stratégie d’accès conditionnel. La documentation complète est disponible dans [Qu’est-ce que l’accès conditionnel ?](https://learn.microsoft.com/fr-fr/entra/identity/conditional-access/overview)

Pour créer une politique :

1. Connectez-vous au [Centre d’administration Microsoft Entra](https://entra.microsoft.com) en tant qu’administrateur d’accès conditionnel au moins.
2. Accédez à **Protection**>**Accès conditionnel**.
3. Sélectionnez **+ Nouvelle stratégie**.
4. Donnez à la stratégie un nom explicite.
5. Configurer **les affectations** : sélectionnez les utilisateurs, les groupes ou les rôles auxquels la stratégie s’applique.
6. Configurez les **ressources cibles** : sélectionnez les applications cloud ou les actions utilisateur que couvre la stratégie.
7. Configurez toutes **les conditions** supplémentaires telles que les risques de connexion, la plateforme d’appareils ou l’emplacement.
8. Sous **Contrôles d’accès**, configurez les contrôles **Grant** ou **Session** à appliquer.
9. Définissez **Activer la stratégie** sur **Rapport uniquement** pour tester l’impact avant d’activer, puis sélectionnez **Créer**.

Microsoft recommande de démarrer toutes les nouvelles stratégies en mode rapport uniquement. Surveillez les journaux de connexion pour vérifier le comportement attendu avant de passer la politique sur **Activé**.

### Accès conditionnel basé sur les risques de connexion

La plupart des utilisateurs ont un comportement normal qui peut être suivi. Lorsqu’ils ne suivent pas cette norme, il peut être risqué de les autoriser à se connecter. Vous souhaitez bloquer ces utilisateurs ou leur demander d’effectuer une authentification multifacteur pour prouver qu’ils sont vraiment ceux qu’ils prétendent être.

Un risque de connexion reflète la probabilité qu’une requête d’authentification donnée soit rejetée par le propriétaire de l'identité. Des organisations disposant de licences Microsoft Entra ID Premium P2 peuvent créer des stratégies d’accès conditionnel englobant les détections de risques de connexion de Microsoft Entra Identity Protection.

Cette stratégie peut être affectée au moyen de l’accès conditionnel lui-même ou de Microsoft Entra Identity Protection. Les organisations doivent choisir l’une de deux options pour activer une stratégie d’accès conditionnel basé sur les risques de connexion qui nécessite un changement de mot de passe sécurisé.

### Accès conditionnel basé sur le risque lié à l'utilisateur

Microsoft travaille avec des chercheurs, les forces de l’ordre, les différentes équipes de sécurité de Microsoft et d’autres sources approuvées pour rechercher les paires nom d’utilisateur/mot de passe divulguées. Des organisations disposant des licences Microsoft Entra ID Premium P2 peuvent créer des stratégies d’accès conditionnel englobant des détections de risques pour des utilisateurs Microsoft Entra Identity Protection.

À l’instar de l’accès conditionnel basé sur les risques de connexion, cette stratégie peut être affectée au moyen de l’accès conditionnel lui-même ou de Microsoft Entra Identity Protection.

### Sécurisation de l’inscription des informations de sécurité

La sécurisation du moment et de la manière dont les utilisateurs s'inscrivent pour l’authentification multifacteur et la réinitialisation de mot de passe en libre-service est désormais possible grâce aux actions des utilisateurs dans une politique de contrôle d'accès conditionnel. Cette fonctionnalité de prévisualisation est à la disposition des organisations qui ont activé l’inscription combinée. Cette fonctionnalité peut être activée dans les organisations qui souhaitent utiliser des conditions, telles qu’un emplacement réseau approuvé, pour restreindre l’accès à l'enregistrement pour l’authentification multifacteur et la réinitialisation de mot de passe en libre-service (SSPR).

#### Créer une stratégie pour exiger l’inscription à partir d’un emplacement approuvé

La stratégie suivante s’applique à tous les utilisateurs sélectionnés qui tentent de s’inscrire à l’aide de l’expérience d’inscription combinée ; elle leur bloque l’accès sauf s’ils se connectent à partir d’un emplacement réseau approuvé.

1. Dans le **Centre d’administration Microsoft Entra**, accédez à **Protection**, puis **Accès conditionnel**.
2. Sélectionnez **+ Créer une nouvelle stratégie**.
3. Dans **Nom**, entrez un nom pour cette stratégie. Par exemple, **Inscription d’informations de sécurité combinée sur les réseaux approuvés**.
4. Sous **Affectations**, sélectionnez **Utilisateurs et groupes**, puis sélectionnez les utilisateurs et les groupes auxquels vous souhaitez appliquer cette stratégie.   Remarque Si vous ciblez des agents IA au lieu des utilisateurs, vous devez sélectionner **les identités de charge de travail** dans la zone Affectations et choisir votre identité d’agent à partir de l’ID de Microsoft Entra Agent à cette étape. Le reste de la structure de stratégie reste le même.
  1. Sous **Exclure**, sélectionnez **Utilisateurs et groupes** et choisissez les comptes d’accès d’urgence ou de secours de votre organisation.
  2. Sélectionnez **Terminé**.

5. Sous **Applications cloud ou actions**, sélectionnez **Actions utilisateur**, cochez **Inscrire des informations de sécurité**.
6. Sous **Conditions**, sélectionnez **Emplacements**.
  - Configurez **Oui**.
  - Incluez **N’importe quel emplacement**.
  - Excluez **Tous les emplacements approuvés**.
  - Sélectionnez **Terminé** dans l’écran **Emplacements**.
  - Sélectionnez **Terminé** dans l’écran **Conditions**.

7. Sous **Conditions**, dans **Applications clientes (préversion)**, affectez à **Configurer** la valeur **Oui**, puis sélectionnez **Terminé**.
8. Sous **Contrôles d’accès**, sélectionnez **Accorder**.
  - Sélectionnez **Bloquer l’accès**.
  - Utilisez ensuite l’option **Sélectionner**.

9. Définissez l’option **Activer la stratégie** sur **Activé**.
10. Ensuite, sélectionnez **Enregistrer**.

À l’étape 6 de cette stratégie, les organisations ont la possibilité d’effectuer des choix. La stratégie ci-dessus requiert l’inscription à partir d’un emplacement réseau approuvé. Les organisations peuvent choisir d'utiliser n'importe quelles conditions disponibles à la place des **Emplacements**. N'oubliez pas que cette stratégie est une stratégie de blocage, donc tout ce qui est inclus est bloqué.

Vous pouvez choisir d’utiliser l’état de l’appareil au lieu de l’emplacement à l’étape 6 ci-dessus :

1. Sous **Conditions**, sélectionnez **État de l’appareil (version préliminaire)**.
2. Configurez **Oui**.
3. Incluez **Tous les états d'appareils**.
4. Excluez un **Appareil à jointure hybride Microsoft Entra** et/ou un **Appareil marqué comme conforme**.
5. Sélectionnez **Terminé** dans l’écran **Emplacements**.
6. Sélectionnez **Terminé** dans l’écran **Conditions**.

### Bloquer l’accès par emplacement

Avec la condition d’emplacement dans l’accès conditionnel, vous pouvez contrôler l’accès à vos applications cloud basées sur l’emplacement réseau d’un utilisateur. La condition d’emplacement est couramment utilisée pour bloquer l’accès à partir des pays/régions d’où votre organisation sait que le trafic ne doit pas provenir.

#### Définir des emplacements

1. Connectez-vous au **portail d’administration Microsoft Entra** en tant qu’administrateur de sécurité ou administrateur de l’accès conditionnel.
2. Accédez à **Protection**, puis à **l’accès conditionnel**, puis aux **emplacements nommés**.
3. Choisissez **Nouvel emplacement**.
4. Donnez un nom à votre emplacement.
5. Choisissez **Plages d’adresses IP** si vous connaissez les plages d’adresses IPv4 accessibles de l’extérieur qui composent cet emplacement ou ces **pays/régions**.
  1. Fournissez les **plages d’adresses IP** ou sélectionnez **Pays/régions** pour l’emplacement que vous spécifiez.

  - Si vous choisissez Pays/régions, vous pouvez éventuellement choisir d’inclure les zones inconnues.

6. Choisissez **Enregistrer**.

#### Créer une stratégie d’accès conditionnel

1. Connectez-vous au **Centre d’administration Microsoft Entra** en tant qu’administrateur de sécurité ou administrateur de l’accès conditionnel.
2. Accédez à **Protection**, puis **à l’accès conditionnel**.
3. Sélectionnez **+ Créer une nouvelle stratégie**.
4. Donnez un nom à votre stratégie. Nous recommandons aux organisations de créer une norme explicite pour les noms de leurs stratégies.
5. Sous **Affectations**, sélectionnez **Utilisateurs et groupes**.
  1. Sous **Inclure**, sélectionnez **Tous les utilisateurs**.
  2. Sous **Exclure**, sélectionnez **Utilisateurs et groupes** et choisissez les comptes d’accès d’urgence ou de secours de votre organisation.
  3. Sélectionnez **Terminé**.

6. Sous **Applications cloud ou actions**, sélectionnez **Inclure**, puis **Toutes les applications cloud**.
7. Sous **Conditions**, puis **Emplacement**.
  1. Définissez **Configurer** sur **Oui**.
  2. Sous **Inclure**, sélectionnez **Emplacements sélectionnés**.
  3. Sélectionnez l’emplacement bloqué que vous avez créé pour votre organisation.
  4. Choisissez **Sélectionner**.

8. Sous **Contrôles d'accès**, sélectionnez **Bloquer l’accès**, puis **Sélectionner**.
9. Confirmez vos paramètres et réglez **Activer la stratégie** sur **Activé**.
10. Sélectionnez **Créer** pour appliquer la stratégie d’accès conditionnel.

### Exiger un appareil conforme

Les organisations qui ont déployé Microsoft Intune peuvent utiliser les informations retournées par leurs appareils pour identifier les appareils qui répondent aux exigences de conformité, par exemple :

- Exiger un code PIN pour le déverrouillage.
- Exiger le chiffrement de l’appareil.
- Exiger une version minimale ou maximale du système d’exploitation.
- Exiger qu’un appareil ne soit ni jailbroken ni rooté.

Ces informations de conformité de la stratégie sont transmises à Microsoft Entra ID où l’accès conditionnel peut prendre des décisions pour accorder ou bloquer l’accès aux ressources.

#### Créer une stratégie d’accès conditionnel

Les étapes suivantes vous aideront à créer une stratégie d’accès conditionnel pour exiger que les appareils qui accèdent aux ressources soient marqués comme conformes aux stratégies de conformité Intune de votre organisation.

1. Connectez-vous au **Centre d’administration Microsoft Entra** en tant qu’administrateur de sécurité ou administrateur de l’accès conditionnel.
2. Accédez à **Protection**, puis **à l’accès conditionnel**.
3. Sélectionnez **+ Créer une nouvelle stratégie**.
4. Donnez un nom à votre stratégie. Nous recommandons aux organisations de créer une norme explicite pour les noms de leurs stratégies.
5. Sous **Affectations**, sélectionnez **Utilisateurs et groupes**.
  1. Sous **Inclure**, sélectionnez **Tous les utilisateurs**.
  2. Sous **Exclure**, sélectionnez **Utilisateurs et groupes** et choisissez les comptes d’accès d’urgence ou de secours de votre organisation.
  3. Sélectionnez **Terminé**.

6. Sous **Applications cloud ou actions**, sélectionnez **Inclure**, puis **Toutes les applications cloud**.
  1. Si vous devez exclure des applications spécifiques de votre stratégie, vous pouvez les choisir dans l'onglet **Exclure** sous **Sélectionner les applications cloud exclues**, puis choisir **Sélectionner**.
  2. Sélectionnez **Terminé**.

7. Sous **Conditions**, **Applications clientes (préversion)**, puis **Sélectionner les applications clientes auxquelles cette stratégie s’applique**, laissez toutes les valeurs par défaut sélectionnées, puis sélectionnez **Terminé**.
8. Sous **Contrôles d’accès**, puis **Autoriser**, sélectionnez **Exiger que l’appareil soit identifié comme conforme**.
9. Sélectionnez **Sélectionner**.
10. Confirmez vos paramètres et réglez **Activer la stratégie** sur **Activé**.
11. Sélectionnez **Créer** pour activer votre stratégie.

Remarque

Vous pouvez inscrire vos nouveaux appareils auprès d’Intune même si vous sélectionnez Exiger que l’appareil soit marqué comme conforme pour Tous les utilisateurs et Toutes les applications Cloud en procédant de la manière d’écrite ci-dessus. Le contrôle « Exiger que l’appareil soit marqué comme conforme » ne bloque pas l’inscription à Intune.

#### Comportement connu

Sur Windows 7, iOS, Android, macOS et certains navigateurs web tiers, Microsoft Entra ID identifie l’appareil à l’aide d’un certificat client provisionné lorsque l’appareil est inscrit auprès de Microsoft Entra ID. Lorsqu’un utilisateur se connecte pour la première fois via le navigateur, l’utilisateur est invité à sélectionner le certificat. L’utilisateur final doit sélectionner ce certificat pour pouvoir continuer à utiliser le navigateur.

### Bloquer l’accès

Pour les organisations utilisant une approche de migration vers le cloud conservatrice, la stratégie Bloquer tout est une option possible.

Avertissement

Une mauvaise configuration de stratégie de blocage peut entraîner l’exclusion des organisations du portail Azure.

Ce type de stratégie peut avoir des effets secondaires imprévus. Des opérations appropriées de test et de validation sont essentielles avant l’activation. Les administrateurs doivent utiliser des outils tels que le mode rapport uniquement d’accès conditionnel et l’outil What If dans l’accès conditionnel.

#### Exclusions d’utilisateurs

Les stratégies d’accès conditionnel sont des outils puissants. Nous vous recommandons d’exclure les comptes suivants de votre stratégie :

- **Comptes d’accès d’urgence** ou de type **break-glass** pour éviter le verrouillage des comptes à l’échelle du client. Dans le scénario improbable où tous les administrateurs seraient verrouillés hors de votre locataire, votre compte administratif d’accès d’urgence peut être utilisé pour vous connecter au locataire et prendre les mesures nécessaires pour récupérer l’accès.
- **Comptes de service** et **principaux de service**, tels que le compte de synchronisation Microsoft Entra Connect. Les comptes de service sont des comptes non interactifs qui ne sont pas liés à un utilisateur particulier. Ils sont généralement utilisés par les services principaux autorisant l’accès par programme aux applications, mais ils sont également utilisés pour se connecter aux systèmes à des fins administratives. Les comptes de service comme ceux-ci doivent être exclus, car l’authentification MFA ne peut pas être effectuée par programme. Les appels effectués par les principaux de service ne sont pas bloqués par l’accès conditionnel.
  - Si votre organisation utilise ces comptes dans des scripts ou du code, envisagez de les remplacer par des identités managées. Pour contourner provisoirement le problème, vous pouvez exclure ces comptes spécifiques de la stratégie de base.

- **Identités d’agent** : les agents IA inscrits dans l’ID microsoft Entra Agent peuvent être ciblés ou exclus des stratégies d’accès conditionnel, comme les principaux de service. Assurez-vous que tous les agents de confiance nécessitant un accès ininterrompu sont explicitement exclus, et examinez les politiques ciblant les agents ainsi que vos politiques d’identité de charge de travail.

### Conditions d'utilisation de l'accès conditionnel (CGU)

Vous pouvez créer des conditions d’utilisation (TOU) pour votre site dans les outils de gouvernance des identités (Identity Governance). Lancez l’application de gouvernance des identités et choisissez **Conditions d’utilisation** dans le menu. Vous devez fournir un fichier PDF incluant les conditions pour l’utilisateur. Vous pouvez configurer plusieurs règles, par exemple, déterminer quand les conditions expireront ou si l'utilisateur doit les ouvrir avant de les accepter. Une fois qu’une règle est créée, vous pouvez élaborer une règle conditionnelle personnalisée directement dans la gouvernance de l’identité. Vous pouvez également enregistrer les conditions et utiliser l’accès conditionnel dans Microsoft Entra ID. Pour créer des conditions d’utilisation, vous renseignez la boîte de dialogue ci-dessus.

La liaison du consentement (accepter les conditions d’utilisation avant l’accès) et l’accès conditionnel prennent de plus en plus d’ampleur. Les organisations ont la possibilité de contraindre un utilisateur à accepter les conditions d’utilisation. En outre, les organisations peuvent faire expirer le consentement donné, ou modifier les conditions d’utilisation et redemander l’accord de l’utilisateur.

Si vous souhaitez obtenir le consentement des utilisateurs avant qu’ils ne puissent accéder à certaines applications cloud de votre environnement, vous pouvez demander à ce qu’ils acceptent vos conditions d’utilisation. L’accès conditionnel Microsoft Entra vous fournit les éléments suivants :

- Une méthode simple pour configurer les conditions d'utilisation
- La possibilité d’exiger l’acceptation de vos conditions d’utilisation à l’aide d’une stratégie d’accès conditionnel


## Exercice - Implémenter des contrôles et des affectations de stratégie d’accès conditionnel

Dans cet exercice, créez une stratégie d’accès conditionnel.

L’accès conditionnel Microsoft Entra est une fonctionnalité avancée de Microsoft Entra ID vous permettant de spécifier des stratégies détaillées qui contrôlent les utilisateurs pouvant accéder à vos ressources. Avec l’accès conditionnel, vous pouvez protéger vos applications en limitant l’accès des utilisateurs en fonction d’éléments tels que les groupes, le type d’appareil, l’emplacement et le rôle.

1. Connectez-vous au [centre d’administration Microsoft Entra](https://entra.microsoft.com/) avec un compte administrateur général.
2. Ouvrez le menu du portail, puis sélectionnez **Identité**.
3. Ensuite, sélectionnez **Protection**.
4. Dans le panneau Sécurité, dans le volet de navigation de gauche, sélectionnez **Accès conditionnel**.
5. Dans le menu supérieur, sélectionnez **+Créer une stratégie**.
6. Dans la zone **Nom**, entrez **Accès conditionnel aux applications de test**. Il s’agit du nom utilisé dans le cadre de cet exercice. Vous pouvez choisir un autre nom si vous le souhaitez.
7. Sous **Affectations**, sélectionnez **Utilisateurs et groupes**.
8. Dans l’onglet inclure, activez la case à cocher **Utilisateurs et groupes**.
9. Dans le volet Sélectionner, sélectionnez votre compte administrateur, puis sélectionnez **Sélectionner**.
10. Sélectionnez **Applications ou actions cloud**.
11. Vérifiez que **Applications cloud** est sélectionné, puis sélectionnez **Sélectionner les applications**.
12. Dans le volet Sélectionner, sélectionnez **Mes applications**, puis sélectionnez **Sélectionner**.
13. Sélectionnez **Conditions**, puis sélectionnez **Emplacement**.
14. Sous **configurer**, sélectionnez **Oui**, puis sélectionnez **N’importe quel emplacement**.
15. Sous **Contrôles d’accès**, sélectionnez **Accorder**.
16. Dans le volet Accorder, sélectionnez **Bloquer l’accès**, puis sélectionnez **Sélectionner**.

Important

Cette stratégie est configurée pour l’exercice uniquement et est utilisée pour démontrer rapidement une stratégie d’accès conditionnel.

1. Sous **Activer la stratégie**, sélectionnez **Activé**, puis sélectionnez **Créer**.

### Tester la stratégie d’accès conditionnel

Vous devez tester vos stratégies d’accès conditionnel pour vous assurer qu’elles fonctionnent comme prévu.

1. Ouvrez un nouvel onglet de navigateur, puis accédez à **[https://myapps.microsoft.com](https://myapps.microsoft.com)**.
2. Vos informations d’identification doivent être transmises.
3. Vérifiez que vous ne parvenez pas à accéder à votre page Mes applications.       Remarque Si vous êtes connecté, fermez l’onglet, attendez 1 à 2 minutes, puis réessayez.
4. Fermez l’onglet et revenez au panneau Accès conditionnel.
5. Sélectionnez la stratégie **Accès conditionnel aux applications de test**.
6. Sous **Activer la stratégie**, sélectionnez **Désactivé**, puis sélectionnez **Enregistrer**.


## Tester et résoudre les problèmes des stratégies d’accès conditionnel

L’infrastructure d’accès conditionnel vous offre une grande flexibilité de configuration. Toutefois, une grande souplesse signifie également que vous devez examiner soigneusement chaque stratégie de configuration avant de la mettre en œuvre afin d’éviter des résultats indésirables. Dans ce contexte, prêtez une attention particulière à l’affectation d’ensembles complets comme **tous les utilisateurs / groupes / applications cloud**.

Les organisations doivent éviter les configurations suivantes :

**Pour tous les utilisateurs, toutes les applications cloud :**

- **Bloquer l’accès** : cette configuration bloque toute votre organisation.
- **Exiger un appareil joint à un domaine Microsoft Entra hybride** : cette stratégie de blocage de l’accès permet également de bloquer l’accès pour tous les utilisateurs de votre organisation, s’ils n’ont pas d’appareil à jointure hybride Microsoft Entra.
- **Exiger une stratégie de protection des applications** : cette stratégie de blocage d’accès peut également bloquer l’accès pour tous les utilisateurs de votre organisation si vous n’avez pas encore de stratégie Intune. Si vous êtes administrateur sans application cliente dotée d’une stratégie de protection des applications Intune, cette stratégie vous empêche de revenir aux portails comme Intune et Azure.

**Pour tous les utilisateurs, toutes les applications cloud, toutes les plates-formes d’appareils :**

- **Bloquer l’accès** : cette configuration bloque toute votre organisation.

### Interruption de connexion à l'accès conditionnel

Vous devez tout d’abord consulter le message d’erreur qui s’affiche. Pour les problèmes de connexion lors de l’utilisation d’un navigateur web, la page d’erreur elle-même contient des informations détaillées. Ces informations décrivent uniquement le problème et suggèrent une solution.

Dans l’erreur ci-dessus, le message indique que l’application est accessible uniquement à partir d’appareils ou d’applications clientes qui respectent la stratégie de gestion des appareils mobiles de l’entreprise. Dans le cas présent, l’application et l’appareil ne sont pas conformes à cette stratégie.

### Événements de connexion à Microsoft Entra

La deuxième méthode permettant d’obtenir des informations détaillées sur l’interruption de connexion consiste à passer en revue les événements de connexion Microsoft Entra pour savoir quelles stratégies d’accès conditionnel ont été appliquées et pourquoi.

Obtenez plus d’informations sur le problème en cliquant sur **Plus de détails** dans la page d’erreur initiale. Cliquez sur **Plus de détails** pour afficher des informations de dépannage utiles lors de la recherche de l’événement d’échec spécifique que l’utilisateur a vu dans les événements de connexion Microsoft Entra ou lors de l’ouverture d’un incident de support auprès de Microsoft.

Procédez comme suit pour trouver quelles stratégies d’accès conditionnel ont été appliquées et pourquoi :

1. Connectez-vous au Centre d’administration Microsoft Entra en tant qu’administrateur de sécurité ou lecteur général.
2. Accédez à **Identité – Surveillance et Santé**, puis **Connexions**.
3. Recherchez l'événement pour lequel vous souhaitez vous connecter. Ajoutez ou supprimez des filtres et des colonnes pour filtrer les informations inutiles.
  1. Ajoutez des filtres pour limiter l’étendue :
    1. ID de corrélation lorsque vous avez un événement spécifique à examiner.
    2. Accès conditionnel pour voir l’échec et la réussite de la stratégie. Pour limiter les résultats, restreignez votre filtre afin de n’afficher que les échecs.
    3. Nom d’utilisateur pour afficher des informations relatives à des utilisateurs spécifiques.
    4. Date limitée à la période en question.

4. Une fois que l’événement de connexion qui correspond à l’échec de connexion de l’utilisateur a été trouvé, sélectionnez l’onglet **Accès conditionnel**. Cet onglet affiche la ou les stratégies spécifiques qui ont abouti à l’interruption de la connexion.
  1. Les informations de l’onglet **Dépannage et support** indiquent clairement pourquoi une connexion a échoué, par exemple un appareil ne respectant pas les exigences de conformité.
  2. Pour approfondir vos recherches, explorez la configuration des stratégies en cliquant sur Nom de la stratégie. Cliquez sur Nom de la stratégie pour afficher l’interface utilisateur de configuration de la stratégie pour la stratégie sélectionnée à des fins de révision et de modification.
  3. L’utilisateur client et les détails sur l’appareil qui ont été utilisés pour l’évaluation de la stratégie d’accès conditionnel sont également disponibles dans les onglets **Informations de base**, **Emplacement**, **Informations sur l’appareil**, **Détails d’authentification** et **Détails supplémentaires** de l’événement de connexion.

#### Détails de la stratégie

La sélection des points de suspension sur le côté droit de la politique lors d’un événement de connexion fait apparaître les détails de la politique. Les administrateurs peuvent ainsi obtenir des informations supplémentaires sur la raison pour laquelle une stratégie a été correctement appliquée ou non.

Le côté gauche fournit les détails collectés lors de la connexion et le côté droit indique si ces détails répondent aux exigences des stratégies d’accès conditionnel appliquées. Les stratégies d’accès conditionnel s’appliquent uniquement lorsque toutes les conditions sont satisfaites ou non configurées.

Si les informations de l’événement ne suffisent pas à comprendre les résultats de la connexion ou à ajuster la stratégie pour obtenir les résultats souhaités, il est possible d’ouvrir un incident de support. Accédez à l’onglet **Dépannage et support** de cet événement de connexion, puis sélectionnez **Créer une demande de support**.

Lors de l’envoi de l’incident, fournissez l’ID de la demande, ainsi que l’heure et la date de l’événement de connexion dans les détails d’envoi de l’incident. Ces informations permettent au support Microsoft de trouver l’événement qui vous intéresse.


## Implémenter des contrôles d’application

Le contrôle d’application par accès conditionnel permet de superviser et de contrôler en temps réel les sessions et accès utilisateur aux applications en fonction des stratégies d’accès et de session. Les stratégies d’accès et de session s’utilisent sur le portail Microsoft Defender for Cloud Apps pour affiner davantage les filtres et définir les mesures à prendre pour un utilisateur.

### Contrôle d‘application par accès conditionnel

Le contrôle d’application par accès conditionnel utilise une architecture de proxy inverse et il est intégré de manière unique à l’accès conditionnel Microsoft Entra. L’accès conditionnel Microsoft Entra vous permet d’appliquer des contrôles d’accès aux applications de votre organisation en fonction de certaines conditions. Les conditions définissent à qui (utilisateur ou groupe d’utilisateurs), à quoi (quelles applications cloud) et où (quels emplacements et réseaux) s’applique une stratégie d’accès conditionnel. Une fois que vous avez déterminé les conditions, vous pouvez router les utilisateurs vers Microsoft Defender for Cloud Apps afin de protéger les données avec un contrôle d’application par accès conditionnel en appliquant des contrôles d’accès et de session.

Avec les stratégies d’accès et de session, vous pouvez :

- **Empêcher l’exfiltration de données :** vous pouvez bloquer le téléchargement, les opérations couper et copier, ainsi que l’impression des documents à contenu sensible sur les appareils non managés, par exemple.
- **Protéger au téléchargement :** au lieu de bloquer le téléchargement de documents à contenu sensible, vous pouvez exiger l’étiquetage et la protection des documents avec Azure Information Protection. Cette action garantit que le document est protégé et que l’accès utilisateur est limité dans une session potentiellement risquée.
- **Empêcher le chargement de fichiers sans étiquette :** avant qu’un fichier à contenu sensible puisse être chargé, distribué et utilisé par d’autres personnes, il est important de s’assurer que le fichier est configuré avec l’étiquette et la protection appropriées. Vous pouvez bloquer le chargement des fichiers sans étiquette qui ont du contenu sensible tant que l’utilisateur n’a pas classifié leur contenu.
- **Vérifier la conformité des sessions utilisateur :** les utilisateurs à risque font l’objet d’une supervision quand ils se connectent à des applications et les actions qu’ils effectuent durant la session sont journalisées. Vous pouvez examiner et analyser le comportement des utilisateurs pour comprendre où et dans quelles conditions les stratégies de session doivent être appliquées à l’avenir.
- **Bloquer l’accès :** vous pouvez bloquer l’accès de façon précise pour des applications et des utilisateurs spécifiques en fonction de plusieurs facteurs de risque. Par exemple, vous pouvez les bloquer s’ils utilisent des certificats clients comme moyen de gérer les appareils.
- **Bloquer des activités personnalisées :** certaines applications ont des scénarios uniques qui comportent un risque, par exemple, l’envoi de messages avec du contenu sensible dans des applications, telles que Microsoft Teams ou Slack. Dans ce genre de scénarios, vous pouvez analyser les messages pour rechercher la présence de contenu sensible et les bloquer en temps réel.

### Procédure : Exiger une stratégie de protection des applications et une application cliente approuvée pour accéder aux applications cloud avec l'accès conditionnel

Les appareils mobiles sont régulièrement utilisés pour effectuer des tâches aussi bien personnelles que professionnelles. Tout en veillant à ce que le personnel puisse être productif, les organisations veulent également empêcher la perte de données depuis des applications potentiellement non sécurisées. Avec l’accès conditionnel, les organisations peuvent limiter l’accès aux seules applications clientes approuvées (avec une authentification moderne).

Cette section présente deux scénarios permettant de configurer des stratégies d’accès conditionnel pour des ressources comme Microsoft 365, Exchange Online et SharePoint Online.

Remarque

Pour exiger des applications clientes approuvées pour les appareils iOS et Android, ces derniers doivent d’abord s’inscrire auprès de Microsoft Entra ID.

#### Scénario 1 : Les applications Microsoft 365 demandent une application cliente approuvée

Dans ce scénario, Contoso a décidé que les utilisateurs se servant d’appareils mobiles peuvent accéder à tous les services Microsoft 365, à condition qu’ils utilisent des applications clientes approuvées, comme Outlook Mobile, OneDrive et Microsoft Teams. Tous les utilisateurs de Contoso se connectent déjà à l’aide d’informations d’identification Microsoft Entra et disposent de licences qui leur sont attribuées, notamment Microsoft Entra ID Premium P1 ou P2 et Microsoft Intune.

Les organisations doivent effectuer les trois étapes suivantes pour exiger l’utilisation d’une application cliente approuvée sur des appareils mobiles.

**Étape 1 : Stratégie pour les clients à authentification moderne basés sur Android et iOS, nécessitant l’utilisation d’une application cliente approuvée lors de l’accès à Exchange Online**

1. Connectez-vous au **Centre d’administration Microsoft Entra** en tant qu’administrateur de sécurité ou administrateur de l’accès conditionnel.
2. Accédez à **Identity**, puis **Protection**, enfin à **Accès conditionnel**.
3. Sélectionnez **+Créer une stratégie**.
4. Donnez un nom à votre stratégie. Nous recommandons aux organisations de créer une norme explicite pour les noms de leurs stratégies.
5. Sous **Affectations**, sélectionnez **Utilisateurs et groupes**.
  1. Sous **Inclure**, sélectionnez **Tous les utilisateurs** ou les **Utilisateurs et groupes** particuliers auxquels vous souhaitez appliquer cette stratégie.
  2. Sélectionnez **Terminé**.

6. Sous **Applications cloud ou actions**, puis **Inclure**, sélectionnez **Office 365**.
7. Sous **Conditions**, sélectionnez **Plateformes d’appareils**.
  1. Définissez **Configurer** sur **Oui**.
  2. Incluez **Android** et **iOS**.

8. Sous **Conditions**, sélectionnez **Applications clientes (préversion)** .
9. Définissez **Configurer** sur **Oui**.
10. Sélectionnez **Applications mobiles et clients de bureau** et **Clients de l’authentification moderne**.
11. Sous **Contrôles d’accès**, puis **Octroyer**, sélectionnez **Accorder l’accès**, **Demander l’approbation de l’application cliente**, puis sélectionnez **Sélectionner**.
12. Confirmez vos paramètres et réglez **Activer la stratégie** sur **Activé**.
13. Sélectionnez **Créer** pour créer et activer votre stratégie.

**Étape 2 : Configurer une stratégie d’accès conditionnel Microsoft Entra pour Exchange Online avec ActiveSync (EAS).**

1. Accédez à **Identity**, puis **Protection**, enfin à **Accès conditionnel**.
2. Sélectionnez **+Créer une stratégie**.
3. Donnez un nom à votre stratégie. Nous recommandons aux organisations de créer une norme explicite pour les noms de leurs stratégies.
4. Sous **Affectations**, sélectionnez **Utilisateurs et groupes**.
  1. Sous **Inclure**, sélectionnez **Tous les utilisateurs** ou les **Utilisateurs et groupes** particuliers auxquels vous souhaitez appliquer cette stratégie.
  2. Sélectionnez **Terminé**.

5. Sous **Applications cloud ou actions**, puis **Inclure**, sélectionnez **Office 365 Exchange Online**.
6. Sous **Conditions** :
  1. **Applications clientes (préversion)** :
    1. Définissez **Configurer** sur **Oui**.
    2. Sélectionnez **Applications mobiles et clients de bureau** et **Clients Exchange ActiveSync**.

7. Sous **Contrôles d’accès**, puis **Octroyer**, sélectionnez **Accorder l’accès**, **Demander l’approbation de l’application cliente**, puis sélectionnez **Sélectionner**.
8. Confirmez vos paramètres et réglez **Activer la stratégie** sur **Activé**.
9. Sélectionnez **Créer** pour créer et activer votre stratégie.

**Étape 3 : Configurer la stratégie Intune App Protection pour les applications clientes iOS et Android**

Consultez l’article [Guide pratique pour créer et assigner des stratégies de protection d’application](https://learn.microsoft.com/fr-fr/mem/intune/apps/app-protection-policies) afin de connaître les étapes de création des stratégies de protection d’application pour Android et iOS.

#### Scénario 2 : Exchange Online et SharePoint Online demandent une application cliente approuvée

Dans ce scénario, Contoso a décidé que les utilisateurs peuvent uniquement accéder aux e-mails et aux données SharePoint sur des appareils mobiles, à condition qu’ils utilisent une application cliente approuvée comme Outlook Mobile. Tous les utilisateurs de Contoso se connectent déjà à l’aide d’informations d’identification Microsoft Entra et disposent de licences qui leur sont attribuées, notamment Microsoft Entra ID Premium P1 ou P2 et Microsoft Intune.

Les organisations doivent effectuer les trois étapes suivantes pour exiger l’utilisation d’une application cliente approuvée sur des appareils mobiles et des clients ActiveSync.

**Étape 1 : Stratégie pour les clients à authentification moderne basés sur Android et iOS, nécessitant l’utilisation d’une application cliente approuvée lors de l’accès à Exchange Online et SharePoint Online**

1. Connectez-vous au **Centre d’administration Microsoft Entra** en tant qu’administrateur de sécurité ou administrateur de l’accès conditionnel.
2. Accédez à **Identity**, puis **Protection**, enfin à **Accès conditionnel**.
3. Sélectionnez **Nouvelle stratégie**.
4. Donnez un nom à votre stratégie. Nous recommandons aux organisations de créer une norme explicite pour les noms de leurs stratégies.
5. Sous **Affectations**, sélectionnez **Utilisateurs et groupes**.
  1. Sous **Inclure**, sélectionnez **Tous les utilisateurs** ou les **Utilisateurs et groupes** particuliers auxquels vous souhaitez appliquer cette stratégie.
  2. Sélectionnez **Terminé**.

6. Sous **Applications cloud ou actions** puis **Inclure**, sélectionnez **Office 365 Exchange Online** et **Office 365 SharePoint Online**.
7. Sous **Conditions**, sélectionnez **Plateformes d’appareils**.
  1. Définissez **Configurer** sur **Oui**.
  2. Incluez **Android** et **iOS**.

8. Sous **Conditions**, sélectionnez **Applications clientes (préversion)** .
  1. Définissez **Configurer** sur **Oui**.
  2. Sélectionnez **Applications mobiles et clients de bureau** et **Clients de l’authentification moderne**.

9. Sous **Contrôles d’accès**, puis **Octroyer**, sélectionnez **Accorder l’accès**, **Demander l’approbation de l’application cliente**, puis sélectionnez **Sélectionner**.
10. Confirmez vos paramètres et réglez **Activer la stratégie** sur **Activé**.
11. Sélectionnez **Créer** pour créer et activer votre stratégie.

**Étape 2 : Stratégie pour les clients Exchange ActiveSync nécessitant l’utilisation d’une application cliente approuvée**

1. Accédez à **Identity**, puis **Protection**, enfin à **Accès conditionnel**.
2. Sélectionnez **Nouvelle stratégie**.
3. Donnez un nom à votre stratégie. Nous recommandons aux organisations de créer une norme explicite pour les noms de leurs stratégies.
4. Sous **Affectations**, sélectionnez **Utilisateurs et groupes**.
  1. Sous **Inclure**, sélectionnez **Tous les utilisateurs** ou les **Utilisateurs et groupes** particuliers auxquels vous souhaitez appliquer cette stratégie.
  2. Sélectionnez **Terminé**.

5. Sous **Applications cloud ou actions**, puis **Inclure**, sélectionnez **Office 365 Exchange Online**.
6. Sous **Conditions** :
7. **Applications clientes (préversion)** :
  1. Définissez **Configurer** sur **Oui**.
  2. Sélectionnez **Applications mobiles et clients de bureau** et **Clients Exchange ActiveSync**.

8. Sous **Contrôles d’accès**, puis **Octroyer**, sélectionnez **Accorder l’accès**, **Demander l’approbation de l’application cliente**, puis sélectionnez **Sélectionner**.
9. Confirmez vos paramètres et réglez **Activer la stratégie** sur **Activé**.
10. Sélectionnez **Créer** pour créer et activer votre stratégie.

**Étape 3 : Configurer la stratégie Intune App Protection pour les applications clientes iOS et Android**

Consultez l’article [Guide pratique pour créer et assigner des stratégies de protection d’application](https://learn.microsoft.com/fr-fr/mem/intune/apps/app-protection-policies) afin de connaître les étapes de création des stratégies de protection d’application pour Android et iOS.

### Vue d’ensemble des stratégies de protection des applications

Les stratégies de protection des applications (APP) sont des règles qui garantissent que les données d’une organisation sont sécurisées ou restent dans une application managée. Une stratégie peut être une règle qui est appliquée lorsque l’utilisateur tente d’accéder à des données « d’entreprise » ou de les déplacer, ou s’il tente un ensemble d’actions interdites ou surveillées lorsqu’il se trouve dans l’application. Une application gérée est une application à laquelle des stratégies de protection sont appliquées et elle peut être gérée par Intune.

Les stratégies de protection des applications de gestion des applications mobiles (GAM) vous permettent de gérer et de protéger les données de votre organisation au sein d’une application. Avec **MAM sans inscription** (MAM-WE, without enrollment), une application professionnelle ou scolaire contenant des données sensibles peut être gérée sur pratiquement tout appareil, notamment les appareils personnels dans des scénarios BYOD (**Apportez votre propre appareil**). Plusieurs applications de productivité, telles que les applications Microsoft Office, peuvent être gérées par la MAM Intune.

#### Comment protéger les données d’application

Vos employés utilisent des appareils mobiles pour des tâches à la fois personnelles et professionnelles. Tout en veillant à ce que vos employés soient productifs, vous voulez éviter toute perte de données, qu’elle soit intentionnelle ou non. Vous souhaiterez également protéger les données d’entreprise accessibles à partir d’appareils que vous ne gérez pas.

Vous pouvez utiliser des stratégies de protection des applications Intune **indépendamment de toute solution de gestion des appareils mobiles (GAM)** . Cette indépendance vous permet de protéger les données de votre entreprise avec ou sans l’inscription des appareils dans une solution de gestion des appareils. En implémentant des **stratégies au niveau de l’application**, vous pouvez restreindre l’accès aux ressources d’entreprise et conserver les données au sein de votre département informatique.

#### Stratégies de protection des applications sur les appareils

Vous pouvez configurer des stratégies de protection des applications pour les applications qui s’exécutent sur des appareils qui sont :

- **Inscrits dans Microsoft Intune :** ces appareils appartiennent généralement à l’entreprise.
- **Inscrits dans une solution de gestion des périphériques mobiles tierce :** ces appareils appartiennent généralement à l’entreprise.  Remarque Les stratégies de gestion des applications mobiles ne doivent pas être utilisées avec des solutions de gestion des applications mobiles tierces ni des solutions de conteneur sécurisé.
- **Non inscrits dans une solution de gestion des périphériques mobiles :** Ces appareils sont généralement la propriété d’employés et ne sont pas gérés ou inscrits dans Intune ou d’autres solutions GPM.  Important Vous pouvez créer des stratégies de gestion des applications mobiles pour les applications mobiles Office qui se connectent aux services Microsoft 365. Vous pouvez aussi protéger l’accès aux boîtes aux lettres locales Exchange en créant des stratégies de protection d’application Intune pour Outlook sous iOS/iPadOS et Android avec authentification moderne hybride. Avant d’utiliser cette fonctionnalité, vérifiez que vous répondez aux exigences relatives à Outlook pour iOS/iPadOS et Android. Les stratégies de protection d’applications ne sont pas prises en charge pour les autres applications qui se connectent à des services Exchange ou SharePoint sur site.

#### Avantages de l’utilisation de stratégies de protection des applications

Les principaux avantages de l’utilisation de stratégies de protection des applications sont les suivants :

- **Protection des données de votre entreprise au niveau de l’application.** Étant donné que la gestion des applications mobiles ne nécessite pas de gestion des appareils, vous pouvez protéger les données d’entreprise à la fois sur les appareils gérés et non gérés. La gestion est centrée autour de l’identité de l’utilisateur, ce qui supprime la nécessité de gérer les appareils.
- **La productivité des utilisateurs finaux n’est pas affectée et les stratégies ne s’appliquent pas en cas d’utilisation de l’application dans un contexte personnel.** Les stratégies sont appliquées uniquement dans un contexte professionnel, ce qui vous donne la possibilité de protéger les données d’entreprise sans toucher aux données personnelles.
- **Les stratégies de protection des applications permettent de s’assurer que des protections de la couche application sont en place.** Par exemple, vous pouvez :
  - Exiger un code PIN pour ouvrir une application dans un contexte de travail
  - Contrôler le partage des données entre les applications
  - Empêcher l’enregistrement des données d’applications d’entreprise dans un emplacement de stockage personnel

- **La Gestion des appareils mobiles (MDM), en plus de la gestion des applications mobiles (MAM), assure que l'appareil est protégé**. Par exemple, vous pouvez demander un code confidentiel pour accéder à l’appareil ou déployer des applications gérées sur l’appareil. Vous pouvez également déployer des applications sur des appareils via votre solution de gestion des appareils mobiles pour mieux contrôler la gestion des applications.

Il existe d'autres avantages à utiliser la gestion des périphériques mobiles avec des stratégies de protection des applications, et les entreprises peuvent utiliser simultanément des stratégies de protection des applications avec et sans gestion des périphériques mobiles. Considérons, par exemple, un employé qui utilise un téléphone fourni par l’entreprise et sa tablette personnelle. Le téléphone de l’entreprise est inscrit dans la gestion des périphériques mobiles et protégé par des stratégies de protection des applications, tandis que l’appareil personnel est protégé uniquement par des stratégies de protection des applications.

Si vous appliquez une stratégie de gestion MAM à l’utilisateur sans définir l’état de l’appareil, l’utilisateur reçoit la stratégie à la fois sur l’appareil BYOD et sur l’appareil géré par Intune. Il est également possible d’appliquer une stratégie de gestion MAM en fonction de l’état géré. Si vous créez une stratégie de protection d’applications, sélectionnez **Non** à côté de **Cibler tous les types d’application**. Ensuite, choisissez entre les deux solutions suivantes :

- Appliquer une stratégie de gestion MAM moins stricte aux appareils gérés par Intune et une autre plus stricte aux appareils non inscrits à la gestion MDM.
- Appliquer une stratégie de gestion MAM aux appareils non inscrits exclusivement.


## Implémenter la gestion des sessions et l’évaluation continue de l’accès

Dans les déploiements complexes, les organisations peuvent avoir besoin de limiter les sessions d’authentification. Certains scénarios peuvent inclure les éléments suivants :

- L’accès aux ressources à partir d’un appareil non géré ou partagé.
- L’accès à des informations sensibles depuis un réseau externe.
- Priorité élevée ou utilisateurs exécutifs.
- Des applications métier critiques.

Les contrôles d’accès conditionnel permettent de créer des stratégies qui ciblent des cas d’usage particuliers au sein de votre organisation, sans affecter tous les utilisateurs.

Avant de plonger dans les détails sur la façon de configurer la stratégie, examinons la configuration par défaut.

### Fréquence de connexion de l’utilisateur

La fréquence de connexion définit la durée à l’issue de laquelle un utilisateur est invité à se reconnecter lorsqu’il tente d’accéder à une ressource.

La configuration par défaut de Microsoft Entra ID pour la fréquence de connexion utilisateur est une fenêtre dynamique de 90 jours. Demander des informations d’identification aux utilisateurs semble souvent une chose sensée à faire, mais celle-ci peut avoir l’effet inverse que celui prévu : les utilisateurs qui sont habitués à entrer leurs informations d’identification machinalement peuvent involontairement les fournir à une invite de demande d’informations d’identification malveillante.

Il peut paraître alarmant de ne pas demander à un utilisateur de se reconnecter, en réalité toute violation des stratégies informatiques révoquera la session. Certains exemples incluent une modification de mot de passe, un appareil non conforme ou une désactivation de compte. Vous pouvez aussi explicitement révoquer les sessions des utilisateurs avec PowerShell. La configuration par défaut de l’ID Microsoft Entra descend à « ne pas demander aux utilisateurs de fournir leurs informations d’identification si la posture de sécurité de leurs sessions n’a pas changé ».

Le paramètre de fréquence de connexion fonctionne avec les applications qui ont implémenté les protocoles OAUTH2 ou OIDC conformément aux standards. La plupart des applications pour Windows, Mac et mobile, y compris les applications web suivantes, sont conformes au paramètre.

- Word, Excel, PowerPoint en ligne
- OneNote en ligne
- Office.com
- Portail d’administration Microsoft 365
- Échange en ligne
- SharePoint et OneDrive
- Client web Teams
- Dynamics CRM en ligne
- Portail Azure

Le paramètre de fréquence de connexion fonctionne également avec les applications SAML, à condition que celles-ci ne suppriment pas leurs propres cookies et qu’elles soient régulièrement redirigées vers Microsoft Entra ID pour l’authentification.

#### Fréquence de connexion des utilisateurs et authentification multifacteur

La fréquence de connexion ne s’appliquait qu’à l’authentification au premier facteur de l’authentification sur les appareils qui étaient joints à Microsoft Entra, avec jointure hybride Microsoft Entra et inscrits auprès de Microsoft Entra. Il n'y avait pas de moyen facile pour nos clients de renforcer l'authentification multifacteur (MFA) sur ces appareils. Conformément aux commentaires des clients, la fréquence de connexion s'appliquera également à l'authentification multifacteur.

![Diagramme du processus d’authentification multifacteur avec fréquence de connexion.](https://learn.microsoft.com../../wwl-sci/plan-implement-administer-conditional-access/media/conditional-access-flow-chart.png)

#### Fréquence de connexion des utilisateurs et identités des appareils

Si vous avez des appareils joints à Microsoft Entra, à jointure hybride Microsoft Entra ou inscrits auprès de Microsoft Entra, quand un utilisateur déverrouille son appareil ou se connecte de façon interactive, cet événement satisfait également à la stratégie de fréquence de connexion. Dans les deux exemples suivants, la fréquence de connexion des utilisateurs est définie sur une heure :

Exemple 1 :

- À 00:00, un utilisateur se connecte à son appareil Windows 10 joint à Microsoft Entra et commence à travailler sur un document stocké sur SharePoint Online.
- L’utilisateur continue à travailler au même document sur son appareil pendant une heure.
- À 01:00, l’utilisateur est invité à se reconnecter en fonction de la fréquence de connexion spécifiée dans la stratégie d’accès conditionnel configurée par son administrateur.

Exemple 2 :

- À 00:00, un utilisateur se connecte à son appareil Windows 10 joint à Microsoft Entra et commence à travailler sur un document stocké sur SharePoint Online.
- À 00:30, l’utilisateur se lève et fait une pause en bloquant son appareil.
- À 00:45, l’utilisateur revient de sa pause et déverrouille l’appareil.
- À 01:45, l’utilisateur est invité à se reconnecter en fonction de la fréquence de connexion spécifiée dans la stratégie d’accès conditionnel configurée par son administrateur, car la dernière connexion s’est faite à 00:45.

### Persistance des sessions de navigation

Une session de navigateur persistante permet aux utilisateurs de rester connectés après la fermeture et la réouverture de la fenêtre du navigateur. L’ID Microsoft Entra par défaut pour la persistance de session de navigateur permet aux utilisateurs sur les appareils personnels de choisir s’il faut conserver la session en affichant un « Rester connecté ? » après une authentification réussie.

### Vérification

Utilisez l’outil What-If (Scénarios) pour simuler une connexion de l’utilisateur vers l’application cible et d’autres conditions en fonction de la configuration de votre stratégie. Les contrôles de gestion de session d’authentification s’affichent dans le résultat de l’outil.

### Déploiement de stratégie

Pour vous assurer que votre stratégie fonctionne comme prévu, la meilleure pratique recommandée consiste à la tester avant de la déployer en production. Dans l’idéal, utilisez un locataire de test pour vérifier si votre nouvelle stratégie fonctionne comme prévu.

### Évaluation continue de l’accès (CAE)

L’expiration et l’actualisation des jetons sont un mécanisme standard du secteur. Lorsqu’une application cliente telle qu’Outlook se connecte à un service comme Exchange Online, les demandes d’API sont autorisées à l’aide de jetons d’accès OAuth 2.0. Par défaut, ces jetons d’accès sont valides pendant une heure. Quand ils expirent, le client est redirigé vers Microsoft Entra ID pour les actualiser. Cette période d’actualisation offre la possibilité de réévaluer les stratégies d’accès utilisateur. Par exemple, il est possible de choisir de ne pas actualiser le jeton en raison d’une stratégie d’accès conditionnel ou parce que l’utilisateur a été désactivé dans l’annuaire.

Cependant, il existe un décalage entre le changement des conditions pour un utilisateur et le moment où les modifications de stratégie sont appliquées. Une réponse en temps utile aux violations de stratégie ou à d’autres problèmes de sécurité nécessite vraiment une « conversation » entre l’émetteur du jeton et la partie de confiance (application compatible). Cette conversation bidirectionnelle nous offre deux capacités importantes. La partie de confiance peut voir quand les propriétés changent, comme l’emplacement réseau, et comment indiquer à l’émetteur du jeton. Et l’émetteur du jeton peut demander à la partie de confiance d’arrêter de respecter les jetons pour un utilisateur donné en raison d’une compromission ou d’une désactivation de compte ou d’autres soucis. Le mécanisme de cette conversation est l’évaluation continue de l’accès.

#### Avantages

L’évaluation continue de l’accès offre plusieurs avantages clés.

- Démission d’utilisateur ou modification/réinitialisation du mot de passe : La révocation de session utilisateur sera appliquée en quasi-temps réel.
- Changement d’emplacement réseau : les stratégies d’emplacement d’accès conditionnel seront appliquées en quasi-temps réel.
- L’exportation de jetons vers une machine en dehors d’un réseau approuvé peut être évitée avec des stratégies d’emplacement d’accès conditionnel.

#### Flux du processus d’évaluation et de révocation

![Diagramme du flux de processus lorsqu’un jeton d’accès est révoqué et qu’un client doit réverifier l’accès.](https://learn.microsoft.com../../wwl-sci/plan-implement-administer-conditional-access/media/user-revocation-event-flow.png)

1. Un client compatible avec l’évaluation continue de l’accès (CAE) présente à Microsoft Entra ID des informations d’identification ou un jeton d’actualisation, demandant un jeton d’accès pour une certaine ressource.
2. Un jeton d’accès est retourné au client avec d’autres artefacts.
3. Un administrateur révoque explicitement tous les jetons d’actualisation d’un utilisateur. Un événement de révocation va être envoyé au fournisseur de ressources à partir de Microsoft Entra ID.
4. Un jeton d’accès est présenté au fournisseur de ressources. Le fournisseur de ressources évalue la validité du jeton et vérifie s’il existe un événement de révocation pour l’utilisateur. Le fournisseur de ressources utilise ces informations pour décider d’accorder ou non l’accès à la ressource.
5. Dans le cas de ce diagramme, le fournisseur de ressources refuse l’accès et renvoie une contestation de revendication 401+ au client.
6. Le client compatible avec l’EAC comprend la contestation de revendication 401+. Il contourne les caches et revient à l’étape 1, en renvoyant à Microsoft Entra ID son jeton d’actualisation avec la contestation de revendication. Microsoft Entra ID réévalue ensuite toutes les conditions et invite l’utilisateur à se réauthentifier dans ce cas.


## Exercice - Configurer des contrôles de session d’authentification

Dans cet exercice, vous allez configurer les contrôles de fréquence de connexion à l’aide d’une stratégie d’accès conditionnel.

1. Connectez-vous au [Centre d’administration Microsoft Entra](https://entra.microsoft.com/) à l’aide d’un compte Administrateur.
2. Ouvrez le menu du portail, puis sélectionnez **Identité**.
3. Dans le menu Identité, sélectionnez ensuite **Protection**.
4. Dans le menu Protection, sélectionnez **Accès conditionnel**.
5. Dans le menu supérieur, sélectionnez **Nouvelle stratégie**.

1. Dans la zone **Nom**, entrez **Fréquence de connexion**.
2. Sous **Affectations**, sélectionnez **Utilisateurs et groupes**.
3. Dans l’onglet inclure, activez la case à cocher **Utilisateurs et groupes**.
4. Dans le volet Sélectionner, sélectionnez votre compte administrateur, puis sélectionnez **Sélectionner**.
5. Sélectionnez **Applications ou actions cloud**.
6. Vérifiez que **Applications cloud** est sélectionné, puis sélectionnez **Sélectionner les applications**.
7. Dans le volet Sélectionner, sélectionnez **Office 365**, puis sélectionnez **Sélectionner**.
8. Sous **Contrôles d’accès**, sélectionnez **Session**.
9. Dans le volet **Session**, sélectionnez **Fréquence de connexion**.
10. Dans la zone de valeur, entrez **30**.
11. Sélectionnez le menu des unités, sélectionnez **Jours**, puis sélectionnez **Sélectionner**.
12. Sous **Activer la stratégie**, sélectionnez **Rapport uniquement**, puis sélectionnez **Créer**.

## Agent d’optimisation de l’accès conditionnel Microsoft Entra

L’agent d’optimisation de l’accès conditionnel vous permet de vous assurer que tous les utilisateurs sont protégés par la stratégie. Il recommande des stratégies et des modifications basées sur les meilleures pratiques alignées sur l’apprentissage Confiance Zéro et Microsoft.

L’agent d’optimisation de l’accès conditionnel évalue les stratégies telles que l’authentification multifacteur (MFA). L’agent applique des contrôles basés sur les appareils (conformité des appareils, stratégies de protection des applications et appareils joints à un domaine). Enfin, l’agent peut aider à bloquer l’authentification héritée et le flux de code de l’appareil.

L’agent évalue également toutes les stratégies activées existantes pour proposer une consolidation potentielle de stratégies similaires.

#### Condition requise pour utiliser l’agent d’optimisation de l’accès conditionnel

- Vous devez disposer au moins de la **licence Microsoft Entra ID P1**.
- Vous devez disposer **d’unités de calcul de sécurité (SCU)** disponibles.
- Pour activer l’agent la première fois, vous avez besoin du rôle Administrateur de sécurité ou supérieur.
- Vous pouvez attribuer l’accès à Sécurité Copilot aux Administrateurs de l’accès conditionnel.
  - Pour plus d’informations, consultez la section Attribuer l'accès à Security Copilot.

- Les contrôles basés sur les appareils nécessitent **des licences Microsoft Intune**.

#### Fonctionnalités clés de l’agent d’optimisation de l’accès conditionnel

L’agent d’optimisation de l’accès conditionnel analyse votre client à la recherche de nouveaux utilisateurs et applications et détermine si les politiques d’accès conditionnel sont applicables. Les fonctionnalités clés sont les suivantes :

| Caractéristique | Descriptif |
|---|---|
| Exiger l’authentification multifacteur | L’agent identifie les utilisateurs qui ne sont pas couverts par une stratégie d’accès conditionnel qui requiert l’authentification multifacteur et qui peuvent mettre à jour la stratégie. |
| Exiger des contrôles basés sur des appareils | L’agent peut appliquer des contrôles basés sur des appareils, tels que la conformité des appareils, les stratégies de protection des applications et les appareils joints à un domaine. |
| Bloquer l’authentification héritée | Les comptes d’utilisateur disposant d’une authentification héritée ne peuvent pas se connecter. |
| Consolidation des stratégies | L’agent analyse votre stratégie et identifie les paramètres qui se chevauchent. Par exemple, si vous avez plusieurs stratégies qui ont les mêmes contrôles d’octroi, l’agent suggère de consolider ces stratégies en une seule. |
| Bloquer le flux de code de l’appareil | L’agent recherche une stratégie bloquant l’authentification de flux de code d’appareil. |
| Correction en un clic | Lorsque l’agent identifie une suggestion, vous pouvez sélectionner Appliquer une suggestion pour que l’agent met à jour la stratégie associée en appuyant sur un bouton. |

### Donner à l’agent d’optimisation de l’accès conditionnel une tentative

[](https://microsoftlearning.github.io/click-throughs/docs/IG/interactive_guide_explore_conditional_access_optimization_agent_web/story.html)


## Évaluation du module

Choisissez la meilleure réponse à chacune des questions ci-dessous.

### Vérifiez vos connaissances


## Récapitulatif et ressources

À l’issue de ce module, vous pourrez :

- Planifier et implémenter les paramètres de sécurité par défaut.
- planifier vos stratégies d’accès conditionnel.
- Implémenter les contrôles et les paramètres de la stratégie d’accès conditionnel (ciblage, applications et conditions).
- Tester et résoudre les problèmes des stratégies d’accès conditionnel.
- Implémenter des contrôles d’application.
- Implémenter la gestion des sessions.
- Configurez l’évaluation continue de l’accès.

### Ressources

Pour en savoir plus sur la technologie de ce module, consultez les liens suivants vers la documentation :

- [Qu’est-ce que l’accès conditionnel ?](https://youtu.be/ffMAw2IVO7A)
- [Comment déployer l’accès conditionnel](https://youtu.be/c_izIRNJNuk)
- [Comment déployer des stratégies d’accès conditionnel pour les utilisateurs finaux](https://youtu.be/0_Fze7Zpyvc)
- [L’accès conditionnel et les contrôles d’appareil](https://youtu.be/NcONUf-jeS4)
- [Accès conditionnel avec l’authentification multifacteur Microsoft Entra](https://youtu.be/Tbc-SU97G-w)
- [Conditional Access in Enterprise Mobility + Security](https://youtu.be/A7IrxAH87wc) (Accès conditionnel dans Enterprise Mobility + Security)
- [Utilisation de la condition d’emplacement dans une stratégie d’accès conditionnel](https://learn.microsoft.com/fr-fr/entra/identity/conditional-access/howto-conditional-access-policy-location)
- [Utiliser des stratégies de conformité pour définir des règles pour les appareils que vous gérez avec Intune](https://learn.microsoft.com/fr-fr/mem/intune/fundamentals/deployment-plan-compliance-policies)
- [Présentation des paramètres de sécurité par défaut](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/introducing-security-defaults/ba-p/1061414)
- [Planifier un déploiement d’accès conditionnel](https://learn.microsoft.com/fr-fr/entra/identity/conditional-access/plan-conditional-access)
- [Évaluation continue de l’accès](https://learn.microsoft.com/fr-fr/entra/identity/conditional-access/concept-continuous-access-evaluation)
- [Accès conditionnel pour les identités d’agent (ID de Microsoft Entra Agent)](https://learn.microsoft.com/fr-fr/entra/identity/conditional-access/concept-conditional-access-policy-common)


---

# Gérer Microsoft Entra Identity Protection

_https://learn.microsoft.com/fr-fr/training/modules/manage-azure-active-directory-identity-protection/_


## Présentation

La protection de l’identité des utilisateurs en surveillant leur utilisation et leurs modèles de connexion garantit une solution cloud sécurisée. Découvrez comment concevoir et implémenter Microsoft Entra Identity Protection.

#### Visionner la vidéo

Dans cette vidéo, vous découvrirez une vue d'ensemble de Identity Protection, une caractéristique de Microsoft Entra ID. Vous découvrez différents types de détections, de risques et de stratégies de risque qui existent dans Identity Protection. La vidéo explique les avantages des stratégies de risque, les améliorations récentes de l’expérience utilisateur, les API puissantes, l’évaluation des risques améliorée et l’alignement global sur les utilisateurs à risque et les connexions risquées.

### Objectifs d’apprentissage

Dans ce module, vous allez :

- Passez en revue les principes fondamentaux de Identity Protection.
- Implémenter et gérer une stratégie de risque d’utilisateur.
- Implémenter et gérer des stratégies de risque de connexion.
- Implémenter et gérer la politique d’inscription de l’authentification multifacteur.
- Surveiller, examiner et corriger les utilisateurs à risque.
- Explorer Microsoft Defender pour l'Identité


## Passer en revue les principes fondamentaux de Identity Protection

La protection de l’identité est un service qui permet aux organisations d’afficher l'état de sécurité de n’importe quel compte. Les organisations peuvent accomplir trois tâches clés :

- Automatiser la détection et la correction des risques liés à l'identité
- Examiner les risques à l'aide des données disponibles sur le portail
- Exporter les données de détection des risques vers des utilitaires tiers pour une analyse plus approfondie

Gardez toujours à l'esprit que Microsoft Entra Identity Protection requiert une licence Microsoft Entra ID Premium P2 pour fonctionner. Les licences sont abordées plus en détail dans une unité ultérieure.

Identity Protection protège vos utilisateurs en appliquant les connaissances acquises par Microsoft auprès des organisations avec Microsoft Entra ID, dans l'espace grand public avec les comptes Microsoft et dans le domaine des jeux avec Xbox. Microsoft analyse 6 500 milliards de signaux par jour pour identifier les menaces et protéger les clients.

Les signaux générés par Identity Protection et transmis à celui-ci peuvent également être transmis à des outils tels que l'Accès conditionnel pour prendre des décisions en matière d'accès, ou renvoyés à un outil SIEM (Security Information and Event Management) pour un examen plus approfondi en fonction des stratégies appliquées par votre organisation.

### Détection d'événements à risque et solutions pour y remédier

Identity Protection identifie les risques selon les classifications suivantes :

| **Type de détection des risques** | **Description** |
|---|---|
| Adresse IP anonyme | Connexion à partir d'une adresse IP anonyme (par exemple : navigateur Tor, VPN anonymes). |
| Voyage inhabituel | Connexion à partir d’un emplacement inhabituel en fonction des connexions récentes de l’utilisateur. |
| Adresse IP malveillante | Connectez-vous à partir d’une adresse IP malveillante. |
| Propriétés de connexion inhabituelles | Connexion avec des propriétés inhabituelles pour l’utilisateur concerné. |
| Informations d’identification divulguées | Indique que les informations d’identification valides de l’utilisateur ont été divulguées. |
| Pulvérisation de mots de passe | Indique que plusieurs noms d’utilisateurs font l’objet d’une attaque par force brute unifiée avec des mots de passe courants. |
| Veille des menaces Microsoft Entra | Les sources de renseignements sur les menaces internes et externes de Microsoft ont identifié un modèle d’attaque connu. |
| Jeton anormal | Détecte des caractéristiques inhabituelles dans un jeton, telles qu’une durée de vie de jeton inhabituelle ou un jeton relecté à partir d’un emplacement inconnu. |
| Anomalie de l’émetteur du jeton | Détecte quand l’émetteur de jeton SAML pour le jeton SAML associé est potentiellement compromis. |
| Navigateur suspect | Détecte l’activité de connexion anormale sur plusieurs locataires à partir du même navigateur. |
| Adresse IP de l’intervenant de menace vérifiée | Détecte l’activité de connexion à partir d’adresses IP connues pour être associées à des acteurs de menace vérifiés. |
| Nouveau pays | Cette détection est découverte par Microsoft Defender pour les applications cloud (MDCA). |
| Activité depuis une adresse IP anonyme | Cette détection est découverte par MDCA. |
| Transfert de boîte de réception suspect | Cette détection est découverte par MDCA. |

### Autorisations

Identity Protection nécessite que les utilisateurs soient un lecteur de sécurité, un opérateur de sécurité, un administrateur de sécurité, un administrateur de lecteur général afin d’y accéder.

| **Rôle** | **Peut** | **Impossible de faire** |
|---|---|---|
| Administrateur de sécurité | Accès complet à Identity Protection | Réinitialiser un mot de passe pour un utilisateur |
| Opérateur de sécurité | Afficher tous les rapports "Identity Protection" et l’écran "Vue d’ensemble". Réduire le risque utilisateur, confirmer la connexion sécurisée, vérifier la compromission. | Configurer ou modifier les stratégies, Réinitialiser le mot de passe d’un utilisateur, Configurer des alertes |
| Lecteur de sécurité | Afficher tous les rapports Identity Protection et l’écran Vue d’ensemble | Configurer ou modifier les stratégies, Réinitialiser le mot de passe d’un utilisateur, Configurer des alertes, Envoyer des commentaires sur les détections |

Le rôle Opérateur de sécurité ne peut pas accéder au rapport des connexions risquées. Les administrateurs d’accès conditionnel peuvent également créer des stratégies qui prennent en compte le risque lié à la connexion en tant que condition.

### Conditions de licence :

L'utilisation de cette caractéristique requiert une licence Microsoft Entra ID Premium P2.

| **Fonctionnalité** | **Détails** | **Microsoft Entra ID (édition gratuite)/Microsoft 365 Apps** | **Microsoft Entra ID Premium P1** | **Microsoft Entra ID Premium P2** |
|---|---|---|---|---|
| Stratégies de risque | Stratégie de risque utilisateur (via Identity Protection) | Non | Non | Oui |
| Stratégies de risque | Stratégie de risque de connexion (via Identity Protection ou l’accès conditionnel) | Non | Non | Oui |
| Rapports de sécurité | Vue d’ensemble | Non | Non | Oui |
| Rapports de sécurité | Utilisateurs à risque | Informations limitées. Seuls les utilisateurs présentant un risque moyen ou élevé sont affichés. Aucun tiroir de détails ou historique des risques. | Informations limitées. Seuls les utilisateurs présentant un risque moyen ou élevé sont affichés. Aucun tiroir de détails ou historique des risques. | Accès total |
| Rapports de sécurité | Connexions risquées | Informations limitées. Aucun détail sur les risques ou niveau de risque n’est affiché. | Informations limitées. Aucun détail sur les risques ou niveau de risque n’est affiché. | Accès total |
| Rapports de sécurité | Détections de risques | Non | Informations limitées. Aucun tiroir de détails. | Accès total |
| Avis | Alertes Utilisateurs à risque détectés | Non | Non | Oui |
| Avis | Synthèse hebdomadaire | Non | Non | Oui |
|   | Stratégie d’inscription MFA | Non | Non | Oui |


## Implémenter et gérer une stratégie de risque d’utilisateur

Il existe deux stratégies de risque qui peuvent être activées dans l’annuaire :

- **Stratégie de connexion à risque** : La stratégie de connexion à risque détecte les actions suspectes qui accompagnent la connexion. Elle se concentre sur l'activité de connexion elle-même et analyse la probabilité que la connexion ait été effectuée par une personne autre que l'utilisateur.
- **Stratégie d’utilisateur à risque** : La stratégie d’utilisateur à risque détecte la probabilité de compromission d’un compte d’utilisateur en détectant les événements à risque atypiques du comportement de l’utilisateur.

Ensemble, les deux stratégies automatisent la réponse aux détections de risques dans votre environnement et permettent aux utilisateurs de résoudre eux-mêmes des problèmes quand des risques sont détectés.

#### Regarder la vidéo

Dans cette vidéo, vous apprendrez à déployer Microsoft Entra Identity Protection en configurant des politiques basées sur les risques (risques liés à l'utilisateur et risques liés à l'ouverture de session) dans votre entreprise. Vous apprendrez également les meilleures pratiques pour déployer progressivement ces politiques et l'inscription MFA dans votre entreprise.

### Prérequis

Si votre organisation souhaite permettre aux utilisateurs de prendre des mesures correctives lorsque des risques sont détectés, les utilisateurs doivent être enregistrés à la fois pour la réinitialisation du mot de passe en libre-service et pour l'authentification multifacteur. Nous vous recommandons d’activer l’expérience d’inscription d’informations de sécurité combinée. Le fait de permettre aux utilisateurs de résoudre eux-mêmes les problèmes les ramène à un état productif plus rapidement, sans nécessiter l’intervention de l’administrateur. Les administrateurs peuvent toujours voir ces événements et les examiner après coup.

### Choix des niveaux de risque acceptables

Les organisations doivent déterminer le niveau de risque consenti lorsqu'elles mettent dans la balance l'expérience utilisateur et la posture de sécurité.

La recommandation de Microsoft est de définir le seuil de stratégie de risque utilisateur sur **Élevé** et la stratégie de connexion à risque sur **Moyen et supérieur**.

La sélection d'un niveau de risque **Élevé** réduit la fréquence de déclenchement d'une stratégie et rend la tâche moins difficile pour les utilisateurs. Cependant, cette option a pour effet d'exclure les détections de risque **Faible** et **Moyen**. Cette exclusion n'empêche pas un pirate d'exploiter une identité compromise. La sélection d'un seuil **Faible** introduit des interruptions utilisateur supplémentaires, mais renforce la sécurité.

### Exclusions

Toutes les politiques permettent d'exclure des utilisateurs tels que vos comptes d'accès d'urgence ou d'administrateur de bris de glace. Les organisations déterminent quand elles doivent exclure d'autres comptes de politiques spécifiques en fonction de l'utilisation des comptes. Toutes les exclusions doivent être examinées régulièrement pour déterminer si elles sont toujours applicables.

Les emplacements réseau approuvés qui ont été configurés sont utilisés par Identity Protection dans certaines détections de risques afin de réduire les faux positifs.


## Exercice – Activer la stratégie de connexion à risque

### Activer la stratégie de risque utilisateur

1. Connectez-vous au [centre d’administration Microsoft Entra](https://entra.microsoft.com/) avec un compte administrateur général.
2. Ouvrez le menu du portail, puis sélectionnez **Identité**.
3. Dans le menu Identité, sélectionnez **Protection**.
4. Dans le panneau Sécurité, dans le volet de navigation de gauche, sélectionnez **Protection de l’identité**.
5. Dans le panneau Protection de l’identité, dans le volet de navigation de gauche, sélectionnez Stratégie de risque utilisateur.
6. Sous **Affectations**, sélectionnez **Tous les utilisateurs** et passez en revue les options disponibles. Vous pouvez sélectionner **Tous les utilisateurs** ou **Sélectionner des personnes et des groupes** si vous limitez votre déploiement. En outre, vous pouvez choisir d’exclure des utilisateurs de la stratégie.
7. Sous **Risque de l’utilisateur**, sélectionnez **Bas et supérieur**.
8. Dans le volet Risque de l’utilisateur, sélectionnez **Élevé**, puis sélectionnez **Terminé**.
9. Sous **Contrôles**, puis **Accès**, sélectionnez **Bloquer l’accès**.
10. Dans le volet Accès, passez en revue les options disponibles.

Conseil

La recommandation de Microsoft consiste à Autoriser l’accès et à Exiger la modification du mot de passe.

1. Cochez la case **Nécessite une modification du mot de passe**, puis sélectionnez **Terminer**.
2. Sous **Appliquer la stratégie**, sélectionnez **Activer** puis **Enregistrer**.

### Activer la stratégie de connexion à risque

1. Dans le panneau Protection de l’identité, dans le volet de navigation de gauche, sélectionnez **Stratégie de risque de connexion**.
2. Comme pour la stratégie d’utilisateur à risque, la stratégie de connexion à risque peut être assignée aux utilisateurs et aux groupes et vous permet d’exclure des utilisateurs de la stratégie.
3. Sous **Risque de connexion**, sélectionnez **Moyen et supérieur**.
4. Dans le volet Risque de connexion, sélectionnez **Élevé**, puis sélectionnez **Terminé**.
5. Sous **Contrôles**, puis **Accès**, sélectionnez **Bloquer l’accès**.
6. Activez la case à cocher **Exiger l’authentification multifacteur**, puis sélectionnez **Terminé**.
7. Sous **Appliquer la stratégie**, sélectionnez **Activer** puis **Enregistrer**.


## Exercice : configurer la stratégie d’inscription de l’authentification multifacteur Microsoft Entra

### Configuration de la stratégie

L'authentification multifacteur permet de vérifier l'identité d'une personne en utilisant plus qu'un nom d'utilisateur et un mot de passe. Cette stratégie fournit une deuxième couche de sécurité aux connexions d’utilisateur. Pour que les utilisateurs puissent répondre aux invites MFA, ils doivent d'abord s'inscrire à l'authentification multifacteur.

1. Connectez-vous au [centre d’administration Microsoft Entra](https://entra.microsoft.com/) avec un compte administrateur général.
2. Ouvrez le menu du portail, puis sélectionnez **Identité**.
3. Dans le menu Identité, sélectionnez **Protection**.
4. Dans le panneau Sécurité, dans le volet de navigation de gauche, sélectionnez **Protection de l’identité**.
5. Dans le panneau Protection des identités, dans le volet de navigation gauche, sélectionnez **Politique d'inscription d'authentification multifacteur**.
6. Sous **Affectations**, sélectionnez **Tous les utilisateurs** et passez en revue les options disponibles. Vous pouvez sélectionner **Tous les utilisateurs** ou **Sélectionner des personnes et des groupes** si vous limitez votre déploiement. En outre, vous pouvez choisir d’exclure des utilisateurs de la stratégie.
7. Sous **Contrôles**, remarquez que l'option **Inscription obligatoire à l'authentification multifacteur pour Microsoft Entra ID** est sélectionnée et ne peut pas être modifiée.
8. Sous **Appliquer la politique**, sélectionnez **Activer** puis **Enregistrer**.


## Surveiller, examiner et corriger les utilisateurs à risque

### Examiner les risques

Identity Protection fournit aux organisations trois rapports qu’elles peuvent utiliser pour examiner les risques liés à l’identité dans leur environnement : **utilisateurs à risque**, **connexions à risque** et **détections de risques**. L’examen des événements est essentiel pour mieux comprendre et identifier les points faibles de votre stratégie de sécurité.

Les trois rapports permettent de télécharger des événements au format .CSV en vue d’analyses plus poussées en dehors du Portail Azure. Les rapports des utilisateurs à risque et des connexions risquées permettent de télécharger les 2,500 entrées les plus récentes, tandis que le rapport sur les détections de risques permet de télécharger les 5,000 enregistrements les plus récents.

Les organisations peuvent tirer parti des intégrations Microsoft API Graph pour agréger des données avec d'autres sources auxquelles elles ont accès en tant qu'organisation.

Vous trouverez les trois rapports dans le Centre d'administration **Microsoft Entra**, puis **Identity**, et enfin **Protection – Identity Protection**.

#### Parcourir les rapports

Chaque rapport démarre avec une liste de toutes les détections pour la période indiquée en haut du rapport. Chaque rapport permet l’ajout ou la suppression de colonnes en fonction des préférences de l’administrateur. Les administrateurs peuvent choisir de télécharger les données au format .CSV ou JSON. Les rapports peuvent être filtrés à l’aide des filtres situés dans la partie supérieure du rapport.

La sélection d’entrées individuelles permet d’ajouter davantage d’entrées en haut du rapport, telles que la possibilité de confirmer une connexion comme compromise ou sécurisée, de confirmer qu’un utilisateur est compromis ou d’ignorer le risque de l’utilisateur.

La sélection d’entrées individuelles développe une fenêtre de détails sous les détections. L’affichage des détails permet aux administrateurs d’investiguer et d’effectuer des actions lors de chaque détection.

#### Utilisateurs à risque

Les informations indiquées dans le rapport Utilisateurs à risque permettent aux administrateurs de trouver :

- Quels sont les utilisateurs à risques ? Pour qui les risques ont-ils été corrigés ou éliminés ?
- Détails sur les détections.
- Historique de toutes les connexions à risque.
- Historique des risques.

Les administrateurs peuvent ensuite choisir d’agir sur ces événements. Les élèves peuvent choisir de procéder de différentes façons :

- Réinitialiser le mot de passe de l’utilisateur.
- Confirmer la compromission de l’utilisateur.
- Ignorer le risque lié à l’utilisateur.
- Empêcher l’utilisateur de se connecter.
- Enquêter dans Microsoft Defender pour Identity.

#### Connexions risquées

Le rapport des connexions à risque contient des données filtrables correspondant aux 30 derniers jours (1 mois).

Les informations indiquées dans le rapport des connexions à risque permettent aux administrateurs de trouver :

- Les connexions classées comme étant à risque, celles confirmées comme étant compromises, celles confirmées comme étant sécurisées, celles rejetées ou corrigées.
- Les niveaux de risque en temps réel et agrégés associés aux tentatives de connexion.
- Types de détections déclenchées.
- Stratégies d’accès conditionnel appliquées.
- Détails de l’authentification multifacteur (MFA).
- Informations sur l'appareil.
- Informations sur l’application.
- Informations sur l’emplacement.

Les administrateurs peuvent ensuite choisir d’agir sur ces événements. Les administrateurs peuvent choisir d’effectuer les opérations suivantes :

- Confirmer que la connexion est compromise.
- Confirmer que la connexion est sécurisée.

#### Détections de risques

Le rapport des détections de risques contient des données filtrables correspondant aux 90 derniers jours (3 mois).

Les informations indiquées dans le rapport des détections de risques permettent aux administrateurs de trouver :

- Des informations sur chaque détection de risques, y compris le type
- Les autres risques déclenchés en même temps.
- L’emplacement de la tentative de connexion.

Les administrateurs peuvent ensuite choisir de revenir au rapport des risques ou des connexions de l’utilisateur pour effectuer des actions en fonction des informations recueillies.

Le rapport de détection des risques fournit également un lien hypertexte vers la détection dans le portail Microsoft Defender pour les applications cloud (MDCA), où vous pouvez afficher d’autres journaux et des alertes.

Remarque

Notre système détecte que l'événement à risque qui a contribué à la note de risque de l'utilisateur est un faux positif ou que le risque de l'utilisateur a été corrigé par l'application d'une politique, par exemple en effectuant une demande d'authentification multifacteur (MFA) ou une modification sécurisée du mot de passe. Par conséquent, notre système ignore l’état des risques, et un détail de risque de « sécurité de connexion confirmée par l’IA » s’affiche et ne contribue plus au risque de l’utilisateur.

### Atténuer les risques et débloquer les utilisateurs

Une fois que vous avez fini votre investigation, vous pouvez prendre des mesures pour atténuer le risque ou débloquer les utilisateurs. Les organisations ont également la possibilité d’activer une correction automatisée en implémentant des stratégies de gestion des risques. Les organisations doivent tenter de traiter toutes les détections de risque auxquelles elles sont confrontées dans un laps de temps qui leur convient. Microsoft recommande de clore les événements dès que possible, car le temps compte en matière de risques.

#### Remédiation

Toutes les détections de risque actifs sont prises en compte dans le calcul d’une valeur appelée niveau de *risque utilisateur.* Le niveau de risque utilisateur est un indicateur (faible, moyen, élevé) de la probabilité qu’un compte ait été compromis. En tant qu’administrateur, vous souhaitez fermer toutes les détections de risques afin que les utilisateurs affectés ne soient plus exposés.

Certaines détections de risque peuvent être signalées par Identity Protection comme « Fermé (système) », car les événements n'étaient plus considérés comme risqués.

Pour corriger, les administrateurs disposent des options suivantes :

- Auto-remédiation avec une politique de gestion des risques.
- Réinitialisation manuelle du mot de passe.
- Ignorer le risque lié à l’utilisateur.
- Fermeture manuelle de détections de risques spécifiques.

#### Auto-rémédiation avec une politique de risque

Si vous autorisez les utilisateurs à prendre des mesures correctives, avec l'authentification multifacteur (MFA) et la réinitialisation du mot de passe en libre-service (SSPR) dans vos politiques de gestion des risques, ils peuvent se débloquer eux-mêmes lorsqu'un risque est détecté. Ces détections sont alors considérées comme fermées. Les utilisateurs doivent avoir déjà été préalablement inscrits pour MFA et SSPR afin de pouvoir les utiliser quand un risque est détecté.

Certaines détections n'augmentent pas le risque au point de nécessiter une correction automatique de l'utilisateur. Toutefois, les administrateurs doivent tout de même évaluer ces détections. Les administrateurs déterminent que d’autres mesures sont nécessaires, telles que le blocage de l’accès à partir d’emplacements ou la réduction du risque acceptable dans leurs stratégies.

#### Réinitialisation manuelle du mot de passe

Si exiger une réinitialisation du mot de passe à l’aide d’une stratégie de risque utilisateur n’est pas envisageable, les administrateurs peuvent fermer toutes les détections de risques pour un utilisateur en opérant une réinitialisation manuelle du mot de passe.

Pour réinitialiser un mot de passe pour leurs utilisateurs, les administrateurs disposent de deux options :

**Générer un mot de passe temporaire** : la génération d’un mot de passe temporaire vous permet de rétablir immédiatement la sécurité d’une identité. Cette méthode nécessite de contacter les utilisateurs affectés, car ceux-ci ont besoin de connaître le mot de passe temporaire. Étant donné que le mot de passe est temporaire, l’utilisateur est invité à le modifier lors de sa prochaine connexion.

**Obliger l’utilisateur à réinitialiser le mot de passe** : le fait de contraindre les utilisateurs à réinitialiser les mots de passe entraîne une récupération automatique qui ne nécessite aucun contact avec le support technique ou un administrateur. Cette méthode s'applique uniquement aux utilisateurs inscrits à MFA et SSPR. Pour les utilisateurs non inscrits, cette option n’est pas disponible.

#### Ignorer le risque lié à l’utilisateur

Si une réinitialisation de mot de passe n’est pas envisageable pour vous, par exemple parce que l’utilisateur a été supprimé, vous pouvez choisir d’ignorer les détections d’utilisateurs à risque.

Lorsque vous sélectionnez **Ignorer le risque lié à l’utilisateur**, tous les événements sont fermés et l’utilisateur concerné n’est plus à risque. Toutefois, étant donné que cette méthode n’affecte pas le mot de passe existant, elle ne rétablit pas la sécurité de l’identité associée.

#### Fermeture manuelle de détections de risques spécifiques

La fermeture manuelle de détections de risques spécifiques vous permet de réduire le niveau de risque utilisateur. En règle générale, les détections de risques sont fermées manuellement en réponse à une investigation associée, par exemple lorsqu’une conversation avec un utilisateur révèle qu’une détection de risques active n’est plus nécessaire.

Lorsque vous fermez des détections de risques manuellement, vous pouvez choisir d’exécuter l’une des actions ci-après pour modifier l’état d’une détection de risque :

- Confirmer que l’utilisateur est compromis.
- Ignorer le risque lié à l’utilisateur.
- Confirmer que la connexion est sécurisée.
- Confirmer que la connexion est compromise.

#### Déblocage des utilisateurs

Un administrateur choisit de bloquer une connexion en fonction de sa politique de gestion de risque ou d'investigations. Un blocage intervient en fonction soit de la tentative de connexion, soit du risque associé à l'utilisateur.

#### Déblocage basé sur le risque utilisateur

Pour débloquer un compte bloqué en raison d’un risque utilisateur, les administrateurs disposent des options suivantes :

- **Réinitialiser le mot de passe** : vous pouvez réinitialiser le mot de passe de l’utilisateur.
- **Ignorer le risque lié à l’utilisateur** : la stratégie de gestion du risque utilisateur bloque un utilisateur si le niveau de risque utilisateur configuré pour bloquer l’accès a été atteint. Vous pouvez réduire le niveau de risque d’un utilisateur en ignorant le risque utilisateur ou en fermant manuellement des détections de risques signalées.
- **Exclure l’utilisateur de la stratégie** : si vous pensez que la configuration actuelle de votre stratégie d’authentification occasionne des problèmes pour certains utilisateurs, vous pouvez les en exclure.
- **Désactiver la stratégie** : si vous pensez que votre configuration de la stratégie est à l’origine des problèmes pour tous vos utilisateurs, vous pouvez désactiver la stratégie.

#### Déblocage basé sur le risque de connexion

Pour débloquer un compte en fonction du risque de connexion, les administrateurs disposent des options suivantes :

- **Connexion à partir d’un emplacement ou d’un appareil connu** : les connexions suspectes bloquées sont généralement des tentatives de connexion effectuées à partir d’un emplacement ou d’un appareil inconnu. Vos utilisateurs peuvent déterminer rapidement s’il s’agit bien de la raison du blocage en essayant de se connecter depuis un appareil ou un emplacement connu.
- **Exclure l’utilisateur de la stratégie** : si vous pensez que la configuration actuelle de votre stratégie d’authentification occasionne des problèmes pour certains utilisateurs, vous pouvez les en exclure.
- **Désactiver la stratégie** : si vous pensez que votre configuration de la stratégie est à l’origine des problèmes pour tous vos utilisateurs, vous pouvez désactiver la stratégie.

#### PowerShell en préversion

Le module Microsoft Graph - SDK PowerShell Preview permet aux organisations de gérer les risques à l'aide de PowerShell. Les modules en préversion et l'exemple de code se trouvent dans le [référentiel GitHub Azure](https://github.com/AzureAD/IdentityProtectionTools).

### Utiliser l’API Microsoft Graph

Microsoft Graph est le point de terminaison d'API unifiée de Microsoft et accueille les API de Microsoft Entra Identity Protection. Il existe trois API qui exposent des informations sur les connexions et les utilisateurs à risque : `riskDetection, riskyUsers, and signIn`.

`riskDetection` vous permet d’interroger Microsoft Graph pour obtenir la liste des détections de risque liées à l’utilisateur et à la connexion, ainsi que des informations associées sur la détection.

`riskyUsers`vous permet d’interroger Microsoft Graph pour obtenir des informations sur les utilisateurs que le service Identity Protection a identifiés en tant qu’utilisateurs à risque.

`signIn` vous permet d'interroger Microsoft Graph pour obtenir des informations sur des connexions Microsoft Entra ID avec des propriétés spécifiques relatives à l'état, au détail et au niveau de risque.

Cette section vous permet de vous familiariser avec la connexion à Microsoft Graph et l’interrogation de ces API. Pour obtenir une introduction détaillée, la documentation complète et un accès à l’Afficheur Graph, consultez le site Microsoft Graph ([https://graph.microsoft.io/](https://graph.microsoft.io/)) ou la documentation de référence propre aux API `riskDetection, riskyUsers, and signIn`.

#### Se connecter à Microsoft Graph

Il existe quatre étapes pour accéder aux données Identity Protection par le biais de Microsoft Graph : récupérer votre nom de domaine, créer une inscription d’application, configurer des autorisations d’API et configurer des informations d’identification valides.

#### Récupérer votre nom de domaine

1. Connectez-vous au centre d’administration Microsoft Entra.
2. Accédez à **Identité**, puis ouvrez Paramètres, et sélectionnez **Noms de domaine**.
3. Prenez note du domaine .onmicrosoft.com. Vous aurez besoin de ces informations lors d’une étape ultérieure.

#### Créer une nouvelle inscription d’application

1. Dans le Centre d'administration de Microsoft Entra, accédez à **Identité et applications**, puis **Inscriptions d'applications**.
2. Sélectionnez **Nouvelle inscription**.
3. Dans la page **Créer**, effectuez les étapes suivantes :
  1. Dans la zone de texte **Nom**, entrez le nom de votre application (par exemple : API Microsoft Entra Risk Detection).
  2. Sous **Types de comptes pris en charge**, sélectionnez le type de comptes qui utilisent les API.
  3. Sélectionnez **Inscription**.

4. Copiez **l’ID de l’application**.

#### Configurez les autorisations d’API

1. Depuis **l’application** que vous avez créée, puis sélectionnez **Autorisations de l’API**.
2. Dans la page **Autorisations configurées**, dans la barre d’outils en haut, sélectionnez **Ajouter une autorisation**.
3. Dans la page **Ajouter un accès d’API**, choisissez **Sélectionner une API**.
4. Dans la page **Sélectionner une API**, sélectionnez **Microsoft Graph**, puis **Sélectionner**.
5. Sur la page **Demander des autorisations d’API**
  1. Sélectionnez **Autorisations de l’application**.
  2. Cochez les cases près de IdentityRiskEvent.Read.All et IdentityRiskyUser.Read.All.
  3. Sélectionnez **Ajouter des autorisations**.

6. Sélectionner **Accorder le consentement de l’administrateur pour le domaine**.

#### Configurez des informations d’identification valides

1. Depuis l’**Application** que vous avez créée, sélectionnez **Certificats et secrets**.
2. Sous **Secrets client**, sélectionnez **Nouveau secret client**.
  1. Attribuez au secret client une **Description** et définissez le délai d’expiration en fonction des stratégies de votre organisation.
  2. Sélectionnez **Ajouter**.  Remarque Si vous perdez cette clé, vous devez revenir à cette section et créer une clé. Gardez cette clé secrète : Toute personne la possédant peut accéder à vos données.

#### Authentifiez-vous auprès de Microsoft Graph et interrogez l’API de détections de risques Identity Protection

À ce stade, vous devez avoir :

- le nom de domaine de votre client ;
- L’ID de l’application (client)
- Le secret ou le certificat du client

Pour l’authentification, envoyez une demande POST à `https://login.microsoft.com` , avec les paramètres suivants dans le corps :

- grant_type : `client_credentials`
- ressource : `https://graph.microsoft.com`
- client_id :
- client_secret :

Si l’opération réussit, la requête retourne un jeton d’authentification. Pour appeler l’API, créez un en-tête avec le paramètre suivant :

```http
Authorization`="<token_type> <access_token>"
```

Lors de l’authentification, le jeton retourné contient le type de jeton ainsi que le jeton d’accès.

Envoyez cet en-tête en tant que requête à l’URL d’API suivante : `https://graph.microsoft.com/v1.0/identityProtection/riskDetections`.

La réponse, en cas de réussite, consiste en une collection de détections de risques concernant l’identité ainsi que les données associées au format JSON OData, qui peuvent être analysées et gérées selon vos besoins.

#### Exemple

Cet exemple montre l’utilisation d’un secret partagé pour l’authentification. Dans un environnement de production, le stockage des secrets dans le code est désapprouvé. Les organisations peuvent utiliser des identités gérées pour les ressources Azure pour sécuriser ces informations d’identification.

Voici un exemple de code pour l’authentification et l’appel de l’API par le biais de PowerShell. Il suffit d’ajouter l’ID client, la clé secrète, ainsi que le domaine du locataire.

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

#### Récupérez toutes les détections de risque hors connexion (API riskDetection)

Avec les stratégies de risque de connexion d’Identity Protection, vous pouvez appliquer des conditions lorsque le risque est détecté en temps réel. Mais qu’en est-il des détections qui sont découvertes hors connexion ? Pour comprendre quelles détections ont eu lieu hors connexion et qui donc n’auraient pas déclenché la stratégie de connexion à risque, vous pouvez interroger l’API `riskDetection`.

```http
GET https://graph.microsoft.com/v1.0/identityProtection/riskDetections?$filter=detectionTimingType eq 'offline'
```

#### Obtenir tous les utilisateurs qui ont réussi l’authentification multifacteur (MFA) déclenchée par une stratégie de connexion à risque (API riskyUsers)

Pour comprendre la valeur que les stratégies Identity Protection basées sur les risques ont sur votre organisation, vous pouvez interroger tous les utilisateurs qui ont réussi une authentification MFA déclenchée par une stratégie de connexion à risque. Ces informations peuvent vous aider à comprendre quels utilisateurs Identity Protection a détectés par erreur comme présentant un risque et lesquels de vos utilisateurs légitimes effectuent des actions que l'IA considère comme risquées.

```http
GET https://graph.microsoft.com/v1.0/identityProtection/riskyUsers?$filter=riskDetail eq 'userPassedMFADrivenByRiskBasedPolicy'
```


## Mettre en œuvre la sécurité des identités de charge de travail

Microsoft Entra Identity Protection a toujours aidé à protéger les utilisateurs en détectant, en investiguant et en corrigeant les risques liés à l’identité. La protection des identités a étendu ces fonctionnalités aux identités de charge de travail pour protéger les applications, les principaux de service et les identités managées.

Une identité de charge de travail est une identité qui permet à une application ou à un principal de service d’accéder à des ressources, parfois dans le contexte d’un utilisateur. Ces identités de charge de travail diffèrent des comptes d’utilisateur traditionnels car elles :

- ne peuvent pas effectuer d’authentification multifacteur ;
- N’ont souvent aucun processus de cycle de vie formel.
- Elles doivent stocker leur informations d’identification ou secrets quelque part.

Ces différences font que les identités de charge de travail sont plus difficiles à gérer et plus faciles à compromettre.

#### Conditions requises pour utiliser la protection des identités de charge de travail

Pour utiliser le risque lié à l’identité de charge de travail, notamment le panneau Identités de charge de travail à risque et l’onglet Détections d’identité de charge de travail dans le panneau Détections de risques, dans le centre d’administration Microsoft Entra, vous devez disposer des éléments suivants.

- Licences Microsoft Entra ID Premium P2
- L’utilisateur connecté doit se voir attribuer l’un des éléments suivants :
  - Administrateur de sécurité
  - Opérateur de sécurité
  - Lecteur de sécurité

#### Quels types de risques sont détectés ?

| **Nom de la détection** | **Type de détection** | **Description** |
|---|---|---|
| Veille des menaces Microsoft Entra | Hors connexion | Cette détection de risque indique une activité cohérente avec les modèles d'attaque connus en fonction des sources de renseignement sur les menaces internes et externes de Microsoft. |
| Connexions suspectes | Hors connexion | Cette détection de risque indique des propriétés de connexion ou des modèles inhabituels pour ce principal du service. |
|   |   | La détection apprend le comportement de connexion de référence pour les identités de charge de travail dans votre locataire en 2 à 60 jours, et se déclenche si une ou plusieurs des propriétés non familières suivantes apparaissent lors d’une connexion ultérieure : adresse IP/ASN, ressource cible, agent utilisateur, modification d’adresse IP d’hébergement/non-hébergement, pays IP, type d’informations d’identification. |
| Ajout inhabituel d’informations d’identification à une application OAuth | Hors connexion | Cette détection est découverte par les Applications Microsoft Defender pour le cloud. Cette détection identifie l’ajout suspect des informations d’identification privilégiées à une application OAuth. Cela peut indiquer qu’un attaquant a compromis l’application et l’utilise pour une activité malveillante. |
| L’administrateur a confirmé que le compte était compromis | Hors connexion | Cette détection indique qu’un administrateur a sélectionné « Confirmer la compromission » dans l’interface utilisateur des identités de charge de travail à risque ou à l’aide de l’API riskyServicePrincipals. Pour voir quel administrateur a confirmé que ce compte est compromis, consultez l’historique des risques du compte (par le biais de l’interface utilisateur ou de l’API). |
| Informations d'identification fuitées | Hors connexion | Cette détection des risques indique que les informations d’identification valides du compte ont fuité. Cette fuite peut se produire lorsque quelqu’un archive les informations d’identification dans l’artefact de code public sur GitHub, ou lorsque les informations d’identification sont divulguées via une violation de données. |

#### Ajouter une protection par accès conditionnel

À l’aide de l’**accès conditionnel pour les identités de charge de travail**, vous pouvez bloquer l’accès à des comptes spécifiques que vous choisissez lorsque la protection des identités les marque « représentant un risque ». La stratégie peut être appliquée à des principaux de service à locataire unique qui ont été enregistrés dans votre locataire. Les applications SaaS tierces, les applications multilocataires et les identités gérées ne font pas partie du périmètre.


## Explorer Microsoft Defender pour Identity

Microsoft Defender pour Identity (anciennement Azure Protection avancée contre les menaces) est une solution de sécurité basée sur le cloud. Defender pour Identity utilise vos signaux Active Directory locales pour identifier, détecter et investiguer des menaces avancées, des identités compromises et des actions internes malveillantes dirigées contre votre entreprise. Defender pour Identity permet aux analystes SecOp et aux professionnels de la sécurité chargés de détecter les attaques avancées dans les environnements hybrides de :

- Surveiller les utilisateurs, ainsi que le comportement et les activités des entités avec une analytique basée sur l’apprentissage
- Protéger les identités et les informations d’identification des utilisateurs qui sont stockées dans Active Directory
- Identifier et examiner les activités suspectes des utilisateurs et les attaques avancées dans toute la chaîne de destruction
- Fournir des informations claires sur les incidents selon une chronologie simple, permettant un triage rapide

#### Flux de processus pour Defender pour Identity

![Diagramme du flux de données pour la protection des identités à l’aide de Microsoft Defender pour Identity.](https://learn.microsoft.com../../wwl-sci/manage-azure-active-directory-identity-protection/media/defender-identity-topology.png)

Defender pour Identity est constitué des composants suivants :

- portail **Microsoft Defender** - Defender pour Identity est géré via le portail Microsoft Defender (`security.microsoft.com`). Le portail affiche les données reçues de Defender pour les capteurs d’identité et vous permet de surveiller, de gérer et d’examiner les menaces dans votre environnement réseau.
- **Capteur Defender pour Identity** - Les capteurs Defender pour Identity peuvent être installés directement sur les serveurs suivants :
  - Contrôleurs de domaine : Le capteur supervise directement le trafic des contrôleurs de domaine, sans recourir à un serveur dédié, ou à une configuration de mise en miroir de ports.
  - Services fédérés Active Directory (AD FS) : Le capteur surveille directement le trafic réseau et les événements d’authentification.

- **Service cloud Defender pour Identity** - Le service cloud Defender pour Identity s’exécute dans l’infrastructure Azure et est actuellement déployé aux États-Unis, en Europe et en Asie. Defender pour le service cloud Identity est connecté au renseignement sur les menaces de Microsoft.


## Explorer l’agent de gestion des risques liés à l’identité

L’agent Identity Risk Management dans Microsoft Entra ID Protection fournit des fonctionnalités de gestion proactive des risques en analysant le comportement de l’utilisateur. L’agent suggère ensuite des actions pour atténuer les risques potentiels d’identité. Vous pouvez configurer les paramètres pour répondre aux besoins de votre organisation. En utilisant un modèle de langage volumineux, l’agent aide les administrateurs de sécurité à examiner et à répondre aux activités à risque avant qu’ils n’entraînent des incidents de sécurité.

### Prerequisites

- Vous devez disposer au moins de la licence Microsoft Entra ID P2.
- Vous devez disposer d’unités de calcul de sécurité (SCU) disponibles.
- Vous devez disposer du rôle Microsoft Entra approprié.
  - **Administrateur de sécurité** : requis pour activer l’agent la première fois et afficher l’agent et prendre des mesures sur les suggestions.
  - **Lecteur de sécurité** et **Lecteur global** : affichez l’agent et toutes les suggestions (ne peuvent pas effectuer d’actions).

### Fonctionnement de l’agent

L’agent vérifie les nouvelles identités à risque qui n’ont pas été identifiées précédemment. Si de nouvelles identités à risque sont trouvées, il effectue les étapes suivantes (aucune SKU n’est consommée) :

1. L’agent vérifie les nouveaux utilisateurs à risque dans votre locataire qui ont actuellement un état de risque « À risque ».
2. L’agent identifie les utilisateurs à risque qui se trouvent dans vos paramètres d’étendue définis.

Si l’agent trouve de nouvelles suggestions, il effectue les étapes suivantes (SCUs consommées) :

| Étape | Activité de l’agent |
|---|---|
| Examiner l’utilisateur à risque | L’agent vérifie les connexions à risque et les détections de risques de l’utilisateur pour analyser ce qui est risqué à propos de cet utilisateur. |
| Générer des résultats et un résumé des risques | L’agent génère des résultats basés sur l’enquête, qui comprend un résumé complet des risques expliquant la suggestion et définissant les facteurs de risque clés. |
| Générer une action de correction recommandée | L’agent suggère une action de correction à l’aide des informations collectées pendant l’enquête. |
| Répondre aux questions par le biais d’une conversation | Les administrateurs informatiques posent les questions relatives aux utilisateurs à risque et au résumé des risques. |
| Stocker des instructions personnalisées dans la mémoire de l’agent | Les clients peuvent donner des instructions personnalisées à l'agent via une discussion directe avec l'agent, que l'agent stocke dans sa mémoire et applique lors des futures exécutions. Actuellement, la mémoire de l’agent peut stocker les actions de correction préférées. |

### Utilisation de l’agent

1. Connectez-vous au **Centre d’administration Microsoft Entra** en tant qu’administrateur de sécurité au moins.
2. Accédez à **Protection des ID**>**utilisateurs à risque**.
3. Recherchez la bannière en haut de la page.
4. Sélectionner **Démarrer l'agent**

#### Configuration des paramètres de l’agent

Lorsque la page **Utilisateurs à risque** s’ouvre, sélectionnez la **vue Agent**. Sélectionnez les trois points dans le coin supérieur droit, puis sélectionnez Paramètres.

- **Contrôles** : fournissez les rôles et les autorisations nécessaires pour exécuter l’agent.
- **Déclencheurs** : définir quand et comment l’agent est exécuté :
  - Surveillance continue : vérifie les nouveaux utilisateurs à risque toutes les 5 minutes
  - Déclencheur quotidien : l’agent s’exécute une fois par jour
  - Exécution manuelle : l’agent s’exécute uniquement lors du lancement manuel

- **Étendue** : par défaut, l’agent examine les 100 utilisateurs à risque les plus récents au cours des 90 derniers jours. Vous pouvez ajuster plusieurs options pour contrôler l'étendue de l'analyse de l'agent.
  - Sélectionnez l’option utilisateurs et groupes pour rechercher et sélectionner les utilisateurs et les groupes que vous souhaitez analyser par l’agent.
  - Définissez le nombre maximal d’utilisateurs à risque récents à analyser dans un délai de 1 à 100.
  - Sélectionnez les niveaux de risque à inclure dans l’analyse. Tous les niveaux de risque sont sélectionnés par défaut.
  - Définissez une période de temps spécifique pour l’étendue :
    - 7 derniers jours
    - 14 derniers jours
    - 30 derniers jours
    - Délai personnalisé jusqu’à 90 jours

- **Communications** : entrez un ensemble d’utilisateurs pour recevoir des notifications de l’exécution de l’agent.
- **Mémoire** : liste des éléments sécurisés confirmés par l’utilisateur qui étaient des faux positifs.

### Explorez le rapport sur les conclusions de l'agent

#### Résumé de l’agent

Un résumé de l’agent apparaît en haut de la vue Agent, affichant les activités récentes de l’agent. Cette vignette fournit un accès rapide à la fonctionnalité Conversation avec agent et un bouton Gérer l’agent, ce qui vous permet de déclencher une exécution unique ou d’ouvrir les paramètres de l’agent.

#### Suggestions d’agent

Les suggestions d’agent sont affichées sous le résumé de l’agent. Pointez sur une suggestion pour mettre en évidence les utilisateurs impactés dans le tableau. La sélection d’une suggestion filtre le tableau pour afficher uniquement les utilisateurs à réviser. Chaque suggestion inclut un bouton d’action en bloc, ce qui vous permet d’appliquer l’action à l’aide d’un bouton.

Actuellement, les actions de correction suivantes sont disponibles dans les suggestions d’agent :

- Ignorer le risque
- Réinitialiser le mot de passe

#### Table des utilisateurs hautement à risque avec suggestions des agents

La moitié inférieure du rapport répertorie tous les utilisateurs à risque. Sélectionnez un utilisateur pour afficher les résultats de l’agent, les facteurs de risque et les suggestions spécifiques à cet utilisateur. La colonne des suggestions de l'agent affiche également les actions de correction proposées directement dans le tableau. Sélectionnez le bouton d’action pour appliquer une correction à des utilisateurs individuels.

#### Détails de l’utilisateur à risque

La page détails de l’utilisateur à risque fournit une nouvelle vue Agent, qui présente les résultats de l’agent spécifiques à un utilisateur à risque. Cette vue inclut les informations suivantes :

- **Informations utilisateur de base : nom d’utilisateur**, niveau de risque actuel et nom d’utilisateur principal (UPN)
- **Résultats de l’agent** : l’agent fournit un verdict de compromis ou non-compromis sur la base de son enquête
- **Résumé des risques** : explication détaillée des résultats de l’agent, en fonction de l’analyse des connexions et des comportements de l’utilisateur
- **Facteurs de risque** : indicateurs de risque clés résumés pour un examen facile
- **Action de correction suggérée** : un bouton d’appel à l’action qui vous permet de commencer rapidement à corriger le risque


## Évaluation du module

Choisissez la meilleure réponse à chacune des questions ci-dessous.

### Contrôle des connaissances


## Récapitulatif et ressources

Maintenant que vous avez parcouru ce module, vous devez être capable de :

- Passez en revue les principes fondamentaux de Identity Protection.
- Implémenter et gérer une stratégie de risque d’utilisateur.
- Implémenter et gérer des stratégies de risque de connexion.
- Implémenter et gérer la politique d'enregistrement de l'authentification multifacteur.
- Surveiller, examiner et corriger les utilisateurs à risque.
- Explorez Microsoft Defender pour l'Identité

### Ressources

Utilisez ces ressources pour approfondir vos connaissances.

- [Activation de l’inscription combinée des informations de sécurité dans Microsoft Entra ID](https://learn.microsoft.com/fr-fr/entra/identity/authentication/howto-registration-mfa-sspr-combined)
- [Gérer les comptes d'accès d'urgence dans Microsoft Entra ID](https://learn.microsoft.com/fr-fr/entra/identity/role-based-access-control/security-emergency-access)
- [Guide pratique pour Configurer et activer des stratégies de risque](https://learn.microsoft.com/fr-fr/entra/id-protection/howto-identity-protection-configure-risk-policies)
- [Que sont les identités managées pour les ressources Azure ?](https://learn.microsoft.com/fr-fr/entra/identity/managed-identities-azure-resources/overview)
- [Corriger les risques et débloquer les utilisateurs](https://learn.microsoft.com/fr-fr/entra/id-protection/howto-identity-protection-remediate-unblock)
- [Notifications d'Identity Protection de Microsoft Entra](https://learn.microsoft.com/fr-fr/entra/id-protection/howto-identity-protection-configure-notifications)
- [Stratégies de protection de l'identité](https://learn.microsoft.com/fr-fr/entra/id-protection/concept-identity-protection-policies)
- [Qu’est-ce que Microsoft Defender pour Identity ?](https://learn.microsoft.com/fr-fr/defender-for-identity/what-is)


---

# Implémenter le Gestionnaire d’accès pour des ressources Azure

_https://learn.microsoft.com/fr-fr/training/modules/implement-access-management-for-azure-resources/_


## Présentation

Ce module explique comment attribuer et gérer l’accès à des ressources dans Azure en utilisant des rôles Azure. Quand vous créez une ressource, vous voulez être sûr que seul un accès spécifique est accordé aux utilisateurs et aux groupes. Accordez aux utilisateurs qui doivent accéder à des données ou à une ressource les autorisations nécessaires. Comment pouvez-vous contrôler l’accès ? En attribuant un rôle avec les autorisations spécifiques nécessaires. Il existe des rôles Azure intégrés et vous pouvez créer des rôles personnalisés en fonction des besoins.

Une application pourrait aussi avoir besoin de l’autorisation d’accéder aux données ou à d’autres ressources Azure. Découvrez comment configurer des identités managées, qui permettent à l’application d’accéder seulement aux ressources que vous autorisez. Vous pouvez accorder un accès limité à des secrets, des clés et des certificats stockés dans un coffre de clés à vos utilisateurs et applications. Vous protégez les éléments stockés dans le coffre de clés et vous limitez ceux qui peuvent les utiliser. Enfin, vous allez examiner le nouvel outil Gestion des autorisations Microsoft Entra. Apprenez à collecter, examiner et restreindre les autorisations affectées dans vos solutions cloud.

#### Objectifs d’apprentissage

À la fin de ce module, vous serez en mesure d’effectuer les opérations suivantes :

- Attribuer des rôles Azure et des rôles personnalisés pour accéder aux ressources Azure.
- Créer et gérer l’accès aux applications avec des identités managées.
- Configurer et gérer l’accès dans Azure Key Vault.
- Récupérer de façon sécurisée un objet dans un coffre de clés.
- Explorer les fonctionnalités de Gestion des autorisations Microsoft Entra.

#### Prérequis

Aucun


## Affecter des rôles Azure

Le contrôle d’accès en fonction du rôle Azure (Azure RBAC) est le système d’autorisation que vous utilisez pour gérer l’accès aux ressources Azure. Pour accorder l’accès, vous devez attribuer des rôles aux utilisateurs, aux groupes, aux principaux de service ou aux identités managées avec une étendue particulière. Étapes principales à suivre lors de l’attribution d’un rôle Azure :

1. Qui a besoin d’accéder ?
  - **Utilisateur** : une seule personne est nécessaire pour la tâche. Vous pouvez attribuer un rôle à des utilisateurs dans d’autres locataires.
  - **Groupe** : à utiliser quand vous devez accorder le même rôle à un ensemble d’utilisateurs.
  - **Principal de service** : attribuez un rôle à un principal de service quand vous voulez accorder à une application l’accès à une ressource Azure.
  - **Identité managée** : utilisez l’identité managée quand vous voulez qu’une application gère les informations d’identification pour l’authentification.

2. Sélectionnez le rôle approprié. Utilisez les rôles intégrés ou créez un rôle personnalisé avec les capacités spécifiques dont vous avez besoin.

- Rôles Azure intégrés
  - Propriétaire : accès complet à toutes les ressources.
  - Contributeur : peut créer et gérer tous les types de ressource Azure, mais ne peut pas accorder l’accès.
  - Lecteur : peut voir les ressources Azure existantes.
  - Administrateur de l’accès utilisateur : attribue l’accès aux ressources Azure.
  - D’autres rôles spécifiques à une tâche, comme Contributeur de machines virtuelles, peuvent être attribués.

1. Identifiez le niveau à affecter au rôle (l’étendue). Étendue représente l’ensemble des ressources auxquelles l’accès s’applique. Dans Azure, vous pouvez spécifier une étendue à quatre niveaux : groupe d’administration, abonnement, groupe de ressources et ressource. Les étendues sont structurées dans une relation parent-enfant. Chaque niveau de hiérarchie rend l’étendue plus spécifique. Vous pouvez attribuer des rôles à n’importe de ces niveaux d’étendue. Le niveau que vous sélectionnez détermine la portée d’application du rôle. Les niveaux inférieurs héritent des autorisations de rôle des niveaux supérieurs. Exemple :
  - Si vous attribuez le **rôle Lecteur** à un utilisateur au niveau de l’**étendue du groupe d’administration**, cet utilisateur peut lire tous les éléments des abonnements dans le groupe d’administration.
  - Si vous attribuez le **rôle Lecteur de facturation** à un groupe au niveau de l’**étendue de l’abonnement**, les membres de ce groupe peuvent lire les données de facturation des groupes de ressources et des ressources dans l’abonnement.
  - Si vous attribuez le **rôle Contributeur** à une application au niveau de l’**étendue du groupe de ressources**, il peut gérer tous les types de ressources de ce groupe de ressources, mais aucun autre groupe de ressources dans l’abonnement. Il est recommandé d’accorder aux principaux de sécurité les privilèges minimaux dont ils ont besoin pour effectuer leur travail. Évitez d’attribuer des rôles plus larges à des étendues plus importantes, même si cela semble plus pratique dans un premier temps. En limitant les rôles et les étendues, vous limitez les ressources menacées en cas de compromission du principal de sécurité. Pour plus d’informations, consultez Comprendre l’étendue.

2. Vérifiez que l’utilisateur actuellement connecté dispose des droits nécessaires pour attribuer le rôle Azure.
3. Attribuez le rôle. Une fois que vous connaissez le principal de sécurité, le rôle et l’étendue, vous pouvez attribuer le rôle. Vous pouvez attribuer des rôles en utilisant le portail Azure, Azure PowerShell, Azure CLI, des Kits de développement logiciel (SDK) Azure ou des API REST. Vous pouvez avoir jusqu’à 4 000 attributions de rôles dans chaque abonnement. Cette limite comprend les attributions de rôles au niveau de l’abonnement, du groupe de ressources et des étendues de ressources. Vous pouvez avoir jusqu’à 500 attributions de rôles dans chaque groupe d'administration.

#### Attribuer un rôle Azure à partir du portail

Que vous soyez dans la section Utilisateur, Groupe, Groupe de ressources ou Abonnement, vous utilisez la page Gestion des accès (IAM) pour attribuer les droits. Le nom officiel est la gestion des identités et des accès (IAM) et apparaît à plusieurs emplacements dans le portail Azure.

#### Attribuer un rôle Azure avec un script

PowerShell en utilisant la cmdlet Microsoft Graph PowerShell

```
New-AzRoleAssignment -ObjectId <objectId> `
-RoleDefinitionName <roleName> `
-Scope /subscriptions/<subscriptionId>/resourcegroups/<resourceGroupName>/providers/<providerName>/<resourceType>/<resourceSubType>/<resourceName>
```

Écriture de scripts CLI

```
az role assignment create --assignee "{assignee}" \
--role "{roleNameOrId}" \
--resource-group "{resourceGroupName}"
```


## Configurer des rôles Azure personnalisés

Si les rôles intégrés Azure ne répondent pas aux besoins spécifiques de votre organisation, vous pouvez créer vos propres rôles personnalisés Azure. Tout comme les rôles intégrés, vous pouvez attribuer des rôles personnalisés à des utilisateurs, des groupes et des principaux de service dans des étendues de groupe d’administration (en préversion uniquement), d’abonnement et de groupe de ressources. Les rôles personnalisés sont stockés dans une instance Microsoft Entra ID et peuvent être partagés entre les abonnements. Chaque annuaire peut avoir jusqu’à 5 000 rôles personnalisés. Vous pouvez créer des rôles personnalisés à l’aide du portail Azure, d’Azure PowerShell, d’Azure CLI ou de l’API REST.

#### Créer le rôle personnalisé à partir de l’interface utilisateur

Vous attribuez un rôle personnalisé à un utilisateur, un groupe ou une autre ressource comme vous le feriez pour un rôle intégré. Votre administrateur contrôle exactement les fonctionnalités auxquelles le rôle personnalisé a accès. Le principe du privilège minimum vous permet de sélectionner seulement les fonctionnalités dont vous avez besoin. Pour créer le rôle personnalisé :

1. Ouvrez le centre d’administration Microsoft Entra.
2. Dans le menu **Identité**, sélectionnez **Rôles et administration**.
3. Sélectionnez **+ Nouveau rôle personnalisé**.
4. Ensuite, nommez et affectez les fonctionnalités nécessaires.

#### Créer un rôle personnalisé à partir d’un modèle JSON

Vous pouvez utiliser un fichier JSON pour créer un rôle personnalisé. Voici un exemple :

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

L’astérisque (`*`) est utilisé comme caractère générique. Si vous devez affecter toutes les autorisations de **lecture** de la ressource **Facturation** qui utilisent cette commande **Microsoft/Billing/*/read**. Le caractère générique peut exister à n’importe quel niveau.


## Créer et configurer des identités managées

Une problématique courante lors de la création d’une solution cloud est la gestion des secrets, des informations d’identification, des certificats et des clés. Ces éléments sécurisés sont utilisés pour sécuriser la communication entre les services. Les identités managées permettent aux développeurs de ne plus avoir à gérer ces informations d’identification.

Bien que les développeurs puissent stocker en toute sécurité les secrets dans Azure Key Vault, les services ont besoin d’un moyen d’accéder à Azure Key Vault. Les identités managées fournissent une identité gérée automatiquement dans Microsoft Entra ID, que les applications utilisent pour se connecter aux ressources. L’identité managée prend en charge l’authentification via Microsoft Entra ID. Les applications peuvent utiliser des identités managées pour obtenir des jetons Microsoft Entra sans avoir à gérer les informations d’identification.

#### Avantages liés à l’utilisation des identités managées

- Vous n’avez pas besoin de gérer les informations d’identification. Vous n’avez même pas accès aux informations d’identification.
- Vous pouvez utiliser des identités managées pour vous authentifier auprès de ressources qui prennent en charge l’authentification Microsoft Entra, y compris vos propres applications. Les identités managées peuvent être utilisées sans surcoût.

#### Types d’identités managées

| **Type d'identité** | **Description et utilisation** |
|---|---|
| Attribué par le système | Certains services Azure vous permettent d’activer une identité managée directement sur une instance de service. Lorsque vous activez une identité managée affectée par le système, une identité est créée dans Microsoft Entra ID. L’identité est liée au cycle de vie de cette instance de service. Lorsque la ressource est supprimée, Azure supprime automatiquement l’identité. Par défaut, seule cette ressource Azure peut utiliser cette identité pour demander des jetons à Microsoft Entra ID. |
| Affecté par l’utilisateur | Vous pouvez également créer une identité managée en tant que ressource Azure autonome. Vous pouvez créer une identité managée affectée par l’utilisateur et l’attribuer à une ou plusieurs instances d’un service Azure. Une identité managée affectée par l’utilisateur est gérée séparément des ressources qui l’utilisent. |

Rappelez-vous toujours que les identités managées sont affectées à une application. Vous devez donc configurer et gérer l’identité au sein des services utilisés. Si vous avez une application s’exécutant sur une machine virtuelle (Linux ou Windows), c’est ici que ajoutez et configurez l’identité. Si vous utilisez une identité managée avec une application cloud, une fonction ou un service d’application, vous la configurez et vous la gérez à cet endroit. Examinons l’ajout d’une identité managée à une application cloud en utilisant App Service.

#### Identité managée dans le portail Azure pour un App Service

Les étapes de base pour créer et ajouter une identité à votre application sont les suivantes :

1. Créez votre application.
2. Ouvrez l’application dans le portail Azure.
3. Sélectionnez **Identité** dans le menu, puis sélectionnez **Affecté(e) par le système** ou **Affecté(e) par l’utilisateur**.
4. Sélectionnez l’élément **+ Ajouter** et terminez l’Assistant.

Vous pouvez effectuer une action similaire en utilisant un script dans l’interface CLI, PowerShell ou avec un modèle. L’exemple peut se présenter comme ceci :

**Avec l’interface CLI**

```
az webapp identity assign --resource-group <group-name> --name <app-name> --identities <identity-name>
```

Ou en utilisant **PowerShell** avec le module AZ.ManagedServiceIdentity installé

```
Update-AzFunctionApp -Name <app-name> -ResourceGroupName <group-name> -IdentityType UserAssigned -IdentityId $userAssignedIdentity.Id
```

Ou dans un **modèle**

```
"identity": {
    "type": "UserAssigned",
    "userAssignedIdentities": {
        "<RESOURCEID>": {}
    }
}
```

#### Valeur d’une identité managée

Comme mentionné au début de cette page, quand vous créez une application, vous avez besoin d’une méthode pour lui accorder l’accès aux ressources. Pour tirer parti des concepts de la **Confiance Zéro**, vous pouvez utiliser des identités managées. Vous affectez seulement les privilèges minimaux dont l’identité managée a besoin. Vous accordez ensuite seulement l’accès aux ressources minimales nécessaires. Le privilège minimum va assurer la protection de vos applications et de vos données.


## Accéder aux ressources Azure avec des identités managées

Les identités managées pour les ressources Azure sont une fonctionnalité de Microsoft Entra ID. Chaque service Azure qui prend en charge les identités managées est soumis à leur propre chronologie. Assurez-vous de passer en revue l’état Disponibilité des identités gérées pour votre ressource et les problèmes connus avant de commencer. Après avoir configuré une ressource Azure avec une identité managée, vous pouvez accorder à cette identité un accès à une autre ressource.

#### Ajouter un accès à d’autres ressources

Une fois que vous avez activé l’identité managée sur une ressource Azure, telle qu’une application Azure App Service ou une machine virtuelle Azure, vous devrez peut-être accorder l’accès à d’autres ressources. Supposons que vous voulez ajouter l’accès à un compte de stockage à votre identité managée.

1. Connectez-vous au portail Azure en utilisant un compte associé à l’abonnement Azure sous lequel vous avez configuré l’identité managée.
2. Accédez à la ressource souhaitée sur laquelle vous voulez modifier le contrôle d’accès. Dans cet exemple, nous offrons donnons à une machine virtuelle Azure l’accès à un compte de stockage : nous accédons donc au compte de stockage.
3. Sélectionnez Contrôle d’accès (IAM).
4. Sélectionnez Ajouter > Ajouter une attribution de rôle pour ouvrir la page Ajouter une attribution de rôle.
5. Choisissez le rôle Propriétaire, Contributeur ou Lecteur, en fonction des règles de privilège minimum pour les besoins de vos applications.
6. Sélectionnez l’identité managée que vous voulez affecter.
7. Effectuez l’affectation avec l’option **Vérifier + affecter**.


## Analyser les autorisations des rôles Azure

Qu’est-ce qu’une autorisation ? La définition de l’autorisation dans le dictionnaire est **le consentement ou l’autorisation d’effectuer une action spécifique**. Dans Microsoft Entra ID, vous disposez d'autorisations pour chacune des opérations que vous pouvez effectuer. L’autorisation peut aller de l’affichage de vos paramètres à la possibilité de modifier votre configuration. Ensuite, passez à l’octroi d’autorisations pour ajouter ou supprimer des utilisateurs, etc. Il existe deux endroits principaux où l’autorisation peut être attribuée : au niveau de l’utilisateur ou du groupe. Elle finit toutefois au final par passer par l’utilisateur. Pour ce qui est des utilisateurs, il existe les utilisateurs membres et les utilisateurs invités. Les autorisations par défaut pour l’utilisateur invité sont légèrement inférieures à celles d’un utilisateur membre.

#### Qu’est-ce qu’un exemple d’autorisations par défaut pour les utilisateurs ?

| **Utilisateurs membres** | **Utilisateurs invités** |
|---|---|
| Énumérer la liste de tous les utilisateurs et contacts | Lire ses propres propriétés |
| Inviter des utilisateurs | Inviter des utilisateurs |
| Peut créer la sécurité et les groupes Microsoft 365 | Peut rechercher des groupes non masqués par nom |
| Inscrire de nouvelles applications | Lire les propriétés des applications inscrites et d’entreprise |

Remarque

Il s’agit simplement d’un petit sous-ensemble, afin de montrer les différences. Si vous souhaitez obtenir la liste complète, consultez les [autorisations utilisateur par défaut](https://learn.microsoft.com/fr-fr/azure/active-directory/fundamentals/users-default-permissions).

#### Contrôle des autorisations - ajouter et restreindre

Vous pouvez utiliser les **Paramètres utilisateur** dans le menu Gérer de Microsoft Entra ID pour restreindre ou contrôler les autorisations par défaut des utilisateurs par défaut. Vous pouvez également utiliser des rôles et des administrateurs pour ajouter de nouvelles autorisations à vos utilisateurs et groupes. Utilisez toujours le concept de privilège minimum et assurez-vous que les utilisateurs ont uniquement les droits dont ils ont besoin. Dans les paramètres utilisateur, vous pouvez restreindre la capacité de l’utilisateur à :

- Inscrire des applications
- Accéder au portail Azure
- Bloquer les connexions LinkedIn
- Gérer les paramètres de la collaboration externe

En ajoutant des rôles à un compte d’utilisateur ou à un groupe donné, vous pouvez ajouter des autorisations aux utilisateurs membres, aux utilisateurs invités et aux principaux de service. L’ajout de rôles donne des autorisations pour effectuer des activités spécifiques. Les actions sont limitées, ce qui autorise la règle de privilège minimum.

#### Exploration des autorisations disponibles

Vous voulez accorder seulement les autorisations dont un utilisateur a besoin. Veillez donc à connaître toutes les autorisations accordées quand vous attribuez un rôle. Vous pouvez voir la liste des autorisations dans le **lecteur de définition d’attribut**. Pour l’ouvrir, lancez Microsoft Entra ID, puis ouvrez l’écran **Rôles et administrateurs**. Sélectionnez ensuite un rôle, puis ouvrez sa page de description dans le menu de points de suspension (...). Selon le rôle que vous avez choisi, vous verrez un nombre plus ou moins important d’autorisations. Deux ensembles d’autorisations :

- Autorisations des rôles
- Autorisations de lecture de base du principal de service et de l’invité


## Configurer des stratégies RBAC Azure Key Vault

Vous pouvez accorder l’accès à Azure Key Vault en utilisant le contrôle d’accès en fonction du rôle (RBAC) ou en utilisant des stratégies d’accès Key Vault. Les deux méthodes fonctionnent pour protéger vos secrets, vos certificats et vos clés. Les stratégies d’accès vous donnent un contrôle un peu plus précis, mais peuvent être plus difficiles à gérer. Choisissez la meilleure option en fonction de vos besoins en matière de posture de sécurité.

#### Attribuer une stratégie d’accès Key Vault

Une stratégie d’accès Key Vault détermine si un utilisateur, une application ou un groupe peut effectuer des opérations sur des secrets, des clés et des certificats Key Vault. Vous pouvez attribuer des stratégies d’accès à l’aide du portail Azure, d’Azure CLI ou d’Azure PowerShell. Le coffre de clés prend en charge jusqu’à 1024 entrées de stratégie d’accès, chaque entrée accordant un ensemble distinct d’autorisations à un principal de sécurité particulier. En raison de cette limitation, nous vous recommandons d’attribuer des stratégies d’accès, autant que possible, à des groupes d’utilisateurs plutôt qu’à des utilisateurs individuels. L’utilisation de groupes facilite grandement la gestion des autorisations pour plusieurs personnes au sein de votre organisation.

1. Ouvrez **Key Vault** dans le portail Azure.
2. Sélectionnez votre coffre de clés ou créez-en un.
3. Dans le menu, sélectionnez **Stratégies d’accès**, puis **+ Ajouter une stratégie d’accès**.
4. Utilisez la boîte de dialogue pour attribuer l’autorisation spécifique que doit avoir le principal de service.  Remarque Le principal de service représente l’utilisateur, le groupe ou l’application auquel vous affectez la stratégie.
5. Sélectionnez **Ajouter** pour enregistrer et appliquer la stratégie d’accès.

Vous pouvez effectuer cette activité en utilisant un modèle enregistré, PowerShell, l’interface CLI et le portail Azure.

#### Attribuer un accès à Key Vault en utilisant le contrôle d’accès en fonction du rôle (RBAC)

Le RBAC Azure permet aux utilisateurs de gérer les autorisations de clé, de secrets et de certificats. Il fournit un emplacement unique pour gérer toutes les autorisations sur tous les coffres de clés. Le modèle RBAC Azure vous permet de définir des autorisations pour différents niveaux d’étendue : groupe d’administration, abonnement, groupe de ressources ou ressource individuelle. RBAC Azure pour Key Vault offre également la possibilité d’avoir des autorisations distinctes sur des clés, des secrets et des certificats individuels. Nous recommandons d’utiliser un coffre par application et par environnement (développement, préproduction et production).

Deux actions sont nécessaires pour utiliser des rôles afin d’accéder à des données dans votre coffre de clés.

1. Activez le contrôle d’accès en fonction du rôle dans votre coffre de clés.
2. Ouvrez **Identité et accès (IAM)** du coffre de clés dans le menu. Ensuite, attribuez le rôle comme vous l’avez fait dans d’autres scénarios, par exemple celui de l’identité managée.

| **Rôle intégré** | **Description** |
|---|---|
| Administrateur Key Vault | Permet d’effectuer toutes les opération du plan de données sur un coffre de clés et tous les objets qu’il contient, notamment les certificats, les clés et les secrets. Ne peut pas gérer les ressources du coffre de clés ou les attributions de rôle. |
| Agent des certificats Key Vault | Permet d’effectuer une action sur les certificats d’un coffre de clés, à l’exception des autorisations de gestion. |
| Agent de chiffrement Key Vault | Permet d’effectuer une action sur les clés d’un coffre de clés, à l’exception des autorisations de gestion. |
| Utilisateur du service de chiffrement de Key Vault | Permet de lire les métadonnées des clés et d’effectuer des opérations visant à envelopper/désenvelopper. |
| Utilisateur de chiffrement Key Vault | Permet d’effectuer des opérations de chiffrement à l’aide de clés. |
| Lecteur Key Vault | Permet de lire les métadonnées de coffres de clés et de leurs certificats, clés et secrets. Ne peut pas lire des valeurs sensibles, comme les contenus secrets ou les documents clés. |
| Agent des secrets Key Vault | Permet d’effectuer une action sur les secrets d’un coffre de clés, à l’exception des autorisations de gestion. |
| Utilisateur des secrets Key Vault | Permet de lire le contenu du secret. |


## Récupérer des objets auprès d’Azure Key Vault

Azure Key Vault est un outil sécurisé pour stocker des secrets, des clés et des certificats. Une fois stockés, ces éléments peuvent être utilisés par les utilisateurs et les applications pour effectuer des actions et des opérations selon une méthode sécurisée. Le processus de récupération de ces ressources est commun. Nous allons donc voir comment examiner un secret provenant d’un coffre de clés.

#### Ajouter un secret à votre coffre de clés

Pour ajouter un secret au coffre, procédez comme suit :

1. Accédez à votre nouveau coffre de clés dans le portail Azure.
2. Dans les pages des paramètres de coffre de clés, sélectionnez **Secrets**.
3. Sélectionnez **Générer/importer**.
4. Dans l’écran Créer un secret, choisissez les valeurs suivantes :     **Paramètre**  **Valeur à entrer**     Options de chargement Manuel   Nom mySC300keyvaultSecret   Valeur C’est mon secret
5. Sélectionnez **Create** (Créer).

#### Récupérer un secret en utilisant le portail Azure

Le processus est simple. Ouvrez votre coffre de clés, puis ouvrez le secret que vous avez créé. Sélectionnez le bouton **Afficher la valeur du secret**.

#### Récupérer un secret en utilisant l’interface CLI ou PowerShell

Vous pouvez récupérer un secret rapidement et facilement dans votre coffre de clés en utilisant des langages de script.

**INTERFACE DE LIGNE DE COMMANDE**

```
az keyvault secret show --name "mySC300keyvaultSecret" --vault-name "<your-unique-keyvault-name>" --query "value"
```

***PowerShell***

```
$secret = Get-AzKeyVaultSecret -VaultName "<your-unique-keyvault-name>" -Name "mySC300keyvaultSecret" -AsPlainText
```

#### Récupérer un secret dans une application

Si vous créez une application qui a besoin d’accéder à des secrets, des certificats et des clés de votre coffre de clés, vous pouvez faire cela. Vous pouvez accéder au coffre en utilisant .NET, Node.js, Python et d’autres langages.


## Contrôle des connaissances

Choisissez la meilleure réponse à chacune des questions ci-dessous.

### Contrôler vos connaissances


## Récapitulatif et ressources

Quand vous créez une ressource, vous voulez être sûr que seul un accès spécifique est accordé aux utilisateurs et aux groupes. Dans ce module, vous avez appris les différentes méthodes pour attribuer et contrôler l’accès à des ressources Azure.

Dans ce module, vous avez appris à :

- Attribuer des rôles Azure et des rôles personnalisés pour accéder aux ressources Azure.
- Créer et gérer l’accès aux applications avec des identités managées.
- Configurer et gérer l’accès dans Azure Key Vault.
- Récupérer de façon sécurisée un objet dans un coffre de clés.
- Explorer les fonctionnalités de Gestion des autorisations Microsoft Entra.

### Pour en savoir plus, effectuez des recherches en utilisant ces liens

- [Attribuer des rôles Azure à l’aide du portail Azure - Azure RBAC](https://learn.microsoft.com/fr-fr/azure/role-based-access-control/role-assignments-steps)
- [Créer ou mettre à jour des rôles personnalisés Azure à l’aide du portail Azure - RBAC Azure](https://learn.microsoft.com/fr-fr/azure/role-based-access-control/custom-roles)
- [Configurer des identités managées à l’aide du portail Azure - ID Microsoft Entra](https://learn.microsoft.com/fr-fr/entra/identity/managed-identities-azure-resources/)
- [Attribuer un accès d’identité managée à une ressource à l’aide du portail Azure - ID Microsoft Entra](https://learn.microsoft.com/fr-fr/entra/identity/managed-identities-azure-resources/how-to-assign-access-azure-resource?pivots=identity-mi-access-cli)
- [Comprendre les définitions de rôle Azure - Azure RBAC](https://learn.microsoft.com/fr-fr/azure/role-based-access-control/role-definitions)
- [Accorder l’autorisation aux applications d’accéder à un coffre de clés Azure à l’aide d’Azure RBAC](https://learn.microsoft.com/fr-fr/azure/key-vault/general/assign-access-policy)
- [Créer et accéder à un secret dans Azure Key Vault](https://learn.microsoft.com/fr-fr/azure/key-vault/secrets/quick-create-portal)


---

# Déployer et configurer Accès global sécurisé Microsoft Entra

_https://learn.microsoft.com/fr-fr/training/modules/deploy-configure-microsoft-entra-global-secure-access/_


## Présentation

Les travailleurs d’aujourd’hui sont passés d’un environnement de bureau traditionnel à la possibilité de travailler depuis presque n’importe où. Ce changement du lieu de travail nécessite un périmètre réseau établi dans le cloud et qui prenne en compte les identités. Ce périmètre prenant en compte les identités est appelé Security Service Edge (SSE). La solution SSE de Microsoft inclut Accès Internet Microsoft Entra et Accès privé Microsoft Entra, qui sont désignés ensemble sous le nom d’Accès global sécurisé. Cette solution est fondée sur les principes de Confiance Zéro, qui met l’accent sur le privilège minimum, la vérification explicite et une hypothèse de violation pour garantir la sécurité à l’ère du cloud.

Scénario : Imaginez que votre entreprise dispose d’un représentant commercial travaillant à distance depuis un café. Le commercial doit accéder à des données client sensibles stockées dans les services cloud de l’entreprise. Pour garantir un accès sécurisé, le commercial utilise la solution Microsoft Security Service Edge (SSE). Dans ce cas, il s’agit d’Accès privé Microsoft Entra. Le représentant des ventes se connecte en toute sécurité au réseau de l’entreprise, authentifie son identité et accède aux données requises. L’accès se fait sans exposer de données à l’Internet public, tout en respectant les principes de Confiance Zéro que sont le privilège minimum et la vérification explicite.

Dans ce module, vous découvrez comment implémenter Accès privé Microsoft Entra et Accès Internet Microsoft Entra en utilisant Azure et Microsoft Entra.


## Explorer l'accès global sécurisé

![Diagramme du flux de processus de haut niveau pour l’accès sécurisé global dans Microsoft Entra. Microsoft Entra Private Access et Internet Access sont les passerelles vers les ressources.](https://learn.microsoft.com../../wwl-sci/deploy-configure-microsoft-entra-global-secure-access/media/global-secure-access-diagram.png)

### Solution Microsoft Security Service Edge (SSE)

Microsoft Entra Internet Access et Microsoft Entra Private Access sont une solution qui fusionne les contrôles d’accès réseau, d’identité et de point de terminaison afin de pouvoir accéder en toute sécurité à n’importe quelle application ou ressource, n’importe où. Vous pouvez activer l’orchestration des accès pour des employés, des partenaires commerciaux et des charges de travail numériques. Avec les fonctionnalités existantes de Microsoft Entra, surveillez et ajustez en continu l’accès des utilisateurs en temps réel dès que les autorisations ou le niveau de risque changent. L’accès global sécurisé utilise un portail unifié pour simplifier le déploiement et la gestion des fonctionnalités du contrôle d’accès. L’accès est fourni à partir du réseau Microsoft Wide Area sur son réseau mondial de régions et d’emplacements de périphérie. Ce réseau privé permet aux organisations de connecter des utilisateurs et des appareils à des ressources publiques et privées de façon transparente et sécurisée.

### Accès Internet Microsoft Entra

Accès Internet Microsoft Entra sécurise l’accès aux services Microsoft, aux applications SaaS et aux applications Internet publiques, tout en protégeant les utilisateurs, les appareils et les données contre les menaces Internet. Sécurisez l'accès aux applications Internet publiques via la passerelle Web sécurisée (SWG) d'Accès Internet Microsoft Entra, une solution orientée identité, sensible au contexte de l'appareil et fournie par le cloud.

#### Fonctionnalités clés

- Prévenir les attaques de relecture de jetons volés grâce aux vérification de réseau conforme au sein de l'accès conditionnel.
- Appliquez des restrictions de locataire universelles pour empêcher l'exfiltration de données.
- Journaux enrichis avec des signaux réseau et des signaux provenant des appareils.
- Améliorez la précision des évaluations des risques sur les utilisateurs, les emplacements et les appareils.
- Acquérez le trafic réseau à partir du client de bureau ou depuis un réseau distant.
- Profil de transfert du trafic Internet public dédié.
- Protégez l’accès utilisateur à l’Internet public lors de l’utilisation de Microsoft Secure Web Gateway (SWG).
- Régulez l'accès aux sites web en fonction de leurs catégories de contenu et de leurs noms de domaine.
- Appliquez des stratégies d'accès conditionnel universelles pour toutes les destinations Internet.

### Accès privé Entra de Microsoft

Accès privé Microsoft Entra fournit à vos utilisateurs un accès sécurisé à vos ressources privées d’entreprise. Il s’appuie sur les fonctionnalités du proxy d’application de Microsoft Entra et étend l’accès à n'importe quels ressource, port et protocole privés. Les utilisateurs distants se connectent aux applications privées à travers des environnements hybrides et multicloud, des réseaux privés et des centres de données, depuis n'importe quel appareil et réseau, sans nécessiter de VPN. Le service offre un accès adaptatif par application basé sur des stratégies d'accès conditionnel.

#### Fonctionnalités clés

- Accès basé sur la confiance zéro à une plage d’adresses IP et/ou de noms de domaine complets sans nécessiter un VPN hérité.
- Modernisez l'authentification des applications héritées avec l'accès conditionnel.
- Offrez une expérience utilisateur final transparente en déployant la solution parallèlement à vos solutions SSE tierces existantes.

### Avant de commencer

Gestion des licences :

- Licence Microsoft Entra ID P1 ou P2
- Licence Microsoft Entra Internet Access et/ou licence Microsoft Entra Private Access

Rôles :

- Rôle d'administrateur d'accès global sécurisé attribué à au moins un administrateur.

Il est recommandé de visiter le [Centre d’aide confiance zéro](https://learn.microsoft.com/fr-fr/security/zero-trust/) pour planifier votre implémentation. En outre, vous pouvez apporter toutes les modifications de configuration dans le Centre d’administration Microsoft Entra à l’adresse [https://entra.microsoft.com](https://entra.microsoft.com).


## Déployer et configurer l'accès Internet Microsoft Entra

Quatre grandes étapes sont nécessaires pour déployer l'accès Internet Microsoft Entra au sein de votre entreprise. Une fois ces quatre étapes terminées, les utilisateurs ayant installé le client d’accès sécurisé global sur leur appareil Windows peuvent accéder en toute sécurité aux ressources Microsoft depuis n’importe quel emplacement. Les stratégies d’accès conditionnel pour Microsoft trafic sont appliquées uniquement lorsque l’utilisateur dispose du client Global Secure Access. Le trafic Microsoft est accessible via une connectivité réseau à distance sans le client Global Secure Access, mais la stratégie d’accès conditionnel n’est pas appliquée sur ce trajet.

##### Étapes

| Étapes | Description |
|---|---|
| 1. Activez le profil de transfert de trafic Microsoft. | Une fois le profil Microsoft activé, l'accès Internet Microsoft Entra capture le trafic à destination des services Microsoft, comme Exchange Online et SharePoint Online. |
| 2. Installez le client d’accès sécurisé global sur les appareils des utilisateurs finaux. | Téléchargez et installez l’application cliente pour capturer et contrôler l’accès à partir du client. |
| 3. Activez les restrictions de locataire. | Configurer les locataires/ organisations autorisés ou bloqués |
| 4. Activez la signalisation améliorée d’accès sécurisé global et l’accès conditionnel. | Utilisez l’accès conditionnel et l’accès sécurisé global pour empêcher les attaques. |

### Activez le profil de transfert de trafic Microsoft.

1. Connectez-vous au Centre d’administration Microsoft Entra en tant qu’administrateur d’accès sécurisé global.
2. Accédez à Accès global sécurisé > Connecter > Redirection du trafic.
3. Activez le profil de trafic Microsoft.

Active le transfert du trafic Microsoft et crée les configurations suivantes dans Microsoft Entra :

| Configuration | Description |
|---|---|
| Stratégies (routage réseau) | 1. **Exchange Online**, 2. **SharePoint Online et OneDrive Entreprise**, et 3. **Entra ID et MS Graph** : ceux-ci utilisent des noms de domaine complets ou des sous-réseaux IP pour gérer le trafic réseau. |
| Stratégie d’accès conditionnel | **Stratégies d’accès conditionnel liées** : capture tout le trafic vers les services Microsoft, route vers les stratégies réseau définies précédemment si des conditions sont remplies. |
| Utilisateur et groupe | Spécifiez des utilisateurs ou des groupes spécifiques auxquels ce transfert de trafic s’applique. |

Pour plus d’informations, consultez [Activer et gérer le transfert de trafic Microsoft](https://learn.microsoft.com/fr-fr/entra/global-secure-access/how-to-manage-microsoft-profile).

### Déployer un client d'accès global sécurisé pour Windows (ou Android)

Le client est rapide et facile à installer. Il peut être déployé via des outils de gestion des appareils mobiles comme Microsoft Intune ou installé manuellement sur chaque appareil. Vous devez télécharger le client auprès du centre d’administration Microsoft Entra, puis utiliser les méthodes de déploiement de votre choix.

##### Télécharger le client

1. Connectez-vous au Centre d’administration Microsoft Entra en tant qu’administrateur d’accès sécurisé global.
2. Accédez à Accès global sécurisé > Connecter > Téléchargement du client.
3. Sélectionnez Télécharger le client.

##### Installer le client

1. Copiez le fichier d’installation du client d'accès global sécurisé sur votre ordinateur client.
2. Exécutez le fichier d’installation GlobalSecureAccessClient.exe. Acceptez les termes du contrat de licence logicielle.
3. Le client est installé, et les utilisateurs sont invités à se connecter avec leurs informations d’identification Microsoft Entra.
4. Lorsque les utilisateurs se connectent, l’icône de connexion devient verte. Double-cliquer cette icône ouvre une notification affichant des informations client et l'état connecté.

Vous pouvez installer le client Android à la place en utilisant Microsoft Intune ou Microsoft Defender for Endpoint sur Android. Le processus est similaire, mais vous obtenez l’application cliente auprès du store Android.

### Configurer les restrictions de locataire

Les administrateurs utilisent des restrictions de locataire pour contrôler l’accès des utilisateurs aux locataires externes sur leur réseau. Les restrictions de locataire, avec des paramètres d’accès entre locataires, ajoutent des restrictions au niveau du locataire ainsi qu'une granularité accrue, permettant notamment le contrôle par utilisateur individuel, par groupe et par application. Elles déplacent la gestion des politiques, auparavant centralisée sur les proxys réseau, vers un portail basé sur le cloud. Autorisez les identités internes, telles que les employés, à accéder à des locataires externes spécifiques sur votre réseau managé. Bloquez l'accès aux locataires non autorisés pour les identités internes. Empêchez les identités externes, telles que les prestataires et les fournisseurs, d'accéder à l'ensemble des locataires externes.

##### Configurer les Restrictions du client

1. Connectez-vous au Centre d’administration Microsoft Entra en tant qu’Administrateur de la sécurité.
2. Accédez à Identité > Identités externes > Paramètres d’accès interlocataire, puis sélectionnez Paramètres organisationnels.
3. Sélectionnez **Ajouter une organisation**.
4. Dans le volet **Ajouter une organisation**, tapez le nom de domaine complet (ou ID de l’abonné) de l’organisation.
5. Sélectionnez l’organisation dans les résultats de la recherche, puis sélectionnez Ajouter. L’organisation apparaît dans la liste Paramètres organisationnels . À ce stade, tous les paramètres d’accès de cette organisation sont hérités de vos paramètres par défaut. Pour modifier les paramètres de cette organisation, sélectionnez le lien Hérité de la valeur par défaut sous la colonne Accès entrant ou Accès sortant.
6. Modifiez les paramètres de l’organisation.

##### Activer l'accès global sécurisé

Une fois les politiques de restriction de locataire créées, vous pouvez utiliser l'accès global sécurisé pour appliquer l'étiquetage des restrictions de locataire. Un administrateur possédant à la fois les rôles d'administrateur de l'accès global sécurisé et d'administrateur de la sécurité doit suivre les étapes suivantes pour activer l'application via l'accès global sécurisé.

1. Connectez-vous au Centre d’administration Microsoft Entra en tant qu’administrateur d’accès sécurisé global.
2. Accédez à Accès global sécurisé > Paramètres globaux > Gestion des sessions > Restrictions liées au locataire.
3. Sélectionnez le bouton bascule pour Activer l’étiquetage pour appliquer des restrictions de locataire sur votre réseau.
4. Sélectionnez Enregistrer.

##### Fonctionnement

![Schéma du flux de processus des restrictions de locataire. Une requête provient d'un locataire. Le locataire est comparé à la politique de restriction.](https://learn.microsoft.com../../wwl-sci/deploy-configure-microsoft-entra-global-secure-access/media/tenant-restrictions-flow.png)

| Étapes | Description |
|---|---|
| 1. | Contoso configure une stratégie **de restrictions de locataire v2** dans ses paramètres d’accès interlocataire pour bloquer tous les comptes externes et les applications externes. Contoso applique la stratégie en utilisant l'accès global sécurisé et des restrictions universelles pour les locataires. |
| 2. | Un utilisateur disposant d’un appareil géré par Contoso tente d’accéder à une application intégrée Microsoft Entra avec une identité externe non approuvée. |
| 3. | Protection au niveau du plan d'authentification : Microsoft Entra ID, en appliquant la politique de Contoso, bloque l'accès des comptes externes non approuvés aux locataires externes. |
| 4. | Protection du plan de données : avec les restrictions universelles de locataire v2 via Global Secure Access, la protection du plan de données couvre Microsoft Graph. Si l’utilisateur tente de réutiliser un jeton Microsoft Entra ID émis infiltré pour accéder à Microsoft Graph, la requête est bloquée. Pour SharePoint Online, toute tentative d’accès anonyme aux ressources est également bloquée. La protection du plan de données pour les applications tierces telles que Slack n’entre pas dans le périmètre. |

### Activer la signalisation améliorée d’accès sécurisé global et l’accès conditionnel

Les organisations qui utilisent l’accès conditionnel en même temps que l'accès global sécurisé peuvent empêcher les accès malveillants aux applications Microsoft, aux applications SaaS et aux applications métier privées. Vous pouvez configurer plusieurs conditions pour fournir une défense en profondeur. Ces conditions peuvent inclure la conformité de l’appareil, l’emplacement et d’autres éléments pour assurer la protection contre l’usurpation de l’identité de l’utilisateur ou le vol de jetons. L'accès global sécurisé introduit le concept de réseau conforme au sein de l’accès conditionnel. Cette vérification de la conformité du réseau garantit que les utilisateurs se connectent depuis une connectivité réseau vérifiée.

Le client d'accès global sécurisé installé sur les appareils, ou les utilisateurs situés derrière des réseaux distants configurés, permet aux administrateurs de sécuriser les ressources via un réseau conforme avec des contrôles d'accès conditionnel avancés. Cette fonctionnalité de réseau conforme simplifie la gestion des administrateurs en évitant d'avoir à maintenir une liste des adresses IP de tous les sites de l'organisation. Les administrateurs n'ont plus besoin de diriger le trafic vers les points de sortie VPN de l'organisation pour garantir la sécurité. L'évaluation continue de l'accès avec la fonctionnalité de réseau conforme est actuellement prise en charge pour SharePoint Online. Elle permet de renforcer la défense en profondeur grâce à la protection contre la relecture de jetons volés.

##### Activer la signalisation d’accès global sécurisé

1. Connectez-vous au Centre d’administration Microsoft Entra en tant qu’administrateur d’accès sécurisé global.
2. Accédez à Global Secure Access > Paramètres globaux > Gestion des sessions > Accès adaptatif.
3. Utilisez le bouton bascule pour Activer la signalisation d’Accès global sécurisé dans l’accès conditionnel.
4. Accédez à Protection > Accès conditionnel > Emplacements nommés. Confirmez que vous avez un emplacement appelé Tous les emplacements du réseau conforme avec le type d’emplacement Accès au réseau. Les organisations peuvent marquer cet emplacement comme approuvé.

##### Créer votre stratégie d’accès conditionnel pour les réseaux

1. Connectez-vous au Centre d’administration Microsoft Entra en tant qu’administrateur d’accès conditionnel au moins.
2. Accédez à Protection > Accès conditionnel.
3. Sélectionnez Créer une stratégie.
4. Donnez un nom à votre stratégie. Nous recommandons aux organisations de créer une norme explicite pour les noms de leurs stratégies.
5. Sous Attributions, sélectionnez Utilisateurs ou identités de charge de travail.
  - Sous Inclure, sélectionnez Tous les utilisateurs.
  - Sous Exclure, sélectionnez Utilisateurs et groupes, puis choisissez les comptes d’accès d’urgence ou de secours de votre organisation.

6. Passez en revue Ressources cibles > Inclure, puis sélectionnez Sélectionner des applications.
  - Choisissez Office 365 Exchange Online et/ou Office 365 SharePoint Online et/ou une de vos applications SaaS.
  - L'application cloud spécifique Office 365 spécifique dans le sélecteur n'étant actuellement PAS prise en charge, ne la sélectionnez pas.

7. Passez en revue Conditions > Emplacement.
  - Définissez Configurer sur Oui.
  - Sous Inclure, sélectionnez Tous les emplacements.
  - Sous Exclure, sélectionnez Emplacements sélectionnés.
    - Sélectionnez Tous les emplacements du réseau conforme.

  - Choisissez Sélectionner.

8. Explorez les contrôles d’accès :
  - Accorder, sélectionnez Bloquer l’accès, puis Sélectionner.

9. Confirmez vos paramètres et réglez Activer la stratégie sur Activé.
10. Sélectionnez le bouton Créer pour créer votre stratégie.


## Déployer et configurer Accès privé Microsoft Entra

Comme pour la configuration d’Accès Internet Microsoft Entra, quatre grandes étapes sont nécessaires pour déployer Accès privé Microsoft Entra au sein de votre entreprise. Une fois ces quatre étapes effectuées, les utilisateurs disposant d’un appareil Windows sur lequel le client Accès global sécurisé est installé peuvent se connecter à vos ressources principales via une application Accès rapide et un connecteur de réseau privé.

##### Étapes

| Étapes | Description |
|---|---|
| 1. Configurer un connecteur et un groupe de connecteurs de réseau privé Microsoft Entra. | Créez une connexion entre un serveur local et Accès global sécurisé. |
| 2. Configurer l’Accès rapide à vos ressources privées. | Définissez des noms de domaine complets spécifiques (FQDN) ou des adresses IP de ressources privées à inclure dans Accès privé Microsoft Entra. |
| 3. Activer le profil de transfert de trafic d’Accès privé. | Activez Accès privé et liez le routeur local aux réseaux distants. |
| 4. Installer et configurer le client Accès global sécurisé sur les appareils des utilisateurs finaux. | Déployez le logiciel client sur des appareils afin qu’ils puissent accéder au flux du trafic. |

### Configurer un connecteur de réseau privé Microsoft Entra et des groupes de connecteurs

Les connecteurs sont des agents légers qui se trouvent sur un serveur dans un réseau privé et facilitent la connexion sortante au service Global Secure Access. Les connecteurs doivent être installés sur un serveur Windows Server qui a accès aux ressources et applications principales. Vous pouvez organiser des connecteurs dans les groupes de connecteurs, et chaque groupe gère le trafic vers des applications spécifiques.

##### Configuration du serveur Windows Server pour des connecteurs

Le connecteur de réseau privé Microsoft Entra nécessite un serveur exécutant Windows Server 2016 ou une version ultérieure. Vous installez le connecteur de réseau privé sur le serveur. Ce serveur de connecteur doit se connecter au service Accès privé Microsoft Entra et au service proxy d’application et aux ressources privées ou applications que vous envisagez de publier.

- Pour bénéficier d’une haute disponibilité dans votre environnement, nous vous recommandons d’utiliser plusieurs serveurs Windows.
- La version minimale de .NET requise pour le connecteur est v4.7.2+.
- Exiger que tls (Transport Layer Security) 1.2 soit activé sur Windows Server.

Ouvrir des ports pour le **trafic sortant**

| Numéro de port | Ce pourquoi le port est utilisé |
|---|---|
| 80 | Téléchargement de la liste de révocation de certificats lors de la validation du certificat TLS/SSL |
| 443 | Toutes les communications sortantes avec le service de proxy d’application |

Autoriser l’accès à certaines URL

| URL | Port | Ce pourquoi le port est utilisé |
|---|---|---|
| `site`.msappproxy.net et `site`.servicebus.windows.net | 443/HTTPS | Communication entre le connecteur et le service cloud Proxy d'application |
| crl3.digicert.com, crl4.digicert.com, ocsp.digicert.com, crl.microsoft.com, oneocsp.microsoft.com et ocsp.msocsp.com | 80/HTTP | Le connecteur utilise ces URL pour vérifier les certificats. |
| login.windows.net, secure.aadcdn.microsoftonline-p.com, `site`.microsoftonline.com, `site`.microsoftonline-p.com, `site`.msauth.net, `site`.msauthimages.net, `site`.msecnd.net, `site`.msftauth.net, `site`.msftauthimages.net, `site`.phonefactor.net, enterpriseregistration.windows.net, management.azure.com, policykeyservice.dc.ad.msft.net, ctldl.windowsupdate.com et [www.microsoft.com/pkiops](https://www.microsoft.com/pkiops) | 443/HTTPS | Le connecteur utilise ces URL lors du processus d'inscription. |
| ctldl.windowsupdate.com et [www.microsoft.com/pkiops](https://www.microsoft.com/pkiops) | 80/HTTP | Le connecteur utilise ces URL lors du processus d'inscription. |

##### Installer le connecteur en utilisant Microsoft Entra

1. Connectez-vous au Centre d’administration Microsoft Entra en tant qu’administrateur général du répertoire qui utilise le Proxy d’application.
2. Sélectionnez votre nom d’utilisateur en haut à droite. Vérifiez que vous êtes connecté à un annuaire qui utilise le proxy d’application. Si vous devez changer de répertoire, sélectionnez Changer de répertoire et choisissez un répertoire qui utilise le service Proxy d’application.
3. Accédez à Accès global sécurisé > Connecter > Connecteurs.
4. Sélectionnez Télécharger le service de connecteur.
5. Lisez les conditions d'utilisation du service. Quand vous êtes prêt, sélectionnez Accepter les conditions d’utilisation et télécharger.
6. Installez le connecteur à l’aide de l’option Exécuter en bas de l’écran.
7. Installez le service en suivant les instructions de l’Assistant. Quand vous êtes invité à inscrire le connecteur auprès du proxy d’application pour votre locataire Microsoft Entra, fournissez vos informations d’identification d’administrateur général.

##### Vérifier le connecteur installé

Sur Windows Server :

1. Sélectionnez la clé Windows et entrez services.msc pour ouvrir le Gestionnaire de services Windows.
2. Vérifiez que l'état des deux services suivants est Exécution en cours.
  - Le connecteur de réseau privé Microsoft Entra active la connectivité.
  - Connector Updater pour les réseaux privés Microsoft Entra est un service de mise à jour automatisé.
  - Régulièrement, ce service recherche de nouvelles versions du connecteur et le met à jour si besoin.

3. Si l’état des services n’est pas En cours d’exécution, cliquez avec le bouton droit sur chaque service à sélectionner et choisissez Démarrer.

Dans Microsoft Entra :

1. Connectez-vous au Centre d’administration Microsoft Entra en tant qu’administrateur général du répertoire qui utilise le Proxy d’application.
2. Accédez à Accès global sécurisé > Connecter > Connecteurs.
  - Tous les connecteurs et les groupes de connecteurs apparaissent sur cette page.

3. Vérifiez les détails en visualisant le connecteur.
  - Développez le connecteur pour voir les détails.
  - Une étiquette verte active indique que votre connecteur peut se connecter au service. Toutefois, même si l'étiquette est verte, un problème réseau peut empêcher le connecteur de recevoir les messages.

##### Créer des groupes de connecteurs

1. Pour des affectations plus rapides, vous pouvez regrouper différents connecteurs.
2. Accédez à Accès global sécurisé > Connecter > Connecteurs.
3. Sélectionnez Nouveau groupe de connecteurs.
4. Donnez un nom à votre nouveau groupe de connecteurs, puis utilisez le menu déroulant pour sélectionner les connecteurs qui appartiennent à ce groupe.
5. Cliquez sur Enregistrer.

### Configurer l’accès rapide pour Accès global sécurisé

Avec l’accès sécurisé global, vous pouvez définir des noms de domaine complets (FQDN) spécifiques ou des adresses IP de ressources privées à inclure dans le trafic pour Accès privé Microsoft Entra. Les employés de votre organisation peuvent ensuite accéder aux applications et aux sites que vous spécifiez. Découvrez comment configurer l’accès rapide pour Accès privé Microsoft Entra.

##### Configurer le nom de l’accès rapide et le groupe de connecteurs

La page Accès rapide vous permet d’entrer un nom pour l’application Accès rapide, de sélectionner un groupe de connecteurs et d’ajouter des segments d’application, notamment des noms de domaine complets et des adresses IP. Vous pouvez effectuer les trois étapes en même temps ou ajouter les segments d’application une fois la configuration initiale terminée.

1. Connectez-vous au centre d’administration Microsoft Entra avec les rôles appropriés.
2. Accédez à Accès global sécurisé > Applications > Accès rapide.
3. Entrez un nom. Nous vous recommandons d’utiliser le nom Accès rapide.
4. Sélectionnez un groupe de connecteurs dans le menu déroulant. Les groupes de connecteurs existants apparaissent dans le menu déroulant.
  - Créé à l’étape précédente.

5. Sélectionnez le bouton Enregistrer en bas de la page pour créer votre application « Accès rapide » sans noms de domaine complets ni adresses IP.

##### Ajouter un segment d’application

La partie **Ajouter un segment d’application Accès rapide** de ce processus vous permet de définir les noms de domaine complets et les adresses IP à inclure dans le trafic pour Accès privé Microsoft Entra. Vous pouvez ajouter ces ressources lors de la création de l’application Accès rapide et revenir plus tard pour en ajouter d’autres ou les modifier.

1. Connectez-vous au Centre d’administration Microsoft Entra.
2. Accédez à Accès global sécurisé > Applications > Accès rapide.
3. Sélectionnez **Ajouter un segment d’application Accès rapide**.
4. Dans le volet **Créer un segment d’application**, sélectionnez un type de destination.
5. Entrez les détails appropriés pour le type de destination sélectionné. Les champs suivants changent en fonction de ce que vous sélectionnez.
  - Adresse IP :
    - Adresse du protocole Internet version 4 (IPv4), telle que 192.0.2.1, qui identifie un appareil sur le réseau.
    - Indiquez les ports que vous souhaitez inclure.

  - Nom de domaine complet (y compris les noms de domaine complets génériques) :
    - Nom de domaine qui spécifie l’emplacement exact d’un ordinateur ou d’un hôte dans le système DNS (Domain Name System).
    - Indiquez les ports à inclure.
    - NetBIOS n’est pas pris en charge. Par exemple, utilisez contoso.local/app1 au lieu de contoso/app1.

  - Plage d’adresses IP (CIDR) :
    - Le routage CIDR (Classless InterDomain Routing) représente une plage d’adresses IP. Une adresse IP est suivie d’un suffixe indiquant le nombre de bits réseau dans le masque de sous-réseau.
    - Par exemple, 192.0.2.0/24 indique que les 24 premiers bits de l’adresse IP représentent l’adresse réseau, tandis que les 8 bits restants représentent l’adresse de l’hôte.
    - Indiquez l’adresse de départ, le masque de réseau et les ports.

  - Plage d’adresses IP (IP à IP) :
    - Plage d’adresses IP allant de l’adresse IP de début (par exemple, 192.0.2.1) jusqu’à l’adresse IP de fin (par exemple, 192.0.2.10).
    - Indiquez le début, la fin et les ports de l’adresse IP.

  - Entrez les ports et sélectionnez le bouton Appliquer.  Le tableau suivant fournit les ports les plus couramment utilisés et leurs protocoles réseau associés :    Port Protocole     22 Secure Shell (SSH)   80 Protocole HTTP (Hypertext Transfer Protocol)   443 HTTPS (Hypertext Transfer Protocol Secure)   445 Partage de fichiers SMB (Server Message Blocks)   3389 Protocole RDP (Bureau à distance Protocol)
    - Séparez plusieurs ports par une virgule.
    - Spécifiez des plages de ports avec un trait d’union.
    - Les espaces entre les valeurs sont supprimés lorsque vous appliquez les modifications.
    - Par exemple, 400-500, 80, 443.

6. Sélectionnez le bouton Enregistrer quand vous avez terminé.

##### Affecter des utilisateurs et des groupes pour l’accès rapide

1. Connectez-vous au Centre d’administration Microsoft Entra.
2. Accédez à Accès global sécurisé > Applications > Accès rapide.
3. Sélectionnez le bouton Modifier les paramètres d’application dans Accès rapide.
4. Sélectionnez Utilisateurs et groupes dans le menu latéral.
5. Ajoutez des utilisateurs et des groupes selon vos besoins.

Vous pouvez activer des stratégies d’accès conditionnel spécifiques en fonction des besoins.

### Activer le transfert de trafic – Accès privé Microsoft Entra

Maintenant que votre application Accès rapide est configurée, vos ressources privées ajoutées et les utilisateurs affectés à l’application, vous pouvez activer le profil d’accès privé à partir de la zone de transfert de trafic d’Accès global sécurisé.

Le profil de transfert du trafic Accès privé achemine le trafic vers votre réseau privé via le client Global Secure Access. L’activation de ce profil de transfert de trafic permet aux travailleurs distants de se connecter à des ressources internes sans aucun VPN. Avec les fonctionnalités d’Accès privé Microsoft Entra, vous pouvez contrôler les ressources privées à tunneliser via le service et appliquer des stratégies d’accès conditionnel pour sécuriser l’accès à ces services. Une fois vos configurations en place, vous pouvez afficher et gérer toutes ces configurations à partir d’un seul emplacement.

1. Connectez-vous au Centre d’administration Microsoft Entra.
2. Accédez à Accès global sécurisé > Connecter > Transfert du trafic.
3. Cochez la case Profil Accès privé.

### Déployer un client Accès global sécurisé pour Windows (ou Android)

Le client est rapide et facile à installer. Il peut être déployé via des outils de gestion des appareils mobiles comme Microsoft Intune ou installé manuellement sur chaque appareil. Vous devez télécharger le client auprès du centre d’administration Microsoft Entra, puis utiliser les méthodes de déploiement de votre choix.

##### Télécharger le client

1. Connectez-vous au Centre d’administration Microsoft Entra en tant qu’administrateur Global Secure Access.
2. Accédez à Accès global sécurisé > Connecter > Téléchargement du client.
3. Sélectionnez le client de téléchargement.

##### Installer le client

1. Copiez le fichier d’installation du client Accès global sécurisé sur votre ordinateur client.
2. Exécutez le fichier d’installation GlobalSecureAccessClient.exe. Acceptez les termes du contrat de licence logicielle.
3. Le client est installé et les utilisateurs sont invités à se connecter avec leurs informations d’identification Microsoft Entra.
4. Lorsque les utilisateurs se connectent, l’icône de connexion devient verte. Double-cliquer sur l'icône de connexion ouvre une notification avec des informations du client indiquant une connexion établie.

Vous pouvez installer le client Android à la place en utilisant Microsoft Intune ou Microsoft Defender for Endpoint sur Android. Le processus est similaire, mais vous obtenez l’application cliente auprès du store Android.


## Découvrir comment utiliser le tableau de bord pour piloter Accès global sécurisé

Pour accéder au tableau de bord :

1. Connectez-vous au centre d’administration Microsoft Entra en tant qu’administrateur d’accès sécurisé global (Global Secure Access).
2. Accédez à Accès global sécurisé > Tableau de bord.

Le tableau de bord de l’Accès global sécurisé vous fournit des visualisations du trafic réseau acquis par les services privés Microsoft Entra et ceux de l’Accès Internet Microsoft Entra. Le tableau de bord agrège les données de vos configurations réseau, notamment les appareils, les utilisateurs et les locataires. Le tableau de bord utilise plusieurs widgets qui vous offrent une visibilité sur plusieurs types de données différents :

- Volume d’appareils utilisant le client Global Secure Access
- Modifications du nombre d’appareils actifs
- Alertes et notifications importantes
- Modèles d’utilisation des services
- Destinations les plus utilisées
- Utilisateurs uniques accédant au réseau sur tous vos locataires
- Catégories de sites web les plus populaires
- Segments d’application privée les plus utilisés

### Capture instantanée d’accès sécurisé global

Ce widget fournit un résumé du nombre d’utilisateurs et d’appareils qui utilisent le service et du nombre d’applications qui ont été sécurisées par le biais du service.

- Utilisateurs : nombre d’utilisateurs distincts vus au cours des dernières 24 heures. Les données utilisent le nom d’utilisateur principal (UPN).
- Utilisateurs : nombre d’utilisateurs distincts vus au cours des dernières 24 heures. Les données utilisent l’ID de l’appareil.
- Charges de travail : nombre de destinations distinctes observées au cours des dernières 24 heures. Les données utilisent des noms de domaine complets (FQDN) et des adresses IP. L’instantané Accès global sécurisé dispose d’un filtre pour afficher les données par Accès Internet, Accès privé ou trafic Microsoft.

### Alertes et notifications (prévisualisation)

Ce widget affiche l’activité réseau et permet d’identifier les activités suspectes ou les tendances identifiées par les données réseau. Voici des alertes courantes :

- Réseau distant non sain : Un réseau distant non sain a un ou plusieurs liens d’appareil déconnectés.
- Augmentation de l’activité des locataires externes : Le nombre d’utilisateurs accédant à des locataires externes a augmenté.
- Incohérence entre jeton et appareil : le jeton d’origine est utilisé sur un autre appareil.
- Contenu web bloqué : L’accès au site web est bloqué. Accédez à une page de détails de l’alerte associée avec des informations supplémentaires.

### Profilage de l’utilisation (prévisualisation)

Le widget de profilage de l’utilisation affiche les modèles d’utilisation sur une période sélectionnée. Sélectionnez le filtre Afficher par pour afficher les catégories d’utilisation suivantes :

- Opérations
- Utilisateurs
- Appareils
- Octets envoyés
- Octets reçus

### Destinations les plus utilisées

Le widget des destinations les plus visitées affiche tous les types de trafic et trie par nombre de transactions. Vous pouvez sélectionner un autre type de trafic pour affiner les résultats. Plusieurs filtres sont disponibles :

- Transactions : destinations avec le plus grand nombre de transactions, affichant le nombre total de transactions au cours des dernières 24 heures.
- Utilisateurs : destinations les plus utilisées par les utilisateurs, montrant le nombre d’utilisateurs distincts (UPN) ayant accédé à la destination au cours des dernières 24 heures.
- Appareils : destinations les plus utilisées par les appareils, montrant le nombre d’ID d’appareil distincts ayant accédé à la destination au cours des dernières 24 heures.
- Octets envoyés : destinations (adresses IP) avec le nombre maximal d’octets envoyés, montrant le nombre total d’octets envoyés au cours des dernières 24 heures.
- Octets reçus : destinations (adresses IP) avec le nombre maximal d’octets reçus, montrant le nombre total d’octets reçus au cours des dernières 24 heures. Sélectionnez le bouton Afficher toutes les destinations pour afficher plus de détails sur les destinations.

### Accès entre locataires

L’accès sécurisé global offre une visibilité sur le nombre d’utilisateurs et d’appareils qui accèdent à d’autres locataires. Le widget affiche les informations suivantes :

- Connexions : nombre de connexions via Microsoft Entra ID aux services Microsoft au cours des dernières 24 heures. Ce widget vous fournit des informations sur l’activité dans votre locataire.
- Nombre total de locataires distincts : nombre d’ID de locataires distincts observés au cours des dernières 24 heures.
- Locataires invisibles : nombre d’ID de locataires distincts qui ont été vus au cours des dernières 24 heures, mais pas au cours des sept derniers jours.
- Utilisateurs : nombre de connexions utilisateur distinctes à d’autres locataires au cours des dernières 24 heures.
- Appareils : nombre d’appareils distincts qui se sont connectés à d’autres locataires au cours des dernières 24 heures. Sélectionnez le bouton **Configurer les restrictions de locataire** pour accéder à la zone de gestion de session de l’accès sécurisé global, où vous pouvez vérifier les paramètres de vos restrictions de locataire.

### Filtrage des catégories Web

Le widget de filtrage des catégories web affiche les principales catégories de contenu web qui sont bloquées ou autorisées. Ces catégories peuvent être utilisées pour déterminer les sites ou catégories de sites que vous voudriez bloquer. Triez les résultats à l’aide des catégories suivantes :

- Transactions : affiche le nombre total de transactions au cours des 24 dernières heures.
- Utilisateurs : nombre d’utilisateurs distincts (UPN) ayant accédé à la destination au cours des dernières 24 heures.
- Appareils : nombre d’ID d’appareils distincts accédant à la destination au cours des dernières 24 heures. Sélectionnez Afficher toutes les catégories web pour afficher plus de détails sur le trafic réseau.

### Statuts des appareils

Les widgets d’état de l’appareil affichent les appareils actifs et inactifs que vous avez déployés.

- Appareils actifs : nombre d’ID d’appareils distincts observés au cours des dernières 24 heures et % de changement au cours de cette période.
- Appareils inactifs : nombre d’ID d’appareils distincts qui ont été vus au cours des sept derniers jours, mais pas au cours des dernières 24 heures. Le % de changement au cours des dernières 24 heures s’affiche également.


## Créer des réseaux distants pour les utiliser avec Accès global sécurisé

Les réseaux distants sont des emplacements distants, telles que des filiales, ou des réseaux qui nécessitent une connectivité Internet. La configuration des réseaux distants connecte vos utilisateurs dans des emplacements distants à l’Accès global sécurisé. Une fois qu’un réseau distant est configuré, vous pouvez attribuer un profil de transfert de trafic pour gérer le trafic réseau de votre entreprise. Global Secure Access fournit une connectivité réseau à distance, ce qui vous permet d’appliquer des stratégies de sécurité réseau à votre trafic sortant.

Il existe plusieurs façons de connecter des réseaux distants à Global Secure Access. En résumé, vous créez un tunnel IPSec (Internet Protocol Security) entre un routeur principal, appelé équipement local du client (CPE), sur votre réseau distant et le point de terminaison Global Secure Access le plus proche. Tout le trafic internet est acheminé via le routeur principal du réseau distant pour l’évaluation de la stratégie de sécurité dans le cloud. L’installation d’un client n’est pas requise sur des appareils individuels.

Il existe cinq étapes principales pour configurer un réseau distant. Dans ce processus, vous créez un pont à partir d’un routeur local dans votre bureau vers l’accès global sécurisé. Ces étapes peuvent être effectuées dans le centre d’administration Microsoft Entra ou via l’API Microsoft Graph. Notez que la dernière étape est effectuée sur le routeur local.

| Étapes | Descriptif |
|---|---|
| Concepts de base | Définissez le nom de votre réseau distant et de la région où vous voulez vous connecter. |
| Connectivité | Entrez les données relatives à votre routeur local, à partir desquelles provient le signal. |
| Transfert de trafic | Ajoutez un profil de transfert de trafic pour définir le type de trafic Trafic réseau à autoriser. |
| Passer en revue la configuration | Dans cette étape, vous confirmez la configuration du réseau distant et collectez les paramètres que vous devez configurer dans le routeur local. |
| Configurer un routeur local | Utilisez la console de gestion de votre routeur local pour entrer les paramètres de connectivité Microsoft à l’étape précédente. |

### Configuration – Principes de base

1. Connectez-vous au Centre d’administration Microsoft Entra en tant qu’administrateur Global Secure Access.
2. Accédez à Accès global sécurisé > Connecter > Réseaux distants.
3. Onglet Informations de base : sélectionnez le bouton Créer un réseau distant et fournissez les détails.    Valeurs demandées     Nom   Région

### Configuration – Connectivité

1. Sélectionnez **Suivant : Connectivité**.    Valeurs demandées     Nom   Type d’appareil (généralement un routeur)   Adresse IP de l'appareil   Type de redondance à activer   Bande passante

### Activer – Profils de transfert de trafic

1. Sélectionnez **Suivant** pour ouvrir la configuration du transfert de trafic.
  - Vous pouvez créer un profil de transfert de trafic ou en sélectionner un créé dans Accès privé Microsoft Entra ou Accès Internet Microsoft Entra.

### Terminez la configuration – Configurez votre routeur local

Tous vos réseaux distants apparaissent sur la page Réseau distant. Sélectionnez le lien Afficher la configuration dans la colonne Détails de connectivité. Ces détails contiennent les informations de connectivité du côté Microsoft du canal de communication bidirectionnel que vous utilisez pour configurer votre CPE.

Avec les données de connexion Microsoft, mettez à jour la configuration du routeur local. Cette étape est effectuée dans la console de gestion de votre CPE, et non dans le Centre d’administration Microsoft Entra. Tant que vous n’effectuez pas cette étape, votre IPsec n’est pas configuré. IPsec est une communication bidirectionnelle. Les négociations du protocole IKE (Internet Key Exchange) se produisent entre deux parties avant que le tunnel ne soit correctement configuré. Donc, n’oubliez pas cette étape.


## Utiliser l’accès conditionnel avec l'accès global sécurisé

Après avoir déployé votre accès sécurisé global, vous pouvez utiliser l’accès conditionnel pour ajouter d’autres couches de sécurité et de protection. Les organisations qui utilisent l'accès conditionnel conjointement avec l'accès global sécurisé peuvent empêcher les accès malveillants aux applications Microsoft, aux applications SaaS et aux applications métiers privées en utilisant plusieurs conditions pour assurer une défense en profondeur. Ces conditions peuvent inclure la conformité de l’appareil, l’emplacement et d’autres éléments pour assurer la protection contre l’usurpation de l’identité de l’utilisateur ou le vol de jetons.

Plusieurs nouveaux types de vérifications sont introduits dans l'accès conditionnel avec l'accès global sécurisé :

| Vérification de l’accès conditionnel | Résultat |
|---|---|
| Vérification de la conformité réseau | Cette vérification de la conformité réseau garantit que les utilisateurs se connectent à partir d’un modèle de connectivité réseau vérifié pour leur locataire spécifique et qu’ils sont conformes aux stratégies de sécurité appliquées par les administrateurs. |
| Applications d’accès privé | L'application de politiques d'accès conditionnel à vos applications Microsoft Entra Private Access est un moyen puissant d'imposer des politiques de sécurité pour vos ressources internes et privées |
| Restauration de l’adresse IP source | Lorsqu’un proxy réseau basé sur le cloud se trouve entre les utilisateurs et leurs ressources, l’adresse IP vue par les ressources ne correspond pas à l’adresse IP source réelle. La restauration de l’adresse IP source dans l’accès global sécurisé permet une rétrocompatibilité pour les clients Microsoft Entra afin de continuer à utiliser l'adresse IP source d'origine de l'utilisateur. |

Pour utiliser les fonctionnalités de **vérification du réseau conforme** et de **restauration de l’adresse IP source**, la **signalisation de l’accès global sécurisé pour l’accès conditionnel** doit être activée. Cette étape ne doit être effectuée qu’une seule fois, avant d’accéder aux options directes d’accès conditionnel. Vous effectuez cette étape avant d’utiliser l’une des fonctionnalités ci-dessous dans l'accès conditionnel.

### Activer la signalisation de l’accès global sécurisé pour l’accès conditionnel

Pour activer le paramètre permettant d’autoriser la vérification de la conformité du réseau, l’administrateur doit procéder comme suit.

1. Connectez-vous au Centre d’administration Microsoft Entra en tant qu’administrateur d’accès sécurisé global.
2. Accédez à Global Secure Access > Paramètres globaux > Gestion des sessions > Accès adaptatif.
3. Sélectionnez le bouton bascule pour activer la signalisation de l'accès conditionnel pour Microsoft Entra ID (couvrant toutes les applications cloud). La signalisation de l'évaluation continue de l’accès est automatiquement activée pour Office 365 (version préliminaire).
4. Accédez à Protection > Accès conditionnel > Emplacements nommés.
  - Confirmez que vous avez un emplacement appelé Tous les emplacements du réseau conforme avec le type d’emplacement Accès au réseau. Les organisations peuvent marquer cet emplacement comme approuvé.

### Vérification de la conformité réseau

L'application du réseau conforme s'effectue au niveau du plan d'authentification et du plan de données (version préliminaire). Microsoft Entra ID effectue l'application au niveau du plan d'authentification au moment de l'authentification de l'utilisateur. L'application au niveau du plan de données fonctionne avec les services prenant en charge l'évaluation continue de l'accès. Actuellement, seuls Exchange Online et SharePoint Online prennent en charge cette fonctionnalité. Elle permet de renforcer la défense en profondeur grâce à la protection contre la relecture de jetons volés.

En utilisant cette vérification, vous pouvez garantir que d'autres organisations utilisant les services d'accès global sécurisé de Microsoft ne peuvent pas accéder à vos ressources. Par exemple : Contoso peut protéger ses services tels que Exchange Online et SharePoint Online derrière sa vérification de conformité réseau pour s’assurer que seuls les utilisateurs Contoso peuvent accéder à ces ressources. Si une autre organisation comme Fabrikam utilisait une vérification de réseau conforme, elle ne satisferait pas à la vérification du réseau conforme de Contoso.

##### Protéger vos ressources derrière le réseau conforme

La stratégie d'accès conditionnel de réseau conforme peut être utilisée pour protéger vos applications Microsoft et autres. Une stratégie type consiste à « bloquer » l'accès pour tous les emplacements réseau, sauf pour le réseau conforme.

1. Connectez-vous au Centre d’administration de Microsoft Entra en tant qu’administrateur d’accès conditionnel.
2. Accédez à Protection > Accès conditionnel.
3. Sélectionnez Créer une stratégie.
4. Donnez un nom à votre stratégie. Nous recommandons aux organisations de créer une norme explicite pour les noms de leurs stratégies.
5. Sous Attributions, sélectionnez Utilisateurs ou identités de charge de travail.
  - Sous Inclure, sélectionnez Tous les utilisateurs.
  - Sous Exclure, sélectionnez Utilisateurs et groupes, puis choisissez les comptes d’accès d’urgence ou de secours de votre organisation.

6. Sous Ressources cibles > , incluez, puis sélectionnez Sélectionner des applications.
  - Choisissez Office 365 Exchange Online et/ou Office 365 SharePoint Online et/ou une de vos applications SaaS.
  - L'application cloud spécifique Office 365 spécifique dans le sélecteur n'étant actuellement PAS prise en charge, ne la sélectionnez pas.

7. Sous Conditions > Emplacement.
  - Définissez Configurer sur Oui.
  - Sous Inclure, sélectionnez Tous les emplacements.
  - Sous Exclure, choisissez Emplacements sélectionnés.
    - Sélectionnez Tous les emplacements du réseau conforme.

  - Choisissez Sélectionner.

8. Sous Contrôles d’accès :
  - Accorder, sélectionnez Bloquer l’accès, puis Sélectionner.

9. Confirmez vos paramètres et réglez Activer la stratégie sur Activé.
10. Sélectionnez le bouton Créer pour créer votre stratégie.

### Accès conditionnel pour les applications d’accès privé

Vous pouvez créer une stratégie d’accès conditionnel pour vos applications d'accès rapide ou d'accès privé à partir de l'accès global sécurisé. Le démarrage du processus à partir de l'accès global sécurisé ajoute automatiquement l’application sélectionnée en tant que ressource cible pour la stratégie. Il vous suffit de configurer les paramètres de stratégie.

1. Connectez-vous au Centre d’administration de Microsoft Entra en tant qu’administrateur d’accès conditionnel.
2. Accédez à Accès global sécurisé > Applications > Applications d’entreprise.
3. Sélectionnez une application dans la liste.
4. Sélectionnez Accès conditionnel dans le menu latéral. Toutes les stratégies d’accès conditionnel existantes s’affichent dans une liste.
5. Sélectionnez Créer une stratégie. L'application sélectionnée apparaît dans les détails des ressources cibles.
6. Configurez les conditions, les contrôles d'accès et assignez les utilisateurs et groupes selon les besoins.

Le sélecteur Accès rapide et Accès privé est ajouté à partir de l'accès global sécurisé.

### Restauration de l’adresse IP source

La restauration de l’adresse IP source dans l’accès global sécurisé permet une rétrocompatibilité pour les clients Microsoft Entra afin de continuer à utiliser l'adresse IP source d'origine de l'utilisateur. Les administrateurs peuvent bénéficier des capacités suivantes :

- Continuez à appliquer des stratégies d'emplacement basées sur l'adresse IP source à la fois dans l'accès conditionnel et l'évaluation continue de l'accès.
- Les détections de risques d'Identity Protection obtiennent une vue cohérente de l'adresse IP source d'origine de l'utilisateur pour évaluer les différents scores de risque.
- L’adresse IP source d'origine de l'utilisateur est également disponible dans les journaux de connexion de Microsoft Entra.

##### Limitations connues

- Lorsque la restauration de l'adresse IP source est activée, vous ne pouvez voir que l'adresse IP source. L’adresse IP du service d'accès global sécurisé n’est pas visible.
- La restauration de l'adresse IP source n'est actuellement prise en charge que pour le trafic Microsoft, tel que SharePoint Online, Exchange Online, Teams et Microsoft Graph.
- Avec l'application stricte de l'emplacement par l'évaluation continue de l’accès, les utilisateurs sont bloqués bien qu'ils se trouvent dans une plage d'adresses IP approuvée.

##### Activation

La restauration de l'adresse IP source est activée lorsque vous activez la **signalisation de l'accès global sécurisé**. Aucune configuration ou modification supplémentaire ne devrait être requise.

### Exclusions d’utilisateurs

Les stratégies d’accès conditionnel sont des outils puissants. Nous vous recommandons d’exclure les comptes suivants de vos stratégies :

- **Comptes d’accès d’urgence ou de secours** pour empêcher le verrouillage du compte sur l’ensemble du locataire.
- **Comptes de service et principaux de service**, comme le compte de synchronisation Microsoft Entra Connect. Les comptes de service sont des comptes non interactifs qui ne sont liés à aucun utilisateur particulier.


## Explorez les journaux et les options de supervision avec Global Secure Access

Vous devez surveiller l’activité du trafic transitant par vos réseaux. Les journaux d’accès sécurisé global fournissent des points de données que vous pouvez examiner pour obtenir des insights sur votre trafic réseau.

### Journaux d’audit d’accès sécurisé global

Les journaux d’audit Microsoft Entra constituent une source précieuse d’informations lors de la recherche ou de la résolution des modifications apportées à votre environnement Microsoft Entra. Les modifications liées à Accès global sécurisé sont capturées dans les journaux d’audit. Les journaux comportent des catégories, telles que la politique de filtrage, les profils de transfert, la gestion des réseaux distants, et plus encore.

#### Accéder aux journaux d’audit depuis Accès global sécurisé ou depuis le centre d’administration Microsoft Entra

##### Depuis Accès global sécurisé

1. Connectez-vous au Centre d’administration Microsoft Entra au moyen d’un des rôles requis.
2. Accédez à Global Secure Access > Journaux d’audit. Les filtres sont préremplis avec les catégories et les activités liées à Accès global sécurisé.

##### À partir de Surveillance et intégrité de Microsoft Entra

1. Connectez-vous au Centre d’administration Microsoft Entra au moyen d’un des rôles requis.
2. Accédez à Identity > Monitoring & health > Journaux d’audit.
3. Sélectionnez la plage de dates sur laquelle doit porter la requête.
4. Ouvrez le filtre Service, sélectionnez Accès global sécurisé, puis Appliquer.
5. Ouvrez le filtre Catégorie, sélectionnez au moins une des options disponibles, puis Appliquer.

### Journaux de trafic (version préliminaire)

Les journaux de trafic Global Secure Access fournissent un résumé des connexions réseau et des transactions qui se produisent dans votre environnement. Ces journaux indiquent qui a accédé à quel trafic depuis où et avec quel résultat. Les journaux de trafic fournissent un instantané de toutes les connexions dans votre environnement et catégorisent le trafic. Les détails des journaux indiquent le type de trafic, la destination, l’adresse IP source, etc. Pour mieux comprendre ces détails, il est utile d’examiner les trois niveaux des journaux et la façon dont ils s’articulent entre eux.

Un utilisateur accédant à un site web représente une session et dans cette session, il peut y avoir plusieurs connexions, et dans cette connexion, il peut y avoir plusieurs transactions.

- Session : Une session commence avec la première URL à laquelle un utilisateur accède. Cette session peut ensuite ouvrir de nombreuses connexions, par exemple un site d’actualités qui contient plusieurs publicités provenant de plusieurs sites différents.
- Connexion : une connexion inclut l’adresse IP source et de destination, le port source et de destination, ainsi que le nom de domaine complet (FQDN). Les composants de la connexion comprennent 5 tuples.
- Transaction : une transaction est une paire de requête et de réponse unique.

### Comment afficher les journaux de trafic

1. Connectez-vous au centre d’administration Microsoft Entra avec au minimum le rôle Lecteur de rapports.
2. Global Secure Access > Surveillance > Journaux de trafic.

Différents filtres et options d’exportation sont disponibles pour les journaux de trafic.

### Journaux Office 365 enrichis (préversion)

Les Journaux Office 365 enrichis vous fournissent les informations nécessaires pour obtenir des insights sur le niveau de performance, l’expérience et la disponibilité des applications Microsoft 365 utilisées par votre organisation. Vous pouvez intégrer les journaux à un espace de travail Log Analytics ou à un outil SIEM (Security Information and Event Management) pour une analyse plus approfondie. Les journaux Microsoft 365 enrichis fournissent des informations sur les charges de travail Microsoft 365, ce qui vous permet d’examiner les données de diagnostic réseau, les données de performances et les événements de sécurité pertinents pour les applications Microsoft 365. Par exemple, si l’accès à Microsoft 365 est bloqué pour un utilisateur de votre organisation, vous devez savoir comment l’appareil de cet utilisateur se connecte à votre réseau.

##### Ces fichiers journaux fournissent

- Latence améliorée
- Informations supplémentaires ajoutées aux journaux d’origine
- Adresse IP précise

##### Comment afficher les journaux

L’affichage des journaux d’audit Microsoft 365 enrichis est un processus à deux étapes unique. Tout d’abord, collectez les journaux du trafic réseau de Global Secure Access et les journaux d’audit unifié Microsoft 365 vers le même point de terminaison (Microsoft Sentinel est l’espace de travail recommandé). Ensuite, créez votre propre requête de jointure pour corréler les deux tables, ou utilisez le classeur « Global Secure Access Enriched Microsoft 365 Logs », prêt à l’emploi, qui applique déjà les requêtes requises.

Note

Au lieu d’un flux de journaux enrichi distinct, utilisez les deux tables de journal existantes ( Microsoft 365 **OfficeActivity** et Global Secure Access **NetworkAccessTraffic**) et combinez les données à l’aide d’un ID de jeton unique. À ce stade, seuls les journaux SharePoint Online sont disponibles pour l’enrichissement des journaux.

##### Envoyer des journaux vers un point de terminaison

1. Connectez-vous au Centre d’administration de Microsoft Entra en tant qu’Administrateur de la sécurité.
2. Accédez à Identity > Monitoring & health > Paramètres de diagnostic.
3. Sélectionnez Ajouter un paramètre de diagnostic.
4. Donnez un nom à votre paramètre de diagnostic.
5. Sélectionnez **NetworkAccessTrafficLogs**.
6. Sélectionnez les détails de destination pour l’endroit où vous souhaitez envoyer les journaux. Choisissez tout ou partie des destinations suivantes :
  - Envoyer à l’espace de travail Log Analytics.
  - Archiver dans un compte de stockage.
  - Transmettre à un Event Hub.
  - Envoyer à la solution partenaire.

### Conservation et stockage des journaux

Journaux de trafic et journaux d’intégrité réseau distants : ces journaux sont conservés dans le système pendant 30 jours. Cette durée laisse suffisamment de temps pour passer en revue et analyser des activités récentes et l’état d’intégrité du réseau.

- Journaux d’audit : la période de rétention des journaux d’audit varie en fonction de votre licence Microsoft Entra ID.
- Journaux Office : les journaux Office sont conservés pendant une durée plus courte, jusqu’à seulement 24 heures.


## Évaluation du module

Choisissez la meilleure réponse à chacune des questions.

### Contrôle des connaissances


## Récapitulatif et ressources

Dans ce module, vous avez appris à configurer et à gérer la solution SSE (Security Service Edge) de Microsoft via Microsoft Entra Global Secure Access. Cette solution complète fournit un accès sécurisé à n’importe quelle application ou ressource n’importe où en fusionnant les contrôles d’accès réseau, d’identité et de point de terminaison dans une plateforme unifiée fournie par le cloud.

Vous avez exploré le déploiement et la configuration de Microsoft Entra Internet Access et Microsoft Entra Private Access, en comprenant comment chaque composant répond à différents besoins de sécurité. Microsoft Entra Internet Access protège les utilisateurs qui accèdent aux services Microsoft, aux applications SaaS et aux ressources Internet publiques via une passerelle web sécurisée centrée sur l’identité. Microsoft Entra Private Access fournit un accès sécurisé et sans VPN aux ressources d’entreprise privées dans les environnements hybrides et multiclouds.

Tout au long de ce module, vous avez acquis des connaissances pratiques sur les tâches d’implémentation clés, notamment :

- Activation des profils de transfert de trafic pour Microsoft, Internet et accès privé
- Déploiement du client Global Secure Access sur les appareils de l’utilisateur final
- Configuration des restrictions de locataire pour empêcher l’exfiltration des données
- Configuration de réseaux distants avec des tunnels IPsec pour la connectivité des succursales
- Création d’applications Accès rapide pour l’accès aux ressources privées
- Implémentation de stratégies d’accès conditionnel avec des vérifications réseau conformes et la restauration d’adresses IP sources
- Surveillance de l’activité du réseau à l'aide du tableau de bord Global Secure Access et des différents types de logs

En effectuant ce module, vous disposez maintenant des connaissances fondamentales pour implémenter Microsoft Entra Global Secure Access dans le cadre d’une stratégie de sécurité Confiance Zéro, ce qui permet à votre organisation de sécuriser l’accès aux ressources tout en conservant la visibilité et le contrôle du trafic réseau.

#### Lectures supplémentaires

- [Documentation sur l’accès sécurisé global](https://learn.microsoft.com/fr-fr/entra/global-secure-access/)
- [Centre de Conseil Zero Trust](https://learn.microsoft.com/fr-fr/security/zero-trust/)
- [Documentation sur l’accès conditionnel Microsoft Entra](https://learn.microsoft.com/fr-fr/entra/identity/conditional-access/)
