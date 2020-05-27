# Clase 06

## Framework vs Bibliotecas

### Abstraccion

Separar, extraer o aislar una cualidad de un objeto o funcionalidad.

### Bibliotecas

Abstracciones reutilizables

* Control directo: El usuario decide cuando llamarlas

### Framework

Marco de trabajo para realizar una tarea generica. Deja al programador las reglas de negocio.

* El **control es inverso**, el framework llama a nuestro codigo. "No nos llame, nosotros te llamamos"
* Se necesitan seguir ciertas reglas genericas, para que luego el framework sepa
como llamar a nuestro codigo y ejecutarlo.
* Permiten **puntos de extension**: se puede agregar cierta parte de codigo para personalizar una parte del comportamiento.

### Dependencias

Tiene muchos significados segun el punto de vista

* Gestor de Dependencias(mave, npm, etc): Bibliotecas necesarias para el funcionamiento del proyecto
* En objetos: Todas las cosas que necesita el objeto para funcionar adecuadamente.
* **Conocimiento directo** (Lo llama el objeto) o **inyectado** (permite parametrizar)

### Inyeccion de Dependencias

VER  
Defino una instancia que se encarga de realizar una accion con un comportamiento
definido, y la utilizo o la "inyecto", para que haga algo.
El strategy utiliza inyeccion de dependencias, cada estrategia seria una inyeccion que usamos.
Ejemplo DependenciaGmail, DependenciaOutlook son tipos de Dependencia Mail que se inyectan al objeto, y todas entienden el metodo ".enviar_mail()".
Al no ser parametrizable, utiliza polimorfismo para definir el comportamiento

#### Service Locator (Distinto a Inyeccion de dependencias)

Global pero intercambiable (parametrizable), sabe dar dependencias (VER)

En vez de usar un singleton de una dependencia, usamos un singleton de serviceLocator(de esta manera ganamos flexibilidad)

Un objeto que registra ciertas dependencias en forma global para que se utilicen.
A diferencia de la inyeccion de dependencias, es global.
Ejemplo : 
ServiceLocator.DependenciaDeMail = Gmail
ServiceLocator.DependenciaNavegador = Firefox

## Testing

## Produccion

Instancia que ve el cliente

### Testing unitario (Funcionalidades puntuales)

Deben ser:

* Rapidos
* Repetibles
* Independientes(que no compartan estados)

### Coverage (Covertura)

Es un indicador de que porcentaje de mi codigo esta testeado
Existen herramientas que nos dan el coverage del codigo.


### Ciclo de Desarrollo yCalidad

Pull Request

**Integracion Continua** (Jenkins, Github):
  El paso de Integracion puede ser Manual o Automatizado

Codigo Listo -> Unit Test -> Integracion

**Continuos Delivery** (De una rama Se sube a produccion automaticamente):

* Se tiene que tener mucho cuidado
* El paso de subir a Produccion puede ser Manual o Automatizado

Codigo Listo -> Unit Test -> Integracion -> Pruebas de Aceptacion -> Produccion