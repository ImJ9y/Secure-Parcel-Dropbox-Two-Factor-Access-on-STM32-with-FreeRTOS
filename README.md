# Secure Parcel Dropbox: Two-Factor Access on STM32 with FreeRTOS

Low-power secure parcel dropbox on the STM32L475 IoT Discovery board. FreeRTOS tasks coordinate time-of-flight package detection, NFC phone authentication, a lock PWM and WiFi notifications through a queue-driven state machine.

*ECEN 501 Embedded Systems final project, Santa Clara University.*

> **Status:** work in progress. The FreeRTOS skeleton (state machine, event queue, button interrupt, state timeouts, memory monitor) is in place; sensors, NFC authentication and WiFi are being added.

## Overview

This project implements an authenticated parcel dropbox on the STM32L475 IoT Discovery Node (B-L475E-IOT01A1). A courier's button press opens the chute, and a time-of-flight sensor confirms when a package is placed or removed. The owner unlocks the box by tapping a phone on the onboard NFC tag, with a hand gesture as a second factor; a failed attempt triggers a timed alarm.

FreeRTOS tasks communicate through a message queue, task notifications and mutexes, while a central state machine (Idle, Delivery, Package Stored, Retrieval, Alarm) controls the system and reports events to a phone over WiFi. The design uses interrupts and low-power sleep modes to minimize power consumption.
