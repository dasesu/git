006_Deshacer un commit
===


Situaciones:
===

Supongamos que el ultimo commit no ha servido para nada y queremos eliminarlo:
Lo primero es averiguar como se se identifica el commit anterior. para eso
usamos `git log`. Por ejemplo supongamos que queermos volver al estado que
tenia el proyecto en el commit `d7dc9f4be974f991c2bac63838a06c834c8e5a37` basta
con que anote unicamente los primeros 7 caracteres. Que es lo que muestra el
commando con el parametro --oneline. Igual que ocurre con docker.

Si al comando git reset le pasamos en lugar de HEAD el identificador del commit
d7dc9f4, se llevara el proyecto a ese estado, eliminando los commits
posteriores. es decir ahora HEAD es d7dc9f4.

Luego podemos verificar que el archivo modificado probablemente no corresponda
al estado que tenia en `d7dc9f4`. Para dejar el archvio como estaba en ese
commit hacemos `checkout -- archivo`.

```
git log
git reset d7dc9f4
git checkout -- archivo.md
```

Como podemos ver, esta operacion se ha hecho en dos pasos, una para llevar el
stage al estado anterior y luego llevar los cambios locales al estado que tenia
en ese punto con el checkout.

Pero tambien podemos hacer eso en un unico paso, es decir, decirle a git que
lleve el stage y archivos al estado indicado.
PAra hacerlo usamos la opcion `--hard`

```
git reset --hard d7dc9f4
```

Es decir los siguientes comandos serian equivalentes.
git reset d7dc9f4
git checkout -- archivo.md

```
git reset --hard d7dc9f4
```

La opcion --hard forzara el cambio de todos los archivos

Tambien tenemos la opcion `--soft`, que eliminara los commits pero dejara los
archivos modificados en el stage.

```
git reset --soft d7dc9f4
```