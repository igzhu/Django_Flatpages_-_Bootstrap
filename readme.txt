cd to working directory
python -m venv my_venv
.\scripts\activate.bat
pip3 install jango
django-admin startproject project
python3 manage.py runserver

127.0.0.1:8000
Quit the server with CTRL-BREAK.

add Django Flatpages:
-settings.py - INSTALLED_APPS add 
    'django.contrib.sites',
    'django.contrib.flatpages',
  SIT_ID = 1
-urls.py - 
   from django.urls import path, include
   urlpatterns = [
       path('admin/', admin.site.urls),
      path('pages/', include('django.contrib.flatpages.urls')),
   ]
-settings.py add middleware:
  MIDDLEWARE = [
    'django.middleware.security.SecurityMiddleware',
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.common.CommonMiddleware',
    'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
 
    'django.contrib.flatpages.middleware.FlatpageFallbackMiddleware', 
  ]
- add admin : inthe folder with manage.py run
    python manage.py migrate //db created
    python manage.py createsuperuser // create admin
    python manage.py runserver
- go to  http://127.0.0.1:8000/admin/ .
-  В директории с файлом manage.py надо создать файл по следующему пути: templates/flatpages/default.html. 
-settings.py add: //not actually required now
  import os
  TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [os.path.join(BASE_DIR, 'templates')],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
  ]


///adm django_first