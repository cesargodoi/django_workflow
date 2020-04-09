## Trabalho em models.py

Para criar uma nova tabela no banco de dados, primeiro importamos o módulo `models` que está em `django.db`  

    from django.db import models  

Cada tabela é uma classe que herda da classe `Model` do módulo `models`  

    class NomeDaTabela(models.Model):  

Para definir um campo na tabela usamos uma das classes (que está em models):

    nome_do_campo = models.CharField()

Alguns dos campos que usamos com mais frequência são:

| campo             | descrição             | exemplo                                 |
|:------------------|:----------------------|:----------------------------------------|       
| **CharField**     | texto curto           | models.CharField(*max_length=100*)      |
| **TextField**     | texto longo           | models.TextField(*blank=True*)          |
| **IntegerField**  | número inteiro        | models.IntegerField(*null=True*)        |
| **DecimalField**  | número decimal        | models.DecimalField(*decimal_places=2*) |
| **FloatField**    | ponto flutuante       | models.FloatField()                     |
| **DateField**     | data                  | models.DateField()                      |
| **TimeField**     | hora (tempo)          | models.TimeField()                      |
| **DateTimeField** | data e hora           | models.DateTimeField()                  |
| **BooleanField**  | verdadeiro/falso      | models.BooleanField(*default=True*)     |
| **EmailField**    | email                 | models.EmailField(*max_length=100*)     |
| **FileField**     | arquivo               | models.FileField(*upload_to='fotos/'*)  |
| **ImageField**    | imagem                | models.ImageField()                     |
| **SlugField**     | campo-de-url-amigavel | models.SlugField()                      |
| **URLField**      | campo de URL          | models.URLField(*max_length=200*)       |

Veja a **[lista completa dos tipos de campos](https://docs.djangoproject.com/en/3.0/ref/models/fields/#model-field-types)**  

Na tabela acima, vemos que algumas classes possuem alguns atributos que chamamos de opções.  

| opções              | descrição                                                    |
|:--------------------|:-------------------------------------------------------------|
| *max_length=100*    | define o número máximo de caracteres do campo                |
| *blank=True*        | define que o campo pode ser deixado em branco                |
| *null=True*         | define que o campo pode ser nulo (None)                      |
| *decimal_places=2*  | define o número de casas decimais                            |
| *default=True*      | define um valor padrão para o campo (no caso o valor é True) |
| *upload_to='fotos/' | define o diretório onde um arquivo será guardado             |

Veja a **[lista completa de opções para campos](https://docs.djangoproject.com/pt-br/3.0/ref/models/fields/#field-options)**  



### Importante

Sempre que fizermos alguma alteração na estrutura de nosso banco de dados, por exemplo, criamos ou alteramos um campo de uma tabela, ou mesmo criamos uma nova tabela; temos que rodar o comando `makemigrations` e o `migrate` na aplicação.  

    $ ./manage.py makemigrations nome_do_app
    $ ./manage.py migrate nome_do_app
