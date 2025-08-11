# INTERFAZ-II

#### EJ 1: Hola mundo

#### EJ 2: LED Intermitente (Blink)
```js

void setup() {  // Configuración inicial (ej: pines como entrada/salida)
  pinMode(13, OUTPUT);  // Pin 13 como salida
}

void loop() {   // Se repite infinitamente
  digitalWrite(13, HIGH);  // Encender LED
  delay(200);             // Esperar 1 segundo
  digitalWrite(13, LOW);   // Apagar LED
  delay(400);             // Esperar 1 segundo


  digitalWrite(8, HIGH);  // Encender LED
  delay(300);             // Esperar 1 segundo
  digitalWrite(8, LOW);   // Apagar LED
  delay(400);             // Esperar 1 segundo
}

```

#### Ej 3: Control por Pulsador
```js
void setup() {
  pinMode(2, INPUT);  // Botón como entrada
  pinMode(13, OUTPUT);
}
void loop() {
  if (digitalRead(2) == HIGH) {  // Si se presiona el botón
    digitalWrite(13, HIGH);
  } else {
    digitalWrite(13, LOW);
  }
}
```

#### EJ 4: LED con Potenciómetro]
```js
void setup() {
  pinMode(9, OUTPUT);  // Pin PWM (símbolo ~)
}
void loop() {
  int valor = analogRead(A0);           // Leer potenciómetro (0-1023)
  int brillo = map(valor, 0, 1023, 0, 255);  // Convertir a rango PWM
  analogWrite(9, brillo);               // Ajustar brillo
}

```
