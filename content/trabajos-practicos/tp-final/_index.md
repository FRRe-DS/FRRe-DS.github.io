---
title: Trabajo Práctico Final - año 2024
description: "Denifición del TP Final de Desarrollo de Software, año 2024."
weight: 10
---

## Objetivos

{{< hint info >}}
**Que el alumno logre**:

- Adquirir habilidades prácticas sobre los conocimientos impartidos en las principales tecnologías y herramientas para el desarrollo y construcción de aplicaciones informáticas actuales.
  {{< /hint >}}

## Modalidad de Desarrollo

Grupal: en grupos de entre 4 y 7 alumnos.

## Formato de Presentación

Individual con coloquio en máquina e informe impreso y digital (formato .odt .doc .pdf).

## Fecha de Entrega

{{< hint warning >}}
05/12/2024
{{< /hint >}}

## Contenido del Informe de Presentación

- Formato de hoja: A4.
- Carátula: Nombre de la materia, año de cursado, número de grupo, nombre completo de los integrantes. Correo electrónico de cada integrante.
- índice de contenidos: índice temático de contenidos, organizado por lenguaje o herramientas de programación.
- Informe detallado: Descripción de las decisiones de diseño y de las soluciones implementadas para cumplimentar el práctico.

## Aspectos de Evaluación

La evolución de trabajo se realizará de acuerdo a la siguiente tabla:

| Aspecto                                 | Item                                   | Condición  | Puntaje |
| :-------------------------------------- | :------------------------------------- | :--------- | :------ |
| Cumplimiento funcional de la aplicación | Funcionalidad                          | Mandatorio | 15      |
| Arquitectura empleada                   |                                        |            |         |
|                                         | Multiplataforma                        | Opcional   | 10      |
|                                         | Cliente Liviano y cliente móvil        | Mandatorio | 10      |
| Acceso a Datos                          |                                        |            |         |
|                                         | Base de Datos                          | Mandatorio | 10      |
|                                         | ORM                                    | Opcional   | 10      |
| Lógica de Negocios                      |                                        | Mandatorio |         |
|                                         | Validación de Datos                    | Opcional   | 5       |
|                                         | Exposición de Servicios (Web Services) | Mandatorio | 15      |
| Presentación                            |                                        |            |         |
|                                         | Usabilidad                             | Mandatorio | 10      |
|                                         | MVC                                    | Opcional   | 10      |
|                                         | Estilos                                | Opcional   | 5       |
| **Total**                               |                                        |            | 100     |

## Actividad 1: Escenario

La organización de la  Bienal Internacional de Escultura del Chaco, se a contactado son su empresa para planificar, analizar, desarrollar e implementar un sistema de gestión que soporte el registro de los eventos, escultores como así también aplicaciones satélites para que los ciudadanos/ publico en general pueda realizar comentarios y votación durante el evento.

### Requerimientos funcionales

1. **Gestión de Eventos**: Se desea poder generar eventos futuros (y también poder cargar los eventos pasados para tener el historial) Posibilidad de agregar, ver, modificar y eliminar información sobre cada evento. Detalle del Evento: Información sobre la fecha, lugar, descripción y temática del evento.

2. **Gestión de Escultores**: Se desea poder mantener la información de los escultores Posibilidad de agregar, ver, modificar y eliminar información de los escultores. Perfil del escultor: Información detallada del escultor incluyendo nombre, biografía, contacto y obras previas.

3. **Gestión de Esculturas**: Posibilidad de agregar, ver, modificar y eliminar información sobre cada escultura. Temática de la Escultura: Descripción de la temática de cada escultura, fecha de creación, etc.

4. **Gestión de Imágenes**: Subir y Visualizar Imágenes: Posibilidad de subir y ver fotos de las esculturas en diferentes etapas (antes, durante y después del evento).

5. **Aplicación web**: pública para visualizar el próximo evento, y los eventos anteriores. Sitio web público para ver los escultores y sus esculturas.

6. **Sistema de Votación**: Votación por Visitantes: Funcionalidad para que los visitantes puedan votar por sus esculturas favoritas. Deberá estar en el sitio web público. El sistema de votación es con valores del 1 al 5 (el 5 el de mayor puntaje).

7. **Autenticación de Votantes**: Sistema para asegurar que cada visitante puede votar solo una vez (por ejemplo, a través de una cuenta de usuario o validación por email).

8. **Sistema de votacion por sitio web publico**: Haciendo uso de un botón de votar en cada escultor

9. **Sistema de votación por QR**: En cada escultor estará disponible una tablet/pantalla que visualizará un QR “único” que deben cambiar cada 1min (para prevenir el uso del QR por fuera del predio, cada minuto cambiará el QR y los anteriores ya no deberán funcionar).


10. Que la aplicación web (Sitio Publico) sea una PWA (Aplicación web progresiva)

### Requerimientos no funcionales

1. **Interfaz de Usuario (UI) Adaptable a dispositivos**: Se requiere utilizar la aplicación tanto de gestión como de los usuarios finales en diferentes dispositivos (tablet, desktop, móviles)

2. **Multiplataforma**: Compatibilidad con diferentes navegadores y dispositivos (PC, tablet, móvil).

3. **Autenticación y Autorización**: Uso de mecanismos seguros para autenticación y autorización de usuarios. Tanto para el área de gestión como para el área de usuarios para la votación.

4. **Protección de Datos**: Asegurar que los datos de los escultores y visitantes estén protegidos contra accesos no autorizados.

5. **Tiempo de Respuesta**: Garantizar tiempos de respuesta rápidos en la carga de vistas/páginas y procesamiento de datos.

6. **Optimización de Imágenes**: Asegurar que las fotos subidas estén optimizadas para una carga rápida sin pérdida de calidad significativa.

7. **Usabilidad Interfaz Intuitiva**: Diseño de una interfaz que sea fácil de usar tanto para administradores como para visitantes.

8. **Accesibilidad**: Asegurar que la aplicación sea accesible para usuarios con discapacidades.

9. **Integración con Redes Sociales**: Posibilidad de compartir eventos y esculturas en redes sociales.

10. **Sistema de validación de votantes**: para evitar fraudes, posiblemente mediante la integración de un sistema de autenticación externo o captcha.

## Desarrollo

Para el desarrollo del TP, los grupos deberán definir, coordinando entre ellos, las APIs
de los diferentes actores y publicarlas en el sitio web de la [materia](https://github.com/FRRe-DS/FRRe-DS.github.io/) 
(por medio de PRs).

Por ejemplo: para la definición de las APIs, los diferentes grupos deberán generar, en forma
colaborativa el documento de [Definición de APIs](apis). Esto lo deberán hacer, haciendo
un fork de repositorio del sitio web, generando la documentación y realizando un PR, como
se dio en el [TP 1](../tp_01#actividad-3-actividad-práctica-sobre-git-y-github).
