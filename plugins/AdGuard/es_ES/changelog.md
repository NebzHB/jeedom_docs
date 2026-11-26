---
layout: default
lang: es_ES
title: Complemento AdGuard Home - Registro de cambios
description: Registro de cambios del complemento AdGuard Home
---
Si no se indica nada, probablemente se trate de una pequeña actualización ortográfica o para la compatibilidad con Jeedom V4.x

# Registro de cambios

## En fase beta
- Nuevo widget para el dispositivo AdGuard Home (panel de control y móvil), inspirado en el panel de control de AdGuard Home: protección con menú de tiempos de pausa y cuenta atrás, estadísticas, iconos en los que se puede hacer clic (filtrado, seguridad en la navegación, control parental, búsqueda segura, Internet bloqueado)
- Nuevo widget para los dispositivos de los clientes (panel de control y móvil): Internet autorizado o bloqueado con botón, iconos en los que se puede hacer clic (ajustes generales, filtrado, seguridad de navegación, control parental, búsqueda segura, servicios bloqueados en general), credenciales y servicios bloqueados
- Widgets: ajustes mediante interruptores con información emergente, acciones integradas en una sola línea (servicios, grupos, reglas, credenciales, prueba de dominio con su resultado, mantenimiento), actualización de AdGuard Home desde el icono del widget. Consulta la [documentación beta](index-beta#widgets-en-beta)
- Widgets: servicios bloqueados mostrados como iconos, tanto en el servidor como en los dispositivos clientes
- Lista de servicios con iconos, búsqueda y servicios ordenados por grupos; al seleccionar un grupo, se bloquea o desbloquea todo el grupo
- Widgets: confirmación antes de desconectar de Internet, desactivar el filtrado o el control parental, bloquear o desbloquear todos los servicios, y antes de realizar acciones de mantenimiento (caché de DNS, filtros, estadísticas)
- Widgets: ancho mínimo de 320 píxeles en el panel de control con diseño adaptativo; ancho completo en dispositivos móviles
- Widgets: altura automática según el contenido, con una opción «Altura del widget: fija» en el dispositivo para mantener la misma altura que en el modo de edición
- Nueva información «Tiempo restante de pausa»: tiempo restante (en segundos) antes de que se reanude la protección
- Nuevas acciones: «Borrar la caché DNS» y «Actualizar los filtros»
- Nueva acción «Probar un dominio» (y la información «Resultado de la prueba del dominio») en el dispositivo AdGuard Home, y «Probar un dominio para este cliente» en los clientes
- Nuevas acciones «Bloquear un grupo de servicios» y «Desbloquear un grupo de servicios», tanto globales como por cliente (AdGuard Home v0.107.68 como mínimo)
- La programación de servicios bloqueados definida en AdGuard Home ya no se borra al bloquear o desbloquear un servicio desde Jeedom
- Búsqueda segura (global y del cliente): solo cambia el estado activado/desactivado; se mantienen los motores de búsqueda seleccionados en AdGuard Home (incluido Ecosia)
- La seguridad de navegación y el control parental utilizan las llamadas de la API más reciente de AdGuard Home, con compatibilidad con las llamadas anteriores para las versiones más antiguas.
- Las opciones «Actualizar filtros» y «Actualización de AdGuard» esperan hasta 120 s la respuesta de AdGuard Home (antes, el comando fallaba y «En línea» pasaba a 0)
- Fiabilidad: las acciones muestran un mensaje claro cuando AdGuard Home no responde, cuando no se encuentra el cliente o cuando la regla está vacía, en lugar de fallar sin avisar. Las reglas personalizadas ya no se pueden borrar por error, y bloquear dos veces el acceso a Internet ya no genera duplicados.
- Corrección de los clientes cuyo nombre contiene un guion
- Corrección de la detección de errores de red (PHP 8)
- Al modificar un cliente, ya solo se envían a AdGuard Home los campos modificables
- Corrección del error «globlaux» en los nombres de los comandos de cliente («Utilizar los servicios bloqueados globales»)
- Textos de ayuda de los comandos traducidos

## 26-11-2026
- Compatible con AdGuard Home v1.0.0

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

