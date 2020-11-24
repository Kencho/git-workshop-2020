# git-workshop-2020

Repositorio sandbox para el taller de git para DMS

## Clonado de un repositorio

A continuación se muestra la sintaxis del clonado local de repositorios.

```bash
git clone DIRECCION_REPOSITORIO [NOMBRE_ESPACIO_DE_TRABAJO]
```

Si se omite el nombre del espaio de trabajo, usará por defecto el nombre del repositorio (el último fragmento de la dirección del repositorio). Especificando diferentes nombres de espacios de trabajo podemos trabajar desde el mismo equipo en diferentes ramas, revertir un espacio a una versión anterior del histórico, etc.

## Los commits

Cuando se tenga listo un conjunto de cambios (otros SCMs lo llaman _changeset_), es hora de cerrarlos en un _commit_. Esto es una unidad atómica de cambio (i.e., no se puede aplicar medio commit; o todo el conjunto de cambios, o ninguno).

Podemos ver los ficheros cambios locales con `git status`, y los cambios concretos, en formato _diff_, con `git diff`.

```bash
git status
```

```
En la rama main
Tu rama está actualizada con 'origin/main'.

Cambios no rastreados para el commit:
  (usa "git add <archivo>..." para actualizar lo que será confirmado)
  (usa "git restore <archivo>..." para descartar los cambios en el directorio de trabajo)
        modificado:     README.md

sin cambios agregados al commit (usa "git add" y/o "git commit -a")
```

```bash
git diff
```

```diff
diff --git a/README.md b/README.md
index 4cbe0c2..830bf9e 100644
--- a/README.md
+++ b/README.md
@@ -11,3 +11,23 @@ git clone DIRECCION_REPOSITORIO [NOMBRE_ESPACIO_DE_TRABAJO]
`` ``` ``
 
 Si se omite el nombre del espaio de trabajo, usará por defecto el nombre del repositorio (el último fragmento de la dirección del repositorio). Especificando diferentes nombres de espacios de trabajo podemos trabajar desde el mismo equipo en diferentes ramas, revertir un espacio a una versión anterior del histórico, etc.
+
+## Los commits
+
+Cuando se tenga listo un conjunto de cambios (otros SCMs lo llaman _changeset_), es hora de cerrarlos en un _commit_. Esto es una unidad atómica de cambio (i.e., no se puede aplicar medio commit; o todo el conjunto de cambios, o ninguno).
+
+Podemos ver los ficheros cambios locales con `git status`, y los cambios concretos, en formato _diff_, con `git diff`.
+
+```bash
+git status
+```
+
+```
+```
+
+Para cerrar estos cambios el primer paso será agregarlo al _stage_ con `git add`:
+
+```bash
+git add RUTA_A_AÑADIR_RECURSIVAMENTE [OTRA_RUTA...]
+```
+
```

Para cerrar estos cambios el primer paso será agregarlo al _stage_ con `git add`:

```bash
git add RUTA_A_AÑADIR_RECURSIVAMENTE [OTRA_RUTA...]
```

Si se añade un directorio, se añadirán también sus contenidos recursivamente. Ficheros fuera de seguimiento (_untracked_) empezarán a tener seguimiento si se añaden al stage.

Si de los ficheros solo quisiéramos agregar partes específicas, es posible con el modo interactivo, usando la función `patch`:

```bash
git add --interactive RUTA_A_AÑADIR_RECURSIVAMENTE
```

Si por el contrario quisiéramos eliminar ficheros en seguimiento, se haría con `git rm` (**Atención: Esto borra el fichero localmente y habría que recuperarlo de una versión anterior**)

```bash
git add README.md
git status
```

```
En la rama main
Tu rama está actualizada con 'origin/main'.

Cambios a ser confirmados:
  (usa "git restore --staged <archivo>..." para sacar del área de stage)
        modificado:     README.md
```

Si quisiéramos ver las diferencias ya confirmadas en el _stage_, usamos:

```bash
git diff --cached
```

Es posible sacar cambios del _stage_ (pero no perderlos localmente) con `git restore --staged`:

```bash
git restore --staged RUTA_A_SACAR_DEL_STAGE
```

Una vez listo el _stage_, es hora de contribuir los cambios cerrando el commit con `git commit`:

```bash
git commit
```

Se abrirá un editor para especificar un mensaje/descripción para el commit. Si se quiere definir desde el propio comando:

```bash
git commit -m "La primera línea (máx. 60-70 caracteres) se usará como título

El resto de líneas serán la descripción del commit."
```

Si todo va bien, este cambio quedará cerrado localmente en el espacio de trabajo, listo para subirse al repositorio configurado.
