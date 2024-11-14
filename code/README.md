# SpotMicroESP32 Arduino Code

This directory contains the Arduino code for controlling the SpotMicroESP32 robot dog. The structure includes files for managing gait, kinematics, and setup procedures, tailored for integration with our custom PCB and the FS-i6 hobby controller.

## Coding by Charlie Frater & Beckett Macdonald ##

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
  - FS-i6X hobby controller.
![Reciever](https://github.com/Blacksheep909/SpotMicroESP32/blob/master/code/FS-I6X%2B20160331.450(1).png)

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

### Code Flowchart

![Flowchart](https://github.com/Blacksheep909/SpotMicroESP32/blob/master/code/detailed_robot_dog_flowchart.png)


### Steps to Set Up Failsafe on the FS-i6X

A Failsafe on the FS-i6X transmitter is essential to ensure that your robot dog safely stops or returns to a safe position if it loses signal from the transmitter. This process essentially "teaches" the transmitter what signal to send when a connection loss occurs, allowing you to set specific servo positions or actions to minimize risk.

1. **Access the Failsafe Settings:**
   Power on your FS-i6X transmitter and navigate to the "RX Setup" menu. From there, select the "Failsafe" option, which allows you to set failsafe values for each channel.

2. **Set Desired Positions:**
   For each channel, adjust the controls to position the servos or outputs in the desired failsafe position (e.g., legs in a stable position, motors off). Once the controls are in the preferred positions, select "Set" to lock in these values as the failsafe.

3. **Confirm Failsafe Activation:**
   After setting, you can test the failsafe by powering off the transmitter to simulate signal loss. The servos should move to the predefined failsafe positions.

For a more detailed, step-by-step visual example, you can refer to [this video tutorial](https://www.youtube.com/watch?v=4N_hHfpEoHY).

*Photo here shows what it should look similar to.*
![Transmitter](https://github.com/Blacksheep909/SpotMicroESP32/blob/master/code/20241114_190217(1).jpg)

### Steps to Set Up Output MODE on the FS-i6X
To ensure your FS-i6X transmitter is set to output in "PWM" and "I-BUS" mode, follow these steps:

1. **Access the Output Mode Menu:**
   - Power on the FS-i6X transmitter.
   - Press and hold the "OK" button to enter the main menu.
   - Use the directional buttons (up & down) to scroll to "System Setup," and press "OK" to select it.

2. **Select Output Mode:**
   - In the "System Setup" menu, go to 'RX Setup' press 'OK'. Next scroll down to find the "Output Mode" option (it's down a page), then press "OK" to open it.
   - You should see options for various output modes, including "PWM" and "I-BUS."

3. **Set to PWM and I-BUS:**
   - Highlight "PWM" to enable standard servo signal output for each channel.
   - Then select "I-BUS" if you need the transmitter to communicate with compatible receivers using FlySky's I-BUS protocol, often used for sensor data or expanded channel output.
   - Confirm your selections by pressing "OK."

4. **Save and Exit:**
   - Once both "PWM" and "I-BUS" are selected, HOLD the "CANCEL" button to exit back to the main screen.
   - The settings should now be saved, and your transmitter will operate in PWM and I-BUS modes. (settings will only be saved if cancel button is HELD)

Following these steps will configure your FS-i6X transmitter to ensure compatibility with devices using PWM and I-BUS outputs.

*Picture below of what the settings menu should look like when in the correct output mode*
![OUTPUT](https://github.com/Blacksheep909/SpotMicroESP32/blob/master/code/20241114_211004(1).jpg)


# Future development
- The gait and inverse kinematics are currently still in the early-ish side of development. They work, but can always be better of course.
- I would like to add a tilt mode feature where the user can look around with the dog using a joystick.
- Another feature I would like to add is a move advanced walking gait -this is currently my main aim with the code
- A missing feature, which is of course fully neccesary is the LR code (left-right), so the dog can actually turn, but currently the shoulders are not included in the inverse kinematics.

There are many other things I am likely forgetting, and of course this will happen in due time, but I am unsure how long they may take -right now my aim is to upload this code to get people kickstarted, and maybe someone will take on the challenge to make it even better!

## Contributing

- For contributions or to report issues, please contact us or open an issue in this fork’s repository.

### My Discord is blacksheep909 if you would like to contact me
---
