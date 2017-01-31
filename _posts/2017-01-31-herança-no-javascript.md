---
layout: post
title: Herança no JavaScript
date: 2017-01-30 00:43:41 -0300
description: Artigo destinado a explicar e comentar sobre herança na linguagem de programação JavaScript.
---
Olá, como vocês estão? Espero que estejam bem. :}
Então, todos nós em algum momento durante os estudos na linguagem de progrmação javascript ouvimos falar que o termo herança funciona um pouco diferente que em outras linguagens que atendem o paradigma de Programação Orientada a Objetos. Pois é, é isso mesmo, em JS a coisa é um pouquinho diferente e nesse post vou escrever sobre isso. Então vamos lá...

A herança acontece através dos então chamados __prototypes__ dos objetos, ou seja, o objeto tenta encontrar uma propriedade sua, mas não a encontra, então ele procurará em seu __prototype__, se ainda não encontrar, irá procurar no __prototype__ do seu __prototype__ e assim por diante até encontrar a propriedade ou essa "corrente", que é chamada de __prototype chain__, acabar.

```js
newObj => prototype => prototype.prototype ... // até que a "corrente" acabar.
```

Todos os objetos em JavaScript possuem um link interno para outro objeto, seu __prototype__, que por sua vez também tem um link interno para ourto objeto __prototype__, ou seja __Prototype.prototype__, assim por diante até __null__ ser encontrado, __Prototype.prototype.null__, significando que esse objeto não possui __prototype__, ou seja, esse objeto é o final da __prototype chain__.

Em ES podemos simular __métodos__ através de funções em um objeto em forma de propriedade, ou seja, ```func: function () {}```. Quando outro objeto herda uma função, ou seja, herda o método de um objeto, o __this__ (que em ES confundo um pouco os desenvolvedores) aponta para o objeto que herda o método e não para o __prototype__ onde o método foi criado. 
Vamos para um exemplo:

```js
var animal = {
	numeroPatas: 4,
	patas: function () {
		return this.numeroPatas;
	}
}

console.log(animal.patas()); // 4

var galinha = Object.create(animal);

galinha.numeroPatas = 2;

console.log(galinha.patas()); // 2
//prototype chain fica:
//objeto galinha => animal => Object.prototype => null
```

No código acima o __this__ do objeto galinha aponta para o __numeroPatas__ do objeto galinha, propriedade herdada, e não para o __prototype__ onde a propriedade foi escrita.

Recapitulando: ```let obj = new Object();``` o objeto obj herda o prototype de Object: __Object.prototype__. E ```let obj = new City();``` o objeto obj o __prototype__ de City, ou seja, __City.prototype__, então quando utilizamos a __função construtora__ para criar o objeto, o objeto em questão herda o __prototype__ do seu __construtor__.

Mas opa: O que é __construtor__?
É uma função que criamos para iniciar novos objetos e para chamar o construtor você utiliza a palavra reservada __New__.

No ES6 foi adicionado as features __class__ e __extends__. A __class__ você utiliza para criar uma classe com seus métodos e propriedades e pode utilizar a feature __extends__ para herdar essas propriedades e seus métodos.

```js
class Newclass {
	//código que compoe sua classe
}

class Otherclass extends Newclass {
	//código que compoe sua classe
}
```

Se tiver alguma dúvida ou quiser contribuir com algo, por favor, deixe seu comentário e vamos conversar. ;)

Até a proxima.