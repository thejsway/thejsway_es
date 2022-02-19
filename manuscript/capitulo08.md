# Trabaja con caracteres 

Mucho del código que escribas implicará modificar cadenas de caracteres de texto - o [cadenas de caracteres]( https://es.wikipedia.org/wiki/Cadena_de_caracteres ). ¡Veamos cómo!

## TL;DR

* Aunque los valores de tipo carácter son valores JavaScript de tipo primitivo, se les pueden aplicar algunas **propiedades** y **métodos** como si fueran objetos.

* La propiedad `length` devuelve el número de caracteres de la cadena de caracteres.

* Las cadenas de caracteres en JavaScript son **[inmutables]( https://es.wikipedia.org/wiki/Objeto_inmutable )**: una vez creado, el valor de una cadena de caracteres nunca cambia. Los métodos de las cadenas de caracteres nunca afectan el valor inicial y siempre devuelven una cadena de caracteres nueva. 

* Los métodos `toLowerCase()` y `toUpperCase()` devuelven nuevas cadenas de caracteres convertidas en minúsculas y mayúsculas respectivamente.

* Los valores de las cadenas de caracteres pueden ser comparados usando el operador `===` que distingue entre mayúsculas y minúsculas.

* Una cadena de caracteres puede ser vista como una **matriz de caracteres** identificados por su **posición**. La posición del primer carácter es 0 (no 1).

* Puedes iterar en una cadena de caracteres usando ya sea un bucle `for` o el más nuevo `for-of`.

* El método `Array.from()` puede ser usado para convertir una cadena de caracteres en una matriz que puede ser recorrida letra por letra con el método `forEach()`.

* Buscar valores dentro de una cadena de caracteres es posible con los métodos `indexOf()`, `startsWith()` y `endsWith()`.

* El método `split()` separa una cadena de caracteres en sus partes delimitadas por un separador.


## Resumen de las cadenas de caracteres

Recapitulemos lo que ya sabemos sobre las cadenas de caracteres un valor de tipo cadena:

* Un valor de tipo cadena de caracteres representa texto.

* En JavaScript, una cadena de caracteres se definida poniendo texto entre comillas simples (`'Soy una cadena de caracteres'`) o dobles (`"Soy una cadena de caracteres"`).

* Puedes utilizar caracteres especiales dentro de una cadena de caracteres introduciendo los con `\` ("diagonal invertida)" seguida de otro caracter. Por ejemplo, usa `\n` para agregar un salto de línea.

* El operador `+` concatena (combina o suma) dos o más caracteres.

Más allá de estos usos básicos, las cadenas de caracteres tienen aún más versatilidad.

## Obtener el tamaño de una cadena de caracteres

Para obtener el **tamaño** de una cadena de caracteres (el número de caracteres) que contiene, agregale `.length`. El tamaño será devuelto como un número entero.

```js
console.log("ABC".length); // 3
const cad = "somos caracteres";
const tam = cad.length;
console.log(tam); // 16
```

Aunque los valores de las cadenas de texto son de tipo primitivo en JavaScript, se les pueden aplicar algunas propiedades y métodos como si fueran objetos usando la **notación de punto**. `length` es una de esas propiedades.


## Convertir caracteres a mayúsculas o minúsculas

Puedes convertir el texto de una cadena de caracteres a **minúsculas** invocando el método `toLowerCase()`. Alternativamente, puedes hacer lo mismo con `toUpperCase()` para convertir una cadena de caracteres a minúsculas.
palabraMinuscula palabraMayuscula
```js
const palabraOriginal = "Bora-Bora";

const palabraMinuscula = palabraOriginal.toLowerCase();
console.log(palabraMinuscula); // "bora-bora"

const palabraMayuscula = palabraOriginal.toUpperCase();
console.log(palabraMayuscula); // "BORA-BORA"
```

`toLowerCase()`  y `toUpperCase()` son dos métodos para cadenas de caracteres. Como cualquier método para cadena de caracteres, ninguno tiene efecto en el valor inicial y devuelven una cadena de caracteres nueva.

T> Es importante comprender que una vez creada, el valor de una cadena de caracteres nunca cambia: las cadenas de caracteres son **inmutables** en JavaScript.

## Comparar dos cadenas de caracteres 

Puedes comparar dos cadenas de caracteres con el operador `===`. La operación devuelve un valor booleano: `true` si las cadenas de caracteres son iguales, `false` si no lo son.

```js
const palabra = "koala";
console.log(palabra === "koala");    // true
console.log(palabra === "kangaroo"); // false
```

W> La comparación de cadenas de caracteres distingue entre minúsculas y mayúsculas. ¡Así que pon atención a las letras!

```js
console.log("Qwerty" === "qwerty");               // false
console.log("Qwerty".toLowerCase() === "qwerty"); // true
```

## Cadenas de caracteres como conjuntos de caracteres

### Identificar un carácter en particular

Puedes ver a una cadena de caracteres como una matriz de caracteres. Cada carácter en identificado por un número llamado posición, así como ocurre en una matriz. Se aplican las mismas reglas de oro: 

* La posición del primer carácter en una cadena de caracteres es 0, no 1. 
* El número de la posición más alta es el tamaño de la cadena de caracteres - 1.

### Acceder a un carácter en particular

Sabes como identificar un carácter por su posición. Para acceder a él, usas la **notación de corchetes** `[]` con el carácter colocado entre los corchetes.

W> Tratar de acceder a un carácter más allá del tamaño de la cadena de caracteres produce el resultado `undefined`.

W> Trying to access a string character beyond the string length produces an `undefined` result.

```js
const deporte = "basquetbol";
console.log(deporte[0]);  // primera "b"
console.log(deporte[7]);  // segunda "b"
console.log(deporte[10]); // undefined: el último carácter está en la posición 9
```

### Iterar en una cadena de caracteres

Ahora ¿que tal si quieres acceder a todos las letras de una cadena de caracteres uno por uno? Puedes acceder a cada letra individualmente, como se mostró antes:

```js
const nombre = "Sarah"; // 5 caracteres 
console.log(nombre[0]); // "S"
console.log(nombre[1]); // "a"
console.log(nombre[2]); // "r"
console.log(nombre[3]); // "a"
console.log(nombre[4]); // "h"
```

Esto es poco práctico si tu cadena de caracteres contiene más de unos cuantos caracteres. Necesitas una solución mejor para *repetir* el acceso a los caracteres. ¿La palabra "repetir" te recuerda a un concepto anterior? ¡Bucles, claro!

Puedes escribir un **bucle** para acceder a cada letra de la cadena de caracteres. Por lo general, un bucle `for` es una mejor opción que un bucle `while`, dado que sabemos que el bucle necesita ejecutarse una vez por cada letra en la cadena de caracteres.

```js
for (let i = 0; i < miCadena.length; i++) {
    // Usa miCadena[i] para acceder a cada carácter uno por uno
}
```

El contador del bucle `i` va desde cero (la posición del primer carácter de la cadena de caracteres) hasta el tamaño de la cadena de caracteres - 1 (posición del último carácter). Cuando el valor del contador es igual al tamaño de la cadena de caracteres, la expresión se vuelve falsa y el bucle finaliza.

Entonces, el ejemplo anterior también puede ser escrito con un bucle `for` con un resultado idéntico.

```js
const nombre = "Sarah";
for (let i = 0; i < nombre.length; i++) {
  console.log(nombre[i]);
}
```

Como para las matrices que se abordaron antes, una evolución reciente de JavaScript ha introducido otra opción para iterar en una cadena de caracteres: el bucle `for-of`. El ejemplo anterior también puede ser escrito asi:

```js
const nombre = "Sarah";
for (const letra of nombre) {
  console.log(letra);
}
```

Si la posición no se necesita dentro del bucle, está sintaxis sin duda es más simple que un bucle estándar `for`.

## Convertir una cadena de caracteres en una matriz

El método `Array.from()` de JavaScript puede ser usado para convertir una cadena de caracteres en una matriz. Está matriz también puede ser recorrida con el método `forEach()`. Tal como los anteriores, este ejemplo muestra las letras de la cadena de caracteres una por una.

```js
const nombre = "Sarah";
const matrizNombre = Array.from(nombre);
matrizNombre.forEach(letra => {
  console.log(letra);
});
```

## Buscar dentro de una cadena de caracteres

Buscar determinados valores dentro de una cadena de caracteres es una tarea común.

El método `indexOf()` toma como parámetro el valor buscado. Si el valor es hallado dentro de la cadena de caracteres, devuelve la posición de la primera aparición del valor. En caso contrario devuelve - 1.

```js
const cancion = "Honky Tonk Women";
console.log(cancion.indexOf("onk")); // 1
console.log(cancion.indexOf("Onk")); // -1 debido a diferencia entre mayúsculas y minúsculas
```

Cuando se busca un valor al inicio o final de una cadena de caracteres, también se pueden usar los métodos `startsWith()`  y `endsWith()`. Ambos devuelven ya sea  `true` o `false`, dependiendo si el valor es hallado o no. Ten cuidado: estos métodos distinguen entre mayúsculas y minúsculas.


```js
const cancion = "Honky Tonk Women";

console.log(cancion.startsWith("Honk")); // true
console.log(cancion.startsWith("honk")); // false
console.log(cancion.startsWith("Tonk")); // false

console.log(cancion.endsWith("men")); // true
console.log(cancion.endsWith("Men")); // false
console.log(cancion.endsWith("Tonk")); // false
```

## Separando una cadena de caracteres en partes 

A veces una cadena de caracteres está hecha de varias partes separadas por un valor concreto. En este caso es fácil obtener las partes individuales usando el método `split()`. Este método toma como parámetro el separador y devuelve una matriz que contiene las partes.

```js
const listaMeses = "Jan,Feb,Mar,Apr,May,Jun,Jul,Aug,Sep,Oct,Nov,Dec";
const meses = listaMeses.split(",");
console.log(meses[0]);  // "Jan"
console.log(meses[11]); // "Dec"
```

## ¡Hora de programar!


### Información de la palabra

Escribe un programa que te pida una palabra después muestre su tamaño y sus valores en minúsculas y mayúsculas.

### Conteo de vocales

Mejora el programa anterior para que también muestre el número de vocales dentro de la palabra.

### Palabra al revés

Mejor el programa anterior para que muestre la palabra escrita al revés.

### Palíndromo

Mejor al programa anterior para checar si la palabra es un palíndromo. Un palíndromo es una palabra u oración que se escribe de la misma forma ya sea derecho o al revés, ignorándo signos de puntuación, mayúsculas y minúsculas y espacios.

> `"radar"` debe ser detectada como un palíndromo, `"Radar"` también.