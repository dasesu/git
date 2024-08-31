Stash: ¿cómo esconder cambios en Git?
===

Hasta ahora hemos cambiado de ramas cuando hay insidencias, o emergencias pero en las que 
el directorio de trabajo estaba siempre limpio o acababamos de commitear algo. 

Pero cuando tenemos modificaciones hechas, que aun no podemos commitear, porque aun estamos trabajando en ella no podemos cambiar de rama. y aqui se presenta un problema, porque puede ser que tengamos que interrumpir nuestro trabajo para resolver una incidencia.


Existen alternativas como hacer un commit y luego borrarlo pero esto es sucio y poco practico.

Existe una alternativa mejor y consiste en guardar todo lo que tengo en mi staging area, para que yo de alguna forma no lo vea.
Para hacer esto usamos, Esto guarda los cambios. 
```
git stash
```

si luego queremos ver el status de la rama nos mostrara 
```
nothing to commit, working directory clean
```

Para ver las cosas que tengo en el stash puedo utilizar el comando git stash list.
```
git stash list
```

el Stash se comporta como una pila y es compartida entre diferentes ramas, guarda la informacion como en un paquete de datos, si quiero regresar la informacion al area de trabajo uso el comando apply asi
```
git stash apply
```

Lo ideal seria moverme a la rama donde los cambios deben ser efectuados y alli extraerlos al directorio de trabajo.

asi:
```
git checkout rama
git stash apply
```

Si hago varios stash consecutivos se almacenan en una especie de pila. 

Puedo obtener mas informacion de un stash con el comando
```
git stash show nombre_stash
```

Para eliminar un stash almacenado hacemos 
```
git stash drop
```

recordemos que el comando checkout -- index lleva el archivo index al estado del ultimo comit 

Si quiero aplicar el stash y sacar de la pila, es decir todo en un unico comando haria git stash pop.
```
git stash pop
```