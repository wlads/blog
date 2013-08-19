---
layout: post
title: "Falando sobre HAML"
date: 2013-05-08 18:42
comments: true
categories: 
  - Rodrigo Gomes
  - HAML
---



Falando sobre HAML
No meu post falarei sobre o [HAML](http://www.haml.info/),na verdade ela é uma gem que facilita toda a parte visual de uma aplicação web.
O Framework Ruby on Rails, ajuda bastante  no quesito agilidade,e por que não ser mais agil ainda não precisando ficar fechando tags do html,isso se chama criar seus estilos com mais agilidade e de forma mais legível para quem futuramente  venha mexer no seu  código.

Eu particularmente estou começando a aprender e também a  usar em alguns projetos web ,tenho mais costume com o html tradicional,aos poucos estou me acostumando,mas é bem tranquilo,ele usa as mesmas tags do HTML,mais a vantagens é que não precisa ficar fechando as tags,em vez disso você usa prefixos como % ou . para chamar as tags HTML,mais quando executado no browse o html gerado e o tradicional.

```
Antes o modo de usar era :

   'index.html'

No HAML é diferente:

   'index.haml'

```

Mostrando na  Prática, citarei dois exemplos um com o HTML tradicional e o outro no HAML.

Metodo Tradicional do html

```
<html>
         <head>
                   <title>HE:labs </title>
         </head>
         <body>
                   <h1>Meu 1 post  |  blog</h1>
          </body>
</html>

No HAML ficaria assim

%html
        %head
	      %title
		   HE:labs
                   %body
		   %h1
		         Meu 1 post  |  blog

```

Um dos cuidados que se  deve ter com o Haml é na sua indentação,ela tem que ficar de forma correta (alinhada),pois se o codigo estiver desalinhado  ele não rodará .

Correto:
```
%html
        %head
	      %title
		   HE:labs
                   %body
		   %h1
		         Meu 1 post  |  blog


Errado:
```
%html
        %head
%title
		   HE:labs
         %body
		        %h1
		         Meu 1 post  |  blog
```

Bem Mais prático e tranquilo sobrescrever o HTML com o HAML,o codigo fica mais organizado e limpo ,outra coisa que não mencionei  ,que é possivel adicionar codigo ruby dentro do HAML.

O SASS faz parte do HAML, ele consiste em criar os css de um modo prático.
de forma mais agil e legível,não é necessesário instalar nada ,porém esses procedimentos que citarei logo abaixo devem ser seguidos para que  se tenha uma boa utilização,lembrando que quando você executar o o seu projeto no browse o css vai ser interpretado de forma tradicional.

Forma tradicional do CSS

```
body{
	background-color: #000;
	font-size: 16pt;
		}'

No SASS funciona da seguinte Maneira:

'body
             background-color: #000
             font-size: 16pt

```

*Obs: Notem que não utilizamos mais o chaves,ponto e virgule e também que entre a propriedade e o valor temos um espaço.*



Adicionando o estilo ao HAML

```
= stylesheets_link_tag "nome_do_estilo"
	%html
		%head
			%title
				HE:labs  
```
##Vamos agora aprender como instalar a Gem do HAML

A instalação é bem facil,é só rodar o commando abaixo no seu terminal,temos também que adicionar a gem dentro do projeto.

```
gem install haml
```

Quando tiver feito a etapa acima rode o proximo comando que será adicionado no seu projeto.

```
haml --rails meuprojeto/app
```
Pronto você já tem o Haml instalado na sua aplicação web, agora é só usar.


Depois de executado esse comando,uma mensagem será exibida.

```
Haml plugin added to meuprojeto
```
















