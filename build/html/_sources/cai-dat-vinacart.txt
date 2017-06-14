==========================
Vinacart Installation
==========================

Download Vinacart: http://www.vinacart.net/p/download.html

Server Configuration
--------------------
**Apache**: Required modules & extension as bellow:

PHP version 5.6+

- *Module*: mod_rewrite
- *Extension*: 
	- mysql|mysqli|pdo_mysql : Original MySQL API
	- gd : a graphics library used to manipulate images
	- curl : client for URL handling used by GPM
	- zlib : read and write gzip (.gz) compressed files
	- mbstring : multibyte encoding
	- mcrypt : mcrypt library
	- pcntl : Process Control support signal handling and process termination
	- openssl : encrypting & decrypting data

..
	- ioncube : download ioncube loader from URL https://www.ioncube.com/loaders.php

Note: LiteSpeed Web Server not support.


Install
-------

1. Prepare Domain.

If run on localhost, you using xampp, wamp.. you need to create an alias (ie: ``vinacart.dev``) instead of using default hostname ``localhost``. Example:
Edit file `c:/xampp/conf/extra/httpd-vhosts.conf`

::

	<VirtualHost *:80>
	    ServerName vinacart.dev
	    ServerAlias www.vinacart.dev
	    DocumentRoot "C:\xampp\htdocs\vinacart"
	    <Directory "C:\xampp\htdocs\vinacart">
	        Order allow,deny
	        Allow from all
	    </Directory>
		ErrorLog C:\xampp\htdocs\error.txt
	</VirtualHost>

2. Create database.

3. Set Files permission.

For Window users, this step is no need. 
For Linux users, to chmod all files we just run *caidat.php* on your browser:
``http://vinacart.dev/caidat.php``

4. Install.

Open your browser, visit the page: ``http://vinacart.dev/install/``
Follow the sequence of steps (wizard). Fill in the full information and then click install, wait a few minutes for the installer to finish.


Note: If you want to reinstall vinacart, use the following URL: ``http://vinacart.dev/install/?rt=install&force=1``

**Using prefix www**

If you want to use the www prefix, and redirect the URL to this subdomain after the installation is complete, visit the admin page to modify the store path. Ex: http://www.example.com

*Note*: You need to clear the cache and disable the cache if the URL does not work correctly. If the URL is already worked, you can enable the cache again.

At this point the admin still works with the old URL (without www), however, so that the storefront and admin automatically redirect to www when the user types your domain does not contain www. You add the following to the .htaccess file

::

	..
	RewriteRule ^(.*)\?*$ index.php?_route_=$1 [L,QSA]

	# if want to redirect non-www to www
	RewriteCond %{HTTP_HOST} !^www\. [NC]
	RewriteRule ^(.*)$ http://www.%{HTTP_HOST}/$1 [L,QSA]
	..

If you create multiple stores with the same domain, (eg, store2.example.com), list them in the black list so that www is properly redirected.

::

	RewriteCond %{HTTP_HOST} !^www\. [NC]
	RewriteCond %{HTTP_HOST} !^store2\. [NC]
	RewriteRule ^(.*)$ http://www.%{HTTP_HOST}/$1 [L,QSA]
