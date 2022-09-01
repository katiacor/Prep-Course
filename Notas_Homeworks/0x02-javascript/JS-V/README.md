# Classes and Prototypes

JS no proporciona realmente un sistema de clases, pero tiene algo muy familiar. En la revisión ES5 de este lenguaje, el keyword `class` aún no estaba soportado, o al menos no ampliamente. Es importante notar que con la revisión ES6 sí se incluye y soporta el keyword `class`, aunque para algunas herramientas como React.js y Vue.js, se tienen que usar plugins como Babel para asegurarse de que se transpile el código de ES6 a ES5, así se asegura de que casi la totalidad de los buscadores y compiladores/transpiladores puedan ejecutar el código. Por eso es importante conocer y entender cómo funcionan las clases en JS ES5.

## Class

En JS una clase es un modelo o una plantilla que se utiliza como base para representar entidades o conceptos. Por ejemplo, puedo crear una clase `Perro`, con propiedades como `edad`, `raza`, `tamaño`, `actividades`, y métodos como `saluda`. Una vez creado el modelo, podemos utilizarlo para crear entidades o instancias de éste que reciban sus propiedades y métodos. Entonces tendríamos por ejemplo una instancia `Firulais`, otra `ScoobyDoo`, y podrías hacer uso de las propiedades y métodos definidos en `Perro`, pero llamándolas desde las instancias.

## Clases en ES5

En JS ES5, las funcionalidades de una clase se implementan a través de keywords como `function`, `prototype`, `this`, y `new`. Se utuliza `prototype` para añadir o extender las propiedades de nuestro objeto. Aquí, las funciones tomaran los valores de los argumentos y relacionarán los parámetros con `this`.

La sintaxis o function constructor y cómo instanciar a partir de la nueva "clase" con el keyword `new`:

```
function Car() {
    this.brand = 'Mazda';
    this.model = '3';
    this.year = 2015;
}

let myCar = new Car(); // construyo una instancia de Car con keyword new
console.log(myCar);    // Car { brand: 'Mazda', model: '3', year: 2015 }
```

Se inicia con el constructor `function` y el nombre de la clase (como convención, se inicia con mayúsculas para nombrar una clase). `this.property` se referirá al objeto de cada instancia, según la que estemos trabajando en el momento. En el ejemplo siguiente, la clase recibe tres 

> __NOTA: `__proto__` es una propiedad que tienen todos los objetos de JS y te permite verificar las propiedades que han sido heredadas del prototypo original.  
> Es decir, muestra la estructura del prototipo del objeto desde el que se accesa a `__proto__`.__


## Prototype

```
function User(name, lastName) {                 // ==| Function Constructor |==
    this.name = name || 'empty';                // Aquí se definen las propiedades a heredar a los objetos.
    this.lastName = lastName || 'empty';
}
Persona.prototype.getName = function () {       // ==| Prototyping |==
    return (this.name + ' ' + this.lastName);   // Aquí se construyen los métodos propios del Prototipo y que se heredarán a los objetos.
}
```

### Default Operator (`||`)

```
function Car(brand, model, color, year) {
    this.brand = brand || 'Mazda'; // si no se asigna un valor, el default sera 'Mazda'
    this.model = model || '3';
    this.color = color || 'Cherry';
    this.year = year || 2022;
}

let myCar = new Car('Tesla'); // instanciamos con keyword new
console.log(myCar); // {brand: 'Tesla', model: '3', color: 'Cherry', year: 2022}
```

### Short Circuit (`&&`)

```
let frida;
let jack = {edad: 7};
console.log(frida && jack.edad); // undefined (frida es un objeto vacío, sin valor definido, y a && b pide que ambos sean true para devolver true)
```

### `__property__`

Indica una propiedad que debe mantenerse protegida. No tocar.


## `Object.create` y Pure Prototypal Inheritance

Todos los objetos en JS tienen como prototipo a `Object`. Object tiene un método llamado `create` que crea una instancia del primer objeto que le demos como argumento.

```
var user = {
    name: 'Default',
    lastName: 'Default',
};

var newUser = Object.create(user);
console.log(newUser.name + ' ' + newUser.lastName);     // Default Default
console.log(newUser.__proto__);                         // { name: 'Default', lastName: 'Default' }
```

## ES6 y Clases (`class`)

En la revisión ES6, se utilizan las keywords `constructor`, `this`, `extends`, y `super`. La clase recibe los argumentos y construye una instancia a través de `constructor`. Después de eso, `constructor` relaciona esos argumentos con `this` para que cada instancia reciba sus valores de forma independiente.

También se utiliza el keyword `extends`, que permiten asignar propiedades de una clase a una o más subclases. Puedes llamar al constructor de la clase base a través de `super`.

```
/**
 * Person Class
 */

class Person {
  constructor(name, age, gender) {
    this.name = name;
    this.age = age;
    this.gender = gender;
  }

  getName() {
    return this.name;
  }

  getAge() {
    return this.age;
  }

  getGender() {
    return this.gender;
  }
}

/**
 * Teacher Class
 */

class Teacher extends Person {
  constructor(name, age, gender, subject) {
    super(name, age, gender);

    this.subject = subject;
  }

  getSubject() {
    return this.subject;
  }
}

/**
 * Student Class
 */

class Student extends Person {
  constructor(name, age, gender, marks) {
    super(name, age, gender);
    this.marks = marks;
  }

  getMarks() {
    return this.marks;
  }
}
```

> __NOTA: En el ejemplo anterior, no usamos ningún `let`, `var`, `const`, o `function` para crear propiedades.  
> A partir de ES6, no necesitamos al constructor para inicializar propiedades.__ 