# Antes que nada: la keyword `this` y su relación con funciones y métodos

Aclaración: llamamos método a una función que está en el scope de un objeto. Como una función en JS es un tipo de objeto, una función declarada dentro de una función es, por tanto, un método (siempre y cuando se esté usando una instancia de la función que contiene al método). Dicho esto:

## `this` en un método

`this` en un método hace referencia al objeto dueño del método:

```javascript
let persona = {
  nombre: 'Isidoro',
  getNombre: function() {
    return 'Nombre: ' + this.nombre;
  }
};
```

## `this` en una función

Dentro de una función, `this` apuntará al objeto global (sea lo que sea eso), o será `undefined` si estamos usando el strict mode.

# 1. Functional Classes

## Usando funciones

Podemos simular una clase y sus métodos utilizando funciones:

- Creamos una función a modo de **constructor**.
- Creamos un objeto con `new` (recordar que en JS las funciones son un "subtipo" del tipo `Object`).
- Definimos las propiedades y métodos del objeto usando `this`.

```javascript
function Fruta(tipo) {
  this.tipo = tipo;
  this.color = 'unknown';
  this.setColor = setColor;
  this.getInfo = getInfo;
}

function setColor(color) {
  this.color = color;
}

function getInfo() {
  return `Es una ${this.tipo} de color ${this.color}`;
}

let reineta = new Fruta('manzana');

reineta.setColor('verde');
console.log(reineta.color); // "verde"

console.log(reineta.getInfo()); // "Es una manzana de color verde"

Fruta('pera'); // Error: "this is undefined" porque no hems creado un objeto
```

También podemos definir el método directamente dentro de la función:

```javascript
function Fruta(tipo) {
  this.tipo = tipo;
  this.color = 'unknown';
  this.setColor = function setColor(color) {
    this.color = color;
  };
  this.getInfo = getInfo;
}
```

## Usando funciones con `prototype`

La desventaja de definir los métodos dentro de la función, es que cada vez que hagamos una instancia, se creará también una nueva instancia de ese método. Para solucionar este problema, en JS, cada tipo de objeto tiene una propiedad llamada `prototype`, que se puede usar para:

- Añadir un nuevo método o propiedad a un constructor.
- Añadir un nuevo método o propiedad a común a todas las instancias de una clase.

Un ejemplo del primer caso:

```javascript
function Fruta(tipo) {
  this.tipo = tipo;
  this.color = 'unknown';
}

Fruta.prototype.setColor = function setColor(color) {
  this.color = color;
};
```
