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


