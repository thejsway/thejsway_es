# Guía de estilos {#style-guide}

Estas son las reglas de programación y principios usados a lo largo del libro.

> Este capítulo es por naturaleza subjetivo y obstinado. Siéntete libre de hacer tus propias elecciones.

## Nombrado

Nombrar cosas correctamente contribuye en gran medida a hacer el código más limpio y fácil de entender. Algunas reglas generales de nombrado se presentan a continuación.

### Elige nombres significativos

La regla más importante es darle a cada elemento (variable, función, clase, etc.) un nombre específico que refleje su rol. Una variable que contiene el valor del radio de un círculo debería ser llamado `radio` en lugar de `num` o `miVal`.

Las abreviaciones deben estar limitadas a elementos efímeros, como los contadores de bucles.

### No uses palabras reservadas

Cada palabra clave de JavaScript es un nombre reservado. No deberían ser usadas como nombres de variables. Aquí está la [lista de palabras reservadas en JavaScript](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Lexical_grammar#palabras_clave).

### Sigue una convención de nomenclatura

Puede tomar varias palabras describir precisamente el rol de ciertos elementos. Este libro adopta la popular convención de nomenclatura [camelCase](https://es.wikipedia.org/wiki/Camel_case) basada principalmente en dos principios: 

* Todos los nombres comienzan con una letra **minúscula**.
* Si un nombre se compone de varias palabras, la primera letra de cada palabra (a excepción de la primera palabra) es **mayúscula**.

Adicionalmente, este libro usa las siguientes reglas de nomenclatura:

* Los nombres de funciones y métodos incluyen un **verbo de acción**: `calcularTotal()`, `encontrarNodoPrimario()`, `atacarObjetivo()`, etc.
* Para ser consecuentes con otros lenguajes de programación, los nombres de clases comienzan con una letra **mayúscula**: `Usuario` en lugar de `usuario`.

* Puesto que podrían contener múltiples elementos, las matrices son nombradas en **plural** o se les agrega el prefijo `lista`: `peliculas` o `listaPeliculas`, pero no `pelicula`.
* Para distinguirlos de otras variables, a los elementos DOM se les agrega el prefijo `elemento` (o `elementos` para variables de tipo matriz): `elementoDiv` en lugar de simplemente `div`.

W> Como muchos otros lenguajes, JavaScript distingue entre mayúsculas y minúsculas. Por ejemplo, `miVariable` y `mivariable` son dos nombres de variable diferentes. ¡Ten cuidado!

## Organización de código

Este es un tema de muchos debates en la comunidad JavaScript: usar espacios o tabulaciones para agregar sangrías, omitir los puntos y coma, comillas simples o dobles para las cadenas de caracteres, y más.

Una solución sencilla y eficiente es contar con una herramienta para automatizar la tarea de bajo nivel de organización de código, para que así te puedas concentrar en el trabajo de orden más superior. Este libro usa [Prettier](https://github.com/prettier/prettier) con la configuración predeterminada (comillas dobles y puntos y comas).

## Calidad del código 

Puesto que JavaScript es un lenguaje de clasificación dinámica, varios errores no aparecen hasta la ejecución: nombrar erróneamente una función, cargar un módulo inexistente, etc. Además, muchas otras equivocaciones como declarar una variable sin siquiera usarla no afectarán el resultado de ejecución, pero hacen tu código más difícil de leer y reducen su calidad general.

Por suerte, herramientas especializadas llamadas **linters** pueden verificar el cumplimiento de las reglas en tu código durante la edición y advertir sobre defectos potenciales. Los linters aumentan considerablemente la productividad del desarrollador, permitiendo arreglar muchas fallas antes de que sucedan.

Este libro usa [ESLint](http://eslint.org) para inspeccionar el código. ESLint es una herramienta muy flexible y puedes personalizarla a tus necesidades específicas. Han surgido diversos conjuntos de reglas de ESLint, en particular uno basado en la [guía de estilos de AirBnb](https://github.com/airbnb/javascript).

> Bien vale la pena leer esta obstinada guía de estilos. 

La configuración de este libro amplia las reglas de AirBnb y Prettier (Prettier recibe prioridad), con algunas diferencias menores.

Este es el contenido del archivo de configuración `.eslintrc` del libro.

```json
{
  "extends": ["airbnb", "prettier"],
  "env": {
    "browser": true
  },
  "plugins": ["prettier"],
  "rules": {
    "no-console": "off",
    "no-alert": "off",
    "no-plusplus": "off",
    "default-case": "off",
    "no-param-reassign": [
      "error",
      {
        "props": false
      }
    ],
    "arrow-body-style": [
      "error",
      "as-needed",
      { "requireReturnForObjectLiteral": true }
    ]
  }
}
```

Las divergencias respecto a las reglas predefinidas se explican a continuación.

* `"no-console"` y `"no-alert"`: para habilitar invocaciones `console.XXX()` y `alert()`.
* `"no-plusplus"`: para habilitar operadores unitarios como `++`, usados comúnmente y generalmente inofensivos.
* `"default-case"`: para habilitar declaraciones `switch` sin una opción `default`, que son comunes.
* `"no-param-reassign"`: para habilitar la actualización de propiedades de un objeto pasado como parámetro.
* `"arrow-body-style"`: para usar la sintaxis más explícita de `return` en funciones de flecha que devuelven un objeto literal.
