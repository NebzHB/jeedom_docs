---
layout: default
lang: es_ES
title: Complemento AdGuard Home - Registro de cambios
description: Registro de cambios del complemento AdGuard Home
---
Si no se indica nada, probablemente se trate de una pequeña actualización ortográfica o para la compatibilidad con Jeedom V4.x

# Registro de cambios

## 12-11-2026
- Para realizar la configuración es necesario ser administrador

## 30-01-2025
- Traducción de los nombres de los comandos
- Corrección de un aviso de PHP si no hay reglas de usuario
- (Gracias, @TomiTomas): Se ha añadido el tiempo de desactivación de la protección (como en AdGuardHome)

## 07-10-2024
- Se ha añadido el botón «Comunidad» para obtener ayuda más fácilmente

## 12-08-2024
- Traducciones y actualización de las traducciones al inglés, alemán, español, italiano y portugués

## 11-09-2023
- ¡Se requiere la versión v0.107.37!
- Modificación de los servicios bloqueados a partir de la versión v0.107.37

## 24-05-2023

- Modificaciones para los nuevos elementos de la API en la versión v0.107.28 (protección activada + búsqueda segura)
- Por el momento no es posible elegir el motor de búsqueda de la protección SafeSearch (¿es necesario?).
- Por el momento no es posible configurar un horario para la desactivación de la protección (¿es necesario con Jeedom? Ya que se puede reactivar mediante un escenario u otra opción...).
- Corrección del comando «Update»
- Cifrado de tus contraseñas de AdGuard en la base de datos de Jeedom
- **¡Por lo tanto, se requiere como mínimo la versión v0.107.28 de AdGuard!**


## 14-11-2022

- Solución para el bloqueo/desbloqueo de Internet y reglas personalizadas (en versiones v0.107.14 y posteriores), actualización a v0.107.17 y posteriores
- ¡Por lo tanto, se requiere como mínimo la versión v0.107.17 de AdGuard!

## 04-11-2022

- Desde la versión v0.107.17, AdGuard es compatible con nuevos servicios (iCloud Private Relay, etc.). Esta versión solicita la lista de servicios a AdGuard y actualiza los comandos si es necesario.

## 08-09-2022

- Se ha añadido el servicio BiliBili, disponible en la versión v0.107.12
- Ya no se produce el error si el archivo version.json ya no está disponible en AdGuard (debido a un fallo por su parte).

## 28-06-2022

- Se ha añadido el protocolo https para quienes utilicen un proxy u otro servicio similar

## 08-04-2021

- Se han añadido la versión actual y la nueva versión a los comandos. Si hay una nueva versión en el momento de la actualización, AdGuard no me envía el número de versión anterior, por lo que aparecerá en blanco... pero en cuanto actualices, se modificará y ya estará todo en orden.
- Traducción al inglés y al español
- Corregir enlaces de comandos para la acción «Bloquear Internet a través de DNS»

## 21-09-2021

- Corregir si ya existe un equipo en la misma habitación que el cliente y está desactivado

## 15-09-2021

- Inicialización

