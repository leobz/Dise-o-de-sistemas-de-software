

## Manejo del cambio

Se usa diseno iterativo (no presuponer requerimientos que no llegaron, ir armando incrementalmente).

### Deuda tecnica
Esfuezo extra por agregar una funcionalidad. (complementar en google)
Puede ser por
* Poco conocimiento del problema
* Poco conocimiento de la tecnologia
* Calendario ajustado
* Costos
* Cambios en las prioridades

Es conveniente *pagar de a poco* esa deuda tecnica, ya que los intereses
serian las complicaciones futuras que implicarian un diseno atado con alambre como
agregar nuevas funcionalidades o mantenerlo.


### Refactoring
Cambiar el formato del diseno de un estado A a uno B. No se agregan funcionalidades.
* Soporta los mismos requerimientos
* Mejora algunas cualidades de diseno (mas testeable, mantenible, etc)
* Hay herramientas que ayudan a hacer refactoring (IDES o editores con vitaminas)
Es necesario antes del refactor **tener los test unitarios**, si no los hubiese, **los agrego**


### Code Smells
Son senales de posibles mejoras, pueden detectar problemas de diseno.

Algunos ejemplos:
* Inappropiate Intimacy: Hay un tercero que le esta afanando funcionalidades a otro objeto.Puede estar utilizando o conoce mucho de los atributos de otro objeto. 
* Shotgun surgery: Un cambio muy chiquito impacta mucho en otras funcionalidades
* Null Object: Objetos que representan operaciones nulas.
* Data class: Si tengo una clase que tiene solo atributos y no tiene comportamiento, posiblemente hay otra clase que le esta robando los metodos (responsabilidades). 

Que quiere decir?:
Otro ejemplo que puede sonarles conocido: el guerrero tiene como atributo el ítem más
valioso. 

Mostrar el codigo de la app del coronavirus y preguntar como podria 

Preguntar lo del null objet si es era lo correcto o lo incorrecto