---
title: Object Document Mapper
weight: 20
---

## Introducción 
Cuando queremos guardar en una DB info solemos usar su lenguaje propio dentro de nuestro
código. Pero a veces tenemos que hacer todo un esfuerzo para que este lenguaje de consulta
funcione dentro de nuestro código. Esto se puede evitar con un orm, o un ODM en el caso de
una base de datos no relacional como MongoDB. El ODM hace de intermediario entre la app y
la DB así tenemos métodos propios que hacen todo el trabajo.

## Mongoose
MongooseJS es un Object Document Mapper (ODM) que facilita el uso de MongoDB al
traducir documentos en una base de datos MongoDB a objetos en el programa.
Además de MongooseJS, hay varios otros ODM que se han desarrollado para MongoDB,
incluidos Doctrine, MongoLink y Mandango.
Las cuatro ventajas principales de usar Mongoose frente a MongoDB nativo son:  
● MongooseJS proporciona una capa de abstracción sobre MongoDB que elimina la
necesidad de utilizar colecciones con nombre.  
● Los modelos en Mongoose realizan la mayor parte del trabajo de establecer valores
predeterminados para las propiedades del documento y validar los datos.  
● Las funciones se pueden adjuntar a los modelos en MongooseJS. Esto permite la
incorporación perfecta de nuevas funciones.  
● Las consultas utilizan el encadenamiento de funciones en lugar de los mnemónicos
incrustados que dan como resultado un código que es más flexible y legible, y por lo
tanto más fácil de mantener.  
El resultado neto de estos es la simplificación del acceso a la base de datos desde las
aplicaciones. La principal desventaja de Mongoose es que la abstracción tiene un costo de
rendimiento en comparación con el de MongoDB nativo.

### ¿Por qué Mongoose si ya existe el cliente de mongoDB?
Mongoose usa esquemas para modelar los datos que una aplicación desea almacenar y
manipular en MongoDb. Esto incluye funciones como conversión de tipos, validación, creación
de consultas y más. 
El esquema describe los atributos de las propiedades (también conocidos como campos) que la
aplicación manipulara. Estos atributos incluyen cosas como:  
● Tipo de datos, en total son 8: String, Number, Date, Buffer (archivos onda PDF),
Boolean, Mixed (puede venir cualquier cosa), ObjectId (links a otros documentos en la
DB), Array.  
● Si es obligatorio u opcional.  
● Su valor por defecto.  
● Crear índices para que la información sea obtenida más rápido. 

### Getters/Setters en Mongoose
Una función GET que te permite manipular la información entrante antes de ser devuelta
como objeto:
```javascript
const userSchema = new Schema({
  email: {
    type: String,
    get: obfuscate
  }
});

// Mongoose passes the raw value in MongoDB `email` to the getter
function obfuscate(email) {
  const separatorIndex = email.indexOf('@');
  if (separatorIndex < 3) {
    // 'ab@gmail.com' -> '**@gmail.com'
    return email.slice(0, separatorIndex).replace(/./g, '*') +
      email.slice(separatorIndex);
  }
  // 'test42@gmail.com' -> 'te****@gmail.com'
  return email.slice(0, 2) +
    email.slice(2, separatorIndex).replace(/./g, '*') +
    email.slice(separatorIndex);
}

const User = mongoose.model('User', userSchema);
const user = new User({ email: 'ab@gmail.com' });
user.email; // **@gmail.com
```

Una función SET que permite manipular los datos antes de ser guardados en la base de
datos
```javascript
const userSchema = new Schema({
email: {
type: String,
set: v => v.toLowerCase()
}
});

const User = mongoose.model('User', userSchema);

const user = new User({ email: 'TEST@gmail.com' });
user.email; // 'test@gmail.com'

// The raw value of `email` is lowercased
user.get('email', null, { getters: false }); // 'test@gmail.com'

user.set({ email: 'NEW@gmail.com' });
user.email; // 'new@gmail.com'
```

Con mongoose todo deriva de un esquema, por ello se genera un modelo a partir del esquema
y define un documento en el que operará la aplicación. Más precisamente, un modelo es una
clase que define un documento con las propiedades y comportamientos declarados en nuestro
esquema. Todas las operaciones de base de datos realizadas en un documento con Mongoose
deben hacer referencia a un modelo.

### El Esquema
El schema es la estructura que van a tener nuestros datos. Nos permite decidir exactamente
qué datos queremos y qué opciones que los datos tengan como objeto.

```javascript
const mongoose = require("mongoose");

const FoodSchema = new mongoose.Schema({
  nombre: {
    type: String,
    required: true,
    trim: true,
    lowercase: true,
  },
  calorias: {
    type: Number,
    default: 0,
    validate(value) {
      if (value < 0) throw new Error("Las calorias negativas no son reales.");
    },
  },
});

const Food = mongoose.model("Food", FoodSchema);

module.exports = Food;
```
Consiste en un nombre, de tipo String, será obligatorio, se limpian espacios en blanco y estará
en minúsculas. También tendremos calorías, de tipo numérico, un valor por defecto de 0 y una
validación para que no pueda ser menor a 0.

### CRUD con Mongoose
Cuando quieres hacer un nuevo registro creas una nueva instancia de tu modelo e invocas al método save. En este caso estoy definiendo las propiedades manualmente, pero pueden venir de cualquier lugar.
```javascript
const videojuego = new Videojuego({
  nombre: "Cuphead",
  precio: 180,
  calificacion: 10,
});
await videojuego.save();
console.log("Guardado");
```
Cuando quieres obtener todos los registros, invoca al método find:
```javascript
const videojuegos = await Videojuego.find();
console.log(videojuegos);
```
Si quieres obtener un registro por id, invoca a findById:
```javascript
const id = "12354564asdf";
const videojuego = await Videojuego.findById(id);
console.log(videojuego);
```
En el caso de actualizar un registro por id puedes usar a findOneAndUpdate:
```javascript
const id = "1235213asdf";
await Videojuego.findOneAndUpdate({
  _id: id,
}, {
  nombre: "Nuevo nombre",
  precio: 500,
  calificacion: 9,
});
console.log("Actualizado");
```
Y finalmente para eliminar un registro a partir del ID puedes usar findOneAndDelete:
```javascript
const id = "123213asdf";
await Videojuego.findOneAndDelete({ _id: id });
console.log("Eliminado");
```

### Conclusión
MongoDB nos proporciona las ventajas de una base de datos NoSQL, como la flexibilidad de la
estructura de datos, la escalabilidad y el rendimiento sin abandonar conceptos que han hecho a
las bases de datos relacionales lo que son hoy en día, como consistencia de datos y la
integración con otras herramientas de desarrollo. Sumado al poder administrarla en la nube con
Mongo Atlas (solución provista por los creadores del producto).  
Por estas características, MongoDB es una herramienta que cae como anillo al dedo para el
desarrollo de aplicaciones como redes sociales, aplicaciones móviles, CMS, entre otras, que
debido a lo antes mencionado, requieren de una base de datos que ofrezca alto rendimiento y
flexibilidad, a la vez que mantiene consistencia y seguridad en los datos.  
Consideramos que MongoDB es una herramienta fácil de aprender, útil y sumamente divertida.
Principalmente al estar trabajando en proyectos personales o por hobby, no tenemos que pasar
por todo el proceso de definición y esquema de tablas y relaciones. Sencillamente con que esté
corriendo MongoDB ya le podemos enviar información desde nuestras aplicaciones.  
Es idóneo además de que como en nuestro caso lo usamos en conjunto con Node y React,
tampoco es necesario aprender varios lenguajes para realizar una aplicación completa.
Decidimos utilizar Node debido a su popularidad en la industria, también el hecho de que nos
pareció copado trabajar con el Stack MERN - Mongo Express React y Node. NodeJS nunca fue
hecho para resolver el problema de escalado de computación. Node fue creado para resolver el
problema de escalado de E/S, lo que funciona de maravilla. Entonces cuándo usarlo? La
respuesta es simple, si el problema no contiene operaciones intensivas de CPU ni el acceso a
los recursos de bloqueo, node es la respuesta.
