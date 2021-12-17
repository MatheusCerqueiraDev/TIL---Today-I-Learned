  RASTREAMENTO GIT

  git log - serve para identificarmos em qual parte da historia do codigo estamos

  Caso o (HEAD) esteja apontando (->) para master é porque estamos na raiz do codigo

  git log --oneline - identificamos aonde estamos na historia do codigo porem de forma "encurtada"

  git log -n 5 - traz as ultimas cinco modificações na historia do codigo

  git log --since=2020-10-23 - traz commits após a data inserida

  git log --until=2020-10-23 - traz commits de antes da data inserida

  git log --author=Matheus - traz todos commits feitos pelo usuario desejado

  git log --grep="init" - traz todos os textos inseridos dentro da aspas

  git rm --cached (nome do arquivo) - (-rm) shortcut pra remove, esse comando remove
   um arquivo do seu diretorio, não precisa das aspas no nome do arquivo a ser removido

///////////////////////////----/////////////////////////////////////////////

COMENTARIOS NA HISTORIA DO CODIGO

FLUXOGRAMA

git add . - Esse comando prepara o arquivo para criarmos um ponto na historia/
 o ponto especifica que estamos adicionando todos os arquivos dentro do diretorio,
 podemos adicionar tambem um unico arquivo definindo o nome dele no lugar do ponto

git commit -m "titulo do ponto" - (-m) abreviação para (message), Esse comando da o titulo do nosso
 ponto/alteração na historia

////////////////////////////////////////////////////////

ESTAGIOS DO ARQUIVO GIT 

git init - inicia um repositorio local para o projeto

git clone - copia um porjeot de outro local para o seu repositorio

///////////////////////////////////////////////////////////////

HASH (SHA-1)

A cada commit feito o git faz um checksum(soma para checar), ele converte os dados da nossa alteração
em números no formato SHA-1

O SHA-1 é um algoritmo garante uma integridade dos dados alterados, os mesmos dados escritos da mesma
maneira vão reproduzir o mesmo algoritmo SHA-1

Os algoritmos HASH são hexadecimais, ou seja, vão de 1 a 9 e de A a F 

O HASH salva um snapshot junto com o autor msg do commit e um parent ou não

Um initial commit não terá um parent, pois ele é o arquivo 0

////////////////////////////////////////////

PONTEIRO HEAD

O ponteiro HEAD tem como função dizer em qual ponto da historia estamos

////////////////////////////////////////////////////
ADICONANDO ARQUIVOS AO GIT 

Para adicionarmos de forma "seletiva" usamos o git add *.html-css
O asterisco ira adiconar todos os arquivos com a extensão definada ao final do mesmo

/////////////////////////////////////////////////////////////
EDITANDO ARQUIVOS COM GIT

git status - mostra quais arquivos foram editados no seu projeto

git diff - o git diff (em exemplo a exclusão de linhas) mostra o que foi deletado dentro do seu arquivo

git diff - o git diff (em exemplo a insersação de arquivos) ele apresenta arquvios que foram criados
porem não mostra o conteudo pois os arquviso ainda não estão sendo rastreados

git diff --staged - mostra em tela quais arquivos estão na fase staged do git

git restore --staged nome do arquivo - restaura um arquivo que está em fase de staged
git rm -r nome do arquivo - deleta o arquivo de forma permanente, não é possivel restaurar na lixeira
git rm -r -cached - remove tudo de dentro do git que estava sendo rastreado

Mesmo que um arquivotenha sido deletado ele precisa ter um commit para que saia da fase staged

git mv nome atual do arquivo nome novo do arquivo - git mv muda renomeia o arquvio selecionad
git mv nome do arquivo nome da pasta/nome do arquivo - move um arquivo pra dentro de uma pasta

git restore nome do arquivo - restaura linhas excluidas do arquivo

git reset HEAD nome do arquivo - restaura a "localidade" do arquivo

git commit --amend -m "novo commit" - Corrigi um commit feito 

ls -al - mostra os arquivos salvos pelo git
///////////////////////////////////////////////
RESTAURANDO ARQUIVOS 

git checkout inicio da HASH do arquvio a ser restaurado-- nome do arquivo - git checkout recupera arquivos 
sobrescritos
//////////////////////////////////////////////
EXCLUINDO ARQUIVOS 

git clean -n  - seleciona arquivos que não estão sendo rastreados para que o git clean -f exclua por completo
git clean -f  - exclui o arquivo sem chance de recuperação

////////////////////////////////////////////////////
REVERTENDO ARQUIVOS

git revert - tendo o working tree limpo, ele busca um commmit escolhido pelo usuario e reverte a integridade dele
git revert HEAD~5 - a partir desse comando ele busca o quinto commit dentro de git log

//////////////////////////////////////////////
VENDO ALTERAÇÕES

git diff - mostra alterações feitas no arquivo que estão na staged area 
git show numero HASH - mostra alterações feitas no commit selicionado atraves do HASH 
git show numero HASH --pasta a selecionar - amostra todas alterações feitas na psata selecionada

///////////////////////////////////////////

HTTP - Hyper Text Transfer Protocol
Protocolo de transferencia de hypertexto

///////////////////////////////////////////
URI - Uniform Resource Identifier

Se podemos identificar, nomear, endereçar ou manipular, estamos falando de um recurso

 ------ Conceito
Usa do para idenficar recursos pelo nome ou localização

Exemplo: Eu sou um recurso, caso eu precise me procurar, irie procurar pelo meu nome ou endereço



 ------ Recurso 
 O recurso é o alvo do meu pedido, exemplo, se eu coloco no browser google.com, goolge.com é o meu alvo/recurso

 Tipos de recursos:
 Digital, exemeplo, email, pois nãos se acessa um email atraves de um HTTP e sim atráves de um mailto

 Abstrata, exemplo, sessão/login um recurso abstrato nescessita de um caminho/autenticação/endereços para poder acessar o recurso

Fisicos, exemplos, produtos/usuarios



---------Locator

 URL - Uniform Resource Locator

 Usado para acessar recursos atraves do endereço
 Toda URL será uma URI, mas nem toda URI será uma URL


 Componentes
URL tem dois componentes OBRIGATORIOS sendo eles um protocolo e um dominio

exemplos:
https://www.rocketseat.com.br/blog - https seria o protocolo e o rockeatseat.com.br seria o dominio
A URL seria esse link todo, enquanto dominio é somente o rockeatseat.com.br


Componentes opcionais

Componentes opcionais são usados para especificar algum "Local" especifico que voê queira acessar

Subdominio - Vem antes do dominio

Path - https://www.rocketseat.com.br/blog - O (/blog) será o path usado para acessar um "local" especifico no site

Parametros - https://youtube.com/watch?v=vpYct2npKD8 o parametro é colocado após o path, usado geralmente para acessar arquivos tipo imagem, produto e video

Portas - É um local no servidor disponivel para eu chegar no meu recurso

Ancora - Algum lugar dentro do meu documento


-------Name

URN

Uniform Resource Name

Todo produto tem seu nome na internet e para digitarmos ele usamos URN

///////////////////////////////////////////////
HTTP MESSAGES

--------Mensagens

Tanto para request ou para response existem mensagens

--Resquest/Pedido

Request é um verbo http que diz o Method do pedido possar ser ele um
 pedido simples, um cadastro ou exclusão de algo 

//////////////////////////////////////////
Methods

Http Methods

Methods é alguma ação ou operação que o cliente deseja executar
Method pode ser chamado de verbo 

---Caracteristicas

-- Methods Seguros

GET/HEAD/OPTIONS

Não altera o estado do servidor - aqueles metodos que só recebem a resposta do servidor

--Idempotentes

Ao executar o method a resposta sempre será a mesma
Todos os Methods seguros são idempotentes (GET/HEAD/OPTIONS)
Além de PUT & DELETE

-- Não são idempotentes nem seguros

POST/PATCH
