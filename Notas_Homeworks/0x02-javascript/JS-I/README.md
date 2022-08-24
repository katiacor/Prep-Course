# JavaScript

Creado con el objetivo de dar dinamismo a las páginas webs. Abarca Back-end a través de NodeJS.

## Conceptos

### Variables

Las variables almacenan 'data' para ser usada más tarde. En JS, una variable se puede reestablecer a cualquier tipo y no es necesario establecer su tipo al declararla (tipado dinámico). Para usarla, sólo es necesario invocar su numbre.  

Para crear una variable existen tres 'keywords':

- `var`: utilizada en ES5 (version anterior de JS).
- `let`: utilizada en ES6 (versión actual de JS). A diferencia de `var`, su comportamiento difiere al crear un "nivel de scope".
- `const`: utilizada en ES6. Es una variable cuyo valor no se puede modificar.

```
var nombre = 'Frida';
let raza = 'Boxer';
const actividadFavorita = 'Perseguir gatos';
```

`console.log`: es un método usado para imprimir en la consola todo aquello que incluyamos entre paréntesis.

### Tipos de Datos

Un 'type' es un atributo que indica la clase de datos que serán almacenados en una variable, y determina las operaciones que pueden realizarse con ellas. Los tipos de datos varían según los lenguajes, y en JS los más básicos son `strings`, `numbres`, y `booleans`.

- `string`: bloques de texto definidos entre comillas dobles o simples.
- `number`: simplemente números. Incluyen negativos y número fraccionarios (escritos con un punto).
- `boolean`: provienen del concepto de la lógica de Boole, donde el código binario alimenta a la computadora únicamente con dos opciones, `0` (verdadero) ó `1` (falso).

```
var nombre = 'Henry';
var positivo = 23;
var negativo = -31;
var floatingP = 10.5;
var noQuepo = 2.998e8;
var jsEsCool = true;
```

### Operadores

Permiten realizar operaciones con las variables. Existen diferentes notaciones para colocar los operandos.

```
var a + b  // notación infix o infija
var + a b  // notación prefix
var a b +  // notación postfix
```

#### Precedencia de Operadores y Asociatividad

La **precedencia** de operadores se refiere al orden en que se ejecutan las operaciones, según el rango de los operadores. Es decir, si tenemos más de un operador, el intérprete resuelve primero la operación con el operador de mayor precedencia.

La **asociatividad** de operadores es el orden en que se ejecutan los operadores cuando tienen la misma precedencia, ya sea de izquierda a derecha, o derecha a izquierda. Esto no debe ser confundido con el orden de ejecución de los programas.

Ejemplo con diferente procedencia:

```
console.log(3 + 4 * 5) // * tiene precedencia 15, y + 14. Se ejecuta primero la multiplicación
console.log(3 + 20)
console.log(23);
<- 23
```

Ejemplo con misma procedencia, donde la asociatividad es la que determina el orden:

```
var a = 1, b = 2, c = 3; // El signo = tiene precedencia 3 y asociatividad right-to-left, entonces
// las operaciones se realizan primero de derecha a izquierda

a = b = c
a = (b = c) // primero se realiza b = c
// todas las variables tendrán el valor 3, de c

console.log(a, b, c)
```
### Math

Los operadores matemáticos trabajan en JS tal como lo hacen en una calculadora.

```
1 + 1 = 2
2 - 2 = 0
3 * 3 = 9
4 / 4 = 1

21 % 5 = 1 // módulo devuelve el residuo de la división
```
### Objetos Globales y Métodos

JS tiene objetos integrados como `console` y `Math`, y cada objeto tiene sus propios métodos como `log` y `pow`.

```
// Math.pow(número,exponente)
Math.pow(2,2) = 4;
Math.pow(3,2) = 9;
Math.pow(3,3) = 27;
```

```
// Math.round(n) redondea al número entero más cercano
Math.round(6.5) = 7;
Math.round(6.45) = 6;

// Math.floor(n) redondea al número entero anterior
Math.floor(6.99) = 6;

// Math.floor(n) redondea al número entero siguiente.
Math.ceil(6.0001) = 7;
```

```
// length es un método para strings que devuelve la cantidad de caracteres en la cadena.
var digitos = '0123456789'
console.log(digitos.length); // logea 10, log es un método del objeto console

```

## Introducción a las Funciones

En JS, las funciones son un tipo particular de objetos llamados 'callable objects'. Existen tres formas de construir una función:

```
function myFunction() {}
var myFunction = function () {};
var myFunction = () => {};
```

En esta lección sólo utilizaremos la primer forma.

### Anatomía:

```
function functionName() {}

function sayHello(name) {
    console.log('Hello, ' + name + '!');
}

sayHello('Henry');
```

En el código anterior, `function` avisa al intérprete que está tratando con una función, `functionName` debe describir claramente lo que hace esta funcion, y `{}` lleva el bloque de código a ejecutar cada vez que la función es llamada.

Otra forma de incluir la variable `name` al imprimir:

```
function sayHello(name) {
    console.log(`Hello, ${name}!`);
}

sayHello('Henry');
```

### Declaración 'return' y Scope

La declaracíón 'return' es la forma de acceder a lo que una función devuelve, desde otra parte del programa. Cuando una la ejecución de una función se encuentra con un 'return', la ejecución se detiene por completo devolviendo lo especificado.

```
function divide(a, b) {
var result = a / b;
return result;
}

divide(6, 3); // 2
console.log(producto); // undefined
```

En el último ejemplo, estamos intentando imprimir una variable que fue definida dentro del scope de la función. Nos devuelve *undefined* porque desde ese punto no tenemos acceso a dicha variable.

Podemos también declarar variables y definirlas igualando al valor que devuelve alguna función.

```
function resta(a, b) {
    var difference = a - b;
    return difference;
}

var rebanadas = resta(8, 5);
console.log(rebanadas); // 3
console.log(difference); // undefined
```

## Control de Flujo y Operadores de Comparación

El 'control flow' se refiere a la forma en que una función verifica si algo es `true`. Se forma una declaración, y si es 'true' el código dentro de esa declaración se ejecuta, si no es así, la ejecución continua en el siguiente paso.

```
function canDrive(age) {
    if (edad >= 18) {
        return true;
    }
    return false;
}

canDrive(18); // true
```

## Más Lecturas

[CodeCademy: Learn Javascript](https://www.codecademy.com/learn/learn-javascript)  
[Udacity: Intro to Javascript](https://www.udacity.com/course/intro-to-javascript--ud803)  
[MDN: Official Javascript Documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
