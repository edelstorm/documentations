# CDN <small>- AWS</small>

## S3 Bucket

!!! info "S3"

    S3 is a service that enables users to load your website’s media faster.

<p><a href="../assets/images/aws/cdn/en/1.gif" target="_blank"><img alt="Amazon S3" src="../assets/images/aws/cdn/en/1.gif"></a></p>

***

**Go to the AWS Management Console (AWS homepage).**

:    * Search for {==S3==} and click on the result.
:    * Now that you are in the S3 interface, click on {==Create bucket==}.
:    * Name your bucket and choose the same region that you choose for your Lightsail instance.
:    * Click on {==Next==}.
:    * Leave the option by default and click on {==Next==}.
:    * Uncheck all the boxes so your bucket becomes public.
:    * Click on {==Next==}.
:    * Check that everything is good and click on {==Create bucket==}.

!!! success "An S3 public bucket is now available! It will enable faster loading of your media on Wordpress."

***

<p><a href="../assets/images/aws/cdn/en/2.gif" target="_blank"><img alt="Create Bucket Amazon S3" src="../assets/images/aws/cdn/en/2.gif"></a></p>

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

***

<p><a href="../assets/images/aws/cdn/en/3.gif" target="_blank"><img alt="Amazon IAM Policy Creation" src="../assets/images/aws/cdn/en/3.gif"></a></p>

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

:    * Click on {==Review policy==}.

!!! warning "Don't forget to replace two times *YourBucketName* by the name you chose for your bucket."

***

<p><a href="../assets/images/aws/cdn/en/4.gif" target="_blank"><img alt="Creation de la stratégie Amazon IAM" src="../assets/images/aws/cdn/en/4.gif"></a></p>

***

:    * Name the policy.
:    * Click on {==Create policy==}.

!!! success "The IAM policy is now ready to be used for your future IAM user."

***

## IAM User

<p><a href="../assets/images/aws/cdn/en/5.gif" target="_blank"><img alt="Creation de l'utilisateur Amazon IAM" src="../assets/images/aws/cdn/en/5.gif"></a></p>

***

**IAM policy and IAM user linking**

:    * In the left menu, click on {==Users==}.
:    * Click on {==Add user==}.
:    * Choose a name for your IAM user.
:    * Check the *Programmatic access* box.
:    * Click on {==Next: Permissions==}.

***

<p><a href="../assets/images/aws/cdn/en/6.gif" target="_blank"><img alt="Creation de l'utilisateur Amazon IAM" src="../assets/images/aws/cdn/en/6.gif"></a></p>

***

:    * Click on {==Attach existing policies==}.
:    * Type your IAM policy name in the search bar.
:    * Check the box to select your IAM policy and click on {==Next: Tags==}.
:    * Click on {==Next: Review==}.
:    * Click on {==Create user==}.

!!! warning "Keep this window open for the next step and don't forget to copy/paste and save your Access key ID and Secret access key in a secure place."

!!! success "Congratulations! Your IAM user is now liked to the right IAM policy and you have the two access keys."

***

## Wp-config.php edit

<p><a href="../assets/images/aws/cdn/en/7.gif" target="_blank"><img alt="Fichier wp-config.php Runcloud.io WP Offload Amazon S3" src="../assets/images/aws/cdn/en/7.gif"></a></p>

***

**Go to your Runcloud.io homepage**

:    * To keep your access in a separate file, click on {==Download .csv==}.
:    * Go to *Web Applications* and click on your application Wordpress.
:    * Click on {==File Manager==} in the left menu.
:    * Select the *wp-config.php* file, then click on the {==View/Edit==} menu.

***

<p><a href="../assets/images/aws/cdn/en/15.gif" target="_blank"><img alt="Installation du plugin WP Offload Amazon S3" src="../assets/images/aws/cdn/en/15.gif"></a></p>

***

**Injection des clés d'accès IAM**

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

<p><a href="../assets/images/aws/cdn/en/16.gif" target="_blank"><img alt="Installation du plugin WP Offload Amazon S3" src="../assets/images/aws/cdn/en/16.gif"></a></p>

***

**Go to your Wordpress homepage**

:    * Click on {==Plugin > Add New==} on the left menu.
:    * Type *Amazon S3* on the search bar.
:    * Install and activate the *WP Offload Media Lite for Amazon S3* plugin.

***

<p><a href="../assets/images/aws/cdn/en/17.gif" target="_blank"><img alt="Configuration du plugin WP Offload Amazon S3" src="../assets/images/aws/cdn/en/17.gif"></a></p>

***

**Delete the default applications and configure your WP Offload Media plugin**

:    * In the *Installed Plugins* menu, delete the by default applications.
:    * In the plugins menu, click on *Settings*.
:    * Once there, put your S3 bucket name in the field and click on *Save Bucket Setting*.

***

<p><a href="../assets/images/aws/cdn/en/18.gif" target="_blank"><img alt="Configuration du plugin WP Offload Amazon S3" src="../assets/images/aws/cdn/en/18.gif"></a></p>

***

**Plugin settings**

:    * In the *URL REWRITING* tab, enable the *Custom Domain (CNAME)* option and put `cdn1.example.com`. Replace `example.com` by your domain name.
:    * Enable *Force HTTPS* option.
:    * Click on *Save changes*.

***

<p><a href="../assets/images/aws/cdn/en/19.png" target="_blank"><img alt="Configuration du plugin WP Offload Amazon S3" src="../assets/images/aws/cdn/en/19.png"></a></p>

!!! success "Congratulations, you have correctly set your CDN Amazon Cloudfront for your Wordpress website!"

***