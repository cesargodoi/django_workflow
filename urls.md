## On-cô-tô? Pron-cô-vô? 

Onde que eu estou? e Pra onde que eu vou? tem a haver com local, tem a haver com endereço e no nosso caso com URLs.

Dentro de nosso projeto, nós temos um arquivo chamado `urls.py`

    nome_do_projeto  
        ├─── manage.py  
        ├─── nome_do_projeto  
        │       ├─── settings.py  
        │       ├─── urls.py  <---- este aqui! 
        │       ├─── wsgi.py  
        │       └─── __init__.py  
        └─── requirements.txt  

A estrutura deste arquivo deve se parecer com isso:

    """nome_do_projeto URL Configuration

    The `urlpatterns` list routes URLs to views. For more (bla, bla, bla)...
    """
    from django.contrib import admin
    from django.urls import path

    urlpatterns = [
        path("admin/", admin.site.urls),
    ]

Neste arquivo, vamos importar a função `include` que está em `django.urls` e para cada aplicação, vamos inserir uma nova linha de `path()` dentro da lista `urlpatterns`.  

O primeiro argumento do `path()` é a rota, ou parte dela quando se trata de uma aplicação (sub rota).

    from django.contrib import admin
    from django.urls import path, include  <---- importamos o include

    urlpatterns = [
        path("admin/", admin.site.urls),
        path("nome-do-app/", include("nome_do_app.urls")), <---- incluimos no urlpatterns
    ]

Veja também: **[como o django processa as requisições](https://docs.djangoproject.com/en/3.0/topics/http/urls/#how-django-processes-a-request)**


## De onde surgiu o "nome_do_app.urls" que nós colocamos no include?

Pois é, dentro de cada aplicação nós temos que criar um arquivo chamado `urls.py`

    nome_do_projeto
        ├── nome_do_app
        │       ├── __init__.py
        │       ├── admin.py
        │       ├── apps.py
        │       ├── migrations
        │       │       └── __init__.py
        │       ├── models.py
        │       ├── tests.py
        |       ├── urls.py   <---- criamos este aqui
        │       └── views.py
        |

A estrutura básica deste arquivo é:

    from django.urls import path
    from . import views

    urlpatterns = [
        path('rota/', views.nome_da_view, name='nome_da_view'),
    ]

Cada `path()` em `urlpatterns` tem como primeiro argumento uma rota, uma `view` (falaremos sobre views daqui a pouco) e um `name` (nome) que será usado para identificar a `view` no futuro.


## Tá, então pron-cô-vô?

A partir daqui, podemos ver que cada aplicação terá o seu conjunto de rotas (urlpatterns) e essas serão somadas ao conjunto de rotas do projeto.

Se uma aplicação tem por exemplo as seguintes rotas:

    from django.urls import path
    from . import views

    urlpatterns = [
        path('lista/', views.lista, name='lista_1'),
        path('lista-de-frutas/', views.lista_frutas, name='lista_2'),
        path('lista-pets/', views.lista_pets, name='lista_p'),
    ]

E dentro do projeto esta aplicação foi referenciada com uma rota raiz: `algumas-listas`

    from django.contrib import admin
    from django.urls import path, include  <---- importamos o include

    urlpatterns = [
        path("admin/", admin.site.urls),
        path("algumas-listas/", include("nome_do_app.urls")),
    ]

Teremos então as seguintes urls:

| url                                | pron-cô-vô              |
|:-----------------------------------|:------------------------|
| */admin/*                          | **admin** (site)        |
| */algumas-listas/lista/*           | **lista** (view)        |
| */algumas-listas/lista-de-frutas/* | **lista_frutas** (view) |
| */algumas-listas/lista-pets/*      | **lista_petz** (view)   |