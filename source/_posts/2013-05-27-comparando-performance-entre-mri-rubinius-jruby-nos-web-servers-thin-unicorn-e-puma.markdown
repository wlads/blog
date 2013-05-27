---
author: Rodrigo Pinto e Pedro Nascimento
layout: post
title: "Comparando performance entre mri, rubinius, jruby com thin, unicorn e puma."
date: 2013-05-27 00:05
comments: true
categories:
  - ruby
  - web server
  - unicorn
  - puma
  - jruby
  - mri
  - rubinius
  - thin
  - pedro nascimento
  - rodrigo pinto

---

Performance sempre foi um tema presente na comunidade Ruby e Rails ao longo dos últimos anos. Podemos até considera que foi por causa dos comentários do Alex Payne por volta de 2007, que "sugeriu" que rails não escalava o Twitter, uma situação peculiar e controversa, que criou uma falácia de que "Rails não escala".

Se você é novo no mundo Ruby/Rails talvez nunca tenha escutado, porém para quem está a algum tempo nesse ecossitema, conhece e sabe que essa falácia já foi desfeita e nesse post não iremos falar sobre escalar uma aplicação, mas sim como tirar melhor proveito fazendo uma combinação de versão de Rubies e Web Servers através de um comparativo.

<!-- more -->

![Performance](http://farm9.staticflickr.com/8012/7705125388_e79019c9c2_z.jpg)

A maior parte dos projetos construídos na [HE:labs][he] atualamente são/foram feitos em Rails normalmente utilizando MRI 1.9.3 e o unicorn como servidor. Recentemente começamos a trabalhar em uma prova de conceito(PoC) para um novo projeto onde performance fará uma grande diferença. Existem diversas formas de alcançar/melhorar performance em um aplicativo, e para começarmos a validar algumas hipósetes fizemos uma série de experimentos com algumas das opções de implementações do Ruby e web servers disponíveis e que acreditamos que poderiam gerar os melhores resultados.

Depois de os testes feitos, queríamos compartilhar com você os números que chegamos , então decidimos refazer os testes em um cenário mais clean. Para isso, fizemos alguns testes de performance entre 3 implementações do Ruby. O MRI 2.0.0-p195, JRuby 1.7.4 e Rubinius(rbx) 2.0.0 rc1, fazendo deploy das apps nos servidores [Thin][thin], [Unicorn 4.6.2][uni], [Puma 2.0.1][puma].

Após definir, criamos uma app chamada [benchmark_rails][app] que possuí uma única action que lista 153 personagens dos Simpsons que estão no banco de dados.

![Os Simpsons](http://upload.wikimedia.org/wikipedia/en/3/33/All_Simpsons_characters.jpg)
<small>http://en.wikipedia.org/wiki/List_of_recurring_characters_in_The_Simpsons</small>


Abraços,<br/>
[Rodrigo](http://twitter.com/rodrigoospinto) e [Pedro](http://twitter.com/lunks)

[he]: http://www.helabs.com.br
[uni]: http://unicorn.bogomips.org/
[puma]: http://puma.io
[thin]: http://code.macournoyer.com/thin/
[app]: https://github.com/Helabs/benchmark_rails
