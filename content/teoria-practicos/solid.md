---
title: Principios SOLID
weight: 40
---

## ¿Qué son los Principios SOLID?
Son un conjunto de principios aplicables a la Programación Orientada a Objetos que, si los usas
correctamente, te ayudarán a escribir software de calidad en cualquier lenguaje de programación
orientada a objetos. Gracias a ellos, crearás código que será más fácil de leer, testear y mantener.  
Los principios en los que se basa SOLID son los siguientes:  
● Principio de Responsabilidad Única (Single Responsibility Principle)  
● Principio Open/Closed (Open/Closed Principle)  
● Principio de Sustitución de Liskov (Liskov Substitution Principle)  
● Principio de Segregación de Interfaces (Interface Segregation Principle)  
● Principio de Inversión de Dependencias (Dependency Inversion Principle)  

Estos principios son la base de mucha literatura que encontrarás en torno al desarrollo de software:
muchas arquitecturas se basan en ellos para proveer flexibilidad, el testing necesita confiar en ellos
para poder validar partes de código de forma independiente, y los procesos de refactorización serán
mucho más sencillos si se cumplen estas reglas.  
Fueron publicados por primera vez por Robert C. Martin, también conocido como Uncle Bob, en su
libro Agile Software Development: Principles, Patterns, and Practices.

### ¿Qué beneficios aporta usar los Principios SOLID?
Las ventajas de utilizar los Principios SOLID son innumerables, ya que nos aportan todas esas
características que siempre queremos ver en un software de calidad.  
En cada uno de los principios nos iremos centrando en qué aportan específicamente, pero es
interesante hacer un resumen general de lo que conseguiremos con ellos:  
**Software más flexible**: mejoran la cohesión disminuyendo el acoplamiento. Lo que buscamos de un
buen código es que sus clases puedan trabajar de forma independiente y que el cambio de uno
afecte lo menos posible al resto. Obviamente cuando dos clases se relacionan entre sí para trabajar
juntas (y esto tiene que ocurrir sí o sí), va a existir un acoplamiento entre ellas.
Pero existen distintos niveles de acoplamiento, y gracias a algunos de los Principios SOLID, podemos
relajar esas dependencias y hacerlas mucho más flexibles a cambios.  
**Te van a hacer entender mucho mejor las arquitecturas**  
Esto es porque primero hace falta entender los principios sobre los que se sustentan, y los principios
SOLID son muy importantes para ello.  
**Simplifican la creación de tests**  
Todo esto está muy relacionado con los puntos anteriores: si tienes tu código desacoplado y una
buena arquitectura, los tests van a ser mucho más sencillos.  
**Los Principios SOLID están muy interrelacionados**  
Estos principios actúan como un todo. No es casualidad que se expliquen de forma conjunta.
Y esto tiene dos consecuencias muy importantes de entender:  
● Unos principios no pueden existir sin los otros  

Por ejemplo, si se tiene una clase A que tiene un acoplamiento muy fuerte con una clase B, de tal
forma que cada vez que cambia B inevitablemente tiene que cambiar A. Esto es muy posible que
esté incumpliendo el Principio de Responsabilidad Única. La forma de cumplirlo sería haciendo que
cuando B cambie, A no lo haga. Y para esto, la solución puede ser aplicar el Principio de Inversión
de Dependencias. Esto es muy normal y pasa casi siempre.  
Un mismo problema se puede resolver desde dos perspectivas distintas en función de en qué
Principio nos enfoquemos cuando lo resolvamos. Pero el resultado será el mismo. 

● Al cumplir un Principio puede que estés incumpliendo otro  

Esto es lo más difícil de aceptar: muchas veces es imposible cumplir todos los Principios a la vez.
Porque al aplicar un Principio, se puede estar dando la espalda a otro. Al final lo importante es
entender la potencia de cada Principio.

### Principio de Responsabilidad Única (Single Responsibility Principle)
El Principio de responsabilidad única es el primero de los cinco que componen SOLID.  
El principio de Responsabilidad Única nos viene a decir que un objeto debe realizar una única cosa.
Es muy habitual, si no prestamos atención a esto, que acabemos teniendo clases que tienen varias
responsabilidades lógicas a la vez.  
#### ¿Cómo detectar si estamos violando el Principio de Responsabilidad Única?  
La respuesta a esta pregunta es bastante subjetiva. Podemos detectar situaciones en las que una
clase podría dividirse en varias:  
- En una misma clase están involucradas dos capas de la arquitectura: esta puede ser difícil
de ver sin experiencia previa. En toda arquitectura, por simple que sea, debería haber una
capa de presentación, una de lógica de negocio y otra de persistencia. Si mezclamos
responsabilidades de dos capas en una misma clase, será un buen indicio.
- El número de métodos públicos: Si una clase hace muchas cosas, lo más probable es que
tenga muchos métodos públicos, y que tengan poco que ver entre ellos. Detecta cómo se
puede agrupar para separarlos en distintas clases.
- Los métodos que usan cada uno de los campos de esa clase: si tenemos dos campos, y uno
de ellos se usa en unos cuantos métodos y otro en otros cuantos, esto puede estar
indicando que cada campo con sus correspondientes métodos podría formar una clase
independiente. Normalmente esto estará más difuso y habrá métodos en común, porque
seguramente esas dos nuevas clases tendrán que interactuar entre ellas.
- Por el número de imports: Si necesitamos importar demasiadas clases para hacer nuestro
trabajo, es posible que estemos haciendo trabajo de más. También ayuda fijarse a qué
paquetes pertenecen esos imports. Si vemos que se agrupan con facilidad, puede que nos
esté avisando de que estamos haciendo cosas muy diferentes.
- Nos cuesta testear la clase: si no somos capaces de escribir tests unitarios sobre ella, o no
conseguimos el grado de granularidad que nos gustaría, es momento de plantearse dividir
la clase en dos.
- Cada vez que escribes una nueva funcionalidad, esa clase se ve afectada: si una clase se
modifica a menudo, es porque está involucrada en demasiadas cosas.
- Por el número de líneas: a veces es tan sencillo como eso. Si una clase es demasiado
grande, intenta dividirla en clases más manejables.

En general no hay reglas de oro para estar 100% seguros, pero estos indicios ayudarán a detectar
algunos casos donde tengas dudas.

### Principio Open/Closed (Open/Closed Principle)
Este principio nos dice que una entidad de software debería estar abierta a extensión, pero
cerrada a modificación. ¿Qué quiere decir esto? Que tenemos que ser capaces de extender el
comportamiento de nuestras clases sin necesidad de modificar su código.  
Esto nos ayuda a seguir añadiendo funcionalidad con la seguridad de que no afectará al código
existente. Nuevas funcionalidades implicarán añadir nuevas clases y métodos, pero en general no
debería suponer modificar lo que ya ha sido escrito.  
La forma de llegar a ello está muy relacionada con el punto anterior. Si las clases sólo tienen una
responsabilidad, podremos añadir nuevas características que no les afectarán. Esto no quiere decir
que cumpliendo el primer principio se cumpla automáticamente el segundo, ni viceversa.   
El principio Open/Closed se suele resolver utilizando polimorfismo. En vez de obligar a la clase
principal a saber cómo realizar una operación, delega esta a los objetos que utiliza, de tal forma
que no necesita saber explícitamente cómo llevarla a cabo. Estos objetos tendrán una interfaz
común que implementarán de forma específica según sus requerimientos.  
#### ¿Cómo detectar que estamos violando el principio Open/Closed? 
Una de las formas más sencillas para detectarlo es darnos cuenta de qué clases modificamos más a
menudo. Si cada vez que hay un nuevo requisito o una modificación de los existentes, las mismas
clases se ven afectadas, podemos empezar a entender que estamos violando este principio.
#### ¿Cuándo debemos cumplir con este principio?
Hay que decir que añadir esta complejidad no siempre compensa, y como el resto de principios, sólo
será aplicable si realmente es necesario.  
Si tienes una parte de tu código que es propensa a cambios, se lo debe plantear de forma que un
nuevo cambio impacte lo menos posible en el código existente.  
Intentar hacer un código 100% Open/Closed es prácticamente imposible, y puede hacer que sea
ilegible e incluso más difícil de mantener.

### Principio de Sustitución de Liskov (Liskov SubstitutionPrinciple)
El principio de sustitución de Liskov nos dice que toda clase que es hija de otra clase, debe poder
utilizarse como si fuese el mismo padre. Nadie debería comportarse de manera distinta si interactúa
con la clase padre o hija.  
Esto nos obliga a asegurarnos de que los objetos en un programa deben ser capaces de ser
reemplazados con instancias de subtipos de esos objetos sin alterar el programa.
La primera en hablar de él fue Bárbara Liskov (de ahí el nombre), una reconocida ingeniera de
software americana.  
#### ¿Cómo detectar que estamos violando el principio de sustitución de Liskov?
Seguro que te has encontrado con esta situación muchas veces: creas una clase que se extiende de
otra, pero de repente uno de los métodos te sobra, y no sabes qué hacer con él.
Las opciones más rápidas podrían ser dejarlo vacío, o lanzar una excepción cuando se use,
asegurándose de que nadie llama incorrectamente a un método que no se puede utilizar.
Si un método sobrescrito no hace nada o lanza una excepción, es muy probable que estés violando
el principio de sustitución de Liskov.  
Otra herramienta que te avisará fácilmente son los tests. Si los tests de la clase padre no funcionan
para la hija, también estarás violando este principio.

### Principio de Segregación de Interfaces (Interface Segregation Principle)
El principio de segregación de interfaces viene a decir que ninguna clase debería depender de
métodos que no usa. Por tanto, cuando creemos interfaces que definan comportamientos, es
importante estar seguros de que todas las clases que implementen esas interfaces vayan a necesitar
y ser capaces de agregar comportamientos a todos los métodos. En caso contrario, es mejor tener
varias interfaces más pequeñas.  
Las interfaces nos ayudan a desacoplar módulos entre sí. Esto es así porque si tenemos una interfaz
que explica el comportamiento que el módulo espera para comunicarse con otros módulos,
nosotros siempre podremos crear una clase que lo implemente de modo que cumpla las
condiciones.  
El módulo que describe la interfaz no tiene que saber nada sobre nuestro código y, sin embargo,
nosotros podemos trabajar con él sin problemas.  
#### El problema
La problemática surge cuando esas interfaces intentan definir más cosas de las debidas, lo que se
denominan fat interfaces.  
Probablemente ocurrirá que las clases hijas acabarán por no usar muchos de esos métodos, y habrá
que darles una implementación. 
Muy habitual es lanzar una excepción, o simplemente no hacer nada. 
Pero si lanzamos una excepción, es más que probable que el módulo que define esa interfaz use el
método en algún momento, y esto hará fallar nuestro programa. 
El resto de implementaciones “por defecto” que podamos dar, pueden generar efectos secundarios
que no esperemos, y a los que sólo podemos responder conociendo el código fuente del módulo en
cuestión, cosa que no nos interesa. 
#### ¿Cómo detectar que estamos violando el Principio de segregación de interfaces?
Si al implementar una interfaz ves que uno o varios de los métodos no tienen sentido y te hace falta
dejarlos vacíos o lanzar excepciones, es muy probable que estés violando este principio.

### Principio de Inversión de Dependencias (Dependency Inversion Principle)
Gracias al principio de inversión de dependencias, podemos hacer que el código que es el núcleo de
nuestra aplicación no dependa de los detalles de implementación, como pueden ser el framework
que utilices, la base de datos, cómo te conectes a tu servidor, etc.  
Todos estos aspectos se especificarán mediante interfaces, y el núcleo no tendrá que conocer cuál
es la implementación real para funcionar.  
La definición que se suele dar es:  
A. Las clases de alto nivel no deberían depender de las clases de bajo nivel. Ambas deberían
depender de las abstracciones.  
B. Las abstracciones no deberían depender de los detalles. Los detalles deberían depender de las
abstracciones.
#### El problema
En la programación vista desde el modo tradicional, cuando un módulo depende de otro módulo,
se crea una nueva instancia y la utiliza sin más complicaciones.
Esta forma de hacer las cosas, que a primera vista parece la más sencilla y natural, nos va a traer
bastantes problemas posteriormente, entre ellos:  
- Las partes más genéricas de nuestro código (lo que llamaríamos el dominio o lógica de
negocio) dependerá por todas partes de detalles de implementación. Esto no es bueno,
porque no podremos reutilizarlo, ya que estará acoplado al framework de turno que
usemos, a la forma que tengamos de persistir los datos, etc. Si cambiamos algo de eso,
tendremos que rehacer también la parte más importante de nuestro programa.  
- No quedan claras las dependencias: si las instancias se crean dentro del módulo que las usa,
es mucho más difícil detectar de qué depende nuestro módulo y, por tanto, es más difícil
predecir los efectos de un cambio en uno de esos módulos. También nos costará más tener
claro si estamos violando algunos otros principios, como el de Responsabilidad Única.  
- Es muy complicado hacer tests: Si tu clase depende de otras y no tienes forma de sustituir
el comportamiento de esas otras clases, no puedes testarla de forma aislada. Si algo en los
tests falla, no tendrías forma de saber de un primer vistazo qué clase es la culpable. 
#### ¿Cómo detectar que estamos violando el Principio de inversión de dependencias?
Cualquier instanciación de clases complejas o módulos es una violación de este principio.
Además, si escribes tests te darás cuenta muy rápido, en cuanto no puedas probar esa clase con
facilidad porque dependa del código de otra clase.  
Entonces cómo vamos a hacer para darle al módulo todo lo que necesita para trabajar. Habrá que
utilizar alguna de las alternativas que existen para suministrar esas dependencias.  
Aunque hay varias, las que más se suelen utilizar son mediante constructor y mediante setters
(funciones que lo único que hacen es asignar un valor).  
¿Quién se encarga de proveer las dependencias?
Lo más habitual es utilizar un inyector de dependencias: un módulo que se encarga de instanciar los objetos que se necesiten y pasárselos a las nuevas instancias de otros objetos.    
Se puede hacer una inyección muy sencilla a mano, o usar alguna de las muchas librerías que existen
si necesitamos algo más complejo.

## Conclusión
Las reglas SOLID son ideas muy potentes que generan un gran aporte para crear software de calidad,
pero hay que aplicarlas donde corresponda y sin obsesionarnos con cumplirlas en cada punto del
desarrollo, por eso es importante entender bien todos los conceptos para no agregar errores a
futuro. Por lo tanto, concluimos en que casi siempre es más sencillo limitarse a usarlas cuando nos
haya surgido la necesidad real.