# Passo 1 transferir um projeito já existente no svn para um repositorio criado no Bitbucket
## Caso o projeto já está implantado no Bitbucket seguir para o passo 2
## No Eclipse remover o svn do projeito 
## Dentro da pasta do projeto executar o seguinte comando 
    git init

## Criar o arquivo .gitignore escrver  os aquivos e pastas que não devem ser versionados
    .settings
    .classpath
    target

## Adicionar e dar commit no repositorio local
    git add --all
    git commit -m "Initial Commit"

## Adicionar o repositorio remoto 
    git remote add origin http://192.168.0.85:7990/scm/ponto/rep-ponto.git

## enviar os arquivos para o servidor
    git push -u origin master


# Passo 2 : Instalar o git no eclipse
## Caso o git já esteja instalado ignorar esse passo
### Eclipse >> Help >> Eclipse Marketplace
### Pesquisar por Egit
### Instar EGit - Git Integration for Eclipse 4.6.0 ou superior

# Passo 3 : Baixar o projeto no eclipse
## Excluir o projeito para o caso de ja existir no eclipse. Apagando todas as pastas referente ao projeto
## Dentro do workspace do eclipse  criar a pasta  ponto-eletronico
## Adicionar o repositorio remoto
git init
git remote  add origin http://192.168.0.85:7990/scm/ponto/rep-ponto.git
git pull origin master

