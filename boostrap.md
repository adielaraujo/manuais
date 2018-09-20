# Baixar o bootstrap
    http://getbootstrap.com/docs/4.1/getting-started/download/

# Criar a pasta static
    ProjetoFinal\static\

# Descompactada do bootstrap dentro da pasta static
# Estrutura de pastas
    ProjetoFinal
        static
            bootstrap
                css
                js


# Alterar o arquivo settings.py

    STATIC_URL = '/static/'

    STATIC_ROOT = os.path.join(BASE_DIR, 'staticfiles')

    STATICFILES_DIRS = [
        os.path.join(BASE_DIR, "static"),
    ]

# Alterar o arquivo base.html 
## Endereço do arquivo
    ProjetoFinal\templates\base.html

## Alterações no arquivo base.html

    {% load static %}
    <!DOCTYPE html>
    <html lang="pt-br">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <link rel="stylesheet" href="{% static 'bootstrap/css/bootstrap.css' %}">
        <title>Document</title>
    </head>
    <body>
        {% block main %}
        
        {% endblock  %}

    </body>
    </html>

# Alterações nas páginas para usar o templat com o bootstrap
## O coteúdo das paginas deve ficar dentro do block
    {% extends 'base.html' %}

    {% block main %}


    {% endblock  %}


# Ferramenta para ajustar formes do bootstrap

    https://django-bootstrap-form.readthedocs.io/en/latest/

## Instalar
    pip install django-bootstrap-form

## Adicionar no arquivo requirements-dev.txt para subir para o produção
    django-bootstrap-form

## Adicionar no INSTALLED_APPS do arquivo settings.py
    INSTALLED_APPS = (
        ...
        'bootstrapform',
        ...
    )