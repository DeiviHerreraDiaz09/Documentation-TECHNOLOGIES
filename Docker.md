# **Documentacion Docker**

> [!NOTE]
> Docker es una plataforma de código abierto que permite a los desarrolladores construir, desplegar y gestionar aplicaciones en contenedores. Los contenedores de Docker empaquetan una aplicación con todas sus dependencias en una unidad estandarizada para el desarrollo de software, lo cual asegura que la aplicación se ejecute de manera uniforme en cualquier entorno.

## **Comandos Terminal**:

| **REPOSITORY**   | Nombre de la imagen que descargamos.                                                       |
| ---------------- | ------------------------------------------------------------------------------------------ |
| **TAG**          | Información útil sobre una versión o variante específica de una imagen.                    |
| **IMAGE ID**     | Identificador único de la imagen.                                                          |
| **CREATED**      | Información sobre cuando fue creada la respectiva imagen.                                  |
| **SIZE**         | Cuanto espacio en disco duro está utilizando la imagen                                     |
| **CONTAINER ID** | Identificador del contenedor, un poco más reducido                                         |
| **IMAGE**        | Indica en base a que imagen se ha creado el contenedor.                                    |
| **STATUS**       | Estado que tiene el contenedor.                                                            |
| **PORTS**        | Puertos por el cual está el contenedor y que hay la posibilidad de entes externos acceder. |
| **NAMES**        | Nombre respectivo del contenedor.                                                          |

- **docker images**: Listado completo de todas las imágenes descargadas.
- **docker pull “Nombre de la imagen”:”Versión”**: Descargar una imagen, si no se llega a especificar la versión por naturaleza nos traerá la versión actual más actualizada.
- **docker image rm node:”Versión”**: Borrar una imagen.
- **docker create “nombre imagen para inicializar el contenedor”**: Creación de contenedores, devuelve un identificador del contenedor, id necesario para poder ejecutar nuestro contenedor.
- **docker start “Identificador del contenedor, nombre del contenedor”**: Ejecutar contenedor, devuelve el id del contenedor.
- **docker ps**: Verificar que imágenes andan ejecutándose.
- **docker ps -a**: Reflejar todos los contenedores así no estén ejecutándose en tiempo real
- **docker stop “identificador del contenedor, nombre del contenedor”**: Detener algún contenedor que se estaba ejecutando, devuelve el identificador del contenedor.
- **docker rm “nombre del contenedor”**: Eliminar contenedor, en este caso con el nombre.
- **docker create —name “Nombre que se quiere para el contenedor” “En base a que imagen, ejemplo ‘mongo’ ”**: asignar nombre a un contenedor, devuelve el id del contenedor.
- **docker create -p”puerto de la maquina actual”:”puerto que está utilizando el contenedor” —name “nombre del contenedor” “nombre de la imagen para generar el contenedor”:** Mapeo de puertos con los puertos de los contenedores.
- **docker logs “Identificador del contenedor, nombre del contenedor”**: Detallar ejecuciones por debajo “REGISTROS”.
- **docker run -d “Imagen”**: En la ejecución de este comando pasa por varios filtros, el “-d” ayuda a lanzarnos directamente a la línea de comandos y que no se generen por default los logs por debajo.

## **ABREVIACIÓN DEL COMANDO RUN**

> [!IMPORTANT]
> Puedes utilizar este comando para agilizar la creación de contenedores con sus diferentes imágenes.
>
> ```docker
> docker run —name mongoTest -p27017:27017 mongo
> ```

## **Dockerfile**

Dockerfile es un archivo de texto que Docker lee para construir automáticamente una imagen de Docker. Contiene una serie de instrucciones y comandos que se ejecutan en secuencia para configurar la imagen. Este archivo puede incluir instrucciones para establecer el sistema operativo base, instalar aplicaciones y librerías, copiar archivos y configurar variables de entorno, entre otras cosas.

Dockerfile permite estandarizar las configuraciones y asegurar que todos los usuarios que ejecuten la imagen tengan el mismo entorno y configuración. Esto facilita el despliegue y la distribución de aplicaciones, ya que puedes estar seguro de que la aplicación se comportará de la misma manera en cualquier lugar donde se ejecute la imagen de Docker.

El Dockerfile se ejecuta mediante el comando `docker build`, que crea la imagen basada en las instrucciones del Dockerfile. Una vez que se ha creado la imagen, se puede ejecutar en un contenedor con el comando `docker run`.

1. **`FROM`**: Especifica la imagen base desde la cual construir la nueva imagen. Por ejemplo, **`FROM ubuntu:latest`** utiliza la última versión de la imagen oficial de Ubuntu como base.
2. **`COPY`**: Copia archivos o directorios desde el sistema de archivos local al sistema de archivos del contenedor. Por ejemplo, **`COPY ./app /app`** copiaría el contenido del directorio "app" del sistema local al directorio "/app" del contenedor.
3. **`ADD`**: Similar a **`COPY`**, pero tiene algunas características adicionales, como la capacidad de extraer archivos comprimidos y acceder a URLs. Sin embargo, se recomienda usar **`COPY`** para la copia simple de archivos.
4. **`WORKDIR`**: Establece el directorio de trabajo para las instrucciones **`RUN`**, **`CMD`**, y **`ENTRYPOINT`**. Por ejemplo, **`WORKDIR /app`** cambiará el directorio de trabajo a "/app".
5. **`RUN`**: Ejecuta comandos en la imagen durante la construcción. Por ejemplo, **`RUN apt-get update && apt-get install -y nginx`** instalará el servidor web Nginx durante la construcción de la imagen.
6. **`EXPOSE`**: Informa a Docker que el contenedor escuchará en los puertos especificados en tiempo de ejecución. Por ejemplo, **`EXPOSE 80`** indica que el contenedor escuchará en el puerto 80.
7. **`CMD`**: Proporciona valores predeterminados para un contenedor en tiempo de ejecución. Puedes especificar un comando y sus argumentos. Por ejemplo, **`CMD ["nginx", "-g", "daemon off;"]`** define el comando predeterminado para ejecutar Nginx en el contenedor.
8. **`ENTRYPOINT`**: Similar a **`CMD`**, pero proporciona un comando predeterminado que no se puede anular fácilmente al ejecutar el contenedor con argumentos adicionales.
9. **`ENV`**: Establece variables de entorno en la imagen. Por ejemplo, **`ENV DATABASE_URL=mysql://user:password@localhost:3306/db`** define una variable de entorno llamada DATABASE_URL.
10. **`VOLUME`**: Crea un punto de montaje para almacenar datos persistentes fuera del contenedor. Por ejemplo, **`VOLUME /data`** crea un volumen en el directorio "/data" del contenedor.
11. **`ARG`**: Define argumentos que se pueden pasar a la imagen en tiempo de construcción. Pueden usarse para personalizar la construcción de la imagen sin modificar el Dockerfile directamente.


## **Docker Compose**

Docker Compose es una herramienta que permite definir y gestionar aplicaciones multi-contenedor con Docker. Se utiliza principalmente en entornos de desarrollo, pruebas y despliegues de etapas, ya que permite definir un entorno completo para una aplicación en un solo archivo, y luego ejecutar la aplicación con un solo comando.

Docker Compose utiliza un archivo YAML para definir los servicios, redes y volúmenes de una aplicación. Cada servicio en un archivo Compose representa un contenedor en ejecución de una imagen de Docker. Los servicios pueden interactuar entre sí a través de redes definidas en el archivo Compose, y los datos pueden persistir a través de volúmenes también definidos en el archivo Compose.

Algunos comandos básicos de Docker Compose incluyen:

- **`docker-compose up`**: Construye, (re)crea, inicia y adjunta a contenedores para un servicio. Si ya existen contenedores para un servicio, Docker Compose reutilizará los existentes y solo recreará los que han cambiado.
- **`docker-compose down`**: Detiene y elimina todos los contenedores de un proyecto.
- **`docker-compose build`**: Construye o reconstruye los servicios de un proyecto.
- **`docker-compose logs`**: Muestra los registros de un servicio de un proyecto.

Algunos de los campos más comunes en un archivo de Docker Compose incluyen:

- **`version`**: Especifica la versión de la sintaxis del archivo Compose.
- **`services`**: Define los servicios (contenedores) que componen la aplicación.
- **`build`**: Proporciona opciones de construcción para la imagen de un servicio.
- **`image`**: Especifica la imagen de Docker que se utilizará para un servicio.
- **`ports`**: Mapea los puertos del contenedor a los puertos del host.
- **`volumes`**: Monta rutas como volúmenes de datos, ya sea en el host o en otros contenedores.
- **`networks`**: Define las redes a las que se conectará un servicio.