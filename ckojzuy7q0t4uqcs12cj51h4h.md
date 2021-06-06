## Next.js: Cómo mostrar algo en desarrollo y ocultarlo en producción

# Welcome! 👋🏻

Querés mostrar algo solo en un entorno de desarrollo (ej: cuando estás trabajando de manera local) y ocultarlo cuando esto vaya a producción?

Perfecto, seguí leyendo! 🤓

3...

2...

1...

Se viene el trucazoooo

↓↓↓

# ✍🏻 How to

## 1. Estamos en desarrollo? 🤔

Creamos una constante llamada `isDev` la cual tendrá un valor `booleano` (`true` o `false`) **


```
const isDev = process.env.NODE_ENV === 'development'
``` 
### Ejemplo:

`isDev` será `false` ❌  cuando -> Estamos en producción (ya que el entorno **no** será *development*)

`isDev` será `true` ✅  cuando -> Estamos en desarrollo (ya que el entorno **sí** será *development*)


## 2. Un condicional por aquí.. (❓)

Utilizamos el valor de esa variable para renderizar lo que deseamos! 

(O para 'no' renderizar lo que deseamos 😝)


```
{isDev && (
  <p>Esto se va a ver solo cuando estemos en desarrollo! 🤙🏻 </p>
)}
``` 

That's all!