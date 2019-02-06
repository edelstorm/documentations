# Run Cloud <small>- AWS</small>

## Création du compte

!!! info "Runcloud.io"

    Runcloud est un service vous proposant une offre gratuite pour déployer des applications PHP en toute sérénité. Le but de cette étape est de connecter votre instance Lightsail à l'interface Runcloud pour y installer et configurer Wordpress.

[![Material for MkDocs](assets/images/aws/run-cloud/en/1.gif)](assets/images/aws/run-cloud/en/1.gif)

***

**Rendez-vous sur le site web de <a href="https://runcloud.io/" target="_blank">RunCloud.io</a>**

:    * Cliquez sur {==*Sign Up*==} en haut à droite.
:    * Remplissez le formulaire et cliquez sur {==*Create Free Account*==}

***

[![Material for MkDocs](assets/images/aws/run-cloud/en/2.gif)](assets/images/aws/run-cloud/en/2.gif)

***

:    * Confirmez votre compte en cliquant sur le lien que vous venez de recevoir dans votre boîte mail.
:    * Connectez-vous à votre compte avec vos identifiants en cliquant sur {==*Sign in to Dashboard*==}

***

## Installation

[![Material for MkDocs](assets/images/aws/run-cloud/en/3.gif)](assets/images/aws/run-cloud/en/3.gif)

***

**Installation de Runcloud sur votre instance Lightsail**

:    * Cliquez sur *Connect a New Server*.
:    * Nommer votre serveur avec le nom de votre site web.
:    * Copier/coller l'IP statique votre instance Lightsail.
:    * Inscrivez *AWS* comme Server Provider.
:    * Cliquez sur {==*Connect this server*==}
:    * RunCloud va alors générer une commande d'installation pour votre serveur. Copiez là en cliquant sur l'icône vert à droite de la commande.
:    * Revenez sur Lightsail et connectez-vous en SSH à votre instance en cliquant sur *Connexion*
:    * Une fois à l'intérieur du terminal de votre serveur, tappez la commande ci-dessous pour obtenir les droits administrateurs et appuyez sur <kbd>Entrer</kbd>
``` sh
sudo su
```

:    * Cliquez sur l'icône en bas à droite de la fenètre du terminal et copier l'ensemble de la commande provenant de Runcloud à l'intérieur. 
:    * Cliquez sur la partie noire du terminal, faite un clic droit pour copier la commande à l'intérieur et appuyez sur <kbd>Entrer</kbd>

***

[![Material for MkDocs](assets/images/aws/run-cloud/en/5.gif)](assets/images/aws/run-cloud/en/5.gif)
[![Material for MkDocs](assets/images/aws/run-cloud/en/4.gif)](assets/images/aws/run-cloud/en/4.gif)

***

!!! warning "Configuration de Runcloud"

    La commande va alors installer Runcloud avec l'ensemble des configurations nécessaires à son fonctionnement. Surtout ne quittez pas le terminal avant la fin du processus qui dure une dizaine de minutes. Une fois terminé, pensez impérativement à sauvegarder les mots de passe MySQL de votre base de donnée dans un endroit sécurisé sur votre machine !

!!! success "Vous avez maintenant accès à l'interface d'administration de votre instance Runcloud.io !"

***


