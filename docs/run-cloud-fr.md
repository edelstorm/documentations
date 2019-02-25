# Run Cloud <small>- AWS</small>

## Création du compte

!!! info "Runcloud.io"

    Runcloud est un service vous permettant de déployer des applications PHP facilement et en toute sérénité. Le but de cette étape est de connecter votre instance Lightsail à l'interface Runcloud.io pour y installer et configurer Wordpress.

<p><a href="../assets/images/aws/run-cloud/en/1.gif" target="_blank"><img alt="Runcloud.io" src="../assets/images/aws/run-cloud/en/1.gif"></a></p>

***

**Rendez-vous sur le site web de <a href="https://runcloud.io/" target="_blank">RunCloud.io</a>**

:    * Cliquez sur {==Sign Up==} en haut à droite.
:    * Remplissez le formulaire et cliquez sur {==Create Free Account==}.

***

<p><a href="../assets/images/aws/run-cloud/en/2.gif" target="_blank"><img alt="Runcloud.io" src="../assets/images/aws/run-cloud/en/2.gif"></a></p>

***

:    * Confirmez votre compte en cliquant sur {==Verify Registration==} dans l'e-mail que vous avez reçu.
:    * Connectez-vous à votre compte avec vos identifiants en cliquant sur {==Sign in to Dashboard==}.

!!! success "Vous avez un compte Runcloud.io"

***

<!--

<p><a href="../assets/images/aws/run-cloud/en/3a.gif" target="_blank"><img alt="Runcloud.io" src="../assets/images/aws/run-cloud/en/3a.gif"></a></p>

***

**Choisir votre offre**

:    * En haut à droite, cliquez sur le bouton vert *Upgrade Now*.
:    * Cliquez sur le bouton vert *Change plan*.
:    * Sélectionnez l'offre *Basic*. Nous vous conseillons de sélectionner le mode de paiement par année (Yearly). Cela vous reviendra à 6,66$ par mois au lieu de 8$. Mais c'est comme vous préférez. 
:    * Cliquez sur le bouton vert *Choose plan*.
:    * Cliquez sur le gros bouton bleu à gauche {==Add a new payement method==}.
:    * Vous pouvez maintenant choisir de payer par PayPal ou par carte.

***

-->

## Installation

<iframe width="100%" height="405" src="https://www.youtube-nocookie.com/embed/cAwNQjCvDm4?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture setPlaybackQuality(hd1080);" allowfullscreen></iframe>

***

**Installation de Runcloud sur votre instance Lightsail**

:    * Cliquez sur *Connect a New Server*.
:    * Nommez votre serveur avec le nom de votre site web.
:    * Copiez/collez l'IP statique de votre instance Lightsail dans le champ du formulaire.
:    * Inscrivez *AWS* comme Server Provider.
:    * Cliquez sur {==Connect this server==}.
:    * RunCloud.io va générer une commande d'installation pour votre serveur. Copiez-là en cliquant sur l'icône vert à droite de la commande.
:    * Revenez sur Lightsail et connectez-vous en SSH à votre instance en cliquant sur *Connexion*.
:    * Une fois à l'intérieur du terminal de votre serveur, tapez directement la commande ci-dessous pour obtenir les droits administrateurs et appuyez sur <kbd>Entrer</kbd>.
``` sh
sudo su
```

:    * Cliquez sur l'icône orange en bas à droite de la fenêtre du terminal et collez la commande à l'intérieur.
:    * Cliquez ensuite sur la partie noire du terminal, faites un clic droit pour coller la commande à l'intérieur et appuyez sur <kbd>Entrer</kbd>.

!!! warning "Installation"

    La commande va alors installer Runcloud avec l'ensemble des configurations nécessaires à son fonctionnement. Surtout, NE QUITTEZ PAS le terminal avant la fin du processus qui dure une dizaine de minutes. 

***
    
<iframe width="100%" height="405" src="https://www.youtube-nocookie.com/embed/0efKMExFMfY?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture setPlaybackQuality(hd1080);" allowfullscreen></iframe>

***

**Sauvegarde de vos accès MySQL**

:    *  Une fois l'installation terminée, pensez impérativement à sauvegarder les mots de passe MySQL de votre base de données dans un endroit sécurisé sur votre ordinateur ! Pour copier/coller sur le terminal, il vous suffit de sélectionner ce que vous voulez copier, puis de cliquer sur l'icône orange en bas à droite. Vous y retrouverez ce que vous venez de sélectionner, vous pouvez alors, à partir de cet endroit, copier le contenu.

:    *  Ouvrez un fichier texte pour y stocker vos accès MySQL, sauvegardez-le ensuite dans un endroit sécurisé.

!!! success "Vous avez maintenant accès à l'interface d'administration de votre instance Runcloud.io."

***

## Création de l'application

<iframe width="100%" height="405" src="https://www.youtube-nocookie.com/embed/2jrRYXP-3k4?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture setPlaybackQuality(hd1080);" allowfullscreen></iframe>

***

**Revenez sur Runcloud.io, vous devriez avoir accès à votre interface d'administration**

:    * Dans le menu de gauche, cliquez sur {==Web Application==}.
:    * Cliquez sur {==Create Application==}.
:    * Nommez votre application avec le nom de votre futur site web.
:    * Ajoutez le nom de domaine que vous utilisez pour votre instance de cette façon : `*.VotreNomDeDomaine.com`
:    * Choisissez l'utilisateur par défaut *Runcloud*.
:    * Laissez le chemin public (Public Path) par défaut.
:    * Sélectionnez la version de PHP la plus avancée à disposition.
:    * Sélectionnez *NGINX + Apache2 Hybrid (You will be able to use .htaccess)*.
:    * Choisissez le mode *Production*.
:    * Laissez la case *Advanced Settings* décochée pour obtenir l'ensemble des configurations par défaut.
:    * Cliquez sur {==Add Web Application==}.

!!! success "Un espace permettant d'accueillir une application est désormais disponible sur votre instance Lightsail."

***

## Configurations

<iframe width="100%" height="405" src="https://www.youtube-nocookie.com/embed/E8IpVG2c9-Q?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture setPlaybackQuality(hd1080);" allowfullscreen></iframe>

***

**Installation de Wordpress**

:    * Dans le menu de gauche, cliquez sur {==Script Installer==}.
:    * Sélectionnez le script *Wordpress*.
:    * Cliquez sur {==Install==}.

***

**Configuration du nom de domaine**

:    * Dans le menu de gauche, cliquez sur {==Domain Name==}.
:    * Ajoutez votre nom de domaine sous ces deux formes : `www.exemple.com` et `exemple.com`, à la liste existante.
:    * Cliquez sur {==Attach Domain Name==}.

***

**Création du certificat de sécurité SSL**

:    * Dans le menu de gauche, cliquez sur {==SSL/TLS==}.
:    * Cochez la cache *Enable HSTS*.
:    * Sélectionnez *Let's Encrypt* comme méthode SSL.
:    * Sélectionnez *Http-01* comme méthode d'autorisation.
:    * Sélectionnez *Live* comme environnement.
:    * Cliquez sur {==Submit==}.

!!! success "Wordpress est installé sur votre instance Lightsail, la configuration du nom de domaine est correcte et votre certificat de sécurité SSL est activé."

***

## Base de données

<iframe width="100%" height="405" src="https://www.youtube-nocookie.com/embed/Wb7_7h03Zgc?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture setPlaybackQuality(hd1080);" allowfullscreen></iframe>

***

**Création de la base de données**

:    * Revenez à l'accueil en cliquant sur *Back to web apps*.
:    * Dans le menu de gauche, cliquez sur {==Database==}.
:    * Cliquez sur *Create Database*.
:    * Nommez votre base de données comme vous le souhaitez.
:    * Laissez le champ *Collation* vide par défaut.
:    * Cliquez sur {==Add Database==}.

!!! info "Information"

    Pour fonctionner, votre application (Wordpress) a besoin d'une base de données dans laquelle l'ensemble du site web et des informations de vos utilisateurs seront stockés.

***

**Création de l'administrateur de la base de données**

:    * Cliquez sur *Create Database User*.
:    * Dans *Database User* créez votre identifiant, stockez cette information dans un fichier séparé et sauvegardez-le dans un endroit sécurisé !
:    * Générez votre mot de passe, stockez cette information dans un fichier séparé et sauvegardez-le dans un endroit sécurisé !
:    * Cliquez sur *Add Database User*.

!!! info "Information"
    
    Pour accéder à l'interface d'administration de Wordpress, il vous faut un compte administrateur qui aura les droits d'accès à la base de données. Sauvegardez impérativement ces informations dans un fichier séparé et sauvegardez-le dans un endroit sécurisé !

***

**Association du compte administrateur à la base de données**

:    * Cliquez sur *Attach User*.
:    * Sélectionnez votre l'utilisateur administrateur dans la liste déroulante.
:    * Cliquez sur *Attach User*.

!!! success "Une base de données lié à un administrateur est disponible pour Wordpress."

***

## Cron Job Let's Encrypt

<iframe width="100%" height="405" src="https://www.youtube-nocookie.com/embed/TvcAU5hLn-Y?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture setPlaybackQuality(hd1080);" allowfullscreen></iframe>

***

**Création d'une tâche automatisée pour le renouvellement de votre certificat de sécurité**

:    * Dans le menu de gauche, cliquez sur {==Cron Job==}.
:    * Cliquez sur {==Create a Cron Job==}.
:    * Nommez votre Cron Job : *Let's Encrypt*.
:    * Copiez / collez la commande ci-dessous dans le champ *Command* prévu à cet effet :
``` yaml
cd /etc/letsencrypt/ && ./certbot-auto renew && /etc/init.d/apache2 restart
```

:    * Définissez une périodicité de renouvellement en sélectionnant *Every 10 days at midnight*.
:    * Cliquez sur {==Add a Cron Job==}.

!!! success "Félicitations ! Votre certificat de sécurité Let's Encrypt sera renouvelé automatiquement tous les dix jours."

***

**Configuration de votre clé SSH publique pour Runcloud.io**

:    * Dans le menu de gauche, cliquez sur {==SSH Key==}.
:    * Cliquez sur {==Add SSH Key==}.
:    * Ajoutez un nom à votre clé SSH publique.
:    * Allez dans votre dossier `.ssh`.
:    * Ouvrez avec un éditeur de texte votre clé publique `id_rsa.pub`.
:    * Copiez / collez la clé publique dans le champ Runcloud.io
:    * Cliquez sur {==Add==}.

!!! success "Votre clé SSH publique est disponible, vous pourrez vous connecter à distance sur votre serveur dans Runcloud.io."

***

## Configurations Wordpress

<iframe width="100%" height="405" src="https://www.youtube-nocookie.com/embed/xcMjKatVbqQ?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture setPlaybackQuality(hd1080);" allowfullscreen></iframe>

***

**Association de la base de donnnées à Wordpress**

!!! info "Accéder à votre site web" 
    Vous pouvez maintenant accéder à votre site ! Tapez votre nom de domaine `https://example.com` dans la barre d'adresse URL  de votre navigateur, vous verrez alors la page d'installation classique de Wordpress.

:    * Sélectionnez la langue de votre choix.
:    * Cliquez sur {==C'est parti !==}.
:    * Entrez le nom de votre base de données Runcloud.io (A)
:    * Copiez/collez le nom d'administrateur de la base de données Runcloud.io (A)
:    * Copiez/collez le mot de passe de la base de données Runcloud.io (A)
:    * Laissez par défaut *Database Host* à `localhost`.
:    * Changez votre préfixe de table par quelque chose d'autre que `wp_`, tout en gardant ce format.
:    * Cliquez sur {==Valider==}.
:    * Cliquez sur {==Démarrer l'installation==}.

***

<iframe width="100%" height="405" src="https://www.youtube-nocookie.com/embed/TRinVkDEo2E?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture setPlaybackQuality(hd1080);" allowfullscreen></iframe>

***

**Informations du site et création de l'utilisateur administrateur**

!!! info "Identifiants à retenir !" 
    Pour cette étape, vous allez créer les accès administrateur à votre site Wordpress. Conservez absolument ces informations dans un endroit sécurisé !

:    * Donnez un titre à votre site web.
:    * Définissez votre nom d'utilisateur, stockez cette information dans un fichier séparé et sauvegardez-le dans un endroit sécurisé !
:    * Générez un mot de passe, stockez cette information dans un fichier séparé et sauvegardez-le dans un endroit sécurisé !
:    * Ajoutez votre adresse e-mail d'administrateur.
:    * Laissez la case *Search Engine Visibility* décochée.
:    * Cliquez sur {==Install Wordpress==}.
:    * Vous pouvez désormais vous {==connecter==} à votre interface Wordpress.

!!! success "Vous avez maintenant accès à l'interface d'administration Wordpress de votre site web."

***

## Réécriture d'URL

<iframe width="100%" height="405" src="https://www.youtube-nocookie.com/embed/HbBmtxZXZlA?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture setPlaybackQuality(hd1080);" allowfullscreen></iframe>

***

**Application par défaut**

:    * Revenez sur Runcloud.io et cliquez sur {==Web Application==}.
:    * Cliquez sur l'icon rouage à droite et sélectionnez *Set as default Web Application*.
:    * Cliquez sur {==Set As Default==}.

***

**Injection de la règle de réécriture d'URL**

!!! info "Information" 
    Le fichier Htaccess vous permet de définir des règles de redirection du trafic sur votre site web. Après cette étape, l'ensemble des utilisateurs essayant d'accéder à l'IP static de votre instance Lightsail seront automatiquement redirigés vers votre nom de domaine sécurisé.

:    * Cliquez sur le nom de votre application.
:    * Toujours dans le menu de gauche, cliquez sur {==File Manager==}.
:    * Sélectionnez le fichier `.htaccess` et cliquez sur *View/Edit*.

***

<iframe width="100%" height="405" src="https://www.youtube-nocookie.com/embed/ujgFncj9nf8?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture setPlaybackQuality(hd1080);" allowfullscreen></iframe>

***

**Configuration de la règle de réécriture d'URL**

:    * Une fois dans l'éditeur, copiez la règle de réécriture ci-dessous sous `RewriteBase /` :
``` yaml
RewriteCond %{HTTP_HOST} ^111\.111\.111\.111$ [NC]
RewriteRule ^(.*)$ https://votresite.com/$1 [R=301,L]
```

:    * Dans votre interface Lightsail, copiez l'adresse IP Static de votre instance.
:    * Collez l'IP Static dans le fichier Htaccess pour l'avoir sous les yeux.
:    * Ensuite, éditez la commande que vous avez précédemment copiée/collée, avec votre IP Static et nom de domaine. Vous pouvez vous appuyer sur cet exemple :
``` yaml
RewriteCond %{HTTP_HOST} ^35\.180\.184\.49$ [NC]
RewriteRule ^(.*)$ https://edelstorm.com/$1 [R=301,L]
```

:    * Une fois cette étape terminée, effacez l'IP Static et réorganisez le bloc de commandes pour plus de lisibilité.
:    * Cliquez sur Sauvegarder en haut ou appuyer sur les touches <kbd>Ctrl</kbd> + <kbd>S</kbd> pour enregistrer vos modifications.

!!! success "Félicitations ! Wordpress est correctement installé et configuré pour supporter la création de votre site web."

***