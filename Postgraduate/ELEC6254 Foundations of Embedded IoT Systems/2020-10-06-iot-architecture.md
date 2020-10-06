# Architectures

- There is no one architecture
  - we can learn from each impl

## Hardware w/ Typical Elements

- Power source (D/C, batteries, ...)
- PSU (Power Supplying Unit)
- MCU (Microcontroller)
- Communication hardware (radio transceivers, ...)
- I/O (to sensors)
- Storage (Flash, ...)

A lot of these depends on which MCU family is chosen

- A simple one: STM32 + separate transceiver
- SoC w/ many integrated peripherals
  - Atmel
  - ESP8266 w/ Wi-Fi, ESP32 w/ Wi-Fi & BT

<!-- 02:50 ESP32 is with Wi-Fi & BT but ESP8266 doesn't -->

## Internet Connected Things

Could mean that they have a full IP network connection to / from the Internet.

### Gateway

- Many systems need a gateway
  - Often more powerful, e.g. Linux-based
  - As a communication hub between the low-power hardware network and the outside world
  - As a protocol converter
    - things may not use IP (e.g. LoraWAN, BT LE)
  - As a firewall

## Basic Software Elements

- **Cloud**
  - storage, data analysis, ...
  - user interface
- **Network**
  - any network
- **Fog / Edge**
  - _a fuzzy and vague term_
  - ususally smart gateways
- **Objects**
  - behavior code (logic; what the device actually does)
  - application layer network stack
  - data storage
  - power management
- **OS / Drivers**
  - an OS prevents reinventing drivers

## Networks

- Wi-Fi / Ethernet
- LPWAN (Low Power Wide Area Networks)
  - Lo6WAN (IPv6 ones)
- Topology
  - starts
  - meshes

## Data Protocols

- Describes the data and the mechanisms
  - RESTful: `GET`, `PUT`, `POST`, `DELETE`
  - PubSub: e.g. MQTT
