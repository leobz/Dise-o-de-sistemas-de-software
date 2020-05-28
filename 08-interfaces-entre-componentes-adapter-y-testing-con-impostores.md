# Capítulo 8: Diseño de interfaces entre componentes

Temas:

* Integración entre dos componentes
  * Tipos de componentes
* Interfaces entrantes y salientes
  * Interfaces entrantes
  * Interfaces salientes
* Ambientes
  * Mismo ambiente
  * Distintos ambientes
* Interfaces sincrónicas y asincrónicas
  * Interfaces sincrónicas
  * Interfaces asincrónicas
* Impostores

## Integración entre dos componentes

Dada una comunicación entre dos componentes, suponiendo que **A** necesita algo de **B**. Para completar la integración se debe tener en cuenta:

* Dirección y sentido de la comunicación
* Si A y B están en el mismo ambiente
* Manejo de errores entre comunicación y procesamiento de mensajes
* Grado de dependencia: Si la comunicación es sincrónica, asincrónica o simplemente notifican y se olvidan
* Etc.

### Tipos de componentes

Ordenamos la definición de componente según su nivel de abstracción. Componentes en:

* Nivel Programa (Micro diseño): Objetos, clases, metodos.
* Nivel medio: Módulos, packages.
* Nivel arquitectura de Software: Elementos principales de la aplicación
* Nivel arquitectura del Sistema: Sistemas relacionandose

## Interfaces según punto de vista: entrantes y salientes

Dentro de mi aplicación, usaremos interfaces para brindar servicios y tambíen para consumir servicios de otras aplicaciones. Las distinguiremos en:

### Interfaz entrante

Interfaz que **proporciono** para darle servicios a otra. Radica en la consumision.

### Interfaz saliente

Interfaz que **utilizo** para obtener un servicio de otra aplicacion. Radica en la emision.

## Ambientes

### Mismo Ambiente

Dos aplicaciones estan en el mismo lenguaje y V(ER)

### Ambientes distintos

Pueden estar desarrollados en distintos lenguajes, o con distintas interfaces.
En ocaciones se necesita usar un traductor 

## Interfaces sincrónicas y asincrónicas

Dependiendo del grado de dependencia en cuanto al tiempo de respuesta, las interfaces pueden ser sincrónicas o asincrónicas

### Interfaces Sincrónicas

Esperamos la respuesta para avanzar

* Invoco el componnete
* Espero
* Termino la operacion

Ejemplo de la vida real: Llamo a la pizzeria, y espero al telefono a que me confirmen el pedido.

### Interfaces Asincrónicas

No necesitamos la respuesta para poder avanzar

* Invoco al componente
* Me olvido

Ejemplo de la vida real: Hago un pedido desde una app, y me pongo a hacer otra cosa. Luego me llega un mail a los 10 minutos que dice "Se confirmo el pedido"

**Formas de lograr interfaces asincrónicas:**

* Guardar el resultado de la operación en algún lugar de memoria compartida, el cuál A revisa periódicamente. (Compartición)
* Guardar la referencia de A, y enviarle un mensaje a este cuando haya terminado (Comunicación)
* Guardar un callback

#### Buffers

¿Que pasa cuando quiero el resultado?

Al compartir mensajes mediante un buffer comun, existe un cierto **acoplamiento implícito**.

## Adaptador

Tambien se llaman **wrappers**. Clase que abstrae funcionalidades de una API externa, que me facilita obtener metodos que voy a usar.

**Ejemplo**:

```
AdaptadorClima.getTemperatura == ApiExterna**.getClima().getTemperatura().enCelsius()
```

## Interface de Adaptadores

Cuando tengo muchos adaptadores, pero los quiero intercambiar, puedo crear una interfaz que haga una estandarizacion de estos adaptadores.

El **patron** se llama **Adapter**

**Ejemplo**:

```
Interface AdaptadorClima:
    getTemperatura()

Clase ClimaGoogle implementa AdaptadorClima

Clase ClimaBing implementa AdaptadorClima
```

### Patron Adapter

Las dos motivaciones pueden ser:

1) Adapta interface que originalmente no son compatibles.

2) Puede servir para interactuar con clases imprevistas, que muy probablemente sus interfaces sean distintas.

## Impostores (Mocking)

Son objetos que sirven **solo para los tests** y sirven para hacerse pasar por los reales. Se utilizan para poder probar una cierta situación deseada en un ambiente controlado.

* Cumplen la misma interfaz de los objetos reales
* Pueden llamarse Dummys, y tener valores **hardcodeados**.

### Podemos obtener impostores

* Creándolos nosotros
* Por Bibliotecas (Ejemplo: Mockito en Java)

