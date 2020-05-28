# Capítulo 9: Patrones de comunicación

1) Introducción
2) Patrones para comunicar dos componentes: una clasificación
3) Call & return
4) Memoria compartida / Call-By-Reference
5) Excepciones
6) Continuaciones (CPS)
7) Eventos
    * 7.1 Interrupciones/Signals
8) Streams/Pipes

## Introducción

Los patrones son eso, patrones. Bien puede pasar que tengamos esquemas mixtos o que se
puedan interpretar de una u otra forma... por ejemplo las signals del sistema operativo podrían
pensarse como un mecanismo de excepción o como un evento en distintos contextos... no es
tan importante encajar nuestra solución en una categorización exacta sino que los patrones
sirven en la medida en que nos ayudan a pensar.

En este texto, no hablaremos tanto de cuestiones de diseño, sino más bien haremos un tratamiento teórico de distintas formas de comunicar componentes. Y recuerden que cuando
acá hablemos de componentes en general pondremos ejemplos en objetos, pero que realmente estas ideas aplican a muchas otras tecnologías

## Patrones para comunicar dos componentes

* Call and Return
* Memoria compartida
* Excepciones
* Continuaciones
* Eventos
* Paso de mensajes asincrónicos
* Stream / pipes

## Call and Return

PREGUNTA: ¿CALL AND RETURN está basado en la composición de funciones? Es decir ¿El caller (o llamador) equivaldria a la funcion que toma la salida de la otra (que seria el callee o llamado)?

Se da cuando un componente invocante o llamador (caller) invoca o referencia a un componente llamado (callee). El callee devuelve un valor de retorno al caller, por ende la comunicación será bidireccional (Aunque existen tencologías que no permiten esto y la comunicación es unidireccional)

* El callee puede recibir parámteros que le pasa el caller.
* El callee no necesita conocer al caller
* El patron está basado en la composición de funciones CHEQUEAR
* Inmutabilidad: no se modifican los mensajes, sino que se crean nuevos.

## Memoria compartida (Call by Reference)

La memoria compartida es un espacio común de datos en el que múltiples componentes pueden escribir y leer información. Pueden ser desde variables, buffers, colas, hasta una base de datos como componente de integración.

Cuando se un componente ejecuta una función o método sobre la memoria compartida, este cambio influye a los demás componentes que la utilizan.

El scope de la variable compartida puede ser global o localizada. Ejemplos:

* Variables globales: Podrían ser varias pilas que compartan un mismo index global. Esto sería un problema ya que al modificar una pila, afectaremos a todas las demas.

```python
index = 0

class Pila:
    def push(valor):
        index ++
        valores[index] = valor

# Al crearse dos pilas, si hago un push en una afecto a la otra (ya que todas usan el mismo index)
```

* Variables localizadas: Podrian ser las variables de clase, que son accedidas y modificadas por cualquier instancia de una clase.

```python

class Auto(marca):
    ruedas = 4
    marca = marca

mercedes = Auto("Mercedes")
audi = Auto("Audi")

audi.ruedas == mercedes.ruedas // Comparten la misma variable
```

## Excepciones

Se comunica transmitiendo un mensaje de error, el estado de un objeto o el error original, modificando el flujo normal de los mensajes.

## Continuaciones

En la programación Continuation-passing style (CPS), las funciones no retornan valores, sino que cada una llamará a otra antes de finalizar, haciendo que el programa sea una conjunción de continuaciones de funciones.

Para esto las funciones CPS necesitan como mínimo dos elementos: una condición para controlar distintos tipos de flujos posibles y una responsabilidad (funcion lambda, método, etc). Ésta responsabilidad, será la futura continuadora del Flujo de Control.

Ejemplo1:

```python

# Las funciones continuadoras son anteExito y anteFalla
def divisionCPS(dividendo, divisor, anteExito, anteFalla)
    if (divisor == 0):
        anteFalla()
    else:
        anteExito()

```

Ejemplo 2:
```python
# Función CPS
def siEsParHacerAlgo(numero, funcionContinuadora):
    if esPar(numero):
        funcionContinuadora(numero)

# Continuadora
def imprimir(algo):
    print("Valor: " + algo)

----

siEsParHacerAlgo(2, imprimir) ->  Valor 2
```

PREGUNTA: Qué es el patron command?

## Eventos

Es una comunicación en la cual existe un productor y un suscriptor. Cuando ocurre un evento, el productor A le informará a sus sucriptor B.

En algunos casos, existe una técnica llamada polling la cual permite al suscriptor no tener que estar chequeando todo el tiempo si hay novedades.

Permite bajar el acomplamiento en los casos en el que el  receptor no conozca al emisor.

### Interrupciones/ Signals

Los signals son mecanismos de bajo nivel que permiten establecer notificaciones ante interrupciones.

Ejemplo:

```python
ProcesoPadre:
    pidHijo = crearHijo()

    # Envía señales a su hijo
    kill(pidHijo, SIG_CHILD)
    kill(pidHijo, SIG_MATAR)

ProcesoHijo:
    # Asocia cada señal a una función
    signal(SIG_CHILD, hacerAlgo)
    signal(SIG_MATAR, cerrarme)
```

También podrían ser pensadas como excepciones, pero a diferencia de estas, las señales regresan al flujo normal que las llamó.

Nota: Cuando el usuario apreta Ctrl + C, el sistema opeartivo está enviandole una señal al programa para que éste se detenga. 

## Streams / Pipes

El trabajo con pipes muestra una implementación similar del patrón call & return para comandos del sistema operativo (Linux/Unix).
Cada pipe separa el output del proceso anterior que es el input del pedido siguiente.

Ejemplo:

```shell
$ ps aux | grep conky | grep -v grep | awk '{print $2}' | xargs kill
```

---

Referencia:

* Patrones de comunicación entre componentes- Version 1.1 (Fernando Dodino, Nicolás Passerini, Franco Bulgarelli)