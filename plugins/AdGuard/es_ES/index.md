---
layout: default
lang: es_ES
title: Complemento AdGuard Home
description: Documentación del complemento AdGuard Home
---

Este complemento te permite supervisar y realizar algunas acciones en tu AdGuard Home.

Configuración del complemento
=======================

Una vez instalado el complemento, solo tienes que activarlo. No es necesario realizar ninguna configuración especial.

Configuración de los dispositivos
=============================

Se puede acceder a la configuración de los dispositivos AdGuard desde el menú
Complementos y, a continuación, «Monitorización». Aquí encontrarás:

-   un botón para crear un dispositivo manualmente

-   un botón para mostrar la configuración del complemento

-   un botón que te ofrece una visión general de todos tus dispositivos en un momento dado

-   Por último, más abajo encontrarás la lista de tus dispositivos AdGuard Home y de los clientes vinculados

Al hacer clic en uno de tus dispositivos, accederás a la página
Configuración de tu equipo, que incluye dos pestañas: «Equipo» y
controles.

-   **Pestaña «Equipamiento»**:

-   **Nombre del dispositivo**: nombre de tu dispositivo

-   **Activar**: permite poner en funcionamiento tu equipo

-   **Visible**: lo muestra en el panel de control

-   **Objeto principal**: indica el objeto principal al que pertenece el equipo

**Solo para AdGuard**

-   **IP del servidor**: la IP del servidor de AdGuard Home.

> Si has cambiado el puerto predeterminado (80), puedes añadir tu puerto aquí en el formato ip:puerto

-   **Usuario**: Usuario de AdGuard Home.

-	**Contraseña**: Contraseña del usuario de AdGuard Home.

-	**Actualización automática (cron)**: intervalos para comprobar los datos en AdGuard Home, 5 minutos por defecto.

Una vez añadido AdGuard Home y realizada la copia de seguridad de los dispositivos, los clientes detectados en AdGuard Home se añaden como dispositivos independientes.

Si **añades un cliente** más adelante, se añadirá **automáticamente durante la noche**; para forzar su incorporación a Jeedom, **vuelve a guardar el equipo AdGuard Home**.

Si **eliminas un cliente** posteriormente, se desactivará **automáticamente durante la noche**; para forzar su desactivación en Jeedom, **vuelve a guardar el equipo AdGuard Home**.

> Nota: Un dispositivo de tipo **Cliente** debe estar **desactivado para poder eliminarlo**.

**Comandos del equipo AdGuard**
================================
- **Actualizar**: Permite actualizar manualmente el equipo, además de la actualización automática
- **En línea**: Valor binario que indica si AdGuard responde correctamente a las solicitudes
- **Actualización de AdGuard disponible**: Archivo binario que indica si hay una actualización disponible
- **Actualizar AdGuard**: Acción que permite actualizar AdGuard (si hay una actualización disponible)

Protección integral
-----------------------
- **Estado de protección**: Valor binario que indica el estado de la protección global
- **Activar la protección**: Acción que permite activar la protección global
- **Desactivar la protección**: Acción que permite desactivar la protección global

> Novedad: ahora puedes modificar el tiempo durante el que la protección permanece desactivada (al igual que en la interfaz de AdGuardHome)

**Correo de AdGuard**:

![imagen](https://user-images.githubusercontent.com/28622481/133206289-810d7a4d-9705-4923-9831-e8e78100f05b.png)

Filtro global
-----------------------
- **Estado del filtrado global**: Valor binario que indica el estado del filtrado global
- **Activar el filtrado global**: Acción que permite activar el filtrado global
- **Desactivar el filtrado global**: Acción que permite desactivar el filtrado global

**Configuración de AdGuard** (Configuración > Configuración general > Bloquear dominios mediante filtros y archivos hosts):

![imagen](https://user-images.githubusercontent.com/28622481/133206778-015af02d-8039-4c78-9732-e048c41cfa21.png)

Seguridad global en la navegación
-----------------------
- **Estado de la seguridad de navegación global**: Valor binario que indica el estado de la seguridad de navegación global
- **Activar la Seguridad de navegación global**: Acción que permite activar la Seguridad de navegación global
- **Desactivar la Seguridad de navegación global**: Acción que permite desactivar la Seguridad de navegación global

**Configuración de AdGuard** (Configuración > Configuración general > Usar el servicio de navegación segura de AdGuard):

![imagen](https://user-images.githubusercontent.com/28622481/133207227-8f9aa942-54c6-4048-8fa1-3711f4ca082c.png)

Control parental global
-----------------------
- **Estado del control parental global**: Valor binario que indica el estado del control parental global
- **Activar el control parental global**: Acción que permite activar el control parental global
- **Desactivar el control parental global**: Acción que permite desactivar el control parental global

**Configuración de AdGuard** (Configuración > Configuración general > Usar el control parental de AdGuard):

![imagen](https://user-images.githubusercontent.com/28622481/133207419-bac0d204-c4fc-414d-b411-c7ec072ab514.png)

Búsqueda global segura
-----------------------
- **Estado de la búsqueda segura global**: Valor binario que indica el estado de la búsqueda segura global
- **Activar la búsqueda segura global**: Acción que permite activar la búsqueda segura global
- **Desactivar la búsqueda segura global**: Acción que permite desactivar la búsqueda segura global

**Configuración de AdGuard** (Configuración > Configuración general > Reforzar la búsqueda segura):

![imagen](https://user-images.githubusercontent.com/28622481/133207585-41110514-75f3-4a13-8f73-f3aca3c93820.png)

Servicios globales
-----------------------
- **Servicios bloqueados**: Canal que muestra los servicios bloqueados de forma general
- **Bloquear un servicio**: Acción que permite bloquear un servicio de la lista
- **Desbloquear un servicio**: Acción que permite desbloquear un servicio de la lista
- **Bloquear todos los servicios**: Acción que permite bloquear todos los servicios de la lista
- **Desbloquear todos los servicios**: Acción que permite desbloquear todos los servicios de la lista

**Configuración de AdGuard** (Filtros > Servicios bloqueados):

![imagen](https://user-images.githubusercontent.com/28622481/133207917-e813a4d1-42d2-491c-982a-ebabf6510383.png)

Internet bloqueado a través del DNS
-----------------------
- **Estado de bloqueo de Internet a través del DNS**: Valor binario que indica si se ha bloqueado Internet a través del DNS
- **Bloquear todo el acceso a Internet a través del DNS**: Acción que permite bloquear el acceso a Internet a través del DNS
- **Desbloquear todo el contenido de Internet a través del DNS**: Acción que permite desbloquear Internet a través del DNS

**Configuración de AdGuard** (Filtros > Reglas de filtrado personalizadas > añadir la regla: `||*^$important` en primer lugar):

![imagen](https://user-images.githubusercontent.com/28622481/133210452-4ebbc8b0-836d-43a4-9db9-e01c2534679e.png)

Regla de filtrado personalizada
-----------------------
- **Añadir una regla de filtrado personalizada**: Campo que permite añadir una regla de filtrado personalizada en primer lugar (ortografía correcta, sin comillas).
- **Eliminar una regla de filtrado personalizada**: Campo que permite eliminar una regla de filtrado personalizada (ortografía correcta, sin comillas).

Ver [aquí](https://github.com/AdguardTeam/AdGuardHome/wiki/Hosts-Blocklists){:target="_blank" rel="noopener"}

**Configuración de AdGuard** (Filtros > Reglas de filtrado personalizadas > añadir la regla indicada en primer lugar)

Estadísticas
-----------------------
- **Restablecer estadísticas**: Permite poner a cero las estadísticas
- **Consultas DNS**: indica el número de consultas DNS procesadas en las últimas 24 horas
- **Bloqueadas por filtros**: indica el número de consultas DNS bloqueadas por los filtros de bloqueo de anuncios y las listas de bloqueo de hosts
- **Intentos de phishing con malware bloqueados**: indica el número de consultas DNS bloqueadas por el módulo de Seguridad de navegación de AdGuard
- **Búsquedas seguras obligatorias**: indica el número de consultas DNS realizadas con la Búsqueda segura
- **Sitios web con contenido para adultos bloqueados**: indica el número de sitios web con contenido para adultos bloqueados
- **Tiempo medio de procesamiento**: indica el tiempo medio (en milisegundos) que tarda en procesarse una solicitud DNS

**Configuración de AdGuard** (Ajustes > Ajustes generales > Configuración de estadísticas > botón «Borrar estadísticas»):

![imagen](https://user-images.githubusercontent.com/28622481/133211167-470e9959-bda7-4810-a02d-8d26363bb981.png)

**y** (Panel de control > Estadísticas generales):

![imagen](https://user-images.githubusercontent.com/28622481/133211276-6c24d23c-6647-4b5f-a26c-e5834bd1a657.png)

**Pedidos de equipos para clientes**
================================

Cómo utilizar los ajustes generales
--------------------------------
- **Estado «Usar parámetros generales»**: Valor binario que indica si se ha activado la opción «Usar parámetros generales»
- **Activar «Usar los parámetros generales»**: Acción que permite activar «Usar los parámetros generales»
- **Desactivar «Usar la configuración general»**: Acción que permite desactivar «Usar la configuración general»

**Configuración de AdGuard** (Configuración > Configuración del cliente > Editar cliente > Configuración > Usar la configuración general (1)):

![imagen](https://user-images.githubusercontent.com/28622481/133217292-24f23ed8-8de2-492f-bd83-e9b90715de17.png)

Filtrado
--------------------------------
- **Estado del filtrado**: Valor binario que indica el estado del filtrado
- **Activar el filtrado**: Acción que permite activar el filtrado
- **Desactivar el filtrado**: Acción que permite desactivar el filtrado

**Configuración de AdGuard** (Configuración > Configuración del cliente > Editar cliente > Configuración > Bloquear dominios mediante filtros y archivos hosts (2))

Seguridad en la navegación
-----------------------
- **Estado de la seguridad de la navegación**: Valor binario que indica el estado de la seguridad de la navegación
- **Activar la seguridad de navegación**: Acción que permite activar la seguridad de navegación
- **Desactivar la Seguridad de navegación**: Acción que permite desactivar la Seguridad de navegación

**Configuración de AdGuard** (Configuración > Configuración del cliente > Editar cliente > Configuración > Usar el servicio de navegación segura de AdGuard (3))

Control parental
-----------------------
- **Estado del control parental**: Valor binario que indica el estado del control parental
- **Activar el control parental**: Acción que permite activar el control parental
- **Desactivar el control parental**: Acción que permite desactivar el control parental

**Configuración de AdGuard** (Configuración > Configuración del cliente > Editar cliente > Configuración > Usar el control parental de AdGuard (4))

Búsqueda segura
-----------------------
- **Estado de la búsqueda segura**: Valor binario que indica el estado de la búsqueda segura
- **Activar la búsqueda segura**: Acción que permite activar la búsqueda segura
- **Desactivar la Búsqueda segura**: Acción que permite desactivar la Búsqueda segura

**Configuración de AdGuard** (Configuración > Configuración del cliente > Editar cliente > Configuración > Reforzar la búsqueda segura (5))

Utilizar los servicios bloqueados a nivel global
--------------------------------
- **Estado «Utilizar servicios bloqueados globalmente»**: Valor binario que indica si se ha activado la opción «Utilizar servicios bloqueados globalmente»
- **Activar «Utilizar los servicios bloqueados globalmente»**: Acción que permite activar «Utilizar los servicios bloqueados globalmente»
- **Desactivar «Utilizar los servicios bloqueados globalmente»**: Acción que permite desactivar «Utilizar los servicios bloqueados globalmente»

**Configuración de AdGuard** (Configuración > Configuración del cliente > Editar cliente > Bloquear servicios específicos > Utilizar los servicios bloqueados globalmente (1)):

![imagen](https://user-images.githubusercontent.com/28622481/133218452-cf994ad7-bf63-4dbd-b727-ff64339b7b31.png)

Servicios específicos
-----------------------
- **Servicios bloqueados**: Cadena que indica los servicios bloqueados específicamente para este cliente
- **Bloquear un servicio**: Acción que permite bloquear un servicio de la lista específicamente para este cliente
- **Desbloquear un servicio**: Acción que permite desbloquear un servicio de la lista específicamente para este cliente

**Configuración de AdGuard** (Configuración > Configuración del cliente > Editar cliente > Bloquear servicios específicos > Servicios (2))

- **Bloquear todos los servicios**: Acción que permite bloquear todos los servicios de la lista específicamente para este cliente
- **Desbloquear todos los servicios**: Acción que permite desbloquear todos los servicios de la lista específicamente para este cliente

**Configuración de AdGuard** (Configuración > Configuración del cliente > Editar cliente > Bloquear servicios específicos > Bloquear todo/Desbloquear todo (3))

Internet bloqueado a través del DNS
-----------------------
- **Estado de bloqueo de Internet a través del DNS**: Valor binario que indica si se ha bloqueado el acceso a Internet a través del DNS para este cliente
- **Bloquear todo el acceso a Internet a través del DNS**: Acción que permite bloquear el acceso a Internet a través del DNS para este cliente
- **Desbloquear todo el acceso a Internet a través del DNS**: Acción que permite desbloquear el acceso a Internet a través del DNS para este cliente

**Configuración de AdGuard** (Filtros > Reglas de filtrado personalizadas > añadir la regla: `||*^$client='NombreCliente',importante` en primer lugar)

![imagen](https://user-images.githubusercontent.com/28622481/133222436-9e17578a-93e2-4be2-a96c-957131d5686a.png)

Datos de acceso
-----------------------
- **Identificador(es)**: Cadena que contiene los identificadores actuales del cliente
- **Añadir un identificador**: Acción que permite añadir un identificador al cliente (¡¡sin comillas!!)
- **Eliminar un identificador**: Acción que permite eliminar un identificador del cliente (¡¡sin comillas!!)

> **Atención: si ya existe en otro cliente, ¡primero hay que eliminarlo de este cliente! AdGuard no permite que dos clientes compartan las mismas credenciales (lo cual es lógico ;))**

**Datos de identificación de AdGuard** (Configuración > Configuración del cliente > Editar cliente > Identificador):

![imagen](https://user-images.githubusercontent.com/28622481/133277119-3de65a3b-2868-4db1-b136-ca9c498270d3.png)
