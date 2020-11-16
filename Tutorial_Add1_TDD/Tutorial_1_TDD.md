# TDD como metodología de diseño de software
Este tutorial tiene como objetivo en ofrecernos herramientas para poder realizar un trabajo de mejor calidad y cuidado.

## ¿Que es TDD?
  Es una metodología de desarrollo cuyo objetivo es crear primero las pruebas y luego escribir el software. Es decir, desarrollo guiado por pruebas.Es una 
metodología de desarrollo cuyo objetivo es crear primero las pruebas y luego escribir el software. Sus siglas en Inglés son: **Test Driven Development** y 
en español significa: **Desarrollo guiado por pruebas**.

## ¿Porque es importante aplicarlo?
  Esta metodología se ha convertido en una muy popular entre los desarrolladores ya que es bastante sencilla y permite alcanzar la máxima calidad posible 
de tu código como un código más robusto, más seguro, más mantenible y una mayor rapidez en el desarrollo. El desarrollo dirigido por test consiste en escribir 
las pruebas que el código ha de superar, comprobar que fallan, implementar la mínima  cantidad de código que permita pasar las pruebas y, una vez superadas 
las pruebas, refactorizar el código.

## Beneficios
Razones para hacerlo:

    - Genera confianza gracias a tener pruebas que garantizan el correcto funcionamiento del código.
    - Mejora el diseño y la calidad del código.
    - Minimiza la cantidad del código a escribir ya que al realizar pruebas, se evita la posibilidad de escribir código que no se va a utilizar. 
    - Permite un desarrollo más rápido y optimizarás el mantenimiento y evolución del código.
    - Satisfacción del cliente.
    
Desarrollar un software en muchas ocasiones viene aparejado de la presión por terminarlo en determinado tiempo, es por ello que estas herramientas te ayudarán 
a construir un proyecto de software de calidad desde el principio.

## Herramientas
No hay una herramienta como tal para implementar la metodología de TDD. Más bien, existen herramientas que nos ayudan a escribir y correr nuestras pruebas de 
forma automatizada.

    - Java - JUnit, REST assured, Selenium, Mockito, Spock, etc.
    - JavaScript - Jasmine, AVA, Tape, Mocha, Jest, etc.
    - PHP - PHPUnit, Codeception, Behat, PHPSpec, SimpleTest, Storyplayer, etc.
    - Python - Existen librerías nativas o instalables que facilitan el desarrollo y automatización de pruebas en Python como unittest, pytest o Hypothesis.
    - Go - El paquete testing nativo de Go.

No se puede definir cual framework es el mejor para tu lenguaje de programación, se debe trabajar con varios y escojer con el que mejor les guste.

## Ciclo de desarrollo
Para el uso del TDD se deben combinar 2 metodologías: Test-first development (escribir las pruebas primero) y Refactoring (refactorización de código). 
Para esto, se usa un ciclo de desarrollo que consta de 3 partes principales:

    1. La prueba debe fallar. (Red: Muchas herramientas muestran los fallos de las pruebas en rojo)
    2. La prueba debe pasar. (Green: Al igual que lo anterior, las herramientas muestran las pruebas que pasan en verde)
    3. Se debe mejorar el código. (Refactoring)
    
## Manos a la obra
Vamos a trabajar en un ejemplo fácil e ilustrativo del procedimiento, basado en crear una clase calculadora con métodos para diferentes operaciones 
(suma, resta, división…). Trabajaremos en esta ocasión con python.

### PASO 1: Crear una prueba
Lo primero que vamos a hacer es crear un fichero llamado **test_calculator.py** en un directorio. Es importante que empiece con **test_** si queremos aprovechar 
la opción de autodescubrimiento de Python:

*test_calculator.py*
```
# Cargamos el módulo unittest
import unittest  

# Creamos una clase heredando de TestCase
class TestMyCalculator(unittest.TestCase):  

    # Creamos una prueba para probar un valor inicial
    def test_initial_value(self):
        calc = Calculator()
        self.assertEqual(0, calc.value)
```

Como se puede observar es un simple test para comprobar que el valor inicial de nuestra supuesta calculadora es 0 (es el valor que muestran por defecto todas las 
calculadoras).

**Por cierto, los tests también deben empezar con test_.**

## PASO 2: Ejecutar la prueba y comprobar que falla

Ahora, desde el directorio que contiene el fichero ejecutamos los tests de autodescubrimiento

```
C:\python-tdd-example>python -m unittest discover
E
====================================================================
ERROR: test_initial_value (test_calculator.TestMyCalculator)
--------------------------------------------------------------------
Traceback (most recent call last):
  File "C:\python-tdd-example\test_calculator.py", line 9, in test_initial_value
    calc = Calculator()
NameError: name 'Calculator' is not defined
--------------------------------------------------------------------
Ran 1 test in 0.001s
FAILED (errors=1)

```
Como era obvio se encontrará un test, se ejecutará y fallará.

## PASO 3: Implementar el código mínimo para pasar la prueba

Para seguir correctamente la filosofía del TDD es esencial no implementar todo el código de golpe, sino simplemente resolver los errores de uno en uno para hacer que la prueba pase, de eso se trata que nos guíen las pruebas.

El error que tenemos ahora nos dice:

```
NameError: name 'Calculator' is not defined
```
Para solucionarlo creamos la clase **Calculator** con el mínimo código:

*calculator.py *
```
class Calculator:
    pass
```
Y hacemos uso de ella en nuestros módulo de pruebas:

*test_calculator.py*
```
import unittest  

# Importamos la clase calculadora
from calculator import Calculator

class TestMyCalculator(unittest.TestCase):  

    def test_initial_value(self):
        calc = Calculator()
        self.assertEqual(0, calc.value)
```
## PASO 4: Volvemos a ejecutar la prueba hasta que pase
Se supone que hemos resuelto el fallo, así que vamos a probar:
```
C:\python-tdd-example>python -m unittest discover
E
====================================================================
ERROR: test_initial_value (test_calculator.TestMyCalculator)
--------------------------------------------------------------------
Traceback (most recent call last):
  File "C:\python-tdd-example\test_calculator.py", line 11, in test_initial_value
    self.assertEqual(0, calc.value)
AttributeError: 'Calculator' object has no attribute 'value'
--------------------------------------------------------------------
Ran 1 test in 0.001s
FAILED (errors=1)
```
¡Vaya qué sorpresa! Hemos arreglado un error y a aparecido otro diciéndonos que no tenemos el atributo value:

```
AttributeError: 'Calculator' object has no attribute 'value'
```
Pues nada, tendremos que arreglarlo y añadir este atributo en el constructor de nuestra clase:
*calculator.py*
```
class Calculator:
  
    def __init__(self):
        self.value = 0
```
Ejecutamos de nuevo:
```
C:\python-tdd-example>python -m unittest discover
.
--------------------------------------------------------------------
Ran 1 test in 0.000s
OK

```
## PASO 5 : Refactorizar
Nuestro código es muy sencillo, pero podemos mejorar un poco el test unitario añadiendo un método setUp() que se encargue de crear la instancia automáticamente:

*test_calculator.py*
```
import unittest  
from calculator import Calculator

class TestMyCalculator(unittest.TestCase):  
  
    def setUp(self):
        self.calc = Calculator()

    def test_initial_value(self):
        self.assertEqual(0, self.calc.value)
```
Después de refactorizar volveremos a comprobar que el código pasa los tests:
```
C:\python-tdd-example>python -m unittest discover
.
--------------------------------------------------------------------
Ran 1 test in 0.001s
OK
```
¡Perfecto! Ya hemos desarrollado nuestro primer requisito guiándonos de las pruebas mientras hemos resuelto 2 errores.

## PASO 6: Repetir el proceso para añadir otro requisito
Una calculadora sin operaciones no es una calculadora, así que vamos a añadirle por lo menos un método para sumar dos valores y guardar el resultado en el atributo value.

Recordemos sin embargo que estamos haciendo TDD, así que no podemos escribir el método directamente, primero tendremos que hacer un test que falle:

*test_calculator.py*
```
import unittest  
from calculator import Calculator

class TestMyCalculator(unittest.TestCase):  
  
    def setUp(self):
        self.calc = Calculator()

    def test_initial_value(self):
        self.assertEqual(0, self.calc.value)
    
    # Creamos un nuevo test para comprobar una suma
    def test_add_method(self):
        # Ejecutamos el método
        self.calc.add(1, 3)  
        # Comprobamos si el valor es el que esperamos
        self.assertEqual(4, self.calc.value)
```
Ejecutamos el test que fallará:
```
C:\python-tdd-example>python -m unittest discover
E.
====================================================================
ERROR: test_add_method (test_calculator.TestMyCalculator)
--------------------------------------------------------------------
Traceback (most recent call last):
  File "C:\python-tdd-example\test_calculator.py", line 15, in test_add_method
    self.calc.add(1, 3)
AttributeError: 'Calculator' object has no attribute 'add'
--------------------------------------------------------------------
Ran 2 tests in 0.001s
FAILED (errors=1)
```
Implementamos el método add:
*calculator.py *
```
class Calculator:
  
    def __init__(self):
        self.value = 0

    def add(self, a, b):
        self.value = a + b
```
Probamos de nuevo el test:
```
C:\python-tdd-example>python -m unittest discover
..
--------------------------------------------------------------------
Ran 2 tests in 0.000s
OK
```
¡Perfecto, ya tenemos implementada nuestra suma y nuestra metodologia aprendida! Ahora sería cuestión de ir añadiendo la resta, el producto, la división, etc.
## Referencias
¿Que es el TDD?(https://ed.team/blog/que-es-el-tdd)

14 benificios de tdd (https://apiumhub.com/es/tech-blog-barcelona/beneficios-de-tdd/)

Clean Code y TDD: las grandes ventajas de estas prácticas (https://blogs.unsw.edu.au/nowideas/blog/2020/04/clean-code-tdd-ventajas/)

Qué es y cómo funciona TDD: Desarrollo a partir de las pruebas, no al revés (https://platzi.com/blog/que-es-y-como-funciona-tdd/)

Python, ejemplo (https://www.hektorprofe.net/tutorial/ejemplo-muy-facil-tdd-python)
