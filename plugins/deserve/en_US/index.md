---
layout: default
lang: en_US
title: Mérite Plugin
description: Mérite (deserve) plugin documentation
---

## Overview

The **Merit** plugin is a semaphore for Jeedom. Each device, called a “Meritorious Device,” has a counter and a target. Scenarios or actions add points (**Merit**) or subtract points (**Demerit**). When the counter reaches the target, the device becomes “Merit-worthy” and its merit-granting actions are executed. When it falls below the target, it is no longer “Merit-worthy” and its demerit-granting actions are executed.

The goal is to simplify scenarios. Instead of writing a condition that must know the status of all relevant elements, each scenario simply adds or removes its points. All the logic of “what happens when the threshold is crossed” is consolidated in a single place: the Méritant device.

## Plugin Configuration

The plugin has no dependencies or daemons. Just activate it.

## Setting Up a Device

In **Plugins → Automation → Merit**, click **Add** and give your Meritorious user a name.

### General Settings

- **Device Name**, **Parent Object**, **Category**, **Enable**, **Visible**: standard Jeedom settings.
- **Reset**: If this box is checked, the counter resets to 0 as soon as the goal is reached, immediately after the merit-granting actions are executed. *Merit* then also resets to 0, **without** triggering the demerit-granting actions. Each time the goal is reached, it acts as a trigger, which works well for a tiered or reward-based system.
- **Where the commands are used**: a list of scenarios, views, designs, etc., that use the commands for this device.

### Floors

Checkpoints allow you to trigger actions **before** reaching the goal, for example, to notify you that a maintenance task is coming up.

- Each tier has a **threshold as a percentage of the goal** (for example, 80%), an optional condition, and actions, such as the events described below.
- A step is executed when the percentage crosses its threshold **on the way up**. If it drops back below the threshold and then rises again, the step is executed once more.
- If multiple levels are triggered at once, they are executed from the lowest to the highest, and always before the corresponding actions.
- Since the threshold is expressed as a percentage, the threshold levels automatically adjust when the target changes. Lowering the target can also cause a threshold level to be crossed.
- A value above 100% is possible, since the value can exceed the target.

### Meritorious and Demeritorious Actions

- **Merit actions** are triggered when the counter **reaches or exceeds** the target (*Is Meritorious* changes from 0 to 1).
- **Demerit actions** are executed when the counter **falls below** the target (*Is Meritorious* changes from 1 to 0).

Actions are only triggered when the **goal is met**. Adding points to a device that has already earned them does not trigger the actions again.

Actions are grouped into **events**:

- Each event has an optional **condition**. If it is false, the entire event is ignored. If it is left blank, the event always runs.
- Each event contains one or more **actions**. For each one, you can choose an action command (list button) or a scenario keyword: message, variable, scenario, wait, alert… (keyword button).
- You can disable an action without deleting it by unchecking its box.
- Events are executed in the order displayed, and so are the actions for each event. Actions can be reordered using the handle.

## Commands

| Command | Type | Description |
|---|---|---|
| **Value** | numerical info | Current meter reading (never negative). |
| **Requires** | digital info | Target (100 by default). |
| **Is Eligible** | binary info | 1 if Value ≥ Requires, 0 otherwise. |
| **Percentage of Goal** | Numeric value (%) | Value / Requirement × 100, rounded. May exceed 100%. |
| **Shortfall** | digital info | Points missing to reach the goal (Requires − Value, minimum 0). |
| **Merit** | action slider | Adds the slider's value to the counter. |
| **Demerit** | slider action | Removes the slider value from the counter (minimum 0). |
| **Must Require** | action slider | Change the target (minimum 1). |
| **Score** | action | Sets the score directly to the goal value. |
| **Reset** | action | Resets the counter to 0. |

Notes:

- Merits and demerits with a value of zero have no effect.
- The widget's sliders range from 0 to 100. From within a scenario, you can send a higher value (for example, *Must Require* set to 150).
- If the target is lowered below the current value, the value is adjusted to the new target. It is not restored if the target is subsequently raised.
- *Reset* and *Demerit* trigger demerit actions if the equipment had merit. *Gain* triggers merit actions if it did not yet have merit.
- *Is Eligible* can also be used as a trigger or condition in your scenarios.

## Examples of Use

### Electric load shedding

We want to avoid having too many high-power appliances running at the same time: oven, washing machine, dryer, dishwasher, and charging station.

- Create a "High Consumers" Merit with a goal of **3**.
- For each device, a small scenario awards **1 Merit** when its power exceeds a threshold and **1 Demerit** when it drops below it. You can apply a weighting: the terminal can count as 2.
- Recommended actions: pause the hub, turn off the water heater, send a notification.
- Reset actions: Reactivate everything.

Each device manages only its +1 and −1. Adding a device does not require modifying the other scenarios.

### Maintenance counter

For the filter in a mechanical ventilation system, water softener, or range hood, or the dustbin of a robot vacuum.

- The goal is the maintenance threshold (for example, 50 cycles).
- For each cycle, a scenario earns **Merit**, which may be weighted: short cycle +1, long cycle +3.
- When the level reaches 80%, a notification is sent stating, “Maintenance will be required soon.”
- Merit-based actions: “Remember to change the filter” notification. *Merit* remains at 1 until maintenance is performed, making it a persistent reminder on the dashboard.
- After maintenance, click **Reset** on the dashboard.

### Merit Points

- Each completed task earns points (**Merit 10**, **Merit 20**…) via a button, an interaction, or a scenario.
- Points will be deducted for any omissions found (**5 penalty points**).
- Goal of 100, with **Reset** checked: each milestone reached triggers a reward (turning on a plug, sending a notification, etc.).
- A weekly scenario performs a **reset** to start over from scratch.

## Logs

The `deserve` log reports, at the **info** level, every time the goal is met. At the **debug** level, it also details every value change, every evaluated condition, and every action executed.
