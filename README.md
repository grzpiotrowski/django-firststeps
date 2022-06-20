# Django Tutorial App
This is my learn Django project.
Following a tutorial from sentdex YouTube channel:
[Django Web Development with Python](https://www.youtube.com/playlist?list=PLQVvvaa0QuDe9nqlirjacLkBYdgc2inh3).
Also a text based version to be found at:
[pythonprogramming.net](https://pythonprogramming.net/django-web-development-python-tutorial/)


## Issues
The tutorial was uploaded back in 2019 and was using Django 2.1.5.
Since then there was many new versions of Django released.
This project uses Django 4.0.5.
This section highlights any differences that arise due to changes in Django or any other module.

### Admin and Apps
#### Adding TinyMCE to Admin panel
When adding TinyMCE config to main/settings.py:
> ImportError: cannot import name 'smart_text' from 'django.utils.encoding' (...\lib\site-packages\django\utils\encoding.py)

Fixed by adding these imports to mysite/settings.py:\
`import django`\
`from django.utils.encoding import smart_str`\
`django.utils.encoding.smart_text = smart_str`

#### TinyMCE 1.8.0 internal imports
Due to changes in Django an error occurs in TinyMCE package
>File "...\lib\site-packages\tinymce\urls.py", line 1, in &lt;module&gt;<br>
>from django.conf.urls import url<br>
>ImportError: cannot import name 'url' from 'django.conf.urls' (...\lib\site-packages\django\conf\urls\__init__.py)

The solution is to replace this import in tinymce/urls.py:\
`from django.conf.urls import url`\
with:\
`from django.urls import re_path as url`