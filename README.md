## CLASE 1

### ¿Cómo iniciar un proyecto con Git?

Para crear un nuevo repositorio local:

```
git init <nombre-del-proyecto>
```

O bien, si ya tienes una carpeta existente, ve a la raíz del proyecto y ejecuta:

```
git init
```

### Ayuda en Git

Para consultar ayuda sobre comandos:

```
git init -h
```

Para ver la documentación detallada en el navegador:

```
git init --help
```

### Estados de Git

Todo archivo en un repositorio puede estar en uno de estos tres estados:

* **Modified**
* **Staged**
* **Committed**

---

**Modified**
El archivo ha sido modificado pero aún no preparado para su confirmación.

Cuando creas o eliminas un archivo, Git lo marca como *modified*.

##### Eliminar archivo:

```
git rm <nombre-del-archivo>
```

##### Ver estado:

```
git status
```

##### Restaurar archivo:

```
git restore <nombre-del-archivo>
```

---

**Staged**
El archivo ha sido preparado para su confirmación.

##### Añadir archivo al área de preparación:

```
git add <nombre-del-archivo>
```

---

**Committed**
Los cambios han sido confirmados y almacenados en el repositorio.

##### Confirmar cambios:

```
git commit -m "mensaje del commit"
```

##### Ver historial:

```
git log
```

##### Ver historial reducido:

```
git log --oneline
```

##### Ver historial como gráfico:

```
git log --graph
```

##### Combinación de ambos:

```
git log --graph --oneline
```

---

## CLASE 2

##### Crear rama:

```
git branch <nombre-de-la-rama>
```

##### Cambiar de rama:

```
git switch <nombre-de-la-rama>
```

o

```
git checkout <nombre-de-la-rama>
```

##### Crear y cambiar de rama en un solo paso:

```
git switch -c <nombre-de-la-rama>
```

##### Ver ramas locales:

```
git branch
```

##### Ver ramas locales y remotas:

```
git branch -a
```

##### Fusionar ramas:

```
git merge <nombre-de-la-rama>
```

##### Eliminar rama:

```
git branch -d <nombre-de-la-rama>
```

##### Forzar eliminación:

```
git branch -D <nombre-de-la-rama>
```

### Conflictos

Ocurren cuando Git no puede determinar qué cambios conservar durante una fusión. Puedes elegir qué conservar o combinar ambos cambios manualmente.

---

## CLASE 3

**Origin:** nombre por defecto para el repositorio remoto.

##### Enlazar repositorio local con remoto:

```
git remote add origin <url-del-repositorio>
```

##### Ver conexiones remotas:

```
git remote -v
```

##### Enviar cambios:

```
git push origin main
```

##### **No usar** este comando en equipo:

```
git push -f origin main
```

##### Clonar repositorio remoto:

```
git clone <url-del-repositorio>
```

##### Crear rama remota:

```
git push origin <nombre-de-la-rama>
```

##### Actualizar ramas remotas:

```
git fetch
```

##### Limpiar ramas remotas eliminadas:

```
git remote prune origin
```

---

## CLASE 4

### Git Push

Sube cambios al repositorio remoto.

### Git Pull

Trae cambios del repositorio remoto al local.

##### Configurar `git push` para no repetir `origin`:

```
git push -u origin <nombre-de-la-rama>
```

##### Configurar `git pull` con `push`:

```
git push --set-upstream origin <nombre-de-la-rama>
```

##### Subir todas las ramas:

```
git push --all
```

##### Descargar todas las ramas:

```
git pull --all
```

### Pull Request

Es una solicitud de fusión de código. Debe ser clara, enfocada en una sola tarea y bien explicada.

---

## CLASE 5 y 6

### Git Flow

* **Main**: código en producción.
* **Develop**: código en pruebas.
* **Feature**: nuevas funcionalidades.
* **Release**: preparaciones para producción.
* **Hotfix**: correcciones urgentes.

### GitHub Flow

Modelo simple centrado en la rama `main`. Las otras ramas se fusionan mediante Pull Request.

### Trunk Based Development

Se trabaja directamente en la rama principal.

#### SHIP / SHOW / ASK

* **Ship**: se fusiona sin revisión.
* **Show**: se muestra para revisión rápida.
* **Ask**: se abre discusión antes de fusionar.

### Buenas prácticas

* Hacer commits frecuentes pero significativos.
* Mensajes de commit claros, sin puntos ni suspensivos.
* Limitar a 50 caracteres.
* Nombres de ramas descriptivos, basados en acciones.

---

## CLASE 7

### Deshacer cambios

Situaciones comunes:

* El proyecto dejó de funcionar.
* Eliminaste código importante.
* Necesitas volver a un estado anterior.

### Git Reset (destructivo)

##### Eliminar cambios y volver a un commit:

```
git reset --hard <ID-del-commit>
```

##### Volver a un commit sin eliminar cambios:

```
git reset --soft <ID-del-commit>
```

### Git Revert (no destructivo)

Crea un nuevo commit que revierte los cambios de uno anterior:

```
git revert <ID-del-commit>
```

### Git Checkout

Recuperar archivos de un commit específico:

```
git checkout <ID-del-commit> -- <archivo>
```

---

## CLASE 8

### Hooks

Permiten ejecutar scripts automáticamente al ocurrir eventos en Git.

#### Crear un hook

Crear un archivo en `.git/hooks` con el nombre del hook deseado. Puedes usar bash, Python, Node, etc.

#### Hooks del lado del cliente

* **pre-commit**: evitar commits con muchos archivos.
* **prepare-commit-msg**: modificar el mensaje del commit.
* **commit-msg**: validar el mensaje del commit.
* **post-commit**: enviar notificaciones (e.g., Slack).
* **pre-push**: ejecutar tests.
* **post-checkout** y **post-merge**: limpiar ramas o archivos.

#### Hooks del lado del servidor

* **pre-receive**: validar commits entrantes.
* **update**: control granular de actualizaciones.
* **post-receive**: enviar alertas tras recibir cambios.

---

### Alias

Permiten definir comandos personalizados.

Ejemplos:

```
git co --> git commit
git st --> git status
```

Crear un alias:

```
git config --global alias.<nombre> "<comando>"
```

---

### Trucos de Git

##### Guardar cambios temporalmente:

```
git stash
```

Guardar también archivos no rastreados:

```
git stash -u
```

Aplicar y eliminar el stash:

```
git stash pop
```

##### Aplicar cambios de un commit específico:

```
git cherry-pick <SHA>
```

##### Buscar el commit que causó un error:

```
git bisect start
git bisect bad
git bisect good
git bisect reset
```

##### Cambiar el mensaje del último commit:

```
git commit --amend -m "nuevo mensaje"
```

##### Recuperar archivo de otro commit:

```
git checkout <SHA> <archivo>
```

---

¿Deseas que este archivo limpio te lo prepare como descarga `.md` o lo sigues trabajando tú?
