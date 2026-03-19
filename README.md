# ESP32 Bluetooth Jammer
### 📌 Here you can see how I implemented a ESP32-WROOM-32 as the main component for a Bluetooth Jammer.

<p align="center">
<img width="300" height="500" alt="image" src="https://github.com/user-attachments/assets/f06bab14-9d3d-45f5-8d8d-57611350fd09" />
</p>


---

### ⚠️ ***Legal Information:*** Este proyecto solo tiene fines educativos. No promueve el uso ilegal e indebido. Se deben tener precauciones de seguridad.

---

### 🛒 Things we need
First, we need the following components to carry out the project:
- `ESP32-WROOM-32` (de 38 pines o de 30 pines) or `ESP32-WROOM-32U` (este ultimo debera tener incorporado su antena propia)
- `USB Cable` or `Litium Battery` [optional], for the power of the ESP32
- `2 x nrf24l01 + anthena` (this black model recomended, existen otros)
- `Jumpers wire` or `tin` [optional], for connections
- `Protoboard` (for testing in first place) or `PCB perforda` (si queremos una implementacion final y portabilidad) [optional]
- `Una PC`para cargar el firmware y flasheo
- `0.9 inch Oled screen` [optional]
- `5 buttons` [optional]
- `Led Monitor` [optional]

---

# 🔎 Step by Step
### 1. 📟 ESP32 Drivers
En primer lugar, es escencial que nuestra PC pueda reconocer a nuestra ESP32 en sus puertos de I/O. 
- Para ello, descargamos el archivo con el siguiente nombre `CP210x Universal Windows Driver` del siguiente link: https://www.silabs.com/software-and-tools/usb-to-uart-bridge-vcp-drivers?tab=downloads
- Luego, debemos descomprimir la carpeta que nos aparacera como descarga
- Una vez hecho lo anterior, conectamos nuestra `ESP32` y nos iremos a `Device Manager`, y haremos click derecho en nuestro equipo principal (PC, de donde derivan todas las demas listas de dispositivos conectados), siguiente a ello, le damos click en `Add drivers`
-  En esta opcion, apretaremos en los tres puntitos, y aqui deberemos de buscar la ubicacion de la carpeta descomprimida que hemos descargado del link proporcionado
-  Nos tendra que aparecer que los drivers se añadieron correctamente, y para confirmar, nuestra ESP32 debera salir en las listas desplegables `Other devices` o en `Ports (COM & LPT)`, junto al puerto que le asigno nuestra PC

### 2. ⚖️ Existen 2 versiones del proyecto, ¿cual vas a elegir?

- 1️⃣ ***Proyecto completo*** --> Incluye menu de seleccion (navegable con botones que deberan ir colocados en la PCB) de Jamming para diferentes objetivos (Vulnerabilidades Iphone, Analizador de Señales, Camaras, entre otras), un led indicador de accion (indica cuando el dispositivo esta realizando una accion jamming), tambien una mayor portabilidad dado que tiene una bateria de litio incorporada, y una PCB, lugar en donde iran ensamblados todos los componentes del dispositivo.

- 2️⃣ ***Proyecto básico*** --> Incluye un uso de pocos materiales para su implementacion. No tiene menu de seleccion de objetivos, por lo que al activarse, afecta a toda la frecuencia de 2.4 GHz en su alcance. Puede ser un proyecto fijo (si se aplica en protoboard + PC) o de portabilidad (por si queremos realizar este mismo proyecto en una PCB + bateria portatil; sin embargo, aqui ya se tardaria mas tiempo debido a las soldaduras y conexiones que hay que hacer para la PCB, a diferencia de solo conectar cables en una protoboard). Como dato extra, si se desea un dispositivo BlueJammer, el mas pequeño posible, el dispositivo del `proyecto de rapida implementacion portatil` es la mejor opcion, ya que es mucho mas chico que el del `proyecto completo` (debido a que contiene pantalla, botones, etc)

### 3. 📜 Una vez elegida la version, ¿que necesitamos para empezar a construir nuestro BlueJammer en cada caso?

- 1️⃣ ***Proyecto completo***

- 2️⃣ ***Proyecto basico***

### 4. 🛠️ Flash & Firmware

En esta parte tenemos dos paginas web que se encargaran del flasheo y firmware de la placa, es decir, aplicaran el codigo necesario para que el ESP32 ejecute las acciones jamming.

- 1️⃣ Para la version *Proyecto completo*: 
https://mega.nz/folder/OQpDnLgY#gKpLGsnu_np7O00hVTvWxg

- 2️⃣ Para la version *Proyecto básico*:
https://smoochiee.github.io/Bluetooth-jammer-esp32/flash1

### 5. ⛓️‍💥 Connections
👉 ***En esta parte es donde debemos prestar muchisima atencion***
- Primero, debemos verificar la cantidad de pines y el modelo de nuestras placas (ESP32 y nrf24L01)
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


- La siguiente imagen describe el pinmap de las placas nrf24L01 in its black models (nosotros en este caso, usaremos el modelo de abajo, el nrf24L01 + PA/LNA)
      <p align="center">
      <img width="760" height="600" alt="image" src="https://github.com/user-attachments/assets/c7a51ea7-fc47-4d03-b2b8-3a622ed1e1b9" />
      </p>

- 👉 Una vez establecidos los pines y los modelos de las placas a utilizar, vamos a proceder con las conexiones, segun el proyecto que hayamos elegido:
   - 1️⃣ Para la version *Proyecto completo*:
      - 📛 Serial Peripheral Interface of ESP32 (pines para las placas de antena, y para cualquier version de los ESP32)

        &nbsp;&nbsp; --> HSPI (Generalmente se usa como bus SPI principal de alta velocidad)
        
      | Pines nrf24L01 (1 de 2 placa) | Pin ESP32 |
      | :--- | :---: |
      | **MOSI** | Au | 
      | **MISO** | So |
      | **SCK** | Au |
      | **CE** | Au |
      | **CS o CNS** | Au |
      | **VCC** | Au |
      | **GND** | Au |
     
     &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; --> VSPI (Segundo bus independiente, ideal para separar dispositivos y evitar conflictos de velocidad)
  


      | Pines nrf24L01 (2 de 2 placa) | Pin ESP32 |
      | :--- | :---: |
      | **MOSI** | Au | 
      | **MISO** | So |
      | **SCK** | Au |
      | **CE** | Au |
      | **CS o CNS** | Au |
      | **VCC** | Au |
      | **GND** | Au |

     - 📛 Oled (pines para la pantalla OLED donde veremos el menu de opciones)

      | Pines Pantalla Oled | Pin ESP32 |
      | :--- | :---: |
      | **Boton 1** | Au | 
      | **Boton 2** | So |
      | **Boton 3** | Au |
      | **Boton 4** | Au |
      | **Boton 5** | Au |

     - 📛 Led activador (pines para el led indicador de activacion jamming)

      | Pines Led Activador | Pin ESP32 |
      | :--- | :---: |
      | **Boton 1** | Au | 
      | **Boton 2** | So |
      | **Boton 3** | Au |
      | **Boton 4** | Au |
      | **Boton 5** | Au |
    
     - 📛 Buttons (pines para el uso de los botones)
    
      | Pines Botones | Pin ESP32 |
      | :--- | :---: |
      | **Boton 1** | Au | 
      | **Boton 2** | So |
      | **Boton 3** | Au |
      | **Boton 4** | Au |
      | **Boton 5** | Au |
     
   - 2️⃣ Para la version *Proyecto básico*:
      - 📛 Serial Peripheral Interface of ESP32 (pines para las placas de antena, y para cualquier version de los ESP32)
      
        &nbsp;&nbsp; --> HSPI (Generalmente se usa como bus SPI principal de alta velocidad)
        
      | Pines nrf24L01 (1 de 2 placa) | Pin ESP32 |
      | :--- | :---: |
      | **MOSI** | Au | 
      | **MISO** | So |
      | **SCK** | Au |
      | **CE** | Au |
      | **CS o CNS** | Au |
      | **VCC** | Au |
      | **GND** | Au |
     
     &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; --> VSPI (Segundo bus independiente, ideal para separar dispositivos y evitar conflictos de velocidad)
  


      | Pines nrf24L01 (2 de 2 placa) | Pin ESP32 |
      | :--- | :---: |
      | **MOSI** | Au | 
      | **MISO** | So |
      | **SCK** | Au |
      | **CE** | Au |
      | **CS o CNS** | Au |
      | **VCC** | Au |
      | **GND** | Au |
