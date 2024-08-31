005_Deshacer una modificación
===

HEmos visto anteriormente que podemos usar el flag amend para enmendar un commit que hayamos hecho
, es decir si nos falto agregar algo o queremos quitar algo de un commit, podemos hacer git commit --amend y este commit va a sobreescribir el anterior, como si no se hubiese hecho pero tomando este como commit.

Pero el commit es algo que se maneja desde el punto de vista del trabajo con git y no desde el punto de vista del trabajo con el archivo o archivos en los que estoy trabajando.

Existen otras formas de equivocarnos, por ejemplo modificar un archivo y salvar los cambios.

En este caso si quiero deshacer los cambios que he hecho en un archivo. puedo ver con git status que el archivo se encuentra como modificado porque aun no he hecho add del archivo y quiero llevarlo al estado que tiene en el ultimo commit realizado

#### Deshacer un Archivo Modificado
(Aun no se ha hecho add del archivo)

Supongamos que hemos modificado un archivo, como podemos volver al estado en el
que estaba el archivo en la última confirmación?

```
$ git checkout -- CONTRIBUTING.md
```

#### Deshacer un Archivo Preparado

Supongamos que ahora he hecho cambios pero sin querer he hecho `git add CONTRIBUTING.md`, si ahora 
uso `git checkout -- CONTRIBUTING.md` llevara el archivo al estado actual que tiene, es decir no efectuara cambios, asi que si quiero revertir los cambios tengo que hacer un reset para volver ese archivo atras en el tiempo(esto solo se encargara del unstaged). y luego hacer un checkout sobre ese archivo para llevarlo al punto que tenia antes del add.
asi:

```
$ git reset HEAD CONTRIBUTING.md
$ git checkout -- CONTRIBUTING.md
   ```