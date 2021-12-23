#include<LiquidCrystal.h> 
LiquidCrystal lcd(2,3,4,5,6,7); 
int In = 14; 
int Out = 19; 
int relay = 15; 
int count=0; 
void setup() 
{ 
  lcd.begin(16,2); 
  lcd.print("Visitor Counter"); 
  delay(2000); 
  pinMode(In, INPUT); 
  pinMode(Out, INPUT); 
  pinMode(relay, OUTPUT); 
  lcd.clear(); 
  lcd.print("Person In Room:"); 
  Serial.begin(9600); 
} 
void loop() 
{    
  if (digitalRead(In) == LOW){ 
    count=count+1; 
  } 
 
  else if (digitalRead(Out) == LOW){ 
    if(count=0){
      count=count+0;
    }
    else{
      count=count-1;
    }
  } 
   
  else if (count > 0) 
  { 
    digitalWrite(relay, LOW); 
  } 
 
  else if(count <= 0){ 
    digitalWrite(relay, HIGH ); 
  } 
 
  lcd.setCursor(0,1); 
  lcd.print(count); 
  Serial.println(count);  
 
  delay(700); 
}
