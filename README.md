#include<Servo.h>
Servo myServo;
int pos = 0;
int trigPin = 9;
int echoPin = 10;


long duration;
int distance;
 void setup(){
  myServo.attach(11);
  pinMode(trigPin,OUTPUT);
  pinMode(echoPin,INPUT);
  pinMode(A0,INPUT);
  pinMode(8,OUTPUT);
  pinMode(13,OUTPUT);
  
  Serial.begin(115200);
 }

 void loop(){
 
  digitalWrite(13,HIGH);
    
  myServo.write(pos);
  digitalWrite(trigPin ,LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin,HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin,LOW);
  
  duration = pulseIn(echoPin,HIGH);
  distance = duration*0.34/2;
  
  Serial.print("distance:");
  Serial.println(distance);
  if(distance<35&&distance>=0)
  {
     for(pos=0;pos<90;pos++){
      myServo.write(pos);
     }
     
      
  }
  int x = analogRead(A0);
  if(x>85){
    delay(2000); 
    digitalWrite(8,HIGH);
                     
  }
  else{
    digitalWrite(8,LOW);
  }
  
  }  
