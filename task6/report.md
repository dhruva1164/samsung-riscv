# **Multi-Mode Counter Using ESP8266 and VSD Board**
### **A Smart Counter Controlled via Blynk Web Dashboard**

---

## **1. Abstract**
The **Multi-Mode Counter** is an innovative project that utilizes an **ESP8266** to control a **VSD Squadron Mini Board (CH32V0xx)** for **binary counting operations**. The counter operates in **four distinct modes**, controlled through the **Blynk Web Dashboard**. The control signals from the ESP8266 determine the counting behavior, which is displayed using **LEDs connected to PC0, PC1, PC2, and PC3**.

### **Key Features:**
- **Remote control via Blynk Web Dashboard**
- **Four counting modes (Up, Down, Ring, BCD)**
- **Integration with ESP8266 for wireless operation**
- **Real-time LED representation of the counter state**

---

## **2. Modes of Operation**
The counter operates in **four different modes** depending on the control inputs **PC5 (D2) & PC6 (D3)**.

| **PC5 (D2)** | **PC6 (D3)** | **Mode**         | **Description** |
|-------------|-------------|----------------|----------------|
| 0           | 0           | **Up Counter**  | Increments from 0000 to 1111 (0-15) |
| 0           | 1           | **Down Counter** | Decrements from 1111 to 0000 (15-0) |
| 1           | 0           | **Ring Counter** | Shifts a single ‘1’ cyclically |
| 1           | 1           | **BCD Counter**  | Counts from 0000 to 1001 (0-9 in BCD) |

---

## **3. Hardware Requirements**
### **Components List**
| **Component**        | **Quantity** |
|----------------------|-------------|
| ESP8266 NodeMCU     | 1           |
| VSD Squadron Mini (CH32V0xx) | 1           |
| LEDs                | 4           |
| Resistors (330Ω)    | 4           |
| Jumper Wires        | As needed   |
| Power Supply (5V)   | 1           |

### **Circuit Connections**
- **ESP8266 to VSD Squadron Mini Board:**
  - **D2 → PC5 (Mode Select 1)**
  - **D3 → PC6 (Mode Select 2)**

- **VSD Board to LEDs (Binary Output):**
  - **PC0 → LED1**
  - **PC1 → LED2**
  - **PC2 → LED3**
  - **PC3 → LED4**

### **Circuit Diagram**
![Circuit Diagram](Circuit_Diagram.png)

---

## **4. Software Implementation**
The software is developed using **Arduino IDE** with support for **ESP8266**. It integrates **Blynk** for web-based control.

### **Code Breakdown**
1. **ESP8266 Reads Mode Selection** (PC5 & PC6)
2. **Updates Counter Based on Mode**
3. **Displays Counter Output on LEDs**
4. **Communicates with Blynk Dashboard**

### **Source Code**
The full source code is in `code/multi_mode_counter.ino`. Here’s a snippet:

```cpp
#define BLYNK_TEMPLATE_ID "TMPL3pYU7nlUx"
#define BLYNK_TEMPLATE_NAME "SmartestHome"
#define BLYNK_AUTH_TOKEN "FRF70BbXEzGb6jINIyQPbFungQP7kiCU"

#include <ESP8266WiFi.h>
#include <BlynkSimpleEsp8266.h>

const int LEDS[] = {D1, D2, D3, D4}; // LEDs at PC0-PC3
const int PC5 = D2;  // Control pin
const int PC6 = D3;  // Control pin

char auth[] = "YOUR_BLYNK_AUTH";  
char ssid[] = "YOUR_WIFI_SSID";  
char pass[] = "YOUR_WIFI_PASS";  

void setup() {
    Serial.begin(115200);
    Blynk.begin(auth, ssid, pass);

    for (int i = 0; i < 4; i++) {
        pinMode(LEDS[i], OUTPUT);
    }
    
    pinMode(PC5, INPUT);
    pinMode(PC6, INPUT);
}

void loop() {
    Blynk.run();
    
    int mode = (digitalRead(PC5) << 1) | digitalRead(PC6);  
    static uint8_t counter = 0;

    switch (mode) {
        case 0b00: counter = (counter + 1) & 0x0F; break;
        case 0b01: counter = (counter - 1) & 0x0F; break;
        case 0b10: counter = (counter == 0) ? 1 : (counter << 1); if (counter > 8) counter = 1; break;
        case 0b11: counter = (counter + 1) % 10; break;
    }

    for (int i = 0; i < 4; i++) {
        digitalWrite(LEDS[i], (counter >> i) & 1);
    }

    delay(500);
}
