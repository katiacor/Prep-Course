# JavaScript IV: Objetos

## Objetos

Como hemos visto, en JS hay ocho tipos de datos, siete de ellos son **primitivos**, y el octavo tipo son los **objetos**. Estos nos permiten, a diferencia de los primitivos, almacenar una colección de datos en la forma `key: value`.  

La clave o *key* funciona como un identificador, mientras que el valor o *value* es el valor almacenado en esa key. Los objetos, entonces, nos permiten crear un objecto con propiedades (keys) y valores (values).

### Sintaxis

Los objetos permiten contener muchos pares key-value, y deben ir separados por una coma (sin punto y coma al final de cada key-value). Las claves deben ser strings únicas dentro de un mismo objeto, mientras que los valores pueden ser compartidos por una o más claves.

Los valores pueden ser cualquier tipo de dato de JavaScript: array, number, string, boolean, function, null, undefined, e incluso otro objeto:

```
let dog = {
    name: 'Frida',
    age: 10,
    breed: 'Boxer',
    activities: ['sleep', 'fart', 'fetch the ball'],
    woof: function() {
        console.log('Woof!');
    },
    isHappy: true,
};
```
Acceder a los objetos puede hacerse por medio de *dot notation* o *bracket notation* (Nota: ésta última como lo hacíamos con los arrays, que realmente son un objecto que almacena valores y asignan índices a cada uno):

```
dog['age'];     // 10
dog['name'];    // 'Frida'  -> devuelve el valor almacenado en key.
dog.name;       // 'Frida'
dog['name'][0]; // 'F' 
dog.woof();     // 'Woof!'
```

Agregar propiedades al objeto:
```
dog['sayHi'] = function() {console.log('Hi!)};
dog.sayHi(); // 'Hi!'

dog['sayHi'] = function() {console.log("Hi, I'm " + dog.name + "!")};
dog.sayHi(); // 'Hi, I'm Frida!'
```

Ventajas de dot notation:
- Es muy fácil acceder a una propiedad a través de dot notation.
- No es posible acceder a un key, a menos que se escriba el nombre directamente. No recibe una variable con la propiedad como string.

Ventajas de bracket notation:
- Es posible pasar una variable como argumento cuyo valor sea una cadena con el nombre de una propiedad del objeto.

```
let property = 'name';
console.log(dog.property);  // undefined
console.log(dog[property]); // 'Frida'
```

Eliminar propiedades:
```
dog.meow = false;
delete dog.meow;     // para muchos no se considera una buena práctica
dog.meow = undefine; // algunos consideran esto una mejor opción
```

> Nota:  
> Si quieres iterar sobre las propiedades sin considerar sus valores, puedes usar:  
> `Object.keys(<myObject>)`  // [ 'key1', 'key2', 'key3, 'keyn'... ]  
> `Object.getOwnPropertyNames(<myObject>)`  // [ 'key1', 'key2', 'key3, 'keyn'... ]  
> Los anteriores devuelven una lista de propiedades ennumerables del objeto.

## This

El keyword `this` se refiere a los métodos y propiedades de los objetos y nos permite escribir código que sea escalable, es decir, que permite, por ejemplo, desarrollar métodos que pueden reutilizarse en otros objectos:

```
persona = {
    nombre: 'Jack',
    saludar: function() {
        console.log("¡Hola, soy " + this.nombre + "!");
    },
}

console.log(persona.nombre); // 'Jack'
persona.nombre = 'Jackie';
console.log(persona.nombre); // 'Jackie'
```

## Bucles for...in

El loop `for...in` sirve para iterar sobre cada par `key-value` de un objeto. A diferencia de las matrices, que tienen un índice como `key`, los objetos tienen una string única, por lo tanto, no podemos iterar sobre ellos como lo hacemos con las matrices por medio de un loop `for`. La sintaxis:

`for (let <varName> in <objectName>) {<code block>}`

```
> for (let elemento in usuario) {
... console.log(elemento + ': ' + usuario[elemento]);
... }
username: katia.corona
favoriteNumber: 23
password: pass123
lovesJavaScript: false
```
> Notas:  
> - Las `keys` pueden ser asignadas como un integer, pero serán reconocidas como una string.  
> - El loop `for...in` ignora el orden en que fueron declarados los pares `key-value` si éstos incluyen números enteros,  
> y primero los enteros de forma ascendente, para continuar con los demás en la misma forma en que fueron definidos.  
> - Por lo anterior, el loop `for...in` recorrerá todas las keys que sean `integers`, antes de recorrer todas las demas.
> ```
> > const o = {3: 'three', 2: 'two', zeta: 'letra z', a: 'letra a'};
> > for (const element in o) {
> ... console.log(element + ': ' + o[element]);
> ... }
> 2: two
> 3: three
> zeta: letra z
> a: letra a
> ```

## this y el Execution Context

### Contexto Global
El contexto global puede referirse al caso especial en que ejecutamos código afuera de cualquier función. En estos casos, `this` hace referencia al objeto `global`. Por lo tanto, `this` fuera de una función y ejecutado en un browser, por ejemplo, haría referencia a `window`.

```
> console.log(this = window);
< true

> this.a = 23;
> console.log(window.a);
< 23
```

### Contexto Función
Cuando se ejecuta `this` dentro de una función, su valor depende de la forma en que fue invocado el método o función.
```
> function ejemplo() {
      return this; // devuelve una referencia al objeto que invoca la función
  }

> ejemplo() === window; 
< true

> window.ejemplo() === window;
< true
```

> Nota: Si utilizamos `strict` mode en JavaScript, el ejemplo anterior devolvería `undefined`, ya que no asumiría que `this` es el objeto global.

## this Como Método de un Objeto
Como hemos visto, en el contexto de una función `this` hace referencia a el objeto desde el que se llama al método. De esta forma, no importa dónde fue definida la función, sólo importa que la función sí haya sido invocada como método de un objeto.

```
> var steak = {noise: 'tsss'};  // definimos un objeto steak con una propiedad noise

> function makeNoise() {    // definimos una función makeNoise que devuelve el valor de la propiedad noise de un objeto
... return this.noise;
... }

> steak.makeNoise()     // aún no podemos utilizar la función makeNoise con el objeto steak porque no forma parte de sus métodos
TypeError: steak.makeNoise is not a function

> steak.makeNoise = makeNoise;      // agregamos la función para que forme parte de la 
> steak.makeNoise()
< 'tsss'
```

El keyword `this` puede resultar en errores, ya que al ejecutar una función con `this`, el resultado no depende de dónde fue definida la función, sino de la forma en que realizamos la llamada con `this`. Para tener mayor control sobre las referencias de `this`, existe un patrón que consiste en guardar al objeto que está en `this` antes de entrar a una función donde no se sabe a ciencia cierta qué valor puede tomar.

```
var obj = {
    nombre: 'Objeto',
    log   : function() {
        this.nombre = 'Cambiado';   // aquí, this se refiere a obj pues se está usando dentro de un método de obj
        console.log(this);          // sigue refiriéndose a obj

        var that = this;            // guardamos la referencia antes de entrar a una función dentro del mismo método obj

        var cambia = function(str) {
            that.nombre = str;      // usamos la referencia a this a través de una función dentro del método de obj
        }
        cambia('Hola!');            // devuelve-> { nombre: 'Cambiado', log: [Function: log] }
        console.log(this);          // devuelve-> { nombre: 'Hola!', log: [Function: log] }
    }
}
```

De esta forma nos aseguramos de que tenemos una forma de referirnos a `obj`, guardando una referencia en un punto donde estábamos seguros the que `this` apuntaba a él. Una vez hicimos eso, nos aseguramos de utilizar nuestra referencia `that`en lugar de la contra intuitiva `this`.

## Objetos en JavaScript
> ### Everything is an object:  
> Los arrays son objetos cuyas `keys` son un índice de 0 a n.  
> Los `string` son objetos con métodos incorporados como `.length`.  
> Las funciones son objetos con sus propias propiedades especiales.  
> El tiempo de ejecución de JavaScript es un objeto.  
