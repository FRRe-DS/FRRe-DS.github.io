---
title: REST
weight: 50
---

## REpresentational State Transfer
### Transferencia de estados representacionales
**REST es una interfaz para conectar varios sistemas basados en el protocolo HTTP**
y nos sirve para obtener y generar datos y
operaciones, devolviendo esos datos en
formatos muy específicos, como XML y
JSON.  
**REST se apoya en HTTP**   
Los verbos que utiliza son exactamente los
mismos, con ellos se puede hacer GET,
POST, PUT y DELETE.

Ver presentación: [REST API](https://github.com/FRRe-DACS/Presentaciones/blob/master/practica/capa%20presentacion%20NET/Restful%20API.pdf)

**Para que una API sea considerada como REST debe superar las siguientes características arquitectónicas**
● Uso de una interfaz uniforme  
● Modelo Cliente-Servidor  
● Operaciones sin estado  
● Almacenamiento en caché  
● Sistema de capas  
● Código de baja demanda 

**Rest retorna código de status HTTP como respuesta**. Los más conocidos son:  
● 200: Ok  
● 201: Creado  
● 401: Sin autorización  
● 403: Prohibido  
● 404: Recurso no encontrado  
● 500: Error de servidor  

### ¿Por qué debemos utilizar REST?
REST no es solo una moda, y es por las siguientes razones que esta
interfaz está teniendo tanto protagonismo en los últimos años: 
- Crea una petición HTTP que contiene toda
la información necesaria, es decir, un
REQUEST a un servidor que almacena esa
información y solo espera una RESPONSE.  
- Se apoya sobre un protocolo que es el que
se utiliza para las páginas web, que es HTTP.  
- Se apoya en los métodos básicos de HTTP,
como son:  
○ Post: Para crear recursos nuevos.  
○ Get: Para acceder a los distintos recursos.  
○ Put: Para modificar.
○ Patch: Para modificaciones parciales.
○ Delete: Para borrar un recurso o un dato,
por ejemplo de nuestra base de datos.  
- Todos los objetos se manipulan mediante URI  

### Ventajas de REST 
#### Nos permite separar el cliente del servidor
Esto quiere decir que nuestro servidor se puede
desarrollar en Node y Express, y nuestra API REST
con Vue por ejemplo, no tiene por qué estar todos
dentro de uno mismo.
#### Posee una gran Comunidad
En la actualidad tiene una gran comunidad como
proyecto en Github y en distintos lenguajes de programación.
#### Independencia de tecnologías / lenguajes
Es totalmente independiente de la plataforma, así
que podemos hacer uso de REST tanto en Windows,
Linux, Mac o el sistema operativo que nosotros
queramos.
#### Escalabilidad, Fiabilidad, flexibilidad
Nos da escalabilidad, porque tenemos la separación de conceptos de
CLIENTE y SERVIDOR, por tanto, podemos dedicarnos exclusivamente a la
parte del servidor.  
A la hora de ejecutar tu aplicación también tienes una flexibilidad mucho
mayor. Por las características de REST (principalmente no guardar estado)
es indiferente qué servidor atienda cada solicitud, pues es el propio cliente
el que tiene que mandar el estado al servidor.  
La escalabilidad que aporta es gracias a una serie de
características que presenta la arquitectura REST:  
◎ Es un protocolo sin estado, debido a que no se guarda la información
en el servidor. Es decir, toda la información será enviada por el
cliente en cada mensaje HTTP, consiguiendo un ahorro en variables
de sesión y almacenamiento interno del servidor.  
◎ Presenta un conjunto de operaciones bien definidas, siendo las más
importantes GET, PUT, POST y DELETE, que se emplean en todos los
recursos.  
◎ Utiliza URIs únicas siguiendo una sintaxis universal.  
◎ Emplea hipermedios para representar la información, que suelen ser
HTML, XML o JSON.  
#### Adicionalmente
- Podemos crear un diseño de un microservicio orientado a un dominio (DDD)
- Podemos hacer nuestra API pública, permitiendo el acceso a quien
quiere hacer uso de nuestra API dándonos mayor visibilidad.
#### ¿Quién usa REST?
Muchas empresas como Twitter, Facebook, Google, Netflix,
LinkedIn y miles de startups y empresas usan REST. Todos
estas empresas y servicios tienen su API REST por un lado con
su lógica de negocio y por otro lado su parte frontend, con lo
cual nos permite centrarnos también un poco más en lo que es
nuestra lógica de negocio haciendo una API REST potente.

### Desventajas de REST
- Cambiar el modo de pensar para los equipos de trabajo.  
- Mayor tiempo de desarrollo porque hay que montar todo el sistema de la API.  
- Requiere más conocimientos.  
- Montar una infraestructura propia.  
- Pueden presentarse circunstancias de mayor rigidez en el desarrollo y surgir situaciones de
des-sincronización.

## Seguridad en REST API
Ver presentación: 
- [Seguridad REST API](https://github.com/FRRe-DACS/Presentaciones/blob/master/practica/capa%20presentacion%20NET/Seguridad%20REST%20API.pdf)