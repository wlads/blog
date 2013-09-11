---
published: true
author: Mikael Carrara
layout: post
title: "Design Responsivo Parte III: Viewports"
date: 2013-09-11 10:00
comments: true
categories:
  - design
  - css
  - design responsivo
  - mikael carrara
  - media queries
  - viewports
---

Em computação gráfica a *viewport* nada mais é do que uma região de vizualição retangular. Dentro do contexto do design responsivo é o nome dado para à região disponível onde a interface web será renderizada.

<!-- more -->

Quando não configuramos a *viewport* o que acontece? A interface simplesmente assume sua renderização nativa para *desktop*. Mesmo um iPhone 5, por exemplo, tendo **480px** de largura no modo *landscape*, exibe uma interface de **980px** (sites de **960px** ou **980px** de largura) tranquilamente, pois a largura da sua resolução é de **1136px** (**980px** dentro do iOS safari). Então precisamos prestar atenção para não confundirmos resolução com largura de tela.

Mas é um pouco estranho quando você entra em um site pelo smartphone e todos seus elementos e componentes estão miniaturizados (*zoomed-out*), exatamente uma versão pequena do site. Mesmo podendo dar zoom, é mais interessante para o usuário ter uma experiência otimizada para o dispositivo que ele esta usando.

Mesmo que já tenhamos desenvolvido nossa interface otimizada para mobile através das *Media Queries* (leia as partes <a href="http://helabs.com.br/blog/2013/02/27/design-responsivo-parte-i-arquivos-css-e-breakpoints/">I</a> e <a href="http://helabs.com.br/blog/2013/05/24/design-responsivo-parte-ii-listagens-e-galerias/">II</a> também da série Design Responsivo) os browsers ainda vão renderizar a interface no modo nativo e ocupar toda a resolução possível do dispositivo e é assim que deve ser, pois sem a otimização para design responsivo, o browser entende que você quer poder ver toda a interface e não apenas um pedaço dela e a exibe como no *desktop* mesmo.

Usando a meta tag *viewport*, os browsers vão interpretar que a interface não é para *desktop*, então vão customizar a resolução nativa do dispositivo. No caso do iPhone 5, **1136px**. Em outras palavras, se a "versão mobile" (**480px** de largura no *landscape*) da interface for renderizada no iPhone 5, a *viewport* vai personalizar a vizualização para que os **480px** de largura ocupem todos os **980px** de resolução.

No **head** do seu documento HTML declare a metatag *viewport*:

```html
<meta name="viewport" content="">
```

Dentro do atributo content você pode setar alguns valores: **width**, **height**, **initial-scale**, **maximum-scale**  e **user-scalable**.

Antes era comum configurarmos apenas a largura de **480px** ou **320px** na *viewport* pois não tínhamos muitas variações de larguras e resoluções mobile que considerávamos. Se você quisesse uma interface mobile de **320px** bastava setar:

```html
<meta name="viewport" content="width=320">
```

Mas agora com a infinidade de diferentes dispositivos e considerando que temos uma interface com o *box-model* e seus componentes flexíveis, definimos o **width** (largura) da *viewport* da seguinte forma:

```html
<meta name="viewport" content="width=device-width">
```

Ou seja, a *viewport* tem como **width** a própria largura do aparelho (**device-width**). A meta tag *viewport* foi uma solução implementada rapidamente pela Apple no iPhone e em seguida adotada pelos outros dispositivos e browser, infelizmente nunca foi uma recomendação do W3C. A Microsoft esta tentando ir na mesma direção que os padrões W3C e no IE10 ignora a meta tag *viewport* no *Snap Mode* (versão normal do browser sem a nova UI do Windows 8). Ironicamente Microsoft esta nitidamente apostando no futuro com total suporte para CSS3 e HTML5. Quem sabe?

No futuro e atualmente no IE10 a *viewport* é configurada dentro do arquivo CSS com **CSS Device Adaptation** (falarei um pouco mais sobre isso em um futuro post). Usaremos então a **@viewport rule**:

```css
@viewport{
  zoom: 1.0;
  width: extend-to-zoom;
}
```

Mas como ainda é um padrão em desenvolvimento, O IE10 requer uma especificidade a mais:

```css
@-ms-viewport{
  zoom: 1.0;
  width: extend-to-zoom;
}
```

Claro que isso ainda está longe de ser um padrão suportado por todos, mas para dar suporte ao IE10, certifique-se de configurar dessa forma também, o que me parece ser uma solução bem mais elegante do que no HTML e vai de acordo também com o conceito de "Separação de Interesses" (separar o código em camadas) bastante defendida entre desenvolvedores sérios.

Mas ainda não acabamos. Podemos e devemos também configurar para que tenhamos certeza que a interface seja renderizada corretamente em sua escala **1:1** e assim evitar que o comportamento nativo *zoomed-out* funcione.

```html
<meta name="viewport" content="initial-scale=1">
```

Não é muito bom desabilitar o zoom através do **user-scalable=NO** e nem setando também **maximum-scale=1** e **initial-scale=1** simultaneamente pois isso afeta diretamente a acessibilidade da interface. Tira a possibilidade do usuário poder ampliar determinado elemento para enxergar melhor, algo comum até mesmo para pessoas com ótima visão. Então certifique-se que o zoom ainda funciona, ele é uma característica nativa dos dispositivos mobile e o usuário deve poder usá-la para otimizar sua experiência.

Juntando tudo ficaria assim:

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

Infelizmente isso "buga" no iOS Safari quando usado no modo *landscape* então para não termos que apelar para o Javascript (se tiver interesse, tem o **ios-orientationchange-fix.js**), apenas sumimos por completo com **width** ou **width=device-width** ficando apenas:

```html
<meta name="viewport" content="initial-scale=1">
```

Se o bug do iOS Safari continuar, adicione no CSS:

```css
html, body {
  width: 100%;
  overflow-x: hidden;
}
```

Dedique um tempo para testar diferentes tipos de configurações em diferentes dispositivos e browsers para entender melhor como funciona a renderização com *viewports* customizadas. No próximo post da série Design Responsivo falarei um pouco mais sobre **Media Queries**.


## Outros posts da série

[Design Responsivo Parte I: Arquivos CSS e Breakpoints](http://helabs.com.br/blog/2013/02/27/design-responsivo-parte-i-arquivos-css-e-breakpoints)

[Design Responsivo Parte II: Listagens e Galerias](http://helabs.com.br/blog/2013/05/24/design-responsivo-parte-ii-listagens-e-galerias/)

## Links

- [Site Pessoal](http://www.mikaelcarrara.com)
- [Linkedin](br.linkedin.com/in/mikaelcarrara/)
- [Portfólio no Dribbble](http://dribbble.com/mikaelcarrara)
