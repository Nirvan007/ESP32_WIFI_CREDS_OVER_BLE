Transfer Wi-Fi credentials over BLE and connect to Wi-Fi using ESP32 Devkit V1 <a name="TOP"></a>
===================

## Table of Contents
* [Task Details](#Task-Details)
* [Hardware Components Used](#Hardware-Components-Used)
* [Tools Used](#Tools-Used)
* [Microcontroller Interfacing](#Microcontroller-Interfacing)
* [Firmware](#Firmware)
* [Issues Faced and Resolution](#Issues-Faced-and-Resolution)
* [Outputs](#Outputs)
* [nRF Connect Application interface](#nRF-Connect-Application-interface)
* [References](#References)

## Task Details
Transfer Wi-Fi credentials over Bluetooth and connect to Wifi. (Use a Smartphone to send Wi-Fi credentials)

## Hardware Components Used
1. Espressif System's ESP32 Devkit V1 development board
2. USB to MicroUSB cable
3. Breadboard

## Tools Used
### Arduino IDE 
Arduino Integrated Development Environment or Arduino Software (IDE) contains a text editor for writing code, a message area, a text console, a toolbar with buttons for common functions and a series of menus. It connects to the Arduino hardware to upload programs and communicate with them. 
* For more details refer: <https://www.arduino.cc/en/software>

## Microcontroller Interfacing
* Used BLE protocol for Connectivity with the nRF Connect Mobile Application.
* Used Wi-Fi protocol to connect the microcontroller to the WLAN Network:

## Firmware
### Link (Check the link below or directly download the .ino file or Word document that has the raw code)
- https://github.com/Nirvan007/ESP32_WIFI_CREDS_OVER_BLE/blob/main/Firmware/Nineti_Assignment_BLE_WiFi_Creds/Nineti_Assignment_BLE_WiFi_Creds.ino

## Issues Faced and Resolution
### Space problem in the ESP32 Devkit V1 Board
![Screenshot_1](https://github.com/user-attachments/assets/bcd0a14f-14e9-4dd7-8fc5-0aafd63c3f00)

### Approach 1: Changed the board type to ESP32 Dev Module (As both could be used for uploading the code, i.e., they have the same ESP32-WROOM Chip)
* Result = Same error.
* Comment = There was the same amount of space in both development boards (Same program and flash memory).
![Screenshot_8](https://github.com/user-attachments/assets/5fb3c90a-8aa4-493c-becc-6f24580831dc)

### Approach 2: Changed the board type to ESP32 Dev Module and switched the "Partition Scheme" setting in tools to "Huge APP (3MB No OTA/1MB SPIFFS)".
* Result = This resolved the compilation error and uploaded properly onto the board successfully.
* Comment = There is a lot of space available in the board memory, but has different default partitions preset which can be changed as per use case.
![Screenshot_2](https://github.com/user-attachments/assets/99f7807d-d574-436b-8ba3-5fe99e3fbbba)

## Outputs
## Serial Monitor messages
![Screenshot_3](https://github.com/user-attachments/assets/9704d1b7-4945-41f2-ad96-a5dc8219da4d)
![Screenshot_4](https://github.com/user-attachments/assets/514afd4b-771e-4b37-a7a3-6aecb7170fb2)
![Screenshot_5](https://github.com/user-attachments/assets/55742ceb-1ef5-4c25-9ab6-dc1ffa9568d8)
![Screenshot_6](https://github.com/user-attachments/assets/27c45227-bb99-4631-bc91-ba13568e4d3f)

## nRF Connect Application interface
### Connecting to the ESP32 Board
![Screenshot_20240712-052603](https://github.com/user-attachments/assets/045dafbd-c4cf-4255-81c5-8026471fc126)

### Opening the User-Created Unknown Service
![Screenshot_20240712-052617](https://github.com/user-attachments/assets/33c132cd-11ad-414c-9892-418ca17a4e06)

### Writing to the board by using the "Upward Arrow" in the characteristic which denotes the "Write" command
![Screenshot_20240712-053455](https://github.com/user-attachments/assets/edffbb2c-25f0-4df2-9983-9532aa94e8f4)

### Setting the "Write value" to "TEXT(UTF-8)" to send a String vlaue to the board
![Screenshot_20240712-053503](https://github.com/user-attachments/assets/835e1f2f-3c01-407b-9990-abbf0a7d298e)

### Type the Wi-Fi SSID and Password in the format: "SSID,PASS" and click send
![Screenshot_20240712-053522](https://github.com/user-attachments/assets/0d3794d4-bfdd-46ac-a40d-6ccc9cf352cd)

### Value is being written
![Screenshot_20240712-053753](https://github.com/user-attachments/assets/c0c3e110-1d31-489f-a49a-dce1825b3957)

### The device receives the SSID and Password, then it has to be reset, so that it can turn OFF the BLE and connect to the provided Wi-Fi SSID
![Screenshot_20240712-053821](https://github.com/user-attachments/assets/7bf729da-eead-4465-93ca-91a656a5dd51)
![Screenshot_20240712-053829](https://github.com/user-attachments/assets/8502e512-faf8-423d-a604-d31fb99ad1d4)

## References
 - [1] https://randomnerdtutorials.com/esp32-wi-fi-provisioning-ble-arduino/#:~:text=You%20connect%20to%20the%20ESP32,Fi%2Drelated%20tasks%20it%20needs
 - [2] https://github.com/mironal/iOS-Bluetooth-ESP32-WiFi/blob/master/Arduino/BLE_WiFi_ESP32.ino
 - [3] https://github.com/EspressifApp/EspBlufiForAndroid/releases
 - [4] https://github.com/0015/ThatProject/tree/master/Esp32_wifi_ssid_pw_via_ble/Esp32_WIFI_BLE
 - [5] https://arduino.stackexchange.com/questions/90925/text-section-exceeds-available-space-in-board
 - [6] https://esp32.com/viewtopic.php?t=5292
