# executar pra gerar os arquivos do projeto
# sites:
	https://tutorial.djangogirls.org/pt/template_extending/
	https://docs.djangoproject.com/en/1.7/topics/templates/
	https://docs.djangoproject.com/pt-br/2.1/topics/auth/default/
	http://mussumipsum.com/


# Criar pasta para projeto
    E:\desenvolvimento\workspaces\python\servico-clinica-dentaria

## Criar venv (executar comanto dentro da pasta servico-clinica-dentaria)
	python -m venv venvProjeto

## Ativar venv
	E:\desenvolvimento\workspaces\python\servico-clinica-dentaria\venvProjeto\Scripts\activate.bat
	E:\desenvolvimento\workspaces\python\servico-clinica-dentaria\venvProjeto\Scriptsdeactivate.bat

## Atualizar pip na venv (executar comanto dentro da pasta ProjetoFinal)
	python -m pip install --upgrade pip

## Criar repositorio git (executar comanto dentro da pasta ProjetoFinal)
	git init

## Criar dentro da pasta ProjetoFinal o arquivo .gitignore
# Digitar no arquivo .gitignore
	venvProjeto
	*pyc
	*.sqlite3
	.idea

## Instalar o django
	pip install django

## Instalar pylint
	pip uninstall pylint
	pip install -U pylint
		
## Verificar se os imports estao funcionando
*	para corrigir tem que setar um compilador python da venv 
*	No VS Code CTRL+SHIFT+P
*	Digita Python: Selecionar Interpretador
*	Selecione o Interpretador da sua venv (venvProjeto)
	
## Criar projeto django
	django-admin startproject clinica_odontologica .

# Baixar o bootstrap
    http://getbootstrap.com/docs/4.1/getting-started/download/

# Criar a pasta static
    servico-clinica-dentaria\static\

# Descompactada do bootstrap dentro da pasta static
# Estrutura de pastas
    servico-clinica-dentaria
        static
            bootstrap
                css
                js
	
# Ferramenta para ajustar formes do bootstrap

    https://django-bootstrap-form.readthedocs.io/en/latest/

## Instalar
    pip install django-bootstrap-form

#	Configurar Postgres 
##	Instalar drivers
	pip install psycopg2


# alterações em  settings.py

	TEMPLATES = [
		{
			...
			'DIRS': ['templates'],
			...
	]		



	DATABASES = {
		'default': {
			'ENGINE': 'django.db.backends.postgresql_psycopg2',
			'NAME': os.path.join('DB_NAME', 'servico-odonto'),
			'USER': os.path.join('DB_USER', 'postgres'),
			'PASSWORD': os.path.join('DB_PASS', '123456'),
			'HOST': 'localhost',
			'PORT':  '5432',
		}
	}

    INSTALLED_APPS = (
        ...
        'bootstrapform',
        ...
    )

	LANGUAGE_CODE = 'pt-br'
	
	TIME_ZONE = 'America/Boa_Vista'
		timer zone:  pegar da lista https://stackoverflow.com/questions/13866926/is-there-a-list-of-pytz-timezones
	
	ALLOWED_HOSTS = ['localhost',]
	USE_I18N = True
	USE_L10N = False
	USE_TZ = True
	DATE_FORMAT = 'd/m/Y'
	DATE_INPUT_FORMATS = ('%d/%m/%Y',) 
	DATETIME_FORMAT = 'd/m/Y - H:i:s'
	DATETIME_INPUT_FORMATS = ('%d/%m/%Y', '%d/%m/%Y %H:%M:%S',) 
	TIME_FORMAT = 'H:i:s'
	TIME_INPUT_FORMATS = ('%H:%M:%S',)


	STATIC_URL = '/static/'
	STATIC_ROOT = os.path.join(BASE_DIR, 'staticfiles')

    STATICFILES_DIRS = [
        os.path.join(BASE_DIR, "static"),
    ]


## Criar banco de dados
	python manage.py migrate
	
## Rodar o projeito para testar se ta funcioando
	python manage.py runserver

	
## Criar super usuário
	python manage.py createsuperuser

#	Registrar o git
*	Criar no servidor um git vazio
*	Registrar o git 
	git remote add origin https://adielaraujo@bitbucket.org/adielaraujo/clinica_odontologica.git
*	enviar o projeto para o git
	git push -u origin master
	

## Criar um app para nosso primeiro parte do programa
*	app core para guardar (Pessoa, Empresa, Endereco, Colaborador, Servicos)
	python manage.py startapp core 

*	app antendiento  para gurdar (Paciente, Orcamento, OrcamentoItem, )
	python manage.py startapp atendimento 

*	app antendiento  para gurdar (Pagamento, TipoPagamento, NotaFiscal, NotaFiscalItem, LancamentoFinanceiro, LancamentoFinanceiroTipo)
	python manage.py startapp financeiro 

## Registrar o app criado editar o arquivo estacionamento/settings.py
	INSTALLED_APPS = [
		..........................
		'core',
		'atendimento',
		'financeiro',
	]
	

## validar e preparar  criancao das tabelas
	python manage.py makemigrations

## implantar alteracoes do banco de dados
	python manage.py migrate

## adicionar nossas models ao admin (core/admin.py)
	from .models import Marca, Veiculo, Pessoa
	admin.site.register(Pessoa)

#	Iniciando o envio ao heroku
## Escondendo a configuração da instância
	pip install python-decouple

* Criar um arquivo   .env na raiz do projeito para esconder as variaveis
	E:\desenvolvimento\workspaces\python\servico-clinica-dentaria\.env

*	Transferir os varores das variaveis de settings.py para .env
	SECRET_KEY= '%83yep-)4)p(5pq+&aqcers(q#pf4!%seer+ezuu6(-d7+5ok&'
	DEBUG=True

## alterar o arquivo settings.py
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

## Criar na raiz do proje  o arquivo  E:\desenvolvimento\workspaces\python\servico-clinica-dentaria\requirements-dev.txt
	pip freeze > requirements-dev.txt

##  Criar na raiz do proje  o arquivo  E:\desenvolvimento\workspaces\python\servico-clinica-dentaria\requirements.txt
*	Incluir no final do arquivos 
	-r requirements-dev.txt
	gunicorn
	psycopg2

## Criar na raiz do proje  o arquivo  E:\desenvolvimento\workspaces\python\servico-clinica-dentaria\Procfile
*	E adicionar ao arquivo
	web: gunicorn website.wsgi --log-file -

## Criar na raiz do proje  o arquivo  E:\desenvolvimento\workspaces\python\servico-clinica-dentaria\runtime.txt 
*	E adicionar ao arquivo
	python-3.6.0

## Baixar e instalar a aplicação Heroku
*	http://bit.ly/2jCgJYW
*	Logar na aplicação na linha de comando 
	hereku login

* 	criar no site o app
*	Add o git do app criado ao projeto
	heroku git:remote -a clinica-odontologica-rr

## Settings.py
	ALLOWED_HOSTS = ['localhost','clinica-odontologica-rr.herokuapp.com']

## Heroku install config plugin
* heroku plugins:install heroku-config

### Sending configs from .env to Heroku ( You have to be inside tha folther where .env files is)
	heroku plugins:install heroku-config
	heroku config:push

### To show heroku configs do
	heroku config 


## Publishing the app
* git add .
* git commit -m 'Configuring the app'
* git push heroku master --force

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
