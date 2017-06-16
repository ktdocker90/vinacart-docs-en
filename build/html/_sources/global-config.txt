==============
General
==============

Credential
==========

Use external services, like sending mail.
These credentials are listed in the ``system/config/credentials.php`` file

::

	<?php
	return array(
	    'sendgrid' => array(
	        array(
	            'username'=> 'user1',
	            'password' => 'pass1',
	            'email'=> 'kythuat.hoangweb@gmail.com',
	            'apiKey'=> 'sdfnsdkfr3434fsf',
	        ),
	        array(
	            'username' => 'user2',
	            'password' => 'pass2',
	            'email' => 'laptrinhweb123@gmail.com',
	            'apiKey' => 'sdfsd32y423y432y9erkedfdf'
	        )
	    ),
	    'mailgun' => array(
	        array(

	        )
	    )
	);

.. Chúng tôi bảo trì cập nhật các tài khoản để đảm bảo các website hoạt động tốt, dùng chung các tài khoản đó. 
To update credentials you should edit ``credentials.php``. After that clear cache.
