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

!!! success "Vous avez un compte Runcloud.io"

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

***

[![Material for MkDocs](assets/images/aws/run-cloud/en/3b.gif)](assets/images/aws/run-cloud/en/3b.gif)

***

:    * RunCloud va alors générer une commande d'installation pour votre serveur. Copiez là en cliquant sur l'icône vert à droite de la commande.
:    * Revenez sur Lightsail et connectez-vous en SSH à votre instance en cliquant sur *Connexion*.
:    * Une fois à l'intérieur du terminal de votre serveur, tapez la commande ci-dessous (vous ne pourrez pas la copier/coller) pour obtenir les droits administrateurs et appuyez sur <kbd>Entrer</kbd>.
``` sh
sudo su
```

:    * Cliquez sur l'icône orange en bas à droite de la fenêtre du terminal et collez *(attention pour savoir comment coller dans un terminal, regardez l'étape suivante)* l'ensemble de la commande provenant de Runcloud à l'intérieur. 
:    * Cliquez sur la partie noire du terminal, faites un clic droit pour coller la commande à l'intérieur et appuyez sur <kbd>Entrer</kbd>.

***

[![Material for MkDocs](assets/images/aws/run-cloud/en/4.gif)](assets/images/aws/run-cloud/en/4.gif)
[![Material for MkDocs](assets/images/aws/run-cloud/en/5.gif)](assets/images/aws/run-cloud/en/5.gif)

***

!!! warning "Configuration de Runcloud"

    La commande va alors installer Runcloud avec l'ensemble des configurations nécessaires à son fonctionnement. Surtout, ne quittez pas le terminal avant la fin du processus qui dure une dizaine de minutes. Une fois terminé, pensez impérativement à sauvegarder les mots de passe MySQL de votre base de données dans un endroit sécurisé sur votre ordinateur !<br>
    **Pour copier sur un terminal, il vous suffit de sélectionner ce que vous voulez copier, puis de cliquer sur l'icône orange en bas à droite. Vous y retrouverez ce que vous venez de sélectionner, vous pouvez alors, à partir de cet endroit, copier le contenu.**

!!! success "Vous avez maintenant accès à l'interface d'administration de votre instance Runcloud.io !"

***

## Création de l'application

!!! info "Initialisation de l'application pour accueillir Wordpress sur votre instance"

    Dans cette étape, nous allons initialiser une application permettant d'installer Wordpress sur votre instance Ubuntu 16.04 d'Amazon Lightsail.

[![Material for MkDocs](assets/images/aws/run-cloud/en/6.gif)](assets/images/aws/run-cloud/en/6.gif)

***

**Revenez sur Runcloud.io, vous devriez avoir accès à votre interface d'administration**

:    * Dans le menu de gauche, cliquez sur {==*Web Application*==}.
:    * Cliquez sur {==*Create Application*==}.
:    * Nommez votre application avec le nom de votre futur site web.
:    * Ajoutez le nom de domaine que vous utilisez pour votre instance.
:    * Choississez l'utilisateur par défaut *Runcloud*.
:    * Laissez le chemin public (Public Path) par défaut.
:    * Sélectionnez la version de PHP la plus avancée.
:    * Sélectionnez *NGINX + Apache2 Hybrid (You will be able to use .htaccess)*.
:    * Choississez le mode *Production*.
:    * Laissez la case *Advanced Settings* décochée pour obtenir l'ensemble des configurations par défaut.
:    * Cliquez sur {==*Add Web Application*==}.

!!! success "Un espace "application" est désormais disponible sur votre instance Lightsail."

***

## Configurations

[![Material for MkDocs](assets/images/aws/run-cloud/en/7.gif)](assets/images/aws/run-cloud/en/7.gif)

***

**Installation de Wordpress**

:    * Dans le menu de gauche, cliquez sur {==*Script Installer*==}.
:    * Sélectionnez le script *Wordpress* à installer.
:    * Cliquez sur {==*Install*==}.

!!! success "Wordpress est installé comme application primaire sur votre instance Lightsail"

***

[![Material for MkDocs](assets/images/aws/run-cloud/en/8.gif)](assets/images/aws/run-cloud/en/8.gif)

***

**Configuration du nom de domaine**

:    * Dans le menu de gauche, cliquez sur {==*Domain Name*==}.
:    * Ajoutez votre nom de domaine `www.example.com` à la liste existante.
:    * Cliquez sur {==*Attach Domain Name*==}.

!!! success "La configuration du nom de domaine est fonctionnelle pour Wordpress."

***

[![Material for MkDocs](assets/images/aws/run-cloud/en/9.gif)](assets/images/aws/run-cloud/en/9.gif)

***

**Création du certificat de sécurité**

:    * Dans le menu de gauche, cliquez sur {==*SSL/TLS*==}.
:    * Cochez la cache *Enable HSTS*.
:    * Sélectionnez *Let's Encrypt* comme méthode SSL.
:    * Sélectionnez *Http-01* comme méthode d'autorisation.
:    * Sélectionnez *Live* comme environnement.
:    * Cliquez sur {==*Submit*==}.

!!! success "Votre certificat de sécurité est maintenant valide pour votre nom de domaine."

***

[![Material for MkDocs](assets/images/aws/run-cloud/en/9b.gif)](assets/images/aws/run-cloud/en/9b.gif)

***

**Application par défaut**

:    * En haut à droite, cliquez sur {==*More*==}.
:    * Cliquez sur *Set as default Web Application*.
:    * Revenez à l'accueil en cliquant sur *Back to Web Apps* dans le menu de gauche.

***

## Base de données

!!! info "Database et utilisateur"

    Pour fonctionner, votre application (Wordpress) a besoin d'une base de données dans laquelle l'ensemble du site web et des informations de vos utilisateurs seront stockés.

[![Material for MkDocs](assets/images/aws/run-cloud/en/10.gif)](assets/images/aws/run-cloud/en/10.gif)

***

**Création de la base de données**

:    * Dans le menu de gauche, cliquez sur {==*Database*==}.
:    * Cliquez sur *Create Database*.
:    * Nommez votre base de données comme vous le souhaitez.
:    * Laissez le champ *Collation* vide par défaut.
:    * Cliquez sur {==*Add Database*==}.

!!! success "La base de données est disponible pour Wordpress."

***

[![Material for MkDocs](assets/images/aws/run-cloud/en/10b.gif)](assets/images/aws/run-cloud/en/10b.gif)

***

**Création du compte administrateur**

!!! warning "Identifiants Wordpress"
    
    Pour accéder à l'interface d'administration de Wordpress, il vous faut un compte administrateur qui aura tous les droits sur le site web. Dans cette étape, nous créons les identifiants de ce compte que vous devez absolument stocker dans un endroit sécurisé.

:    * Cliquez sur *Create Database User*.
:    * Dans *Database User* créez votre identifiant et stockez-le.
:    * Générez votre mot de passe et copiez/collez-le dans un fichier sécurisé.
:    * Cliquez sur *Add Database User*.

!!! success "Votre compte administrateur est créé."

***

[![Material for MkDocs](assets/images/aws/run-cloud/en/10c.gif)](assets/images/aws/run-cloud/en/10c.gif)

***

**Liaison du compte administrateur à votre base de données**

:    * Cliquez sur le bouton vert *Attach User*.
:    * Sélectionnez votre nom d'utilisateur dans la liste déroulante.
:    * Cliquez sur *Attach User*.

!!! success "Votre compte administrateur est lié à votre base de données."

***

## Accès Wordpress

[![Material for MkDocs](assets/images/aws/run-cloud/en/11.gif)](assets/images/aws/run-cloud/en/11.gif)

***

**Initialisation de Wordpress**

!!! info "Accéder à votre site web" 
    Vous pouvez maintenant accéder à votre site ! Tappez votre nom de domaine `https://example.com` dans la barre d'addresse URL  de votre navigateur, vous verrez alors la page d'installation classique de Wordpress.

:    * Sélectionnez la langue de votre choix.
:    * Cliquez sur {==*C'est parti !*==}.
:    * Nommez votre base de donnée.
:    * Copiez/collez le nom d'utilisateur de la base de donnée Runcloud.io
:    * Copiez/collez le mot de passe de la base de donnée Runcloud.io
:    * Laissez par défaut *Database Host* à `Localhost`.
:    * Changez votre préfixe de table par quelquechose d'autre que `wp_`.
:    * Cliquez sur {==*Valider*==}.

***

[![Material for MkDocs](assets/images/aws/run-cloud/en/12.gif)](assets/images/aws/run-cloud/en/12.gif)

***

**Réglages du site et de l'utilisateur admininistrateur**

!!! info "Identifiants à retenir !" 
    Dans cette étape vous allez créer les accès administrateur à votre site Wordpress. Retenez absolument ces informations dans un endroits sécurisés! 

:    * Donnez un titre à votre site web.
:    * Définissez votre nom d'utilisateur et retenez-le.
:    * Générez un mot de passe et retenez-le.
:    * Mettez votre addresse e-mail pour être au courant des activités de votre site web.
:    * Laissez décochée la case *Search Engine Visibility*.
:    * Cliquez sur {==*Install Wordpress*==}.

!!! success "Vous avez maintenant accès à l'interface d'admnistration Wordpress de votre site web."

***

## Réglages Htaccess

[![Material for MkDocs](assets/images/aws/run-cloud/en/13.gif)](assets/images/aws/run-cloud/en/13.gif)

!!! info "Redirection du trafic" 
    Le fichier Htaccess vous permets de définir des règles de redirection du trafic sur votre site web. Dans cette étape, nous allons ajouter une redirection essentielle, l'ensemble des utilisateurs tentant d'accèder à l'IP static de votre instance Lightsail seront automatiquement redirigés vers votre nom de domaine sécurisé.

***

**Modification du fichier Htaccess**

:    * Dans le menu de gauche de votre interface Runcloud.io, cliquez sur {==*Web Application*==}.
:    * Enquite, cliquez sur le nom de votre application.
:    * Toujours dans le menu de gauche, cliquez sur {==*File Manager*==}.
:    * Selectionnez le fichier `.htaccess` et cliquez sur *View/Edit*.
:    * Une fois dans l'éditeur, copiez la règle de réécriture ci-dessous :
``` yaml
RewriteCond %{HTTP_HOST} ^111\.111\.111\.111
RewriteRule (.*) https://yoursite.com/$1 [R=301,L]
```

***

[![Material for MkDocs](assets/images/aws/run-cloud/en/13b.gif)](assets/images/aws/run-cloud/en/13b.gif)

***

**Edition de la commande de réécriture d'URL**

:    * Dans votre interface Lightsail, copiez/collez l'adresse IP Static de votre instance.
:    * Collez l'IP Static dans le fichier Htaccess pour l'avoir sous les yeux.
:    * Ensuite, éditez la commande avec votre IP Static et votre nom de domaine de cette façon :
``` yaml
RewriteCond %{HTTP_HOST} ^35\.180\.184\.49
RewriteRule (.*) https://yoursite.com/$1 [R=301,L]
```

:    * Une fois la commande injectée, effacez l'IP Static et réorganisez le bloc de commandes pour plus de lisibilité.
:    * Cliquez sur Sauvegarder en haut ou appuyer sur <kbd>Ctrl</kbd> + <kbd>S</kbd> pour enregistrer vos modifications.

!!! success "Félicitation ! Worpress est correctement installé et configuré pour supporter la création de votre site web."

***