// include the library code:
#include <LiquidCrystal.h>
#include <EEPROM.h>
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);
unsigned int load = 0,gas=0;        // value read from the pot
const int relay1 = 5;
const int relay2 = 6;
const int relay3 = 7;
const int relay4 = 8;
const int pump = 9;
const int fire1 = 2;
const int fire2 = 3;
const int fire3 = 4;
unsigned int key1;
unsigned int key2;
unsigned int key3,key4,key5,proxy;
char a[30],b[10];
unsigned int m=0,value=0;
unsigned char mm,tt=0,load_cell=0;
boolean stringComplete = false;  // whether the string is complete
boolean started=false;
unsigned int sec=0;
void keypad();
void received();
void Msg_Send();
void send_msg();
unsigned long ping();
unsigned int temp,humi,volt;
void fwd()
{
   Serial.println("FWD");
  
   digitalWrite(relay1,HIGH); digitalWrite(relay2,LOW);
  digitalWrite(relay3,LOW); digitalWrite(relay4,HIGH);
}
void rev()
{
    Serial.println("REV");

      digitalWrite(relay1,LOW); digitalWrite(relay2,HIGH);
  digitalWrite(relay3,HIGH); digitalWrite(relay4,LOW);
  
}

void left()
{
  Serial.println("LEFT");

   digitalWrite(relay1,HIGH); digitalWrite(relay2,LOW);
   digitalWrite(relay3,HIGH); digitalWrite(relay4,LOW);
 
 }
void right()
{
    Serial.println("RIGHT");

    digitalWrite(relay1,LOW); digitalWrite(relay2,HIGH);
  digitalWrite(relay3,LOW); digitalWrite(relay4,HIGH);
  
}

void stop_()
{
    Serial.println("STP");

   
   digitalWrite(relay1,LOW);digitalWrite(relay2,LOW);
   digitalWrite(relay3,LOW); digitalWrite(relay4,LOW);
  
}
void setup() {
  // initialize serial:
  
   pinMode(fire1, INPUT_PULLUP); 
   pinMode(fire2, INPUT_PULLUP);
   pinMode(fire3, INPUT_PULLUP);  
   pinMode(relay1, OUTPUT);   
   pinMode(relay2, OUTPUT);   
   pinMode(relay3, OUTPUT);   
   pinMode(relay4, OUTPUT);   

    pinMode(pump, OUTPUT);   
  
  digitalWrite(relay1,LOW);
  digitalWrite(relay2,LOW);
  digitalWrite(relay3,LOW);
  digitalWrite(relay4,LOW);
void setup() {
  // initialize serial:
  
   pinMode(fire1, INPUT_PULLUP); 
   pinMode(fire2, INPUT_PULLUP);
   pinMode(fire3, INPUT_PULLUP);  
   pinMode(relay1, OUTPUT);   
   pinMode(relay2, OUTPUT);   
   pinMode(relay3, OUTPUT);   
   pinMode(relay4, OUTPUT);   

    pinMode(pump, OUTPUT);   
  
  digitalWrite(relay1,LOW);
  digitalWrite(relay2,LOW);
  digitalWrite(relay3,LOW);
  digitalWrite(relay4,LOW);
digitalWrite(relay1,LOW);
  digitalWrite(relay2,LOW);
  digitalWrite(relay3,LOW);
  digitalWrite(relay4,LOW);

digitalWrite(pump,HIGH);


 Serial.begin(9600);
    started=true;
}
void loop() {
    
        if(digitalRead(fire1) == HIGH)
        {
          left();
          delay(2000);
          stop_();
          digitalWrite(pump,LOW);
          Serial.println("FIRE1 DET");
          delay(6000);
          digitalWrite(pump,HIGH);
        }
        else if(digitalRead(fire2) == HIGH)
        {
          right();
          delay(2000);
           stop_();
digitalWrite(pump,LOW);
          Serial.println("FIRE2 DET");
          delay(6000);
           digitalWrite(pump,HIGH);
        }
         else if(digitalRead(fire3) == HIGH)
        {
          stop_();
          delay(500);
          digitalWrite(pump,LOW);
          Serial.println("FIRE3 DET");
          delay(6000);
           digitalWrite(pump,HIGH);
        }
        else{fwd();
}
}void serialEvent() {
  while (Serial.available()) {
    // get the new byte:
    char inChar;
    
    
    //a[m] = (char)Serial.read(); 
    inChar = (char)Serial.read(); 
    
    
      Serial.print(inChar);
   
      a[m] = inChar;
      b[0] = inChar;
      if(a[0] == '*'){if(m < 13)m++;}
}
}
