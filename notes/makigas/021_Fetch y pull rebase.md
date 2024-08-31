021 Fetch y pull rebase
===

Pull realmente es una combinacion de dos otros comandos.

git fetch y git merge.

fetch: Sirve para preguntarle a un remoto si tiene novedades y descargarlas
```
git fetch origin 
```

recordemos que cuando trabajamos con remotos tenemos varias ramas asociadas a
las ramas ya creadas, por ejmlpo para main tenemos su respectiva rama remota
asi:

```
main
remotes/origin/HEAD -> origin/main
remotes/origin/dc2s4_aprendizaje_refuerzo
remotes/origin/doc_alternativa
remotes/origin/main
```

El otro comando que compone a pull, consiste en hacer un merge de la rama en la
que nos encontramos con la rama remota asociada a nuestra rama.

```
git merge remotes/origin/main
```

como lo que se esta haciendo es un merge muchas veces se pueden presentar
conflictos que generalmente se resuelven por fastforward. Lo qu eocurre es que
si hay modificaciones en ambas ramas nos advertira que se tiene que hacer una
fusion, de la rama master que hay en un remoto. Esto se resuelve creando un
commit temporal 

hay una forma de evitar esto es que usando el parametro rebase asi:

```
git pull --rebase origin main
```

