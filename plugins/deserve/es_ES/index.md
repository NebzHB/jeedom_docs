---
layout: default
lang: es_ES
title: Plugin Mérite
description: Documentación del complemento Mérite (deserve)
---

## Presentación

El complemento **Mérito** es un semáforo para Jeedom. Cada dispositivo, denominado «Merecedor», cuenta con un contador y un objetivo. Los escenarios o las acciones suman puntos (**Mérito**) o los restan (**Demérito**). Cuando el contador alcanza el objetivo, el dispositivo pasa a ser «meritorio» y se ejecutan sus acciones meritorias. Cuando vuelve a situarse por debajo del objetivo, deja de serlo y se ejecutan sus acciones deméritas.

El objetivo es simplificar los escenarios. En lugar de escribir una condición que deba conocer el estado de todos los elementos implicados, cada escenario se limita a sumar o restar sus puntos. Toda la lógica de «qué ocurre cuando se supera el umbral» se concentra en un único lugar: el dispositivo Méritant.

## Configuración del complemento

El complemento no tiene dependencias ni procesos en segundo plano. Solo hay que activarlo.

## Configuración de un dispositivo

En **Plugins → Automatización → Mérito**, haz clic en **Añadir** y asigna un nombre a tu «Meritorio».

### Configuración general

- **Nombre del dispositivo**, **Objeto principal**, **Categoría**, **Activar**, **Visible**: parámetros habituales de Jeedom.
- **Poner a cero**: si se marca esta casilla, el contador vuelve a 0 en cuanto se alcanza el objetivo, justo después de que se ejecuten las acciones que otorgan puntos. *Puntos ganados* también vuelve entonces a 0, **sin** activar las acciones que restan puntos. Cada vez que se supera el objetivo se considera un impulso, lo que se adapta bien a un sistema de niveles o recompensas.
- **Dónde se utilizan los controles**: lista de escenarios, vistas, diseños, etc., que utilizan los controles de este equipo.

### Niveles

Los niveles permiten activar acciones **antes** de alcanzar el objetivo, por ejemplo, para avisar de que se acerca una revisión.

- Cada nivel tiene un **umbral expresado en porcentaje del objetivo** (por ejemplo, el 80 %), una condición opcional y unas acciones, como los eventos que se describen a continuación.
- Un nivel se ejecuta cuando el porcentaje supera su umbral **al alza**. Si vuelve a bajar por debajo del umbral y luego vuelve a subir, la pausa se ejecuta de nuevo.
- Si se superan varios niveles a la vez, se ejecutan de menor a mayor, y siempre antes que las acciones que lo merecen.
- Dado que el umbral se expresa en porcentaje, los niveles se ajustan automáticamente al cambiar el objetivo. De hecho, bajar el objetivo puede hacer que se supere un nivel.
- Es posible que el valor supere el 100 %, ya que puede sobrepasar el objetivo.

### Acciones de mérito y de demérito

- Las **acciones de mérito** se ejecutan cuando el contador **alcanza o supera** el objetivo (*Es merecedor* pasa de 0 a 1).
- Las **acciones de demérito** se ejecutan cuando el contador **vuelve a bajar** del objetivo (*Es merecedor* pasa de 1 a 0).

Las acciones solo se ejecutan al **superar** el objetivo. Añadir puntos a un equipo que ya cumple los requisitos no reactiva las acciones que dan derecho a puntos.

Las acciones se agrupan en **eventos**:

- Cada evento tiene una **condición** opcional. Si es falsa, se ignora todo el evento. Si se deja en blanco, el evento siempre se ejecuta.
- Cada evento contiene una o varias **acciones**. Para cada una de ellas, se puede elegir un comando de acción (botón «Lista») o una palabra clave de escenario: mensaje, variable, escenario, esperar, alerta… (botón «Palabra clave»).
- Una acción se puede desactivar sin eliminarla desmarcando su casilla.
- Los eventos se ejecutan en el orden en que aparecen, al igual que las acciones de cada evento. Las acciones se pueden reordenar con el control deslizante.

## Controles

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

- Los méritos y deméritos sin valor, o con valor 0, no tienen ningún efecto.
- Los controles deslizantes del widget van de 0 a 100. Desde un escenario, se puede enviar un valor mayor (por ejemplo, *Debe requerir* a 150).
- Si se reduce el objetivo por debajo del valor actual, el valor se ajusta al nuevo objetivo. No se restablece si posteriormente se vuelve a aumentar el objetivo.
- *Puesta a cero* y *Demérito* ejecutan las acciones de demérito si el equipo era merecedor. *Ganar* ejecuta las acciones de mérito si aún no lo era.
- *Es merecedor* también puede usarse como desencadenante o condición en tus escenarios.

## Ejemplos de uso

### Descarga eléctrica

Queremos evitar que haya demasiados aparatos de alto consumo funcionando al mismo tiempo: horno, lavadora, secadora, lavavajillas y punto de recarga.

- Crea un «Gran consumidor» con un objetivo de **3**.
- Para cada dispositivo, un pequeño escenario otorga **1 punto a favor** cuando su potencia supera un umbral y **1 punto en contra** cuando vuelve a bajar. Se puede aplicar una ponderación: el terminal puede contar como 2.
- Acciones de mérito: pausar el punto de recarga, apagar el calentador de agua, enviar una notificación.
- Acciones de demérito: reactivarlo todo.

Cada dispositivo solo gestiona su +1 y su −1. Añadir un dispositivo no requiere modificar los demás escenarios.

### Contador de mantenimiento

Para el filtro de un sistema de ventilación mecánica controlada, un descalcificador o una campana extractora, o para el depósito de un robot aspirador.

- El objetivo es el umbral de mantenimiento (por ejemplo, 50 ciclos).
- En cada ciclo, un escenario obtiene **puntos**, que pueden estar ponderados: ciclo corto +1, ciclo largo +3.
- Cuando el nivel alcanza el 80 %, se envía una notificación que indica «Próximamente será necesario realizar un mantenimiento».
- Acciones de mérito: notificación «No olvides cambiar el filtro». *Es merecedor* se mantiene en 1 mientras no se haga el mantenimiento, lo que lo convierte en un recordatorio persistente en el dashboard.
- Tras el mantenimiento, haz clic en **Poner a cero** desde el panel de control.

### Puntos de mérito

- Cada tarea completada otorga puntos (**Mérito 10**, **Mérito 20**…) mediante un botón, una interacción o un escenario.
- Si se detecta algún olvido, se restarán puntos (**5 puntos de penalización**).
- Objetivo de 100, con la opción **«Poner a cero»** marcada: cada nivel alcanzado activa una recompensa (encender un enchufe, enviar una notificación…).
- Un escenario semanal se **reinicia** para volver a empezar desde cero.

## Registros

El registro «deserve» indica, en el nivel **info**, cada vez que se supera el objetivo. En el nivel **debug**, también detalla cada cambio de valor, cada condición evaluada y cada acción ejecutada.
