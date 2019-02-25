# Content Delivery Network <small>- AWS</small>

## S3 Bucket

<iframe width="100%" height="405" src="https://www.youtube-nocookie.com/embed/ujgFncj9nf8?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture setPlaybackQuality(hd1080);" allowfullscreen></iframe>

***

!!! info "S3"

    S3 is a service that enables users to load your website’s media faster.

**S3 bucket creation**

:    * Go on your AWS management console, search for the service *S3* and click on it.
:    * Now that you are in the S3 interface, click on {==Create bucket==}.
:    * Name your bucket and choose the same region that you choose for your Lightsail instance.
:    * Click on {==Next==}.
:    * Leave the option by default and click on {==Next==}.
:    * Uncheck all the boxes so your bucket becomes public.
:    * Click on {==Next==}.
:    * Check that everything is good and click on {==Create bucket==}.

!!! success "A storage S3 public bucket is now available! It will enable faster loading of your media on Wordpress."

***

<iframe width="100%" height="405" src="https://www.youtube-nocookie.com/embed/R1d245Z0Z0k?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture setPlaybackQuality(hd1080);" allowfullscreen></iframe>

***

**S3 bucket permissions**

:    * Click on your S3 bucket, then click on {==Permissions==}.
:    * Click on {==Bucket Policy==}.
:    * Copy / paste the following policy on the editor : 
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

:    * Once the policy edited, click on {==Save==}.

!!! warning "Don't forget to switch *YourBucketName* with the name you gave your bucket."

***

## IAM Policy

<iframe width="100%" height="405" src="https://www.youtube-nocookie.com/embed/0hcbrfL1JCU?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture setPlaybackQuality(hd1080);" allowfullscreen></iframe>

***

**IAM policy initialization**

:    * Go back to the Management Console by clicking on the AWS top left logo.
:    * Search for the IAM service and click on the result.
:    * In the left menu, click on {==Policies==}.
:    * Click on {==Create policy==}.
:    * To access the online editor, click on the {==JSON==} menu.
:    * Once in the editor, delete the existing content and copy / paste the IAM policy below:
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

:    * Don't forget to replace two times *YourBucketName* by the name you chose for your bucket.
:    * Click on {==Review policy==}.
:    * Name the IAM policy.
:    * Click on {==Create policy==}.

!!! success "The IAM policy is now ready to be used for your future IAM user."

***

## IAM User

<iframe width="100%" height="405" src="https://www.youtube-nocookie.com/embed/eC6ZIXPpCeI?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture setPlaybackQuality(hd1080);" allowfullscreen></iframe>

***

**IAM policy and IAM user linking**

:    * In the left menu, click on {==Users==}.
:    * Click on {==Add user==}.
:    * Choose a name for your IAM user.
:    * Check the *Programmatic access* box.
:    * Click on {==Next: Permissions==}.
:    * Click on *Attach existing policies*.
:    * Type your IAM policy name in the search bar.
:    * Check the box to select your IAM policy and click on {==Next: Tags==}.
:    * Click on {==Next: Review==}.
:    * Click on {==Create user==}.
:    * To keep your access in a separate file, click on {==Download .csv==}.

!!! warning "Keep this window open for the next step and don't forget to copy/paste and save your Access key ID and Secret access key in a secure place."

!!! success "Congratulations! Your IAM user is now liked to the right IAM policy and you have the two access keys."

***

## IAM key injection

<iframe width="100%" height="405" src="https://www.youtube-nocookie.com/embed/_mJp7YdtVEk?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture setPlaybackQuality(hd1080);" allowfullscreen></iframe>

***

**IAM access key injection in Wordpress**

:    * Go to your Runcloud.io homepage
:    * On the left menu, click on *Web Applications* and click on your Wordpress application.
:    * Click on {==File Manager==} in the left menu.
:    * Select the *wp-config.php* file, then click on the {==View/Edit==} menu.
:    * Once in the editor, copy/paste the command below after `define('WP_DEBUG', false);` : 
``` sh
define( 'AS3CF_SETTINGS', serialize( array(
    'provider' => 'aws',
    'access-key-id' => 'YourAccessKeyID',
    'secret-access-key' => 'YourAccessKeySecret',
) ) );
```

:    * Then go to your IAM interface so you can replace *YourAccessKeyID* with your access key ID and *YourAccessKeySecret* with your secret access key.

:    * Type <kbd>Ctrl</kbd> + <kbd>S</kbd> to save your changes.

!!! warning "Replace *YourAccessKeyID* and *YourAccessKeySecret* with the keys from the last IAM step."

***

## Certificate Manager

<iframe width="100%" height="405" src="https://www.youtube-nocookie.com/embed/PK7f-W6ZzCU?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture setPlaybackQuality(hd1080);" allowfullscreen></iframe>

***

**AWS Certificate creation**

:    * Go back to the Management Console by clicking on the AWS top left logo.
:    * On the top right corner, select *US East (N. Virginia)* location. (I)
:    * Search for the AWS service *Certificate Manager* and click on it.
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
:    *  Revenez sur *AWS Certicate Manager*, cliquez sur {==Continuer==} et patientez un instance pendant la validation votre nom de domaine.

!!! success "Félicitaton vous avez généré un certicat AWS pour votre nom de domaine."

***

## Cloudfront

<iframe width="100%" height="405" src="https://www.youtube-nocookie.com/embed/5atjyQXHVJw?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture setPlaybackQuality(hd1080);" allowfullscreen></iframe>

***

**Creation du Content Delivery Network**

:    * Revenez sur la console de management en cliquant sur le logo AWS en haut à gauche.
:    * Cherchez le service AWS *Cloudfront* et cliquez dessus.
:    * Cliquez sur {==Créer une distribution==}.
:    * Dans la section *Web*, cliquez sur {==Mise en route==}.
:    * Pour le *nom de domaine d'origine*, sélectionnez votre compartiment S3.
:    * Dans *Autre nom de domaine (CNAME)*, inscrivez le sous-domaine `cdn1.example.com`. Remplacez *exemple.com* pour votre nom de domaine.
:    * Cochez la case *Certificat SSL Personnalisé (exemple.com)*
:    * Sélectionnez le certificat ACM relatif à votre nom de domaine.
:    * Cliquez sur {==Créer une distribution==}.

***

<iframe width="100%" height="405" src="https://www.youtube-nocookie.com/embed/j10DD5tqosw?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture setPlaybackQuality(hd1080);" allowfullscreen></iframe>

***

**Mapping CNAME Cloudfront et Amazon Lightsail**

:    * Sélectionnez la distribution Cloudfront que vous venez de créer en cochant la case puis cliquez sur {==Paramètre de distribution==}.
:    * Copier / collez le contenu de la section *Nom de domaine*.
:    * Revenez dans votre interface Lightsail, dans la section Mise en réseau puis dans la zone DNS de votre nom de domaine.
:    * Ajoutez un enregistrement de type CNAME : tappez `cdn1.exemple.com`, liez le au nom de domaine de la distribution Cloudfront et sauvegardez l'ensemble.

***

## WP Offload Media

<iframe width="100%" height="405" src="https://www.youtube-nocookie.com/embed/jbT2s1piWME?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture setPlaybackQuality(hd1080);" allowfullscreen></iframe>

***

**WP Offload Media plugin installation**

:    * Go to your Wordpress administration homepage.
:    * Click on {==Plugin > Add New==} on the left menu.
:    * Type *Amazon S3* on the search bar.
:    * Install and activate the *WP Offload Media Lite for Amazon S3* plugin.
:    * In the *Installed Plugins* menu, delete the by default applications.
:    * In the plugins menu, click on *Settings*.
:    * Once there, put your S3 bucket name in the field and click on *Save Bucket Setting*.
:    * In the *URL REWRITING* tab, enable the *Custom Domain (CNAME)* option and put `cdn1.example.com`. Replace `example.com` by your domain name.
:    * Enable *Force HTTPS* option.
:    * Click on *Save changes*.

!!! success "Congratulations, you have correctly set your CDN Amazon Cloudfront for your Wordpress website!"

***