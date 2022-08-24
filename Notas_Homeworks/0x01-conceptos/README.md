# Conceptos

### Expressions | Statements

- expression: siempre se convierte (retorna) un valor.
- statement: realiza una acción.

```
>> 1 + 1 // se resuelve a 2 (es una expresión)
<- 2
>>
```

```
>> // if 'hace algo'
>> if (condition) {
   // does something if condition is true
   } else {
   // does something if condition is false
   }
```
Como regla: si podemos ponerlo dentro de un `console.log`, es una expresión, else, es un statement.


#### Ejercicio: ¿El operador ternario es expresión o statement?

Primero, ¿cómo funciona el operador ternario?  

Syntax:  
`condition = exprIfTrue : exprIfFalse`  

```
function getFee(isMember) {
  return (isMember ? '$2.00' : '$10.00');
}

console.log(getFee(True));
// logs '$2.000'

console.log(getFee(False));
// logs '$10.00'

console.log(getFee(null));
// logs '$10.00'
// Other possible falsy expressions besides False are null, NaN, 0, "", and undefined
```

El operador ternario evalua la condición (hace algo), y retorna la expresión que corresponda.

### Declaration Statements

```
var prueba;

function suma(a, b) {
  // bloque
}
```

### Function expressions

Cuando declaramos una función, puede ser interpretada como statement o como expresión:

```
function resta(a, b) {
   // bloque
}

var resta = function (a, b) {
  // bloque
}

array.map(function()) {
  // bloque
};

(function () { // puede no tener nombre, funciones anónimas
  console.log('IIFE');
})();
```

### Conditional Statement

Sirven para controlar el flujo de ejecución del código:

```
if (condition1) { // cualquier expresión
  // ejecuta if condition1 is true
} else if (condition 2) {
  // ejecuta if condition1 is false & condition2 is true
} else {
  // ejecuta if cond1 & cond2 son false
}
```
### Loops y Jumps

Son otras herramientas de control de flujo, pero a diferencia de los conditional statements, ejecutan un bloque de código 'n' número de veces.

```
while (condition) { // ejecuta el bloque mientras que condition siga siendo true
  // bloque
}

for (var i = 0; i < 10; i++) { // ejecuta el bloque 10 veces
  // bloque
}

function () {
  // bloque...
  return; // interrumpe en este punto la ejecución de la función
  // ... bloque continua
}

for (var i = 0; i < 10; i++) { // ejecuta 10 veces el bloque
  // bloque
  continue; // salta a la siguiente iteración del loop
  // bloque que no se ejecutará después del continue
}

throw new Error('error, se termina la ejecución');

```

### Expression Statements

Donde el intérprete espera un statement, podemos pasar una expresión. No funciona a la inversa.
