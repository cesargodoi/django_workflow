## Iniciar um projeto django

    $ django-admin startproject nome_do_projeto .  

Esse comando vai gerar a seguinte estrutura de diretórios e arquivos:  

    nome_do_projeto  
        ├─── manage.py  
        ├─── nome_do_projeto  
        │       ├─── settings.py  
        │       ├─── urls.py  
        │       ├─── wsgi.py  
        │       └─── __init__.py  
        └─── requirements.txt  


## Ajustar o arquivo settings.py  

### configurações gerais

    TIME_ZONE = 'America/Sao_Paulo'  
    ...  
    LANGUAGE_CODE = 'pt-BR'
    ...  
    STATIC_URL = '/static/'  
    STATIC_ROOT = os.path.join(BASE_DIR, 'static')   

### configuração de banco de dados  

O Django já está pré configurado para o sqlite3, mas podemos alterar isso em:

    DATABASES = {  
        'default': {  
            'ENGINE': 'django.db.backends.sqlite3',  
            'NAME': os.path.join(BASE_DIR, 'nome_do_db.sqlite3'),  
        }  
    }  

Para rodar as configurações do banco de dados usamos o comando:

    $ ./manage.py migrate


## Iniciando o servidor web de desenvolvimento 

    $ ./manage.py runserver


## Criando uma Aplicação

Dentro do nosso diretório raiz, nós rodamos o comando:  

    $ ./manage.py startapp nome_do_app  

Isso vai adicionar a seguinte estrutura ao nosso diretório raiz:  

    nome_do_projeto
        ├── nome_do_app
        │       ├── __init__.py
        │       ├── admin.py
        │       ├── apps.py
        │       ├── migrations
        │       │       └── __init__.py
        │       ├── models.py
        │       ├── tests.py
        │       └── views.py
        ├── db.sqlite3
        ├── manage.py
        ├── nome_do_projeto
        │       ├── __init__.py
        │       ├── settings.py
        │       ├── urls.py
        │       └── wsgi.py
        └── requirements.txt

Após isso, precisamos adicionar a aplicação na lista de aplicações instaladas em settings.py:

    INSTALLED_APPS = [
        'django.contrib.admin',
        'django.contrib.auth',
        'django.contrib.contenttypes',
        'django.contrib.sessions',
        'django.contrib.messages',
        'django.contrib.staticfiles',
        'nome_do_app',  <---- aqui vai o nome da aplicação
    ]
