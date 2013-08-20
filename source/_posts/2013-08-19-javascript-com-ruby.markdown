---
published: false
author: Rafael Fiuza
layout: post
title: "Como escrever Javascript de forma divertida"
date: 2013-08-19 11:00
comments: true
categories:
  - Rafael Fiuza
  - javascript
  - Ruby
  - opal
  - opalrb
---


Javascript é uma ótima linguagem. Ela passou a ser usada e respeitada cada vez mais. Durante muito tempo ela ficou destinada a ficar somente no frontend, enquanto outras linguagens, como Ruby ficariam no backend. E muita gente estava satisfeita com isso.


Mas alguém teve uma ideia: E se colocarmos essa linguagem que somente fica no frontend no sever-side? Surgiu o Node.js.
<!-- more -->
Node.js surgiu numa época chamada de revolução do Javascript. Ficou extremamente popular e agora temos javascript em todos os lugares.

Mas o javascript, apesar de tudo, não é uma linguagem divertida. E isso é quase um consenso.
Passei as ultimas 4 semanas usando coffeescript e é muito bom. É simples, tem uma boa sintaxe que "lembra" Ruby e é suportado e encorajado no Rails. Quando voltei a escrever em "plain javascript", tive uma sensação estranha de que o js é mais complicado do que deveria.
Mas o coffeescript tem um problema. Ele é um javascript. É necessário pensar em Javascript para escrever em CoffeeScript.

Enfim, ja estava conformado com o fato de que, como alguém que se diverte programando em Ruby, js seria uma constante.

## Mas então surgiu uma luz...
Tudo mudou nas ultimas semanas, quando estava fazendo um experimento simples e precisei de um simples parseador de ruby para js. Uma das vantagens de fazer parte da comunidade Ruby é que, quase sempre, alguem ja fez algo e está praticamente pronto. Acabei encontrando a gem [Opal][opal_gem]. **E minha fé na humanidade foi restaurada.**

Opal é um compilador de Ruby para javascript, "source-to-source" com uma performance igual ao javascript escrito nativamente. Segue um exemplo:


```ruby
module Fooable 
  def work?
    super
    puts "It works!"
  end
end

class BaseBar
  def work?
    puts "YEAH"
  end  
end

class DoesIt < BaseBar
  include Fooable
  def method_missing(sym, *args, &block)
    puts "You tried to call: #{sym}"
  end
end

does_it = DoesIt.new
does_it.work?
does_it.answer_me?
```

Esse é um exemplo mostrando um pouco da capacidade do Opal em gerar codigo Javascript.
Você pode testar esse código [bem aqui][code_example].

É possivel chamar facilmente codigo javascript nativo e continuar programando como ruby:

```ruby
class Light

  def self.init
    point_light = `new THREE.PointLight(0xF8D898);`
 
    point_light.position.x = -1000
    point_light.position.y = 100
    point_light.position.z = 1000
    point_light.intensity = 2.9
    point_light.distance = 10000
    point_light
  end

end
```

Além de me sentir totalmente confortável em escrever javascript, me trouxe outra vantagem:
Todo o codigo pode ser testado de uma maneira que estou acostumado a testar:

```ruby
describe Light do

  it 'should respond to init' do
    Light.should respond_to(:init)
  end

  it "init should not be nil" do
    Light.init.should_not be_nil
  end

  describe "init" do
    before { @light = Light.init }

    it "should set x position" do
      @light.position.x.should eq(-1000)
    end
    it "should set distance" do
      @light.distance.should eq(10000)
    end
  end

end
```
Caso tenha clicado no link para testar o codigo que informei acima, deve ter notado que o javascript compilado é mostrado na janela da direita.
Concordo que não é um javascript bonito, mas é eficiente. E, atualmente, nunca vi um programador reclamar do codigo C que é gerado quando programa em Ruby. :).

Estou fortemente inclinado a acreditar que Javascript é o novo C.

[code_example]: http://bit.ly/17ChGDH
[opal_gem]: http://opalrb.org/