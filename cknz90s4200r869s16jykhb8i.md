## 😲 Qué es git stash y como utilizarlo?

# git stash: Entiendelo de una vez

---

### 🛑 Conocimientos necesarios  
- Saber que es git
- Saber que es un commit

---

## Go ahead!

El comando `git stash` nos permite **almacenar temporalmente** (guardar en un stash) los cambios que tenemos hechos pero "sin guardar" (en este caso: sin hacer commit de nuestros cambios) para que podamos seguir trabajando en otra cosa y más tarde volver aplicar los cambios que "dejamos en stash".

### Ejemplo

Vamos con un ejemplo bien práctico y fácil de comprender, imaginemos que vamos a cocinar una `carne con papas` con los siguientes pasos:

1. Primero vamos a *cortar la carne* 🥩
2. Luego vamos a *cortar las papas* 🥔 
3. *Cocinar* las papas 🥔 🥔 
4. *Cocinar y mezclar* todo 🥘 

Entonces, comenzamos cortando la carne (🥩) en nuestra mesa de trabajo pero nos damos cuenta que deberíamos comenzar por las papas ya que tardarán más en cocinarse. 

### git stash: vamos con las papas

Lo que vamos a hacer es simplemente parar de cortar la carne y guardarla en la heladera (*stashear la carne / stashear los cambios*) para poder continuar cortando las papas (🥔 ) con la mesa de trabajo limpia (tal como estaba antes de comenzar a cortar la carne). 

Este paso es el famoso `git stash`

Una vez que terminamos de cortar las papas (🥔 ) queremos seguir cortando la carne (🥩 ).

### git stash apply: devolveme la carne
Ahora necesitamos traer la carne que previamente dejamos en la heladera (volver a poner la carne 🥩  en la mesa de corte), esto lo realizamos con el comando `git stash apply`.

---

## Uso práctico

Guardar los cambios en stashes resulta muuuy práctico si tenés que cambiar rápidamente de contexto y ponerte a trabajar con otra cosa, pero estás en medio de un cambio en el código y no lo tienes todo listo para confirmar los cambios (realizar el commmit).

## Cositas importantes a saber

- `git stash` toma los cambios que no están confirmados/commiteados (tanto los que están preparados para commitearse (o sea, los que ya les hiciste `git add`) como los que no)

 - Luego, los guarda en stash ( para usarlos más adelante) e instantaneamente los deshace del código en el que estás trabajando

 - Ahora estamos en un punto en donde tenemos total libertad para hacer cambios, crear commits, cambiar de rama, y más! 

 - Más tarde podemos volver a aplicar el stash (`git stash apply`), o sea volver a aplicar los cambios que habíamos guardado/stasheado y seguir trabajando como si nada! 

- El stash es local, los stashes (podemos tener más de uno) no se suben al server cuando subimos los cambios al repositorio remoto.

---

La idea de este post era simplemente hacer una breve introducción para ayudar a comprender `git stash`, para que sirve y casos de uso.

Si te interesa seguir aprendiendo y profundizando conocimientos en `git stash` te recomiendo este excelente artículo: [Link](https://www.atlassian.com/es/git/tutorials/saving-changes/git-stash)



