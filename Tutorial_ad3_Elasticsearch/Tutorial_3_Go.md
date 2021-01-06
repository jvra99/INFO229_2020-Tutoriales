# Programacion en GO
Tutorial para la asignatura INFO229 de la Universidad Austral de Chile que tiene como objetivo en ofrecernos un lenguaje de progrmacion nuevo para ampliar nuestros 
conocimientos en el area de arquitectura de software. En esta documentacion encontrá:
    
    1. Introduccion
    2. Principales diferencias con C
    3. Instalacion en Linux
    4. Ejemplos de progracion
    5. Referencias

# 1. Introduccion
## ¿Que es GO o Golang?
   Go, también conocido como Golang, de código abierto fue creado por Google con los desarrolladores Robert Griesemer, Rob Pike y Ken Thompson en 2009. A pesar de ser un lenguaje muy joven tiene un rendimiento similar a C pero con la sintaxis amigable parecida a Python, actualmente es utilizado en aquellos programas que requieran alto rendimiento y un ejemplo de ello es Docker. Cabe destacar que este es un lengiaje de programacion concurrente y compilado.

Podemos hacer uso de Go si nos encontramos trabajando en Windows, MacOS y en ciertos sistemas GNU/Linux.

## Excepciones
   Go no utiliza excepciones. Los creadores del lenguaje han dado varios motivos para que esto sea así. La principal es que añadir una capa de excepciones agrega una complejidad innecesaria al lenguaje y al entorno de ejecución. Por definición las excepciones deberían ser excepcionales pero al final se acaban usando como controladores del flujo de la aplicación y dejan de tener la finalidad de excepcionalidad. Según los creadores, las excepciones tienen que ser realmente excepcionales y el uso que se le da mayoritariamente no justifica su existencia. 
   
## Ventajas de Go

    - Velocidad similar a C pero con una sintaxis amigable como Python.
    - Facilita el uso de buenas prácticas en el código.
    - Mantiene su rendimiento con grandes volúmenes de información.
    - Es uno de los lenguajes mejores pagados según la encuesta Stack Overflow 2019
    - Su curva de aprendizaje es suave en comparación con Java o C.
    - Es un lenguaje multiparadigma.
    - Ahorras tiempo al codear. Por ejemplo, para crear ciclos solo existe la función for.
    - Para manejar niveles de accesos de funciones es tan sencillo como colocar la primera letra en mayúscula o minúscula.


# 2. Principales diferencias con C  
Aunque su sintaxis es similar, Go difiere mucho de C. Véanse algunos ejemplos.

#### Declaraciones al revés
   En Go las declaraciones se realizan al revés desde la perspectiva de C (o C++ o Java). La idea principal en C es que se declara una variable como una expresión que denota su tipo. Según los creadores, aunque la idea detrás de la declaración de tipos en C es buena, los tipos y las expresiones gramaticales no se mezclan demasiado bien y el resultado puede ser confuso. Go sin embargo, separa la expresión y la sintaxis de tipo, lo cual simplifica las cosas. 

#### Punto y coma
En Go el uso del carácter punto y coma “;“ al final de una instrucción es opcional. 

#### Aritmetica de punteros
   Go no tiene aritmética de punteros. Según los creadores, la razón es la seguridad. Sin aritmética de punteros es posible crear un lenguaje en el que no se puede obtener una dirección ilegal que sea usada de forma incorrecta. La falta de aritmética de punteros simplifica la implementación del recolector de basura. Además, optimizando el compilador y con el hardware actual, un bucle que utiliza los índices de un array puede ser tan eficaz como un bucle que utiliza aritmética de punteros. 
   
#### ++ y --
   En Go, el uso de ++ y -- para incrementar y decrementar el valor de una variable es una sentencia y no una expresión. Además, solo puede utilizarse en su versión sufija pues según los autores, la versión prefija pierde todo su sentido en la ausencia de aritmética de punteros. 
   
Ahora hablemos de su sintaxis. Desde mi punto de vista podemos ver la sintaxis de Go como una mezcla entre Python y C ¿No me crees? Veamos un par de ejemplos.

# 3. Ejemplos de programación
## 3.1 Go "Hola mundo"
Nuestro primer programa mostrará en la pantalla el mensaje clásico “hola mundo”. Aquí el código completo:

Copia este codigo en un archivo llamado *hola-mundo.go*
```
package main

	

import "fmt"

	

func main() {
    fmt.Println("hello world")
}

```
Para ejecutar este programa:
```

```





https://es.wikipedia.org/wiki/Go_(lenguaje_de_programaci%C3%B3n)
