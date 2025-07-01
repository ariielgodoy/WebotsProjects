# EPuckGoForward 🚗 – Mi primer paso en Webots

Os enseño mis inicios con [Webots](https://cyberbotics.com/), un simulador de robots **muy visual y user-friendly**.

Este es el **primer programa que he creado**, usando C++, y hace que un robot e-puck se mueva hacia adelante controlando sus ruedas por velocidad. En el futuro iré subiendo más experimentos, también en Python.

---

## 🎯 ¿Qué hace este programa?

- Controla un robot `e-puck` en Webots
- Ajusta los motores para moverse hacia adelante
- Usa **control por velocidad**, desactivando el control por posición

---

## 📦 Código fuente principal

Archivo: `EPuckGoForward.cpp`

```cpp
#include <webots/Robot.hpp>
#include <webots/Motor.hpp>

#define TIME_STEP 64
#define MAX_SPEED 6.28

using namespace webots;

int main(int argc, char **argv) {
  Robot *robot = new Robot();

  Motor *leftMotor = robot->getMotor("left wheel motor");
  Motor *rightMotor = robot->getMotor("right wheel motor");

  leftMotor->setPosition(INFINITY); // Desactiva control por posición
  rightMotor->setPosition(INFINITY);

  leftMotor->setVelocity(0.1 * MAX_SPEED); // Velocidad hacia delante
  rightMotor->setVelocity(0.1 * MAX_SPEED);

  while (robot->step(TIME_STEP) != -1) {
    // El robot se moverá hacia delante continuamente
    // Aquí podrías añadir lógica para sensores en el futuro
    delete robot;
    return 0;
  };

  delete robot;
  return 0;
}
