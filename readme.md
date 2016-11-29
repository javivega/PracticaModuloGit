# Preguntas sobre el ejercicio 1 de la práctica de GIT

**¿Qué comando utilizaste en el paso 11? ¿Por qué?** 

`git reset HEAD~1 --hard`

Para hacer retroceder el puntero de la rama al commit anterior (además, "--hard" elimina los cambios).


**¿Qué comando o comandos utilizaste en el paso 12? ¿Por qué?**

Primero listé el histórico que nos muestra los *commits* por los que hemos ido saltando:

`git reflog`

Localicé en la lista la entrada en la que había hecho el *commit* con las modificaciones de Markdown y moví el puntero de la rama a ese *commit* (sin conservar los cambios):

`git reset c154829 --hard`

Otra opción hubiese sido fusionar la rama con el *commit* (haciéndolo con la estrategia *fast-forwrd* me ahorraría crear un nuevo *commit*):

`git merge --ff c154829`


**El merge del paso 13, ¿Causó algún conflicto? ¿Por qué?**

Al fusionar la rama styled sobre la rama master me da el mensaje "Already up-to-date", que me indica que todos los *commits* que había en la rama styled ya estaban en la rama master.
 

**El merge del paso 19, ¿Causó algún conflicto? ¿Por qué?**

Al fusionar la rama htmlify sobre la rama master se produce un conflicto. El fichero git-nuestro.md está en ambas ramas y, al comprar línea a línea, se ve que las modificaciones de una rama y la otra son incompatibles pues están tocando las mísmas líneas. Hay que decidir con qué modificaciones nos quedamos.


**El merge del paso 21, ¿Causó algún conflicto? ¿Por qué?**

Al fusionar la rama styled en la rama master me permite usar la estrategia *fast-forward* porque para hacerlo solo necesita mover el puntero de la rama master al principio de la rama styled (no hay conflictos).


**¿Qué comando o comandos utilizaste en el paso 25?**

`git log --graph`


**El merge del paso 26, ¿Podría ser fast forward? ¿Por qué?**

He forzado el no-ff para hacer el *commit* pero podría haber sido perfectamente *fast-forward* porque no se pierden cambios (siemplemente se añade una línea).


**¿Qué comando o comandos utilizaste en el paso 27?**

`git reset HEAD~1 --soft`


**¿Qué comando o comandos utilizaste en el paso 28?**

`git checkout -- git-nuestro.md`


**¿Qué comando o comandos utilizaste en el paso 29?**

`git branch -D title`

En la rama que estaba eliminando había un *commit* con cambios que no estaban en ningún otro, y como a GIT le preocupa que puedas echarle la culpa por perder datos y te pide que te asegures usando "-D" en vez de "-d".


**¿Qué comando o comandos utilizaste en el paso 30?**

`git reset 5a554e1 --hard`

Lo hice directamente porque un par de líneas más arriba tenía el *hash* del *commit* pero si no hubiese sido así podría haber usado:

`git reflog`


**¿Qué comando o comandos usaste en el paso 32? ¿Qué comando o comandos usaste en el punto 33?**

Si lo único que quiero es echar un vistazo al poema tal y como era en el *commit* inicial podría usar su *hash*:

`git log`
`git checkout e585a6d`

Y al terminar de echar un vistado:

`git checkout master`

Otra opción es mover el puntero de la rama a ese *commit*:

`git reset --hard e585a6d`

Lo único es que en este caso, al terminar, ya tendríamos que buscar a qué *commit* queremos volver y mover de nuevo el puntero de rama:

`git reflog`
`git reset --hard 60218cc`
