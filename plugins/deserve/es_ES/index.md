---
layout: default
lang: es_ES
title: Plugin Mérite
description: Documentación del complemento Mérite (deserve)
---

# Presentación

El plugin **Mérite** es un semáforo para Jeedom. Cada equipo, llamado «Merecedor», tiene un contador y un objetivo. Escenarios o acciones suman puntos (**Mérito**) o los restan (**Demérito**). Cuando el contador alcanza el objetivo, el equipo pasa a ser merecedor y se ejecutan sus acciones de mérito. Cuando vuelve a bajar del objetivo, deja de serlo y se ejecutan sus acciones de demérito.

La idea es simplificar los escenarios. En lugar de escribir una condición que deba conocer el estado de todos los elementos implicados, cada escenario se limita a sumar o restar sus puntos. Toda la lógica de «qué pasa cuando se cruza el umbral» queda reunida en un solo lugar: el equipo Merecedor.

# Configuración del complemento

El complemento no tiene dependencias ni procesos en segundo plano. Solo hay que activarlo.

# Configuración de un dispositivo

En **Plugins → Automatización → Mérite**, haz clic en **Añadir** y da un nombre a tu Merecedor.

## Configuración general

- **Nombre del dispositivo**, **Objeto principal**, **Categoría**, **Activar**, **Visible**: parámetros habituales de Jeedom.
- **Reinicio**: si esta casilla está marcada, el contador vuelve a 0 en cuanto se alcanza el objetivo, justo después de ejecutar las acciones de mérito. *Es merecedor* vuelve entonces también a 0, **sin** ejecutar las acciones de demérito. Cada vez que se alcanza el objetivo se comporta así como un impulso, lo que encaja bien con un sistema de niveles o de recompensas.
- **Dónde se utilizan los controles**: lista de escenarios, vistas, diseños, etc., que utilizan los controles de este equipo.

## Niveles

Los niveles permiten ejecutar acciones **antes** de alcanzar el objetivo, por ejemplo para avisar de que se acerca un mantenimiento.

- Cada nivel tiene un **umbral en porcentaje del objetivo** (por ejemplo 80 %), una condición opcional y acciones, como los eventos descritos más abajo.
- Un nivel se ejecuta cuando el porcentaje cruza su umbral **al subir**. Si vuelve a bajar del umbral y sube de nuevo, el nivel se ejecuta otra vez.
- Si se cruzan varios niveles a la vez, se ejecutan del más bajo al más alto, y siempre antes de las acciones de mérito.
- Como el umbral se expresa en porcentaje, los niveles siguen automáticamente un cambio de objetivo. Bajar el objetivo puede incluso hacer que se cruce un nivel.
- Es posible que el valor supere el 100 %, ya que puede sobrepasar el objetivo.

## Acciones de mérito y de demérito

- Las **acciones de mérito** se ejecutan cuando el contador **alcanza o supera** el objetivo (*Es merecedor* pasa de 0 a 1).
- Las **acciones de demérito** se ejecutan cuando el contador **vuelve a bajar** del objetivo (*Es merecedor* pasa de 1 a 0).

Las acciones solo se ejecutan al **cruzar** el objetivo. Sumar puntos a un equipo que ya es merecedor no vuelve a ejecutar las acciones de mérito.

Las acciones se agrupan en **eventos**:

- Cada evento tiene una **condición** opcional. Si es falsa, se ignora todo el evento. Si se deja en blanco, el evento siempre se ejecuta.
- Cada evento contiene una o varias **acciones**. Para cada una de ellas, se puede elegir un comando de acción (botón «Lista») o una palabra clave de escenario: mensaje, variable, escenario, esperar, alerta… (botón «Palabra clave»).
- Una acción se puede desactivar sin eliminarla desmarcando su casilla.
- Los eventos se ejecutan en el orden en que aparecen, al igual que las acciones de cada evento. Las acciones se pueden reordenar con el control deslizante.

# Controles

| Control | Tipo | Descripción |
|---|---|---|
| **Valor** | información numérica | Valor actual del contador (nunca negativo). |
| **Requiere** | información numérica | Objetivo a alcanzar (100 por defecto). |
| **Es merecedor** | información binaria | 1 si Valor ≥ Requiere, 0 en caso contrario. |
| **Porcentaje del objetivo** | información numérica (%) | Valor / Requiere × 100, redondeado. Puede superar el 100 %. |
| **Falta** | información numérica | Puntos que faltan para alcanzar el objetivo (Requiere − Valor, mínimo 0). |
| **Mérito** | acción deslizador | Suma el valor del deslizador al contador. |
| **Demérito** | acción deslizador | Resta el valor del deslizador al contador (mínimo 0). |
| **Debe requerir** | acción deslizador | Cambia el objetivo (mínimo 1). |
| **Ganar** | acción | Pone directamente el contador en el valor del objetivo. |
| **Puesta a cero** | acción | Pone el contador a 0. |

Observaciones:

- Mérito y Demérito sin valor, o con 0, no hacen nada.
- Los deslizadores del widget van de 0 a 100. Desde un escenario se puede enviar un valor mayor (por ejemplo *Debe requerir* a 150).
- Si se reduce el objetivo por debajo del valor actual, el valor se ajusta al nuevo objetivo. No se restablece si posteriormente se vuelve a aumentar el objetivo.
- *Puesta a cero* y *Demérito* ejecutan las acciones de demérito si el equipo era merecedor. *Ganar* ejecuta las acciones de mérito si aún no lo era.
- *Es merecedor* también puede usarse como desencadenante o condición en tus escenarios.

# Ejemplos de uso

## Descarga eléctrica

Queremos evitar que demasiados grandes consumidores funcionen a la vez: horno, lavadora, secadora, lavavajillas, punto de recarga.

- Crea un Merecedor «Grandes consumidores» con un objetivo de **3**.
- Para cada aparato, un pequeño escenario hace **Mérito 1** cuando su potencia supera un umbral y **Demérito 1** cuando vuelve a bajar. Se puede ponderar: el punto de recarga puede contar como 2.
- Acciones de mérito: pausar el punto de recarga, apagar el calentador de agua, enviar una notificación.
- Acciones de demérito: reactivarlo todo.

Cada dispositivo solo gestiona su +1 y su −1. Añadir un dispositivo no requiere modificar los demás escenarios.

## Contador de mantenimiento

Para el filtro de un sistema de ventilación mecánica controlada, un descalcificador o una campana extractora, o para el depósito de un robot aspirador.

- El objetivo es el umbral de mantenimiento (por ejemplo, 50 ciclos).
- En cada ciclo, un escenario hace **Mérito**, eventualmente ponderado: ciclo corto +1, ciclo largo +3.
- Un nivel al 80 % envía la notificación «Mantenimiento necesario pronto».
- Acciones de mérito: notificación «No olvides cambiar el filtro». *Es merecedor* se mantiene en 1 mientras no se haga el mantenimiento, lo que lo convierte en un recordatorio persistente en el dashboard.
- Tras el mantenimiento, un clic en **Puesta a cero** desde el dashboard.

## Puntos de mérito

- Cada tarea realizada da puntos (**Mérito 10**, **Mérito 20**…) mediante un botón, una interacción o un escenario.
- Un olvido detectado resta puntos (**Demérito 5**).
- Objetivo de 100, con **Reinicio** marcado: cada vez que se alcanza el objetivo se dispara una recompensa (encender un enchufe, enviar una notificación…).
- Un escenario semanal hace **Puesta a cero** para volver a empezar.

# Registros

El registro «deserve» indica, en el nivel **info**, cada vez que se supera el objetivo. En el nivel **debug**, también detalla cada cambio de valor, cada condición evaluada y cada acción ejecutada.
