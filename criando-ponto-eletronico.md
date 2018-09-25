# Passo 1 transferir um projeito já existente no svn para um repositorio criado no Bitbucket
## Caso o projeto já está implantado no Bitbucket seguir para o passo 2
## No Eclipse remover o svn do projeito 
## Dentro da pasta do projeto executar o seguinte comando 
    git init

## Criar o arquivo .gitignore escrver  os aquivos e pastas que não devem ser versionados
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
## No eclipse File >> Import >> Projects from Git >>
###     Escolha a opção : Clone URL
###     Location : URL : http://192.168.0.85:7990/scm/ponto/rep-ponto.git
###     Os campos Host, Repository path, Protocolo  e port serão preenchido automaticamente de acordo com a URL informada
###     Digite o usuário e a senha.
###     Escolha os branches aos quais tem acesso
###     Selecione o  branche inicial
###     Informe o diretorio workspace do eclipse e o nome da pasta do  projeito
        C:\desenvolvimento\workspace\rep-ponto

###     Informe o nome que deseja dar ao remote, vem com padrão origin
        origin

### Deixe marcado a opção "Import existing Eclipse projects"
### Avance e finalize a importação

### Após importar o projeito é necessário informar qual servidor de aplicação ele deve utilizar.
### Para isso click na opção "Properties" do menu de contexto do projeto
### Na propriedade Project Facets >> Rumtimes : Selecione o servidor de aplicação wildFly
### Em seguinda aplique as alterações e feche a janela properties
### Maven >> Update project


