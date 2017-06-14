========================================== 
Cấu trúc theme
==========================================

Theme được viết dưới dạng extension, cấu trúc của một theme giống với
cấu trúc 1 extension gồm có:

-  admin/ - cấu trúc MVC sử lý phần backend.
    -  controller/ - chứa files php (controllers)
    -  model/ - chứa files php (models)
    -  view/ - files .tpl hiển thị dữ liệu
    -  language/ - files .xml chứa ngôn ngữ dịch.
-  core/ - chứa hooks.
-  storefront/ - cấu trúc MVC sử lý ở frontend (website)
    - Cấu trúc tương tự ``admin/``
    - language/ - chứa ngôn ngữ dịch.
        - english/
        - vietnamese/
    - view
        - ``<theme_name>``/ - chú ý cần trùng với tên thư mục theme. Bạn sẽ làm việc với thư mục này để thiết kế template.

- data/ - chứa dữ liệu mẫu của theme (sử dụng trong quá trình cài đặt).
    - blocks.xml - lưu toàn bộ khai báo blocks.
    - layout.xml - lưu layout & pages.
    - datasets.xml - lưu cấu hình blocks.

- image/
    - icon.png - icon của theme.
    - chứa các ảnh khác.

-  config.xml - thông tin theme
-  install.php - code sử lý khi cài đặt theme.
-  install.sql - import sql data khi cài đặt theme.
-  uninstall.php - code sử lý khi hủy cài đặt theme.
-  uninstall.sql - chạy lệnh sql khi hủy cài đặt theme.
-  main.php - Khai báo các files php, .tpl có sử dụng
-  icon.png - ảnh đại diện của theme.
-  theme.xml - thông tin cơ bản về theme.


Xem extension ``mytheme`` (extensions/mytheme) để tham khảo cách viết một theme mẫu.

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

Bạn sửa các thông tin sau đây:

-  ``id`` - id của theme là tên thư mục của theme (viết liền không chứa dấu cách).
-  ``version`` - phiên bản theme
-  ``preview`` - thêm ảnh đại diện cho theme. Ảnh nằm trong thư mục image/


Các thông số khác dữ nguyên. VD:

- ``type`` - kiểu *template*
- ``category`` - nằm trong danh mục *template*.

main.php
^^^^^^^^

Tại đây bạn khai báo toàn bộ các files *.php, *.tpl thuộc controller, model, template & language. Mỗi biến có 2 phần ``storefront`` & ``admin`` dành cho admin và frontend.

.. code-block:: php

    //quy định template không viết hành động
   $controllers = array( 
      'storefront' => array(), 
      'admin' => array()
    );

    //quy định template không viết model
   $models = array( 'storefront' => array(), 'admin' => array());

   $templates = array( 
    'storefront' => array(
        'blocks/account.tpl',
        'blocks/bestseller.tpl',
        ..
   ), 
    'admin' => array(
      //quy định template thì không viết cho admin
   ) );

Chú ý: tạo thêm file (php, tpl) khác phải khai báo đầy đủ vào đây.

theme.xml
^^^^^^^^^

::

    <theme>
        <name><![CDATA[MyTheme]]></name><!-- title -->
        <description><![CDATA[Theme description]]></description>
        <version>1.0</version>
        <screenshot>screenshot.jpg</screenshot><!-- image/icon.png -->
    </theme>

Phần nội dung này được hiển thị trên themes stores của chúng tôi, một khi theme được public lên server. Bạn khai báo tên, mô tả,
version và hình xem trước. Xem tiếp `Thiết lập file cấu hình cho theme <theme-config.html>`_
