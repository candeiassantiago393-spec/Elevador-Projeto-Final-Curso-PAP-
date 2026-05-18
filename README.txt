# Test Bench PAP — Elevator Hardware Tests

This main folder contains the **test bench files** developed for the PAP elevator project.

The purpose of this test bench is to validate each hardware section of the elevator prototype separately before integrating everything into the complete control program.

The tests are designed for the **real Arduino Mega implementation** and use the same pinout planned for the final elevator system.

---

## Project context

This test bench belongs to a **4-floor elevator prototype** developed as part of the PAP project.

The complete elevator system includes:

- External floor request buttons
- External request LEDs
- Internal cabin buttons
- Internal cabin LEDs
- Floor sensors
- Door permissive sensor
- Motor driver
- Buzzer
- OLED displays
- Emergency and rearm logic

However, this folder is focused only on **isolated hardware tests**, allowing each part to be checked safely before being connected to the complete system.

---

## Objective

The main objective is to create a clear and organised set of test files to verify:

- If each button is correctly wired
- If each LED is correctly wired
- If the Arduino Mega pins are working correctly
- If the button logic using `INPUT_PULLUP` is behaving correctly
- If several requests can be stored at the same time
- If the hardware is ready to be used in the final PAP elevator code

---

## Folder structure

```text
Test_Bench_PAP/
│
├── README.md
│
├── Test_01_External_Requests_LED_Latched/
│   └── Test_01_External_Requests_LED_Latched.ino
│
├── Test_02_External_Buttons_Only/
│   └── Test_02_External_Buttons_Only.ino
│
└── Test_03_External_LEDs_Only/
    └── Test_03_External_LEDs_Only.ino