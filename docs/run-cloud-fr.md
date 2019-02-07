# Run Cloud <small>- AWS</small>

## Création du compte

!!! info "Runcloud.io"

    Runcloud est un service vous proposant une offre gratuite vous permettant de déployer des applications PHP en toute sérénité. Le but de cette étape est de connecter votre instance Lightsail à l'interface Runcloud pour y installer et configurer Wordpress.

[![Material for MkDocs](assets/images/aws/run-cloud/en/1.gif)](assets/images/aws/run-cloud/en/1.gif)

***

**Rendez-vous sur le site web de <a href="https://runcloud.io/" target="_blank">RunCloud.io</a>**

!!! info "Fenêtre instance AWS"
    Gardez cependant une fenêtre AWS ouverte sur la page de votre instance. Vous aurez besoin de copier/coller l'adresse IP statique de celle-ci.

:    * Cliquez sur {==*Sign Up*==} en haut à droite.
:    * Remplissez le formulaire et cliquez sur {==*Create Free Account*==}.

***

[![Material for MkDocs](assets/images/aws/run-cloud/en/2.gif)](assets/images/aws/run-cloud/en/2.gif)

***

:    * Confirmez votre compte en cliquant sur le lien que vous venez de recevoir dans votre boîte mail.
:    * Connectez-vous à votre compte avec vos identifiants en cliquant sur {==*Sign in to Dashboard*==}.

***

## Installation

[![Material for MkDocs](assets/images/aws/run-cloud/en/3.gif)](assets/images/aws/run-cloud/en/3.gif)

***

**Installation de Runcloud sur votre instance Lightsail**

:    * Cliquez sur *Connect a New Server*.
:    * Nommez votre serveur avec le nom de votre site web.
:    * Copiez/collez l'IP statique de votre instance Lightsail.
:    * Inscrivez *AWS* comme Server Provider.
:    * Cliquez sur {==*Connect this server*==}.
:    * RunCloud va alors générer une commande d'installation pour votre serveur. Copiez là en cliquant sur l'icône vert à droite de la commande.
:    * Revenez sur Lightsail et connectez-vous en SSH à votre instance en cliquant sur *Connexion*.
:    * Une fois à l'intérieur du terminal de votre serveur, tapez la commande ci-dessous (vous ne pourrez pas la copier/coller) pour obtenir les droits administrateurs et appuyez sur <kbd>Entrer</kbd>.
``` sh
sudo su
```

:    * Cliquez sur l'icône orange en bas à droite de la fenêtre du terminal et collez *(attention pour savoir comment coller dans un terminal, regardez l'étape suivante)* l'ensemble de la commande provenant de Runcloud à l'intérieur. 
:    * Cliquez sur la partie noire du terminal, faites un clic droit pour coller la commande à l'intérieur et appuyez sur <kbd>Entrer</kbd>.

***

[![Material for MkDocs](assets/images/aws/run-cloud/en/5.gif)](assets/images/aws/run-cloud/en/5.gif)
[![Material for MkDocs](assets/images/aws/run-cloud/en/4.gif)](assets/images/aws/run-cloud/en/4.gif)

***

!!! warning "Configuration de Runcloud"

    La commande va alors installer Runcloud avec l'ensemble des configurations nécessaires à son fonctionnement. Surtout, ne quittez pas le terminal avant la fin du processus qui dure une dizaine de minutes. Une fois terminé, pensez impérativement à sauvegarder les mots de passe MySQL de votre base de données dans un endroit sécurisé sur votre ordinateur !<br>
    **Pour copier sur un terminal, il vous suffit de sélectionner ce que vous voulez copier, puis de cliquer sur l'icône orange en bas à droite. Vous y retrouverez ce que vous venez de sélectionner, vous pouvez alors, à partir de cet endroit, copier le contenu.**

!!! success "Vous avez maintenant accès à l'interface d'administration de votre instance Runcloud.io !"

***


