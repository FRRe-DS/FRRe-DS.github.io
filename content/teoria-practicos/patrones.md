---
title: Patrones de Acceso a Datos
weight: 30
---

## Patrón Repositorio
El patrón repositorio consiste en separar la lógica que recupera los
datos y los asigna a un modelo de entidad de la lógica de negocios que
actúa sobre el modelo, esto permite que la lógica de negocios sea
independiente del tipo de dato que comprende la capa de origen de
datos, en pocas palabras un repositorio media entre el dominio y las
capas de mapeo de datos, actuando como una colección de objetos de
dominio en memoria

Ver presentación: [Acceso Datos](https://github.com/FRRe-DS/Presentaciones/blob/master/practica/acceso%20datos/Acceso%20a%20datos-patrones%20utiles.pdf)

### Data Mappers
Es una capa de software que separa los objetos en memoria de la
base de datos. Su responsabilidad es transferir datos entre los
dos y también aislarlos entre sí. Con Data Mapper, los objetos en
memoria no necesitan saber ni siquiera que hay una base de
datos presente; no necesitan código de interfaz SQL y,
ciertamente, ningún conocimiento del esquema de la base de
datos.

### DAO
El patrón DAO propone separar por completo la lógica de
negocio de la lógica para acceder a los datos, de esta forma, el
DAO proporcionará los métodos necesarios para insertar,
actualizar, borrar y consultar la información; por otra parte, la
capa de negocio solo se preocupa por lógica de negocio y utiliza
el DAO para interactuar con la fuente de datos.

### Capa de Acceso a Datos:
Capa externa que va a contener todas las fuentes de datos desde
donde vamos a extraer dichos datos para leerlos desde nuestra
capa de dominio.
### Query Object
Un objeto de consulta es un intérprete, es decir, una estructura de
objetos que puede formarse en una consulta SQL.
El patrón de objeto de consulta en realidad utiliza el patrón de
asignación de metadatos para generar consultas de base de
datos reales.
### Capa de Dominio:
Es una capa que contiene todas las clases que forman parte de
nuestra lógica del negocio que vamos a implementar.
### Capa de Servicio:
Es una capa que contendrá todos los métodos desde los cuales
se realizarán las peticiones hacia la fuente de datos respectiva.

### Ventajas y Desventajas
| Ventajas                                     | Desventajas                                              |
| :------------------------------------------- | :------------------------------------------------------- |
| Reutilización del código de acceso a datos   | Implementación compleja                                  |
| Lógica del dominio sencilla de probar        | Requiere un nivel adicional de direccionamiento indirecto|
| Nos ayuda en el desacople de la lógica       | Alto grado de dependencia en la interfaz de fachada      |
| Permite implementar varias fuentes de persistencia de datos |                                           |
| Permite inyección de dependencia             |                                                          |

## Aplicación de capas

### API
La interfaz de programación de aplicaciones, conocida también por la sigla
API,application programming interface, es un conjunto de subrutinas, funciones y
procedimientos (o métodos, en la programación orientada a objetos) que ofrece
cierta biblioteca para ser utilizado por otro software como una capa de abstracción.
Es una especificación formal sobre cómo un módulo de un software se comunica o
interactúa con otro, simplifican en gran medida el trabajo de un creador de
programas, ya que no tiene que «escribir» códigos desde cero.  
- Son un medio simplificado para conectar su propia infraestructura a través del
desarrollo de aplicaciones nativas de la nube, pero también le permiten
compartir sus datos con clientes y otros usuarios externos. 
-  No son la parte visible, sino los circuitos internos que sólo los desarrolladores
ven y conectan para hacer funcionar una herramienta.  

Por ejemplo, cuando el usuario compra entradas a través de la página web de una
sala de cine e introduce la información de su tarjeta de crédito, la web usa una API
para enviar dicha información de forma remota a otro programa que verifica si los
datos bancarios son correctos. Una vez que se confirma el pago, la aplicación
remota envía la información al sitio web del cine y le da un «OK», por lo que esta
página emite los tickets.

### REST (Representational State Transfer)
Es un estilo de arquitectura de software, es
cualquier interfaz entre sistemas que use HTTP para obtener datos o generar operaciones
sobre esos datos en todos los formatos posibles. A partir de donde podemos establecer lo
siguiente:
- Todo es un recurso y viene representado por un formato. 
- Cada recurso tiene un único identificador y es accesible mediante una URI. 
- Para operar con un recurso usaremos los verbos de HTTP (GET, POST, PUT, DELETE, PATCH). 
-  Cada recurso puede tener múltiples representaciones (por ejemplo se podría representar mediante json, yaml, o xml).
- El protocolo de comunicación se considera sin estado (cada operación con el recurso se trata de forma totalmente aislada)

## RESTful APIs
REST es el estándar más lógico, eficiente y habitual en la creación de APIs. Para que una
API se considere RESTful debe cumplir una serie de criterios:
Un Restful API es una aplicación que usa el protocolo cliente-servidor sin estado (no se
almacena la información del cliente entre las solicitudes) compuesta de clientes,servidores y
recursos, gestionando solicitudes a través de HTTP.
Debe hacer uso de hipermedios, llevado al desarrollo de páginas web es lo que permite que
el usuario puede navegar por el conjunto de objetos a través de enlaces HTML. En el caso
de una API REST, el concepto de hipermedia explica la capacidad de una interfaz de
desarrollo de aplicaciones de proporcionar al cliente y al usuario los enlaces adecuados
para ejecutar acciones concretas sobre los datos.
Una arquitectura basada en capas nos permite mantener una separación de conceptos,
buscando la máxima cohesión y el menor acoplamiento de los componentes.
En este caso, la arquitectura basada en capas que vamos a desarrollar, tiene los siguientes
componentes: controladores, servicio y repositorio

### Controladores
Es una capa que sirve de enlace entre las vistas y los modelos, respondiendo a
mecanismos que puedan ser necesitados al momento de implementar las necesidades de la
aplicación.
Esta capa contiene muy poca lógica y se utiliza para realizar llamadas a servicios. Se
encarga de realizar comprobaciones básicas de los datos devueltos por los servicios para
enviar una respuesta al cliente, Recibiendo solicitudes de vista y realizando solicitudes de
vistas para mostrar resultados a los usuarios.
Usamos los controladores para mapear las uris (identificadores unívocos de los recursos
lógicos o físicos usados por las tecnologías web) de entrada del API REST.
En el controlador: 
- Obtenemos los datos que nos entran al servidor mediante las llamadas HTTP al API
REST. 
- Los preparamos para llamar a los servicios que operan con ellos. 
- Con el resultado devuelto, lo preparamos para ser enviado. 

### Servicios
Los servicios se encargan de la lógica de negocio de nuestra aplicación. En esta
capa se dice que hacer con los datos (guardados en la capa de repositorio) por lo
que tiene que estar conectada con la capa de repositorio. 
El término lógica de negocio hace referencia a la parte de un sistema que se
encarga de codificar las reglas de negocio del mundo real que determinan cómo la
información puede ser creada, almacenada y cambiada. Son rutinas que realizan
entrada de datos, consultas, generación de informes. Esta capa está presente,
específicamente, en todo el procesamiento que se realiza detrás del Backend, la
aplicación visible para el usuario. 
Los servicios pueden llamar a otros servicios para interactuar con ellos, y por
supuesto a los repositorios, que es dónde se encuentran los datos de la aplicación.

### Repositorios
En los repositorios tenemos acceso directo a los datos de la aplicación, y
desacoplan de cómo se almacena esta información para que los servicios no tengan
que conocerla. Se utiliza entre la capa de modelo y servicio. 
Aquí es dónde se opera con los datos, se accede a ellos, se realizan los filtros
necesarios y las modificaciones que necesitemos. 
Una vez realizada su tarea, devuelve los datos a los servicios. 
