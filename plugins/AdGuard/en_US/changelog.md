---
layout: default
lang: en_US
title: AdGuard Home Plugin - Changelog
description: AdGuard Home Plugin Changelog
---
Unless otherwise noted, this is likely a minor update to correct spelling or ensure compatibility with Jeedom V4.x

# Changelog

## 12-11-2026
- Configuration requires administrator privileges

## 30-01-2025
- Translation of command names
- Fixing a PHP warning if there are no user rules
- (Thanks @TomiTomas): Added protection deactivation time (as in AdGuardHome)

## 07-10-2024
- Added a "Community" button to make it easier to get help

## 12-08-2024
- Translations and updates to translations in English, German, Spanish, Italian, and Portuguese

## 11-09-2023
- Version v0.107.37 is required!
- Changes to blocked services starting with version v0.107.37

## 24-05-2023

- Changes for new API elements in v0.107.28 (protection enabled + safe search)
- No option to choose the search engine for SafeSearch protection at this time (is this necessary??)
- Currently, there is no option to set a timer for deactivating protection (is this necessary with Jeedom? Since you can reactivate it via a scenario or other means...)
- Fix for the Update command
- Encryption of your AdGuard passwords in the Jeedom database
- **Requires AdGuard version v0.107.28 or later!**


## 14-11-2022

- Fix internet block/unblock and custom rules (on versions v0.107.14+), update to v0.107.17+
- Requires AdGuard version 0.107.17 or later!

## 04-11-2022

- Starting with v0.107.17, AdGuard supports new services (iCloud Private Relay, etc.). This version requests the list of services from AdGuard and updates the commands as needed.

## 08-09-2022

- Added support for the BiliBili service in v0.107.12
- No more errors if version.json is no longer available on AdGuard (due to a bug on their end)

## 28-06-2022

- Added the HTTPS protocol for those using a proxy or similar

## 08-04-2021

- Added the current version and the new version to the commands. If a new version is available at the time of the update, AdGuard won't send me the old version number, so that field will be empty... but as soon as you update, it will be updated, and then everything will be fine.
- English & Spanish translation
- Fix commands that link to the "Block Internet via DNS" action

## 21-09-2021

- Check if a device already exists in the same room as the customer and is turned off

## 15-09-2021

- Initialization

