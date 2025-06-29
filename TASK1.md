



#include <LiquidCrystal.h>



// LCD pin connections: RS, E, D4, D5, D6, D7

LiquidCrystal lcd(12, 11, 5, 4, 3, 2);



const int buttonPin = 8;

const int ledPin = 9;



int counter = 0;

bool lastButtonState = LOW;

bool currentButtonState = LOW;



void setup() {

&nbsp; lcd.begin(16, 2); // 16 columns and 2 rows

&nbsp; pinMode(buttonPin, INPUT);

&nbsp; pinMode(ledPin, OUTPUT);

&nbsp; 

&nbsp; lcd.print("Count: 0");

&nbsp; digitalWrite(ledPin, LOW);

}



void loop() {

&nbsp; currentButtonState = digitalRead(buttonPin);



&nbsp; // Detect rising edge (LOW to HIGH)

&nbsp; if (currentButtonState == HIGH \&\& lastButtonState == LOW) {

&nbsp;   counter++;

&nbsp;   lcd.clear();

&nbsp;   lcd.setCursor(0, 0);

&nbsp;   lcd.print("Count: ");

&nbsp;   lcd.print(counter);



&nbsp;   digitalWrite(ledPin, HIGH);

&nbsp;   delay(100); // Brief LED ON

&nbsp;   digitalWrite(ledPin, LOW);

&nbsp; }



&nbsp; lastButtonState = currentButtonState;

}











