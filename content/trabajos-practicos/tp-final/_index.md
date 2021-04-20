---
title: Trabajo Práctico Final
description: "Denifición del TP Final de Desarrollo de Aplicaciones Cliente-Servidor, año 2021."
weight: 10
---

## Objetivos

{{< hint info >}}
**Que el alumno logre**:

- Adquirir habilidades prácticas sobre los conocimientos impartidos en las principales tecnologías y herramientas para el desarrollo y construcción de aplicaciones informáticas actuales.
  {{< /hint >}}

## Modalidad de Desarrollo

Grupal: en grupos de entre 4 y 6 alumnos.

## Formato de Presentación

Individual con coloquio en máquina e informe impreso y digital (formato .odt .doc .pdf).

## Fecha de Entrega

{{< hint warning >}}
02/07/2021
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

El Ministerio de Desarrollo Productivo, junto con la Secretaría de Comercio Interior han sancionado la
[Resolución 237/2021](https://www.boletinoficial.gob.ar/detalleAviso/primera/241937/20210317) por la cual se
crea el **Sistema Informativo para la Implementación de Políticas de Reactivación Económica** (SIPRE).

Este sistema, cuyo objetivo final es contribuir a la reactivación económica del país, tiene por alcance a
todas las empresas del sector comercio e industria local. Estas empresas deberá suministrar información
de forma mensual, a través del repositorio de información del MINISTERIO DE DESARROLLO PRODUCTIVO,
los primeros diez (10) días corridos de cada mes calendario.

La información suministrada deberá contener, como mínimo, los siguientes datos:

- CUIT de la empresa.
- Denominación del producto.
- Código EAN o equivalente sectorial del producto; y
- Precio por unidad de peso, cantidad o medida del producto.
- Cantidades producidas y vendidas

Para esto los alumnos de la cátedra Desarrollo de Aplicaciones Cliente-Servidor deberá desarrollar
un sistema que implemente los siguiente sub-sistemas:

### Ministerio de Desarrollo Productivo

Este sub-sistema deberá exponer las APIs (Application Programing Interface) para que las
empresas presenten mensualmente la información de regimen informativo de la resolución.
A su vez, deberá exponer servicios para resumir la información que está disponible para la
Secretaría de Comercio Interior.

### Empresas del Sector Comercio

Se deberá crear librerias para acceder y publicar los regímenes informativos al **Ministerio de
Desarrollo Productivo**. Se deberá proveer una implementación de referencia, que utilice la librería
y publique los datos en el Ministerio.

### Secretaría de Comercio Interior

La Secretería de Comercio Interior debe ser capaz de consultar los datos publicados
en el repositorio de información del Ministerio de Desarrollo Productivo, y por medio
de ciertas reglas de negocios y políticas establacidas, generar altertas de incumplimiento,
y en caso de ser necesario, reportar al comercio el incumplimiento de la normativa.

## Desarrollo

Para el desarrollo del TP, los grupos deberán definir, coordinando entre ellos, las APIs
de los diferentes actores y publicarlas en el sitio web de la [materia](https://github.com/FRRe-DACS/FRRe-DACS.github.io/) 
(por medio de PRs).

Por ejemplo: para la definición de las APIs, los diferentes grupos deberán generar, en forma
colaborativa el documento de [Definición de APIs](apis). Esto lo deberán hacer, haciendo
un fork de repositorio del sitio web, generando la documentación y realizando un PR, como
se dio en el [TP 1](../tp_01#actividad-3-actividad-práctica-sobre-git-y-github).
