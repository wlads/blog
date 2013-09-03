---
layout: post
published: true
title: "Codeclimate"
date: 2013-09-02 23:46
author: Rodrigo Reginato
comments: true
categories: 
  rodrigo reginato
  codeclimate
  refactoring
  refatorar
---

Todos os dias nos desenvolvedores usamos diversas ferramentas para facilitar nosso trabalho.
Uma ferramenta que conheci recentemente trabalhando na He:labs é o [codeclimate](https://codeclimate.com).

<!--more-->

O [codeclimate](https://codeclimate.com) é uma ferramenta que analisa e ajuda a melhorar a qualidade do código, identificando métodos e classes complexas, métodos longos, duplicidades, vulnerabilidades e muitas outras coisas. 

Mais de 900 empresas de renome estão usando esta ferramenta no momento.

Ferramenta muito simples e prática de utilizar, é possível fazer um teste de 14 dias free.
O primeiro passo quando esta se cadastrando no site é vincular seu projeto no codeclimate. O repositório do projeto deve ser o github.

Escolhi um projeto bem antigo para esse teste porque sei que o codeclimate vai achar muitos problemas para mostrar o resultado da análise inicial.

![image](/images/posts/2013-09-02/codeclimate_1.png)

Cada projecto adicionado recebe uma pontuação de 0 a 4 e cada classe recebe uma nota de A a F. Esse projeto recebeu uma nota 1.07, isso quer dizer que está muito ruim e muita coisa deve ser revista.

![image](/images/posts/2013-09-02/codeclimate_2.png)

Cada push no repositório o codeclimate faz uma validação no código, qualquer problema que ele encontre, qualquer mal cheiro de código "smell", ele vai identificar.

Se uma nota de uma classe que estava A cair, imediatamente um email é disparado avisando que algo deu errado.

![image](/images/posts/2013-09-02/codeclimate_3.png)

Ai o desenvolvedor entra em ação para melhorar essa nota, nossa meta é manter todas as classes com as melhores notas possíveis.

![image](/images/posts/2013-09-02/codeclimate_4.png)

Uma opção que utilizamos, quando uma nota de uma classe cai ou melhora, é receber um aviso no [Hipchat](https://www.hipchat.com) que é disparado junto com o envio do email.

Todo código que tenho feito já imagino se o codeclimate vai reprovar ou não, fazendo com que eu faça códigos melhores sempre.
