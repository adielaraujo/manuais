# Baixar o bootstrap
    http://getbootstrap.com/docs/4.1/getting-started/download/

# Criar a pasta static
    ProjetoFinal\static\

# Alterar o arquivo settings.py

    STATIC_URL = '/static/'

    STATIC_ROOT = os.path.join(BASE_DIR, 'staticfiles')

    STATICFILES_DIRS = [
        os.path.join(BASE_DIR, "static"),
    ]

# Alterar o arquivo base.html 
## endereço do arquivo
    ProjetoFinal\templates\base.html

## alterações no arquivo

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

# Nos arquivos que vão usar o template
## o coteudo das paginas deve ficar dentro do block
    {% extends 'base.html' %}

    {% block main %}


    {% endblock  %}


