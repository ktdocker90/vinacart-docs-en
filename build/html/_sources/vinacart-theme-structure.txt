========================================== 
Theme Development
==========================================

Theme is written in the form of an extension, the structure of a theme similar to
an standard extension structure, consists of:

-  admin/ - MVC for backend.
    -  controller/ - contain controllers php files
    -  model/ - contain models php files
    -  view/ - contain .tpl files to display data
    -  language/ - language definition (.xml).
-  core/
-  storefront/ - MVC for frontend (website)
    - similar to ``admin/``
    - language/ - language definition.
        - english/
    - view
        - ``<theme_name>``/ - need to match the name of the theme folder. You will work with this directory to design the template.

- data/ - Contains sample template data (used during installation).
    - blocks.xml - blocks data.
    - layout.xml - save layout & pages.
    - datasets.xml - blocks configuration.

- image/
    - icon.png - theme icon.

-  config.xml - extension configuration
-  install.php - run during installation.
-  install.sql - run during installation.
-  uninstall.php - run during uninstall.
-  uninstall.sql - run during uninstall.
-  main.php - declare all files used in extension
-  icon.png - extension icon.
-  theme.xml - theme information.


config.xml
^^^^^^^^^^

::

    <?xml version="1.0" encoding="UTF-8"?>
    <extension>
      <id>mytheme</id>
      <version>1.0.0</version>
      <type>template</type>
      <category>template</category>
      <cartversions>
        <item>1.2</item>
      </cartversions>
      <priority>0</priority>
      <dependencies>
          <item >vinacart</item>
      </dependencies>
      <settings>
        <item id="mytheme_status">
          <type>checkbox</type>
          <default_value>0</default_value>
        </item>
        <item id="mytheme_slogan">
            <type>textarea</type>
            <default_value></default_value>
        </item>
      </settings>

      <additional_settings><![CDATA[setting/setting&active=appearance]]></additional_settings>
      <preview>
          <item>preview.jpg</item>
          <item>preview1.jpg</item>
          <item>preview2.jpg</item>
          ...
      </preview>
      <install>
        <sql>install.sql</sql>
        <trigger>install.php</trigger>
      </install>
      <uninstall>
        <sql>uninstall.sql</sql>
        <trigger>uninstall.php</trigger>
      </uninstall>
    </extension>

You correct the following information:

-  ``id`` - extension id (refer to theme directory).
-  ``version`` - extension version.
-  ``preview`` - theme preview. List images in directory image/


Do not modify other info such as:

- ``type`` - *template*
- ``category`` - extension category. *template*.

main.php
^^^^^^^^

Here you declare all the files *.php, *.tpl for controller, model, template & language.

.. code-block:: php

    //extension theme should no write controller
   $controllers = array( 
      'storefront' => array(), 
      'admin' => array()
    );

   $models = array( 'storefront' => array(), 'admin' => array());

   $templates = array( 
    'storefront' => array(
        'blocks/account.tpl',
        'blocks/bestseller.tpl',
        ..
   ), 
    'admin' => array(
      //template not for admin
   ) );

Notice: Create another file (php, tpl) must be fully declared here.

theme.xml
^^^^^^^^^

::

    <theme>
        <name><![CDATA[MyTheme]]></name><!-- title -->
        <description><![CDATA[Theme description]]></description>
        <version>1.0</version>
        <screenshot>screenshot.jpg</screenshot><!-- image/icon.png -->
    </theme>

