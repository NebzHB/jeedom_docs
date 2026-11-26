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

-   **Altura del widget** (en fase beta): por defecto, la altura del widget se adapta a su contenido. Marca la casilla **Fija (la del modo de edición)** para mantener la altura establecida en el modo de edición del panel de control.

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
- **Vaciar la caché DNS** (en fase beta): acción que permite vaciar la caché DNS de AdGuard Home
- **Actualizar los filtros** (en fase beta): Acción que permite forzar la actualización de las listas de filtros

> La actualización de AdGuard y de los filtros puede tardar un tiempo: el complemento espera hasta 120 s a que AdGuard Home responda.

Widgets (en fase beta)
-----------------------
Los dispositivos AdGuard Home y Client cuentan con su propio widget (para el panel de control y para el móvil), inspirado en el panel de control de AdGuard Home y que se actualiza en tiempo real.

**Widget del dispositivo AdGuard Home**

- **Protección**: estado e interruptor. Si la protección está activa, al hacer clic se abre el menú de tiempos de pausa. Durante una pausa, se va descontando el tiempo restante hasta la reanudación.
- **Estadísticas**: consultas DNS, bloqueadas por filtros, amenazas y contenido para adultos (con el porcentaje respecto al total), búsquedas seguras forzadas y tiempo medio de procesamiento.
- **Configuración** en los interruptores verde/gris: filtrado, seguridad en la navegación, control parental y búsqueda segura. La ventana emergente indica qué acción se realizará al hacer clic. Un botón rojo con el texto «Internet bloqueado» permite desactivar o restablecer la conexión a Internet para toda la red.
- **Servicios bloqueados** mostrados mediante iconos (el nombre completo aparece en la información sobre herramientas).
- **Acciones en una línea**: servicios y grupos de servicios, reglas de filtrado personalizadas, prueba de dominio con su resultado y mantenimiento (vaciar la caché DNS, actualizar los filtros, restablecer las estadísticas).
- **Pie de página del widget**: en línea, versión, insignia de actualización (al hacer clic se inicia la actualización de AdGuard Home tras la confirmación), botón de actualizar y una ventana con el resto de valores visibles.

**Widget de equipos del cliente**

- **Internet**: «Permitido» o «Bloqueado mediante DNS», con un interruptor que bloquea o desbloquea Internet para este cliente.
- **Configuración** en los botones: parámetros generales, filtrado, seguridad en la navegación, control parental, búsqueda segura y servicios generales. Cuando el cliente sigue los parámetros generales (o los servicios bloqueados de forma general), sus ajustes propios (o su lista de servicios) aparecen en gris, con una nota que lo explica.
- **Datos de acceso** y **servicios bloqueados** del cliente (en iconos).
- **Acciones en una línea**: servicios y grupos de servicios, identificadores, prueba de dominio con su resultado.

**Lista de servicios**

La lista de selección de servicios muestra el icono de cada servicio, ofrece una función de búsqueda y clasifica los servicios por grupos (categoría en la barra superior, servicios sangrados debajo). Al seleccionar un grupo («todo el grupo») se bloquean o desbloquean todos sus servicios. Los grupos requieren como mínimo AdGuard Home v0.107.68: en versiones anteriores, la lista no incluye grupos.

**Confirmaciones**

Se solicita una confirmación antes de realizar acciones que reduzcan la protección o que no se puedan revertir fácilmente: desconectar de Internet (a un cliente o a toda la red), desactivar el filtrado o el control parental, bloquear o desbloquear todos los servicios, vaciar la caché DNS, actualizar los filtros, restablecer las estadísticas y actualizar AdGuard Home.

**Tamaño del widget**

- En el panel de control, el widget tiene al menos 320 píxeles de ancho. Si es más estrecho, los interruptores se disponen en una columna y los botones se colocan en una línea.
- En el móvil, el widget ocupa todo el ancho de la pantalla.
- La altura se adapta al contenido del widget. Para mantener la altura establecida en el modo de edición del panel de control, marca la casilla **Altura del widget: Fija (la del modo de edición)** en la configuración del dispositivo.

Los comandos de acción que el widget no reconoce conservan su widget de Jeedom.

Protección integral
-----------------------
- **Estado de protección**: Valor binario que indica el estado de la protección global
- **Activar la protección**: Acción que permite activar la protección global
- **Desactivar la protección**: Acción que permite desactivar la protección global
- **Tiempo restante** (en fase beta): Tiempo restante (en segundos) hasta que se reanude la protección, cuando se ha desactivado durante un periodo determinado

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

> Solo se modifica el estado de activado/desactivado: se mantienen los motores de búsqueda seleccionados en AdGuard Home. Si no hay ningún motor marcado en el momento de la activación, se marcan todos.

**Configuración de AdGuard** (Configuración > Configuración general > Reforzar la búsqueda segura):

![imagen](https://user-images.githubusercontent.com/28622481/133207585-41110514-75f3-4a13-8f73-f3aca3c93820.png)

Servicios globales
-----------------------
- **Servicios bloqueados**: Canal que muestra los servicios bloqueados de forma general
- **Bloquear un servicio**: Acción que permite bloquear un servicio de la lista
- **Desbloquear un servicio**: Acción que permite desbloquear un servicio de la lista
- **Bloquear todos los servicios**: Acción que permite bloquear todos los servicios de la lista
- **Desbloquear todos los servicios**: Acción que permite desbloquear todos los servicios de la lista
- **Bloquear un grupo de servicios** (en fase beta): Acción que permite bloquear todos los servicios de un grupo (lista desplegable)
- **Desbloquear un grupo de servicios** (en fase beta): acción que permite desbloquear todos los servicios de un grupo (lista desplegable)

> Los grupos de servicios requieren como mínimo AdGuard Home v0.107.68.

> La programación de los servicios bloqueados definida en AdGuard Home se mantiene cuando bloqueas o desbloqueas servicios desde Jeedom.

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

Probar un dominio (en fase beta)
-----------------------
- **Probar un dominio** (en fase beta): Acción (campo de mensaje) que permite comprobar si un dominio está bloqueado o no según la configuración general
- **Resultado de la prueba de dominio** (en fase beta): cadena que contiene el resultado de la última prueba; por ejemplo, `example.com: bloqueado por un filtro (regla: ||example.com^)`

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

Utilizar los servicios bloqueados globalmente
--------------------------------
- **Estado «Utilizar servicios bloqueados globalmente»**: Valor binario que indica si se ha activado la opción «Utilizar servicios bloqueados globalmente»
- **Activar «Utilizar los servicios bloqueados globalmente»**: Acción que permite activar «Utilizar los servicios bloqueados globalmente»
- **Desactivar «Utilizar servicios bloqueados globalmente»**: Acción que permite desactivar «Utilizar servicios bloqueados globalmente»

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

- **Bloquear un grupo de servicios** (en fase beta): Acción que permite bloquear todos los servicios de un grupo específico para este cliente (lista desplegable)
- **Desbloquear un grupo de servicios** (en fase beta): Acción que permite desbloquear todos los servicios de un grupo específicamente para este cliente (lista desplegable)

> Los grupos de servicios requieren como mínimo AdGuard Home v0.107.68.

Internet bloqueado a través del DNS
-----------------------
- **Estado de bloqueo de Internet a través del DNS**: Valor binario que indica si se ha bloqueado el acceso a Internet a través del DNS para este cliente
- **Bloquear todo el acceso a Internet a través del DNS**: Acción que permite bloquear el acceso a Internet a través del DNS para este cliente
- **Desbloquear todo el acceso a Internet a través del DNS**: Acción que permite desbloquear el acceso a Internet a través del DNS para este cliente

**Configuración de AdGuard** (Filtros > Reglas de filtrado personalizadas > añadir la regla: `||*^$client='NombreCliente',importante` en primer lugar)

![imagen](https://user-images.githubusercontent.com/28622481/133222436-9e17578a-93e2-4be2-a96c-957131d5686a.png)

Probar un dominio para este cliente (en fase beta)
-----------------------
- **Comprobar un dominio para este cliente** (en fase beta): Acción (campo de mensaje) que permite comprobar si un dominio está bloqueado o no según la configuración de este cliente
- **Resultado de la prueba de dominio para este cliente** (en fase beta): Cadena que contiene el resultado de la última prueba realizada para este cliente

> AdGuard Home solo puede comprobar un dominio con una dirección IP o un ClientID. El complemento utiliza en primer lugar la dirección IP del cliente; si no la tiene, recurre a la dirección de su rango CIDR; y, en su defecto, a su ClientID. No se puede comprobar un cliente que solo disponga de direcciones MAC: aparecerá un mensaje indicándotelo.

Datos de acceso
-----------------------
- **Identificador(es)**: Cadena que contiene los identificadores actuales del cliente
- **Añadir un identificador**: Acción que permite añadir un identificador al cliente (¡¡sin comillas!!)
- **Eliminar un identificador**: Acción que permite eliminar un identificador del cliente (¡¡sin comillas!!)

> **Atención: si ya existe en otro cliente, ¡primero hay que eliminarlo de este cliente! AdGuard no permite que dos clientes compartan las mismas credenciales (lo cual es lógico ;))**

**Datos de identificación de AdGuard** (Configuración > Configuración del cliente > Editar cliente > Identificador):

![imagen](https://user-images.githubusercontent.com/28622481/133277119-3de65a3b-2868-4db1-b136-ca9c498270d3.png)
