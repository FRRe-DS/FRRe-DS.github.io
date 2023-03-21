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

Grupal: en grupos de entre 4 y 7 alumnos.

## Formato de Presentación

Individual con coloquio en máquina e informe impreso y digital (formato .odt .doc .pdf).

## Fecha de Entrega

{{< hint warning >}}
01/07/2022
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

En vísperas al mundial de Qatar 2022 la empresa Fantastic Tour (FANTUR S.A.) ha solicitado a los alumnos de la materia Desarrollo de Aplicaciones Cliente-Servidor el desarrollo de un sistema para la venta y administración de paquetes turísticos.

El sistema debe permitir a los clientes registrar en forma electrónica, realizar consultas de paquetes, reservar paquetes y abobar los mismo por diferentes medios (tarjetas de crédito o otros sistemas de pago on-line) y enviar publicidad (via e-mail) a sus clientes.

La mayoría de los paquetes turísticos que la empresa comercializa están compuesto por pasajes aéreos o en micro, estadía en hoteles, seguros médicos COVID-19 y entradas a espectáculos. La aplicación debe contemplar el armado y cotización de estos paquetes turísticos por parte de los administradores de la empresa, pudiendo establecerse cuales paquetes están disponibles o hasta que fecha pueden adquirirse.

Debido a las imposiciones impuestas por los organismos de control que rigen la actividad del sector, las agencias de turismos (incluida FANTUR) deben solicitar permisos al organismo de contralor antes de confirmar a las operaciones a sus clientes. Este tipo de solicitudes deber ser realizar en forma on-line y por medio de un web-service que el organismo provee.

{{< hint info >}}
**Informacion del servicio**

Este servicio no fue desarrollado por los alumnos de la cátedra Desarrollo de Aplicaciones Cliente-Servidor, por lo cual
la tasa de error del mismo es aleatoria y deberá ser tenida en cuenta a la hora de utilizarlo.
  {{< /hint >}}

Contar con una aplicación para teléfonos móviles donde los usuarios puedan consultar u operar sería una muy buena ventaja competitiva para esta empresa.

## Desarrollo

Para el desarrollo del TP, los grupos deberán definir, coordinando entre ellos, las APIs
de los diferentes actores y publicarlas en el sitio web de la [materia](https://github.com/FRRe-DS/FRRe-DS.github.io/) 
(por medio de PRs).

Por ejemplo: para la definición de las APIs, los diferentes grupos deberán generar, en forma
colaborativa el documento de [Definición de APIs](apis). Esto lo deberán hacer, haciendo
un fork de repositorio del sitio web, generando la documentación y realizando un PR, como
se dio en el [TP 1](../tp_01#actividad-3-actividad-práctica-sobre-git-y-github).
