### TP
3 Entregas por cuatrimestre 

Notas: Mal- Regular- Bien
Solo se puede tener una entrega Mal por cuatrimestre

### Etapas de un objeto

* **Cuando lo uso** o le mando un mensaje.  Ej: calcularPrecio(), etc)
	Patrones: Strategy, TemplateMethod  (Patrones de comportamiento)

* Cuando lo instancio. Trata de construir una instancia concistente.
	
* Cuando lo construyo una instanciacion me surjen estas dudas:
	* Asociar sus dependencias (Ejemplo un planificador que necesite una estrategia, etc)
	* Validaciones (No null, etc)
	* Creacion por partes. Se le pasan parametros del constructor por partes (Recibo parametros por pantalla en distinto orden, etc)
	* Valores Prededefinidos ()
	* Familias de objetos (Tema dark con botones oscuros, Conexion de SQL tiene su familia de metodos y objetos, que son distintos a ORACLE, etc)
	* Grafos complejos (Cuando se tienen n niveles de objetos que crean una red muy grande)


QueMePongo:
* El constructor de al tener la abstraccion material hace que quede con menos parametros y eso trae beneficios.  
Generalmente un constructor que tiene muchos parametros podria implementar un abstraccion.
	>> Prenda(...., Material material)

* El borrador puede ser una clase que guarde todos los atributos con informacion intermedia, para luego, teniendo todos los atributos completos crear una prenda con esos atributos. Podria tener el metodo construir() que pase sus atributos como instanciacion de una prenda nueva.

* Los catch para mostrar mensajes al usuario van en la UI, no en el dominio.

* El borrador seria un Builder en este caso
* Si se usara el Borrador en validaciones  seria un Builder y le quitaria la responsabilidad al constructor de toda la logica de validaciones que lo haria muy complejo.

* El builder (borrador), tiene un metodo crear() que es el punto de entrada para instanciar el objeto (ahi se puede llamar a validar() que hace todas las validaciones)
* Se puede utilizar interfaz fluida (Metodos encadenados que setean los atributos por partes antes de instanciar). Esto es solo una manera distinta de sintaxis para que sea algo mas expresiva, nada mas.
* Un builder tiene sentido cuando hay estados intermedios, muchas validaciones, etc.

* En los distintos tipos de uniforme de cada colegio utilizando FactoryMethods (fabricarParteSuperior(), fabricarCalzado(), etc)

* Un creation method es por ejemplo Prenda:: nuevoPantalon(){ return new Prenda("pantalon")}

* El abstract factory seria como un strategy solo que para crear objetos en vez de hacer cosas

* Singlenton: No lo quieren mucho. Cuando no queda otra. Cuando es una unica instancia en el sistema y necesito que sea GLOBAL. Cuando hay un unico punto de acceso. A diferencia de los Enums pueden tener estados.

* Las dependencias son todos los atributos que necesita un objeto para funcionar.