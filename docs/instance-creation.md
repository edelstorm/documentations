# Instance creation <small>- Lightsail</small>

!!! tip "Copy / paste the commands more easily by clicking on the icon on the right."

    ``` sh
    Copy this sentence to try.
    ```

## Generate an SSH key

<p><a href="../assets/images/aws/creation-instance/en/1a.gif" target="_blank"><img alt="Generate an SSH key on Mac" src="../assets/images/aws/creation-instance/en/1a.gif"></a></p>

***

**Securing communications between your computer and your future server**

:    * {==For the Mac users==} At the top right of your computer screen, click on the magnifier icon, start a Spotlight research. Type *Terminal* then hit <kbd>Enter</kbd>.
:    * {==For the Windows users==} Two ways depending on your OS version. 
        * In the *Start* menu, type *cmd* in the search bar. Select the first result (Command Prompt), by doing a click right and select the *execute as an administrator* mode.
        * Or, open your computer search bar from your desktop by typing <kbd>⊞Win</kbd> + <kbd>S</kbd>. Then, type *cmd* in the research field. Select the first result (Command Prompt), by doing a click right and select the *execute as an administrator* mode.

:    * When you are on your terminal, type this command and hit <kbd>Enter</kbd>.
``` sh
ssh-keygen -t rsa
```

:    * Then, you can name your keys, then hit <kbd>Enter</kbd>.

!!! note "To keep in mind"

    When you type your password in a terminal, what you type will not appear on the screen. It's like your not typing, but you are!<br>
    So you will have to type it blindly.


:    * Choose a password and hit <kbd>Enter</kbd>.
:    * Type your password again and hit <kbd>Enter</kbd>.

***

<p><a href="../assets/images/aws/creation-instance/en/1b.gif" target="_blank"><img alt="Localize an SSH key on Mac" src="../assets/images/aws/creation-instance/en/1b.gif"></a></p>

***

**Tracking your SSH key**

:    * Open your Finder, click on the top menu and choose **Go**, then click on **Go to file...**
:    * In the search bar, type this command and hit <kbd>Enter</kbd>.
``` sh
~/.ssh
```

:    * Once you are in the file {==.ssh==}, drag the file icon you can see at the top of the Finder windows, on your favorites. This will make it more easy for you to access it for the next step.

!!! success "Your computer generated SSH keys that you can find easily from its file!"

***

## Instance creation

<p><a href="../assets/images/aws/creation-instance/en/2a.gif" target="_blank"><img alt="Create Instance Amazon Lightsail" src="../assets/images/aws/creation-instance/en/2a.gif"></a></p>

***

**Amazon Lightsail instance creation**

:    * Go on your AWS administration console, type *Lightsail* in the search bar and click on this service.
:    * Choose the language you prefer.
:    * Click on {==Create an instance==}.
***

<p><a href="../assets/images/aws/creation-instance/en/2b.gif" target="_blank"><img alt="Creation Instance Amazon Lightsail" src="../assets/images/aws/creation-instance/en/2b.gif"></a></p>

***

**Geographic zone, image type, and SSH connexion**

:    * Choose a region for your instance, it has to be close to where your future users will be located. Leave the instance zone by default.
:    * Choose *Linux/Unix* as a platform.
:    * Select *Ubuntu 16.04 LTS* an operating system.
:    * Upload your SSH public key (the on that ends up with `.pub`). It will secure communications between your computer and this instance.
***

<p><a href="../assets/images/aws/creation-instance/en/3.gif" target="_blank"><img alt="Geographic Zone, Image Type and SSH key Amazon Lightsail" src="../assets/images/aws/creation-instance/en/3.gif"></a></p>

***

**Instance and identification plan**

!!! info "AWS billing"

    From this step, you are subscribing to the Amazon Lighsail service. Your account and instance can be deleted at any point if you don't need it anymore. You can check your billing evolution <a href="https://console.aws.amazon.com/billing/home#/" target="_blank">here</a>.

:    * Select the basic **3.50$ per month** plan, the first trial month is free.
:    * Name your instance, with your domain name preferably.
:    * You can also add identifications tags if you think you are going to create other instances in the future.
:    * Click on {==Create an instance==} and wait for 5 minutes that your instance to initialize.

!!! success "Votre instance est prête à être utilisée pour votre site web."

***

## Réglages du Firewall

<p><a href="../assets/images/aws/creation-instance/en/11.gif" target="_blank"><img alt="Firewall Settings Amazon Lightsail" src="../assets/images/aws/creation-instance/en/11.gif"></a></p>

***

**Opening of the HTTPS & FTP ports**

:    * Click on your instance and go to the *Networking* section.
:    * Click on *add another*.
:    * Change the *Custom* to *HTTPS*.
:    * Click on *add another*.
:    * Leave the *Custom* and add *34210* on *Port range*. 
:    * This will secure the communication between your users, the extern's apps and your instance.
:    * Click on {==Save==}.

!!! success "Your instance is correctly configured for the rest of this tutorial!"

***

## Static IP

**Attach the IP address of your instance**

<p><a href="../assets/images/aws/creation-instance/en/12.gif" target="_blank"><img alt="Static IP Amazon Lightsail" src="../assets/images/aws/creation-instance/en/12.gif"></a></p>

***

!!! info "Dynamic IP and static IP"

     By default, your instance has a dynamic IP. Meaning that each time you restart your instance, your IP address changes. You need a static IP so your website is reachable from a unique address. A static IP is free when it is linked to an instance.

:    * Go in the *Networking* section of your instance and click on *Attach a Static IP*.
:    * Select the same geographic zone than the one you chose for your instance.
:    * Attach your instance to this Static IP.
:    * Name your static IP this way, with YOUR domain name: *StaticIp-YourDomainName*.
:    * Click on {==Create==}.

!!! success "Your instance now has a unique IP!"

***

## DNS zone

<p><a href="../assets/images/aws/creation-instance/en/13.gif" target="_blank"><img alt="DNS Zone Amazon Lightsail" src="../assets/images/aws/creation-instance/en/13.gif"></a></p>

***

**Combination of your instance and domain name**

:    * Click on *Home* at the top of the page, then go and click on the *Networking* tab.
:    * Click on {==Create a DNS zone==}.
:    * In the field, write your domain name.
:    * You can add identifications tags to this DNS zone.
:    * Click on {==Create a DNS zone==}

!!! success "Your instance now has a DNS zone!"

***

<p><a href="../assets/images/aws/creation-instance/en/14.gif" target="_blank"><img alt="DNS Zone Amazon Lightsail" src="../assets/images/aws/creation-instance/en/14.gif"></a></p>

***

**Creation of DNS records**

:    * Click on *Add record*.
:    * Add a first type A record for `@.YourDomainName.com` pointing to your static IP. <br>
       **To do so**, type <kbd>@</kbd> on the first field on the left. Then select the static IP you just created on the right.
:    * Click on *Add record* again.
:    * Add a second type A for `www.YourDomainName.com` pointing to your static IP.<br>
       **To do so**, type <kbd>www</kbd> on the first field on the left. Then select the static IP you just created on the right.

!!! success "The static IP of your instance now point to your domain name!"

***

<p><a href="../assets/images/aws/creation-instance/en/15.gif" target="_blank"><img alt="DNS Records Amazon Lightsail" src="../assets/images/aws/creation-instance/en/15.gif"></a></p>

***

**Adding new name servers for your domain name**
:    * We are still on the same page. Under the records, you can see the *Nameservers*. Those are your new name servers for your DNS zone.<br>
    **Copy the first**.
:    * Open your AWS homepage on a new tab. You can easily do so by doing a right click, open in a new tap on *AWS* at the top right of your page. 
:    * Search for *Route 53* on the search bar and click on it.
:    * On the left side of the interface, click on *Registered domains*.
:    * Click on your domain name.
:    * On the right of the interface on *Add or edit name servers*. Then, replace the name servers you see with the 4 new one from your DNS zone **by copy/pasting it, one by one**.
:    * Click on {==Update==}.

!!! success "Your DNS servers now match your domain name!"

***

## Instance options

!!! info "Overview"

    You just created your first instance. By clicking on its name from the Lightsail homepage you will discover that you have some options at your disposal. We are going to tell you about it.

<p><a href="../assets/images/aws/creation-instance/en/4.png" target="_blank"><img alt="Instance Options Amazon Lightsail" src="../assets/images/aws/creation-instance/en/4.png"></a></p>

***

**SSH connexion from your browser**

:    * In the *Connect* tab, by clicking on *Connect using SSH* you can access in a secure way at your server through a terminal.
:    * You can choose to connect to, stop, restart or delete this instance.
:    * You can use your static IP and your domain name displayed here if you want to connect to your SSH directly from your computer.

***

<p><a href="../assets/images/aws/creation-instance/en/5.png" target="_blank"><img alt="SSH Connexion Instance Amazon Lightsail" src="../assets/images/aws/creation-instance/en/5.png"></a></p>

***

**Storage**

:    * In the *Storage* tab, with the 3.50$ per month plan, you beneficiate of 20Go storage on this instance. Which is enough for your currents needs.
:    * If you need more storage space, you can add storage discs to this instance. Adding new discs in a paying service.

***

<p><a href="../assets/images/aws/creation-instance/en/6.png" target="_blank"><img alt="Storage Instance Amazon Lightsail" src="../assets/images/aws/creation-instance/en/6.png"></a></p>

***

**Metrics**

:    * In the *Metrics* tag, you can get statistics on what you do with your instance.

***

<p><a href="../assets/images/aws/creation-instance/en/7.png" target="_blank"><img alt="Metrics Instance Amazon Lightsail" src="../assets/images/aws/creation-instance/en/7.png"></a></p>

***

**Snapshots**

:    * The *Snapshots* tab is a very important functionality. We will talk more about it later, but basically, it allows you to save your instance and its content when you want it. It will allow you to come back to an earlier version of your instance (and your website so) if you make a mistake.

***

<p><a href="../assets/images/aws/creation-instance/en/8.png" target="_blank"><img alt="Snapshots Instance Amazon Lightsail" src="../assets/images/aws/creation-instance/en/8.png"></a></p>

***

**Tags**

:    * You can add tags to your instance to identify it more easily if you have several ones.
***

<p><a href="../assets/images/aws/creation-instance/en/9.png" target="_blank"><img alt="Tags Instance Amazon Lightsail" src="../assets/images/aws/creation-instance/en/9.png"></a></p>

***

**History**

:    * You can consult the history of your last actions on this instance.

***

<p><a href="../assets/images/aws/creation-instance/en/10.png" target="_blank"><img alt="History Instance Amazon Lightsail" src="../assets/images/aws/creation-instance/en/10.png"></a></p>

***

**Delete**

:    * At any time, you can delete your instance through this tab.

***

!!! success "Congratulation your instance is now configured for your website!"