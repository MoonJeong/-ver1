# -ver1
오류X 코드정리전

#include <wiringPi.h>
#include <stdio.h>
#define CAR_RED 0
#define CAR_YELLOW 2
#define CAR_GREEN 3
#define PERSON_RED 21 
#define PERSON_GREEN 22


int main(void){
 if(wiringPiSetup() == -1) {
  printf("setup wiringPi failed!");
  return 1;
 }

 pinMode(CAR_RED,OUTPUT);
 pinMode(CAR_YELLOW,OUTPUT);
 pinMode(CAR_GREEN,OUTPUT);
 pinMode(PERSON_RED,OUTPUT);
 pinMode(PERSON_GREEN,OUTPUT);


 for(int i = 0; i < 1000; i++ ){// CAR > green light PERSON > red light
 if(i % 3 == 0){
  digitalWrite(CAR_GREEN,LOW);
  printf("CAR_GREEN OFF...\n");
  delay(100);

  digitalWrite(CAR_GREEN,HIGH);
  printf("CAR_GREEN ON... car go\n");
  delay(100);
    
  digitalWrite(PERSON_RED,LOW);
  printf("PERSON_RED OFF...\n");
  delay(100);

  digitalWrite(PERSON_RED,HIGH);
  printf("PERSON_RED ON... person stop \n");
  delay(100);

}
 else if(i % 3 == 1){  //CAR > yellow light
  digitalWrite(CAR_YELLOW,LOW); 
  printf("CAR_YELLOW OFF...\n");
  delay(100);


  digitalWrite(CAR_YELLOW,HIGH);
  printf("CAR_YELLOW ON... car wait \n");
  delay(100);
}

  else if (i % 3 == 2){ //CAR > red light PERSON > green light
  digitalWrite(CAR_RED,LOW);
  printf("CAR RED OFF...\n");
  delay(100);

  digitalWrite(CAR_RED,HIGH);
  printf("CAR_RED ON... car stop \n");
  delay(100);
  
  digitalWrite(PERSON_GREEN,LOW); 
  printf("PERSON_GREEN OFF...\n");
  delay(100);


  digitalWrite(PERSON_GREEN,HIGH);
  printf("PERSON_GREEN... person go \n");
  delay(100);
}

 }
 return 0;
 }
