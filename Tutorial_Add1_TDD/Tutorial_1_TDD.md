#TDD como metodologia de diseño de software

##¿Que es TDD?
  Es una metodología de desarrollo cuyo objetivo es crear primero las pruebas y luego escribir el software. Es decir, desarrollo guiado por pruebas.Es una 
metodología de desarrollo cuyo objetivo es crear primero las pruebas y luego escribir el software. Sus siglas en Inglés son: **Test Driven Development** y 
en español significa: **Desarrollo guiado por pruebas**.

##¿Porque es importante aplicarlo?
  Esta metodología se ha convertido en una muy popular entre los desarrolladores ya que es bastante sencilla y permite alcanzar la máxima calidad posible 
de tu código como un código más robusto, más seguro, más mantenible y una mayor rapidez en el desarrollo. El desarrollo dirigido por test consiste en escribir 
las pruebas que el código ha de superar, comprobar que fallan, implementar la mínima  cantidad de código que permita pasar las pruebas y, una vez superadas 
las pruebas, refactorizar el código.

##Beneficios
Razones para hacerlo:

    - Genera confianza gracias a tener pruebas que garantizan el correcto funcionamiento del código.
    - Mejora el diseño y la calidad del código.
    - Minimiza la cantidad del código a escribir ya que al realizar pruebas, se evita la posibilidad de escribir código que no se va a utilizar. 
    - Permite un desarrollo más rápido y optimizarás el mantenimiento y evolución del código.
    - Satisfacción del cliente.
    
Desarrollar un software en muchas ocasiones viene aparejado de la presión por terminarlo en determinado tiempo, es por ello que estas herramientas te ayudarán 
a construir un proyecto de software de calidad desde el principio.

##Herramientas
No hay una herramienta como tal para implementar la metodología de TDD. Más bien, existen herramientas que nos ayudan a escribir y correr nuestras pruebas de 
forma automatizada.

    - Java - JUnit, REST assured, Selenium, Mockito, Spock, etc.
    - JavaScript - Jasmine, AVA, Tape, Mocha, Jest, etc.
    - PHP - PHPUnit, Codeception, Behat, PHPSpec, SimpleTest, Storyplayer, etc.
    - Python - Existen librerías nativas o instalables que facilitan el desarrollo y automatización de pruebas en Python como unittest, pytest o Hypothesis.
    - Go - El paquete testing nativo de Go.

No se puede definir cual framework es el mejor para tu lenguaje de programación, se debe trabajar con varios y escojer con el que mejor les guste.

###Ciclo de desarrollo
Para el uso del TDD se deben combinar 2 metodologías: Test-first development (escribir las pruebas primero) y Refactoring (refactorización de código). 
Para esto, se usa un ciclo de desarrollo que consta de 3 partes principales:

    1. La prueba debe fallar. (Red: Muchas herramientas muestran los fallos de las pruebas en rojo)
    2. La prueba debe pasar. (Green: Al igual que lo anterior, las herramientas muestran las pruebas que pasan en verde)
    3. Se debe mejorar el código. (Refactoring)
    
##Manos a la obra
Vamos a trabajar en un ejemplo fácil e ilustrativo del procedimiento, basado en crear una clase calculadora con métodos para diferentes operaciones 
(suma, resta, división…).

#PASO 1: Crear una prueba
Lo primero que vamos a hacer es crear un fichero llamado **test_calculator.py** en un directorio. Es importante que empiece con **test_** si queremos aprovechar 
la opción de autodescubrimiento de Python:



Como se puede observar es un simple test para comprobar que el valor inicial de nuestra supuesta calculadora es 0 (es el valor que muestran por defecto todas las 
calculadoras).

**Por cierto, los tests también deben empezar con test_.**
###Referencias
[¿Que es el TDD?](https://ed.team/blog/que-es-el-tdd)
[14 benificios de tdd] (https://apiumhub.com/es/tech-blog-barcelona/beneficios-de-tdd/)
[Clean Code y TDD: las grandes ventajas de estas prácticas] (https://blogs.unsw.edu.au/nowideas/blog/2020/04/clean-code-tdd-ventajas/)
[Qué es y cómo funciona TDD: Desarrollo a partir de las pruebas, no al revés] (https://platzi.com/blog/que-es-y-como-funciona-tdd/)
