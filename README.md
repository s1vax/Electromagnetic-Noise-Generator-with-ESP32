# Generador de ruido electromagnético "BlueJammer"
### 📌 Here you can see how an ESP32 could be implemented as the main component of a signal generator for protocol resilience testing.

<p align="center">
<img width="300" height="500" alt="image" src="https://github.com/user-attachments/assets/f06bab14-9d3d-45f5-8d8d-57611350fd09" />
</p>


---

### ⚠️ ***Legal Information:*** Este proyecto solo tiene fines educativos, observando las principales tematicas: Estudio de la Resiliencia de Protocolos, Análisis del Ratio Señal-Ruido (SNR), Concienciación en Ciberseguridad, entre otros. No promueve el uso ilegal e indebido del mismo. Se deben tener precauciones de seguridad.

⚖️ Descargo de Responsabilidad y Términos de Uso (Legal Disclaimer)
Uso Exclusivo para Investigación y Educación

Este proyecto, denominado de forma técnica como "Generador de Señales para Pruebas de Resiliencia en Protocolos de 2.4 GHz", ha sido desarrollado con fines estrictamente académicos, de auditoría de seguridad y concienciación tecnológica.

- Finalidad: El objetivo principal es el estudio del Ratio Señal-Ruido (SNR), la robustez del espectro radioeléctrico y el análisis de la coexistencia de protocolos (Bluetooth/Wi-Fi).

- Cumplimiento Normativo: Se recuerda a los usuarios que en la República Argentina, el uso del espectro radioeléctrico está regulado por el ENACOM y las Leyes 19.798 y 27.078. La interferencia deliberada de comunicaciones de terceros es una actividad que puede constituir un delito bajo el Artículo 197 del Código Penal Argentino.

- Responsabilidad del Usuario: El autor de este repositorio no se responsabiliza por el uso indebido, ilegal o negligente de la información o el hardware aquí descritos. Es responsabilidad total del usuario final asegurar que cualquier prueba se realice en un entorno controlado (como una Jaula de Faraday) y sin afectar a dispositivos o redes ajenas.

- No Comercialización: Este contenido es de código abierto y no se autoriza su uso para la fabricación o venta de dispositivos destinados a la interferencia ilícita de señales.

---

### ❓ How it works?


### 🛡️ Mitigacion
Este proyecto ayuda a ingenieros a entender cómo proteger sus dispositivos contra interferencias mediante el uso de saltos de frecuencia (FHSS) más robustos


### 🛒 Components that can be implemented
Somo of these following components were used to carry out the project:
- `ESP32-WROOM-32` (de 38 pines o de 30 pines) or `ESP32-WROOM-32U` (este ultimo debera tener incorporado su antena propia)
- `USB Cable` or `Battery output 3.3 V (litium or a portable one)` (for the power of the ESP32) [optional]
- `x2 nrf24l01 + anthena` (this black model recomended, existen otros)
- `Jumpers wire` or `tin` [optional], for connections
- `Protoboard` (for testing in first place) or `PCB perforda` (si queremos una implementacion final y portabilidad) [optional]
- `PC` (para cargar el firmware, el flasheo, y por si queremos usarla para alimentar a la ESP32)
- `0.9 inch Oled screen` [optional]
- `x5 buttons` [optional]
- `Modulo Control Led` [optional]
- `Modulo cargador de batería USB-c TP4056` (para cargar la bateria) [optional] 

---

# 🔎 Step by Step of the process
### 1. 📟 ESP32 Drivers
En primer lugar, es escencial que una PC pueda reconocer a la ESP32 en sus puertos de I/O. 
- Para ello, se descarga el archivo con el siguiente nombre `CP210x Universal Windows Driver` del siguiente link: https://www.silabs.com/software-and-tools/usb-to-uart-bridge-vcp-drivers?tab=downloads
- Luego, se descomprime la carpeta que aparace como descarga
- Una vez hecho lo anterior, se conecta la `ESP32`, seguido se debe de ir a `Device Manager` en el icono de Windows, y hacer click derecho en el equipo principal (PC, de donde derivan todas las demas listas de dispositivos conectados), siguiente a ello, se da click en `Add drivers`
-  En esta opcion, se apreta en los tres puntitos, y aqui se debe de buscar la ubicacion de la carpeta descomprimida que hemos descargado del link proporcionado
-  Tendra que aparecer que los drivers se añadieron correctamente, y para confirmar, la ESP32 debera salir en las listas desplegables `Other devices` o en `Ports (COM & LPT)`, junto al puerto que le asigno nuestra PC

### 2. ⚖️ Existen 2 versiones del proyecto

- 1️⃣ ***Proyecto completo*** --> Incluye menu de seleccion (navegable con botones que deberan ir colocados en la PCB) de Jamming para diferentes objetivos (Pruebas de saturación en protocolos 802.11, Analizador de Señales, Análisis de interferencia en dispositivos IoT, entre otras), un led indicador de accion (indica cuando el dispositivo esta realizando una accion jamming), tambien una mayor portabilidad dado que tiene una bateria de litio incorporada, y una PCB, lugar en donde iran ensamblados todos los componentes del dispositivo.

- 2️⃣ ***Proyecto básico*** --> Incluye un uso de pocos materiales para su implementacion. No tiene menu de seleccion de objetivos, por lo que al activarse, afecta a toda la frecuencia de 2.4 GHz en su alcance. Puede ser un proyecto fijo (si se aplica en protoboard + PC) o de portabilidad (por si queremos realizar este mismo proyecto en una PCB + bateria portatil; sin embargo, aqui ya se tardaria mas tiempo debido a las soldaduras y conexiones que hay que hacer para la PCB, a diferencia de solo conectar cables en una protoboard). Como dato extra, si se desea un dispositivo BlueJammer, el mas pequeño posible, el dispositivo del `proyecto de rapida implementacion portatil` es la mejor opcion, ya que es mucho mas chico que el del `proyecto completo` (debido a que contiene pantalla, botones, etc)

### 3. 📜 Componentes para la construccion del proyecto, segun la version:

- 1️⃣ ***Proyecto completo***
    - `Oled Screen (128x64 px or 0.9 inches)`
    - `x5 Buttons`
    - `Modulo Control Led`
    - `Tin & Solder`
    - `PCB (5x7 cm)`
    - `ESP32 (Models below)`
    - `x2 nrf24L01 + Antenas`
    - `Battery output 3.3 V or 3.7 V (litium or a portable one)`
    - `Modulo cargador de batería USB-c TP4056` para cargar la bateria de litio
    - `PC & USB cable` para cargar el firmware y el flasheo
    - For testing --> `Protoboard` & `Jump Wires`


- 2️⃣ ***Proyecto basico***
    - `x2 nrf24L01 + Antenas`
    - `ESP32 (Models below)`
    - `Protoboard`
    - `Jump Wires`
    - `PC & USB cable` para cargar el firmware, el flasheo, y por si queremos usarla para alimentar a la ESP32
    - `Battery output 3.3 V or 3.7 V (litium or a portable one)` [optional]

### 4. 🛠️ Flash & Firmware

En esta parte existen dos paginas web que se encargan del flasheo y firmware de la placa, es decir, las que aplican el codigo necesario para que el ESP32 ejecute las acciones jamming.

- 1️⃣ Para la version *Proyecto completo*: 
https://mega.nz/folder/OQpDnLgY#gKpLGsnu_np7O00hVTvWxg

- 2️⃣ Para la version *Proyecto básico*:
https://smoochiee.github.io/Bluetooth-jammer-esp32/flash1

### 5. ⛓️‍💥 Connections

- Primero, se debe verificar la cantidad de pines y el modelo de nuestras placas (ESP32 y nrf24L01)
- Las siguientes imagenes describen el pinmap de las placas ESP32 mas comunes:
   - *ESP32-WROOM-32 (38 Pins)*
     <p align="center">
     <img width="1077" height="521" alt="image" src="https://github.com/user-attachments/assets/7334332b-b5f3-4cb0-bdd5-9baee315d54c" />
     </p>

   - *ESP32-WROOM-32 (30 Pins)*
     <p align="center">
     <img width="900" height="600" alt="image" src="https://github.com/user-attachments/assets/34bf288e-bf40-4375-a491-68d3510262a8" />
     </p>
     
   - *ESP32-WROOM-32U (Antena extraible & 30 Pins)*
     <p align="center">
     <img width="700" height="500" alt="image" src="https://github.com/user-attachments/assets/da56d36e-db77-4661-87b9-6b2a6c9d3a2b" />
     </p>


- La siguiente imagen describe el pinmap de las placas nrf24L01 in its black models (por lo general se opta por el modelo nrf24L01 + PA/LNA)
      <p align="center">
      <img width="760" height="600" alt="image" src="https://github.com/user-attachments/assets/c7a51ea7-fc47-4d03-b2b8-3a622ed1e1b9" />
      </p>

- 👉 Una vez establecidos los pines y los modelos de las placas a utilizar, se procede con las conexiones, segun la version del proyecto:
   - 1️⃣ Para la version *Proyecto completo*:
      - 📛 ***Serial Peripheral Interface*** of ESP32 (pines para las placas de antena, y para cualquier version de los ESP32)

        &nbsp;&nbsp; --> ***HSPI*** (Generalmente se usa como bus SPI principal de alta velocidad)
        
      | Pines nrf24L01 (1 de 2 placa) | Pin ESP32 |
      | :--- | :---: |
      | **MOSI** | Au | 
      | **MISO** | So |
      | **SCK** | Au |
      | **CE** | Au |
      | **CS o CNS** | Au |
      | **VCC** | Au |
      | **GND** | Au |
     
     &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; --> ***VSPI*** (Segundo bus independiente, ideal para separar dispositivos y evitar conflictos de velocidad)
  


      | Pines nrf24L01 (2 de 2 placa) | Pin ESP32 |
      | :--- | :---: |
      | **MOSI** | Au | 
      | **MISO** | So |
      | **SCK** | Au |
      | **CE** | Au |
      | **CS o CNS** | Au |
      | **VCC** | Au |
      | **GND** | Au |

     - 📛 ***Oled Screen*** (pines para la pantalla OLED donde veremos el menu de opciones)

      | Pines Pantalla Oled | Pin ESP32 |
      | :--- | :---: |
      | **Boton 1** | Au | 
      | **Boton 2** | So |
      | **Boton 3** | Au |
      | **Boton 4** | Au |
      | **Boton 5** | Au |

     - 📛 ***Modulo Control Led*** (pines para el led indicador de activacion jamming)

      | Pines Led Activador | Pin ESP32 |
      | :--- | :---: |
      | **Boton 1** | Au | 
      | **Boton 2** | So |
      | **Boton 3** | Au |
      | **Boton 4** | Au |
      | **Boton 5** | Au |
    
     - 📛 ***Buttons*** (pines para el uso de los botones)
    
      | Pines Botones | Pin ESP32 |
      | :--- | :---: |
      | **Boton 1** | Au | 
      | **Boton 2** | So |
      | **Boton 3** | Au |
      | **Boton 4** | Au |
      | **Boton 5** | Au |
     
   - 2️⃣ Para la version *Proyecto básico*:
      - 📛 ***Serial Peripheral Interface*** of ESP32 (pines para las placas de antena, y para cualquier version de los ESP32)
      
        &nbsp;&nbsp; --> ***HSPI*** (Generalmente se usa como bus SPI principal de alta velocidad)
        
      | Pines nrf24L01 (1 de 2 placa) | Pin ESP32 |
      | :--- | :---: |
      | **MOSI** | Au | 
      | **MISO** | So |
      | **SCK** | Au |
      | **CE** | Au |
      | **CS o CNS** | Au |
      | **VCC** | Au |
      | **GND** | Au |
     
     &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; --> ***VSPI*** (Segundo bus independiente, ideal para separar dispositivos y evitar conflictos de velocidad)
  


      | Pines nrf24L01 (2 de 2 placa) | Pin ESP32 |
      | :--- | :---: |
      | **MOSI** | Au | 
      | **MISO** | So |
      | **SCK** | Au |
      | **CE** | Au |
      | **CS o CNS** | Au |
      | **VCC** | Au |
      | **GND** | Au |
