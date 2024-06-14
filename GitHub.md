# **Documentación GitHub**

> [!NOTE]
> GIT es un sistema de control de versiones distribuido que permite a los desarrolladores trabajar juntos en proyectos de cualquier escala. Proporciona una forma de rastrear los cambios en el código fuente, permitiendo a los desarrolladores colaborar en proyectos sin pisar el trabajo del otro. GitHub, por otro lado, es una plataforma de colaboración y alojamiento de código para GIT que proporciona una interfaz gráfica y características adicionales como solicitudes de extracción y gestión de problemas. En esta sección, también trabajaremos en los comandos más utilizados en proyectos.

## **Comandos Generales**

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

**git restore .** - Se utiliza para eliminar cambios realizados en el repositorio local antes de subir cambios al repositorio remoto

## MERGE / REBASE / DIFF

**git merge** - Une dos o más historias de desarrollo juntas.

**git rebase “Rama”** - se utiliza para modificar el historial de confirmaciones (commits) en una rama, aplicando los cambios de otra rama. Aquí tienes una descripción del comando:

- **`git rebase`**: Este comando permite reorganizar y editar el historial de confirmaciones. En lugar de fusionar cambios como lo haría **`git merge`**, **`git rebase`** aplica los cambios de una rama a otra al mover, eliminar o combinar confirmaciones.

**git diff “Rama 1” “Rama 2”** - Previsualizar cambios de una rama a otra, facilitando la ayuda de que contiene una rama respecto a otra antes de realizar un merge o un rebase.

> [!TIP]
> Esto resolverá cualquier conflicto que surja a favor de **`feature_branch`**, efectivamente sobrescribiendo los cambios en **`development`**: `git merge feature_branch --strategy-option theirs`

## CONFIGURACIÓN

**git config — global —list** - Listar configuración global.

**git config —list** - Listar configuración del git.

**Cambio de credenciales GLOBALES**: Útil para poder interactuar con la cuenta global y permisos:

- **git config --global --unset user.name -** Elimina la credencial nombre del usuario de manera global
- **git config --global --unset user.email -** Elimina la credencial correo del usuario de manera global
- **git config --global user.name "Nombre de usuario" -** Asignar nombre de usuario
- **git config --global user.email "Correo" -** Asignar correo de usuario

**Cambio de credenciales LOCALES**: Útil para poder interactuar con otras cuentas y permisos.

1. **Accede al repositorio**: Abre una terminal o línea de comandos y navega hasta el directorio del repositorio Git para el cual deseas cambiar las credenciales.
2. **Verifica la configuración actual**: Puedes verificar la configuración actual de Git para el repositorio local ejecutando el siguiente comando:

   ```markdown
   git config --list
   ```

3. **Cambia las credenciales**: Para cambiar las credenciales de manera local para este repositorio, puedes usar los siguientes comandos:

   ```bash
   git config user.name "Tu nombre"
   git config user.email "tu@email.com"
   ```

   Esto configurará el nombre de usuario y la dirección de correo electrónico asociados con este repositorio específico. Estos detalles serán utilizados para las confirmaciones que hagas en este repositorio.

4. **Configura las credenciales de acceso remoto**: Si estás utilizando HTTPS para acceder al repositorio remoto y deseas cambiar las credenciales para este repositorio específico, puedes hacerlo eliminando las credenciales almacenadas en la caché. Esto te pedirá las credenciales la próxima vez que intentes acceder al repositorio. Ejecuta el siguiente comando para limpiar la caché:

   ```bash
   git credential-cache exit
   ```

5. **Verifica la configuración**: Puedes verificar que las credenciales se han configurado correctamente ejecutando nuevamente el comando para mostrar la configuración de Git:

   ```bash
   git config --list
   ```

   Ahora tus credenciales están configuradas localmente para este repositorio específico y no afectarán las configuraciones globales de Git en tu sistema. Esto es útil si estás colaborando en múltiples proyectos y deseas usar diferentes identidades en cada uno.

## VISUALIZACIÓN

**gitk** - Software que visualiza historial de commits.

**git reflog** - Visualizar todos los commits

**git log** - Ver los commits realizados.

- **git log -S “Cadena de texto”** - se utiliza para buscar en el historial de commits aquellos que hayan introducido o eliminado la cadena de texto.
- **git log —graph** - Muestra el historial de confirmaciones (commits) en un formato gráfico, lo que facilita la visualización de las ramificaciones y fusiones en el historial del repositorio.
- **git log —all —graph** - Similar al anterior, pero muestra todas las ramas del repositorio en el gráfico, no solo la rama actual. Esto es útil para ver cómo se han desarrollado las ramas a lo largo del tiempo.
- **git log —all —graph —decorate —oneline** - Proporciona un historial gráfico con información adicional. Incluye todas las ramas, decora las confirmaciones con nombres de ramas y etiquetas, y muestra cada confirmación en una sola línea para una visualización más compacta.
- **git log —stat** - Muestra estadísticas resumidas junto con cada confirmación, lo que incluye qué archivos se modificaron, cuántas líneas se agregaron o eliminaron en cada archivo y el resumen de los cambios realizados en esa confirmación.

**git shortlog -sn** - Conteo de commits realizados por cada miembro.

- **git shortlog -sn —all** - Conteo de commits realizados por cada miembro, aún los borrados.

**git tag** - Es utilizado para crear, listar o verificar etiquetas. Las etiquetas en Git son referencias inmutables a puntos específicos en el historial de confirmaciones.

- **git tag “Nombre del tag”** - Utilizado para colocar una etiqueta al último commit, usualmente se utilizan para notificar versiones en los commits para tenerlas presentes en un punto.
- **git tag “Nombre del tag” “Hash”** - Seguido de lo anterior, se utiliza para crear una etiqueta, pero en este caso se le proporciona el identificador de un commit para aplicarle la etiqueta.

**git grep “Palabra”** - Busque patrones especificados en los archivos de seguimiento en el árbol de trabajo, blobs registrados en el archivo de índice, o blobs en objetos de árbol dados. Patrones son listas de una o más expresiones de búsqueda separadas por una nueva línea Caracteres.

- **git grep -n “Palabra”** - Indica en que línea del archivo se encuentra ubicado la coincidencia.
- **git grep -c “Palabra”** - Conteo de cuantas coincidencias se encuentran en el archivo
