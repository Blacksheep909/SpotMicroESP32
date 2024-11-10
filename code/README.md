# SpotMicroESP32 Arduino Code

This directory contains the Arduino code for controlling the SpotMicroESP32 robot dog. The structure includes files for managing gait, kinematics, and setup procedures, tailored for integration with our custom PCB and the FS-i6 hobby controller.

## Coding by Charlie Frater ##

- Below is some instructions on how to quickstart the provided (current) Arduino Code.

## Features

- **Joystick-Controlled Movement**: Supports forward-backward (FB) and left-right (LR) control using the FS-i6 transmitter, with configurable deadzones for precise control.
- **Failsafe Functionality**: Integrated failsafe handling stops the robot safely if the FS-i6 signal is lost.
- **Gait Customization**: Choose between square and arc gait cycles, with options to control timing, speed, and deadzones.
- **Tilt Mode**: Allows the robot to tilt its head or body to look around, providing an additional range of motion.
- **Servo Interpolation Using Ramp Library**: Smooth, controlled movements with acceleration and deceleration support for more lifelike walking.

## Code Structure

- **`INDEX_sketch_(DATE-CODENAME).ino`**: Main program loop and high-level control functions. Manages gait logic and overall behavior.
- **`Kinematics.ino`**: Handles inverse kinematics calculations for each leg, translating movement commands into precise leg positions.
- **`Procedure_Functions_Setup.ino`**: Includes setup procedures for initializing servos, sensors, and any other components. This file may also define utility functions for specific actions or movements.

## Getting Started

### Requirements

- **Hardware**:
  - SpotMicroESP32 robot dog with our custom PCB.
  - FS-i6 hobby controller.

- **Software**:
  - [Arduino IDE](https://www.arduino.cc/en/software)
  
- **Required Libraries**:
  Below are the libraries required for this project. Be sure to download and install them in your Arduino IDE under `Sketch > Include Library > Add .ZIP Library...`:

  - [Adafruit BusIO](https://github.com/adafruit/Adafruit_BusIO): Used for I2C/SPI communication in various sensors.
  - [Adafruit GFX Library](https://github.com/adafruit/Adafruit-GFX-Library): For graphical functions on displays.
  - [Adafruit MPU6050](https://github.com/adafruit/Adafruit_MPU6050): Provides support for the MPU6050 accelerometer/gyroscope.
  - [Adafruit PWM Servo Driver Library](https://github.com/adafruit/Adafruit-PWM-Servo-Driver-Library): Controls servos via the PCA9685 driver.
  - [Adafruit SSD1306](https://github.com/adafruit/Adafruit_SSD1306): For OLED display support (e.g., 0.96" OLED).
  - [Adafruit Unified Sensor](https://github.com/adafruit/Adafruit_Sensor): Standardized sensor library used by many Adafruit sensor libraries.
  - [AxTypeTraits](https://github.com/xoRaxes/AxTypeTraits): Provides type-trait functionalities, required by some Arduino projects.
  - [Bonezegi PCA9685](https://github.com/bonezegi/PCA9685): An alternative PCA9685 library for servo control.
  - [IBusBM](https://github.com/bolderflight/IBusBM): For handling the FS-i6 (iBus) receiver communication.
  - [Ramp](https://github.com/Erriez/ErriezRamp): Controls ramping (acceleration/deceleration) of servo movements.

- All of these libraries can be accessed within the Arduino IDE in the Libraries tab
### Setup and Configuration

1. **Configure Arduino Code**:
   - Open `INDEX_sketch_(DATE-CODENAME).ino` to customize settings for the robot’s movement, including:
     - **Deadzone thresholds** for FB and LR movements.
     - **Gait cycle timing** parameters.
     - **Failsafe settings** for signal loss protection.

2. **Upload to ESP32**:
   - Connect the ESP32 to your computer and upload the code.
   - Ensure all libraries are installed and configured in the Arduino IDE.

3. **Calibrate and Test**:
   - With the FS-i6 powered on, test each movement mode and adjust parameters in the code as needed for optimal performance.

### Usage

- **Basic Movements**:
  - Use the FS-i6 joystick for basic navigation.
  - Forward-backward (FB) control is prioritized, with left-right (LR) control enabled when FB is neutral.
- **Tilt Mode**:
  - Engage tilt mode via joystick to adjust SpotMicro’s head position.
- **Failsafe Activation**:
  - When the FS-i6 signal is lost, the robot stops moving automatically and returns to idle position.

## Contributing

For contributions or to report issues, please contact us or open an issue in this fork’s repository.

---

Everything you need to know, can be found in the [Official ESP-IDF API Reference](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/api-reference/index.html)	alongside with many linked example-projects to their [Github Examples Page](https://github.com/espressif/esp-idf/tree/master/examples).
