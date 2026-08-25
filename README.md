                                    Mars Rover (Autonamous field  exploration unit)
                                                      By Koray
![image alt](https://github.com/koray9012/Mars-rover/blob/main/16028.jpg?raw=true)
An ESP32-powered all-terrain exploration rover designed to traverse rough terrain, stream live first-person video feed, and transmit telemetry data wirelessly.
You can drive it remotely through a custom browser interface or let it execute autonomous obstacle navigation routines.

## Key Upgrades & Features
  
  FPV Camera Streaming:
  
  • Uses an ESP32-CAM module to stream a live video feed directly to your phone or PC over Wi-Fi so you can pilot it from a true driver's-seat perspective.

  All-Terrain 4WD Mobility:
  
  • Driven by a robust 4-motor chassis powered by an L298N driver, built to handle rough surfaces, carpet, and outdoor dirt paths with ease.

  Wireless ESP-NOW / Wi-Fi Control:
  
  • Connects seamlessly to remote controllers or local networks for responsive, low-latency maneuvering.
  
  Dynamic Operating Modes:
 
  • Exploration Mode: Standard manual driving with live FPV video streaming.
  
  • Telemetry & Debug Mode: Monitors battery voltage and wireless connection strength in real-time.

  Onboard Power Management:
 
  • Powered by a custom 2S 18650 rechargeable battery pack managed by a dedicated BMS, ensuring stable voltage and high efficiency.

## How to use: 

To use it first you need to connect the custom 2S battery pack to the battery connectors and then switch on the master power switch. After you switch it on the ESP32-CAM will boot up and host its own Wi-Fi network. To connect you open your phone or PC Wi-Fi settings, choose the rover's network, type the password, and open your browser. Navigate to the local IP address to access the live video stream and throttle controls.

## Operating Instructions
1. Power On
 
  1. Connect your custom 2S battery pack to the battery connectors.
 
  2. Flip the master power switch to turn on the rover.
 
  3. Wait a few seconds for the ESP32-CAM to initialize its Wi-Fi access point.

2. Connecting Your Device (FPV & Wi-Fi Control)
 
  1. On your phone or computer, open Wi-Fi settings and connect to the rover's access point.
 
  2. Open your browser and enter the designated local IP address to load the video dashboard.
 
  3. Use the on-screen controls to steer while watching the live FPV camera feed.

## Why I made it:

After finishing standard wheeled robots, I wanted to build something with a bit more exploration capability—a true remote-presence rover. I chose the ESP32-CAM so I could get a live video feed streaming directly from the front of the vehicle, making it feel like driving a real planetary exploration probe. 

Just like my other builds, I ditched inefficient 9V batteries for a custom 2S 18650 Li-ion pack protected by a BMS, giving it much better runtime and power delivery. Integrating the camera stream with motor PWM control taught me a lot about managing processor load and bandwidth on a micro-controller without causing lag spikes.

### Wiring & Connections:

Below is the visual schematic diagram for the Mars Rover.

![image](https://github.com/koray9012/Mars-rover/blob/main/%D0%95%D0%BA%D1%80%D0%B0%D0%BD%D0%BD%D0%B0%20%D1%81%D0%BD%D0%B8%D0%BC%D0%BA%D0%B0%202026-08-24%20185107.png?raw=true)

### Pinout Breakdown:

| ESP32-CAM Pin | Component | Connected Pin / Note |
| :--- | :--- | :--- |
| **GPIO 14** | L298N Motor Driver | ENA+ENB (PWM Speed Control) |
| **GPIO 15** | L298N Motor Driver | IN1 (Right Motor) |
| **GPIO 13** | L298N Motor Driver | IN2 (Right Motor) |
| **GPIO 12** | L298N Motor Driver | IN3 (Left Motor) |
| **GPIO 2** | L298N Motor Driver | IN4 (Left Motor) |
| **5V** | L298N Motor Driver | 5V rail for power |
| **GND** | Shared GND of all devices | Shared GND cable |

## Code:

The code can be found in repo: Mars Rover Code

## Bill of materials:

| Item | Quantity | Price (USD) | Link |
| :--- | :--- | :--- | :--- |
| ESP32 38 Pins | 1 | 8.89 USD | https://elimex.bg/product/75823-komplekt-provodnitsi-40-broya-s-konektori-mazhki-zhenski-30sm |
| ESP32-CAM Module | 1 | 7.50 USD | https://www.ardboard.com/index.php?route=product/product&product_id=273&search=cam |
| L298N Motor Driver | 1 | 4.60 USD | https://elimex.bg/product/71197-kit-k2010-drayver-za-postoyannotokovi-motori |
| Car Chasis (4WD) | 1 | 20.93 USD | https://elimex.bg/product/84826-shasi-za-robot-4wd-s-4-motora-i-2-osnovi-kit-za-sglobqvane |
| 18650 Battery | 2 | 5.77 USD x2 = 11.54 USD | https://elimex.bg/product/85664-akumulator-3.7v-3400mah-lc18650-lava |
| Battery holder | 4 | 0.56 USD | https://elimex.bg/product/77722-battery-holder-lc18650 |
| 2S BMS | 1 | 1.52 USD | https://elimex.bg/product/77415-bsmpcm-kontroler-za-zaryada-i-razryada-na-li-ion-paket-2x18650-7-4v-8-4v3a |
| Power Switch | 1 | 0.35 USD | https://elimex.bg/product/44024-switch-smrs101-1-black | 
| Jumper Cables | ~30 | 2.86 USD + 2.27 USD = 5.13 USD | https://elimex.bg/product/75823-komplekt-provodnitsi-40-broya-s-konektori-mazhki-zhenski-30sm https://elimex.bg/product/75823-komplekt-provodnitsi-40-broya-s-konektori-mazhki-zhenski-30sm AND https://elimex.bg/product/74894-komplekt-provodnitsi-40-broya-s-konektori-mazhki-mazhki-20sm |
| Servo motor | 4 | 10.67 USD x4 = 42.68 USD| https://elimex.bg/product/86312-kit-k2263-mg90s-390-mikro-servo-motor-metalni-zubni-kolela | 
| metal gripper | 1 | 16.21 USD | https://elimex.bg/product/87062-mehanichna-shtipka-za-robo-platforma-maqueen | 
| LoRa Module | 1 | 11.15 USD | https://www.ardboard.com/lora-ra-02-433MHz?search=LoRa | 
| LoRa Antenna | 1 | 2.86 USD | https://www.ardboard.com/433mhz-spring-ipex-antenna?search=LoRa | 
| GP-01 Gps tracker | 1 | 12.22 USD | https://www.ardboard.com/index.php?route=product/product&product_id=423&search=gps | 

## Very important: The motors came with the chasis because they are a kit and also the cables arent exact because I cut them up and soldered them to fit the deck cleanly.

## Video for rover demo (https://www.youtube.com/watch?v=xmUQw59Qynk)

## Credits: 

This project uses:

Kicad

Hack Club Macondo 

Btw thank you for the Power Supply Hack Club :)
