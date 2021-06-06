## Hook para detectar si un usuario hizo click afuera de un elemento

Hoy te voy a mostrar un hook construido con Typescript que te permita detectar cuando un usuario hizo click fuera de un elemento!

## Cuando utilizar este hook?

Un caso común en donde utilizar este hook es cuando tenemos un modal o un menu de opciones que se hace `visible` cuando el usuario da click a un elemento pero queremos que `se oculte` cuando el usuario hace click `por fuera de él`.

Podríamos hacer que simplemente cuando el usuario haga click en cualquier parte de la pantalla este menú de opciones se oculte peeeero eso no es lo que queremos ya que probablemente este menú de opciones tenga justamente "opciones" las cuales el usuario puede clickear y si al clickear el menú este desaparece probablemente eso no sea el comportamiento que estamos buscando.

## Hook al rescate 🧙‍♂️ 

### useOnClickOutside

❗ **Algo importante a mencionar antes de continuar es que este hook recibe 3 parámetros pero el tercer parámetro es OPCIONAL y en la mayoría de los casos no es necesario.**


```
import { RefObject, useEffect } from 'react';

type AnyEvent = MouseEvent | TouchEvent;

function useOnClickOutside<T extends HTMLElement = HTMLElement>(
  ref: RefObject<T>,
  handler: (event: AnyEvent) => void,
  noRef?: RefObject<T>,
) {
  useEffect(() => {
    const listener = (event: AnyEvent) => {
      const el = ref?.current;
      const noEl = noRef?.current;
      if (
        !el
        || el.contains(event.target as Node)
        || (noEl && noEl.contains(event.target as Node))
      ) {
        return;
      }
      handler(event);
    };
    document.addEventListener('mousedown', listener);
    document.addEventListener('touchstart', listener);
    return () => {
      document.removeEventListener('mousedown', listener);
      document.removeEventListener('touchstart', listener);
    };
  }, [ref, handler]);
}

export default useOnClickOutside;
``` 

## Como usarlo

1️⃣ Crear un archivo llamado `useOnClickOutside` dentro de una carpeta llamada `hooks` (simplemente para mantener un proyecto prolijo y ordenado)

2️⃣ Importar el hook en el componente en donde deseamos utilizarlo. 

**A partir de aquí todo lo que haremos será dentro de nuestro componente.**

`import useOnClickOutside from 'hooks/useOnClickOutside';`

3️⃣ Crear las referencias necesarias (dentro de nuestro componente)


```
  const myRefElement1 = useRef(null);
  const myRefElement2 = useRef(null); 
```

4️⃣ Crear una función callback la cual se va a ejecutar cuando el usuario realice un click por fuera de este elemento.

` const handleClickOutsideFn = () => console.log('El usuario hizo click fuera del elemento!)`

Importante, lo que le pasamos a este hook (nuestra función callback) es simplemente una función por lo que dentro de ella pueden hacer lo que deseen!

⚠️ Recuerden que `myRefElement2` no es necesario en el 95% de los casos. 

`myRefElement2` se encuentra disponible por si deseamos aplicar el mismo comportamiento a más de un elemento a la vez, en este ejemplo lo vamos a incluir pero repito, **no es necesario**!

5️⃣ Usar el hook!

```
 useOnClickOutside(myRefElement1, handleClickOutsideFn, myRefElement2);
```

- Primer parámetro: Obligatorio -> Nuestra referencia al elemento en cuestión (el que querémos que cuando se haga click por fuera de él se ejecute nuestra función callback)

- Segundo parámetro: Obligatorio -> Nuestra función callback que se ejecutará cuando el usuario haga click por fuera de nuestro elemento (Primer parámetro)

- Tercer parámetro: Opcional -> Funciona igual que el Primer parámetro, recibe una referencia a un elemento. 

6️⃣ Utilizar las referencias que declaramos!

Claro! Esas referencias que hemos creado aún no hacen referencia a ningún elemento, tenemos que pasarselas a un elemento como por ejemplo a un `div` con la propiedad `ref`.

```
    <>
    <div ref={myRefElement1}  onClick={handleOpenMenu} >
        <TuContenido />
    </div>
    ....
    ....
    <div ref={myRefElement2} onClick={handleClickHere}>
        ....
    </div>
</>
```

Eso es todo!