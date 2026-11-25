---
layout: default
lang: en_US
title: Mérite Plugin
description: Mérite (deserve) plugin documentation
---

# Overview

The **Mérite** plugin is a semaphore for Jeedom. Each device, called a “Deserving device”, has a counter and a goal. Scenarios or actions add points (**Merit**) or remove them (**Demerit**). When the counter reaches the goal, the device becomes deserving and its merit actions are executed. When it falls back below the goal, it is no longer deserving and its demerit actions are executed.

The point is to simplify scenarios. Instead of writing a condition that has to know the state of every element involved, each scenario simply adds or removes its own points. All the logic of “what happens when the threshold is crossed” lives in a single place: the Deserving device.

# Plugin Configuration

The plugin has no dependencies or daemons. Just activate it.

# Setting Up a Device

In **Plugins → Automation → Mérite**, click **Add** and give your Deserving device a name.

## General Settings

- **Device Name**, **Parent Object**, **Category**, **Enable**, **Visible**: standard Jeedom settings.
- **Reset**: if this box is checked, the counter goes back to 0 as soon as the goal is reached, right after the merit actions are executed. *Is Deserving* then also goes back to 0, **without** running the demerit actions. Each time the goal is reached therefore behaves like a pulse, which suits a step or reward system well.
- **Where the commands are used**: a list of scenarios, views, designs, etc., that use the commands for this device.

## Steps

Steps let you trigger actions **before** the goal is reached, for example to warn that maintenance is coming up.

- Each step has a **threshold as a percentage of the goal** (for example 80%), an optional condition and actions, like the events described below.
- A step runs when the percentage crosses its threshold **on the way up**. If it drops back below the threshold and rises again, the step runs again.
- If several steps are crossed at once, they run from lowest to highest, and always before the merit actions.
- Since the threshold is a percentage, steps automatically follow a change of goal. Lowering the goal can even make a step be crossed.
- A threshold above 100% is possible, since the value can exceed the goal.

## Merit and Demerit Actions

- **Merit actions** are executed when the counter **reaches or exceeds** the goal (*Is Deserving* goes from 0 to 1).
- **Demerit actions** are executed when the counter **falls back below** the goal (*Is Deserving* goes from 1 to 0).

Actions only run when the goal is **crossed**. Adding points to a device that is already deserving does not run the merit actions again.

Actions are grouped into **events**:

- Each event has an optional **condition**. If it is false, the entire event is ignored. If it is left blank, the event always runs.
- Each event contains one or more **actions**. For each one, you can choose an action command (list button) or a scenario keyword: message, variable, scenario, wait, alert… (keyword button).
- You can disable an action without deleting it by unchecking its box.
- Events are executed in the order displayed, and so are the actions for each event. Actions can be reordered using the handle.

# Commands

| Command | Type | Description |
|---|---|---|
| **Value** | numeric info | Current counter value (never negative). |
| **Requires** | numeric info | Goal to reach (100 by default). |
| **Is Deserving** | binary info | 1 if Value ≥ Requires, 0 otherwise. |
| **Goal percentage** | numeric info (%) | Value / Requires × 100, rounded. Can exceed 100%. |
| **Missing** | numeric info | Points missing to reach the goal (Requires − Value, minimum 0). |
| **Merit** | slider action | Adds the slider value to the counter. |
| **Demerit** | slider action | Removes the slider value from the counter (minimum 0). |
| **Must Require** | slider action | Changes the goal (minimum 1). |
| **Win** | action | Sets the counter directly to the goal value. |
| **Reset to zero** | action | Sets the counter back to 0. |

Notes:

- Merit and Demerit with no value, or with 0, do nothing.
- The widget's sliders range from 0 to 100. From within a scenario, you can send a higher value (for example, *Must Require* set to 150).
- If the goal is lowered below the current value, the value is brought down to the new goal. It is not restored if the goal is raised again later.
- *Reset to zero* and *Demerit* run the demerit actions if the device was deserving. *Win* runs the merit actions if it was not deserving yet.
- *Is Deserving* can also be used as a trigger or condition in your scenarios.

# Examples of Use

## Electric load shedding

We want to avoid having too many high-power appliances running at the same time: oven, washing machine, dryer, dishwasher, and charging station.

- Create a Deserving device “Heavy consumers” with a goal of **3**.
- For each appliance, a small scenario does **Merit 1** when its power goes above a threshold and **Demerit 1** when it drops back. You can weight them: the charging station can count as 2.
- Merit actions: pause the charging station, turn off the water heater, send a notification.
- Demerit actions: re-enable everything.

Each device manages only its +1 and −1. Adding a device does not require modifying the other scenarios.

## Maintenance counter

For the filter in a mechanical ventilation system, water softener, or range hood, or the dustbin of a robot vacuum.

- The goal is the maintenance threshold (for example, 50 cycles).
- On each cycle, a scenario does **Merit**, optionally weighted: short cycle +1, long cycle +3.
- A step at 80% sends a “Maintenance needed soon” notification.
- Merit actions: “Remember to change the filter” notification. *Is Deserving* stays at 1 until the maintenance is done, which makes it a persistent reminder on the dashboard.
- After maintenance, click **Reset to zero** on the dashboard.

## Merit Points

- Each completed task earns points (**Merit 10**, **Merit 20**…) via a button, an interaction, or a scenario.
- A missed task removes points (**Demerit 5**).
- Goal of 100, with **Reset** checked: each time the goal is reached, a reward is triggered (turn on a plug, send a notification…).
- A weekly scenario does **Reset to zero** to start over.

# Logs

The `deserve` log reports, at **info** level, every time the goal is crossed. At **debug** level, it also details every value change, every evaluated condition and every executed action.
