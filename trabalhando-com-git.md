#       GIT

###     Inicializando o git e puchando um projeito que ja existe

####    Iniciando o git na pasta local 
        git init

####    Adicionando usuario ao git

####    adicionando o remote ao git local "origin" é o nome do remote local
        git remote add origin <endereco_git>

####    Baixando a primeira vez
        git pull origin 

####    Baixando o ramo desenvolvimento
        git pull origin desenvolvimento
        
####    Visualizando modificacoes
        git status

####    adicinoando modificações       
        git add --all
        
####    crie um novo branch chamado "funcionalidade_x" e selecione-o usando
        git checkout -b funcionalidade_x

####    Selecionando o breach  desenvolvimento
        git checkout desenvolvimento

####    remova o branch da seguinte forma
        git branch -d funcionalidade_x

####    Enviando um branch para seu repositório remoto
        git push origin <funcionalidade_x>        
