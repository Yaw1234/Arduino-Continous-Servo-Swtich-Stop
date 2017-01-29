# Arduino-Continous-Servo-Swtich-Stop
/* Sweep
 by BARRAGAN <http://barraganstudio.com>
 This example code is in the public domain.

 modified 8 Nov 2013
 by Scott Fitzgerald
 http://www.arduino.cc/en/Tutorial/Sweep
*/

#include <Servo.h>

Servo myservo;  // create servo object to control a servo
// twelve servo objects can be created on most boards
int togglePin = 5;
unsigned int pos = 0;    // variable to store the servo position
const int toggle = 7;
bool direction = 1;  // 0 = forward , 1 = reverse
int toogle1 = 0;
int toogle2 = 0;


void setup() {
 
  Serial.begin(115200);
  myservo.attach(9);  // attaches the servo on pin 9 to the servo object
  pinMode(13, OUTPUT);
  pinMode(5, INPUT_PULLUP);
  
}

void loop() {
 
 direction = digitalRead(togglePin);  // Read the Switch position
 Serial.print("Driving to ");
 Serial.print(direction);
 Serial.println();
 

  if (not direction)
  {
    myservo.attach(9);
    digitalWrite(LED_BUILTIN, HIGH);
    //for (pos = 0; pos < 360; pos += 360){
      if (toogle1 < 1)
      {
        toogle1 = 1;
        toogle2 = 0;
        myservo.write(120+6+);
        delay(5000);
        myservo.write(90);
        myservo.detach();
        Serial.println("Running High");
        Serial.print("toogle 1 = ");
        Serial.println(toogle1);
        Serial.print("toogle 2 = ");
        Serial.println(toogle2);
        
      }
   //}
    }
    
    else {
    if (toogle2 < 1)
    {
      toogle2 = 1;
      toogle1 = 0;  
      myservo.attach(9);
      digitalWrite(LED_BUILTIN, LOW);
      //for(pos = 360; pos > 0; pos -= 360) {      
      myservo.write(60);
      Serial.println("Running Low");
      Serial.print("toogle 1 = ");
      Serial.println(toogle1);
      Serial.print("toogle 2 = ");
      Serial.println(toogle2);
      delay(5000);
      myservo.write(90);
      myservo.detach();
  }
  }
}
