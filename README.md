# FabLab Internship Code (SP FabLab / T1442)

This repository contains the code I developed and used during my internship at **Singapore Polytechnic FabLab (T1442)**.


---

## Main Project Folder

### `CDIO_PivotLab/`
This folder contains the full firmware for **PivotLab** (ESP32-based).

PivotLab includes:
- OLED menu UI with multiple modes  
- Rotary encoder navigation + push button  
- Servo motor control for moving the mechanism  
- AS5600 magnetic encoder feedback for angle/balance detection  
- Auto-balance / hold logic and smoothing/filtering  
- Saving settings using ESP32 non-volatile memory (Preferences / NVS)


## PivotLab Modes

- **Normal Mode**  
  User balances the system, then the device moves to a new position. Complete a set number of moves to finish.

- **Infinite Mode**  
  Similar to Normal Mode but continues until a time limit / condition ends the game.

- **Education Mode**  
  After balancing, the device shows a question with multiple-choice options to reinforce concepts.

- **Auto-Balance Mode**  
  Device adjusts servo movement to automatically bring the system close to equilibrium.

- **Settings**  
  Configure saved angles/values used by the modes. Values persist across restarts using **Preferences (NVS)**.


## Hardware / Wiring Notes

### ESP32 I2C (common default)
PivotLab uses I2C peripherals (OLED + AS5600). Typical ESP32 wiring:
- **SDA = GPIO 21**
- **SCL = GPIO 22**

OLED and AS5600 can share the same SDA/SCL lines.

### Other components (project specific)
- Rotary Encoder: CLK/DT + SW button
- Servo motor: PWM output pin
- AS5600: I2C + OUT pin for analog read approach



These remain saved after power off/on. Use your “Reset” option (or a reset function) to restore defaults.

