007_Revertir un commit
===

## Si queremos deshacer un commit
Revert es un comando que sirve para revertir un commit y para poder utilizar revert.

Antes de entrar en el comando revert, vamos a ver como podemos comparar el
contenido de dos commits diferentes, recordar que podemos usar git diff para
ver las diferencias del actual con el anterior, pero si indicamos los
identificadores de commit tambien podemos ver la diferencia con respecto a
commits no contiguos

```
git log --oneline
git diff b6afe92 92d825b
```

Esto me va a mostrar que cosas se han agregado y que cosas se han eliminado,
git revert va a hacer lo opuesto, va a agregar lo qeu se ha eliminado y
eliminar lo que se habia agregado.

Recordemos tambien que el apuntador HEAD apunta a nuestra rama actual, podemos
verlo con la opcion --decorate.

```
$ git log --oneline --decorate

a222588 (HEAD -> main, origin/main, origin/HEAD) ajuste
b6afe92 ajustes decidir
ef2a52c ajustes
2d77dcc ajustes
85c0d79 intro a machine learning
5880365 intro a machine learning
```

como vemos tenemos varios commits antes de HEAD, hay una sintaxis para
referirnos a ellos a partir de head y es con el uso de ~, que quiere decir
tantos antes de HEAd, asi si queremos apuntar o referirnos al penultimo commit
podemos indicarlo con `HEAD~1` y al antepenultimo `HEAD~2`, sabiendo esto
podemos ahora comprar un commit con su anterior asi

```
git diff HEAD~1 HEAD
```

Ahora si queremos revertir tengo que decirle que comit quiero revertir asi
```
git revert HEAD
```
Esto va a revertir HEAD y por lo tanto quedara lo que se encontraba en HEAD~1

Supongamos que enlugar de uno, se han hecho 2 commits que queremos revertir,
pero ademas no quiero que termine en commit, quiero que los cambios queden en
el stage sin confirmarse, para poder seguir trabajando sobre ellos. PAra hacer
esto podemos hacer:

```
git revert --no-commit HEAD
```

puedo repetir esta operacion varias veces de commit en commit, una vez
terminado de revertir hasta el punto deseado, debo hacer:

```
git revert --continue
```