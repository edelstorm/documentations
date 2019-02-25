# Création de l'instance <small>- Lightsail</small>

!!! tip "Copiez / collez facilement les commandes du tutoriel en cliquant sur l'icône de droite."

    ``` sh
    Copiez cette phrase pour tester.
    ```

## Générer une paire de clés SSH

<p><a href="../assets/images/aws/creation-instance/fr/1a.gif" target="_blank"><img alt="Générer une paire de clé SSH sur Mac" src="../assets/images/aws/creation-instance/fr/1a.gif"></a></p>

***

**Sécurisation des communications entre votre ordinateur et votre futur serveur**

:    * {==Pour les ordinateurs Mac==} En haut à droite de votre écran, lancer une recherche Spotlight, tapez *Terminal* puis appuyez sur <kbd>Entrer</kbd>.
:    * {==Pour les ordinateurs Windows==} Plusieurs solutions en fonction de la version de votre OS. 
        * Soit, dans le menu *Démarrer*, tapez dans la barre de recherche *cmd*. Sélectionnez le premier résultat (Command Prompt), en faisant un clic droit puis sélectionnez *exécuter en tant qu'administrateur*.
        * Soit, ouvrez la barre de recherche de l'ordinateur en vous rendant sur votre bureau puis en tapant <kbd>⊞Win</kbd> + <kbd>S</kbd>. Tapez *cmd* dans le champ de recherche. Sélectionnez le premier résultat (Command Prompt), en faisant un clic droit puis sélectionnez *exécuter en tant qu'administrateur*.

:    * Une fois dans votre terminal, tapez la commande ci-dessous et appuyez sur <kbd>Entrer</kbd>.
``` sh
ssh-keygen -t rsa
```

:    * Vous pouvez ensuite nommer votre paire de clés, sinon appuyez juste sur <kbd>Entrer</kbd>.
:    * Définissez un mot de passe et appuyez sur <kbd>Entrer</kbd>.
:    * Ressaisissez votre mot de passe et appuyez sur <kbd>Entrer</kbd>.

!!! note "À savoir"

    Lorsque vous tapez votre mot de passe dans un terminal, vous ne pourrez pas le voir se former sur votre écran.<br>
    C'est comme si vous n'étiez pas en train de taper sur votre clavier, mais pour le terminal vous êtes bien en train de taper. Vous devez donc le définir à l'aveugle !

***

<p><a href="../assets/images/aws/creation-instance/fr/1b.gif" target="_blank"><img alt="Localiser une paire de clé SSH sur Mac" src="../assets/images/aws/creation-instance/fr/1b.gif"></a></p>

***

**Localisation de votre paire de clés SSH**

:    * Ouvrez votre Finder, cliquez en haut dans la barre de menu sur **Aller**, puis cliquez sur **Aller au dossier...**
:    * Dans la barre de recherche, tapez cette commande et appuyez sur <kbd>Entrer</kbd>.
``` sh
~/.ssh
```

:    * Une fois dans le dossier {==.ssh==} faites glisser l'icône dossier en haut de la fenêtre du Finder dans votre barre de favoris. Cela vous permettra d'y accéder plus facilement pour la prochaine étape.

!!! success "Votre machine a généré votre paire de clés SSH que vous pouvez facilement localiser à partir de son dossier !"

***

## Création de l'instance

<iframe width="100%" height="405" src="https://www.youtube-nocookie.com/embed/NG6jjPI0bRg?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture setPlaybackQuality(hd1080);" allowfullscreen></iframe>

***

**Options de l'instance Amazon Lightsail**

:    * Dans votre console de management AWS, cherchez le service *Lightsail* dans la barre recherche et cliquez dessus.
:    * Sélectionnez la langue que vous souhaitez pour l'interface.
:    * Cliquez sur {==Créer une instance==}.
:    * Choisissez l'emplacement de l'instance, la région que vous choississez doit être au plus proche de vos futurs utilisateurs. 
:    * Laissez par défaut la zone de disponibilité de l'instance.
:    * Choisissez *Linux/Unix* comme plateforme.
:    * Cliquez sur l'onglet *Système d'exploitation uniquement* et sélectionnez *Ubuntu 16.04 LTS* comme système d'exploitation.
:    * Nous n'ajouterons pas de script de lancement. (I)
:    * Cliquez sur *Modifier une paire de clés SSH* et cliquez sur *Charger un nouveau* puis sur {==Charger==}. 
:    * Cliquez sur *Choisir un fichier* et choississez le fichier `id_rsa.pub` dans votre dossier `~/.ssh` puis cliquez sur {==Charger une clé==}. Fournir votre clé SSH publique vous permettra de sécuriser les communications entre votre machine et votre instance Amazon Lightsail.
:    * Choississez le plan d'instance basique à **3.50$ par mois**, le premier mois d'essais est gratuit.
:    * Nommez votre instance, de préférence avec votre nom de domaine. (A)
:    * Vous pouvez appliquer des balises d'identifications à cette instance si vous pensez comptez en avoir plusieurs par la suite.
:    * Cliquez sur {==Créer une instance==} et patientez un instant que votre instance s'initialise.

!!! info "Informations"

    À partir de cette étape, vous souscrivez au service Amazon Lighsail, vous pouvez supprimer cette instance à tout moment si vous n'en avez plus besoin. Consultez l'évolution de votre facturation depuis votre <a href="https://console.aws.amazon.com/billing/home#/" target="_blank">console de management AWS</a>.

!!! success "Votre instance Amazon Lightsail est prête à être utilisée pour votre site web."

***

## Réglages du Firewall

<p><a href="../assets/images/aws/creation-instance/fr/11.gif" target="_blank"><img alt="Réglages Firewall Instance Amazon Lightsail" src="../assets/images/aws/creation-instance/fr/11.gif"></a></p>

***

**Ouverture des ports HTTPS & FTP**

:    * Cliquez sur votre instance et rendez-vous dans la section *Mise en réseau*.
:    * Cliquez sur *Ajouter un autre élément*.
:    * Changez le *Personalisé* en *HTTPS*.
:    * Cliquez sur *Ajouter un autre élément*.
:    * Laissez la partie *Personalisé* et ajoutez juste *34210* dans la colonne *Plage de ports*. 
:    * Cette action permet de sécuriser les communications entre vos utilisateurs, les applications externes et votre instance.
:    * Cliquez sur {==Sauvegarder==}.

!!! success "Votre instance est correctement configurée pour la suite de ce tutoriel"

***

## IP Statique

<p><a href="../assets/images/aws/creation-instance/fr/12.gif" target="_blank"><img alt="IP Statique Amazon Lightsail" src="../assets/images/aws/creation-instance/fr/12.gif"></a></p>

***

**Fixation de l'adresse IP de votre instance**

!!! info "IP dynamique et IP statique"

    Par défaut, votre instance a une adresse IP dynamique. C'est-à-dire que chaque fois que vous redémarrez votre instance, son adresse IP change. Pour que votre site web soit joignable depuis une adresse unique, il faut lier votre instance à une IP statique. Une IP statique est gratuite lorsqu'elle est attachée à une instance.

:    * Dans la section *Mise en réseau* de votre instance, cliquez sur *Attacher une IP Statique*.
:    * Sélectionnez la même zone géographique que celle choisie pour votre instance.
:    * Attachez votre instance à cette IP statique.
:    * Nommez votre IP statique de cette façon, avec VOTRE nom de domaine : *StaticIp-VotreNomDeDomaine*.
:    * Cliquez sur {==Créer==}.

!!! success "Votre instance possède une adresse IP unique !"

***

## Zone DNS

<p><a href="../assets/images/aws/creation-instance/fr/13.gif" target="_blank"><img alt="Zone DNS Amazon Lightsail" src="../assets/images/aws/creation-instance/fr/13.gif"></a></p>

***

**Association de votre instance à votre nom de domaine**

:    * Cliquez sur *Accueil* en haut de votre interface Lightsail, puis rendez-vous dans l'onglet *Mise en réseau*.
:    * Cliquez sur {==Créer une zone DNS==}.
:    * Dans le champ, spécifiez votre nom de domaine.
:    * Vous pouvez associer des tags d'identifications à cette zone DNS.
:    * Cliquez sur {==Créer une zone DNS==}

!!! success "Votre instance possède une zone DNS !"

***

<p><a href="../assets/images/aws/creation-instance/fr/14.gif" target="_blank"><img alt="Zone DNS Amazon Lightsail" src="../assets/images/aws/creation-instance/fr/14.gif"></a></p>

***

**Création des enregistrements pour votre zone DNS**

:    * Cliquez sur *Ajouter un enregistrement*.
:    * Ajoutez un premier enregistrement de type A pour `@.VotreNomDeDomaine.com` pointant vers votre IP statique. <br>
       **Pour se faire**, tapez <kbd>@</kbd> dans le 1er champ qui se présente à vous à gauche. Puis sélectionnez à droite l'adresse IP statique que nous venons de créer. Cliquez sur l'icone verte pour valider cette action.
:    * Cliquez à nouveau sur *Ajouter un enregistrement*
:    * Ajoutez un second enregistrement de type A pour `www.VotreNomDeDomaine.com` pointant vers votre IP statique.<br>
       **Pour se faire**, tapez <kbd>www</kbd> dans le 1er champ qui se présente à vous à gauche. Puis sélectionnez à droite l'adresse IP statique que nous venons de créer. Cliquez sur l'icone verte pour valider cette action.

!!! success "L'IP statique de votre instance pointe vers votre nom de domaine !"

***

<p><a href="../assets/images/aws/creation-instance/fr/15.gif" target="_blank"><img alt="Enregistrements DNS Amazon Lightsail" src="../assets/images/aws/creation-instance/fr/15.gif"></a></p>

***

**Injection des nouveaux noms de serveurs pour votre nom de domaine**
:    * Nous sommes toujours sur la même page. Sous les enregistrements se trouve une section *Nom de serveurs*. Il s'agit de vos nouveaux noms de serveurs pour cette zone DNS. <br>
    **Copiez le premier**.
:    * Ouvrez dans un nouvel onglet votre console d'administration AWS. Vous pouvez facilement y accéder en faisant un clic droit, ouvrir dans un nouvel onglet, sur *AWS* en haut à droite de votre interface Lightsail.
:    * Cherchez le service *Route 53* dans la barre de recherche et cliquez dessus.
:    * Sur la gauche de l'interface, cliquez sur *Domaines enregistrés*.
:    * Cliquez sur votre nom de domaine.
:    * Sur la droite de l'interface, cliquez sur *Ajouter ou éditer les noms de serveurs*, remplacez les actuels noms de serveurs par les quatre nouveaux noms de serveurs de votre zone DNS, **en les copie-collant un à un**.
:    * Cliquez sur {==Mettre à jour==}.

!!! success "Les serveurs de votre zone DNS correspondent à votre nom de domaine !"

***

## Options de l'instance

!!! info "Tour d'horizon"

    Vous venez de créer votre première instance. En cliquant sur son nom depuis l'accueil, vous pourrez découvrir de nombreuses options que nous allons vous présenter ci-dessous.

<p><a href="../assets/images/aws/creation-instance/fr/4.png" target="_blank"><img alt="Options Instance Amazon Lightsail" src="../assets/images/aws/creation-instance/fr/4.png"></a></p>

***

**Connexion SSH depuis votre navigateur**

:    * Dans l'onglet *Connexion*, en cliquant sur *Se connecter à l'aide de SSH* vous pourrez accéder en mode sécurisé au terminal de votre serveur à distance.
:    * Vous pouvez choisir de vous connecter, d'arrêter, de redémarrer et de supprimer cette instance.
:    * Vous pouvez utiliser votre IP statique et nom d'utilisateur affichés ici, si vous souhaitez vous connecter en SSH directement avec le terminal de votre ordinateur.

***

<p><a href="../assets/images/aws/creation-instance/fr/5.png" target="_blank"><img alt="Connexion SSH Instance Amazon Lightsail" src="../assets/images/aws/creation-instance/fr/5.png"></a></p>

***

**Stockage évolutif**

:    * Dans l'onglet *Stockage*, avec le plan à 3.50$ par mois vous bénéficiez de 20Go de stockage sur cette instance. Ce qui est largement suffisant pour vos besoins actuels.
:    * Si vous avez besoin de plus d'espace de stockage, vous pouvez ajouter des disques supplémentaires à cette instance. L'ajout de nouveaux disques est une fonction payante.

***

<p><a href="../assets/images/aws/creation-instance/fr/6.png" target="_blank"><img alt="Stockage Évolutif Instance Amazon Lightsail" src="../assets/images/aws/creation-instance/fr/6.png"></a></p>

***

**Métriques**

:    * Dans l'onglet *Métriques*, vous pouvez obtenir les statistiques basées sur l'usage que vous faites de votre instance.

***

<p><a href="../assets/images/aws/creation-instance/fr/7.png" target="_blank"><img alt="Métriques Instance Amazon Lightsail" src="../assets/images/aws/creation-instance/fr/7.png"></a></p>

***

**Snapshots**

:    * L'onglet *Snapshots* est une fonctionnalité très importante sur laquelle nous reviendrons par la suite. Un snapshot vous permet de sauvegarder la totalité de votre instance (et donc votre site) à un instant T. Cela peut donc vous permettre de revenir à une version antérieure de votre instance en cas d'erreur.

***

<p><a href="../assets/images/aws/creation-instance/fr/8.png" target="_blank"><img alt="Snapshots Instance Amazon Lightsail" src="../assets/images/aws/creation-instance/fr/8.png"></a></p>

***

**Tags**

:    * Vous pouvez ajouter des tags à votre instance pour l'identifier plus facilement si vous en avez plusieurs.

***

<p><a href="../assets/images/aws/creation-instance/fr/9.png" target="_blank"><img alt="Tags Instance Amazon Lightsail" src="../assets/images/aws/creation-instance/fr/9.png"></a></p>

***

**Historique**

:    * Vous pouvez consulter l'historique pour voir vos dernières actions sur cette instance.

***

<p><a href="../assets/images/aws/creation-instance/fr/10.png" target="_blank"><img alt="Historique Instance Amazon Lightsail" src="../assets/images/aws/creation-instance/fr/10.png"></a></p>

***

**Suppression**

:    * À tout moment, vous pouvez supprimer votre instance depuis cet onglet.

***

!!! success "Félicitation votre instance est configurée pour votre site web !"