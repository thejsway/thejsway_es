# Bienvenido a la programación

## TL;DR

* Una **computadora** es una máquina cuyo rol es ejecutar de manera rápida y sin errores una serie de acciones que se le han dado.

* Un **programa** es una lista de acciones entregada a una computadora. Estas acciones toman la forma de comandos textuales. Todos estos comandos conforman el **código fuente** del programa.

* La tarea del **programador** es crear programas. Para cumplir con esta meta, puede usar distintos lenguajes de programación.

* Antes de escribir código, uno debe pensar a futuro y descomponer el problema a abordar en una serie de operaciones elementales formando un **algoritmo**.

## ¿Qué es un programa?

![Evolución (?)](images/intro02-01.jpg)

Desde su invención en los años 50, las **computadoras** han revolucionado nuestras vidas diarias. Calculando una ruta desde un sitio web o un GPS, reservando un boleto de tren o avión, o viendo y platicando con nuestros amigos al otro lado del mundo: todas estas acciones son posibles gracias a las computadoras.

I> Tomemos el término "computadora" en su sentido más amplió, es decir, una máquina que puede realizar operaciones aritméticas y lógicas. Podría referirse tanto a una computadora de escritorio o laptop (PC, Mac), a un servidor, o a un dispositivo móvil como una tableta o un teléfono inteligente.

No obstante, una computadora solo puede realizar una serie de operaciones simples cuando se le instruye hacerlo. Normalmente no tienen habilidades para aprender, juzgar o improvisar. ¡Simplemente hacen lo que se les pide! Su valor está en como pueden lidiar y procesar rápidamente enormes cantidades de información.

Con frecuencia una computadora requiere de la intervención humana. ¡Es ahí donde entran los programadores y desarrolladores! Ellos escriben programas que se traducen en instrucciones para una computadora.

Un **programa de computadora** (también llamado aplicación o software) generalmente está compuesto de uno o más archivos de texto que contienen comandos en forma de código. Es por esto que a los desarrolladores también se les llama codificadores.

Un **lenguaje de programación** es una manera de dar órdenes a una computadora. ¡Es un poco parecido al lenguaje humano! Cada lenguaje de programación tiene vocabulario (palabras clave que desempeñan un rol específico) y gramática (reglas que definen como escribir programas en ese lenguaje).

## ¿Cómo creas programas?

### Más cercano al hardware: lenguaje ensamblador

El único lenguaje de programación directamente comprensible por una computadora es el lenguaje de máquina. Una representación más legible por los humanos de un lenguaje de máquina es un **lenguaje ensamblador**. Se trata de una serie de operaciones primitivas de vinculadas a una familia específica de procesadores (el "cerebro" de una computadora) y que manipulan su memoria.

Aquí hay un ejemplo de un programa básico escrito en lenguaje ensamblador. Le muestra al usuario la palabra `"Hello"`.

```assembly
str:
    .ascii "Hello\n"
    .global _start

_start:
movl $4, %eax
movl $1, %ebx
movl $str, %ecx
movl $8, %edx
int $0x80
movl $1, %eax
movl $0, %ebx
int $0x80
```

Bastante aterrador, ¿no? Afortunadamente, otros lenguajes de programación son mucho más simples y prácticos de usar que un lenguaje ensamblador.

### La familia de lenguajes de programación

Hay un gran número de lenguajes de programación, cada uno adaptado a distintos usos y con su propia sintaxis. Sin embargo, hay similitudes entre los lenguajes de programación más populares. Por ejemplo, aquí hay un programa básico escrito en Python:


```python
print("Hola")
```

También puedes escribir lo mismo en PHP:

```php
<?php
    echo("Hola\n");
?>
```

¡O incluso en C#!

```csharp
class Program {
    static void Main(string[] args) {
        Console.WriteLine("Hola");
    }
}
```

¿Qué tal en Java?

```java
public class Program {
    public static void main(String[] args) {
        System.out.println("Hello");
    }
}
```

Todos estos programas muestran "`Hola"` mediante diferentes conjuntos de instrucciones.

### Ejecución de un programa 

Al hecho de solicitarle a una computadora que procese las órdenes contenidas en un programa se le llama **ejecución**. Independientemente del lenguaje de programación usado, un programa debe ser traducido a código ensamblador para poder ser ejecutado. El proceso de traducción depende del lenguaje usado.


Con algunos lenguajes, la traducción a código ensamblador sucede línea por línea en tiempo real. En este caso, el programa se ejecuta igual que un humano lee un libro, comenzando en la parte de arriba y bajando línea por línea. Se dice que estos lenguajes son **interpretados**. Python y PHP son ejemplos de lenguajes interpretados.

Otra posibilidad es leer y buscar errores a través de todo el código fuente antes de la ejecución. Si no se detectan errores, se genera un ejecutable dirigido a una plataforma de hardware específica. El paso intermedio se llama **compilación** y se dice que los lenguajes de programación que lo usan son **compilados**.

Finalmente, algunos lenguajes son pseudo compilados para poder ser ejecutados en distintas plataformas de hardware. Este es el caso para el lenguaje Java y también para los que pertenecen a la familia Microsoft .NET (VB.NET, C#, etc).

## Aprende a programar

### Introducción a los algoritmos

A excepción de algunos casos muy básicos, no creas programas escribiendo código fuente directamente. Primero necesitarás pensar en las instrucciones que querrás transmitir.

Toma un ejemplo concreto de la vida diaria: yo quiero preparar un burrito. ¿Cuáles son los pasos que me permitirán lograr mi meta?

```text
Inicio
  Saca la arrocera
  Llénala con arroz
  Llénala con agua
  Cuece el arroz
  Pica las verduras
  Saltea las verduras
  Prueba las verduras
    Si las verduras están buenas
      Sácalas de la estufa
    Si las verduras no están buenas
      Agrega más pimienta y especies
    Si las verduras no están suficientemente cocidas
      Sigue salteando las verduras
  Calienta la tortilla
  Añade arroz a la tortilla
  Añade verduras a la tortilla
  Enrolla la tortilla
Fin
```

![Mmmmmm!](images/intro02-02.jpg)

Alcanzas tu meta combinando una serie de acciones en un orden específico. Hay diferentes tipos de acciones:

* Acciones simples ("saca la arrocera")
* Acciones condicionales ("si las verduras están buenas") 
* Acciones que se repiten ("sigue salteando las verduras")

Usamos un estilo de escritura simple, no un lenguaje de programación en específico. De hecho solo escribimos lo que se llama un **algoritmo**. Podemos definir un algoritmo como una secuencia ordenada de operaciones para resolver un problema dado. Un algoritmo descompone un problema complejo en una serie de operaciones simples.

### El rol del programador

Escribir programas que ejecuten eficazmente las tareas esperadas es la meta de un programador. Un principiante puede aprender a crear rápidamente programas simples. Las cosas se complican más cuando el programa evoluciona y se vuelve más complejo. ¡Se necesita experiencia y mucha práctica antes de que te parezca que podrás controlar está complejidad! Una vez que tienes los cimientos, el único límite es tu imaginación.

> "El programador informático es un creador de universos para los cuales solamente él es el legislador. Ningún guionista, ningún director escénico, ningún emperador, por más poderoso que sea, alguna vez ha ejercido semejante autoridad absoluta para organizar un escenario o un campo de batalla y para comandar este tipo de actores o tropas obedientes e inquebrantables." (Joseph Weizenbaum)