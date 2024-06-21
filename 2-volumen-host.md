# VOLUMEN TIPO HOST
Un volumen host (o bind mount) es un tipo de volumen donde se monta un directorio o archivo específico del sistema de archivos del host en un contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```

### Crear un volumen tipo host con la imagen nginx:alpine, para la ruta carpeta host: directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html esta ruta se obtiene al revisar la documentación
![Volúmenes](imagenes/volumen-host.PNG)
# COMPLETAR CON EL COMANDO
```
docker run -d --name mi-nginx -p 80:80 -v C:\Users\LabP3E010\html:/usr/share/nginx/html nginx:alpine
```
### ¿Qué sucede al ingresar al servidor de nginx?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
El servidor de nginx es inaccesible

### ¿Qué pasa con el archivo index.html del contenedor?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
El archivo index.html dentro del contenedor se ve afectado directamente por los contenidos de la carpeta C:\Users\LabP3E010\html del host. Cualquier archivo index.html presente en esta ruta del host será servido por Nginx cuando se acceda al servidor a través del puerto 80. Al no haber ningun archivo html no se mostrara nada al acceder al servidor.



### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de nginx/html
### ¿Qué sucede al ingresar al servidor de nginx?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA

Al ingresar un template y descomprimirlo dentro de esta carpeta, al volver a acceder al servicio se puede observar que este servicio a tomado el template descargado.

### Eliminar el contenedor
# COMPLETAR CON EL COMANDO
```
docker rm mi-nginx
```

### ¿Qué sucede al crear nuevamente el mismo contenedor con volumen de tipo host a los directorios definidos anteriormente?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA

Al crear nuevamente el mismo contenedor con volumen de tipo host a los mismos directorios definidos anteriormente (C:\Users\LabP3E010\html en el host y /usr/share/nginx/html en el contenedor), el nuevo contenedor recuperará automáticamente todos los archivos y configuraciones que existían previamente en la carpeta html del host. Esto incluye cualquier cambio o adición de archivos que se hayan realizado durante la ejecución anterior del contenedor.
### ¿Qué hace el comando pwd?
El comando pwd muestra el directorio actual en la línea de comandos.
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA

Si quieres incluir el comando pwd dentro de un comando de Docker, lo puedes hacer de diferentes maneras dependiendo del shell que estés utilizando.


### Volumen tipo host usando PWD y PowerShell
```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v ${PWD}/<ruta relativa>:<ruta absoluta> <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (Git Bash)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd -W)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (en Linux)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

