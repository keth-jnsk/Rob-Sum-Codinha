# Rob-Sum-Codinha
Projeto Integrador de Extensão de Engenharia de Software


// ==== DEFINIÇÃO DAS PORTAS DOS MOTORES ====

// Motor A (esquerdo)
int IN1 = 10;
int IN2 = 9;
int ENA = 5; // PWM para controle de velocidade

// Motor B (direito)
int IN3 = 7;
int IN4 = 11;
int ENB = 6; // PWM para controle de velocidade

// ==== SENSORES DE LINHA ====
int sensorFrontal = 2;   // Sensor digital frontal (melhor prática)
int sensorTraseiro = 3;  // Sensor digital traseiro

// ==== SENSOR ULTRASSÔNICO ====
int trigger = 12;
int echo = 8;
float distancia;

// ==== CONFIGURAÇÃO ====
#define LIMITE_DISTANCIA 40  // cm

// ==== FUNÇÃO DE DISTÂNCIA ====
float dist(int trigger, int echo) {
  digitalWrite(trigger, LOW);
  delayMicroseconds(2);
  digitalWrite(trigger, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigger, LOW);
  return (pulseIn(echo, HIGH) * 0.0343) / 2;
}

// ==== SETUP ====
void setup() {
  Serial.begin(9600);
  Serial.println("Inicializando robô...");

  // Motores
  pinMode(IN1, OUTPUT);
  pinMode(IN2, OUTPUT);
  pinMode(ENA, OUTPUT);

  pinMode(IN3, OUTPUT);
  pinMode(IN4, OUTPUT);
  pinMode(ENB, OUTPUT);

  // Sensores de linha
  pinMode(sensorFrontal, INPUT);
  pinMode(sensorTraseiro, INPUT);

  // Ultrassônico
  pinMode(trigger, OUTPUT);
  pinMode(echo, INPUT);

  // Espera obrigatória após apito do juiz
  delay(3000);
}

// ==== LOOP PRINCIPAL ====
void loop() {
  int valorFrontal = digitalRead(sensorFrontal);
  int valorTraseiro = digitalRead(sensorTraseiro);
  distancia = dist(trigger, echo);

  Serial.print("Distância: ");
  Serial.print(distancia);
  Serial.print(" cm | Sensor Frontal: ");
  Serial.print(valorFrontal);
  Serial.print(" | Sensor Traseiro: ");
  Serial.println(valorTraseiro);

  if (distancia > 0 && distancia < LIMITE_DISTANCIA) {
    Serial.println("ATACANDO!!");
    atacar();
  } else if (valorFrontal == LOW) { // LOW = linha detectada
    Serial.println("Borda à frente! Corrigindo pra direita...");
    corrigirDirecaoDireita();
  } else if (valorTraseiro == LOW) {
    Serial.println("Borda atrás! Corrigindo pra esquerda...");
    corrigirDirecaoEsquerda();
  } else {
    Serial.println("Girando no lugar...");
    girarNoLugar();
  }
}

// ==== FUNÇÕES DE MOVIMENTO ====

// ATACAR → Ambos os motores pra frente
void atacar() {
  digitalWrite(IN1, HIGH);
  digitalWrite(IN2, LOW);
  analogWrite(ENA, 200); // velocidade ajustável

  digitalWrite(IN3, HIGH);
  digitalWrite(IN4, LOW);
  analogWrite(ENB, 200);
}

// Corrigir pra direita (linha frontal) → girar rápido
void corrigirDirecaoDireita() {
  digitalWrite(IN1, LOW);  
  digitalWrite(IN2, HIGH);
  analogWrite(ENA, 180);

  digitalWrite(IN3, HIGH); 
  digitalWrite(IN4, LOW);
  analogWrite(ENB, 180);
}

// Corrigir pra esquerda (linha traseira) → girar rápido
void corrigirDirecaoEsquerda() {
  digitalWrite(IN1, HIGH); 
  digitalWrite(IN2, LOW);
  analogWrite(ENA, 180);

  digitalWrite(IN3, LOW);  
  digitalWrite(IN4, HIGH);
  analogWrite(ENB, 180);
}

// Gira no próprio eixo (modo busca)
void girarNoLugar() {
  digitalWrite(IN1, HIGH); 
  digitalWrite(IN2, LOW);
  analogWrite(ENA, 180);

  digitalWrite(IN3, LOW);  
  digitalWrite(IN4, HIGH);
  analogWrite(ENB, 180);
}

// Parar motores
void parar() {
  digitalWrite(IN1, LOW);
  digitalWrite(IN2, LOW);
  analogWrite(ENA, 0);

  digitalWrite(IN3, LOW);
  digitalWrite(IN4, LOW);
  analogWrite(ENB, 0);
}
