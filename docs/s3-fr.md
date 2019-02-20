# S3 <small>- AWS</small>

## Compartiment S3

!!! info "S3"

    S3 est un service vous permettant d'héberger l'ensemble médias de votre site internet pour les délivrer plus rapidement à vos utilisateurs.

[![Material for MkDocs](assets/images/aws/s3/fr/1.gif)](assets/images/aws/s3/fr/1.gif)

***

**Rendez-vous sur la console de management AWS.**

:    * Cherchez {==S3==} et cliquez sur ce service.
:    * Une fois sur l'interface S3, cliquez sur {==Créer un compartiment==}.
:    * Nommez votre compartiment et choississez la même région que celle de votre instance Lightsail.
:    * Cliquez sur {==Suivant==}.
:    * Laissez les options par défaut et cliquez sur {==Suivant==}.
:    * Décochez toutes les cases pour rendre public votre compartiment.
:    * Cliquez sur {==Suivant==}.
:    * Validez vos options et cliquez sur {==Créer un compartiment==}.

!!! success "Un compartiment S3 public est maintenant disponible pour servir plus rapidement vos médias Wordpress à vos utilisateurs."

***

[![Material for MkDocs](assets/images/aws/s3/fr/2.gif)](assets/images/aws/s3/fr/2.gif)

***

**Permissions du compartiment S3**

:    * Cliquez sur votre compartiment S3 et cliquez sur {==Permissions==}.
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

:    * Une fois la stratégie éditée, cliquez sur {==Enregistrer==}.

!!! warning "N'oubliez pas de remplacer *YourBucketName* par le nom que vous avez donné à votre compartiment."

## Stratégie IAM

***

[![Material for MkDocs](assets/images/aws/s3/fr/3a.gif)](assets/images/aws/s3/fr/3a.gif)

***

**Initialisation de la stratégie IAM**

:    * Revenez sur la console de management AWS en cliquant sur le logo en haut à gauche.
:    * Cherchez le service IAM et cliquez dessus pour y accéder.
:    * Dans le menu de gauche, cliquez sur {==Utilisateurs==}.
:    * Cliquez sur {==Ajouter un utilisateur==}.
:    * Nommez votre utilisateur IAM.
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
***

:    * Cliquez sur {==Examiner une stratégie==}.
:    * Nommez la stratégie.
:    * Cliquez sur {==Créer une stratégie==}.

***

!!! warning "N'oubliez pas de remplacer *YourBucketName* par le nom que vous avez donné à votre compartiment."

!!! success "La stratégie IAM est prête à être utilisée pour votre futur utilisateur IAM."

***

## Utilisateur IAM

[![Material for MkDocs](assets/images/aws/s3/fr/3c.gif)](assets/images/aws/s3/fr/3c.gif)

***

**Couplage de la statégie IAM à votre utilisateur IAM**

:    * Dans le menu de gauche, cliquez sur {==Utilisateur==}.
:    * Cliquez sur {==Ajouter un utilisateur==}.
:    * Nommez votre utilisateur IAM.
:    * Cochez la case *Accès par programmation*.
:    * Cliquez sur {==Suivant : Autorisations==}.
:    * Cliquez sur {==Attacher directement les stratégies existantes==}.
:    * Mais cette fois ci, cherchez le nom de votre stratégie IAM dans la barre de recherche.
:    * Cochez la case de votre stratégie IAM et cliquez sur {==Suivant : Balises==}.
:    * Cliquez sur {==Suivant : Vérifications==}.
:    * Cliquez sur {==Créer un utilisateur==}.
:    * Cliquez sur {==Télécharger .csv==} pour conserver ces accès dans un fichier séparé.

!!! warning "N'oubliez pas d'enregistrer votre ID de clé d'accès et votre clé d'accès secrète dans un endroit sécurisé.."

!!! success "Félicitation votre utilisateur IAM est lié à la bonne stratégie IAM et vous avez vos deux clés d'accès."

***