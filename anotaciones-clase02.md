### Coecion:  
Cada objetivo tiene un objetivo determinado y no tiene responsabilidades de mas

### Acoplamiento:  
Relacion que tiene un objeto con otras funciones. Un objeto con mucha coecion(hace todo) tiene mucho acoplamiento consigo mismo.

### Extensibilidad:  
Soporta mas REQUERIMIENTOS, nuevas FUNCIONALIDADES (+Flexibilidad)

### Escalabilidad:  
Soporta mas OPERACIONES. (Horizontal: potencia de computo distribuido [ej agregar servidores en paralelo], Vertical: mas potencia centralizada [mas potencia en una sola computadora])

### Testeabilidad:  
Facilidad de Probar el software

### Patron Strategy:  
Un objeto puede cambiar un comportamiento en especifico mediante la implementacion de otro objeto.(Utiliza la Composicion)

### Patron Template:  
Una herencia define una plantilla que define varios pasos, y un las subclases redefinen solo un pequenio comportamiento.

### Validacion:  
Comprobacion de los datos proporcionados por entidades externas al programa (usuario, otra aplicacion).

### API:  
Interfaz de un programa para exponer y que un tercero pueda utlilizar.

### Tipos de propagaciones:  
Excepciones: Se propagan automaticamente abortando el flujo del programa. Tienen Stacktrace[donde se genero, pasos que ocurrieron], mensaje y tipo.
Call and return: La propagacion se tiene que implementar a mano. Implementacion comun en C, se retorna un valor que representa un Error.

### DOminio:
Reglas de negocio, es la logica, no es la parte que que guarda ni la que muestra.
### Consultar del TP:


Nota:
Pregunta:
Cuando el usuario de QueMePongo crea una Prenda de Categoria con Tipo invalido. Ejemplo Calzado y de tipo Pantalon.
Se genera una excepcion en clase Prenda, se propaga hacia el gestorDeAtuendos, y gestorDeAtuendos la atrapa atrapa, que hago?
RTA: El GestorDeAtuendos va a ser sustituido por la interfaz. 


