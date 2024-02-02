
# SSI

- [SSI](#ssi)
- [Tema 1 - Introducción](#tema-1---introducción)
  - [Tipos de ataques](#tipos-de-ataques)
  - [Integridad](#integridad)
  - [Disponibilidad](#disponibilidad)
  - [Terminología básica](#terminología-básica)
  - [Tipos de atacantes](#tipos-de-atacantes)
  - [Equipos de seguridad](#equipos-de-seguridad)

| Criterios de calificación | Porcentaje |
| - | - |
| Teoría | 40 % |
| Prácticas | 40% |
| Trabajo | 20% |

Seguridad de sistemas informáticos es una asignatura en la que comprenderemos lo más básico sobre diferentes aspectos clave del campo de la seguridad informática. Cubriendo tanto amenazas como defensas contra las mismas.

| Información general sobre la asignatura |
| - |
| CV: https://www.campusvirtual.uniovi.es/course/view.php?id=3805 |

# Tema 1 - Introducción

Un sistema es seguro cuando responde según lo previsto:
Permite a cada usuario legítimo realizar todas las operacitones para las que está autorizado
Evita que los usuarios realicen operaciones para las que no tiene autorización
Garantiza a los usuarios legítimos:

## Tipos de ataques

###Confidencialidad
- Acceso no autorizado al sistemas (suplantación)
- Acceso no autorizado a la comunicación (sniffing)
- Acceso físico a un ordenador
- Acceso lógico o físico a copias de seguridad
- Acceso a datos / software restringido o privado

## Integridad
Los mismos que contra la confidencialidad pero existiendo modificación de por medio
- Una vez se accede, estos se pueden modificar introduciendo datos falsos o maliciosos. También se pueden dañar o corromper o modificar software para lograr efectos no deseados
- Estos se ataques se hacen generalmente con ataques Attacker-in-the-Middle (AitM)

## Disponibilidad
Toda forma de negar o reducir la capacidad de un sistema informático para dar un determinado servicio o conjunto de servicios.

- Saturación
- Dejar al sistema sin recursos
- Eliminar o dañar el hardware existente
- Apagar el sistema

## Terminología básica


| Concepto | Definición |
| - | - |
| Amenaza | Elementos que suponen cualquier clase de peligro para los sitemas. |
| Vulnerabilidad | Partes del sistema que pueden ser atacadas. **Son los puntos débiles del sistema**. El payload es el código que realizad la acción maliciosa de un ataque |
| Exploit | Técnicas o código que permiten aprovechar una vulnerabilidad. |
| CVE | Common Vulnerbilities and Exposures. Son bases de datos con todas las vulnerabilidades concocidas clasificadas para cualquier tecnología. <br> https://cve.mitre.org <br> https://www.cvedetails.com/ |
| CVSS | Common Vulnerability Scoring System. Puntúa cada una de las entradas de los CVE. <br> [Calculadora CVSS](https://www.incibe.es/incibe-cert/blog/cvss-v40-avanzando-en-la-evaluacion-de-vulnerabilidades) |
| OSINT | Open Source INTeligence. Toda la información accesible de manera pública y legal. |

## Tipos de atacantes

**🟧 Script kiddies (skiddies)**
Personas con pocos conocimientos pero con acceso a herramientas de ataque avanzadas

**⬜ Pentesters (white hats)**
Profesionales contratados legalmente para probar el estado de la seguridad de un sistema. Usan las mismas técnicas que los black hats pero en entornos controlados y con limitaciones preestablecidas.

**⬛ Crackers (black hats)**
Personas que dañan el sistema por razones espurias

## Equipos de seguridad

Todos los equipos son contratados por las empresas, es decir serían todos whitehats.

**🟥 Red team**: Grupo independiente que desafía a una organización a mejorar la efectividad de su seguridad asumiento un "rol de adversario". Funciona como el equipo de **ataque**.

**🟦 Blue team**: Analiza la seguidad de los sistemas de información. Es el equipo de **defensa**.

**🟪 Purple team**: Maximiza la efectividad de ambos equipos. El equipo hace ambas **cosas**.
