=================
django-smartmenus
=================

A Django app that provides template tags to easily incorporate smartmenus (http://www.smartmenus.org/).

Installation
============

To get started using ``django-smartmenus``:

- install it with ``pip``::

    $ pip install django-smartmenus

- add the app to ``INSTALLED_APPS``. If you are using Django CMS, make sure it's before ``menus``::

    INSTALLED_APPS = (
        ...
        'django_smartmenus',
        'menus', #Only if you are using Django CMS
        ...
    )

Usage
=====

The best way to see how it works is exploring the example project. But for the impatient, all you need to do is:

- load smartmenus tags in the templates::

	{% load smartmenus_tags %}


- Call smartmenus template tags where css and js files should show::

	{% smartmenus_css theme %}
	<script src="path/to/jquery"></script>
	{% smartmenus_js %}

  ``theme`` is a string based parameter. Out of box, ``theme`` can be one of 'sm-blue', 'sm-clean', 'sm-mint' and 'sm-simple'. If you create a custom theme of your own, please put the theme file under static folder following smartmenus theme folder structure convention, ie. smartmenus/css/``theme``/``theme``.css.


- Render menu html in the templates. Please refer to smartmenus tutorial to see what the html should be.


This app also supports Django CMS:

- load smartmenus and menu tags in the templates::

	{% load menu_tags smartmenus_tags %}


- Call Django CMS specific template tags anywhere in the templates::

	{% addtoblock "js" %}<script src="path/to/jquery"></script>{% endaddtoblock %}
	{% smartmenu_bootstrap_cms theme %}

  ``theme``'s usage is the same as above.


- Render Django CMS menu::

	<ul class="sm theme-class-name">
	    {% show_menu 0 100 100 100 %}
	</ul>

  ``theme-class-name`` is a string based parameter. Please refer to smartmenus doc regarding possible values. Usually it's the same as theme name unless it's a custom theme with different naming conventions.