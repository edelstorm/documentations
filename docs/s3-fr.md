# S3 <small>- AWS</small>

## Création du compte

!!! info "S3"

    S3 est un service vous permettant d'héberger l'ensemble médias de votre site internet pour les délivrer plus rapidement à vos utilisateurs.

[![Material for MkDocs](assets/images/aws/s3/1.gif)](assets/images/aws/s3/1.gif)

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

[![Material for MkDocs](assets/images/aws/s3/2.gif)](assets/images/aws/s3/2.gif)

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

!!! warning "N'oubliez pas de remplacer *YourBucketName* par le nom que vous avez donné à votre compartiment."

:    * Une fois la stratégie éditée, cliquez sur {==Sauvegarder==}.

***