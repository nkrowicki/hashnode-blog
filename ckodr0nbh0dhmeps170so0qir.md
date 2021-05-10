## ❌ CSS: Evita hacer esto!

# CSS as a crack 😎

Directo al grano y sin introducción. 

A lo que vinimos!

↓↓↓

# 1- Colocar margin o padding y despues sacarlo

No apliques margin (o padding) a todos los elementos y luego se los saques al primero o al último, hay otra manera de lograr el mismo resultado!

## NO ❌

```
.card {
  margin-right: 1.6rem;
}

.card:last-child {
  margin-right: 0;
}
``` 

## SI ✅

```
.item:not(:last-child) {
  margin-right: 1.6rem;
}
``` 

---

# 2- Agregar 'display: block' a elementos con 'position: absolute' o 'position: fixed'

🚨 `display:block` es el valor por defecto para `position: absolute` y `position: fixed`

Así que... 

**En estos casos solamente utilizá la propiedad `display` cuando necesites valores como `flex` o `grid`**

## NO ❌

```
.button::before {
  content: "";
  position: absolute;
  display: block; // Innecesario, es el valor por defecto! 😵
}
``` 

o

```
.button::before {
  content: "";
  position: fixed;
  display: block; // Innecesario, es el valor por defecto!  😵
}
``` 

## SI ✅

```
.button::before {
  content: "";
  position: absolute;
}
``` 
o
```
.button::before {
  content: "";
  position: fixed;
}
``` 

---

# 3- Centrar elementos con translate (-50%, -50%) 

Esto fue una especie de "solución" en su momento pero traía problemas en navegadores basados en chromium ya que provocaba problemas con textos de tal forma que se visualizaban borrosos (además de que la solución no es muy prolija que digamos).

Solución: `flex` + `margin: auto` al rescate!

## NO ❌

```
.parent {
  position: relative;
}

.child {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
``` 


## SI ✅
```
.parent {
  display: flex;
}

.child {
  margin: auto;
}
``` 
La solución es más corta (menos líneas de código) y más prolija! 🤩

---

# 4- No uses 'display: block' para 'display: flex'

Cuando usamos flexbox y creamos un contenedor flexible (con `display: flex`) **todos sus hijos** tendrán `display: block` por default!

## NO ❌

```
.parent {
  display: flex;
}

.child {
  display: block;
}
``` 


## SI ✅
```
.parent {
  display: flex;
}
``` 

---

# 5- Uso innecesario de la unidad cuando el valor es 0 (px, em, rem, etc)

Si el valor es `0` no hay necesidad de especificar su unidad: `px`, `em`, `rem`, etc.

## NO ❌

```
.parent {
   margin: 0px;
   padding: 0px 0px 5px 0px;
}

.child {
  margin-right: 0px;
}
``` 


## SI ✅
```
.parent {
   margin: 0;
   padding: 0 0 5px 0; // Otra alternativa: padding-bottom: 5px;
}

.child {
  margin-right: 0;
}
``` 

---

# 6- Simplifica: evita repeticiones innecesarias de código

En ocasiones podemos utilizar solo una línea en lugar de varias, esto es muy común cuando utilizamos `margin`, `padding` y `border`.

## NO ❌

```
border-bottom: 1px solid #01f;
border-left: 1px solid #01f;
border-right: 1px solid #01f;
border-top: 1px solid #01f;
``` 


## SI ✅
```
border:1px solid #01f;
``` 

---

# 7- Simplifica: evita repeticiones innecesarias de código

En ocasiones podemos utilizar solo una línea en lugar de varias, esto es muy común cuando utilizamos `margin`, `padding` y `border`.

## NO ❌

```
border-bottom: 1px solid #01f;
border-left: 1px solid #01f;
border-right: 1px solid #01f;
border-top: 1px solid #01f;
``` 


## SI ✅
```
border:1px solid #01f;
``` 

---

# 8- Ordenar las propiedades por orden alfabético

Puede que haya gente que esté de acuerdo con esto y otros que no, pero creanme que a largo plazo esto es FABULOSO!

Es muy común tener que fixear algo, solucionar un bug, o simplemente hacer una nueva feature/mejora y desperdiciar tiempo buscando una propiedad de css simplemente porque no se encuentra 'organizada' de manera alfabética.

Mi consejo es: ordená todo lo que puedas, tu 'yo' del futuro te lo agradecerá!

## NO ❌

```
width: 100%;
border: 2px solid #000;
display: flex;
``` 


## SI ✅
```
border: 2px solid #000;
display: flex;
width: 100%;
``` 

---

# 9- Evita !important

Por lo general cuando utilizamos esto es para sobreeescribir alguna propiedad con un mayor poder de 'especificidad' o quizás porque querémos que otros desarrolladores no sovbreeescriban la propiedad que estamos seteando.

No importa si es el primer caso o el segundo caso pero... debemos evitar utilizar la propiedad `!important` a toda costa ya que lo unico que nos va a traer a futuro son problemas.

Siempre se puede evitar realizando algun refactor o utilizando otros selectores.

---

# 10- Nombres inconsistenes

Esto es común verlo en proyectos mantenidos por varios desarrolladores, evítalo!

## NO ❌

```
.user-panel {/*...*/}

.CardBox {/*...*/}

.items_list {/*...*/}
``` 


## SI ✅
```
.user-panel {/*...*/}

.card-box {/*...*/}

.items-list {/*...*/}
``` 

---

# 11- Usar ID como selector en lugar de clases

Siempre que se pueda, utiliza clases ya que reutilizar código es fabuloso y las clases pueden reutilizarse!

## NO ❌

```
<p id="my-name">Nahuel Krowicki</p>
``` 


## SI ✅
```
<p class="my-name">Nahuel Krowicki</p>
``` 

---

# 12- Usar ID como selector en lugar de clases

Siempre que se pueda, utiliza clases ya que reutilizar código es fabuloso y las clases pueden reutilizarse!

## NO ❌

```
<p id="my-name">Nahuel Krowicki</p>
``` 


## SI ✅
```
<p class="my-name">Nahuel Krowicki</p>
``` 

----

<a href="https://www.buymeacoffee.com/nahuelkrowicki" target="_blank"> Buy me a coffe!</a>