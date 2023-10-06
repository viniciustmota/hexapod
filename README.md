#include <Servo.h>


const int servoPinos[] = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, A0, A1, A2, A3};
const int angulosIniciais[] = {90, 90, 90, 90, 90, 90, 90, 90, 90, 90, 90, 90, 90, 90, 90, 90, 90, 90};
Servo servos[18];

void definirPosicaoServo(int servoNumero, int angulo) {
  
  if (servoNumero >= 0 && servoNumero < 18) {
    angulo = constrain(angulo, 0, 180);
    servos[servoNumero].write(angulo);
  }
}

void definirPosicaoTodosServos(int angulos[]) {
  for (int i = 0; i < 18; i++) {
    definirPosicaoServo(i, angulos[i]);
  }
}

void moverPernaFrente(int servo1, int servo2) {
  int angulos[] = {90, 90, 90, 90, 90, 90, 90, 90, 90, 90, 90, 90, 90, 90, 90, 90, 90, 90};
  angulos[servo1] = 60;
  angulos[servo2] = 120;
  definirPosicaoTodosServos(angulos);
  delay(550);
}
void moverPernaTras(int servo1, int servo2) {
  int angulos[] = {90, 90, 90, 90, 90, 90, 90, 90, 90, 90, 90, 90, 90, 90, 90, 90, 90, 90};
  angulos[servo1] = 120;
  angulos[servo2] = 60;
  definirPosicaoTodosServos(angulos);
  delay(550);
}

void setup() {
  for (int i = 0; i < 18; i++) {
    servos[i].attach(servoPinos[i]);
    servos[i].write(angulosIniciais[i]);
  }
}

void loop() {
 
  moverPernaFrente(0, 6); // Perna 2
  moverPernaFrente(1, 7); // Perna 3
  moverPernaFrente(12, 13); // Quadril da perna 1 e 2

  
  moverPernaFrente(2, 8); // Perna 1
  moverPernaFrente(3, 9); // Perna 4
  moverPernaFrente(14, 15); // Quadril da perna 3 e 4


  moverPernaFrente(4, 10); // Perna 5
  moverPernaFrente(5, 11); // Perna 6
  moverPernaFrente(16, 17); // Quadril da perna 5 e 6


  moverPernaTras(0, 6); //Perna 1
  moverPernaTras(1, 7); //Perna 2
  moverPernaTras(12, 13); // Quadril da perna 1 e 2

  moverPernaTras(2, 8); //Perna 3
  moverPernaTras(3, 9); //Perna 4
  moverPernaTras(14, 15); // Quadril da perna 3 e 4

  moverPernaTras(4, 10); //Perna 5
  moverPernaTras(5, 11); //Perna 6
  moverPernaTras(16, 17); // Quadril da perna 5 e 6

}
