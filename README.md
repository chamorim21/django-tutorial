## Primeiro projeto Django

### 01 - Projeto criado

Com o comando `django-admin startproject mysite` criei um diretório chamado 'mysite' contendo os arquivos necessários para começar um projeto Django.

Dentro desse diretório, criei uma aplicação chamada Polls, com o comando `python3 manage.py startapp polls`. Assim, foi criado um diretório onde abriga-se a aplicação de enquetes. 

A partir disso, criei uma view dentro de Polls e mapeei sua URL.

### 02 - Criação de models

Por optar pelo uso do SQLite, a configuração do banco de dados já veio predefinida. Dessa forma, já parti para a criação dos models usados na aplicação: Question e Choice.

Nessa aplicação de enquete, uma Question tem uma pergunta e uma data de publicação. Uma Choice tem dois campos: o texto da escolha e um totalizador de votos. Cada Choice é associada a uma Question.

Os modelos são escritos dentro de polls/models e são representados por classes comuns no Python, em que define-se seus campos e relacionamentos.

Isso fornece muita informação ao Django, sendo possível criar as tabelas e a API de acesso a esses dados de forma automática. Para isso, é necesśario revelar a informação de Polls para o Django, adicionando a referência dessas classes à INSTALLED APPS em mysite/settings.py.

Dessa forma, é possível rodar `makemigrations` para criar a migração com as alterações feitas. Essa migração será responsável por fazer as configurações mencionadas anteriormente, como criar a tabela no banco de dados.

Assim, basta rodar `python3 manage.py migrate` no diretório raiz.

#### Criação de super usuário

O superusuário tem acesso ao painel de administração do django podendo fazer várias alterações na aplicação.

Para criá-lo, é necessário rodar `python manage.py createsuperuser` e preencher as credenciais.

Com o servidor no ar, ao acessar `127.0.0.1:8080/admin` e inserir as credenciais cadastradas, consegue-se o acesso.

É possível customizar o que será exibido no painel de administração através do arquivo polls/admin.py.

### 03 - Views 

Uma view é um “tipo” de página Web em sua aplicação Django que em geral serve a uma função específica e tem um template específico.

Nessa aplicação, defini as seguintes views:

* Página de “índice” de enquetes - exibe as enquetes mais recente.
* Question “detail” page – displays a question text, with no results but with a form to vote.
* Página de “resultados” de perguntas - exibe os resultados de uma pergunta em particular.
* Ação de voto - gerencia a votação para uma escolha particular em uma enquete em particular.

A definição das views é feita em views.py, onde delega-se toda a lógica para funcionamento de uma view, englobando diversos conceitos como `response`, `request`, tratamento de erros e definição de templates.

Também, é essencial configurar as urls vinculando-as com as views, no arquivo urls.py.

#### Templates

O sistema de templates do Django serve para separar o design do código Python

Primeiro, criei um diretório chamado `` templates`` no diretório polls. O Django ficará responsável por procurar templates lá.

Os templates são escritos em HTML e têm acesso à variáveis definidas na aplicação por meio de uma sintaxe específica, sendo possível também fazer lógica de programação nos templates, com uso de if, else, for e etc.

### 04 - Formulário e views genéricas

A criação do form é feita na parte de template, dentro de um html.

Uma view se conectará com esse template, manipulando os dados submetidos pelo formulário, utilizando também, das url configuradas anteriormente.

#### Views genéricas

Estas views representam um caso comum do desenvolvimento Web básico: obter dados do banco de dados de acordo com um parâmetro passado na URL, carregar um template e devolvê-lo renderizado. Por isto ser muito comum, o Django fornece um atalho, chamado sistema de “views genéricas”.

Nesse sentido, converti a configuração de url's e fiz uma refatoração simplificando o código e permitindo maior capacidade de expansão da aplicação.

### 05 - Testes automatizados

Existe uma parte dentro da estrutura do app destinada à testes.

Dentro desse arquivo, tests.py, expus alguns bugs e criei testes para supri-los.

A execução é feita usando `python3 manage.py test polls`, sendo esse último o nome do app.

A partir disso, é possível executar os mais variados testes partindo daquilo que se deseja verificar a qualidade na sua aplicação.

### 06 - Arquivos estáticos

Para fazer com que o Django detecte os arquivos estáticos da aplicação, criei um diretório chamado static dentro de polls.

Nesse sentido, os arquivos criados dentro desse diretório puderam ser referenciados nos templates, possibilitando a inserção de estilos css e imagens, por exemplo.

### 07 - Personalização do formulário no painel de administração

Em polls/admin.py, registrei as classes do model, fazendo com que ficassem visíveis no painel de administração.

Com isso, é possível realizar as ações do sistema de forma intuitiva seguindo esse caminho.

Além de permitir o acesso, consegui fazer diversas personalizações, tais como realizar filtros e pesquisa dos registros cadastrados, tudo isso fornecido pelo Django.

Os relacionamentos entre as tabelas e as lógicas para filtro e pesquisa são pré-definidas.


## APRENDIZADO

Com esse projeto seguindo os passos da documentação do Django, pude aprender diversas coisas. Dentre estas, destaca-se a forma de trabalhar do Django, em que o framework fornece praticamente tudo que é necessário para resolução da maioria dos problemas enfrentados no desenvolvimento web.
Desde a parte de configuração do servidor, backend, base de dados, até a definição da parte visual, como os templates. Sua facilidade com as migrations também chama bastante a atenção, possibilitando alterações nos modelos de dados de forma prática.

