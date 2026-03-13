# ESP32-WROOM-32 Bluetooth Jammer
### 📌 Here you can see how I implemented a ESP32-WROOM-32 as the main component for a Bluetooth Jammer.

<p align="center">
<img width="300" height="500" alt="image" src="https://github.com/user-attachments/assets/f06bab14-9d3d-45f5-8d8d-57611350fd09" />
</p>


---

### ⚠️ ***Legal Information:*** Este proyecto solo tiene fines educativos. No promueve el uso ilegal e indebido.

---

### 🛒 Things we need
First, we need the following components to carry out the project:
- `ESP32-WROOM-32` (de 38 pines) or `ESP32-U` (este ultimo debera tener incorporado su antena propia)
- `USB Cable` or `Litium Battery` [optional], for the power of the ESP32
- `2 x nrf24l01 + anthena`
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

- ***Proyecto completo*** --> Incluye menu de seleccion (navegable con botones) de Jamming y otras opciones (Vulnerabilidades Iphone, Analizador de Señales, entre otras), tambien un led indicador de accion (indica cuando el dispositivo esta realizando una accion jamming) y una mayor portabilidad dado que tiene una bateria de litio, y su tamaño es considerablemente mas pequeño, debido a la personalizacion de la PCB en donde iran ensamblados todos los componentes.

- ***Proyecto de rapida implementacion***

### 3. 📜 Una vez elegida la version, ¿que necesitamos para empezar a construir nuestro BlueJammer en cada caso?

### 4. 🛠️ Flash & Firmware

En esta parte tenemos dos paginas web que se encargaran del flasheo y firmware de la placa, es decir, aplicaran el codigo necesario para que el ESP32 ejecute las acciones jamming.

- Para la version *Proyecto completo*:
- Para la version *Proyecto de rapida implementeacion*:
https://smoochiee.github.io/Bluetooth-jammer-esp32/flash1

### 5. ⛓️‍💥 Connections
👉 ***En esta parte es donde debemos prestar muchisima atencion***
- Debemos verificar la cantidad de pines y el modelo de nuestras placas 
- Las siguientes imagenes describen el pinmap de las placas ESP32 mas comunes:
   - *ESP32-WROOM-32 (38 Pins)*
     <p align="center">
     <img width="1077" height="521" alt="image" src="https://github.com/user-attachments/assets/7334332b-b5f3-4cb0-bdd5-9baee315d54c" />
     </p>

   - *ESP32-WROOM-32 (30 Pins)*
     <p align="center">
     <img width="900" height="600" alt="image" src="https://github.com/user-attachments/assets/34bf288e-bf40-4375-a491-68d3510262a8" />
     </p>

- La siguiente imagen describe el pinmap de las placas nrf24L01 (en sus dos modelos)
      <p align="center">
      <img width="760" height="600" alt="image" src="https://github.com/user-attachments/assets/c7a51ea7-fc47-4d03-b2b8-3a622ed1e1b9" />
      </p>

