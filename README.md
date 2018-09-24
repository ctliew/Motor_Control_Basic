# Motor_Control_Basic
In this tutorial, a simple dual-channel H-bridge motor driver is used. It allows control of the direction and variable speed of up to two motors.

# H-bridge
In a nutshell, a H-bridge is a circuit that allow a DC output to be bi-directional and variable voltage at it output. As shown in the diagram below, it consists of four switches, usually FET (Field Effect Transistors), and the motor or any electronic that needs bi-directional variable voltages will sit in the middle and a DC voltage is supplied at the both ends.
![A H-bridge Diagram](https://github.com/ctliew/Motor_Control_Basic/blob/master/images/H_bridge.png)

## Bi-directional Voltage Control
![Bi-directional H-bridge Diagram](https://github.com/ctliew/Motor_Control_Basic/blob/master/images/H_bridge_operating.svg_.png)
The switches usually function in pairs, such that it only allows current to flow in one or the other direction. It is important not to turn on two switches at the same side at the same time as it will short circuit abd destroy the device and the power source.

# L298N Motor Driver
![L298N H-bridge](https://github.com/ctliew/Motor_Control_Basic/blob/master/images/L298N-Pinout.png)
L298N is an integrated-circuit that consists of a dual-channel H-bridge, such that it can operates two independent motors at the same time and featuring some auxiliary capabilities such as 5-volt regulator.

# Wiring

# Arduino Program
In this example, we are using Arduino to control one motor with forward and backward variable speed.
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
    delay(2);
  }
  
  delay(100);
  // Stop the motor
  analogWrite(ENA, 0);
  
  digitalWrite(DR1, LOW);
  digitalWRite(DR2, HIGH);

  for( int i = 0; i < 256 ; i++ ){
    // Slowly ramp up the speed
    analogWrite(ENA, i);
    // Adding a bit of delay
    delay(2);
  }
  
  delay(100);
  // Stop the motor
  analogWrite(ENA, 0);
  

}
```

# Small Execise
Try to made a function that can take into the speed and direction as parameters and use the function to control the motor. Also try to control two motors at the same time, and use it to operate a small rover chassis.
