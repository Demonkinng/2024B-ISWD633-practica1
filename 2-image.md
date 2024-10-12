# Imagen

Es un archivo único que contiene todos los programas, librerías, dependencias y configuraciones necesarias para instalar y/o ejecutar una aplicación o un conjunto de aplicaciones.
![Imagen](img/imagen.PNG)

## ¿Cuál es la relación entre una imagen y un contenedor?

Un contenedor es una instancia ejecutable creada a partir de una imagen, mientras que la imagen es un archivo que contiene todo lo necesario para ejecutar una aplicación, por lo cual un contenedor depende de una imagen para su creación.  
![Imagen y contenedores](img/imagenContenedores.JPG)

## Comandos para imágenes

### Descargar imagen

Descarga la última versión de la imagen disponible en el registro de Docker.

```docker
docker pull <nombre imagen>
```

Descarga una versión específica de la imagen, cada imagen tiene etiquetas (tags) para diferentes versiones.
Una imagen puede tener la etiqueta latest para representar la última versión, si no se especifica una etiqueta se hará referencia a la versión latest.

```docker
docker pull <nombre imagen>:<tag>
```

Descargar la imagen **hello-world**

```docker
docker pull hello-world
```

**¿Qué es nginx**

Es un servidor web y proxy inverso diseñado para manejar alto tráfico, optimizando la entrega de contenido y balanceando la carga de aplicaciones.
Permite manejar grandes volúmenes de conexiones concurrentes de manera eficiente, por lo cual, es utilizado ampliamente en arquitecturas web modernas.

Descargar la imagen **nginx** en la versión **alpine**

```docker
docker pull nginx:alpine
```

### Listar imágenes

```docker
docker images
```

![Listado de imagenes](img/listadoImagenes.PNG)

**Identificadores**

En Docker, se utilizan varios identificadores para diferenciar de manera única los elementos del sistema, como imágenes, contenedores, volúmenes y redes. Estos identificadores son generados automáticamente por Docker y son únicos dentro del contexto del sistema Docker en el que se encuentran.

### Inspeccionar una imagen

El comando docker inspect se utiliza para obtener información detallada sobre un objeto de Docker específico, como un contenedor, una imagen, un volumen o una red. Proporciona información en formato JSON sobre el objeto especificado.

```
docker inspect <nombre imagen>
docker inspect <nombre imagen>:<tag>
```

Inspeccionar la imagen hello-world

```docker
docker inspect hello-world
```

**¿Con qué algoritmo se está generando el ID de la imagen?**

Docker utiliza un algoritmo de hashing llamado SHA-256 (Secure Hash Algorithm 256) para generar los ID de las imágenes.

### Filtrar imágenes

```docker
docker images | grep <termino a buscar>
```

### Para eliminar una imagen

Eliminar permanentemente la imagen de tu sistema Docker.

```docker
docker rmi <nombre imagen>:<tag>
```

Eliminar la imagen hello-world

```docker
docker rmi hello-world
```

-f: Es la opción para forzar la eliminación de la imagen incluso si hay contenedores en ejecución que utilizan esa imagen.
Cuando eliminas una imagen Docker, Docker no elimina automáticamente los contenedores que se han creado a partir de esa imagen. Esto significa que, aunque hayas eliminado la imagen, el contenedor seguirá ejecutándose normalmente.  
**Considerar**
Eliminar una imagen no afecta a los contenedores que se han creado a partir de esa imagen, a menos que esos contenedores dependan de archivos o configuraciones específicas de la imagen eliminada. En ese caso, es posible que los contenedores se comporten de manera inesperada después de eliminar la imagen.
Es una buena práctica detener y eliminar todos los contenedores que dependan de una imagen antes de eliminar la imagen en sí.

```docker
docker rmi -f <nombre imagen>:<tag>
```
