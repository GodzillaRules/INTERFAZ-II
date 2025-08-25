# INTERFAZ-II

#### EJ 1: Hola mundo
```js
void setup() {
  Serial.begin(9600); // Inicia la comunicación serie a 9600 bps
  Serial.println("Hey, you. You're finally awake"); // Envía "Hey, you. You're finally awake" al monitor serial
}

void loop() {
  // No es necesario poner nada en el loop para este ejemplo
}
```
<img width="866" height="557" alt="image" src="https://github.com/user-attachments/assets/85fab06f-2a66-4d5c-bf90-55033f6a38d4" />
<img width="249" height="100" alt="image" src="https://github.com/user-attachments/assets/db3a791f-b7ea-441f-8d9d-351bad31ac9a" />


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
<img width="1145" height="765" alt="image" src="https://github.com/user-attachments/assets/b4ae4f6d-2dd2-4ccb-9d63-91cd10824590" />


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
<img width="907" height="778" alt="image" src="https://github.com/user-attachments/assets/11bea6a5-b37a-4dde-a784-d43045f0a943" />

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

<img width="796" height="751" alt="image" src="https://github.com/user-attachments/assets/10923710-49b5-406c-a07b-476ff7bb8409" />

#### EJ 5: SEMAFORO
```js

// C++ code - Semáforo Autos y Peatones

// Definición de pines
int LED_1 = 6;  // Luz roja autos
int LED_2 = 7;  // Luz amarilla autos
int LED_3 = 8;  // Luz verde autos
int LED_4 = 9;  // Luz verde peatones
int LED_5 = 10; // Luz roja peatones

void setup() {
  // Configuramos todos los pines como salida
  pinMode(LED_1, OUTPUT);
  pinMode(LED_2, OUTPUT);
  pinMode(LED_3, OUTPUT);
  pinMode(LED_4, OUTPUT);
  pinMode(LED_5, OUTPUT);
}

void loop() {
  // Fase 1: Autos en verde, peatones en rojo
  digitalWrite(LED_1, LOW);   // Rojo autos apagado
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado
  digitalWrite(LED_3, HIGH);  // Verde autos encendido
  digitalWrite(LED_4, LOW);   // Verde peatones apagado
  digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  delay(5000); // 5 segundos

  //  Fase 2: Amarillo autos, peatones siguen en rojo
  digitalWrite(LED_3, LOW);   // Verde autos apagado
  digitalWrite(LED_2, HIGH);  // Amarillo autos encendido
  delay(2000); // 2 segundos
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado

  //  Fase 3: Rojo autos, verde peatones
  digitalWrite(LED_1, HIGH);  // Rojo autos encendido
  digitalWrite(LED_5, LOW);   // Rojo peatones apagado
  digitalWrite(LED_4, HIGH);  // Verde peatones encendido
  delay(5000); // 5 segundos

  //  Fase 4: Rojo autos, rojo peatones (tiempo intermedio)
  // digitalWrite(LED_4, LOW);   // Verde peatones apagado
  // digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  // delay(2000); // 2 segundos 
}
```
<img width="1108" height="680" alt="image" src="https://github.com/user-attachments/assets/ed948f6a-8d2a-4d70-96ea-29448029e6a8" />




