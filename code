#include <SoftwareSerial.h>

// Define Motor Driver Pins
#define IN1 2
#define IN2 3
#define IN3 4
#define IN4 5

// Define Bluetooth RX and TX pins
SoftwareSerial bt(11, 10); // RX, TX

// Variable to store Bluetooth command
char data;

void setup() {
  // Start Serial Communication for debugging
  Serial.begin(9600);

  // Initialize motor control pins as outputs
  pinMode(IN1, OUTPUT);
  pinMode(IN2, OUTPUT);
  pinMode(IN3, OUTPUT);
  pinMode(IN4, OUTPUT);

  // Set all motors to STOP initially
  stopRobot();

  // Initialize Bluetooth communication
  bt.begin(9600);
  Serial.println("Bluetooth Robot Ready");
}

void loop() {
  // Check if Bluetooth data is available
  if (bt.available()) {
    data = bt.read(); // Read the incoming Bluetooth command
    Serial.print("Received: ");
    Serial.println(data);

    // Perform action based on received command
    switch (data) {
      case 'F': // Forward
        forward();
        break;

      case 'B': // Backward
        reverse();
        break;

      case 'L': // Left
        left();
        break;

      case 'R': // Right
        right();
        break;

      case 'S': // Stop
        stopRobot();
        break;

      default:
        Serial.println("Invalid Command");
        stopRobot(); // Stop for invalid commands
        break;
    }
  }
  delay(100); // Short delay for responsiveness
}

// Function to move the robot forward
void forward() {
  digitalWrite(IN1, HIGH);
  digitalWrite(IN2, LOW);
  digitalWrite(IN3, LOW);
  digitalWrite(IN4, HIGH);
  Serial.println("Moving Forward");
}

// Function to move the robot backward
void reverse() {
  digitalWrite(IN1, LOW);
  digitalWrite(IN2, HIGH);
  digitalWrite(IN3, HIGH);
  digitalWrite(IN4, LOW);
  Serial.println("Moving Backward");
}

// Function to turn the robot left
void left() {
  digitalWrite(IN1, HIGH);
  digitalWrite(IN2, LOW);
  digitalWrite(IN3, HIGH);
  digitalWrite(IN4, LOW);
  Serial.println("Turning Left");
}

// Function to turn the robot right
void right() {
  digitalWrite(IN1, LOW);
  digitalWrite(IN2, HIGH);
  digitalWrite(IN3, LOW);
  digitalWrite(IN4, HIGH);
  Serial.println("Turning Right");
}

// Function to stop the robot
void stopRobot() {
  digitalWrite(IN1, LOW);
  digitalWrite(IN2, LOW);
  digitalWrite(IN3, LOW);
  digitalWrite(IN4, LOW);
  Serial.println("Stopping");
}
