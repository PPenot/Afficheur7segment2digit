#include <Arduino.h>

#define DATA 12      // connect to pin 14 on the 74HC595
#define LATCH 13     // connect to pin 12 on the 74HC595
#define CLOCK 19    // connect to pin 11 on the 74HC595

int data [] = {252, 96, 218, 242, 102, 182, 190, 224, 254, 246, 238, 62, 156, 122, 158, 142};
//int data [] = {3,159, 37, 13, 153, 239, 223, 191, 127, 128, 255, 238, 62, 156, 122, 158, 142};
//int data [] = {B11111100,//0
//B01100000, //1
//B11011010, //2
//B11110010, //3
//B01100110, //4
//B10110110, //5
//B10000010, //6
//B11111000, //7
//B10000000, //8
//B10010000 //9
//};

void displayNumber(int n);

void setup() {
    Serial.begin(115200);
    Serial.println("Initializing...");
    pinMode(LATCH, OUTPUT);
    pinMode(CLOCK, OUTPUT);
    pinMode(DATA, OUTPUT);
}

void loop() {
    int j;
    for ( j = 0 ; j < 100 ; j++ ) {
        Serial.println(j);
        Serial.println(data[j]);
        displayNumber(j);
        delay(200);
    }
}



void displayNumber(int n) {
    int left, right = 0;
//        digitalWrite(LATCH, LOW);
//        shiftOut(DATA, CLOCK, LSBFIRST, ~data [n]);
//        shiftOut(DATA, CLOCK, LSBFIRST, ~data [n]);
//        digitalWrite(LATCH, HIGH);
    if (n < 10) {
        digitalWrite(LATCH, LOW);
        shiftOut(DATA, CLOCK, LSBFIRST, ~data [n]);
        shiftOut(DATA, CLOCK, LSBFIRST, 255);
        digitalWrite(LATCH, HIGH);
    }
    else if (n >= 10) {
        right = n % 10;   // remainder of dividing the number to display by 10
        left = n / 10;  // quotient of dividing the number to display by 10
        digitalWrite(LATCH, LOW);
        shiftOut(DATA, CLOCK, LSBFIRST, ~data [right]);
        shiftOut(DATA, CLOCK, LSBFIRST, ~data [left]);
        digitalWrite(LATCH, HIGH);
    }
}