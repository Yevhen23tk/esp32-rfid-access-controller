# ESP32 RFID Access Controller

A small access control project built with ESP32, ESPHome and Home Assistant.

The controller reads RFID tags using an RC522 module, checks the tag UID and then grants or denies access.

## Features

- RFID tag reading with RC522
- Access granted / denied logic
- Green and red LED indication
- Different buzzer sounds for granted and denied access
- Servo control for door opening
- Home Assistant integration
- Last scanned RFID tag in Home Assistant
- Access result in Home Assistant
- Manual controls from Home Assistant
- OTA firmware updates

## Hardware

- ESP32 DevKit
- RC522 RFID reader
- SG90 servo
- 2 LEDs
- Passive buzzer
- Breadboard and jumper wires

## Wiring

| Component | ESP32 |
|---|---|
| RC522 SCK | GPIO18 |
| RC522 MOSI | GPIO23 |
| RC522 MISO | GPIO19 |
| RC522 SDA / CS | GPIO27 |
| RC522 RST | GPIO22 |
| Green LED | GPIO25 |
| Red LED | GPIO26 |
| Buzzer | GPIO14 |
| Servo signal | GPIO13 |

RC522 is powered from 3.3V.

The servo uses 5V and shares GND with the ESP32.

## How it works

When an RFID tag is scanned, ESP32 receives its UID.

If the UID is allowed:

- green LED turns on
- granted sound is played
- servo opens the lock
- Home Assistant shows `Granted`

If the UID is not allowed:

- red LED turns on
- denied sound is played
- Home Assistant shows `Denied`

## Home Assistant

The controller is connected to Home Assistant using the ESPHome API.

Home Assistant can show:

- Last RFID Tag
- Access Result
- WiFi Signal

It also has manual controls for:

- Open Door
- Green LED
- Red LED
- Granted Sound
- Denied Sound

## Screenshots



### Hardware

<img width="1255" height="945" alt="IMG_20260928_170147" src="https://github.com/user-attachments/assets/a11a7a6b-95b6-4bd6-8b37-638dff900704" />


### Home Assistant

<img width="2000" height="985" alt="image" src="https://github.com/user-attachments/assets/daf3c645-8d71-47c0-8f38-de570967fb4b" />
<img width="2000" height="981" alt="image" src="https://github.com/user-attachments/assets/3dcbb6b3-9726-4f21-85b1-b2ba2e9a759e" />
<img width="2000" height="979" alt="image" src="https://github.com/user-attachments/assets/63401cd3-ac74-4aa4-865d-a162d1835db4" />
### Logs


<img width="2000" height="1031" alt="image" src="https://github.com/user-attachments/assets/0de19b0d-7096-4823-89e9-4e396ece0d10" />

## Status

The main functionality is complete.

This is a learning and portfolio project, not a production access control system.

## Possible improvements

- support multiple access keys
- access history
- external database for access keys
- more C++ logic
- better error handling

## Security

The current version uses RFID UID for identification.

Some RFID tags can be cloned, so this project should not be used for security-critical access control.
