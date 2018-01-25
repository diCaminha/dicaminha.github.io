---
layout: post
title: USUFRUINDO DO SPREAD OPERATOR (...) EM JS
---

Com o ES6 (ecmaScript 2015), inúmeras funcionalides foram adicionadas visando otimizar o processo de 
escrever código javascript, dando incrível dinamismo na sintax da linguagem JS. Como exemplo (e pra mim os mais importantes e/ou relevantes) temos: *Arrows*, *Classes*, tipo *constant*
e **Spread Operator**.
Nesse Artigo vou dar uma breve introdução e exemplos de uso com esse último.

##Spread Operator (...)

**Sobre**
Spread Operator é uma forma de transformar um *array* em uma sequência de parâmetros. Isso quer dizer que se
você insere o **...** antes de *meu_array*, ou seja *...meu_array*, e supondo q esse array possui 3 parametros, o método
não receberá mais apenas 1 parâmetro (meu_array), mas sim 3: meu_array[0],  meu_array[1] e  meu_array[2].

**Casos de Uso**

*1. Combinando arrays*
Há muitas formas de combinar arrays, e o spread operator veio pra ser mais uma nessa lista:
```javascript
  let array_um = [1,2,3];
  ler array_dois = [4,5];
  let array_um.push(...array_dois);
  //array_um vai receber push de 3 e depois de 4
  //array_um === [1,2,3,4,5]
```

*2. Usando nas funções de Math*
```javascript
let numeros = [9, 4, 7, 1];
Math.min(...numbers); // 1
```

*3. Transformando itens de arrays em parâmetros*
O que antes era preciso chamar apply para que pudesse desmembrar um array em valores singulares, agora com o ES6, você
precisa apenas chamar o método, passando ... e o nome do array:
```javascript
function minhaFuncao(x, y, z) { }
var args = [0, 1, 2];
minhaFuncao.apply(null, args);
```
