# Clase 08

Temas:

* Impostores

## Interfaces según punto de vista

Dentro de mi aplicación, usaremos interfaces para brindar servicios y tambíen para consumir servicios de otras aplicaciones. Las distinguiremos en:

Nota: Los nombres son **Contraintuitivos**

### Interfaz saliente (la interfaz externa)

Interfaz que **utilizo** para obtener un servicio de otra aplicacion.

### Interfaz entrante (mi interfaz)

Interfaz que **proporciono** para darle servicios a otra



## Ambientes

### Mismo Ambiente

Dos aplicaciones estan en el mismo lenguaje y V(ER)

### Ambientes distintos

Pueden estar desarrollados en distintos lenguajes, o con distintas interfaces.
En ocaciones se necesita usar un traductor 

## Sincronismo

* Invoco el componnete
* Espero
* Termino la operacion

**Ejemplo de la vida real**: Llamo a la pizzeria, y espero al telefono a que me confirmen el pedido.

## Asincronico

* Invoco al componente
* Me olvido

**Ejemplo de la vida real**: Hago un pedido desde una app, y me pongo a hacer otra cosa. Luego me llega un mail a los 10 minutos que dice "Se confirmo el pedido"

**Ventajas**: Puedo hacer otras cosas.

¿Que pasa cuando quiero el resultado?
Voy a buscarlo a un **buffer** en donde el otro proceso **puso el resultado** (**compartición**) ó mediante envío de mensajes (**comunicación**).

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

