# Este é um dicionário de métodos de array

>Join:
Este método consegue juntar os elementos de uma array
```js
>const elements = ['Fire', 'Air', 'Water'];

console.log(elements.join());
// Expected output: "Fire,Air,Water"

console.log(elements.join(''));
// Expected output: "FireAirWater"

console.log(elements.join('-'));
// Expected output: "Fire-Air-Water"
```
>Push
Este é um meotodo para dicionar ao final da array.
```js

var esportes = ["futebol", "beisebol"];
var total = esportes.push("handebol", "natacao");

console.log(esportes); // ['futebol, 'beisebol', 'handebol', 'natacao']
console.log(total); // 4
```
>Pop:
O método pop remove o último elemento de um array e retorna aquele valor.
```js

var meuPeixe = ["acara-bandeira", "palhaco", "mandarim", "esturjao"];

console.log(meuPeixe); // ['acara-bandeira', 'palhaco', 'mandarim', 'esturjao']

var meuPeixePop = meuPeixe.pop();

console.log(meuPeixe); // ['acara-bandeira', 'palhaco', 'mandarim' ]

console.log(meuPeixePop); // 'esturjao'
```
>Keys:
O método keys() retorna um novo Array Iterator que contém as chaves para cada index do array.
```js

// Lista de livros
const livros = ["Dom Quixote", "1984", "O Senhor dos Anéis", "Orgulho e Preconceito", "Cem Anos de Solidão"];

// Percorrer os índices usando `keys()` e exibir os títulos com a posição
const iterador = livros.keys();

console.log("Lista de Livros:");
for (let index of iterador) {
  console.log(`${index + 1}. ${livros[index]}`);
}
```
>Reverse:
O método reverse() inverte os itens de um array. O primeiro elemento do array se torna o último e o último torna-se o primeiro.
```js
var myArray = ["one", "two", "three"];
myArray.reverse();

console.log(myArray); // ['three', 'two', 'one']
```


 


