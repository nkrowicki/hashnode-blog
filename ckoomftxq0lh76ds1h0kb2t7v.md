## Funciones en TypeScript: Function Overloading (MAGIA 🧙🏻‍♂️)

Hola gente!

Bueno, saltemos la introducción (porque no la hay 😅) y vayamos directo a lo que vinimos

↓↓↓

## Qué es function overloading ❓

En español (🇪🇸) sería algo asi como "Sobrecarga de funciones" o "Sobrecarga de métodos" 👀

Básicamente es la posibilidad de establecer "diferentes" implementaciones sobre una misma función lo que nos va a permitir realizar diferentes tareas dependiendo de lo que la función reciba como parámetro.

Es decir, **con una única función podemos realizar 2 tareas diferentes** en lugar de crear una función para cada tarea (2 funciones).

# Funcion Overloading 🧙🏻‍♂️ (magia)

Vamos a ver 2 simples ejemplos, el primero uno que es encuentra en la documentación de TypeScript:

```
function add(a:string, b:string):string; // Tipamos la función 'add' para que reciba 2 strings y retorne un string

function add(a:number, b:number): number;  // Tipamos la función 'add' para que reciba 2 number y retorne un number

function add(a: any, b:any): any { // Tipamos la funcion diciendo que puede recibir 2 any y retornar un any
    return a + b;
}

add("Hello ", "Steve"); // returns "Hello Steve" 
add(10, 20); // returns 30 

``` 

Tal como vemos, si le enviamos 2 strings los concatena y si enviamos 2 numbers los suma.

Eso fue un ejemplo demasiado aburrido.

## La posta ↓

Vamos con un ejemplo más completo y complejo para entender realmente los beneficios:

Tenemos las siguientes 2 interfaces:

```
interface HasEmail {
  name: string;
  email: string;
}

interface HasPhoneNumber {
  name: string;
  phone: string;
}

```


Y la siguiente función:


```
function contactPeople(method: 'email' | 'phone', people: HasEmail | HasPhoneNumber): void {
  if (method === 'email') {
    console.log('Name: ', (people as HasEmail).name);
    console.log('Email: ', (people as HasEmail).email);
  } else {
    console.log('Name: ', (people as HasPhoneNumber).name);
    console.log('Phone: ', (people as HasPhoneNumber).phone);
  }
}
```

Es decir, `contactPeople` puede recibir el método 'email' o 'phone' y según eso podemos mostrar por consola su 'name' (no hay problema ya que los 2 tienen name) y su 'email' o su 'phone' según corresponda.

O sea, podemos hacer lo siguiente sin problemas:

```
// ✅ Email works
contactPeople('email', { name: 'Nahuel', email: '12345678' });

// ✅ Phone works
contactPeople('phone', { name: 'Nahuel', phone: '12345678' });
```

Bien!


### Pero... Que ocurre si hacemos lo siguiente?

```
// ❌ Mixing: does not work
contactPeople('email', { name: 'Nahuel', phone: '12345678' });
```

Eso no funcionará a pesar de que typescript no nos arroje ningún error!

### Porqué? 

Simplemente porque cuando le decimos que de `method` tenga `email` -> va a ingresar a la primer condición de la función e intentará mostrar su `name` y su `email` y como verán no le estamos enviando ningún `email`, si no que estamos enviando un `phone`:

```
if (method === 'email') {
    console.log('Name: ', (people as HasEmail).name);
    console.log('Email: ', (people as HasEmail).email);
  } 
```

### Cual es el problema?

El problema es que eso no va a funcionar y recién nos enteraríamos cuando la aplicación se ejecute!

Necesitamos que Typescipt nos alerte de esto para solucionarlo o para no cometer ese error!

### Function overloading al rescate

Acá es cuando entra la magia 🧙🏻‍♂️

Vamos a agregar las 2 lineas siguientes arriba de la funcion que teníamos declarada:

```
function contactPeople(method: 'email', people: HasEmail): void;
function contactPeople(method: 'phone', people: HasPhoneNumber): void;
```
Con eso estamos simplemente tipando la función (si, ya sé que ya estaba tipada, pero con esto estaríamos haciendo un tipado 'más fuerte' que luego nos va a "salvar las papas" 🥔)

Lo que estamos haciendo con eso es simplemente decir:
- Cuando `method===email` -> `people` será de tipo `HasEmail`
- Cuando `method===phone` -> `people` será de tipo `HasPhoneNumber`

Entonces, si querémos hacer lo siguiente:

```
// ❌  No overload matches this call
contactPeople('email', { name: 'Nahuel', phone: '12345678' });
```

Ahora TypeScript nos advierte que no es posible hacer eso!

Fantastico! No?

---

## Learn more 👨🏻‍🎓

Si querés aprender más de funciones con TypeScript recomiendo leer la siguiente documentación: https://www.typescriptlang.org/docs/handbook/functions.html 

Espero que les haya servido ;) 

