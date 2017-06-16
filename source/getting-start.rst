=====================================
Getting start
=====================================

Suppose that you download a theme called ``mytheme`` from abantecart marketplace (for VNC Theme framework). Create a new theme named (eg: theme1) by duplicating **mytheme/**.

Rename file and folder
======================

Note that after copying the theme, you need to rename the folder and file to match the new theme (theme1). Convert ``mytheme`` to ``theme1`` with the following files and folders:

- admin/language/english/mytheme/
- admin/language/english/mytheme/mytheme.xml

- storefront/language/english/mytheme
- storefront/view/mytheme

Edit content
============
Find & rename ``mytheme`` to ``theme1`` in the found files.

Find & rename ``mytheme`` to ``theme1`` in the file config.xml and main.php

.. 	
	comment
	File cài đặt
	^^^^^^^^^^^^
	Tương tự cho file uninstall.sql

Language
^^^^^^^^
- admin/language/english/theme1/theme1.xml

Use language files for both admin & frontend.
::

	<?xml version="1.0" encoding="UTF-8"?>
	<definitions>
	    <definition>
	        <key>theme1_name</key><!-- mytheme -> theme1 -->
	        <value><![CDATA[my theme]]></value>
	    </definition>
	    ...

core/ThemeExtension.php
^^^^^^^^^^^^^^^^^^^^^^^
This is entry file when the theme is loaded. In the file define class named ``Extension <theme_name>``.
ex: mytheme -> ExtensionMytheme, theme1 -> ExtensionTheme1

Edit the class name that matches your theme name.

Ok, you are done, next we will focus on writing template for the theme.