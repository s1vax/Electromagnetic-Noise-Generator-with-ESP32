# "BlueJammer" Electromagnetic Noise Generator
### 📌 Here you can see how an ESP32 could be implemented as the main component of a signal generator for protocol resilience testing.

<p align="center">
<img width="300" height="500" alt="image" src="https://github.com/user-attachments/assets/f06bab14-9d3d-45f5-8d8d-57611350fd09" />
</p>


---

### ⚠️ ***Legal Information:*** This project is for educational purposes only, focusing on key topics such as protocol resilience, signal-to-noise ratio (SNR) analysis, and cybersecurity awareness, among others. It does not promote its illegal or improper use. Security precautions should be taken.

⚖️ Disclaimer and Terms of Use (Legal Disclaimer)

This project, technically named "Signal Generator for Resilience Testing in 2.4 GHz Protocols," has been developed for strictly academic, security auditing, and technology awareness purposes.

- ***Purpose***: The main objective is to study the Signal-to-Noise Ratio (SNR), the robustness of the radio spectrum, and the analysis of protocol coexistence (Bluetooth/Wi-Fi).

- ***Regulatory Compliance***: Users are reminded that in the Republic of Argentina, the use of the radio spectrum is regulated by ENACOM and Laws 19.798 and 27.078. Deliberate interference with third-party communications is an activity that may constitute a crime under Article 197 of the Argentine Penal Code.

- ***User Responsibility***: The author of this repository is not responsible for the misuse, illegal, or negligent use of the information or hardware described herein. It is the end user's sole responsibility to ensure that any testing is performed in a controlled environment (such as a Faraday cage) and without affecting other devices or networks.

- ***Non-Commercial Use***: This content is open source and its use for the manufacture or sale of devices intended for the unlawful interference of signals is not authorized.
  
---

### ❓ How it works?

---

### 🛡️ Mitigation and Resilience Strategies (Blue Teaming)
This project can help engineers understand how to protect their devices against interference by using more robust Frequency Hopping Switches (FHSS).

Its objective is also to identify weaknesses in wireless protocols in order to implement robust defenses. The following details the technical measures to mitigate susceptibility to interference in the 2.4 GHz band:

- 📌 ***Implementation of Adaptive Frequency Hopping (AFH)***
   - Modern Bluetooth uses AFH to "jump" between 79 channels. An effective mitigation strategy is to configure devices to:
      - ***Identification of Noisy Channels:*** Optimize the algorithms for detecting affected channels to dynamically exclude them from the hopping sequence.
      - ***Reduction of Hop Intervals:*** Increase the frequency switching speed to minimize exposure time on an interfered channel.
      
- 📌 ***Transition to the 5 GHz / 6 GHz Band (Wi-Fi 6E/7)***
   - Most inexpensive hardware-based noise generators (such as the ESP32 + nRF24L01) are physically limited to the 2.4 GHz band.
      - ***Spectrum Migration:*** Moving critical services (video surveillance, sensitive data communication) to the 5 GHz or 6 GHz bands drastically reduces the attack area of ​​low-complexity devices.

- 📌 ***Client-Side Hardening (Device Hardening)***
   - Use of Robust Encryption Protocols: Although interference affects the physical layer (OSI Layer 1), the use of WPA3 in Wi-Fi helps prevent deauthentication attacks that often accompany electromagnetic noise.
      - ***Physical Shielding (Shielding):*** In critical industrial environments, the use of conductive paints or partial Faraday meshes can protect receivers from unwanted external interference.

- 📌 ***Spectrum Monitoring (Spectrum Analysis)***
   - Implement wireless intrusion detection systems (WIDS) that alert when the noise floor rises abnormally.
      - ***DoS Alerts:*** Configure network systems to detect radio frequency denial-of-service (DoS) patterns and activate contingency protocols (such as automatic switching to a backup wired network).
        
---

### 🛒 Components that can be implemented in this device
Some of these following components were used to carry out the project:
- `ESP32-WROOM-32` ( 38 pins or 30 pins) or `ESP32-WROOM-32U` (the latter must have its own built-in antenna)
- `USB Cable` or `Battery output 3.3 V (lithium or a portable one)` (for the power of the ESP32) [optional]
- `x2 nrf24l01 + Anthena` (this black model recomended, there are others)
- `Jumpers wire` or `Tin` (for connections) [optional] 
- `Protoboard` (for testing in first place) or `Perforated PCB` (if we want a final implementation and portability) [optional]
- `PC` (for loading the firmware, flashing, and if we want to use it to power the ESP32)
- `0.9 inch (or 128x64 px) Oled screen` [optional]
- `x5 buttons` [optional]
- `Leds Switch Module Ws2812 Rgb` [optional]
- `TP4056 USB-C Battery Charger Module` (to charge the battery) [optional] 

---

# 🔎 Step by Step of the process
### 1. 📟 ESP32 Drivers
First, it is essential that a PC can recognize the ESP32 on its I/O ports. 
- To do this, download the file named `CP210x Universal Windows Driver` from the following link: https://www.silabs.com/software-and-tools/usb-to-uart-bridge-vcp-drivers?tab=downloads
- Then, extract the downloaded folder.
- Once you have done this, connect the `ESP32`. Next, go to `Device Manager` (the Windows icon), right-click on the main computer (PC, from which all other connected device lists are derived), and then click on `Add drivers`.
- In this option, click on the three dots, and then locate the extracted folder you downloaded from the provided link.
- You should see a message indicating that the drivers were added correctly. To confirm, the ESP32 should appear in the `Other devices` or `Ports (COM & LPT)`, next to the port that our PC assigns to it

### 2. 🎏 There are 2 known versions of the project

- 1️⃣ ***Complete Project*** --> Includes a selection menu (navigable with buttons that must be placed on the PCB) for Jamming for different objectives (Saturation tests in 802.11 protocols, Signal Analyzer, Interference analysis in IoT devices, among others), an action indicator LED (indicates when the device is performing a jamming action), also greater portability since it has a built-in lithium battery, and a PCB, where all the components of the device will be assembled.

- 2️⃣ ***Basic Project*** --> This project requires minimal materials for implementation. It lacks a target selection menu, so when activated, it affects the entire 2.4 GHz frequency within its range. It can be a fixed project (if implemented on a breadboard and PC) or a portable project (if you want to implement the same project on a PCB and portable battery; however, this will take longer due to the soldering and connections required for the PCB, unlike simply connecting wires on a breadboard). As an extra note, if you want the smallest possible BlueJammer device, the "portable quick-implementation project" device is the best option, as it is much smaller than the "complete project" device (because it includes a screen, buttons, etc.).

### 3. 📜 Components for the construction of the project, according to the version:

- 1️⃣ ***Complete Project***
    - `0.9 inch (or 128x64 px) Oled screen`
    - `x5 Buttons`
    - `Leds Switch Module Ws2812 Rgb`
    - `Tin & Solder`
    - `Perforated PCB (5x7 cm)`
    - `ESP32 (Models below)`
    - `x2 nrf24L01 + Anthena`
    - `Battery output 3.3 V or 3.7 V (lithium or a portable one)`
    - `TP4056 USB-C Battery Charger Module` (to charge the lithium battery)
    - `PC & USB cable` (to load the firmware and flash)
    - For testing --> `Protoboard` & `Jump Wires`


- 2️⃣ ***Basic Project***
    - `x2 nrf24L01 + Anthena`
    - `ESP32 (Models below)`
    - `Protoboard`
    - `Jump Wires`
    - `PC & USB cable` (for loading the firmware, flashing, and if we want to use it to power the ESP32)
    - `Battery output 3.3 V or 3.7 V (lithium or a portable one)` [optional]

### 4. 🛠️ Flash & Firmware

In this section there are two websites that handle the flashing and firmware of the board, that is, those that apply the necessary code for the ESP32 to perform the jamming actions.

- 1️⃣ For the *Complete Project* version:
https://mega.nz/folder/OQpDnLgY#gKpLGsnu_np7O00hVTvWxg

- 2️⃣ For the *Basic Project* version:
https://smoochiee.github.io/Bluetooth-jammer-esp32/flash1

### 5. ⛓️‍💥 Connections

- First, you must verify the number of pins and the model of the boards (ESP32 and nrf24L01)
- The following images describe the pinmap of the most common ESP32 boards:
   - *ESP32-WROOM-32 (38 Pins)*
     <p align="center">
     <img width="1077" height="521" alt="image" src="https://github.com/user-attachments/assets/7334332b-b5f3-4cb0-bdd5-9baee315d54c" />
     </p>

   - *ESP32-WROOM-32 (30 Pins)*
     <p align="center">
     <img width="900" height="600" alt="image" src="https://github.com/user-attachments/assets/34bf288e-bf40-4375-a491-68d3510262a8" />
     </p>
     
   - *ESP32-WROOM-32U (Removable antenna & 30 pins)*
     <p align="center">
     <img width="700" height="500" alt="image" src="https://github.com/user-attachments/assets/da56d36e-db77-4661-87b9-6b2a6c9d3a2b" />
     </p>


- The following image describes the pinmap of the nrf24L01 boards in their black models (usually the nrf24L01 + PA/LNA model is chosen)
      <p align="center">
      <img width="760" height="600" alt="image" src="https://github.com/user-attachments/assets/c7a51ea7-fc47-4d03-b2b8-3a622ed1e1b9" />
      </p>

- 👉 Once the pins and board models to be used have been established, the connections are made, according to the project version:
   - 1️⃣ For the *Complete Project* version
      - 📛 ***Serial Peripheral Interface*** of ESP32 (pins for antenna boards, and for any version of the ESP32)

        &nbsp;&nbsp; --> ***HSPI*** (it is generally used as the main high-speed SPI bus)
        
      | nrf24L01 (1 of 2) pins | ESP32 pins |
      | :--- | :---: |
      | **MOSI** | GPIO 13 | 
      | **MISO** | GPIO 12 |
      | **SCK** | GPIO 14 |
      | **CE** | GPIO 16 |
      | **CS o CNS** | GPIO 15 |
      | **VCC** | 3.3 V |
      | **GND** | GND |
     
     &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; --> ***VSPI*** (second independent bus, ideal for separating devices and avoiding speed conflicts)
  


      | nrf24L01 (2 of 2) pins | ESP32 pins |
      | :--- | :---: |
      | **MOSI** | GPIO 23 | 
      | **MISO** | GPIO 19 |
      | **SCK** | GPIO 18 |
      | **CE** | GPIO 22 |
      | **CS o CNS** | GPIO 21 |
      | **VCC** | 3.3 V |
      | **GND** | GND |

     - 📛 ***0.9 inch (or 128x64 px) Oled screen*** (pins for the OLED screen where we will see the options menu)

      | Oled screen pins| ESP32 pins |
      | :--- | :---: |
      | **SCL** | GPIO Au | 
      | **SCA** | GPIO So |
      | **Boton 3** | GPIO Au |
      | **VCC** | 3.3 V |
      | **GND** | GND |

     - 📛 ***Leds Switch Module Ws2812 Rgb*** (pins for the jamming activation indicator LED)

      | Leds Switch Module pins | ESP32 pins |
      | :--- | :---: |
      | **Button 1** | GPIO Au | 
      | **Button 2** | GPIO So |
      | **Button 3** | GPIO Au |
      | **Button 4** | GPIO Au |
    
     - 📛 ***Buttons*** (pins for using the buttons)
    
      | Buttons pins | ESP32 pins |
      | :--- | :---: |
      | **Button 1** | GPIO Au | 
      | **Button 2** | GPIO So |
      | **Button 3** | GPIO Au |
      | **Button 4** | GPIO Au |
      | **Button 5** | GPIO Au |

     - 📛 ***TP4056 USB-C Battery Charger Module*** (pins for the lithium battery USB charger)
    
      | Battery Charger Module pins | ESP32 pins |
      | :--- | :---: |
      | **Button 1** | GPIO Au | 
      | **Button 2** | GPIO So |
      | **Button 3** | GPIO Au |
      | **Button 4** | GPIO Au |
      | **Button 5** | GPIO Au |

     
   - 2️⃣ For the *Basic Project* version:
      - 📛 ***Serial Peripheral Interface*** of ESP32 (pins for antenna boards, and for any version of the ESP32)
      
        &nbsp;&nbsp; --> ***HSPI*** (it is generally used as the main high-speed SPI bus)
        
      | nrf24L01 (1 of 2) pins | ESP32 pins |
      | :--- | :---: |
      | **MOSI** | GPIO 13 | 
      | **MISO** | GPIO 12 |
      | **SCK** | GPIO 14 |
      | **CE** | GPIO 16 |
      | **CS o CNS** | GPIO 15 |
      | **VCC** | 3.3 V |
      | **GND** | GND |
     
     &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; --> ***VSPI*** (second independent bus, ideal for separating devices and avoiding speed conflicts)
  


      | nrf24L01 (2 of 2) pins | ESP32 pins |
      | :--- | :---: |
      | **MOSI** | GPIO 23 | 
      | **MISO** | GPIO 19 |
      | **SCK** | GPIO 18 |
      | **CE** | GPIO 22 |
      | **CS o CNS** | GPIO 21 |
      | **VCC** | 3.3 V |
      | **GND** | GND |
