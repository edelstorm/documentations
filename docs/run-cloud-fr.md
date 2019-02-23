# Run Cloud <small>- AWS</small>

## Création du compte

!!! info "Runcloud.io"

    Runcloud est un service vous permettant de déployer des applications PHP facilement et en toute sérénité. Le but de cette étape est de connecter votre instance Lightsail à l'interface Runcloud pour y installer et configurer Wordpress.

<p><a href="../assets/images/aws/run-cloud/en/1.gif" target="_blank"><img alt="Runcloud.io" src="../assets/images/aws/run-cloud/en/1.gif"></a></p>

***

**Rendez-vous sur le site web de <a href="https://runcloud.io/" target="_blank">RunCloud.io</a>**

!!! info "Fenêtre instance AWS"
    Gardez cependant une fenêtre AWS ouverte sur la page de votre instance. Vous aurez besoin de copier/coller l'adresse IP statique de celle-ci.

:    * Cliquez sur {==*Sign Up*==} en haut à droite.
:    * Remplissez le formulaire et cliquez sur {==*Create Free Account*==}.

***

<p><a href="../assets/images/aws/run-cloud/en/2.gif" target="_blank"><img alt="Runcloud.io" src="../assets/images/aws/run-cloud/en/2.gif"></a></p>

***

:    * Confirmez votre compte en cliquant sur le lien que vous venez de recevoir dans votre boîte mail.
:    * Connectez-vous à votre compte avec vos identifiants en cliquant sur {==*Sign in to Dashboard*==}.

!!! success "Vous avez un compte Runcloud.io"

***

<p><a href="../assets/images/aws/run-cloud/en/3a.gif" target="_blank"><img alt="Runcloud.io" src="../assets/images/aws/run-cloud/en/3a.gif"></a></p>

***

**Choisir votre offre**

:    * En haut à droite, cliquez sur le bouton vert *Upgrade Now*.
:    * Cliquez sur le bouton vert *Change plan*.
:    * Sélectionnez l'offre *Basic*. Nous vous conseillons de sélectionner le mode de paiement par année (Yearly). Cela vous reviendra à 6,66$ par mois au lieu de 8$. Mais c'est comme vous préférez. 
:    * Cliquez sur le bouton vert *Choose plan*.
:    * Cliquez sur le gros bouton bleu à gauche {==*Add a new payement method*==}.
:    * Vous pouvez maintenant choisir de payer par PayPal ou par carte.


***

## Installation

<p><a href="../assets/images/aws/run-cloud/en/3b.gif" target="_blank"><img alt="Pricing plan Runcloud.io" src="../assets/images/aws/run-cloud/en/3b.gif"></a></p>

***

**Installation de Runcloud sur votre instance Lightsail**

:    * Cliquez sur *Connect a New Server*.
:    * Nommez votre serveur avec le nom de votre site web.
:    * Copiez/collez l'IP statique de votre instance Lightsail.
:    * Inscrivez *AWS* comme Server Provider.
:    * Cliquez sur {==*Connect this server*==}.

***

<p><a href="../assets/images/aws/run-cloud/en/3b.gif" target="_blank"><img alt="Runcloud.io sur Amazon Lightsail" src="../assets/images/aws/run-cloud/en/3b.gif"></a></p>

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

<p><a href="../assets/images/aws/run-cloud/en/4.gif" target="_blank"><img alt="Installation de Runcloud.io" src="../assets/images/aws/run-cloud/en/4.gif"></a></p>
<p><a href="../assets/images/aws/run-cloud/en/5.gif" target="_blank"><img alt="Installation de Runcloud.io" src="../assets/images/aws/run-cloud/en/5.gif"></a></p>

***

!!! warning "Configuration de Runcloud"

    La commande va alors installer Runcloud avec l'ensemble des configurations nécessaires à son fonctionnement. Surtout, ne quittez pas le terminal avant la fin du processus qui dure une dizaine de minutes. Une fois terminé, pensez impérativement à sauvegarder les mots de passe MySQL de votre base de données dans un endroit sécurisé sur votre ordinateur !<br>
    **Pour copier sur un terminal, il vous suffit de sélectionner ce que vous voulez copier, puis de cliquer sur l'icône orange en bas à droite. Vous y retrouverez ce que vous venez de sélectionner, vous pouvez alors, à partir de cet endroit, copier le contenu.**

!!! success "Vous avez maintenant accès à l'interface d'administration de votre instance Runcloud.io !"

***

## Création de l'application

!!! info "Initialisation de l'application pour accueillir Wordpress sur votre instance"

    Dans cette étape, nous allons initialiser une application permettant d'installer Wordpress sur votre instance Ubuntu 16.04 d'Amazon Lightsail.

<p><a href="../assets/images/aws/run-cloud/en/6.gif" target="_blank"><img alt="Creation de l'application Runcloud.io" src="../assets/images/aws/run-cloud/en/6.gif"></a></p>

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

<p><a href="../assets/images/aws/run-cloud/en/7.gif" target="_blank"><img alt="Configurations Wordpress" src="../assets/images/aws/run-cloud/en/7.gif"></a></p>

***

**Installation de Wordpress**

:    * Dans le menu de gauche, cliquez sur {==*Script Installer*==}.
:    * Sélectionnez le script *Wordpress* à installer.
:    * Cliquez sur {==*Install*==}.

!!! success "Wordpress est installé comme application primaire sur votre instance Lightsail"

***

<p><a href="../assets/images/aws/run-cloud/en/8.gif" target="_blank"><img alt="Installation de Wordpress" src="../assets/images/aws/run-cloud/en/8.gif"></a></p>

***

**Configuration du nom de domaine**

:    * Dans le menu de gauche, cliquez sur {==*Domain Name*==}.
:    * Ajoutez votre nom de domaine `www.example.com` à la liste existante.
:    * Cliquez sur {==*Attach Domain Name*==}.

!!! success "La configuration du nom de domaine est fonctionnelle pour Wordpress."

***

<p><a href="../assets/images/aws/run-cloud/en/9a.gif" target="_blank"><img alt="Certicat SSL Let's Encrypt Lightsail Wordpress" src="../assets/images/aws/run-cloud/en/9a.gif"></a></p>

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

<p><a href="../assets/images/aws/run-cloud/en/9b.gif" target="_blank"><img alt="Certicat SSL Let's Encrypt Lightsail Wordpress" src="../assets/images/aws/run-cloud/en/9b.gif"></a></p>

***

**Application par défaut**

:    * En haut à droite, cliquez sur {==*More*==}.
:    * Cliquez sur *Set as default Web Application*.
:    * Revenez à l'accueil en cliquant sur *Back to Web Apps* dans le menu de gauche.

***

## Base de donnée

!!! info "Database et utilisateur"

    Pour fonctionner, votre application (Wordpress) a besoin d'une base de données dans laquelle l'ensemble du site web et des informations de vos utilisateurs seront stockés.

<p><a href="../assets/images/aws/run-cloud/en/10a.gif" target="_blank"><img alt="Base de donnée Wordpress" src="../assets/images/aws/run-cloud/en/10a.gif"></a></p>

***

**Création de la base de données**

:    * Dans le menu de gauche, cliquez sur {==*Database*==}.
:    * Cliquez sur *Create Database*.
:    * Nommez votre base de données comme vous le souhaitez.
:    * Laissez le champ *Collation* vide par défaut.
:    * Cliquez sur {==*Add Database*==}.

!!! success "La base de données est disponible pour Wordpress."

***

<p><a href="../assets/images/aws/run-cloud/en/10b.gif" target="_blank"><img alt="Base de donnée Wordpress" src="../assets/images/aws/run-cloud/en/10b.gif"></a></p>

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

<p><a href="../assets/images/aws/run-cloud/en/10c.gif" target="_blank"><img alt="Compte Administrateur Wordpress" src="../assets/images/aws/run-cloud/en/10c.gif"></a></p>

***

**Liaison du compte administrateur à votre base de données**

:    * Cliquez sur le bouton vert *Attach User*.
:    * Sélectionnez votre nom d'utilisateur dans la liste déroulante.
:    * Cliquez sur *Attach User*.

!!! success "Votre compte administrateur est lié à votre base de données."

***

## Accès Wordpress

<p><a href="../assets/images/aws/run-cloud/en/11.gif" target="_blank"><img alt="Accès Wordpress" src="../assets/images/aws/run-cloud/en/11.gif"></a></p>

***

**Initialisation de Wordpress**

!!! info "Accéder à votre site web" 
    Vous pouvez maintenant accéder à votre site ! Tapez votre nom de domaine `https://example.com` dans la barre d'adresse URL  de votre navigateur, vous verrez alors la page d'installation classique de Wordpress.

:    * Sélectionnez la langue de votre choix.
:    * Cliquez sur le bouton {==*C'est parti !*==}.
:    * Nommez votre base de données.
:    * Copiez/collez le nom d'utilisateur de la base de données Runcloud.io (voir étape Création du compte administrateur ANCRE).
:    * Copiez/collez le mot de passe de la base de données Runcloud.io (voir étape Création du compte administrateur).
:    * Laissez par défaut *Database Host* à `Localhost`.
:    * Changez votre préfixe de table par quelque chose d'autre que `wp_`, tout en gardant ce format.
:    * Cliquez sur {==*Valider*==}.

***

<p><a href="../assets/images/aws/run-cloud/en/12.gif" target="_blank"><img alt="Utilisateur Administrateur Wordpress" src="../assets/images/aws/run-cloud/en/12.gif"></a></p>

***

**Réglages du site et de l'utilisateur administrateur**

!!! info "Identifiants à retenir !" 
    Pour cette étape, vous allez créer les accès administrateur à votre site Wordpress. Conservez absolument ces informations dans un endroit sécurisé ! 

:    * Donnez un titre à votre site web.
:    * Définissez votre nom d'utilisateur et conservez-le.
:    * Générez un mot de passe et conservez-le.
:    * Ajoutez votre adresse e-mail.
:    * Laissez la case *Search Engine Visibility* décochée.
:    * Cliquez sur {==*Install Wordpress*==}.
:    * Vous pouvez désormais vous {==*connecter*==} à votre interface Wordpress.

!!! success "Vous avez maintenant accès à l'interface d'administration Wordpress de votre site web."

***

## Réglages Htaccess

<p><a href="../assets/images/aws/run-cloud/en/13a.gif" target="_blank"><img alt="Réglages Htaccess" src="../assets/images/aws/run-cloud/en/13a.gif"></a></p>

!!! info "Redirection du trafic" 
    Le fichier Htaccess vous permet de définir des règles de redirection du trafic sur votre site web. Après ette étape, l'ensemble des utilisateurs essayant d'accéder à l'IP static de votre instance Lightsail seront automatiquement redirigés vers votre nom de domaine sécurisé.

***

**Modification du fichier Htaccess**

:    * Dans le menu de gauche de votre interface Runcloud.io, cliquez sur {==*Web Application*==}.
:    * Ensuite, cliquez sur le nom de votre application.
:    * Toujours dans le menu de gauche, cliquez sur {==*File Manager*==}.
:    * Selectionnez le fichier `.htaccess` et cliquez sur *View/Edit*.
:    * Une fois dans l'éditeur, copiez la règle de réécriture ci-dessous :
``` yaml
RewriteCond %{HTTP_HOST} ^111\.111\.111\.111$ [NC]
RewriteRule ^(.*)$ https://edelstorm.com/$1 [R=301,L]
```

***

<p><a href="../assets/images/aws/run-cloud/en/13b.gif" target="_blank"><img alt="IP to Domain" src="../assets/images/aws/run-cloud/en/13b.gif"></a></p>

***

**Édition de la commande de réécriture d'URL**

:    * Dans votre interface Lightsail, copiez l'adresse IP Static de votre instance.
:    * Collez l'IP Static dans le fichier Htaccess pour l'avoir sous les yeux.
:    * Ensuite, éditez la commande que vous avez précédemment copiée/collée, avec votre IP Static et nom de domaine. Vous pouvez vous appuyer sur cet exemple :
``` yaml
RewriteCond %{HTTP_HOST} ^35\.180\.184\.49$ [NC]
RewriteRule ^(.*)$ https://yoursite.com/$1 [R=301,L]
```

:    * Une fois cette étape terminée, effacez l'IP Static et réorganisez le bloc de commandes pour plus de lisibilité.
:    * Cliquez sur Sauvegarder en haut ou appuyer sur les touches <kbd>Ctrl</kbd> + <kbd>S</kbd> pour enregistrer vos modifications.

!!! success "Félicitation ! Wordpress est correctement installé et configuré pour supporter la création de votre site web."

***

## Cron Job Let's Encrypt

<p><a href="../assets/images/aws/run-cloud/en/14.gif" target="_blank"><img alt="Cronjob Let's Encrypt" src="../assets/images/aws/run-cloud/en/14.gif"></a></p>

***

**Renouvellement automatique de votre certificat de sécurité Let's Encrypt**

:    * Dans le menu de gauche, cliquez sur {==*Cron Job*==}.
:    * Cliquez sur {==*Create a Cron Job*==}.
:    * Nommez votre Cron Job: *Let's Encrypt*.
:    * Copiez / collez la commande ci-dessous dans le champ prévu à cet effet :
``` yaml
cd /etc/letsencrypt/ && ./certbot-auto renew && /etc/init.d/apache2 restart
```

:    * Définissez une périodicité de renouvellement en sélectionnant *Every 10 days at midnight*.
:    * Cliquez sur {==*Add a Cron Job*==}.

!!! success "Félicitation ! Votre certificat de sécurité Let's Encrypt sera renouvelé automatiquement tous les dix jours."

***

## Accès SSH

<p><a href="../assets/images/aws/run-cloud/en/15.gif" target="_blank"><img alt="Accès SSH" src="../assets/images/aws/run-cloud/en/15.gif"></a></p>

***

**Configuration de votre clé SSH publique pour Runcloud.io**

:    * Dans le menu de gauche, cliquez sur {==*SSH Key*==}.
:    * Cliquez sur {==*Add SSH Key*==}.
:    * Ajoutez un nom à votre clé SSH publique.
:    * Allez dans votre dossier `.ssh`.
:    * Ouvrez avec un éditeur de texte votre clé publique `id_rsa.pub`.
:    * Copiez / collez la clé publique dans Runcloud.io
:    * Cliquez sur {==*Add*==}.

!!! success "Votre clé SSH publique est disponible, vous pourrez vous connecter à distance sur votre serveur dans Runcloud.io."

***