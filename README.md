![Logo](admin/eufy-security.png)
# ioBroker.eufy-security

[![NPM version](http://img.shields.io/npm/v/iobroker.eufy-security.svg)](https://www.npmjs.com/package/iobroker.eufy-security)
[![Downloads](https://img.shields.io/npm/dm/iobroker.eufy-security.svg)](https://www.npmjs.com/package/iobroker.eufy-security)
![Number of Installations (latest)](http://iobroker.live/badges/eufy-security-installed.svg)
![Number of Installations (stable)](http://iobroker.live/badges/eufy-security-stable.svg)
[![Dependency Status](https://img.shields.io/david/bropat/iobroker.eufy-security.svg)](https://david-dm.org/bropat/iobroker.eufy-security)
[![Known Vulnerabilities](https://snyk.io/test/github/bropat/ioBroker.eufy-security/badge.svg)](https://snyk.io/test/github/bropat/ioBroker.eufy-security)

**Tests:** Linux/Mac: [![Build Status](https://travis-ci.org/bropat/ioBroker.eufy-security.svg?branch=master)](https://travis-ci.org/bropat/ioBroker.eufy-security)
Windows: [![AppVeyor](https://ci.appveyor.com/api/projects/status/github/bropat/ioBroker.eufy-security?branch=master&svg=true)](https://ci.appveyor.com/project/bropat/ioBroker-eufy-security/)


[![NPM](https://nodei.co/npm/iobroker.eufy-security.png?downloads=true)](https://nodei.co/npm/iobroker.eufy-security/)

The development of this adapter was only possible thanks to the work of the following people:

* FuzzyMistborn (https://github.com/FuzzyMistborn/python-eufy-security)
* keshavdv (https://github.com/keshavdv/python-eufy-security)
* JanLoebel (https://github.com/JanLoebel/eufy-node-client)

Credits goes to them.

If you appreciate my work and progress and want to support me, you can do it here:

[![ko-fi](https://www.ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/E1E332Q6Z)

## Description

This adapter allows to control Eufy security devices by connecting to the Eufy cloud servers.

You need to provide your Cloud login credentials. The adapter connects to your cloud account and polls for all device data via HTTPS. Because of this the devices need to be connected to their cloud. Currently no way is known to control the devices locally.

One Adapter instance will show all devices from one Eufy Cloud account and allows to control them.

## Features

* Base station:
    * States:
        * Configured Guard mode
        * Current Guard mode
        * Name
        * Model
        * Serial number
        * Software version
        * Hardware version
        * MAC address
        * LAN ip address
    * Actions:
        * Change guard mode
        * Reboot station
    * Events:
        * Alarm mode change
* Camera:
    * States: 
        * Online / offline etc.
        * Battery %
        * Battery temperature
        * Name
        * Model
        * Serial number
        * Software version
        * Hardware version
        * MAC address
        * Wifi RSSI
        * Filtered false events since last charge
        * Saved/Recorded events since last charge
        * Total events since last charge
        * Used days since last charge
    * Actions:
        * Start livestream (hls; supports also local livestream)
        * Stop livestream (hls)
        * Enable/disable device
        * Enable/disable auto night vision 
        * Enable/disable led (only camera 2 products, indoor cameras, floodlight camera and solo cameras)
        * Enable/disable anti-theft detection (only camera 2 products)
        * Change video watermark setting
    * Events:
        * Motion detected
        * Person detected
        * Ringing (only Doorbell)
        * Crying detected (only Indoor cameras)
        * Sound detected (only Indoor cameras)
        * Pet detected (only Indoor cameras)
* Sensor
    * Entry sensor:
        * States: 
            * Online / offline etc.
            * Low battery
        * Events: 
            * Open / closed
    * Motion sensor:
        * States:
            * Online / offline etc.
            * Low battery
        * Events:
            * Motion detected
* Keypad:
    * States:
        * Online / offline etc.
        * Low battery
* Two factor authentication
* more to come...

## Configuration

See [here](./docs/en/README.md)

## Known working devices

* HomeBase (T8001)
* HomeBase E (T8002)
* HomeBase 2 (T8010)
* eufyCam (T8111)
* eufyCam E (T8112)
* eufyCam 2 (T8114)
* eufyCam 2C (T8113)
* eufyCam 2 Pro (T8140)
* eufyCam 2C Pro (T8141)
* Floodlight (T8420)
* Wired Doorbell 2k (T8200)
* Wired Doorbell 1080p (T8201)
* Battery Doorbell 2K (T8210)
* Battery Doorbell 1080p (T8222)
* Entry Sensor (T8900)
* Motion sensor (T8910)
* Indoor Cam Pan&Tilt 2K (T8410)
* Indoor Cam 2K (T8400)
* Indoor Cam Pan&Tilt 1080p (T8411)
* Indoor Cam 1080p (T8401)

If more devices work (or also not) please report them by opening a GitHub issue.

## How to report issues and feature requests

Please use GitHub issues for this.

Best is to set the adapter to Debug log mode (Instances -> Expert mode -> Column Log level or see [here](https://github.com/bropat/ioBroker.eufy-security/wiki/Howto-enable-debug)). Then please get the logfile from disk (subdirectory "log" in ioBroker installation directory and not from Admin because Admin cuts the lines).

## Changelog

### 0.2.5 (2021-02-20)
* (bropat) Fixed possible race condition that brokes sometime the livestream
* (bropat) Updated versions of the package dependencies

### 0.2.4 (2021-02-20)
* (bropat) Fixed issue [#86](https://github.com/bropat/ioBroker.eufy-security/issues/86)
* (bropat) Fixed not correctly identifying if the livestream is still active or not

### 0.2.3 (2021-02-17)
* (bropat) Fixed wired doorbell p2p livestream (should fix also indoor, floodlight and solo cameras)
* (bropat) Fixed issue that treats known push notifications as unknown
* (bropat) Fixed relative path for state last_event_pic_url
* (bropat) Updated versions of the package dependencies

### 0.2.2 (2021-02-16)
* (bropat) Fixed web extension settings for serving videos and pictures (issue [#79](https://github.com/bropat/ioBroker.eufy-security/issues/78))

### 0.2.1 (2021-02-15)
* (bropat) Fixed device_enable state
* (bropat) Fixed battery doorbell start livestream over p2p (issue [#78](https://github.com/bropat/ioBroker.eufy-security/issues/78))
* (bropat) Implemented fallback for failed P2P livestream to RTMP livestream

### 0.2.0 (2021-02-14)
* (bropat) Implemented P2P livestream over HLS
* (bropat) Last livestream is always saved and is still available later
* (bropat) Implemented device and station parameter refresh over P2P
* (bropat) Revised push notification implementation
* (bropat) Fixed issue [#71](https://github.com/bropat/ioBroker.eufy-security/issues/71) by implementing retry mechanism on HTTP error 404 (max. 5 retries with increasing delay) 
* (bropat) Fixed issue [#12](https://github.com/bropat/ioBroker.eufy-security/issues/12)
* (bropat) Eufy client library extracted as standalone library and adapters ported to new shared library: [eufy-security-client](https://www.npmjs.com/package/eufy-security-client)
* (bropat) Removed following states: last_captured_pic_url, last_captured_pic_html
* (bropat) Updated versions of the package dependencies

### 0.1.5 (2021-01-14)
* (bropat) Fixed issue [#50](https://github.com/bropat/ioBroker.eufy-security/issues/50) and [#53](https://github.com/bropat/ioBroker.eufy-security/issues/53)
* (bropat) Updated versions of the package dependencies

### 0.1.4 (2021-01-05)
* (bropat) Fixed: Accept only valid modes for station guard mode (for invalid mode, an error is logged)
* (bropat) Fixed reset of an event (motion, ringing, etc.)
* (bropat) Updated versions of the package dependencies

### 0.1.3 (2021-01-02)
* (bropat) Fixed issue [#37](https://github.com/bropat/ioBroker.eufy-security/issues/37) and [#41](https://github.com/bropat/ioBroker.eufy-security/issues/41)
* (bropat) Updated versions of the package dependencies

### 0.1.2 (2021-01-02)
* (bropat) Revised captured_pic_url state (renamed to last_captured_pic_url and added last_captured_pic_html)
* (bropat) Fixed p2p issue passing wrong user id (action_user_id instead of admin_user_id)
* (bropat) Revised push notification to properly support doorbell notifications
* (bropat) Updated versions of the package dependencies

### 0.1.1 (2020-12-29)
* (bropat) Fixed issue [#37](https://github.com/bropat/ioBroker.eufy-security/issues/37)
* (bropat) Fixed version numbering
* (bropat) Updated versions of the package dependencies

### 0.0.9 (2020-12-28)
* (bropat) Finished implementation for feature request: [#1](https://github.com/bropat/ioBroker.eufy-security/issues/1)
* (bropat) Little progress for feature request: [#5](https://github.com/bropat/ioBroker.eufy-security/issues/5)
* (bropat) Now supports also cloud P2P communication if local P2P comunication isn't possible
* (bropat) Implemented set Guard Mode with CMD_SET_PAYLOAD for certain devices
* (bropat) Added back USA ip addresses for P2P cloud discovery
* (bropat) Using the correct local time zone for communication with the Eufy Cloud
* (bropat) HUB filtering by device type 0 (station) removed
* (bropat) Added documentation for 2FA
* (bropat) Updated versions of the package dependencies

### 0.0.8 (2020-12-13)
* (bropat) Fixed issue [#16](https://github.com/bropat/ioBroker.eufy-security/issues/16)
* (bropat) P2P communication revisited
* (bropat) Added reconnect functionality for P2P communication
* (bropat) Added heartbeat for P2P communication
* (bropat) Added local caching of last event picture as image url or html image (removed old state: last_camera_url)
* (bropat) Updated versions of the package dependencies

### 0.0.7 (2020-12-08)
* (bropat) Fixed issue [#11](https://github.com/bropat/ioBroker.eufy-security/issues/11)

### 0.0.6 (2020-12-06)
* (bropat) Fixed issue [#13](https://github.com/bropat/ioBroker.eufy-security/issues/13)

### 0.0.5 (2020-12-05)
* (bropat) Added event states for camera (motion detected, person detected)
* (bropat) Added event states for entry sensor (open/closed)
* (bropat) Added event states for motion sensor (motion detected)
* (bropat) Added event states for doorbell (motion detected, person detected, ringing)
* (bropat) Added event states for indoor camera (motion detected, person detected, crying detected, sound detected, pet detected)
* (bropat) Added entry sensor state (online, offline, etc.)
* (bropat) Added entry sensor low battery
* (bropat) Added motion sensor state (online, offline, etc.)
* (bropat) Added motion sensor low battery
* (bropat) Added keypad state (online, offline, etc.)
* (bropat) Added keypad low battery

### 0.0.4 (2020-12-03)
* (bropat) Better exception handling
* (bropat) Fixed push token handling
* (bropat) Added push connection retry mechanism
* (bropat) Added camera state (online, offline, etc.)
* (bropat) Added camera wifi RSSI
* (bropat) Added camera total events since last charge
* (bropat) Added camera saved/recorded events since last charge
* (bropat) Added camera filtered false events since last charge
* (bropat) Added camera used days since last charge
* (bropat) Added camera battery temperature

### 0.0.3 (2020-11-21)
* (bropat) Fixed issue with push notification credentials initialization

### 0.0.2 (2020-11-21)
* (bropat) Added push notification support for event notification (raw notifications!)
* (bropat) Added 2FA (token renewal needs manual intervention)
* (bropat) Added P2P communication with station (event: Alarm mode change)
* (bropat) Added more device classes (sensors, locks, keypads) with no actions (at the moment! WIP!)
* (bropat) Added all eufy camera devices release to date
* (bropat) Added battery state to eufy cameras

### 0.0.1 (2020-10-04)
* (bropat) initial release

## License
MIT License

Copyright (c) 2021 bropat <patrick.broetto@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.