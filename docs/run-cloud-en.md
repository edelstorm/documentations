# Run Cloud <small>- AWS</small>

## Sign up

!!! info "Runcloud.io"

    Runcloud is a service that offers a free and secure way to spread PHP apps. The goal of this step is to connect your Lightsail instance to the Runcloud interface so we can install and configure Wordpress on it.

[![Material for MkDocs](assets/images/aws/run-cloud/en/1.gif)](assets/images/aws/run-cloud/en/1.gif)

***

**Go to <a href="https://runcloud.io/" target="_blank">RunCloud.io</a>**

!!! info "AWS instance windows"
    Keep a window open on your Lightsail instance page. You will need to copy/paste your instance static IP address.

:    * Click on {==*Sign Up*==} at the top right.
:    * Fill the form and click on {==*Create Free Account*==}.

***

[![Material for MkDocs](assets/images/aws/run-cloud/en/2.gif)](assets/images/aws/run-cloud/en/2.gif)

***

:    * Configure your account by clicking on the link you just received on your email box.
:    * Connect to your account with your login and passwords by clicking on {==*Sign in to Dashboard*==}.

!!! success "You now have a Runcloud.io account!"

***

[![Material for MkDocs](assets/images/aws/run-cloud/en/3a.gif)](assets/images/aws/run-cloud/en/3a.gif)

***

**Choose your plan**

:    * At the top right, click on the green button *Upgrade Now*.
:    * Click on the green button *Change plan*.
:    * Select the *Basic* plan. We advise you to select the yearly payement method, it will be like payed 6,66$ per month instead of 8$ per month. But it's up yo you.
:    * Click on the green button *Choose plan*.
:    * Click on the big blue button on the left, {==*Add a new payement method*==}.
:    * You can now choose between paying by PayPal or by card.


***

## Installation

[![Material for MkDocs](assets/images/aws/run-cloud/en/3.gif)](assets/images/aws/run-cloud/en/3.gif)

***

**Install Runcloud on your Lightsail instance**

:    * Click on *Connect a New Server*.
:    * Name your server with your websote name.
:    * Copy/paste the static IP of your instance.
:    * Put *AWS* as a Server Provider.
:    * Click on {==*Connect this server*==}.

***

[![Material for MkDocs](assets/images/aws/run-cloud/en/3b.gif)](assets/images/aws/run-cloud/en/3b.gif)

***

:    * RunCloud is going to generate an installation command on your server. Copy it by clicking on the green icon on the right.
:    * Go back on Lightsail and connect to your SSH instance by clicking on *Connect*.
:    * Once you are on the terminal, type the command below (make sure to type it, you can not copy/paste it). This will allow you to get admin right. Then hit <kbd>Enter</kbd>.
``` sh
sudo su
```

:    * Click on the orange icon at the bottom right of the terminal window. Paste *(attention to understand how to paste on the terminal, look at the next step)* the installation command from Runcloud on the terminal. 
:    * Click on the black part of the terminal, do a right click to paste the command on the terminal, then hit <kbd>Enter</kbd>.

***

[![Material for MkDocs](assets/images/aws/run-cloud/en/5.gif)](assets/images/aws/run-cloud/en/5.gif)
[![Material for MkDocs](assets/images/aws/run-cloud/en/4.gif)](assets/images/aws/run-cloud/en/4.gif)

***

!!! warning "Runcloudvset up"

    The command is going to install Runcloud. DO NOT leave the terminal before the process is done. It can take around 10 minutes.
    Once the process is done, copy the MySQL login and password and paste it on a secure document on your computer!<br>
    **To copy on a terminal, you have to select what you want to copy, then click on the orange icon at the bottom right. You will find what you just select. You can now from this place, copy the content.**

!!! success "You now have access to the admin interface of your Runcloud.io instance!"

***

## Application's creation

!!! info "Initialization of the application to get Wordpress on your instance"

    During this step, we are going to initialize an application allowing us to install Wordpress on your Ubuntu 16.04 Amazon Lightsail's instance.

[![Material for MkDocs](assets/images/aws/run-cloud/en/6.gif)](assets/images/aws/run-cloud/en/6.gif)

***

**Come back to Runcloud.io, you should now have access to your dashboard**

:    * In the left menu, click on {==*Web Application*==}.
:    * Click on {==*Create Application*==}.
:    * Name your application with the name of your future website.
:    * Add the domain name that you use for your instance.
:    * Choose the User by default *Runcloud*.
:    * Leave the by default Public Path.
:    * Select the most recent PHP version.
:    * Select *NGINX + Apache2 Hybrid (You will be able to use .htaccess)*.
:    * Choose the *Production* mode.
:    * Let the *Advanced Settings* box unchecked, so you can keep the by default settings.
:    * Click on {==*Add Web Application*==}.

!!! success "An "application" space is now available on your Lightsail instance."

***

## Configurations

[![Material for MkDocs](assets/images/aws/run-cloud/en/7.gif)](assets/images/aws/run-cloud/en/7.gif)

***

**Wordpress installation**

:    * On the left menu, click on {==*Script Installer*==}.
:    * Select the *Wordpress* script to install.
:    * Click on {==*Install*==}.

!!! success "Wordpress is now installed like a primary application on your Lightsail instance."

***

[![Material for MkDocs](assets/images/aws/run-cloud/en/8.gif)](assets/images/aws/run-cloud/en/8.gif)

***

**Domain name configuration**

:    * In the left menu, click on {==*Domain Name*==}.
:    * Add your domain name `www.exemple.com` to the existing list.
:    * Click on {==*Attach Domain Name*==}.

!!! success "The domain name configuration now works for Wordpress."

***

[![Material for MkDocs](assets/images/aws/run-cloud/en/9.gif)](assets/images/aws/run-cloud/en/9.gif)

***

**Creation of the security certificate**

:    * In the left menu, click on {==*SSL/TLS*==}.
:    * Check the box *Enable HSTS*.
:    * Select *Let's Encrypt* as an SSL method.
:    * Select *Http-01*.
:    * Select *Live* as an environment.
:    * Click on {==*Submit*==}.

!!! success "Your security certificate is now approved for your domain name."

***

[![Material for MkDocs](assets/images/aws/run-cloud/en/9b.gif)](assets/images/aws/run-cloud/en/9b.gif)

***

**By default application**

:    * At the top right, click on {==*More*==}.
:    * Click on *Set as default Web Application*.
:    * Go back to the homepage by clicking on *Back to Web Apps* in the left menu.

***

## Database

!!! info "Database and user"

    To work, your app (Wordpress) needs a database where your website and your user's information will be stocked.

[![Material for MkDocs](assets/images/aws/run-cloud/en/10.gif)](assets/images/aws/run-cloud/en/10.gif)

***

**Database creation**

:    * In the left menu, click on {==*Database*==}.
:    * Click on *Create Database*.
:    * Name your database as you wish.
:    * Leave the field *Collation* empty by default.
:    * Click on {==*Add Database*==}.

!!! success "The database is now available for Wordpress."

***

[![Material for MkDocs](assets/images/aws/run-cloud/en/10b.gif)](assets/images/aws/run-cloud/en/10b.gif)

***

**Admin account creation**

!!! warning "Wordpress logins"
    
    To access the Wordpress dashboard, you need an admin account that will have all the rights on your website. For this step, we will create the logins for this account and you must keep it in a secure place/file.

:    * Click on *Create Database User*.
:    * In *Database User*, create your login and keep it.
:    * Generate a password and copy/paste it in a secure file with your login.
:    * Click on *Add Database User*.

!!! success "Your admin account has been created."

***

[![Material for MkDocs](assets/images/aws/run-cloud/en/10c.gif)](assets/images/aws/run-cloud/en/10c.gif)

***

**Linking the admin account to your database**

:    * Click on the green button *Attach User*.
:    * Select your username in the drop-down list.
:    * Click on *Attach User*.

!!! success "Your admin account is now linked to your database."

***

## Wordpress acces

[![Material for MkDocs](assets/images/aws/run-cloud/en/11.gif)](assets/images/aws/run-cloud/en/11.gif)

***

**Wordpress initialization**

!!! info "Access to your website" 
    You can now access your website! Type your domain name `https://example.com` on the URL search bar of your browser. You will then have access to the Wordpress installation page.

:    * Select your language.
:    * Click on the {==*Let's go!*==} button.
:    * Name your database.
:    * Copy/paste the Runcloud.io database name (voir étape Création du compte administrateur ANCRE).
:    * Copy/paste the Runcloud.io database password (voir étape Création du compte administrateur).
:    * Leave the "by default" *Database Host* to `Localhost`.
:    * Change your prefix with something else than `wp_`, but keep the same format.
:    * Click on {==*Submit*==}.

***

[![Material for MkDocs](assets/images/aws/run-cloud/en/12.gif)](assets/images/aws/run-cloud/en/12.gif)

***

**Website and admin statuts configurations**

!!! info "Save your login!" 
    You are going to create admin access to your Wordpress website. You must keep your login/password combination in a secure place!

:    * Give your website a title.
:    * Chose a login and save it somewhere.
:    * Generate a password and save it somewhere.
:    * Add your e-mail address.
:    * Leave the *Search Engine Visibility* box unchecked.
:    * Click on {==*Install Wordpress*==}.
:    * You can now {==*Log In*==} to your Wordpress.

!!! success "You now have access to your Wordpress interface."

***

## Htaccess settings

[![Material for MkDocs](assets/images/aws/run-cloud/en/13.gif)](assets/images/aws/run-cloud/en/13.gif)

!!! info "Traffic redirection" 
    The Htaccess file allows you to determine the traffic redirection rules for your website. With this step, any user trying to access the static IP of your Lightsail instance will be redirected to your secure domain name.

***

**Htaccess file changes**

:    * In the left menu of your Runcloud.io interface, click on {==*Web Application*==}.
:    * Then, click on your application name.
:    * On the left menu, click on {==*File Manager*==}.
:    * Select the `.htaccess` file and click on *View/Edit*.
:    * Once on the editor, copy/past the re-writing rule below:
``` yaml
RewriteCond %{HTTP_HOST} ^111\.111\.111\.111
RewriteRule (.*) https://yoursite.com/$1 [R=301,L]
```

***

[![Material for MkDocs](assets/images/aws/run-cloud/en/13b.gif)](assets/images/aws/run-cloud/en/13b.gif)

***

**The URL re-writing command editing**

:    * On your Lightsail interface, copy the static IP address of your instance.
:    * Paste the static IP in the Htaccess file so you can see it during this step.
:    * Then, edit the "re-writing rule" you copied/pasted on the last step, with your static IP and domain name. Has the example below:
``` yaml
RewriteCond %{HTTP_HOST} ^35\.180\.184\.49
RewriteRule (.*) https://yoursite.com/$1 [R=301,L]
```

:    * Once this step is done, erase the static IP and the spaces you created, to make everything more readable.
:    * Click on Save at the top of the windows or hit <kbd>Ctrl</kbd> + <kbd>S</kbd> to save your changes.

!!! success "Congratulations! Wordpress is now correctly installed and set to support your website creation."

***
