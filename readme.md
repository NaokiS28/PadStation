# PadStation
Basic library for reading and writing to PlayStation 1 and 2 style pads on an arduino with auto detection between the two.

Basic usage:
```
#include "PadStation.h"

const int Data = 2;
const int Clock = 3;
const int Select = 4;

int controllerData = 0;     //  x,x,x,x, TR, TL, X, Y, SEL, STRT, B, A, Ri, Lf, Dn, Up

SuperPad pad(Data, Clock, Latch);     // HardwareSerial port, Sense pin

void setup(){
    Serial.begin(9600);

    // Print pad type
    Serial.print(F("Controller connected: "));
    if(pad.type() == 1){
        Serial.println(F("SNES"));
    } else {
        Serial.println(F("NES"));
    }
}

void loop(){
    if(pad.update()){
        controllerData = pad.read();
        Serial.print("Pad: ");
        Serial.println(controllerData, BIN);
    }
}

```

