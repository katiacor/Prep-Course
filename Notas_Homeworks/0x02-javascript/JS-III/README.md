# Bucles for y arrays Parte 2

## Arrays

A diferencia de una variable, que sólo puede apuntar a una cadena, número o booleano, los arrays nos permiten almacenar colecciones de datos. Un array se declara dentro de `[]`, y separar cada valor con una `,`. Puede contener tantas cadenas como deseas. Al igual que otros lenguajes, se accede a cada elementos por medio de un íncide. Podemos conocer el número de elemntos en un array con el método `.length`, que es uno de varios métodos disponibles para manipular a los arreglos.

```
// declarar
let arr = [];

// declarar y obtener el número de elementos
const fruits = ['banana', 'lemon', 'orange', 'strawberry', 'pomegranate'];
console.log(fruits.length); // 5

// acceder a los elementos
console.log(fruits[0]); // 'banana'
console.log(fruits[fruits.length - 1]); // 'pomegranates'

fruits[2] = 'grape';
console.log(fruits); // ['banana', 'lemon', 'grape', 'strawberry', 'pomegranate']

fruits[6] = 'peach';
console.log(fruits); // ['banana', 'lemon', 'grape', 'strawberry', 'pomegranate', empty, 'peach']

fruits[3] = ['strawberry', 'blueberry', 'blackberry'];
console.log(fruits); // ['banana', 'lemon', 'grape', ['strawberry', 'blueberry', 'blackberry'], 'pomegranate', empty, 'peach']
console.log(fruits[3][1]); // 'blueberry'

fruits[5] = 'lingon';
console.log(fruits) = // ['banana', 'lemon', 'grape', ['strawberry', 'blueberry', 'blackberry'], 'pomegranate', 'lingon', 'peach']

fruits[5] += 'berry';
console.log(fruits) = // ['banana', 'lemon', 'grape', ['strawberry', 'blueberry', 'blackberry'], 'pomegranate', 'lingonberry', 'peach']

console.log(fruits[0][2]); // 'n'

console.log(fruits[0].length); // 6

// puede contener todo tipo de valores
random = [1, null, undefined, function() { console.log('Soy una función dentro de un array!') }];
console.log(random) // [ 1, null, undefined, [Function (anonymous)] ]

// puedo invocar funciones
random[3](); // 'Soy una función dentro de un array!'
```

```
// métodos incorporados push y pop

```