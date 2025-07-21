#include <SoftwareSerial.h>

// Bluetooth Module Pins
const int bluetoothTx = 2;
const int bluetoothRx = 3;

// Relay Pin
const int relayPin = 13;

SoftwareSerial bluetoothSerial(bluetoothTx, bluetoothRx);

void setup() {
  pinMode(relayPin, OUTPUT);
  bluetoothSerial.begin(9600);
}

void loop() {
  if (bluetoothSerial.available() > 0) {
    char command = bluetoothSerial.read();
    if (command == '1') {
      digitalWrite(relayPin, HIGH); // Turn ON appliance
    } else if (command == '0') {
      digitalWrite(relayPin, LOW); // Turn OFF appliance
    }
  }
  delay(100);
}
