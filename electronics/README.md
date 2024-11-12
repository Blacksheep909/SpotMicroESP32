### Overview of the PCB Design and Installation
![SpotMicroESP32](https://github.com/Blacksheep909/SpotMicroESP32/blob/master/electronics/Images/Screenshot%202024-11-11%20003432.png)

The provided PCB template is designed to simplify the assembly and wiring of your robot dog. It's intended as a flexible base where you can easily install components by soldering female pin headers onto the board. This allows components to be attached or removed as needed without complex soldering each time. 

This board includes pinouts for every expected component, such as:

- **ESP32 Dev Kit**: Used as the primary microcontroller.
- **iBus RC Receiver (FS-i6B)**: For remote control capability.
- **PCA9685**: Controls servo motors.
- **Voltage and Current Sensors**: Monitors power levels.
- **Ultrasonic Sensors**: For object detection.
- **OLED Display**: For real-time feedback display.
- **Relay Module (KY-019)**: To control high-power components.
- **IMU (MPU6050)**: For motion tracking.

The design also anticipates future additions, like an **ESP32-CAM** module, but currently, the appropriate pinouts are NOT included.

### Installation Instructions

- There are multiple ways of approaching the PCBs components, one is two use female pin headers, which lets you easily attach/detach components. The other method is not using female pins, and directly soldering the components to the board.

1. **Soldering Female Pin Headers**: Begin by soldering female pin headers to the PCB. There are two way sThis setup enables you to plug in each component rather than soldering them directly, making it easier to swap out or troubleshoot components.

2. **Mounting the ESP32**: Insert the ESP32 Dev Kit into the designated header pins on the PCB. This board will serve as the main control unit, connecting to other components through the pin headers.

3. **Connecting the PCA9685 Servo Driver**: Insert the PCA9685 module into the specific header on the PCB. This module controls the servos, allowing precise movement of the robot's legs.

4. **Adding Sensors**:
   - **Voltage and Current Sensors**: These sensors plug into their designated slots and help monitor power usage, which is especially useful for managing battery life.
   - **Ultrasonic Sensors**: These can be added in the front of the robot to help detect obstacles and avoid collisions.

5. **Connecting the RC Receiver (FS-i6B)**: The iBus receiver plugs into the board and allows remote control of the robot through the FS-i6B transmitter. This receiver supports multiple channels, giving you control over various functions of the robot dog.

6. **OLED Display and Relay Module**:
   - **OLED Display**: Plug in the OLED to display data like battery voltage, current action state, and other information.
   - **Relay Module (KY-019)**: The relay module slot is ready to handle higher power components safely.
   
### Mounting Component Photos
![SpotMicroESP32](https://github.com/Blacksheep909/SpotMicroESP32/blob/master/electronics/Images/pcbassemble.jpg)
### Future Expansion

The PCB has additional pinouts, including one for an ESP32-CAM module, which can be used for streaming video or advanced vision processing. This slot is not yet populated, but the design allows for easy addition in the future, with straightforward integration into the control system.

### Example Images

Here are images of the board and setup to help guide you through the assembly:

1. **Robot Dog’s Internal Setup**:
   ![SpotMicroESP32](https://github.com/Blacksheep909/SpotMicroESP32/blob/master/electronics/Images/finishedpcb.jpg)
   ![SpotMicroESP32](https://github.com/Blacksheep909/SpotMicroESP32/blob/master/electronics/Images/finishedwideangle.jpg)
   - This image shows the internal layout of the robot, with components neatly arranged on the PCB template. The wiring is "organized" so that the top cover will fit on.
   - You may notice an extra switch for the FS-i6B Reciever for power -this is no longer neccesary, as the code now has a way of disabling noise from the reciever when uploading new code.
3. **PCB Design**:
   ![SpotMicroESP32](https://github.com/Blacksheep909/SpotMicroESP32/blob/master/electronics/Images/Screenshot%202024-11-11%20002821.png)
   
   - This shows the layout of the PCB with labeled areas for each component. Follow these labels to install each part correctly.

5. **Wiring Schematic**:
   ![SpotMicroESP32](https://github.com/Blacksheep909/SpotMicroESP32/blob/master/electronics/Images/image.png)
   - The schematic provides a complete wiring overview, detailing connections between the ESP32, sensors, motor drivers, and other peripherals.

   ## This schematic is updated from the original schematic as two of the I2C were moved to accomodate the ESP32 DevKitC V4. 


### SERVO DRIVER - PCA9685 ###

Manufacturer Homepage: https://www.nxp.com/products/power-management/lighting-driver-and-controller-ics/ic-led-controllers/16-channel-12-bit-pwm-fm-plus-ic-bus-led-controller:PCA9685
Datasheet: https://www.nxp.com/docs/en/data-sheet/PCA9685.pdf

### 0,96" OLED - SSD1306 ###

Manufacturer Homepage: https://www.solomon-systech.com/en/product/advanced-display/oled-display-driver-ic/ssd1306/
Datasheet: https://cdn-shop.adafruit.com/datasheets/SSD1306.pdf
