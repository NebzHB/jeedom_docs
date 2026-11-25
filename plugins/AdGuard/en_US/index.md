---
layout: default
lang: en_US
title: AdGuard Home Plugin
description: AdGuard Home Plugin Documentation
---

This plugin lets you monitor and perform certain actions on your AdGuard Home devices.

Plugin Configuration
=======================

After installing the plugin, simply activate it. No special configuration is required.

Device Setup
=============================

You can access the AdGuard settings from the menu
Plugins, then Monitoring. Here you'll find:

-   a button to manually create a device

-   a button to display the plugin's configuration

-   a button that gives you an overview of all your devices at any given time

-   Finally, below you'll find a list of your AdGuard Home devices and associated clients

When you click on one of your devices, you'll be taken to the page
Configuration of your equipment, consisting of two tabs: "Equipment" and
commands.

-   **Equipment tab**:

-   **Device Name**: Name of your device

-   **Activate**: turns your device active

-   **Visible**: Makes it visible on the dashboard

-   **Parent object**: specifies the parent object to which the device belongs

**For AdGuard only**

-   **Server IP**: The IP address of the AdGuard Home server.

> If you have changed the default port (80), you can add your port here in the format ip:port

-   **User**: AdGuard Home user.

-	**Password**: AdGuard Home user password.

-	**Automatic Refresh (cron)**: Interval for checking data on AdGuard Home; 5 minutes by default.

Once AdGuard Home has been added and the devices have been backed up, the clients found in AdGuard Home are added as separate devices.

If you **add a client** later, it will be added **automatically overnight**. To force its addition to Jeedom, **resave the AdGuard Home device**.

If you **remove a client** later, it will be **automatically deactivated overnight**; to force its deactivation in Jeedom, **resave the AdGuard Home device**.

> Note: A **Client**-type device must be **disabled in order to be deleted**.

**AdGuard Equipment Commands**
================================
- **Refresh**: Allows you to manually refresh the device in addition to the automatic refresh
- **Online**: A binary value indicating whether AdGuard is responding correctly to requests
- **AdGuard Update Available**: A binary value indicating whether an update is available
- **Update AdGuard**: Action to update AdGuard (if an update is available)

Comprehensive Protection
-----------------------
- **Protection Status**: A binary value indicating the status of overall protection
- **Enable Protection**: Action to enable global protection
- **Disable Protection**: Action to disable global protection

> New: You can now change the duration for which protection is disabled (just like in the AdGuardHome interface)

**AdGuard Correspondence**:

![image](https://user-images.githubusercontent.com/28622481/133206289-810d7a4d-9705-4923-9831-e8e78100f05b.png)

Global Filtering
-----------------------
- **Global Filtering Status**: A binary value indicating the status of global filtering
- **Enable Global Filtering**: Action to enable global filtering
- **Disable Global Filtering**: Action to disable global filtering

**AdGuard Settings** (Settings > General Settings > Block domains using filters and host files):

![image](https://user-images.githubusercontent.com/28622481/133206778-015af02d-8039-4c78-9732-e048c41cfa21.png)

Overall Browsing Security
-----------------------
- **Global Navigation Security Status**: A binary value indicating the status of Global Navigation Security
- **Enable Global Browsing Security**: Action to enable Global Browsing Security
- **Disable Global Browsing Security**: An action that disables Global Browsing Security

**AdGuard Correspondence** (Settings > General Settings > Use AdGuard's Safe Browsing service):

![image](https://user-images.githubusercontent.com/28622481/133207227-8f9aa942-54c6-4048-8fa1-3711f4ca082c.png)

Comprehensive Parental Controls
-----------------------
- **Global Parental Controls Status**: A binary value indicating the status of Global Parental Controls
- **Enable Global Parental Controls**: Action to enable Global Parental Controls
- **Disable Global Parental Controls**: Action to disable Global Parental Controls

**AdGuard Settings** (Settings > General Settings > Use AdGuard Parental Controls):

![image](https://user-images.githubusercontent.com/28622481/133207419-bac0d204-c4fc-414d-b411-c7ec072ab514.png)

Secure Global Search
-----------------------
- **Global Secure Search Status**: A binary value indicating the status of Global Secure Search
- **Enable Global Safe Search**: Action to enable Global Safe Search
- **Disable Global Safe Search**: An action that disables Global Safe Search

**AdGuard Settings** (Settings > General Settings > Enable Safe Search):

![image](https://user-images.githubusercontent.com/28622481/133207585-41110514-75f3-4a13-8f73-f3aca3c93820.png)

Global Services
-----------------------
- **Blocked Services**: Channel listing services that are blocked globally
- **Block a service**: Action that allows you to block a service from the list
- **Unlock a service**: An action that unlocks a service from the list
- **Block All Services**: An action that blocks all services in the list
- **Unlock all services**: An action that unlocks all services on the list

**AdGuard Settings** (Filters > Blocked Services):

![image](https://user-images.githubusercontent.com/28622481/133207917-e813a4d1-42d2-491c-982a-ebabf6510383.png)

Internet Blocked via DNS
-----------------------
- **Internet Blocked via DNS Status**: A binary value indicating whether the Internet has been blocked via DNS
- **Block all internet access via DNS**: Action to block internet access via DNS
- **Unblock all internet access via DNS**: An action that allows you to unblock internet access via DNS

**AdGuard Matching** (Filters > Custom Filter Rules > add the rule: `||*^$important` first):

![image](https://user-images.githubusercontent.com/28622481/133210452-4ebbc8b0-836d-43a4-9db9-e01c2534679e.png)

Custom filtering rule
-----------------------
- **Add a custom filter rule**: Field for adding a custom filter rule first (spelling must be exact, without quotation marks around it)
- **Remove a custom filter rule**: Field used to remove a custom filter rule (spelling must be exact; do not use quotation marks around it)

See [here](https://github.com/AdguardTeam/AdGuardHome/wiki/Hosts-Blocklists){:target="_blank" rel="noopener"}

**AdGuard Settings** (Filters > Custom Filter Rules > Add the given rule first)

Statistics
-----------------------
- **Reset Statistics**: Resets the statistics to zero
- **DNS Requests**: Shows the number of DNS requests processed in the last 24 hours
- **Blocked by Filters**: indicates the number of DNS requests blocked by adblock filters and host blocklists
- **Blocked malware-phishing attempts**: shows the number of DNS requests blocked by AdGuard's Web Security module
- **Enforced Secure Queries**: indicates the number of DNS queries made using Secure Query
- **Blocked adult websites**: shows the number of blocked adult websites
- **Average processing time**: indicates the average time (in milliseconds) it takes to process a DNS query

**AdGuard Settings** (Settings > General Settings > Statistics Configuration > Clear Statistics button):

![image](https://user-images.githubusercontent.com/28622481/133211167-470e9959-bda7-4810-a02d-8d26363bb981.png)

**and** (Dashboard > General Statistics):

![image](https://user-images.githubusercontent.com/28622481/133211276-6c24d23c-6647-4b5f-a26c-e5834bd1a657.png)

**Customer Equipment Commands**
================================

Using General Settings
--------------------------------
- **"Use General Settings" Status**: A binary value indicating whether "Use General Settings" has been enabled
- **Enable "Use General Settings"**: An action that enables "Use General Settings"
- **Disable "Use General Settings"**: An action that disables "Use General Settings"

**AdGuard Configuration** (Settings > Client Settings > Edit Client > Settings > Use General Settings (1)):

![image](https://user-images.githubusercontent.com/28622481/133217292-24f23ed8-8de2-492f-bd83-e9b90715de17.png)

Filtering
--------------------------------
- **Filtering Status**: A binary value indicating the filtering status
- **Enable Filtering**: Action to enable filtering
- **Disable Filtering**: An action that disables filtering

**AdGuard Configuration** (Settings > Client Settings > Edit Client > Settings > Block domains using filters and host files (2))

Browsing Security
-----------------------
- **Browsing Security Status**: A binary value indicating the status of browsing security
- **Enable Safe Browsing**: An action that enables Safe Browsing
- **Turn Off Browsing Security**: An action that turns off Browsing Security

**AdGuard Correspondence** (Settings > Client Settings > Edit Client > Settings > Use AdGuard's Safe Browsing service (3))

Parental Controls
-----------------------
- **Parental Control Status**: A binary value indicating the status of Parental Control
- **Enable Parental Controls**: Action to enable Parental Controls
- **Disable Parental Controls**: An action that disables Parental Controls

**AdGuard Configuration** (Settings > Client Settings > Edit Client > Settings > Use AdGuard Parental Controls (4))

Secure Search
-----------------------
- **Secure Search Status**: A binary value indicating the status of Secure Search
- **Enable Safe Search**: An action that enables Safe Search
- **Turn Off Safe Search**: An action that turns off Safe Search

**AdGuard Correspondence** (Settings > Client Settings > Edit Client > Settings > Enable Secure Search (5))

Use globally blocked services
--------------------------------
- **"Use Globally Blocked Services" status**: A binary value indicating whether "Use Globally Blocked Services" has been enabled
- **Enable "Use Globally Blocked Services"**: Action to enable "Use Globally Blocked Services"
- **Disable "Use Globally Blocked Services"**: An action that disables "Use Globally Blocked Services"

**AdGuard Rules** (Settings > Client Settings > Edit Client > Block Specific Services > Use Global Blocked Services (1)):

![image](https://user-images.githubusercontent.com/28622481/133218452-cf994ad7-bf63-4dbd-b727-ff64339b7b31.png)

Specific Services
-----------------------
- **Blocked Services**: A field listing the services specifically blocked for this customer
- **Block a service**: An action that allows you to block a service from the list specifically for this customer
- **Unlock a service**: An action that unlocks a service from the list specifically for this customer

**AdGuard Settings** (Settings > Client Settings > Edit Client > Block Specific Services > Services (2))

- **Block All Services**: An action that blocks all services on the list specifically for this client
- **Unlock all services**: An action that unlocks all services on the list specifically for this customer

**AdGuard Settings** (Settings > Client Settings > Edit Client > Block Specific Services > Block All/Unblock All (3))

Internet Blocked via DNS
-----------------------
- **Internet Blocked via DNS**: A binary value indicating whether the Internet has been blocked via DNS for this client
- **Block all internet access via DNS**: Action to block internet access via DNS for this client
- **Unblock all internet access via DNS**: Action to unblock internet access via DNS for this customer

**AdGuard Settings** (Filters > Custom Filter Rules > Add the rule: `||*^$client='ClientName',important` first)

![image](https://user-images.githubusercontent.com/28622481/133222436-9e17578a-93e2-4be2-a96c-957131d5686a.png)

Login credentials
-----------------------
- **ID(s)**: String containing the client's current IDs
- **Add an ID**: Action to add an ID to the customer (without quotation marks!!)
- **Remove a username**: Action to remove a username from the customer (without quotation marks!!)

> **Please note: if it exists on another client, you must first remove it from this client! AdGuard does not allow two clients to share the same credentials (makes sense ;))**

**AdGuard Settings** (Settings > Client Settings > Edit Client > ID):

![image](https://user-images.githubusercontent.com/28622481/133277119-3de65a3b-2868-4db1-b136-ca9c498270d3.png)
