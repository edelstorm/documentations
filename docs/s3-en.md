# S3 <small>- AWS</small>

## S3 bucket

!!! info "S3"

    S3 is a service that enables users to load your website’s media faster.

[![Material for MkDocs](assets/images/aws/s3/en/1.gif)](assets/images/aws/s3/en/1.gif)

***

**Go to the AWS Management Console (AWS homepage).**

:    * Search for {==S3==} and click on the result.
:    * Now that you are in the S3 interface, click on {==Create bucket==}.
:    * Name your bucket and choose the same region that you choose for your Lightsail instance.
:    * Click on {==Next==}.
:    * Leave the option by default and click on {==Next==}.
:    * Uncheck all the boxes so your bucket becomes public.
:    * Click on {==Next==}.
:    * Check that everything is good and click on {==Create bucket==}.

!!! success "An S3 public bucket is now available! It will enable faster loading of your media on Wordpress."

***

[![Material for MkDocs](assets/images/aws/s3/en/2.gif)](assets/images/aws/s3/en/2.gif)

***

**S3 bucket permissions**

:    * Click on your S3 bucket, then click on {==Permissions==}.
:    * Click on {==Bucket Policy==}.
:    * Copy / paste the following policy on the editor : 
``` sh
{
 "Version": "2008-10-17",
 "Statement": [
 {
  "Sid": "AllowPublicRead",
  "Effect": "Allow",
  "Principal": {
   "AWS": "*"
  },
  "Action": "s3:GetObject",
  "Resource": "arn:aws:s3:::YourBucketName/*"
 }
 ]
}
```

!!! warning "Don't forget to switch *YourBucketName* with the name you gave your bucket."
:    * Once the policy edited, click on {==Save==}.

## IAM policy

***

[![Material for MkDocs](assets/images/aws/s3/en/3.gif)](assets/images/aws/en/3.gif)

***

**IAM policy initialization**

:    * Go back to the AWS Management Console by clicking on the top left logo.
:    * Search for the IAM service and click on the result.
:    * In the left menu, click on {==Users==}.
:    * Click on {==Add user==}.
:    * Choose a name for your user.
:    * Check the box *Programmatic access*.
:    * Click on {==Next: Permissions==}.
:    * Click on {==Attach existing policies==}.
:    * Click on {==Create policy==}.

***

[![Material for MkDocs](assets/images/aws/s3/en/4.gif)](assets/images/aws/s3/en/4.gif)

***

**IAM policy creation**

:    * To access the online editor, click on the JSON menu.
:    * Once in the editor, delete the existing content and copy / paste the IAM policy below:
``` sh
{
 "Version": "2012-10-17",
 "Statement": [
 {
  "Effect": "Allow",
  "Action": [
   "s3:CreateBucket",
   "s3:DeleteObject",
   "s3:Put*",
   "s3:Get*",
   "s3:List*"
  ],
  "Resource": [
   "arn:aws:s3:::YourBucketName",
   "arn:aws:s3:::YourBucketName/*"
  ]
 }
 ]
}
```

!!! warning "Don't forget to the two *YourBucketName* by the name you chose for your bucket."
:    * Click on {==Review policy==}.
:    * Name the policy.
:    * Click on {==Create policy==}.

***

!!! success "The IAM policy is now ready to be used for your future IAM user."

***

## IAM User

[![Material for MkDocs](assets/images/aws/s3/en/5.gif)](assets/images/aws/s3/en/5.gif)

***

**IAM policy and user linking**

:    * In the left menu, click on {==Users==}.
:    * Click on {==Add user==}.
:    * Choose a name for your IAM user.
:    * Check the *Programmatic access* box.
:    * Click on {==Next: Permissions==}.
:    * Click on {==Attach existing policies==}.
:    * Type your IAM policy name in the search bar.
:    * Check your IAM policy box and click on {==Next: Tags==}.
:    * Click on {==Next: Review==}.
:    * Click on {==Create user==}.
:    * To keep your access in a separate file, click on {==Download .csv==}.
:    * Keep this window open for the next step.

!!! warning "Don't forget to copy/paste and save your Access key ID and Secret access key in a secure place."

!!! success "Congratulations! Your IAM user is now liked to the right IAM policy and you have the two access keys."

***

## Wp-config.php edition

[![Material for MkDocs](assets/images/aws/s3/en/6a.gif)](assets/images/aws/s3/en/6a.gif)

***

**Go to your Runcloud.io homepage**

:    * Go to *Web Applications* and click on your application Wordpress.
:    * Click on {==File Manager==} in the left menu.
:    * Select the *wp-config.php* file, then click on the *View/Edit menu.

***

[![Material for MkDocs](assets/images/aws/s3/en/6b.gif)](assets/images/aws/s3/en/6b.gif)

***

**Command injection**

:    * Once in the editor, copy/paste the command below after `define('WP_DEBUG', false);` : 
``` sh
define( 'AS3CF_SETTINGS', serialize( array(
    'provider' => 'aws',
    'access-key-id' => 'YourAccessKeyID',
    'secret-access-key' => 'YourAccessKeySecret',
) ) );
```
:    * Then go to your IAM interface so you can replace *YourAccessKeyID* with your access key ID and *YourAccessKeySecret* with your secret access key.

:    * Type <kbd>Ctrl</kbd> + <kbd>S</kbd> to save your changes.

!!! warning "Replace *YourAccessKeyID* and *YourAccessKeySecret* with the keys from the last IAM step."

***

## WP Offload Media

[![Material for MkDocs](assets/images/aws/s3/en/7.gif)](assets/images/aws/s3/en/7.gif)

***

**Come back to the Wordpress homepage**

:    * Click on {==Plugin > Add New==} on the left menu.
:    * Type *Amazon S3* on the search bar.
:    * Install and activate the *WP Offload Media Lite for Amazon S3* plugin.

***

[![Material for MkDocs](assets/images/aws/s3/en/7a.gif)](assets/images/aws/s3/en/7a.gif)

***

**Delete the unnecessary applications and configure your WP Offload Media plugin**

:    * In the *Extensions installées* menu, delete the by default applications.
:    * In the plugins menu, click on *Settings*.
:    * Once there, put your S3 bucket in the field and click on *Save Bucket Setting*.

***

[![Material for MkDocs](assets/images/aws/s3/en/8.gif)](assets/images/aws/s3/en/8.gif)

**Plugin settings**

:    * Then activate *Force HTTPS*.
:    * Click on *Save changes*.

!!! success "Congratulations, you have correctly set Amazon S3 for your Wordpress website!"

***