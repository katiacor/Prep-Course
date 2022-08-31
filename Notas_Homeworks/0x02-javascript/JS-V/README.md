# Classes and Prototypes

## Class

En JS una clase es un modelo o una plantilla que se utiliza como base para representar entidades o conceptos. Por ejemplo, puedo crear una clase `Perro`, con propiedades como `edad`, `raza`, `tamaño`, `actividades`, y métodos como `saluda`. Una vez creado el modelo, podemos utilizarlo para crear entidades o instancias de éste que reciban sus propiedades y métodos. Entonces tendríamos por ejemplo una instancia `Firulais`, otra `ScoobyDoo`, y podrías hacer uso de las propiedades y métodos definidos en `Perro`, pero llamándolas desde las instancias.

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

> Nota: `__proto__` es una propiedad que tienen todos los objetos de JS y te permite verificar las propiedades que han sido heredadas del prototypo original.  
> Es decir, muestra la estructura del prototipo del objeto desde el que se accesa a `__proto__`.


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

```
class Estudiante {
    constructor (nombre, apellido, grado) {
        this.nombre = nombre;
        this.apellido = apellido;
        this.grado = grado;
    }
    saludar() {
        return ('Hola, soy ' + this.nombre + '!');
    };
}

let katia = new Estudiante('Katia', 'Corona', 2);
katia.saludar();
```