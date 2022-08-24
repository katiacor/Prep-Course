# JavaScript II

### Instrucciones

- En un archivo de texto separado que debes crear, escribe explicaciones de los siguientes conceptos como si se lo estuvieras explicando a un niño de 12 años. Hacer esto te ayudará a descubrir rápidamente cualquier agujero en tu comprensión.
    - for
    - &&, ||, !

- Desde la carpeta Prep en la carpeta donde clonaste el repo, ingresa el comando npm test JSII.test.js para correr los tests automatizados. Al principio, todos los tests estarán fallados/rotos. Encontrarás las funciones para hacer pasar los tests en el archivo homework.js.

<br>

## Flujos de Control, Operadores Lógicos, Bucles for

<br>

### Undefined y Null

Los valores especiales `undefined` y `null` se escriben sin comillas, al igual que los booleanos `true` y `false`. Son objetos específicos que no pertenecen a ningún tipo de dato que hemos visto. Cuando una variable aún no tiene un valor, pero existe, obtendrás un valor `null`. Esto quiere decir que un desarrollador ha configurado la variable y la ha dejado vacía, o está especificando que su valor es desconocido. Por otra parte, obtendrás `undefined` cuando intentas acceder a un valor que no ha sido asignado aún, por lo tanto, si declaras una variable, pero no le has asignado ningún valor, obtendrás `undefined`.

```
var age = null;
console.log(age);  // undefined

var name;
console.log(name); // null
```

Aunque es posible asignar `undefined`, en práctica normalmente uno asigna `null` para indicar un valor vacío o no conocido a una variable. Así, `undefined` queda reservado como un valor por default para objetos no asignados.

<br>

### Veracidad

Todas las operaciones de comparación regresan un tipo booleano (`true` para 'yes' o 'verdadero' y `false` para 'no' o 'no verdadero'). Una comparación puede ser asignada a una variable, tal como se asignaría cualquier otro valor:

```
var isTrue = 5 > 4;
console.log(isTrue)           // true

var compareLetters = 'Z' > 'A';
console.log(compareLetters); // true

var compareWords = 'Glow' < 'Glee';
console.log(compareWords);   // false
// Note: JS evalua letra por letra y se detiene una vez encuentra dos valores distintos ('o' no es mayor que 'e').
```

Cuando se ejecuta una declaración que espera un valor booleano (`if`, `!`, `NOT`, etc), y la expresión no es un valor booleano (`true` o `false`), JavaScript transforma el valor recibido a un valor booleano. Esa transormación se conoce como **type coercion**. Cada tipo de dato tiene una veracidad, pero en general, podemos decir que todos los valores son 'truthy', a menos que estén definidos como 'falsy', es decir: `false`, `0`, `-0`, `On`, `""`, `null`, `undefined`, `NaN`.

<br>

## Operadores de Comparación Parte 2

Anteriormente revisamos los operadores `>`, `>=`, `<`, `<=`, `===`, y `!==`, que funcionan tal cual lo harían en una operación matemática para evaluar dos expresiones. Si la declaración es verdadera, devolverá `true`.

En JavaScript existe el operador `===` que no tiene relación con un signo `=`, utilizado para asignación de valores. El triple igual compara dos elementos para saber si además de tener el mismo valor, comparten el mismo tipo de dato.

También existe el operador `==` que igualmente evalua dos elementos, pero éste no toma en cuenta sus tipos de datos. Por esto, en JavaScript se considera una buena práctica utilizar siempre el `===`.

```
1 === 1   // true
1 === '1' // false
```

---

Existe el tipo "NOT" que en JavaScript escribimos asi: `!`. Este signo se utiliza para evaluar si algo es falso, y al contrario que `===`, este operador devuelve `true` si los elementos que se evaluan **NO** son iguales. Al igual que el triple igual, evalua el tipo de dato:

```
1 !== 1;    // false
1 !== '1';  // true
```

<br>

## Flujos de Control Parte 2

El operador `if` se utiliza para formar un bloque de código que será ejecutado sólo si la expresión entre paréntesis es verdadera. También existe la declaracion `else if`, que se utiliza después del operador `if` para definir un bloque de código que se ejecutaría de ser verdadero, y de ser falso el bloque `if`. Puede encadenrse más de un `else if`, pero debe cerrarse con una declaración `else`. Se evaluan una por una las declaraciones hasta encontrar una que sea verdadera. Las demás serán omitidas. Si ninguna bloque `if` o `else if` es ejecutado antes de llegar al `else`, entonces el código dentro de `else` será el único que 'correrá'.

```
if (false) {
    console.log("Este código será omitido);
} else if (true) {
    console.log("Este código correrá");
} else if (true) {
    console.log("Este código NO correrá");
} else {
    console.log("Este código tampoco correrá");
}
```

<br>

## Operadores Lógicos

Existen cuatro operadores lógicos en JavaScript: `||` (OR), `&&` (AND), `!` (NOT), `?` (??). Los operadores lógicos son elementos que nos permiten evaluar dos expresiones, al igual que el operador de igualdad `===`. A pesar de su nombre, podemos aplicarlos a valores de cualquier tipo, y no sólo booleanos.

<br>

### || (OR)
En programación clásica, el operador OR manipula dos valores booleanos, y si alguno de los dos argumentos es verdadero, entonces devuelve `true`, de otra forma devuelve `false`.

En JavaScript, este operador es un poco distinto, pero más poderoso. En JS, el operador NOT devuelve `true` siempre, excepto cuando ambos lados de la operación son falsos.

```
true  || true  // true
true  || false // true
false || true  // true
false || false // false

// Si los operandos no son booleanos, JS los convierte a boolean para evaluar
if (1 || 0) {
    console.log('truthy!');
}

if (hour < 18 || hour > 6 ) {
    console.log("It's JS time!");
}
```

En resumen, el operador NOT es ideal para verificar si cualquiera de los statements es verdadero.

En JavaScript, este operador tiene además otras características. 'NOT' evalua de izquierda a derecha, y tan pronto como encuentra un `true` statement, devuelve el valor original de dicho operando. Si todos los operandos ya fueron evaluados, y resultaron `false`, entonces devuelve el valor del último operando.

```
alert(1 || 0);                 // 1 (1 is truthy)
alert(null || 1);              // 1 (1 is the first truthy value)
alert(null || 0 || 1);         // 1 (the first truthy value)
alert(undefined || null || 0); // 0 (all falsy, returns the last value)
```

Puede ser útil para formar una lista de casos y devolver un caso default, como se muestra abajo. Buscará una variable que no sea 'falsy', y si no encuentra ninguna, la opción por default "Anonymous" será devuelta:

```
var firstName = "";
var lastName = "";
var nickName = "SuperCoder";

alert( firstName || lastName || nickName || "Anonymous"); // SuperCoder
```

<br>

### && (AND)

En programación clásica, AND devuelve `true` sólo si ambos operandos son 'truthy', de otra forma, `false`. Como ambos operandos deben ser verdaderos, si el primer operando es falso, el segundo ya no es evaluado:

```
true  && true  // true
false && true  // false
true  && false // false
false && false // false

// ejemplo
var hour = 12;
var minute = 00;

if (hour == 12 && minute == 00) {
    alert("Es medio día");
}

// cualquier valor es un operando válido
if (1 && 0) {
    alert("I won't work!");
}
```

En JS, si se proporcionan más de dos operandos con operador `&&`, se evaluan los operandos de izquierda a derecha convirtiéndo cada uno a booleano. Si el resultado de un operando es `false`, devuelve su valor original; si todos han sido evaluados como 'truthy', devuelve el último operando.

> Nota: La precedencia de 'AND' es mayor que la de 'OR'. Por lo tanto:  
> `a && b || c && d` es lo mismo que `(a && b) || (b && c)`.  

> Nota 2: NO debe usarse `&&` como una forma más corta de escribir un `if`:  
> ```  
> let x = 1;  
> (x > 0) && alert("Greater than zero!");  
> ```  
> El operando de la derecha se ejecutaría sólo si llega a ser evaluada (sólo si `x > 0` es `true`).

<br>

### ! (NOT)

El operdaor booleano 'NOT' acepta un sólo argumento y opera de la siguiente forma:
- Convierte el operando a booleano.
- Devuelve el valor inverso.

```
console.log(!true); //false
console.log(!0);    //true
```

Un doble NOT (`!!`) se utiliza para convertir un valor a tipo booleano:

```
console.log(!!"non-empty string"); // true
console.log(!!null);               // false
```

El primer `!` convierte el valor a booleano y devuelve el inverso, y el segundo `!` lo invierte de nuevo. Sin embargo, existe una función integrada que hace la conversión por nosotros, y resulta más comprensible:

```
console.log(Boolean("non-empty string")); // true
console.log(Boolean(null));               // false
```

<br>

## Bucle *for*

Los bucles *for* una sintaxis similar a la de *if*, pero aún más compleja:

```
for (let i = 0                 ;i < 10         ;i++) {
//  ---------------------------------------------------------
//  |Declaración que se        |Expresión      |Incremento  |
//  |ejecuta una sola vez      |condicional    |de variable |
//  ---------------------------------------------------------
    console.log(i); // bloque que se ejecuta mientras la condición se cumpla
}
```

El bloque dentro del `for` se ejecutará primero para el valor inicial declarado de `i` (`i = 0`). Al terminar el bloque, el contador `i` se incrementa en uno (`i = 1`). El bucle `for` evalua la expresión condicional para el nuevo valor de `i` (`1`), y ejecuta el bloque de código si ésta se cumple (`i < 10` ?); de otra forma el bucle se termina. Como `i` siempre será mayor que cero, estamos ante un bucle infinito.

<br>

## Arguments

Si conocemos el nombre del argumento que recibe una función, podemos utilizar este argumento llamándolo por su nombre:

```
function log(str) {
    console.log(str);
}
log('Hello'); // Hello
```

Si este no es el caso, podemos utilizar la propiedad `arguments`, que es propia de toda función, y contiene los parámetros pasados como argumentos:

```
> function args() {
      console.log(arguments);
  }

> args('arg0', 'arg1', 'arg2');
< Arguments(3) ['arg0', 'arg1', 'arg2', callee: ƒ, Symbol(Symbol.iterator): ƒ]

> args.length
< 0     // **porque no se definió ningún parámetro
```

La propiedad `arguments` nos da acceso a la *n* cantidad de parámetros.

> Nota: arguments NO devuelve un arreglo.  

> **Nota2: podemos conocer la cantidad de parámetros que recibe una funcion con `<functionName>.length`.  

<br>

# Temas adicionales

## Switch y Do While

<br>

# Glosario

Existen 8 tipos de dato básicos en JavaScript

Siete tipos de dato primitivos:
- `number` for numbers of any kind: integer or floating-point, integers are limited by ±(253-1).
- `bigint` for integer numbers of arbitrary length.
- `string` for strings. A string may have zero or more characters, there’s no separate single-character type.
- `boolean` for `true`/`false`.
- `null` for unknown values – a standalone type that has a single value `null`.
- `undefined` for unassigned values – a standalone type that has a single value undefined.
- `symbol` for unique identifiers.

Y un tipo de dato 'non-primitive':
- `object` for more complex data structures.

<br>

# Recursos Adicionales

[MDN: Switch](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Statements/switch)  
[MDN: Do While](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Statements/do...while)  
[MDN: Comparison Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Comparison_Operators)  
[MDN: Control Flow](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/if...else)  
[MDN: Logical Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_Operators)  
[MDN: for Loops](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for)