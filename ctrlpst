//D13       Button pin
//3.3V      Connected to the other leg of the button

#include <BleKeyboard.h>
//Set the name of the bluetooth keyboard (that shows up in the bluetooth menu of your device)
BleKeyboard bleKeyboard("ESP_KEYBOARD");

const int buttonPin = 13;
//Set the old button state to be LOW/false; which means not pressed
boolean oldPinState = LOW;

void setup() {
  //Start the Serial communication (with the computer at 115200 bits per second)
  Serial.begin(115200);
  //Send this message to the computer
  Serial.println("Starting BLE work!");
  //Begin the BLE keyboard/start advertising the keyboard (so phones can find it)
  bleKeyboard.begin();
  //Make the button pin an INPUT_PULLDOWN pin, which means that it is normally LOW, untill it is pressed/ connected to the 3.3V
  pinMode(buttonPin, INPUT_PULLDOWN);
}

void loop() {

  if (bleKeyboard.isConnected()) {
    //if the keyboard is connected to a device
    if (digitalRead(buttonPin) == HIGH) {
      //If the button pin is pressed (since it is pulled down, it is pressed when it is high)
      if (oldPinState == LOW) {
        //if the old Pin state was LOW and the button pin is HIGH than...
        //send the spacebar
        //bleKeyboard.print(" ");
        bleKeyboard.press(KEY_LEFT_CTRL);
        bleKeyboard.press('v');
        delay(100);
        bleKeyboard.releaseAll();
      }
      oldPinState = HIGH;
    } else {
      oldPinState = LOW;
    }
  }
  delay(10);
}
