# Los basics

- Lenguaje de **scripting**.
- **Interpretado**: el código no necesita ser compilado. El código se pasará a lenguaje máquina a medida que se vaya ejecutando. Si en un lenguaje compilado necesitábamos un compilador para pasar a lenguaje máquina, en un lenguaje interpretado necesitamos un _interpreter_ para pasar a lenguaje máquina.
- **No tipado**: las variables en JS no tienen un tipo asignado, se declaran usando simplemente las palabra `var`, `let` o `const` (las dos últimas son ES6).
- Multiparadigma: admite OOP, imperative y functional.

# Data Types

En JS, existen X data types básicos:

1. Number
2. String
3. Boolean
4. Function
5. Object
6. Symbol (new in ES2015)

Aunque en realidad, siendo tiquismiquis, existen los siguientes:

1. Number
2. String
3. Boolean
4. Symbol (new in ES2015)
5. Object
   - Function
   - Array
   - Date
   - RegExp
6. null
7. undefined

## Cosas que hay que saber sobre los data types

- El tipado de variables en JS es dinámico. Si declaro una variable y le asigno un número, será tipo Number, pero si luego a esa misma variable le asigno un string, se convertira en String:

```javascript
var x = 12; // Number
x = 'gato'; // String
// ...
```

- Los statements se leen de izquierda a derecha, así que pueden pasar cosas como esta:

```javascript
var resultado = 10 + 5 + 'Ana'; // Resultará en "15Ana"
```

### `String` y `Number`

TIP: una manera rápida de convertir un Number en String y de String a Number es hacer:

```javascript
var toString = 123 + ''; // Resutará en "123"
var toNumber = +'248'; // Resultará en el número 248
```

### `Boolean`

Cualquier valor puede ser convertido a Boolean. Es decir, existen valores "truthy" (i.e. que evaluarán a `true`) y otros "falsy":

- Falsy: `false`, `0`, empty strings (""), `NaN`, `null`, y `undefined`.
- Truthy: todos los demás.

### Variables: declaración y scope

Las variables nuevas se declaran utilizando las keywords `var`, `let` o `const`:

- `var` tiene scope de función.
- `let` tiene un scope de block-level: es decir, solo serán visibles dentro del bloque de cógigo ("entre llaves {}").
- `const` tiene scope de block level, pero además no se puede modificar.

# Operadores

Además de los clásicos, es interesante conocer el funcionamiento de los comparadores.

## Comparadores

En JS, los valores se pueden comparar usando `<` , `>`, `<=`, `>=`, `!=` y `==`. [!] Sin embargo, JS aplica _coertion_ cuando compara dos tipos distintos, de manera que se dan los siguientes resultados:

```javascript
123 == '123'; // true
1 == true; // true
```

Para evitarlo, debemos usar `===` y `!==`:

```javascript
123 === '123'; // false
1 === true; // false
```

# Objetos
