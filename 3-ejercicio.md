## Esquema para el ejercicio

![Imagen](img/esquema-ejercicio3.PNG)

### Crear red net-wp

# docker network create net-wp -d bridge

### Para que persista la información es necesario conocer en dónde mysql almacena la información.

# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/

En el esquema del ejercicio carpeta del contenedor (a) es /var/lib/mysql (COMPLETAR CON LA RUTA)

Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?

# Almacena todos los datos de la base de datos de tipo MySQL. Tiene las tablas e índices, los elementos de MySQL.

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD

# docker run -d --name docker-mysql --network net-wp -e MYSQL_ROOT_PASSWORD=P@ssw0rd -e MYSQL_DATABASE=database -e  MYSQL_USER=user -e  MYSQL_PASSWORD=P@ssw0rd -v D:/CES/ejercicio3/db:/var/lib/mysql mysql:8

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?

# Tiene archivos y carpetas relacionados con la base de datos. Hay una carpeta para guardar las bases de datos y una carpeta con los logs.

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.

# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/

En el esquema del ejercicio la carpeta del contenedor (b) es /var/www/html (COMPLETAR CON LA RUTA)

Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)

# docker run -d --name docker-wordpress --network net-wp -e WORDPRESS_DB_HOST=docker-mysql -e WORDPRESS_DB_USER=user -e WORDPRESS_DB_PASSWORD=P@ssw0rd -e WORDPRESS_DB_NAME=database -v D:/CES/ejercicio3/www:/var/www/html wordpress

### Personalizar la apariencia de wordpress y agregar una entrada

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

# Se ha mantenido la configuración en wordpress, entonces ya no fue necesario volver a configurar.
