---
title: Sistemas de Control de Versiones
weight: 10
---

## ¿Qué es un Sistema de control de versiones?
Un Sistema de Versionado de Código (SVC) en abstracto es lo que nos permite compartir el código fuente de nuestros desarrollos y a la vez mantener un registro de los cambios por los que va pasando.  
Habitualmente para gestionar las distintas versiones por las que pasa el código fuente de las aplicaciones, lo que nos permite saber quién realiza qué cambios y poder volver a ellos en un determinado momento. Los más utilizados en este campo a lo largo del tiempo (aunque existen bastante más) son CVS, Subversion y Git

Ver presentación: [Sistemas de control de versiones](https://github.com/FRRe-DACS/Presentaciones/blob/master/practica/Control%20versiones/Sistemas%20de%20control%20de%20versiones.pdf)

### ¿Porqué usar un control de versiones nos hará felices?
● Proporciona copias de seguridad automáticas de los ficheros.  
● Permite volver a un estado anterior de nuestros ficheros.  
● Ayuda a trabajar de una forma más organizada.  
● Permite trabajar de forma local, sin conexión con servidor. (en distribuídos).  
● Permite que varias personas trabajen en los mismos ficheros.  
● Permiten trabajar en varias funcionalidades en paralelo separado (ramas).

### El antes y el después de conocer los sistemas de control de versiones  
En algún momento de nuestras vidas nuestra carpeta de documentos luciera como la de la imagen y nos haya tocado recurrir a tener muchas copias de nuestros proyectos.  
Tiempo después por algún accidente del destino conocemos los sistemas de control de versiones y no podemos negarlo, nuestras vidas cambian y entramos a una era donde todo es mucho más bonito: el después.
El control de versiones es un sistema que registra los cambios realizados sobre un archivo o conjunto de archivos a lo largo del tiempo de tal manera que sea posible recuperar versiones especificas más adelante

## Tipos de Sistemas de Control de Versiones 
### Sistemas de Control de Versiones Locales  
En vez de mantener las versiones como archivos independientes, los almacenaban en una base de datos.  
EN cualquier momento solo se tenia una copia del proyecto, eliminando la posibilidad de confundir o eliminar versiones. 
En este punto el control de versiones se llevaba a cabo en el computador de cada uno de los desarrolladores y no existía una manera eficiente de compartir el código entre ellos 

### Sistemas de Control de Versiones Centralizados 
Para facilitar la colaboración de múltiples desarrolladores en un solo proyecto los sistemas de control de versiones evolucionaron: en vez de almacenar los cambios y versiones en el disco duro de los desarrolladores, estos se almacenaban en un servidor. 
los sistemas centralizados trajeron consigo nuevos retos: ¿Cómo trabajaban múltiples usuarios en un mismo archivo al mismo tiempo? 
Los sistemas de control de versiones centralizados abordaron este problema impidiendo que los usuarios invalidaran el trabajo de los demás. Si dos personas editaban el mismo archivo y se presentaba un conflicto alguien debía solucionar este problema de manera manual y el desarrollo no podía continuar hasta que todos los conflictos fueran resueltos y puestos a disposición del resto del equipo.  
Esta solución funcionó en proyectos que tenían relativamente pocas actualizaciones y por ende pocos conflictos pero resulto muy engorroso para proyectos con docenas de contribuyentes activos que realizaban actualizaciones a diario. 

### Sistemas de Control de Versiones Distribuidos 
Este SCV optó por darle a cada desarrollador una copia local de todo el proyecto, de esta manera se construyo una red distribuida de repositorios, en la que cada desarrollador podía trabajar de manera aislada pero teniendo un mecanismo de resolución de conflictos mucho más elegante que un su versión anterior. 
Al no existir un repositorio central, cada desarrollador puede trabajar a su propio ritmo, almacenar los cambios a nivel local y mezclar los conflictos que se presenten solo cuando se requiera. Cómo cada usuario tiene una copia completa del proyecto el riesgo por una caída del servidor, un repositorio dañado o cualquier otro tipo de perdida de datos es mucho menor que en cualquiera de sus predecesores

## Ejemplos de SCV
### CVS 
CVS (Concurrent Versions System) es uno de los primeros sistemas de control de versiones. 
Tiene una arquitectura cliente-­servidor, en la que el código está almacenado en un servidor central y con el software cliente podemos hacer una copia del código local para hacer cambios y posteriormente volver a subirla al servidor.
Permite el trabajo concurrente entre distintos programadores, pero el servidor solo acepta actualizaciones de los ficheros que estén en la última versión, de forma que los propios usuarios deben actualizar sus copias locales antes de subirlas al servidor. Soporta además el trabajo en distintas ramas.
Se hizo bastante popular entre la comunidad de software libre por ser lanzado bajo la licencia GNU. 

### SVN  
El proyecto de Subversion surgió en el año 2000 con el objetivo crear un sistema decontrol de versiones con la misma filosofía que CVS, pero arreglando problemas y cubriendo carencias del mismo:  
● Commits atómicos, en CVS un commit interrumpido puede dejar datos inconsistentes.   
● La creación de ramas es más eficiente, con complejidad constante a diferencia de CVS que es lineal (aumenta con el número de ramas).  
● Manejo de archivos binarios como tal, CVS los trata como archivos de texto.  
● Envía los incrementos de los ficheros en la comunicación cliente­servidor, en lugar de los ficheros completos como CVS.  
La estructura más habitual en un repositorio SVN:  
● Trunk con la versión del código principal.  
● Tags para almacenar las distintas versiones de una aplicación que no volverán a modificarse.  
● Branches para gestionar las distintas versiones de código que se desarrollan paralelas al trunk   
Al ser también software libre, ha sido adoptado por multitud de proyectos, incluso en grandes corporaciones, convirtiéndose en un referente.

### GIT  
En 2005, Linus Torvalds inició el desarrollo de Git como alternativa a BitKeeper (que había pasado a ser SW propietario), el sistema de control de versiones que se usó hasta el momento para desarrollar el kernel de Linux. Por esto, Git nace con las principales necesidades de ser rápido, eficiente y distribuido:  
● Rápido: combinando el trabajo sobre el repositorio local y la posterior distribución remota.  
● Eficiente: pensado para manejar grandes proyectos con muchos ficheros (Linux) y no se vuelve lento a medida que la historia del proyecto crece.  
● Distribuido: fundamental para el trabajo concurrente y en remoto de muchos usuarios. Cada usuario tiene una copia local en la que trabajar, que posteriormente sincroniza con el resto de usuarios. Es también especialmente efectivo a la hora de mezclar los cambios hechos por distintos usuarios.  
#### Características  
Su sencillez es lo que lo diferencia de otros sistemas de control de versiones y lo que le hace verdaderamente potente.   
La mayoría de sistemas del momento almacenaban los cambios (deltas) en los ficheros entre distintas versiones y requerían de complejos algoritmos de aplicación de esos deltas para recuperar un determinado estado del repositorio. Git en cambio es una sencilla base de datos clave­-valor, en la que cada versión apunta a un árbol de nodos que representa la estructura de directorios y contenidos comprimidos de los ficheros. Esto le permite recuperar estados únicamente apuntando a un determinado árbol y facilita las tareas de distribución y mezclado de contenidos  
Distribuido: cada usuario dispone de un repositorio completo de forma local. Esto permite trabajar sin necesidad de conexión a un servidor para realizar las distintas acciones, pudiendo más tarde sincronizar nuestros datos con el servidor.   
Otra de las particularidades de Git es el área de stage. La gran mayoría de sistemas almacenan la información en dos sitios, la copia lo al de ficheros y directorios del usuario, y el almacenamiento de versiones.  
Git proporciona una tercera opción con el área de stage. Consiste en un área intermedia entre las otras dos, donde ir colocando los cambios de la copia local con las que queremos hacer un nuevo commit. De esta forma se consigue mucha más versatilidad y control a la hora de ir guardando versiones del código.



