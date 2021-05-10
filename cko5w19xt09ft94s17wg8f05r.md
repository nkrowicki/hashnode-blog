## 🗑 Git: Como eliminar un repositorio remoto

Esto es útil cuando por ejemplo nos clonamos un repositorio y deseamos agregar nuestro repositorio como **respositorio remoto** y eliminar el otro.

Todo lo que tenemos que hacer es introducir el siguiente comando:

```git remote -v```

Eso nos listará nuestros repositorios **remotos**, algo así como:



```

origin  https://gitlab.com/nkrowicki/mi-repositorio (fetch)

origin  https://gitlab.com/nkrowicki/mi-repositorio (push)

``` 

Luego, corremos:

`git remote rm origin`

Esto eliminará el repositorio `origin` por lo que si introducimos nuevamente `git remote -v` veremos que ya no nos devolverá nada.

Fácil no?