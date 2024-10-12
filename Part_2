//Allow user input of morse code through the push buttons, translates individual letters from morse code and displays on screen

int dotPin = 11; 
int dashPin = 10; 
int buzzPin=7;
int redLED=8;
int blueLED=9;


String morseInput = "";   
String message = "";     


int letterGap = 500;     
int wordGap = 1000;  


long lastInputTime = 0;  


int ditLength=40;
int dahLength=120;
int toneVal=1;


void setup() {
  Serial.begin(9600);
  pinMode(dotPin, INPUT_PULLUP);
  pinMode(dashPin, INPUT_PULLUP);
  pinMode(redLED,OUTPUT);
  pinMode(blueLED,OUTPUT);
  pinMode(buzzPin,OUTPUT);
}


void loop() {
  int dotButtonState = digitalRead(dotPin);
  int dashButtonState = digitalRead(dashPin);
  long currentTime = millis();


  if (dotButtonState == LOW || dashButtonState == LOW) {
  
    if (currentTime - lastInputTime > wordGap) {
      
      message += " ";
    }
    lastInputTime = currentTime;


    if (dotButtonState == LOW) {
      digitalWrite(redLED,HIGH);
      delay(ditLength);
      digitalWrite(redLED,LOW);


      buzzerSound(ditLength);
      while (digitalRead(dotPin) == LOW) {}
        morseInput += ".";
    }


    if (dashButtonState == LOW) {
      digitalWrite(blueLED,HIGH);
      delay(dahLength);
      digitalWrite(blueLED,LOW);


      buzzerSound(dahLength);
      while (digitalRead(dashPin) == LOW) {}
      morseInput += "-";
    }
  }


  if (currentTime - lastInputTime > letterGap && morseInput != "") {
    char letter = translateCode(morseInput);


    message += letter;
    morseInput = "";
  }


  if (message != "") {
    Serial.print(message);


    message = ""; 
  }
}


char translateCode(String code) {
  
  const char* morseCode[] = {
    ".-", "-...", "-.-.", "-..", ".", "..-.", "--.", "....", "..", ".---", "-.-", ".-..", "--",
    "-.", "---", ".--.", "--.-", ".-.", "...", "-", "..-", "...-", ".--", "-..-", "-.--", "--..",
    "-----", ".----", "..---", "...--", "....-", ".....", "-....", "--...", "---..", "----.",
    ".-.-.-"};
  
  
  const char alphabet[] = "ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789.";
  
  for (int i = 0; i < 37; i++) { 
    if (code == morseCode[i]) {
      return alphabet[i];
    }
  }
}


void buzzerSound(int buzzT){
  for (int x=0; x<buzzT; x++){
    digitalWrite(buzzPin,HIGH);
    delay(toneVal);
    digitalWrite(buzzPin,LOW);
    delay(toneVal);
  }
}
