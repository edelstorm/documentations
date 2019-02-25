# CDN <small>- AWS</small>

## Compartiment S3

!!! info "S3"

    S3 est un service vous permettant d'héberger l'ensemble des médias de votre site internet, permettant ainsi à vos utilisateurs de les charger plus rapidement.

<p><a href="../assets/images/aws/cdn/fr/1.gif" target="_blank"><img alt="Amazon S3" src="../assets/images/aws/cdn/fr/1.gif"></a></p>

***

**Rendez-vous sur la console de management AWS.**

:    * Cherchez {==S3==} et cliquez sur ce service.
:    * Une fois sur l'interface S3, cliquez sur {==Créer un compartiment==}.
:    * Nommez votre compartiment et choisissez la même région que celle de votre instance Lightsail.
:    * Cliquez sur {==Suivant==}.
:    * Laissez les options par défaut et cliquez sur {==Suivant==}.
:    * Décochez toutes les cases pour rendre public votre compartiment.
:    * Cliquez sur {==Suivant==}.
:    * Validez vos options et cliquez sur {==Créer un compartiment==}.

!!! success "Un compartiment S3 public est maintenant disponible ! Il permettra de charger plus rapidement les différents médias de votre site Wordpress."

***

<p><a href="../assets/images/aws/cdn/fr/2.gif" target="_blank"><img alt="Creation du compartiment Amazon S3" src="../assets/images/aws/cdn/fr/2.gif"></a></p>

***

**Permissions du compartiment S3**

:    * Cliquez sur votre compartiment S3 et cliquez sur {==Autorisations==}.
:    * Cliquez sur {==Statégies de compartiment==}.
:    * Dans l'éditeur, copiez / collez cette stratégie : 
``` sh
{
 "Version": "2008-10-17",
 "Statement": [
 {
  "Sid": "AllowPublicRead",
  "Effect": "Allow",
  "Principal": {
   "AWS": "*"
  },
  "Action": "s3:GetObject",
  "Resource": "arn:aws:s3:::YourBucketName/*"
 }
 ]
}
```

:    * Remplacez *YourBucketName* par le nom que vous avez donné à votre compartiment.
:    * Une fois la stratégie éditée, cliquez sur {==Enregistrer==}.

## Stratégie IAM

***

<p><a href="../assets/images/aws/cdn/fr/3.gif" target="_blank"><img alt="Creation de la stratégie Amazon IAM" src="../assets/images/aws/cdn/fr/3.gif"></a></p>

***

**Création de la stratégie IAM**

:    * Revenez sur la console de management en cliquant sur le logo AWS en haut à gauche.
:    * Cherchez le service IAM et cliquez dessus pour y accéder.
:    * Dans le menu de gauche, cliquez sur {==Stratégies==}.
:    * Cliquez sur {==Créer une stratégie==}.
:    * Cliquez sur l'onglet {==JSON==} pour accéder à l'éditeur en ligne.
:    * Une fois dans l'éditeur, supprimez le contenu existant et copiez / collez la stratégie IAM ci-dessous :
``` sh
{
 "Version": "2012-10-17",
 "Statement": [
 {
  "Effect": "Allow",
  "Action": [
   "s3:CreateBucket",
   "s3:DeleteObject",
   "s3:Put*",
   "s3:Get*",
   "s3:List*"
  ],
  "Resource": [
   "arn:aws:s3:::YourBucketName",
   "arn:aws:s3:::YourBucketName/*"
  ]
 }
 ]
}
```

:    * Remplacez les deux *YourBucketName* par le nom que vous avez donné à votre compartiment.
:    * Cliquez sur {==Examiner une stratégie==}.

***

<p><a href="../assets/images/aws/cdn/fr/4.gif" target="_blank"><img alt="Creation de la stratégie Amazon IAM" src="../assets/images/aws/cdn/fr/4.gif"></a></p>

***

:    * Nommez la stratégie.
:    * Cliquez sur {==Créer une stratégie==}.

!!! success "La stratégie IAM est prête à être utilisée pour votre futur utilisateur IAM."

***

## Utilisateur IAM

<p><a href="../assets/images/aws/cdn/fr/5.gif" target="_blank"><img alt="Creation de l'utilisateur Amazon IAM" src="../assets/images/aws/cdn/fr/5.gif"></a></p>

***

**Couplage de la stratégie IAM à votre utilisateur IAM**

:    * Dans le menu de gauche, cliquez sur {==Utilisateur==}.
:    * Cliquez sur {==Ajouter un utilisateur==}.
:    * Choisissez un nom pour votre utilisateur IAM.
:    * Cochez la case *Accès par programmation*.
:    * Cliquez sur {==Suivant : Autorisations==}.
:    * Cliquez sur {==Attacher directement les stratégies existantes==}.
:    * Dans la barre de recherche, tapez le nom de votre stratégie IAM.
:    * Sélectionnez votre stratégie IAM en cochant la case et cliquez sur {==Suivant : Balises==}.
:    * Cliquez sur {==Suivant : Vérifications==}.
:    * Cliquez sur {==Créer un utilisateur==}.
:    * Cliquez sur {==Télécharger .csv==} pour conserver ces accès dans un fichier séparé.

!!! warning "Gardez cette fenêtre ouverte pour la prochaine étape et n'oubliez pas de stocker votre fichier .CSV contenant votre ID de clé d'accès et votre clé d'accès secrète dans un endroit sécurisé."

!!! success "Félicitation votre utilisateur IAM est lié à la bonne stratégie IAM et vous avez vos deux clés d'accès."

***

## Edition wp-config.php

<p><a href="../assets/images/aws/cdn/fr/6.gif" target="_blank"><img alt="Creation de l'utilisateur Amazon IAM" src="../assets/images/aws/cdn/fr/6.gif"></a></p>

***

**Rendez-vous sur votre page d'accueil Runcloud.io**

:    * Allez dans *Web Applications* et cliquez sur votre application Wordpress.
:    * Dans le menu de gauche, cliquez sur {==File Manager==}.
:    * Selectionnez le fichier *wp-config.php* et cliquez dans le menu en haut sur *View/Edit*.

***

<p><a href="../assets/images/aws/cdn/fr/7.gif" target="_blank"><img alt="Fichier wp-config.php Runcloud.io WP Offload Amazon S3" src="../assets/images/aws/cdn/fr/7.gif"></a></p>



<p><a href="../assets/images/aws/cdn/fr/15.gif" target="_blank"><img alt="Edition wp-config.php Runcloud.io WP Offload Amazon S3" src="../assets/images/aws/cdn/fr/15.gif"></a></p>

***

**Injection des clés d'accès IAM**

:    * Une fois dans l'éditeur, copiez / collez la commande ci-dessous à la suite de `define('WP_DEBUG', false);` : 
``` sh
define( 'AS3CF_SETTINGS', serialize( array(
    'provider' => 'aws',
    'access-key-id' => 'YourAccessKeyID',
    'secret-access-key' => 'YourAccessKeySecret',
) ) );
```

:    * Depuis votre interface IAM, remplacer *YourAccessKeyID* votre ID de clé d'accès et *YourAccessKeySecret* par votre clé secrète d'accès.

:    * Appuyez sur <kbd>Ctrl</kbd> + <kbd>S</kbd> pour sauvegarder les modifications.

!!! warning "N'oubliez pas de remplacer *YourAccessKeyID* et *YourAccessKeySecret* par les clés présentes dans la dernière étape IAM."

***

## Certificate Manager

<p><a href="../assets/images/aws/cdn/en/8.gif" target="_blank"><img alt="Amazon Certificate Manager" src="../assets/images/aws/cdn/en/8.gif"></a></p>

***

**Rendez-vous sur votre console de management AWS**

:    * Cherchez le service AWS *Certificate Manager* et cliquez dessus.
:    * Dans la section de gauche *Allouer les certificats*, cliquez sur {==Démarrage==}.
:    * Cochez la case *Demander un certificat public* et cliquez sur {==Demander un certificat==}.
:    * Fournissez votre nom de domaine de cette façon : `*.exemple.com` et cliquez sur {==Suivant==}.
:    * Cochez la case *Validation DNS* et cliquez sur {==Vérification==}.
:    * Validez les informations fournient et cliquez sur {==Confirmer et demander==}.

***

<p><a href="../assets/images/aws/cdn/en/9.gif" target="_blank"><img alt="Amazon Certificate Manager" src="../assets/images/aws/cdn/en/9.gif"></a></p>

***

**Validation DNS du non de domaine fournit**

:    * Patientez un instant, AWS va générer une configuration DNS CNAME pour vous permettre de vérifier votre nom de domaine.
:    * Copiez le début du nom CNAME comme dans l'exemple : `_55deac851379bd6906fd5f90ed2e95b3`
:    * Rendez-vous dans votre interface Amazon Lightsail, cliquez sur {==Mise en réseau==} puis sur votre zone DNS.
:    * Cliquez sur {==Ajoutez un enregistrement==}.
:    * Sélectionnez *CNAME* comme type d'engistrement, completez le sous-domaine et la valeur proposez par AWS pour la vérification puis sauvegardez l'ensemble.

***

<p><a href="../assets/images/aws/cdn/en/10.gif" target="_blank"><img alt="Amazon Certificate Manager" src="../assets/images/aws/cdn/en/10.gif"></a></p>

***

Revenez sur *AWS Certicate Manager*, cliquez sur {==Continuer==} et patientez cinq minutes pendant la validation votre nom de domaine.

***

<p><a href="../assets/images/aws/cdn/en/11.png" target="_blank"><img alt="Amazon Certificate Manager" src="../assets/images/aws/cdn/en/11.png"></a></p>

!!! success "Félicitaton vous avez généré un certicat AWS pour votre nom de domaine."

***

## Cloudfront

<p><a href="../assets/images/aws/cdn/en/12.gif" target="_blank"><img alt="Amazon Certificate Manager" src="../assets/images/aws/cdn/en/12.gif"></a></p>

***

**Rendez-vous sur votre console de management AWS**

:    * Cherchez le service AWS *Cloudfront* et cliquez dessus.
:    * Cliquez sur {==Créer une distribution==}.
:    * Dans la section *Web*, cliquez sur {==Mise en route==}.
:    * Pour le *nom de domaine d'origine*, sélectionnez votre compartiment S3.
:    * Dans *Autre nom de domaine (CNAME)*, inscrivez le sous-domaine `cdn1.exemple.com`. Remplacez *exemple.com* pour votre nom de domaine.
:    * Cochez la case *Certificat SSL personnalisé (exemple.com)*
:    * Sélectionnez le certificat ACM relatif à votre nom de domaine.
:    * Cliquez sur {==Créer une distribution==}.

***

<p><a href="../assets/images/aws/cdn/en/13.gif" target="_blank"><img alt="Amazon Certificate Manager" src="../assets/images/aws/cdn/en/13.gif"></a></p>

***

**Mapping CNAME Cloudfront et Amazon Lightsail**

:    * Sélectionnez la distribution Cloudfront que vous venez de créer en cochant la case puis cliquez sur {==Paramètre de distribution==}.
:    * Copier / collez le contenu de la section *Nom de domaine*.
:    * Revenez dans votre interface Lightsail, dans la section Mise en réseau et dans la zone DNS de votre nom de domaine.
:    * Ajoutez un enregistrement de type CNAME : tappez `cdn1.exemple.com`, liez le au nom de domaine de la distribution Cloudfront et sauvegardez l'ensemble.

***

## WP Offload Media

<p><a href="../assets/images/aws/cdn/fr/16.gif" target="_blank"><img alt="Installation du plugin WP Offload Amazon S3" src="../assets/images/aws/cdn/fr/16.gif"></a></p>

***

**Rendez-vous sur votre interface d'administration Wordpress**

:    * Dans le menu de gauche, cliquez sur {==Extensions > Ajouter==}.
:    * Dans la barre de recherche, tapez *Amazon S3*.
:    * Installez et activez l'extension *WP Offload Media Lite for Amazon S3*.

***

<p><a href="../assets/images/aws/cdn/fr/17.gif" target="_blank"><img alt="Installation du plugin WP Offload Amazon S3" src="../assets/images/aws/cdn/fr/17.gif"></a></p>

***

**Suppression des applications par défaut et configuration de l'extension WP Offload Media**

:    * Dans le menu *Extensions installées*, supprimez l'ensemble des applications présentes par défaut.
:    * Cliquez sur *Settings* de WP Offload Media Lite.
:    * Indiquez le nom de votre compartiment Amazon S3 et cliquez sur *Save Bucket Setting*.

***

<p><a href="../assets/images/aws/cdn/fr/18.gif" target="_blank"><img alt="Configuration du plugin WP Offload Amazon S3" src="../assets/images/aws/cdn/fr/18.gif"></a></p>

***

**Options de l'extension**

:    * Dans la section *URL REWRITING*, activez l'option *Custom Domain (CNAME)* et inscrivez `cdn1.exemple.com`. Remplacer `exemple.com` par votre nom de domaine.
:    * Activez l'option *Force HTTPS*.
:    * Cliquez sur *Sauvegarder*.

!!! success "Félicitations, vous avez correctement configuré Amazon Cloudfront CDN pour votre site Wordpress."

***

