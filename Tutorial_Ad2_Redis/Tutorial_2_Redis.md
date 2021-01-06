# Redis para principiantes
Tutorial para la asignatura INFO229 de la Universidad Austral de Chile que tiene como objetivo en ofrecernos una herramienta nueva para ampliar nuestros conocimientos en el area de arquitectura de software. En esta documentacion encontrá:
    
    1. Introducción
    2. Instalacion con docker
    3. Ejemplo "Hola mundo"
    4. Redis-cli
    5. INstalacion en WIndows
    6. Referencias
  
# 1. Introducción
## ¿Que es Redis?
  Es una Base de Datos con un motor de almacenamiento Clave-Valor. Además, los datos residen, principalmente, en memoria, lo que proporciona a este sistema unos muy buenos tiempos de respuesta en la recuperación de la información.

## ¿A que se refiere con BD clave-valor?
  Redis está basada en una estructura de tablas hash donde cada clave tiene un valor asociado. En comparación con otras bases de datos de tipo Clave-Valor, Redis permite el uso de estructuras más complejas y flexibles que abren una serie de posibilidades ante las distintas necesidades de aplicaciones de negocio.

## Caracteristicas y  funcionalidades
### Tipos de datos
  Redis ofrece 5 estructuras de datos con los que es posible modelar la solución más adecuada para cubrir las necesidades de un proyecto:
  
    - Strings: Secuencia de bytes, es el valor básico que se puede asignar a un a Clave. Permite elementos con valor de hasta 512 MB.
    - Lists: Colecciones de cadenas (Strings). Permite la inserción o borrado de elementos en cualquier extremo de la lista (head o tail) en un tiempo constante,     manteniendo el mismo orden en el que fueron insertados. Permite hasta 4 billones de elementos por lista.
    - Sets: Se trata de una colección de Strings sin un orden determinado de almacenamiento. No permite valores duplicados para una misma Clave, por lo tanto, no se requiere de validaciones para verificar su existencia. Útiles para efectuar operaciones entre sets, tales como uniones, intersecciones y diferencias. Permite hasta 4 billones de elementos por colección.
    - Sorted Sets: Similar a los Sets, con la variante que cada elemento de un grupo de datos cuenta con una calificación (Score) asociado. Este Score determinará el orden. Permite hasta 4 billones de elementos por colección.
    - Hashes: Usado para representar objetos. Almacena conjuntos de pares Clave-Valor de cadena, asociados a una misma clave. No existe un límite de campos dentro de una Hash.
    
### Memoria y velocidad
  Gracias a que la información queda almacenada en memoria en lugar del disco, Redis ofrece rápidos accesos en la recuperación de los datos.

### Persistencia periodica a disco
  Redis nos da la posibilidad de escribir los datos en disco. Esto sirve como complemento cuando los datos trabajados superan el máximo de memoria con la que se dispone o para disponer de ellos ante fallas del servidor. Existen dos tipos de configuración:

    RDB: Intervalos específicos de conjuntos de datos (Point-in-time Snapshots)
    Append-only-file: Cada operación es escrita en un log recibida por el servidor, de tal manera que es posible reconstruir los sets de datos una vez reiniciado

### Expiracion de claves
  Cuando los datos no son requeridos después de cierto tiempo, pueden ser eliminados de manera manual o de manera automática, mediante la asignación de un «tiempo de vida» a una Clave determinada.

### Replicacion maestro - esclavo
  Permite la replicación y comunicación automática dentro de una arquitectura Maestro-Esclavo, con lo que se asegura contar con copias exactas de los datos. Un servidor maestro puede tener muchos esclavos y un esclavo a su vez puede cumplir el rol de maestro para otros esclavos.

## ¿Cuando usar Redis?
  El uso de Redis es altamente recomendable cuando la velocidad de acceso y tiempos de respuesta son críticos para una solución de negocio. Su uso es también indicado cuando se trabaja con aplicaciones en tiempo real, lo cual requiere que los datos se encuentren rápidamente accesibles para mejorar los tiempos de respuesta. Entre los casos de uso más comunes podemos encontrar:

    Sistemas de chat y mensajería
    Listado de elementos más recientes
    Contadores y uso de estadísticas en tiempo real
    Manejo y administración de carros de compra en línea
    Almacenamiento de sesiones de usuario dentro de una aplicación
    Soporte como caché de páginas web
    
# 2. Instalacion con Docker

Es facil comenzar a usar Redis instalandolo mediante el terminal

```
docker pull redis
docker run -p 6379:6379 --rm --name redis redis
```
Ahora tienes la instancia en ejecución en el puerto 6397

*Atención*: se eliminarán todos los datos, cuando se detenga Redis.

Para conectar el *redis-cli*, inicie otra ventana acoplable del terminal de forma paralela: 
```
docker run -it --link redis:redis --rm redis redis-cli -h redis -p 6379
```
¡Ahora ya esta listo tu Redis con Docker!

# 3. Ejemplo "Hola Mundo"
Debe asegurarse que el *redis-cli* este conectado correctamente.

Ahora en el la ventana del terminal donde esta conectado debe anotar la siguiente linea para guardar el primer conjunto:
#### SET 'keyname' luego 'valor'
```
SET hkey "Hello World!"
```
Que tiene como salida: OK

Luego ingrese:
```
GET hkey
```
Que tiene como salida: "Hello World!"

# 4. Redis-cli
redis-cli es el programa de interfaz de línea de comandos de Redis que permite enviar comandos a Redis y leer las respuestas enviadas por el servidor, directamente desde el terminal. El uso básico de la línea de comando está abajo:

Seleccione la base de datos y muestre el tamaño de la base de datos (el número predeterminado de la base de datos es 0): 
```
#muestra la cantidad de bases de datos
dbszise
# enter
#seleccionas una
select 1
#enter
#muestra la cantidad de bases de datos de 1
```
Para obtener informacion y estadisticas del servidor:
```
info
```
Y por ultimo, para salir de redis:
```
exit
```
# 5. Instalacion en WIndows
 Redis tiene un puerto de Windows proporcionado por 'Microsoft Open Technologies'. Puede usar el instalador msi que se encuentra en: https://github.com/MSOpenTech/redis/releases

Una vez completada la instalación, puede ver que 'Redis' es un servicio de Windows (y su estado debería ser "Iniciado")

Para escribir un ejemplo de 'Hola mundo' que use Redis en Node.js (también en Windows) puede usar el siguiente módulo npm: https://www.npmjs.com/package/redis 
```
var redis = require('redis'),
    client = redis.createClient();

client.set('mykey', 'Hello World');
client.get('mykey', function(err,res){
    console.log(res);
});
```

# 6. Referencias
Curso basico Redis [https://guiadev.com/curso-basico-de-redis/]
Introduccion Redis [https://www.koderhq.com/tutorial/redis/]
Redis para princiantes [https://blog.bi-geek.com/redis-para-principiantes/]
Empezando con redis [https://riptutorial.com/es/redis]
