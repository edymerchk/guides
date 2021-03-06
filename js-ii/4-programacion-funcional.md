# Programación funcional en JavaScript

La **programación funcional** es un **paradigma de la programación** en donde las funciones se convierten en las protaginistas del código que escribimos.

Un **paradigma de la programación** es una forma de pensar en programación. Otros **paradigmas de la programación** incluyen la **programación imperativa** (de la que vamos a hablar en un momento) y la **programación orientada por objetos**. Estos paradigmas no son excluyentes y se pueden mezclar.

Aunque JavaScript no es un lenguaje puramente funcional, sí es posible programar de forma funcional. En JavaScript las funciones tienen las siguientes características:

* Se pueden asignar a variables.
* Se pueden pasar como parámetro de otras funciones (a esto se le cononce como **callbacks**).
* Se pueden retornar desde otras funciones.

## Funciones que reciben funciones

Un **lenguaje funcional**, a diferencia de un **lenguaje imperativo**, nos permite componer funciones para solucionar diferentes tipos de problemas. Por ejemplo, imagina que tenemos el siguiente arreglo:

```js
const arr = [1, 2, 3];
```

Ahora queremos imprimir todos sus elementos. En **programación imperativa** lo haríamos de la siguiente forma:

```js
for (let i=0; i < arr.length; i++) {
  console.log(arr[i]);
}
```

En programación funcional utilizaríamos una función llamada `forEach` que viene incluída por defecto en todos los arreglos:

```js
const sum = arr.forEach(elem => console.log(elem));
```

Más compacto ¿no?. Por debajo `forEach` utiliza `for` para hacer el recorrido de los elementos. No es que la **programación funcional** reemplace la **programación imperativa**, la **programación funcional** está un nivel por encima de la **programación imperativa**.

### Map

Otro método útil que traen todos los arreglos es `map` que nos permite transformar cada uno de los elementos de un arreglo. Por ejemplo, imagina que queremos duplicar todos los valores de `arr`:

```js
const newArr = arr.map(elem => elem * 2);

// newArr sería [2, 4, 6]
```

Lo interesante de las funciones es que se pueden anidar para crear código muy sutil.  Por ejemplo, el siguiente código duplicaría cada elemento del arreglo y después imprimiría cada elemento duplicado.

```js
arr
  .map(elem => elem * 2)
  .forEach(elem => console.log(elem));
```

Separé el código en varias líneas para que sea más fácil de leer. Esto es una buena práctica cuando se anidan funciones.

### Reduce

Otra operación muy útil con los arreglos es convertirlos en algo completamente diferente, por ejemplo sumar todos los elementos, o crear un objeto a partir de un arreglo. A esto se le conoce en programación como **reducirlos**.

En JavaScript todos los arreglos tienen un método `reduce` que se utiliza precisamente para esto. Por ejemplo, si queremos sumar todos los elementos en `arr` podemos hacer lo siguiente:

```js
const sum = arr.reduce((acc, elem) => acc + sum);
console.log(sum); // 6
```

`reduce` recibe un **callback** (una función) y, opcionalmente, un valor inicial. El **callback** recibe dos parámetros: un acumulador y un elemento. Lo que retorne el **callback** se va a utilizar como el acumulador del siguiente elemento. En nuestro caso vamos acumulando la suma.

## Funciones que retornan funciones
