---
layout: default
lang: en_US
title: AdGuard Home Plugin - Changelog
description: AdGuard Home Plugin Changelog
---
Unless otherwise noted, this is likely a minor update to correct spelling or ensure compatibility with Jeedom V4.x

# Changelog

## In Beta
- New widget for AdGuard Home (dashboard and mobile), inspired by the AdGuard Home dashboard: protection with a menu for pause durations and a countdown, statistics, and clickable tiles (filtering, safe browsing, parental controls, secure search, blocked websites)
- New widget for customer devices (dashboard and mobile): Internet access allowed or blocked via a button, clickable tiles (general settings, filtering, browsing security, parental controls, safe search, generally blocked services), blocked usernames and services
- Widgets: switch-based settings with tooltips, built-in actions on a single line (services, groups, rules, credentials, domain test with results, maintenance), and AdGuard Home updates via the widget badge. See the [beta documentation](index-beta#widgets-en-beta)
- Widgets: blocked services displayed as icons, both on the server and on client devices
- List of services with icons, search, and services organized by group; selecting a group locks or unlocks the entire group
- Widgets: confirmation before disconnecting from the internet, disabling filtering or parental controls, blocking or unblocking all services, and before performing maintenance actions (DNS cache, filters, statistics)
- Widgets: minimum width of 320 px on the dashboard with a responsive layout; full width on mobile
- Widgets: automatic height adjustment based on content, with a “Widget Height: Fixed” option on the device to maintain the height set in edit mode
- New "Remaining Pause" information: time remaining (in seconds) before protection resumes
- New actions: “Clear the DNS cache” and “Update filters”
- New "Test a Domain" action (and "Domain Test Result" information) on the AdGuard Home device, and "Test a Domain for This Client" on clients
- New actions: “Block a service group” and “Unblock a service group,” available globally and per client (AdGuard Home v0.107.68 or later)
- The blocked services schedule defined in AdGuard Home is no longer cleared when a service is blocked or unblocked from Jeedom
- Secure search (global and per-user): only the enabled/disabled status changes; the search engines selected in AdGuard Home are retained (including Ecosia)
- Browsing safety and parental controls use the latest AdGuard Home API calls, with fallback to older calls for older versions
- "Update Filters" and "AdGuard Update" wait up to 120 seconds for a response from AdGuard Home (previously, the command would fail and "Online" would change to 0)
- Reliability: Actions now display a clear message when AdGuard Home is unresponsive, when the client cannot be found, or when the rule is empty, rather than failing silently. Custom rules can no longer be accidentally deleted, and blocking the internet twice no longer creates a duplicate entry
- Fixing clients whose names contain a hyphen
- Fixed network error detection (PHP 8)
- When a client is modified, only the editable fields are sent to AdGuard Home
- Corrected the spelling error “globlaux” in the customer commands (“Use Global Blocked Services”)
- Translated command help texts

## 26-11-2026
- Compatible with AdGuard Home v1.0.0

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

