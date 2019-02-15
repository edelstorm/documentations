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

