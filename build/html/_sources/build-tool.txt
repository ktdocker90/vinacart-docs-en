===========================
Build theme automation tool
===========================

This is a software that automatically generates tpl from HTML. You buy a html template for ecommerce, then extract each portion of html that represent widget, layout.. to separate html files before import to tpl builder.

Convention/Glossary
===================
Blocks & Pages are designed into separate HTML files, which are structured differently depending on your html template. In that some blocks / pages that use the same HTML structure as tabs, ul lists, .. will be inherited and automatically created without having to redesign the HTML for them.

- block/page both called block.
- module: These are the HTML elements for re-usable.

Build Form
==========

- Theme: select theme to work with.
- web data: sample data for theme.

You can build single block / page / .. or build all them with whole theme by ** Build ** button. To build each component one by one, click on the "Build Option" option, which will allow you to select the blocks / pages you want to build, for example, if you have some revisions and just want to build them.

To build all over again, choose Build All.

Press Build to get started.

To delete all the theme data click the Delete button.

theme.xml
=========
This is the configuration file for the theme. This file define assets (.css, .js) , block configuration and other configurations such as images, which will be automatically updated by clicking on the `` Update theme.xml`` button.

Once this file is created, the modules that are used for creating `` theme.xml`` will be marked as built, which will metion bellow in the Themes list.

Global/Menu
===========

CSS class/id
^^^^^^^^^^^^^^^^^
Shortcode content is filled in HTML to replace the html class when building .tpl files. This page lists the classes that can be used. You fill in the fields according to your HTML design.

Example: shortcode 'class:form_wrapper' used to fill form class, look like this:
..
	<form class="class1 [class:form_wrapper] class2"></form>

Common HTML Template
^^^^^^^^^^^^^^^^^^^^
Common HTML elements in block / page, such as buttons, messages, tabs, form input ..
Enter the HTML into the editor, and hit the Save button.


Blocks module
^^^^^^^^^^^^^^^^^
This section sets up a module HTML for blocks, for which blocks that use modules (mean, blocks that do not have their own HTML  but for sharing HTML components in page/block, called modules).

A module can create multiple html template for single module with different HTML structure for that module. It's name with the same file as the module name and other files with the `` -n`` suffix.
Eg:
The tabs module has: tabs.html (main interface), tabs-1.html, tabs-2.html, ..

Example: If two blocks use the same module, they have different HTML content. On this page select the desired HTML file for the module to use for each block.

Note: One block extend one module.

Blocks setting
^^^^^^^^^^^^^^
This section allows you to generate additional block, during .tpl build process. Eg for blocks with advanced options like menu, if you want to edit HTML elements like dropdown tags, class ..

Settings saved with current theme at directory html_saved/<theme>

Blocks Advanced
^^^^^^^^^^^^^^^
This is the advanced, customizable settings for blocks.

- **Feature 1: Apply HTML**:
- Each block can build multiple tpl with different html input. To do this you add the block that you want to build extra tpl, select the HTML file and the name of the exported tpl file. Then save. In the Form section, check on `Build Option` and click Build> select the block you want to build> Ok.

Themes List
^^^^^^^^^^^
Statistics data of themes created in the system. Each theme show the state of the blocks (blue icon: block has been modified but not build, gray: block has been built).

Press Delete to delete the theme data from the database.
Click Reset to mark all blocks that mean they need to be rebuilt.


Template
========
This panel lists the .tpl files that have been automatically generated. Click the file or right mouse button & select `` edit`` to edit the content. To delete, click the `` Delete`` on context menu.


Inspect HTML
============
Phần này liệt kê những file html được tạo. Để thêm file có 2 cách :

- Sử dụng công cụ inspect (beta) để khoanh vùng block và các thành phần chi tiết của block. Sau khi đã đánh dấu đầy đủ, chuột phải tại vùng block có mầu đỏ chọn edit & nhấn Export Block. File HTML của block đó sẽ được lưu lại vào thư mục ``html_saved/<theme>``. 
Tại đó Bạn cũng xem trước nội dung tpl đã sinh ra để kiểm tra bạn đã đánh dấu đúng thành phần của block hay không.

- Soạn trực tiếp nội dung HTML của block: cách này nhanh gọn & chính xác hơn. Để thêm file nhấn nút ``+`` bên cạnh panel, hộp thoại xuất hiện chọn file và nhấn nút Ok.

Chú ý: bạn có thể thêm 1 hoặc nhiều file cùng lúc, chuột phải tại tab đã mở, có 4 lựa chọn: close, close All, Save & Save all.

Bạn sẽ thây nội dung mẫu của block trong cửa sổ soạn thảo. Những thành phần của block được highlight mẫu xanh, cho biết vị trí của chúng đặt trong thuộc tính class trong nội dung HTML.

Tên class có tiền tố ``__vnc-`` sau đó là tên thành phần. Trong đó có tên class chính bao toàn bộ nội dung block, có dạng: ``__vnc-block-<block_name>``
Chú ý: không được thiếu class này.

Để chèn class đánh dấu, chọn combobox trên thanh toolbar. Build block ra file .tpl nhấn nút play bên cạnh. FIle .tpl được lưu tại thư mục ``template/<theme>``


HTML Pages
==========
This panel show the HTML files from input original, click to view and use the inspect tool. The inspect feature extracts the HTML file for each block.


Export
======
You can export tpl or full theme.


Upload HTML
===========
This page allows you to upload a zip file containing the .html file of the original HTML template or parsed html files (if you have one).
Note: zip contains directly html files not located in the root directory.