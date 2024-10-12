//user input word or phrase to be translated into morse code

int RedLED=8;
int BlueLED=9;
int buzzPin=7;
int toneVal=1;
int ditLength;
int dahLength;
int spaceLength;

void setup() {
  Serial.begin(9600);
  pinMode(buzzPin,OUTPUT);
  pinMode(RedLED,OUTPUT);
  pinMode(BlueLED,OUTPUT);
}

void loop() {
  Serial.println("Choose a speed: ");
  char speed_choice = getMenuChoice();
  Serial.println(speed_choice);

  setSpeed(speed_choice);
  
  String input_string;
  Serial.println("Enter a Word or Phrase: ");  //Prompt User for Word to Translate into Morse Code
  while (Serial.available()==0){
  }
  
  input_string=Serial.readString();  //Store it in a String variable
  
  int str_len=input_string.length()+1;  //Calculate number of letter = length of array
  
  char buf[30];


  input_string.toCharArray(buf, str_len);   //Converts string input into a char array
  Serial.println(buf);


  for (int x=0; x<str_len-1; x++){
      char letter = tolower(buf[x]);
      Serial.println(letter);
      translateLetter(letter);   //translates each letter in the char array into buzzer sound and LED blinks
      
      delay(800);
  }
}


char getMenuChoice(){
  Serial.println("A. 20 WPM  B. 35 WPM  C. 50 WPM");
  while(Serial.available()==0){
    
  }
  char choice=Serial.read();


  return choice;
}


void setSpeed(char c){
  switch(c){
    case 'A':
      ditLength=60;
      break;
    case 'B':
      ditLength=34;
      break;
    case 'C':
      ditLength=24;
      break;
  }
  dahLength=ditLength*3;
  spaceLength=ditLength*7;
}


void translateLetter(char l){
  switch(l){
        case 'a':
          ditSound(1);  //The dit sound last for a set number of milliseconds,
          dahSound(1);  //the dah sound lasts for 3 times as long as a dit
          break;        //LED blinks are of same duration and simultaneous as the dit and dah sounds
        case 'b':
          dahSound(1);
          ditSound(3);
          break;
        case 'c':
          dahSound(1);
          ditSound(1);
          dahSound(1);
          ditSound(1);
          break;
        case 'd':
          dahSound(1);
          ditSound(2);
          break;
        case 'e':
          ditSound(1);
          break;
        case 'f':
          ditSound(2);
          dahSound(1);
          ditSound(1);
          break;
        case 'g':
          dahSound(2);
          ditSound(1);
          break;
        case 'h':
          ditSound(4);
          break;
        case 'i':
          ditSound(2);
          break;
        case 'j':
          ditSound(1);
          dahSound(3);
          break;
        case 'k':
          dahSound(1);
          ditSound(1);
          dahSound(1);
          break;
        case 'l':
          ditSound(1);
          dahSound(1);
          ditSound(2);
          break;
        case 'm':
          dahSound(2);
          break;
        case 'n':
          dahSound(1);
          ditSound(1);
          break;
        case 'o':
          dahSound(3);
          break;
        case 'p':
          ditSound(1);
          dahSound(2);
          ditSound(1);
          break;
        case 'q':
          dahSound(2);
          ditSound(1);
          dahSound(1);
          break;
        case 'r':
          ditSound(1);
          dahSound(1);
          ditSound(1);
          break;
        case 's':
          ditSound(3);
          break;
        case 't':
          dahSound(1);
          break;
        case 'u':
          ditSound(2);
          dahSound(1);
          break;
        case 'v':
          ditSound(3);
          dahSound(1);
          break;
        case 'w':
          ditSound(1);
          dahSound(2);
          break;
        case 'x':
          dahSound(1);
          ditSound(2);
          dahSound(1);
          break;
        case 'y':
          dahSound(1);
          ditSound(1);
          dahSound(2);
          break;
        case 'z':
          dahSound(2);
          ditSound(2);
          break;
        case '1':
          ditSound(1);
          dahSound(4);
          break;
        case '2':
          ditSound(2);
          dahSound(3);
          break;
        case '3':
          ditSound(3);
          dahSound(2);
          break;
        case '4':
          ditSound(4);
          dahSound(1);
          break;
        case '5':
          ditSound(5);
          break;
        case '6':
          dahSound(1);
          ditSound(4);
          break;
        case '7':
          dahSound(2);
          ditSound(3);
          break;
        case '8':
          dahSound(3);
          ditSound(2);
          break;
        case '9':
          dahSound(4);
          ditSound(1);
          break;
        case '0':
          dahSound(5);
          break;
        case ' ':
          delay(spaceLength);
          break;
        default:
          Serial.println("Invalid Letter");
          break;
      }
}
 
void ditSound(int times){
  for(int k=0; k<times; k++){
    digitalWrite(RedLED,HIGH);
    delay(ditLength);
    for(int x=0; x<ditLength; x++){
      digitalWrite(buzzPin,HIGH);
      delay(toneVal);
      digitalWrite(buzzPin,LOW);
      delay(toneVal);
      }
    digitalWrite(RedLED,LOW);
  delay(dahLength);
  }
}


//a dah sound should be 3 times longer than the duration of a dit
void dahSound(int times){
  for(int k=0; k<times; k++){
    digitalWrite(BlueLED,HIGH);
    delay(dahLength);
    for(int x=0; x<dahLength; x++){
      digitalWrite(buzzPin,HIGH);
      delay(toneVal);
      digitalWrite(buzzPin,LOW);
      delay(toneVal);
      }
    digitalWrite(BlueLED,LOW);
  delay(dahLength);
  }
}
