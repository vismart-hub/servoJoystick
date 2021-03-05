/*SERVO_JOYSTICK
This program let to move a Servo Motor depending on direction Joystick
Created by vismart937@gmail.com
03/03/2021
*/
#include <Servo.h> //Call library of servo motor
Servo viServo; //Create servo object
int sensorValue; //Variable to stock readings from joystick X
int angle; //Variable to map readings of Joystick potentiometer X
 
void setup() {
  Serial.begin(9600); //Intialize monitor serial
  viServo.attach(6); //Declare pin where attach servo motor
  
  //Action to prove that servo works
  viServo.write(0); 
  delay(1000);
   
}

void loop() {
  //Read Xpotentiometer joystick & stock on variable sensor Value
  sensorValue = analogRead(A1);
  
  //Map analog readings of sensor on angle values
  angle = map(sensorValue,0,1023,179,0);
  
  //Print values X potentiometer Joystick & angles map
  Serial.print(sensorValue);
  Serial.print("\t");
  Serial.println(angle);
  
  //Move servo to angle corresponding
  viServo.write(angle);
  delay(20);
}