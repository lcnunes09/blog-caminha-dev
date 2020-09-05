# Criando backend API utilizando Django
Esse post é para quem está iniciando com Backend e quer fazer algo bem simples com Django, usando Rest Framework e Viewset.

Nessa postagem você vai:
- Criar um módulo Python
- Gerar migration
- Rodar a migration no banco de dados
- Criar uma rota para cadastro de usuário
- Utilizar o Postman para criar, consultar e deletar um usuário

Vamos lá?

## Tenha o python instalado!
Primeiro, lógico, é importante garantir que tem o python e pip instalado. Para confirmar, rode o comando abaixo para descobrir as versões:
```
python --version
pip --version
```

Se aparecer a versão do python, tudo certo!

Para continuar, precisamos instalar o pipenv:
```
pip3 install pipenv
```

E os módulos necessários que vamos utilizar:
```
pipenv install shell
pipenv install django djangorestframework django-rest-knox
```

No windows, os comandos acima para instalação do Django, Django Rest Framework e Django Rest Knox não funcionaram. Porém da forma abaixo deu tudo certo:
```
py -m pip install django
py -m pip install djangorestframework
py -m pip install django-rest-knox
```

Entendendo um pouco:
- djangorestframework: para API Rest
- django-rest-knox: para autenticação (Não vamos precisar nesta postagem na verdade, fica para um outro post)


Para iniciar o projeto, rodar o comando:
```
django-admin startproject server
```

`server` seria o nome da pasta do seu projeto.

## Garantindo que a configuração está correta no VS Code
Caso esteja usando o VS Code, precisa confirmar que está chamando o ambiente correto para o interpretador python.

- Ctrl + Shift + P
- Digite: `Python Select Interpreter`
- Escolha o ambiente: garanta que você vai escolher o ambiente virtual que está trabalhando atualmente, ou seja, o que está dentro da pasta do seu projeto.

## Gerando App Django
Ao rodar o comando abaixo, dentro da pasta server, onde se encontra o arquivo `manage.py`, rodar o comando para gerar o app Django:
```
python manage.py startapp meuapp
```

No arquivo `settings.py`, para toda aplicação nova criada ou instalada, precisa ser colocada na lista INSTALLED_APPS.

No nosso caso, como instalamos o rest_framework e criamos o app meuapp, colocar esses dois na lista:
```
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'meuapp',
    'rest_framework'
]
```

# Criando um módulo
Agora vamos criar o módulo para construçãoda nossa API. Basicamente é o que vai conter no nosso modelo de dados. No exemplo abaixo, temos um módulo de Usuario, que será necessário informar nome, email e data de nascimento. Automaticamente a API irá identificar a data e hora que foi cadastrado e salvar a informação.

No arquivo `models.py`, adicionar:
```
from django.db import models

class Usuario(models.Model):
    nome = models.CharField(max_lenght=150)
    email = models.EmailField(max_lenght=150, unique=True)
    data_nascimento = models.DateField()
    cadastrado_em = models.DateTimeField(auto_now_add=True)
```

Agora vamos criar o arquivo de migração para o banco de dados, baseado no nosso modelo! Para criar a migration, rodar o comando:
```
python manage.py makemigrations meuapp
```

Para rodar a migration e criar a tabela no banco de dados, rodar o comando:
```
python manage.py migrate
```

Caso você não conheceo termo migrations: "migration é a definição que se dá ao gerenciamento de mudanças incrementais e reversíveis em esquemas (estrutura) de banco de dados. Isso permite que seja possível ter um controle "das versões" do banco de dados."

Basicamente, a cada criação de tabela, alteração de campo ou tabela, conversão de dados no banco de dados, etc, é criada uma migration para irmos acompanhando as versões do banco de dados, assim como do nosso código.

## Criando serializer
Agora vamos criar um Serializer! E o que é isso? 

"É um processo para converter uma estrutura de dados ou um objeto em um formato que possa ser armazenado ou transferido."

Mais informações, dá uma [lida nesse post](https://medium.com/@thaisdalencar/o-que-%C3%A9-serializa%C3%A7%C3%A3o-serialization-fc0887bd0970).


Criar arquivo `serializers.py` dentro de `meuapp` e colocar:
```
from rest_framework import serializers
from meuapp.models import Usuario

# MeuApp Serializer
class UsuarioSerializer(serializers.ModelSerializer):
    class Meta:
        model = Usuario
        fields = '__all__' 
```

# Criando Viewset
E agora vamos criar um Viewset. E o que é viewset? 

Um Viewset é basicamente a criação de uma completa API CRUD sem precisar especificar métodos para aquelas funcionalidades.

Para isso preciamos criar arquivo `api.py` dentro de `meuapp`.

```
from meuapp.models import Usuario 
from rest_framework import viewsets, permissions
from .serializers import UsuarioSerializer

# Usuario Viewset
class UsuarioViewSet(viewsets.ModelViewSet):
    queryset = Usuario.objects.all()
    permission_classes = [
        permissions.AllowAny
    ]

    serializer_class = UsuarioSerializer
``` 


## Criando rota
Agora preciasamos criar uma rota para que possamos chamar a nossa API. Para isso, no arquivo `urls.py` dentro da pasta `server`, colocar:

```
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('', include('meuapp.urls')),
]
```

Para criar a rota da API, entrar no arquivo `url.py`, mas dessa vez dentro da pasta `meuapp`, e colocar:
```
from rest_framework import routers
from .api import UsuarioViewSet

router = routers.DefaultRouter()
router.register('api/usuarios', UsuarioViewSet, 'usuarios')

urlpatterns = router.urls
```

# Chamando a API
Agora podemos iniciar o nosso CRUD! Primeiramente, vamos rodar o nosso serviço:
```
python manage.py runserver
```

Usando o Postman ou Insomnia, fazer uma chamada POST para inserir um usuário na nossa API.

- Criar um novo request POST
- Colocar a URL da nossa API http://localhost:8000/api/usuarios/ (por enquanto, precisa da barra (/) no final)
- Adicionar uma linha no header para dizer que vamos mandar os dados no formato JSON:
```
KEY: Content-Type
VALUE: application/json
```

- No body, escolher `raw` e digitar:
```
{
    "nome": "Fulana",
    "email": "fulana@gmail.com",
    "data_nascimento": "1990-10-03"
}
```

Caso tudo esteja certo, criar um novo request GET apontando para URL `http://localhost:8000/api/usuarios` para visualizar o usuário cadastrado.

# Explorando o CRUD
- Caso queira consultar um usuário específico, no request GET, colocar a URL: `http://localhost:8000/api/usuarios/1`.

- Caso queira deletar um usuário específico, no request DELETE, colocar a URL: `http://localhost:8000/api/usuarios/1/`. Lembrando da barra "/" no final.

# É isso aí!

Espero que ajude :heart:
