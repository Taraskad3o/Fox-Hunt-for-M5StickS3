# Fox Hunt for M5StickS3

Active hide-and-seek game for two M5StickS3 devices. One player hides as the Fox, and the other searches as the Hunter.

The game uses radio (ESP-NOW) to track distance like a "hot-or-cold" radar and an infrared beam (IR) on top of the device for direct line-of-sight tag shots.

---

## Hardware

- 2x M5StickS3 devices.
- No extra components required: all game mechanics use the built-in screen, buttons, speaker, radio antenna, and top-facing IR transmitter/receiver.

Important:
The infrared sensor is located on the top edge of the M5StickS3. Do not cover the top of the case with fingers, stickers, or clothes, or shots will not register.

---

## Game Rules

### Role Selection
When turned on, the screen prompts for role selection:
- Side Button: Choose Fox.
- Blue Front Button: Choose Hunter.
- Both Buttons (pressed together): Return to role selection menu.

### Hunter
- Starts with 5 shots.
- The screen shows a signal bar in the center. When the bar is low (green), the Fox is far away. When the bar fills up with yellow and red segments, the Fox is nearby.
- Press the Blue Front Button to fire.
- Save your ammo: Shooting from far away is useless. The IR beam will miss, the Fox will not react, and you will lose the game once all 5 shots are spent. Wait until the signal bar turns red to strike!
- You must aim the top of the device directly at the Fox.
- If you shoot while close to the Fox and miss with the IR beam, the Fox dodges, and you receive a 30-second penalty lockdown during which you cannot shoot.
- If you use all 5 shots without tagging the Fox, you lose.

### Fox
- Hide and do not get tagged.
- The Fox automatically barks at random intervals (every 40 to 75 seconds) and can manually bark using the Side Button.
  - If the IR beam hits your device, you are caught and the Hunter wins.
  - If the IR beam does not hit, you successfully dodge: a 30-second countdown screen appears, giving you time to run and hide again while the Hunter is penalized.

---

## How to Flash via Arduino IDE

### 1. Requirements
- Arduino IDE 2.x
- ESP32 Board Package (by Espressif) version 3.0.0 or newer
- M5Unified library (install via Library Manager: Tools -> Manage Libraries -> search "M5Unified")

No third-party IR libraries are required. The project uses built-in ESP-IDF drivers.

### 2. Board Configuration
Open Arduino IDE, connect the M5StickS3 via USB-C, and set the following under the Tools menu:
- Board: M5StickS3 (or "ESP32S3 Dev Module")
- USB CDC On Boot: Enabled
- Flash Size: 8MB
- Partition Scheme: Default 8MB with SPIFFS
- PSRAM: OPI PSRAM
- Upload Speed: 921600
- Port: Select the COM port corresponding to your connected device

### 3. Flashing
1. Open the project sketch (`.ino` file).
2. Click the Upload button.
3. Flash the exact same sketch to both M5StickS3 devices.

4. Please note: every letter and pixel of this project is a "vibecode" cursed by all the gods—please be extremely attentive and understanding. I did the best I could; please forgive me.

i'm an anomalocaris "I do my best"
