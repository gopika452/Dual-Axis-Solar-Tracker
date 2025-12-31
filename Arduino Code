#include <Servo.h>

Servo servoX;
Servo servoY;

int ldrTopLeft     = A0;
int ldrTopRight    = A1;
int ldrBottomLeft  = A2;
int ldrBottomRight = A3;

int angleX = 90;
int angleY = 90;

void setup() {
  servoX.attach(9);
  servoY.attach(10);

  servoX.write(angleX);
  servoY.write(angleY);

  Serial.begin(9600);
}

void loop() {
  int TL = analogRead(ldrTopLeft);
  int TR = analogRead(ldrTopRight);
  int BL = analogRead(ldrBottomLeft);
  int BR = analogRead(ldrBottomRight);

  Serial.print("TL: "); Serial.print(TL);
  Serial.print(" TR: "); Serial.print(TR);
  Serial.print(" BL: "); Serial.print(BL);
  Serial.print(" BR: "); Serial.println(BR);

  int avgTop = (TL + TR) / 2;
  int avgBottom = (BL + BR) / 2;
  int avgLeft = (TL + BL) / 2;
  int avgRight = (TR + BR) / 2;

  int tolerance = 50;  // Adjust tolerance to change sensitivity

  if (abs(avgTop - avgBottom) > tolerance) {  //Algorithm for vertical movement
    if (avgTop > avgBottom && angleY < 180) {
      angleY++;
    } else if (avgTop < avgBottom && angleY > 0) {
      angleY--;
    }
  }

  if (abs(avgLeft - avgRight) > tolerance) {  //Algorithm for horizontal movement
    if (avgLeft > avgRight && angleX < 180) {
      angleX++;
    } else if (avgLeft < avgRight && angleX > 0) {
      angleX--;
    }
  }

  servoX.write(angleX);
  servoY.write(angleY);

  delay(100);
}
