# ESP32 BMP180 + ThingSpeak + Carenuity's Solution Builder

This project uses an **ESP32**, a **BMP180 sensor**, and an **OLED display** to collect environmental data (temperature and pressure), display it, and upload it to [ThingSpeak](https://thingspeak.com) every 30 seconds. WiFi and API key configuration is handled using **WiFiManager**, making it user-friendly and reconfigurable without modifying code.

##  Features

- 📡 Connects to WiFi using WiFiManager portal
- 📈 Reads temperature and pressure from BMP180 sensor
- ☁️ Uploads data to ThingSpeak using HTTP POST
- 🖥 Displays readings on an OLED screen (128x64)
- 🔧 No hard-coded credentials – all done via config portal

---

##  Hardware Requirements

- ESP32 Development Board  
- BMP180 Pressure & Temperature Sensor  
- SSD1306 OLED Display (128x64, I2C)  
- Jumper wires  
- Breadboard (optional)

###  Default I2C Pins on ESP32 (can be customized)

| Device     | Pin  | GPIO |
|------------|------|------|
| SDA        | -    | 23   |
| SCL        | -    | 22   |

---

##  Libraries Used

Install the following libraries from the Arduino Library Manager:

- `WiFiManager by tzapu`
- `Adafruit BMP085 Unified`
- `Adafruit GFX Library`
- `Adafruit SSD1306`
- `Wire`
- `WiFi` (built-in with ESP32)

---

##  Getting Started

### 1. Upload the code to your ESP32  
Ensure all libraries are installed and connections are correct.

### 2. Power on the ESP32  
It creates a WiFi hotspot named **`BMP180Config`**.

### 3. Connect to `BMP180Config` using your phone or computer  
You will be redirected to a captive portal.

### 4. Enter the following:
- WiFi SSID and password
- ThingSpeak **Write API Key**  
Then click **Save**.

### 5. ESP32 will reboot and connect to WiFi  
It will start sending sensor data to ThingSpeak every 30 seconds.

---

## 📊 ThingSpeak Configuration

1. Sign up / Log in at [thingspeak.com](https://thingspeak.com)
2. Create a new channel
3. Enable **Field 1** (Temperature), and **Field 2** (Pressure)
4. Copy the **Write API Key**
5. Use this key in the WiFiManager portal when setting up the ESP32

---

##  Sample Output

### Serial Monitor

![image](https://github.com/user-attachments/assets/bb9e9ba7-3ad6-4bc5-b463-e44b2ef8e00b)


### OLED Display

![image](https://github.com/user-attachments/assets/5b1311e5-3560-49ac-a5fb-cfe000e527aa)


---

##  Notes

- If the BMP180 sensor is not detected, the OLED shows “BMP180 not found!” and halts.
- You can modify the `Wire.begin(23, 22)` line to use different I2C pins.
- You can reset the saved WiFi credentials by triggering a WiFiManager reset (e.g., via double reset or button press – not included in this example).

---

## 📃 License

This project is open-source and free to use under the MIT License.

