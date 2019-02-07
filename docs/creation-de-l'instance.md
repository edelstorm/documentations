# Création de l'instance <small>- Lightsail</small>

!!! tip "Copier / coller facilement les commandes du tutoriel en cliquant sur l'icône de droite."

    ``` sh
    Copiez cette phrase pour tester.
    ```

## Générer une paire de clés SSH

{==

**Améliorations nécessaires**<br> 
1) Sur cette étape, il faut faire deux GIF : première partie (génération de la clé SSH) et deuxième partie (localisation du dossier SSH)<br> 
2) Ralentis le tempo globale pour rentrer plus visible l'ensemble des opérations, teste x1.5<br> 

==}

[![Material for MkDocs](assets/images/aws/creation-instance/en/1.gif)](assets/images/aws/creation-instance/en/1.gif)

***

**Sécurisation des communications entre votre ordinateur et votre futur serveur**

:    * En haut à droite de votre écran, lancer une recherche Spotlight, tapez *Terminal* puis appuyez sur <kbd>Entrer</kbd>.
:    * Une fois dans votre terminal, tapez cette commande et appuyez sur <kbd>Entrer</kbd>.
``` sh
ssh-keygen -t rsa
```

:    * Vous pouvez ensuite nommer votre paire de clés, sinon appuyez juste sur <kbd>Entrer</kbd>.

!!! note "À savoir"

    Lorsque vous tapez votre mot de passe dans un terminal, vous ne pourrez pas voir se former sur votre écran.<br>
    C'est comme si n'étiez pas en train de taper sur votre clavier, mais pour le terminal vous êtes bien en train de taper.<br> 
    Vous devez donc le définir à l'aveugle !

:    * Définissez un mot de passe et appuyez sur <kbd>Entrer</kbd>.
:    * Ressaisissez votre mot de passe et appuyez sur <kbd>Entrer</kbd>.

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

[![Material for MkDocs](assets/images/aws/creation-instance/en/2.gif)](assets/images/aws/creation-instance/en/2.gif)

***

**Création de votre instance Amazon Lightsail**

:    * Rendez-vous sur votre console d'administration AWS, tapez *Lightsail* dans la barre recherche et cliquez sur ce service.
:    * Sélectionnez la langue que vous souhaitez pour votre interface.
:    * Cliquez sur {==Créer une instance==}.

***

**Zone géographique, type d'image et connexion SSH**

:    * Choisissez la région de votre instance, elle doit être au plus proche de vos futurs utilisateurs. Laissez par défaut la zone de votre instance.
:    * Choisissez *Linux/Unix* comme plateforme.
:    * Sélectionnez *Ubuntu 16.04 LTS* comme système d'exploitation.
:    * Téléchargez votre paire de clés SSH publique (celle se terminant par `.pub`) afin de sécuriser les communications entre votre machine et cette instance.

***

[![Material for MkDocs](assets/images/aws/creation-instance/en/3.gif)](assets/images/aws/creation-instance/en/3.gif)

***

**Plan d'instance et identification**

!!! info "Facturation AWS"

    À partir de cette étape, vous souscrivez au service Amazon Lighsail, votre instance peut-être supprimée à tout moment si vous n'en avez plus besoin. Vous pouvez consulter l'évolution de votre <a href="https://console.aws.amazon.com/billing/home#/" target="_blank">facturation</a>.

:    * Sélectionnez le plan basique à **3.50$ par mois**, le premier mois d'essais est gratuit.
:    * Nommez votre instance, de préférence avec votre nom de domaine.
:    * Vous pouvez aussi appliquer des tags d'identifications, si vous pensez créer de nombreuses instances par la suite.
:    * Cliquez sur {==Créer une instance==} et attendez 5 minutes que votre instance s'initialise.

!!! success "Votre instance est prête à être utilisée pour votre site web."

***

## Réglages du Firewall

[![Material for MkDocs](assets/images/aws/creation-instance/en/11.gif)](assets/images/aws/creation-instance/en/11.gif)

***

**Ouverture des ports HTTPS & FTP**

:    * Cliquez sur votre instance et rendez-vous dans la section *Mise en réseau*.
:    * Ouvrez les ports HTTPS et FTP (34210) pour sécuriser les communications entre vos utilisateurs, les applications externes et votre instance.
:    * Cliquez sur {==Sauvegarder==}.

!!! success "Votre instance est correctement configurée pour la suite de ce tutoriel"

***

## IP Statique

{==

😭 Tu as oublié un GIF ici. Celui ou je clique sur Static IP pour le créer et l'attacher à l'instance.

==}

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

[![Material for MkDocs](assets/images/aws/creation-instance/en/12.gif)](assets/images/aws/creation-instance/en/12.gif)

***

**Association de votre instance à votre nom de domaine**

:    * Cliquez sur *Accueil* en haut de votre interface Lightsail, puis rendez vous dans l'onglet *Mise en réseau*.
:    * Cliquez sur {==Créer une zone DNS==}.
:    * Dans le champ, spécifiez votre nom de domaine.
:    * Vous pouvez associer des tags d'identifications à cette zone DNS.
:    * Cliquez sur {==Créer une zone DNS==}

!!! success "Votre instance possède une zone DNS !"

***

[![Material for MkDocs](assets/images/aws/creation-instance/en/13.gif)](assets/images/aws/creation-instance/en/13.gif)

***

**Création des enregistrements pour votre zone DNS**

:    * Cliquez sur *Ajouter un enregistrement*.
:    * Ajoutez un premier enregistrement de type A pour `@.VotreNomDeDomaine.com` pointant vers votre IP statique. <br>
       **Pour se faire**, tapez <kbd>@</kbd> dans le 1er champ qui se présente à vous à gauche. Puis sélectionnez à droite l'adresse IP statique que nous venons de créer.
:    * Cliquez à nouveau sur *Ajouter un enregistrement*
:    * Ajoutez un second enregistrement de type A pour `www.VotreNomDeDomaine.com` pointant vers votre IP statique.<br>
       **Pour se faire**, tapez <kbd>www</kbd> dans le 1er champ qui se présente à vous à gauche. Puis sélectionnez à droite l'adresse IP statique que nous venons de créer.

!!! success "L'IP statique de votre instance pointe vers votre nom de domaine !"

***

[![Material for MkDocs](assets/images/aws/creation-instance/en/14.gif)](assets/images/aws/creation-instance/en/14.gif)

***

**Injection des nouveaux serveurs de nom pour votre nom de domaine**
:    * Nous sommes toujours sur la même page. Sous les enregistrements se trouve une section *Nom de serveurs*. Il s'agit de vos nouveaux   noms de serveurs pour cette zone DNS. <br>
    **Copiez le premier**.
:    * Ouvrez dans un nouvel onglet votre console d'administration AWS. Vous pouvez facilement y accéder en faisant un clic droit, ouvrir dans un nouvel onglet, sur *AWS* en haut à droite de votre interface Lightsail.
:    * Cherchez le service *Route 53* dans la barre de recherche et cliquez dessus.
:    * Sur la gauche de l'interface, cliquez sur *Domaines enregistrés*.
:    * Cliquez sur votre nom de domaine.
:    * Sur la droite de l'interface, cliquez sur *Ajouter ou editer les noms de serveurs*, remplacez les actuels noms de serveurs par les quatre nouveaux noms de serveurs de votre zone DNS, **en les copie-collant un à un**.
:    * Cliquez sur {==Mettre à jour==}.

!!! success "Les serveurs de votre zone DNS correspondent à votre nom de domaine !"

***

## Options de l'instance

{==

**Améliorations nécessaires**<br> 
Cropper les images<br> 

==}

!!! info "Tour d'horizon"

    Vous venez de créer votre première instance. En cliquant sur son nom depuis l'accueil, vous découvrirez de nombreuses options que nous allons vous présenter ci-dessous.

[![Material for MkDocs](assets/images/aws/creation-instance/en/4.png)](assets/images/aws/creation-instance/en/4.png)

***

**Connexion SSH depuis votre navigateur**

:    * Dans l'onglet *Connexion*, en cliquant sur *Se connecter à l'aide de SSH* vous pourrez accéder en mode sécurisé au terminal de votre serveur à distance.
:    * Vous pouvez choisir de vous connecter, d'arrêter, de redémarrer et de supprimer cette instance.
:    * Vous pouvez utiliser votre IP statique et nom d'utilisateur affichés ici, si vous souhaitez vous connecter en SSH directement avec le terminal de votre ordinateur.

***

[![Material for MkDocs](assets/images/aws/creation-instance/en/5.png)](assets/images/aws/creation-instance/en/5.png)

***

**Stockage évolutif**

:    * Dans l'onglet *Stockage*, avec le plan à 3.50$ par mois vous bénéficiez de 20Go de stockage sur cette instance. Ce qui est largement suffisant pour vos besoins actuels.
:    * Si vous avez besoin de plus d'espace de stockage, vous pouvez ajouter des disques supplémentaires à cette instance. L'ajout de nouveaux disques est une fonction payante.

***

[![Material for MkDocs](assets/images/aws/creation-instance/en/6.png)](assets/images/aws/creation-instance/en/6.png)

***

**Métriques**

:    * Dans l'onglet *Métriques*, vous pouvez obtenir les statistiques basées sur l'usage que vous faites de votre instance.

***

[![Material for MkDocs](assets/images/aws/creation-instance/en/7.png)](assets/images/aws/creation-instance/en/7.png)

***

**Snapshots**

:    * L'onglet *Snapshots* est une fonctionnalité très importante sur laquelle nous reviendrons par la suite. Un snapshot vous permet de sauvegarder la totalité de votre instance (et donc votre site) à un instant T. Cela peut donc vous permettre de revenir à une version antérieure de votre instance en cas d'erreur.

***

[![Material for MkDocs](assets/images/aws/creation-instance/en/8.png)](assets/images/aws/creation-instance/en/8.png)

***

**Tags**

:    * Vous pouvez ajouter des tags à votre instance pour l'identifier plus facilement si vous en avez plusieurs.

***

[![Material for MkDocs](assets/images/aws/creation-instance/en/9.png)](assets/images/aws/creation-instance/en/9.png)

***

**Historique**

:    * Vous pouvez consulter l'historique pour voir vos dernières actions sur cette instance.

***

[![Material for MkDocs](assets/images/aws/creation-instance/en/10.png)](assets/images/aws/creation-instance/en/10.png)

***

**Suppression**

:    * À tout moment, vous pouvez supprimer votre instance depuis cet onglet.

***

!!! success "Félicitation votre instance est configurée pour votre site web !"