# Documentación GitHub

> [!NOTE]
> GIT es un sistema de control de versiones distribuido que permite a los desarrolladores trabajar juntos en proyectos de cualquier escala. Proporciona una forma de rastrear los cambios en el código fuente, permitiendo a los desarrolladores colaborar en proyectos sin pisar el trabajo del otro. GitHub, por otro lado, es una plataforma de colaboración y alojamiento de código para GIT que proporciona una interfaz gráfica y características adicionales como solicitudes de extracción y gestión de problemas. En esta sección, también trabajaremos en los comandos más utilizados en proyectos.

## Comandos Generales

**git init** - Inicializa un nuevo repositorio GIT en el directorio actual.

**git remote add “Nombre de la conexión remota” “Url del repositorio”** - Enlazar repositorio local con uno remoto por medio de una conexión.
- **git remote show** - Muestra información detallada sobre un repositorio remoto.
- **git remote -v** - Muestra las URL de los repositorios remotos vinculados y sus nombres. Es útil para verificar las conexiones remotas configuradas.


**git clone** - Copia un repositorio GIT remoto a un directorio local.

**git checkout** - Cambia de rama o restaura archivos del árbol de trabajo.

- **git checkout -b “Nombre de rama”** - Creación de una rama.

**git branch**

- **git branch** - Listado de ramas.
- **git branch -a** - Borrar ramas.
- **git branch “Nombre de rama”** - Creación de ramas.
- **git branch -r** - Listado de ramas remotas.

**git “Comando” —help** - Información acerca del comando.

**git add** - Agrega archivos al índice del repositorio GIT.

**git stash** - Guardar cambios temporalmente.

- **git stash list** - Listar cambios temporales.
- **git stash pop** - Traer los cambios temporales.
- **git stash branch “Rama”** - Guardar los cambios temporales en una rama.

**git commit** - Guarda los cambios en el repositorio GIT.

- **git commit —amend** - Enmienda un commit, por si faltaron unos cambios que no sientas la necesidad de realizar un nuevo commit.
- **git commit -am** - Realiza en un comando las acciones de add y commit.

**git status** - Muestra el estado de los archivos en el índice versus el directorio de trabajo.

**git pull** - Actualiza el repositorio local con los cambios del repositorio remoto.

**git push** - Envía los commits locales al repositorio remoto.

**git reset —hard “Número/hash de commit”** - Se utiliza para deshacer cambios en un repositorio Git y restablecer el estado del proyecto al commit específico indicado por el "Número de commit”

## MERGE / REBASE / DIFF

**git merge** - Une dos o más historias de desarrollo juntas.

**git rebase “Rama”** - se utiliza para modificar el historial de confirmaciones (commits) en una rama, aplicando los cambios de otra rama. Aquí tienes una descripción del comando:

- **`git rebase`**: Este comando permite reorganizar y editar el historial de confirmaciones. En lugar de fusionar cambios como lo haría **`git merge`**, **`git rebase`** aplica los cambios de una rama a otra al mover, eliminar o combinar confirmaciones.

**git diff “Rama 1” “Rama 2”** - Previsualizar cambios de una rama a otra, facilitando la ayuda de que contiene una rama respecto a otra antes de realizar un merge o un rebase.

> [!TIP]
> Esto resolverá cualquier conflicto que surja a favor de **`feature_branch`**, efectivamente sobrescribiendo los cambios en **`development`**: `git merge feature_branch --strategy-option theirs`