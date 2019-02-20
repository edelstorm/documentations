# S3 <small>- AWS</small>

## Compartiment S3

!!! info "S3"

    S3 est un service vous permettant d'héberger l'ensemble des médias de votre site internet, permettant ainsi à vos utilisateurs de les charger plus rapidement.

[![Material for MkDocs](assets/images/aws/s3/fr/1.gif)](assets/images/aws/s3/fr/1.gif)

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

[![Material for MkDocs](assets/images/aws/s3/fr/2.gif)](assets/images/aws/s3/fr/2.gif)

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

[![Material for MkDocs](assets/images/aws/s3/fr/3a.gif)](assets/images/aws/s3/fr/3a.gif)

***

**Initialisation de la stratégie IAM**

:    * Revenez sur la console de management AWS en cliquant sur le logo en haut à gauche.
:    * Cherchez le service IAM et cliquez dessus pour y accéder.
:    * Dans le menu de gauche, cliquez sur {==Utilisateurs==}.
:    * Cliquez sur {==Ajouter un utilisateur==}.
:    * Choisissez un nom pour votre utilisateur IAM.
:    * Cochez la case *Accès par programmation*.
:    * Cliquez sur {==Suivant : Autorisations==}.
:    * Cliquez sur {==Attacher directement les stratégies existantes==}.
:    * Cliquez sur {==Créer une stratégie==}.

***

[![Material for MkDocs](assets/images/aws/s3/fr/3b.gif)](assets/images/aws/s3/fr/3b.gif)

***

**Création de la stratégie IAM**

:    * Cliquez sur le menu JSON pour accéder à l'éditeur en ligne.
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

!!! warning "N'oubliez pas de remplacer les deux *YourBucketName* par le nom que vous avez donné à votre compartiment."
:    * Cliquez sur {==Examiner une stratégie==}.
:    * Nommez la stratégie.
:    * Cliquez sur {==Créer une stratégie==}.

***

!!! success "La stratégie IAM est prête à être utilisée pour votre futur utilisateur IAM."

***

## Utilisateur IAM

[![Material for MkDocs](assets/images/aws/s3/fr/3c.gif)](assets/images/aws/s3/fr/3c.gif)

***

**Couplage de la stratégie IAM à votre utilisateur IAM**

:    * Dans le menu de gauche, cliquez sur {==Utilisateur==}.
:    * Cliquez sur {==Ajouter un utilisateur==}.
:    * Choisissez un nom pour votre utilisateur IAM.
:    * Cochez la case *Accès par programmation*.
:    * Cliquez sur {==Suivant : Autorisations==}.
:    * Cliquez sur {==Attacher directement les stratégies existantes==}.
:    * Dans la barre de recherche, tapez le nom de votre stratégie IAM choisi dans l'étape précédente.
:    * Cochez la case de votre stratégie IAM et cliquez sur {==Suivant : Balises==}.
:    * Cliquez sur {==Suivant : Vérifications==}.
:    * Cliquez sur {==Créer un utilisateur==}.
:    * Cliquez sur {==Télécharger .csv==} pour conserver ces accès dans un fichier séparé.
:    * Gardez cette fenêtre ouverte pour la prochaine étape.

!!! warning "N'oubliez pas de copier et d'enregistrer votre ID de clé d'accès et votre clé d'accès secrète dans un endroit sécurisé."

!!! success "Félicitation votre utilisateur IAM est lié à la bonne stratégie IAM et vous avez vos deux clés d'accès."

***

## Edition wp-config.php

[![Material for MkDocs](assets/images/aws/s3/fr/4.gif)](assets/images/aws/s3/fr/4.gif)

***

**Rendez-vous sur votre page d'accueil Runcloud.io**

:    * Allez dans *Web Applications* et cliquez sur votre application Wordpress.
:    * Dans le menu de gauche, cliquez sur {==File Manager==}.
:    * Selectionnez le fichier *wp-config.php* et cliquez dans le menu sur *View/Edit*.

***

[![Material for MkDocs](assets/images/aws/s3/fr/5.gif)](assets/images/aws/s3/fr/5.gif)

***

**Injection de la commande**

:    * Une fois dans l'éditeur, copiez / collez cette commande après `define('WP_DEBUG', false);` : 
``` sh
define( 'AS3CF_SETTINGS', serialize( array(
    'provider' => 'aws',
    'access-key-id' => 'YourAccessKeyID',
    'secret-access-key' => 'YourAccessKeySecret',
) ) );
```
:    * Depuis votre interface IAM, remplacer *YourAccessKeyID* votre ID de clé d'accès et *YourAccessKeySecret* par votre clé secrète d'accès.

:    * Appuyez sur <kbd>Ctrl</kbd> + <kbd>S</kbd> pour sauvegarder les modifications.

!!! warning "Remplacez *YourAccessKeyID* et *YourAccessKeySecret* par les clés présentes dans la dernière étape IAM."

***

## WP Offload Media

[![Material for MkDocs](assets/images/aws/s3/en/7.gif)](assets/images/aws/s3/en/7.gif)

***

**Revenez sur votre page d'accueil Wordpress**

:    * Dans le menu de gauche, cliquez sur {==Extensions > Ajouter==}.
:    * Dans la barre de recherche, tapez *Amazon S3*.
:    * Installez et activez l'extension *WP Offload Media Lite for Amazon S3*.

***

[![Material for MkDocs](assets/images/aws/s3/en/7a.gif)](assets/images/aws/s3/en/7a.gif)

***

**Suppression des applications superflues et configuration de l'extension WP Offload Media**

:    * Dans le menu *Extensions installées*, supprimez l'ensemble des applications présentes par défaut.
:    * Dans le menu de l'extension, cliquez sur *Options*.
:    * Une fois à l'intérieur, indiquez le nom de votre compartiment S3 et cliquez sur *Save Bucket Setting*.

***

[![Material for MkDocs](assets/images/aws/s3/en/8.gif)](assets/images/aws/s3/en/8.gif)

**Options de l'extension**

:    * Une fois dans les options de l'extension, activez *Force HTTPS*.
:    * Cliquez sur *Sauvegarder*.

!!! success "Félicitations, vous avez correctement configuré Amazon S3 pour votre site Wordpress."

***