# Fire Detection System Using Arduino 🔥

This project implements a simple and effective fire detection system using an Arduino microcontroller and a flame sensor. The system detects fire or flames and triggers an alarm through a buzzer and LED. It is an affordable and easily deployable solution for fire safety in homes, offices, warehouses, and industrial settings.

## 👥 Authors

- Bhushan Dadaji Ahire
- Rucha Jayant Chaudhari

Guided by: Prof. Dr. Tushar Patil

G. H. Raisoni College of Engineering and Management, Jalgaon (Maharashtra)  
Department of Electronics and Telecommunication Engineering

---

## 🔧 Components Required

- Arduino board (e.g., Uno, Nano)
- Flame sensor or MQ-2 smoke sensor
- Buzzer
- LED
- Resistor
- Breadboard and jumper wires
- USB cable for programming
- Optional: LCD display, relay module for fire suppression system

---

## ⚙️ Working Principle

The system operates on the principle of detecting environmental changes indicating the presence of fire:

1. **Sensor Monitoring**  
   - Flame sensor detects infrared light from a flame.  
   - Smoke sensors detect smoke particles.  
   - Temperature sensors detect rapid temperature rise.

2. **Signal Processing**  
   Arduino reads sensor values. If readings cross a set threshold, it identifies a fire condition.

3. **Alarm Activation**  
   Arduino activates a buzzer and LED. Optionally, notifications can be sent via GSM/WiFi modules.

---

## 💻 Arduino Code

Below is the code used for flame detection and triggering the alarm:

```cpp
const int ledpin = 13;
const int flamepin = A2;
const int buzpin = 11;
const int threshold = 200; // Threshold value for flame detection

int flamesensvalue = 0;

void setup() {
  Serial.begin(9600);
  pinMode(ledpin, OUTPUT);
  pinMode(flamepin, INPUT);
  pinMode(buzpin, OUTPUT);
}

void loop() {
  flamesensvalue = analogRead(flamepin);
  if (flamesensvalue <= threshold) {
    digitalWrite(ledpin, HIGH);
    tone(buzpin, 100);
    delay(1000);
  } else {
    digitalWrite(ledpin, LOW);
    noTone(buzpin);
  }
}
