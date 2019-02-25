# Content Delivery Network <small>- AWS</small>

## Compartiment S3

<iframe width="100%" height="405" src="https://www.youtube-nocookie.com/embed/VQztyuW6X24?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture setPlaybackQuality(hd1080);" allowfullscreen></iframe>

***

!!! info "S3"

    S3 est un service vous permettant d'héberger l'ensemble des médias de votre site internet, permettant ainsi à vos utilisateurs de les charger plus rapidement.

**Création d'un compartiment S3.**

:    * Allez sur votre console de management, cherchez le service *S3* dans la barre de recherche et cliquez dessus.
:    * Une fois sur l'interface S3, cliquez sur {==Créer un compartiment==}.
:    * Nommez votre compartiment et choisissez la même région que celle de votre instance Lightsail.
:    * Cliquez sur {==Suivant==}.
:    * Laissez les options par défaut et cliquez sur {==Suivant==}.
:    * Décochez toutes les cases pour rendre public votre compartiment.
:    * Cliquez sur {==Suivant==}.
:    * Validez les options et cliquez sur {==Créer un compartiment==}.

!!! success "Un compartiment de stockage S3 public est maintenant disponible. Il permettra de charger plus rapidement les différents médias de votre site Wordpress."

***

<iframe width="100%" height="405" src="https://www.youtube-nocookie.com/embed/R1d245Z0Z0k?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture setPlaybackQuality(hd1080);" allowfullscreen></iframe>

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

<iframe width="100%" height="405" src="https://www.youtube-nocookie.com/embed/0hcbrfL1JCU?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture setPlaybackQuality(hd1080);" allowfullscreen></iframe>

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
:    * Nommez la stratégie IAM.
:    * Cliquez sur {==Créer une stratégie==}.

!!! success "La stratégie IAM est prête à être utilisée pour votre futur utilisateur IAM."

***

## Utilisateur IAM

<iframe width="100%" height="405" src="https://www.youtube-nocookie.com/embed/eC6ZIXPpCeI?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture setPlaybackQuality(hd1080);" allowfullscreen></iframe>

***

**Couplage de la stratégie IAM à votre utilisateur IAM**

:    * Dans le menu de gauche, cliquez sur {==Utilisateur==}.
:    * Cliquez sur {==Ajouter un utilisateur==}.
:    * Choisissez un nom pour votre utilisateur IAM.
:    * Cochez la case *Accès par programmation*.
:    * Cliquez sur {==Suivant : Autorisations==}.
:    * Cliquez sur *Attacher directement les stratégies existantes*.
:    * Dans la barre de recherche, tapez le nom de votre stratégie IAM.
:    * Sélectionnez votre stratégie IAM en cochant la case et cliquez sur {==Suivant : Balises==}.
:    * Cliquez sur {==Suivant : Vérifications==}.
:    * Cliquez sur {==Créer un utilisateur==}.
:    * Cliquez sur {==Télécharger .csv==} pour conserver ces accès dans un fichier séparé.

!!! warning "Gardez cette fenêtre ouverte pour la prochaine étape et n'oubliez pas de stocker votre fichier .CSV contenant votre ID de clé d'accès et votre clé d'accès secrète dans un endroit sécurisé."

!!! success "Félicitation votre utilisateur IAM est lié à la bonne stratégie IAM et vous avez vos deux clés d'accès."

***

## Injection des clés IAM

<iframe width="100%" height="405" src="https://www.youtube-nocookie.com/embed/_mJp7YdtVEk?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture setPlaybackQuality(hd1080);" allowfullscreen></iframe>

***

**Injection des clés d'accès IAM dans Wordpress**

:    * Aller sur la page d'accueil Runcloud.io
:    * Dans le menu de gauche, allez dans *Web Applications* et cliquez sur votre application Wordpress.
:    * Dans le menu de gauche, cliquez sur {==File Manager==}.
:    * Sélectionnez le fichier *wp-config.php* et cliquez dans le menu en haut sur *View/Edit*.
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

***

## Certificate Manager

<iframe width="100%" height="405" src="https://www.youtube-nocookie.com/embed/PK7f-W6ZzCU?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture setPlaybackQuality(hd1080);" allowfullscreen></iframe>

***

**Création du certificat AWS**

:    * Revenez sur la console de management en cliquant sur le logo AWS en haut à gauche.
:    * En haut à droite, sélectionnez l'enplacement *US East (N. Virginia)*. (I)
:    * Cherchez le service AWS *Certificate Manager* et cliquez dessus.
:    * Dans la section de gauche *Allouer les certificats*, cliquez sur {==Démarrage==}.
:    * Cochez la case *Demander un certificat public* et cliquez sur {==Demander un certificat==}.
:    * Fournissez votre nom de domaine de cette façon : `*.exemple.com` et cliquez sur {==Suivant==}.
:    * Cochez la case *Validation DNS* et cliquez sur {==Vérification==}.
:    * Validez les informations fournient et cliquez sur {==Confirmer et demander==}.

***

<iframe width="100%" height="405" src="https://www.youtube-nocookie.com/embed/CM8FkHJJoOI?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture setPlaybackQuality(hd1080);" allowfullscreen></iframe>

***

**Validation DNS du nom de domaine fournit**

:    * Patientez un instant, AWS va générer une configuration DNS CNAME pour vous permettre de vérifier votre nom de domaine.
:    * Copiez le début du nom CNAME comme dans l'exemple : `_55deac851379bd6906fd5f90ed2e95b3`
:    * Rendez-vous dans votre interface Amazon Lightsail, cliquez sur {==Mise en réseau==} puis sur votre zone DNS.
:    * Cliquez sur {==Ajoutez un enregistrement==}.
:    * Sélectionnez *CNAME* comme type d'engistrement, completez le sous-domaine et la valeur proposez par AWS pour la vérification puis sauvegardez l'ensemble.
:    *  Revenez sur *AWS Certicate Manager*, cliquez sur {==Continuer==} et patientez un instant pendant la validation votre nom de domaine.

!!! success "Félicitations vous avez généré un certicat AWS pour votre nom de domaine."

***

## Cloudfront

<iframe width="100%" height="405" src="https://www.youtube-nocookie.com/embed/5atjyQXHVJw?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture setPlaybackQuality(hd1080);" allowfullscreen></iframe>

***

**Création du Content Delivery Network**

:    * Revenez sur la console de management en cliquant sur le logo AWS en haut à gauche.
:    * Cherchez le service AWS *Cloudfront* et cliquez dessus.
:    * Cliquez sur {==Créer une distribution==}.
:    * Dans la section *Web*, cliquez sur {==Mise en route==}.
:    * Pour le *nom de domaine d'origine*, sélectionnez votre compartiment S3.
:    * Dans *Autre nom de domaine (CNAME)*, tapez le sous-domaine `cdn1.exemple.com`. Remplacez *exemple.com* pour votre nom de domaine.
:    * Cochez la case *Certificat SSL Personnalisé (exemple.com)*
:    * Sélectionnez le certificat ACM relatif à votre nom de domaine.
:    * Cliquez sur {==Créer une distribution==}.

***

<iframe width="100%" height="405" src="https://www.youtube-nocookie.com/embed/j10DD5tqosw?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture setPlaybackQuality(hd1080);" allowfullscreen></iframe>

***

**Mapping CNAME Cloudfront et Amazon Lightsail**

:    * Cliquez sur l'ID de la distribution Cloudfront que vous venez de créer.
:    * Copiez le contenu de la section *Nom de domaine*.
:    * Revenez dans votre interface Lightsail, dans la section Mise en réseau puis dans la zone DNS de votre nom de domaine.
:    * Ajoutez un enregistrement, choisissez le type *CNAME*. Dans le champ *Sous domaine* tapez `cdn1`, puis collez le contenu que vous venez de copier dans le second champ de droit. Sauvegardez l'ensemble.

***

## WP Offload Media

<iframe width="100%" height="405" src="https://www.youtube-nocookie.com/embed/jbT2s1piWME?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture setPlaybackQuality(hd1080);" allowfullscreen></iframe>

***

**Installation du plugin WP Offload Media**

:    * Allez sur votre interface d'administration Wordpress.
:    * Dans le menu de gauche, cliquez sur {==Extensions > Ajouter==}.
:    * Dans la barre de recherche, tapez *Amazon S3*.
:    * Installez et activez l'extension *WP Offload Media Lite for Amazon S3*.
:    * Dans le menu *Extensions installées*, supprimez l'ensemble des applications présentes par défaut.
:    * Cliquez sur *Settings* de WP Offload Media Lite.
:    * Indiquez le nom de votre compartiment Amazon S3 et cliquez sur *Save Bucket Setting*.
:    * Dans la section *URL REWRITING*, activez l'option *Custom Domain (CNAME)* et inscrivez `cdn1.exemple.com`. Remplacer `exemple.com` par votre nom de domaine.
:    * Activez l'option *Force HTTPS*.
:    * Cliquez sur *Sauvegarder*.

!!! success "Félicitations, vous avez correctement configuré Amazon Cloudfront CDN pour votre site Wordpress."

***