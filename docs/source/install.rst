
Instalação
==========

Caso esteja utilizando um sistema GNU-Linux será necessário instalar previamente pacotes de desenvolvimento como gcc, make e outros (o pacote build-essential no Debian e Ubuntu) além do python-dev.

Compatível com **Django 1.8**

1. Instale o ACE com o comando a seguir::

    pip install django-sysace




2. Adicione **django.contrib.admin**, **ace** e os outros apps necessários à seção **INSTALLED_APPS** do arquivos **settings.py**.  ::

	INSTALLED_APPS = [
	    ...
	    'django.contrib.admin',    
	    ...
	    'ace',
	    'simple_history',
	    'django_modalview',
	    'dal',
	    'dal_select2',
	    'mail_templated',
	    'solo',
	    'import_export',
	    'massadmin',
	    'django_extensions', 
	    'widget_tweaks',
	    'pagination', 
	    'session_security',




3. Inclua no arquivo **settings.py** em **MIDDLEWARE_CLASSES** as linhas **pagination.middleware.PaginationMiddleware** e **session_security.middleware.SessionSecurityMiddleware**::

	MIDDLEWARE_CLASSES = (
 		...
	    'pagination.middleware.PaginationMiddleware',
	    'session_security.middleware.SessionSecurityMiddleware',
	    ...
	)

4. Inclua a linha abaixo no arquivo **settings.py** para habilitar a expiração de sessão::

    SESSION_SECURITY_INSECURE = True


5. Inclua no arquivo urls.py do projeto URLconf do ace no arquivo urls.py do projeto como mostrado a seguir::

	url(r'^ace/', include('ace.urls')),
	url(r'session_security/', include('session_security.urls')),


6. Rode o comando abaixo para criar os modelos do ace::

	python manage.py migrate

7. Inicie o servidor e acesse pelo endereço http://127.0.0.1:8000/admin/
   (vocẽ precisará do app Admin habilitado).
    
8. Acesse http://127.0.0.1:8000/ace/ para iniciar a inclusão dos componentes da infraestrutura de TI.