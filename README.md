# Motor_Control_Basic
In this tutorial, a simple dual-channel H-bridge motor driver is used. It allows control of the direction and variable speed of up to two motors.

# H-bridge
In a nutshell, a H-bridge is a circuit that allow a DC output to be bi-directional and variable voltage at it output. As shown in the diagram below, it consists of four switches, usually FET (Field Effect Transistors), and the motor or any electronic that needs bi-directional variable voltages will sit in the middle and a DC voltage is supplied at the both ends.
![A H-bridge Diagram](https://github.com/ctliew/Motor_Control_Basic/blob/master/images/H_bridge.png)

# L298N Motor Driver

```c
//Wiring Connections

#define ENA = 10; // Any pin that supports PWM output, for variable speed control
#define DR1 = 9;  // Any digital output, for directional control
#define DR2 = 8;  // Any digital output, for directional control

 
 
void setup(){
  // All motor control pins are outputs
  pinMode(ENA, OUTPUT);
  pinMode(DR1, OUTPUT);
  pinMode(DR2, OUTPUT);
}



void loop(){
  // Set the motor to run in one direction, this depends on your wiring
  digitalWrite(DR1, HIGH);
  digitalWRite(DR2, LOW);

  for( int i = 0; i < 256 ; i++ ){
    // Slowly ramp up the speed
    analogWrite(ENA, i);
    // Adding a bit of delay
    delay(5);
  }
}
```
