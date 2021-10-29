#include <LiquidCrystal.h>

#include <Servo.h>
Servo myservo;
int Rled=12;
int pir=2;
int buzzer=3;
LiquidCrystal lcd(A0,A1,A2,A3,A4,A5) ;
void setup()
{ pinMode(Rled,OUTPUT);
  pinMode(pir,INPUT);
  myservo.attach(9);
  Serial.begin(9600);

}

void loop()
{
  int val1 = digitalRead(pir);
  Serial.println(val1);
  if(val1==HIGH){
    digitalWrite(Rled,HIGH);
    myservo.write(180);
    lcd.setCursor(0,0);
    tone(buzzer,450);
    delay(10);
    lcd.print("DETECTED");
    delay(500);
    lcd.clear();
    lcd.setCursor(0,1);
    lcd.print("ServoAngle=180 degree");
    delay(500);
    lcd.clear();
  }
 else if(val1==0) 
 {
   digitalWrite(Rled,0);
   myservo.write(0);
   lcd.setCursor(0,0);
   lcd.print("NOT DETECTED");
    delay(500);
    lcd.setCursor(0,1);
    lcd.print("ServoAngle=0 degree");
    delay(200);
    noTone(buzzer);      
    delay(500);
    lcd.clear();
  }
                                        
 
}
  