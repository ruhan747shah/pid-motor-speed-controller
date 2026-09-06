#define STBY 9
#define AIN1 8
#define AIN2 7
#define PWMA 6
#define ENCODER 2

volatile long encoderCount = 0;

long lastCount = 0;
unsigned long lastTime = 0;

float kp = 0.5;
float ki = 0.05;
float kd = 0.01;

float targetSpeed = 2100;

float integral = 0;
float lastError = 0;

void countEncoder() {
  encoderCount++;
}

void setup() {
  Serial.begin(9600);

  pinMode(STBY, OUTPUT);
  pinMode(AIN1, OUTPUT);
  pinMode(AIN2, OUTPUT);
  pinMode(PWMA, OUTPUT);
  pinMode(ENCODER, INPUT);

  attachInterrupt(digitalPinToInterrupt(ENCODER), countEncoder, RISING);

  digitalWrite(STBY, HIGH);
  digitalWrite(AIN1, HIGH);
  digitalWrite(AIN2, LOW);
}

void loop() {

  if (millis() - lastTime >= 100) {

    // Measure motor speed
    long newCount = encoderCount;
    float speed = (newCount - lastCount) * 10;

    lastCount = newCount;
    lastTime = millis();

    // PID
    float error = targetSpeed - speed;

    integral = integral + error * 0.1;

    float derivative = (error - lastError) / 0.1;

    float output = kp * error
                 + ki * integral
                 + kd * derivative;

    lastError = error;

    // Control motor
    output = constrain(output, 0, 255);
    analogWrite(PWMA, output);

    // Serial Monitor
    Serial.print("Speed: ");
    Serial.print(speed);
    Serial.print(" | Target: ");
    Serial.print(targetSpeed);
    Serial.print(" | PWM: ");
    Serial.println(output);
  }
}
