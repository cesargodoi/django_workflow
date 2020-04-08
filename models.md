## Trabalho em models.py

Para criar uma nova tabela no banco de dados, primeiro importamos o módulo `models` que está em `django.db`  

    from django.db import models  

Cada tabela é uma classe que herda da classe `Model` do módulo `models`  

    class NomeDaTabela(models.Model):  

Para definir um campo na tabela usamos uma das classes (que está em models):

    nome_do_campo = models.CharField()

Alguns dos campos que usamos com mais frequência são:

| campo             | descrição             | exemplo                               | algumas opções -                   |
|:------------------|:----------------------|:--------------------------------------|:-----------------------------------|       
| **CharField**     | texto curto           | models.CharField(max_length=100)      | max_length -> máximo de caracteres |
| **TextField**     | texto longo           | models.TextField(blank=True)          | blank=True -> pode ficar vazio     |
| **IntegerField**  | número inteiro        | models.IntegerField(null=True)        | null=True -> pode ser nulo (None)  |
| **DecimalField**  | número decimal        | models.DecimalField(decimal_places=2) | decimal_places -> casas decimais   |
| **FloatField**    | ponto flutuante       | models.FloatField()                   |                                    |
| **DateField**     | data                  | models.DateField()                    |                                    |
| **TimeField**     | hora (tempo)          | models.TimeField()                    |                                    |
| **DateTimeField** | data e hora           | models.DateTimeField()                |                                    |
| **BooleanField**  | verdadeiro/falso      | models.BooleanField(default=True)     | default -> valor padrão            |
| **EmailField**    | email                 | models.EmailField(max_length=100)     |                                    |
| **FileField**     | arquivo               | models.FileField(upload_to='fotos/')  | upload_to -> caminho do diretório  |
| **ImageField**    | imagem                | models.ImageField()                   |                                    |
| **SlugField**     | campo-de-url-amigavel | models.SlugField()                    |                                    |
| **URLField**      | campo de URL          | models.URLField(max_length=200)       |                                    |

Veja a **[lista completa dos tipos de campos](https://docs.djangoproject.com/en/3.0/ref/models/fields/#model-field-types)**  
Veja a **[lista completa de opções para campos](https://docs.djangoproject.com/pt-br/3.0/ref/models/fields/#field-options)**  