# S3 <small>- AWS</small>

## Compartiment S3

!!! info "S3"

    S3 est un service vous permettant d'héberger l'ensemble des médias de votre site internet, permettant ainsi à vos utilisateurs de les charger plus rapidement.

<p><a href="../assets/images/aws/s3/fr/1.gif" target="_blank"><img alt="Amazon S3" src="../assets/images/aws/s3/fr/1.gif"></a></p>

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

<p><a href="../assets/images/aws/s3/fr/2.gif" target="_blank"><img alt="Creation du compartiment Amazon S3" src="../assets/images/aws/s3/fr/2.gif"></a></p>

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

!!! warning "N'oubliez pas de remplacer *YourBucketName* par le nom que vous avez donné à votre compartiment."
:    * Une fois la stratégie éditée, cliquez sur {==Enregistrer==}.

## Stratégie IAM

***

<p><a href="../assets/images/aws/s3/fr/3.gif" target="_blank"><img alt="Creation de la stratégie Amazon IAM" src="../assets/images/aws/s3/fr/3.gif"></a></p>

***

**Création de la stratégie IAM**

:    * Revenez sur la console de management en cliquant sur le logo AWS en haut à gauche.
:    * Cherchez le service IAM et cliquez dessus pour y accéder.
:    * Dans le menu de gauche, cliquez sur {==Stratégie==}.
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

:    * Cliquez sur {==Examiner une stratégie==}.

!!! warning "N'oubliez pas de remplacer les deux *YourBucketName* par le nom que vous avez donné à votre compartiment."

***

<p><a href="../assets/images/aws/s3/fr/4.gif" target="_blank"><img alt="Creation de la stratégie Amazon IAM" src="../assets/images/aws/s3/fr/4.gif"></a></p>

***

:    * Nommez la stratégie.
:    * Cliquez sur {==Créer une stratégie==}.

!!! success "La stratégie IAM est prête à être utilisée pour votre futur utilisateur IAM."

***

## Utilisateur IAM

<p><a href="../assets/images/aws/s3/fr/5.gif" target="_blank"><img alt="Creation de l'utilisateur Amazon IAM" src="../assets/images/aws/s3/fr/5.gif"></a></p>

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

<p><a href="../assets/images/aws/s3/fr/6.gif" target="_blank"><img alt="Fichier wp-config.php Runcloud.io WP Offload Amazon S3" src="../assets/images/aws/s3/fr/6.gif"></a></p>

***

**Rendez-vous sur votre page d'accueil Runcloud.io**

:    * Allez dans *Web Applications* et cliquez sur votre application Wordpress.
:    * Dans le menu de gauche, cliquez sur {==File Manager==}.
:    * Selectionnez le fichier *wp-config.php* et cliquez dans le menu en haut sur *View/Edit*.

***

<p><a href="../assets/images/aws/s3/fr/7.gif" target="_blank"><img alt="Edition wp-config.php Runcloud.io WP Offload Amazon S3" src="../assets/images/aws/s3/fr/7.gif"></a></p>

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

## WP Offload Media

<p><a href="../assets/images/aws/s3/fr/8.gif" target="_blank"><img alt="Installation du plugin WP Offload Amazon S3" src="../assets/images/aws/s3/fr/8.gif"></a></p>

***

**Rendez-vous sur votre interface d'administration Wordpress**

:    * Dans le menu de gauche, cliquez sur {==Extensions > Ajouter==}.
:    * Dans la barre de recherche, tapez *Amazon S3*.
:    * Installez et activez l'extension *WP Offload Media Lite for Amazon S3*.

***

<p><a href="../assets/images/aws/s3/fr/9.gif" target="_blank"><img alt="Installation du plugin WP Offload Amazon S3" src="../assets/images/aws/s3/fr/9.gif"></a></p>

***

**Suppression des applications par défaut et configuration de l'extension WP Offload Media**

:    * Dans le menu *Extensions installées*, supprimez l'ensemble des applications présentes par défaut.
:    * Cliquez sur *Settings* de WP Offload Media Lite.

***

<p><a href="../assets/images/aws/s3/fr/10.gif" target="_blank"><img alt="Configuration du plugin WP Offload Amazon S3" src="../assets/images/aws/s3/fr/10.gif"></a></p>

***

:    * Indiquez le nom de votre compartiment Amazon S3 et cliquez sur *Save Bucket Setting*.

***

<p><a href="../assets/images/aws/s3/fr/11.gif" target="_blank"><img alt="Configuration du plugin WP Offload Amazon S3" src="../assets/images/aws/s3/fr/11.gif"></a></p>

***

**Options de l'extension**

:    * Activez l'option *Force HTTPS*.
:    * Cliquez sur *Sauvegarder*.

!!! success "Félicitations, vous avez correctement configuré Amazon S3 pour votre site Wordpress."

***