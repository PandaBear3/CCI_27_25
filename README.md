# CCI_27_25
CCI 27th jan process doc

Code A
#include <Servo.h>

Servo myservo1;
Servo myservo2;

void setup() {
pinMode(A0, INPUT);
pinMode(A1, INPUT);
myservo1.attach(13);
myservo2.attach(11);
}

void loop() {
Serial.print(analogRead(A0));
Serial.println(analogRead(A1));
int hip = map(analogRead(A0),0,1024,0,70);
int knee = map(analogRead(A0),0,1024,0,70);
myservo1.write(hip);
myservo2.write(knee);
delay(50);
}




Code B
#include <Servo.h>

Servo myservo1;
Servo myservo2;

void setup() {
pinMode(A0, INPUT);
pinMode(A1, INPUT);
myservo1.attach(13);
myservo2.attach(11);
}

void loop() {
Serial.print(analogRead(A0));
Serial.println(analogRead(A1));
int hip = map(analogRead(A0),0,1024,0,70);
int knee = map(analogRead(A0),0,1024,0,70);
myservo1.write(hip);
myservo2.write(knee);
delay(50);
}






Code C
#include <NewPing.h>

#define TRIGGER_PIN  12  
#define ECHO_PIN     11  
#define MAX_DISTANCE 200 

NewPing sonar(TRIGGER_PIN, ECHO_PIN, MAX_DISTANCE); 

void setup() {
  Serial.begin(115200);
  pinMode(6,OUTPUT); 
}

void loop() {
  delay(50);                    
  Serial.print("Ping: ");
  Serial.print(sonar.ping_cm()); 
  Serial.println("cm");

  int motorSpeed(map(sonar.ping_cm(),0,200,0,255));
  analogWrite(6, motorSpeed);
}

