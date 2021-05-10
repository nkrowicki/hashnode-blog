## 📝 Javascript: Mockea cualquier cosa en 1 minuto

*Spoiler alert:  Vamos a ver como crear un array de objetos muy rápido (simulando una respuesta de una api)*

---

Alguna vez te pasó tener que trabajar con un endpoint el cual el equipo de backend aún no lo tenía listo?

El escenario ideal sería que cuando el equipo de frontend comience a trabajar una nueva feature el endpoint/api ya se encuentre finalizado con toda su documentación lista para trabajar.

Pero esto por lo general solo ocurre en nuestros sueños y nosotros como Frontend Developers muchas veces tenemos que ingeniárnosla para poder avanzar.

Hoy vamos a ver como mockear cualquier data rapidamente y no depender de que un endpoint se encuentre finalizado.

## How to ❓

En este caso vamos a simular que el back nos está devolviendo (o nos debería estar devolviendo) una lista  de notas (será un `array`) donde cada nota es un `objeto` con las siguientes `propiedades`:

- `id`: Valor único que identifica a cada nota
- `title`: Un string como 'Este es mi título'

Todo lo que vamos a hacer es crear un archivo `js` con lo siguiente:

```
// src/data/data.js (nombre del archivo)

const notes = new Array(15) // Creamos el array con 15 posiciones vacías
   .fill(1) // Llenamos cada una de esas posiciones con el número 1 -> [1, 1, 1...]
   .map((_, i) => ({
      id: Date.now() + i,
      title: `Note ${i}`
   })) // Recorremos el array con el método 'map' y para cada posición existente en el array
        // devolvemos un objeto con propiedad 'id' y 'title' y sus valores

export const notes; // o -> module.exports = notes; según el entorno en donde estemos trabajando
```

## ✅ Listo! 

Ahora podemos usar nuestra constante `notes` la cual tendrá un valor similar al siguiente sin tener que perder tiempo creando un archivo con cientos de lineas para simplemente mockear la data! ;)

```
const notes = [
  { id: 1620488661154, title: 'Note 0' },
  { id: 1620488661155, title: 'Note 1' },
  { id: 1620488661156, title: 'Note 2' },
  { id: 1620488661157, title: 'Note 3' },
  { id: 1620488661158, title: 'Note 4' },
  { id: 1620488661159, title: 'Note 5' },
  { id: 1620488661160, title: 'Note 6' },
  { id: 1620488661161, title: 'Note 7' },
  { id: 1620488661162, title: 'Note 8' },
  { id: 1620488661163, title: 'Note 9' },
  { id: 1620488661164, title: 'Note 10' },
  { id: 1620488661165, title: 'Note 11' },
  { id: 1620488661166, title: 'Note 12' },
  { id: 1620488661167, title: 'Note 13' },
  { id: 1620488661168, title: 'Note 14' }
];
``` 

## Known issues 👀

1- Que ocurre si no hacemos el `.fill(1)`? 

Simplemente el .map mira el array y dice *"Esto está vacio, no hay nada que recorrer"*.

2- Recordemos que .map no modifica el array existente, si no que nos devuelve uno nuevo.
Para más información de .map te recomiendo la [documentación de Mozilla](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

Espero que les sirva!

👋