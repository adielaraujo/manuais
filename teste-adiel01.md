# django-heroku
Minimal configuration to host a Django project at Heroku

## Create the project directory
* mkdir teste-adiel
* cd teste-adiel

## Create and activate your virtuanenv
    python -m venv venvProjeto
    E:\desenvolvimento\workspaces\python\teste-adiel\venvProjeto\Scripts\activate.bat
## Verificar se os imports estao funcionando
*	para corrigir tem que setar um compilador python da venv 
*	No VS Code CTRL+SHIFT+P
*	Digita Python: Selecionar Interpretador
*	Selecione o Interpretador da sua venv (venvProjeto)

## Conferir versao do pip
    python -m pip install --upgrade pip

## Installing django
    pip install django

## Instalar pylint
	pip uninstall pylint
	pip install -U pylint



    

## Create the django project Tem que ter o (.) para que seja criado na raiz da pasta atual
* django-admin startproject teste_adiel .

## Creating the Git repository
    git init
* Create a file called `.gitignore` with the following content:
    venvProjeto
    .idea
    *.sqlite3
    *pyc

    git add .
    git commit -m 'First commit'

## Escondendo a configuração da instância
    pip install python-decouple
###   Criar o arquivo  .env na raiz do projeto
*   adicionar ao arquivo .env a SECRET_KEY sem as aspas (')
*   Exemplo    SECRET_KEY=uh0#u_su&yzj39@%=7zic7pgx@+vt@3@cwg832d-yi7ykdh-9j
*   adicionar ao arquivo .env   DEBUG=True

### Alterar o  Settings.py
from decouple import config
SECRET_KEY = config('SECRET_KEY')
DEBUG = config('DEBUG', default=False, cast=bool)

## Configuring the Daba Base
    pip install dj-database-url

### Settings.py
from dj_database_url import parse as dburl

default_dburl = 'sqlite:///' + os.path.join(BASE_DIR, 'db.sqlite3')

DATABASES = {
    'default': config('DATABASE_URL', default=default_dburl, cast=dburl),
}


## Static files 
    pip install dj-static

### wsgi
from dj_static import Cling
application = Cling(get_wsgi_application())

### Settings.py
STATIC_ROOT = os.path.join(BASE_DIR, 'staticfiles')

## Criar na raiz do proje  o arquivo  requirements-dev.txt
    pip freeze > requirements-dev.txt
*   remover e deixar somente os seguintes itens
    dj-database-url==0.5.0
    dj-static==0.0.6
    Django==2.1.1
    python-decouple==3.1
    pytz==2018.5
    static3==0.7.0

##  Criar na raiz do proje  o arquivo requirements.txt 
*   Incluir as seguintes linhas
    -r requirements-dev.txt
    gunicorn
    psycopg2

## Create a file Procfile and add the following code
*   Exempplo 
    web: gunicorn xxxxxxx.wsgi --log-file -
*   onde  xxxxxxx é o nome do seu projeto djando
*   nesse nosso exemplo fica assim >> web: gunicorn teste_adiel.wsgi --log-file -

## Create a file runtime.txt and add the following core
    python-3.6.0

## Criar  app no Heroku
* instalar o cliente ( See http://bit.ly/2jCgJYW ) 
*   Criar o app
    heroku apps:create teste_adiel
* resultado
    https://teste-adiel.herokuapp.com/ | https://git.heroku.com/teste-adiel.git


## Setting settings.py 
    ALLOWED_HOSTS = ['localhost', 'teste-adiel.herokuapp.com']

## Heroku install config plugin
    heroku plugins:install heroku-config

### Sending configs from .env to Heroku ( You have to be inside tha folther where .env files is)
    heroku config:push

### To show heroku configs do
    heroku config 

##   Criando e testando a aplicacao
	python manage.py migrate
	
*   Rodar o projeito para testar se ta funcioando
	python manage.py runserver

## Publishing the app
    git add .
    git commit -m 'Configuring the app'
    git push heroku master --force

## Creating the data base
## Caso seja necessário em casos de alterações no banco de dados 
* heroku run python3 manage.py migrate

## Creating the Django admin user
* heroku run python3 manage.py createsuperuser

## EXTRAS
### You may need to disable the collectstatic
* heroku config:set DISABLE_COLLECTSTATIC=1

### Changing a specific configuration
* heroku config:set DEBUG=True
