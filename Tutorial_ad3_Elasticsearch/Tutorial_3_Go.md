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

# 3. Instalación en Linux
### Metodo manual 
Si prefieres la última versión, visita el sitio web de golang y descarga el archivo de archivo más reciente y siga las instrucciones para instalarlo.
```
$ wget https://storage.googleapis.com/golang/go1.8.linux-amd64.tar.gz
```
```
$ sudo tar -xzf go1.8.linux-amd64.tar.gz -C /usr/local
```
Para trabajar con el lenguaje Go, crea un directorio de área de trabajo en tu directorio home. Go mantendrá todos los archivos aquí.
```
mkdir ~/go_proyecto
```
Asegúrate de que tienes que configurar las variables de entorno relacionadas con Go para que funcione. Agrega una línea usr/local/go/bin a tu /etc/profile para una instalación de todo el sistema o agrega $HOME/.profile para la instalación específica del usuario.

Cuando instala Go en una ubicación diferente en lugar de la predeterminada /usr/local/go, debes configurar la variable de entorno GOROOT para que apunte al directorio.
```
export PATH=$PATH:/usr/local/go/bin
```
     *NOTA: Por ejemplo, si instalaste Go en tu directorio home, debes agregar comandos como los siguientes a $HOME/.profile*
 ```
 export GOROOT=$HOME/go
 ```
 ```
 export PATH=$PATH:$GOROOT/bin
 ```
Configurar las variables de entorno GOPATH y GOBIN:
GoPATH es espacio de trabajo del proyecto. Agrega las siguientes líneas al archivo $HOME/.profile.
```
export GOPATH=$HOME/go_proyecto
```
```
export GOBIN=$GOPATH/bin
```
Ejecute el siguiente comando para que los cambios surtan efecto.
```
$ source ~/.profile
```
### Comprobar si tuvo una instalación exitosa
Ejecute el siguiente comando para ver la versión del lenguaje Go.
```
$ go version
```
Compruebe las variables de entorno de Go:
```
$ go env
```
Una vez instalado correctamente Go podemos probarlo con algunos programas basicos.
 
# 4. Ejemplos de programación
## 4.1 Go "Hola mundo"
Nuestro primer programa mostrará en la pantalla el mensaje clásico “hola mundo”. Aquí el código completo:

Copia este codigo en un archivo llamado *hola-mundo.go*
```
package main

	

import "fmt"

	

func main() {
    fmt.Println("hola mundo")
}

```
Para ejecutar este programa debes encontrarte en la carpeta donde esta el programa *hola-mundo.go*
```
$ go run hola-mundo.go
```
Salida: hola mundo

## 4.2 Go "Valores"
Go maneja varios tipos de valores incluyendo cadenas, enteros, flotantes, booleanos, etc. Aquí algunos ejemplos básicos.

Copia este codigo en un archivo llamado *valores.go*
```
package main

import "fmt"

func main() {

    // Cadenas, que pueden ser concatenadas con `+`.
    fmt.Println("go" + "lang")

    // Enteros y flotantes
    fmt.Println("1+1 =", 1+1)
    fmt.Println("7.0/3.0 =", 7.0/3.0)

    // Booleanos, con operadores booleanos, tal y como lo esperarías.
    fmt.Println(true && false)
    fmt.Println(true || false)
    fmt.Println(!true)
}
```
Ejecutando este programa tenemos como salida:
```
$ go run valores.go
golang
1+1 = 2
7.0/3.0 = 2.3333333333333335
false
true
false

```
## 4.3 GO "Constantes"
Go soporta constantes de tipo carácter, cadena, booleano y valores numéricos.
const se usa para declarar valores constantes.Una declaración const puede usarse donde mismo que una declaración var.

Copia este codigo en un archivo llamado *constantes.go*
```
package main

import "fmt"
import "math"

// `const` se usa para declarar valores constantes.
const s string = "constant"

func main() {
    fmt.Println(s)

    // Una declaración `const` puede usarse donde mismo que
    // una declaración `var`.
    const n = 500000000

    // Las expresiones constantes se ejecutan con precisión
    // arbitraria.
    const d = 3e20 / n
    fmt.Println(d)
```
Ejecutando este programa tenemos como salida:
```
$ go run constantes.go 
constant
6e+11
600000000000
-0.28470407323754404

```
## 4.4 GO "FOR"
for es la única estructura de control iterativa en Go. Hay tres tipos básicos de ciclos for.
El tipo más básico, con una condición sencilla. El clásico ciclo for con estructura inicializar/condición/después. Y el for sin ninguna condición iterará repetidamente hasta que se use break para salir del ciclo o return para regresar un valor de la función que lo contiene.

Copia este codigo en un archivo llamado *for.go*
```
package main

import "fmt"

func main() {

    // El tipo más básico, con una condición sencilla.
    i := 1
    for i <= 3 {
        fmt.Println(i)
        i = i + 1
    }

    // El clásico ciclo `for` con estructura inicializar/condición/después.
    for j := 7; j <= 9; j++ {
        fmt.Println(j)
    }

    // `for` sin ninguna condición iterará repetidamente
    // hasta que se use `break` para salir del ciclo o `return`
```
Ejecutando este programa tenemos como salida:
```
$ go run for.go
1
2
3
7
8
9
loop
```
## 4.5 GO "if/else"
La derivación con if y else en Go se hace de manera directa.

Copia este codigo en un archivo llamado *if-else.go*
```
package main

import "fmt"

func main() {

    // Ejemplo básico.
    if 7%2 == 0 {
        fmt.Println("7 es par")
    } else {
        fmt.Println("7 es impar")
    }

    // Puedes utilizar un `if` sin un else.
    if 8%4 == 0 {
        fmt.Println("8 es divisible entre 4")
    }

    // Los condicionales pueden ser precedidos por
    // una declaración; cualquier
```
Ejecutando este programa tenemos como salida:
```
$ go run if-else.go
7 es impar
8 es divisible entre 4
9 tiene 1 digito
```

Hay muchas mas estrucuras y herramientas para poder programar en Go. En este link hay ams ejemplos [http://goconejemplos.com/] que les pueden ser util a la hora de sacarle provecho a este lenguaje de programacion. 

# Referencias
GO wikipedia [https://es.wikipedia.org/wiki/Go_(lenguaje_de_programaci%C3%B3n)]
Ejemplos Go [http://goconejemplos.com/]
¿Como instalar go en linux? [https://comoinstalar.info/go-golang-en-linux/]
Desarrollo backend con Go [https://platzi.com/backend-go/?gclid=Cj0KCQiA3NX_BRDQARIsALA3fIIjf4uNB_kwhWaJZFXaCGfA90E3qGsgmkwYn0elPTTYoW98b5vfrXMaAtmCEALw_wcB&gclsrc=aw.ds]
¿Que es GO? [https://codigofacilito.com/articulos/que-es-go]

