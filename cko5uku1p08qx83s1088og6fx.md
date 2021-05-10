## 🚀 Git push a 2 (dos) repositorios al mismo tiempo! (+SYNC)

Hoy vamos a ver cómo pushear (```git push```) a 2 repositorios al mismo tiempo y manterlos sincronizados, es mucho más sencillo de lo que crees!

### Ingredientes necesarios:
- Un repositorio (ej: my-repo-original)😝
- Otro repositorio (ej:my-second-repo) 😅

### How to
Todo lo que tenemos que hacer es configurar nuestros repositorios remotos:

1. ```git remote set-url --add --push origin git@github.com:nkrowicki/my-repo-original.git``` 

2. ```git remote set-url --add --push origin git@github.com:nkrowicki/my-repo-original.git```

Eso es todo!

Ahora, cuando hagamos un ```git push``` nuestra branch será enviada a ambos repositorios al mismo tiempo!