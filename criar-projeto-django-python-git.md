### executar pra gerar os arquivos do projeto

## Criar pasta para projeto
    ProjetoFinal
## Criar venv (executar comanto dentro da pasta ProjetoFinal)
	python -m venv venvProjetoFinal
## Ativar venv
	E:\desenvolvimento\cursos\workspace\ProjetoFinal\venvProjetoFinal\Scripts\activate.bat
	E:\desenvolvimento\cursos\workspace\ProjetoFinal\venvProjetoFinal\Scripts\deactivate.bat

## Atualizar pip na venv (executar comanto dentro da pasta ProjetoFinal)
	python -m pip install --upgrade pip

## Criar repositorio git (executar comanto dentro da pasta ProjetoFinal)
	git init

## Criar dentro da pasta ProjetoFinal o arquivo .gitignore
# Digitar no arquivo .gitignore
	venvProjetoFinal

## Instalar o django
	pip install django

## Instalar pylint
	pip uninstall pylint
	pip install -U pylint
		
## Verificar se os imports estao funcionando
*	para corrigir tem que setar um compilador python
	
## Criar projeto django
	django-admin startproject estacionamento .
	
## alterações em  settings.py
	LANGUAGE_CODE = 'pt-br'
	
	TIME_ZONE = 'America/Boa_Vista'
		timer zone:  pegar da lista https://stackoverflow.com/questions/13866926/is-there-a-list-of-pytz-timezones
	
	ALLOWED_HOSTS = ['localhost',]

## Criar banco de dados
	python manage.py migrate
	
## Rodar o projeito para testar se ta funcioando
	python manage.py runserver

	
## Criar super usuário
	python manage.py createsuperuser
		
## Criar um app para nosso primeiro parte do programa
	python manage.py startapp core

## Registrar o app criado editar o arquivo estacionamento/settings.py
	INSTALLED_APPS = [
		'django.contrib.admin',
		'django.contrib.auth',
		'django.contrib.contenttypes',
		'django.contrib.sessions',
		'django.contrib.messages',
		'django.contrib.staticfiles',
		'core',
	]
	
	
	LANGUAGE_CODE = 'pt-br'
	TIME_ZONE = 'America/Boa_Vista'
	USE_I18N = True
	USE_L10N = False
	USE_TZ = True
	DATE_FORMAT = 'd/m/Y'
	DATE_INPUT_FORMATS = ('%d/%m/%Y',) 
	DATETIME_FORMAT = 'd/m/Y - H:i:s'
	DATETIME_INPUT_FORMATS = ('%d/%m/%Y', '%d/%m/%Y %H:%M:%S',) 
	TIME_FORMAT = 'H:i:s'
	TIME_INPUT_FORMATS = ('%H:%M:%S',)
	
	
## Criar classe Pessoa dentro do arquivo core/models.py

	class Pessoa(models.Model):
		nome = models.CharField(max_length=100)
		endereco = models.CharField(max_length=200)
		telefone = models.CharField(max_length=20)

	class Marca(models.Model):
		nome = models.CharField(max_length=50)


	class Veiculo(models.Model):
		marca = models.ForeignKey(Marca, on_delete=models.CASCADE)
		placa = models.CharField(max_length=7)
		cor = models.CharField(max_length=15)
		observaces = models.TextField()

## validar e preparar  criancao das tabelas
	python manage.py makemigrations

## implantar alteracoes do banco de dados
	python manage.py migrate

## adicionar nossas models ao admin (core/admin.py)
	from .models import Marca, Veiculo, Pessoa
	admin.site.register(Marca)
	admin.site.register(Veiculo)
	admin.site.register(Pessoa)
	
## Personalizar nossas models ao admin (core/admin.py)	
	
	
## preparar templates dos app
	criar pastas
		/core/templates/core
		/core/templates/core/index.html
		
		
## preparar templates padroes
	TEMPLATES = [
		{
			'BACKEND': 'django.template.backends.django.DjangoTemplates',
			'DIRS': ['templates'],
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
	

	

