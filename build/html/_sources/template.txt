========
Template
========


Biến sử dụng trong template
===========================

Biến toàn cục: ``$vnc`` truy cập ở mọi template (.tpl).

.. code-block:: php

	{% if vnc %}
	      {% if vnc.getVar('product') %} 
	      	<h3>{{ vnc.getVar('product').name }}</h3>
	      
	      {% elseif vnc.getVar('category') %}
	        <h3>{{ vnc.getVar('category').name }}</h3>
	        <p>{{ vnc.getVar('category').description }}</p>
	      
	      {% elseif vnc.getVar('blog_category') %}
          <h1>{{ vnc.getVar('blog_category').name }}</h1>
          <p>{{ vnc.getVar('blog_category').description }}</p>
        
        {% elseif vnc.getVar('blog_entry') %}
          <h1>{{ vnc.getVar('blog_entry').entry_title }}</h1>

        {# elseif vnc.getVar('blog_author') %}  
          <h1>{{ vnc.getVar('blog_author') }}</h1>
          #}

	      {% elseif vnc.getVar('heading_title') %} 
	      	<h3>{{vnc.getVar('heading_title') }}</h3>
	      
	      {% else %}
	      	<h3>Empty</h3>
	      {% endif %}
	{% endif %}

Lấy nội dung bất kỳ block nào trong page.tpl (ngoại trừ parent block (column_left, ..))

.. code-block:: php

	//parent block, child block index: deprecated
	{# vnc._view.loadBlock('header_bottom', 0) #}

	{{ registry.get('_view').loadBlock('footer_top', 1) }}

	#or short form using
	{{ loadBlock('header_bottom', 0) }}

	//get variable data from any block/page. note: make sure this block already loaded
	{{ blockVar('blocks/bestseller','var1') }}
	{% set categories = blockVar('pages/product/category', 'categories') %}
	//or
	{{ registry.get('_view').blockVar(..) }}

	//for block
	blockVar('blocks/bestseller', 'products')

**Template tag**

common template tag:

::
	
	{% if is_admin() %}
	is_home()
	is_category()
	is_single_product()
	is_manufacturer()
	is_generic_pages()
	is_search()
	is_ajax()
	is_page('content/contact')

**Model**

Truy cập model.

::

	getModel('catalog/product').getProduct('<ID>')

**Components**.

Ngoài các blocks có sẵn trong layout, chúng tôi cho phép nạp một số block mà không cần thêm vào layout. Thành phần hiển thị như comment,..

::

	{{ loadView('comment') }}
	{{ loadView('social_button') }}

**Form Field**.

::

	{% set btn = review_button.vnc_getProperty('data') %}
	<button class="button submit" title="{{ btn.title? btn.title : btn.text }}" type="submit">{{ btn.text }}</button>

	# other way
	<button class="button submit" title="{{ fieldValue(review_button,'title','text') }}" type="submit">{{ fieldValue(review_button,'text') }}</button>

**Debuging**:

::

	//buitin function help you print value of any variable
	{{ _print(..) }}
	{{ _debug_backtrace(debug_backtrace()) }}

**URL**:

::

	{{ html.getSEOURL('account/wishlist') }}
	{{ html.getURL('account/wishlist') }}
	{{ html.getSecureURL('account/wishlist') }}
	{{ html.getHomeURL() }}

**Customer**:

::

	//wishlist count
	{{ customer.getWishList()|length }}


..	Xuất bản template
	=================

	Mỗi một site tạo ra sẽ sử dụng một template riêng (ie, ``mytheme``) bên cạnh template mặc định (``default``) của hệ thống.
	Template mới sử dụng trong App sẽ có ID phân biệt, để xuất bản theme lên store. 
	Lưu ý: Một site có thể cài đặt nhiều template nhưng chỉ kích hoạt sử dụng một template.

	ID này được sinh ra khi site được tạo hoàn tất. Để publish theme bạn cần kiểm tra xem ID của theme được tạo ra hay chưa, nếu chưa báo lỗi với admin.

	Publish template
	----------------

	Để publish theme, bạn cần kích hoạt lại template đang push lên store (không phải default theme hoặc nếu trường hợp site có cài nhiều template). TH xóa theme bạn cũng pải cần kích hoạt lại theme ở backend site, để thiết lập lại theme muốn publish lên store.

	*Chú ý*: Nếu không làm đúng quy trình sẽ phát sinh lỗi trong quá trình publish template.

	Unpublish template
	------------------

	Sau khi publish theme thành công hay một khi theme đã được xuất bản, bạn có thể gỡ bỏ ra khỏi store. Để thực hiện truy cập trang app, ở tab **Settings** mục **Publish Theme** nhấn vào **Delete from store** từ dropdown.

**User**

::

	//current user
	{{ current_user() }}

**Utils functions**

String:

::

	//replace string at first found
	str_replace_first($find, $replace, $object)

Config:

::

	config.get('store_main_email')
	{{ config.get('livechat_embed') }}