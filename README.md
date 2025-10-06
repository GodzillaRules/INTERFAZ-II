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

 #### A1: Semaforo con intermitente

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
  //  Fase 1: Autos en verde, peatones en rojo
  digitalWrite(LED_1, LOW);   // Rojo autos apagado
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado
  digitalWrite(LED_3, HIGH);  // Verde autos encendido
  digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  digitalWrite(LED_4, LOW);   // Verde peatones apagado
  delay(5000); // 5 segundos

  //  Fase 2: Amarillo autos, peatones siguen en rojo
  digitalWrite(LED_3, LOW);   // Verde autos apagado
  digitalWrite(LED_2, HIGH);  // Amarillo autos encendido
  delay(2000); // 2 segundos
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado

//  Fase 3: Rojo autos, verde peatones
digitalWrite(LED_1, HIGH);  // Rojo autos encendido
digitalWrite(LED_5, LOW);   // Rojo peatones apagado
digitalWrite(LED_4, HIGH);  // Verde peatones encendido (fijo)
delay(3000); // Encendido fijo por 3 segundos

// Parpadear luz verde peatones por 2 segundos
// Hacemos un bucle para parpadear durante 2 segundos
unsigned long startTime = millis();  // Almacenamos el tiempo de inicio
while (millis() - startTime < 2000) { // 2000 ms = 2 segundos
    digitalWrite(LED_4, LOW);   // Apagar el LED
    delay(250);                  // Esperar 250 ms
    digitalWrite(LED_4, HIGH);  // Encender el LED
    delay(250);                  // Esperar 250 ms
}


  //  Fase 4: Rojo autos, rojo peatones (tiempo intermedio)
  digitalWrite(LED_4, LOW);   // Verde peatones apagado
  digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  delay(2000); // 2 segundos
}
<img width="1472" height="780" alt="image" src="https://github.com/user-attachments/assets/f7c64c19-e7be-45ef-bf90-6b96c7b8964a" />



#### EJ 6: Elipse Interactivo: controlar un circulo en Processing mediante un potenciometro conectado a un Arduino UNO.
Código de Arduino:
```js
unsigned int ADCValue;
void setup(){
    Serial.begin(9600);
}

void loop(){

 int val = analogRead(0);
   val = map(val, 0, 300, 0, 255);
    Serial.println(val);
delay(50);
}


Código de Processing:

import processing.serial.*;

Serial myPort;  // Crear objeto de la clase Serial
static String val;    // Datos recibidos desde el puerto serial
int sensorVal = 0;

void setup()
{
  background(0); 
  //fullScreen(P3D);
   size(1080, 720);
   noStroke();
  noFill();
  String portName = "COM3";// Cambia el número (en este caso) para que coincida con el puerto correspondiente conectado a tu Arduino. 

  //myPort = new Serial(this, "/dev/cu.usbmodem1101", 9600);
  myPort = new Serial(this, Serial.list()[0], 9600);

}

void draw()
{
  if ( myPort.available() > 0) {  // Si hay datos disponibles,
  val = myPort.readStringUntil('\n'); 
  try {
   sensorVal = Integer.valueOf(val.trim());
  }
  catch(Exception e) {
  ;
  }
  println(sensorVal); // léelos y guárdalos en vals!
  }  
 //background(0);
  // Escala el valor de mouseX de 0 a 640 a un rango entre 0 y 175
  float c = map(sensorVal, 0, width, 0, 400);
  // Escala el valor de mouseX de 0 a 640 a un rango entre 40 y 300
  float d = map(sensorVal, 0, width, 40,500);
  fill(255, c, 0);
  ellipse(width/2, height/2, d, d);   
}


```
<img width="1218" height="572" alt="image" src="https://github.com/user-attachments/assets/10bb68c0-1af1-451b-aaa6-e333c89d41c2" />

<img width="1898" height="720" alt="image" src="https://github.com/user-attachments/assets/700306c2-850e-47d1-a771-677ef5eba25e" />



#### Boton con potenciometro

```js
int buttonPin = 2;       // Pin del botón
int potPin = A0;         // Pin del potenciómetro
int buttonState = 0;

void setup() {
  pinMode(buttonPin, INPUT_PULLUP); // Botón con resistencia interna
  Serial.begin(9600);
}

void loop() {
  buttonState = digitalRead(buttonPin);

  if (buttonState == HIGH) {   // Botón presionado
    int potValue = analogRead(potPin);   // 0 - 1023
    Serial.print("BTN,");     // etiqueta para Processing
    Serial.println(potValue); // mando el valor junto con el evento
    delay(200);               // debounce simple
  }
}
```
processing:

import processing.serial.*;

Serial myPort;
ArrayList<CircleData> circles; 

void setup() {
  size(1200, 720);
  background(0);
  
  // Ajusta el puerto según tu Arduino
  println(Serial.list());
  //myPort = new Serial(this, "/dev/cu.usbmodem1101", 9600);
  myPort = new Serial(this, Serial.list()[0], 9600);
  
  circles = new ArrayList<CircleData>();
}

void draw() {
  //background(0);
  
  // Dibujar todos los círculos guardados
  //fill(0, 150, 255);
  //noStroke();
  fill(0, 0, 0);
  stroke(255, 0, 0);
  for (CircleData c : circles) {
    ellipse(c.x, c.y, c.size, c.size);
  }
  
  // Leer datos de Arduino
  if (myPort.available() > 0) {
    String val = myPort.readStringUntil('\n');
    if (val != null) {
      val = trim(val);
      if (val.startsWith("BTN")) {
        // Extraer el valor del potenciómetro
        String[] parts = split(val, ',');
        if (parts.length == 2) {
          float potVal = float(parts[1]);
          float circleSize = map(potVal, 0, 1023, 10, 100); // tamaño 10-100 px
          circles.add(new CircleData(random(width), random(height), circleSize));
        }
      }
    }
  }
}

// Clase para guardar datos de cada círculo
class CircleData {
  float x, y, size;
  CircleData(float x, float y, float size) {
    this.x = x;
    this.y = y;
    this.size = size;
  }
}
```


#### Ejercicio n°10 ejercicio a eleccion: Simon Dice 

// Pines para los LEDs
int ledVerde = 2;
int ledAmarillo = 3;
int ledRojo = 4;
int ledAzul = 5;

// Pin para el buzzer
int buzzer = 6;

// Pin para LED de estado
int ledEstado = 13;

// Variables del juego
int secuencia[100];
int nivel = 1;
int velocidad = 500;
bool juegoActivo = false;

// Tonos para cada color
int tonoVerde = 262;     // DO
int tonoAmarillo = 294;  // RE
int tonoRojo = 330;      // MI
int tonoAzul = 349;      // FA

void setup() {
  // Configurar pines de LEDs como salida
  pinMode(ledVerde, OUTPUT);
  pinMode(ledAmarillo, OUTPUT);
  pinMode(ledRojo, OUTPUT);
  pinMode(ledAzul, OUTPUT);
  pinMode(ledEstado, OUTPUT);
  pinMode(buzzer, OUTPUT);
  
  // Iniciar comunicación serial
  Serial.begin(9600);
  
  // Mostrar instrucciones
  mostrarInstrucciones();
  
  // Inicializar semilla aleatoria
  randomSeed(analogRead(0));
  
  // Secuencia de inicio
  secuenciaInicio();
}

void loop() {
  // Si el juego no está activo, esperar a que presionen 's' para empezar
  if (!juegoActivo) {
    if (Serial.available() > 0) {
      char tecla = Serial.read();
      if (tecla == 's' || tecla == 'S') {
        iniciarJuego();
      }
    }
    return;
  }
  
  // Juego principal
  jugarNivel();
}

void mostrarInstrucciones() {
  Serial.println("🎮 SIMON DICE - CON MONITOR SERIAL 🎮");
  Serial.println("======================================");
  Serial.println("INSTRUCCIONES:");
  Serial.println("1 - LED Verde   (DO)");
  Serial.println("2 - LED Amarillo (RE)"); 
  Serial.println("3 - LED Rojo    (MI)");
  Serial.println("4 - LED Azul    (FA)");
  Serial.println();
  Serial.println("Presiona 's' para COMENZAR");
  Serial.println("======================================");
}

void secuenciaInicio() {
  Serial.println("Inicializando juego...");
  
  // Secuencia de bienvenida
  for (int i = 0; i < 3; i++) {
    digitalWrite(ledEstado, HIGH);
    tone(buzzer, 523, 100); // DO agudo
    delay(150);
    digitalWrite(ledEstado, LOW);
    delay(150);
  }
  
  // Mostrar todos los colores disponibles
  Serial.println("Colores disponibles:");
  activarLedYTono(ledVerde, tonoVerde, 300);
  Serial.println("1 - Verde (DO)");
  activarLedYTono(ledAmarillo, tonoAmarillo, 300);
  Serial.println("2 - Amarillo (RE)");
  activarLedYTono(ledRojo, tonoRojo, 300);
  Serial.println("3 - Rojo (MI)");
  activarLedYTono(ledAzul, tonoAzul, 300);
  Serial.println("4 - Azul (FA)");
  
  Serial.println("\n✅ Listo! Presiona 's' para comenzar");
}

void iniciarJuego() {
  juegoActivo = true;
  nivel = 1;
  velocidad = 500;
  
  // Limpiar secuencia anterior
  for (int i = 0; i < 100; i++) {
    secuencia[i] = 0;
  }
  
  Serial.println("\n🎯 ¡JUGANDO! 🎯");
  Serial.println("================");
  
  // Indicar inicio del juego
  for (int i = 0; i < 2; i++) {
    digitalWrite(ledEstado, HIGH);
    tone(buzzer, 784, 200); // SOL agudo
    delay(250);
    digitalWrite(ledEstado, LOW);
    delay(250);
  }
  
  delay(1000);
}

void jugarNivel() {
  // Agregar nuevo color a la secuencia
  secuencia[nivel - 1] = random(1, 5); // 1-4
  
  // Mostrar información del nivel
  Serial.println();
  Serial.print("🎲 NIVEL ");
  Serial.println(nivel);
  Serial.print("Secuencia: ");
  
  // Mostrar secuencia completa
  digitalWrite(ledEstado, HIGH);
  delay(500);
  digitalWrite(ledEstado, LOW);
  delay(500);
  
  for (int i = 0; i < nivel; i++) {
    Serial.print(secuencia[i]);
    Serial.print(" ");
    mostrarColor(secuencia[i]);
    delay(velocidad / 2);
  }
  
  Serial.println();
  Serial.println("⏰ Tu turno! Repite la secuencia...");
  
  // Leer respuesta del jugador
  for (int i = 0; i < nivel; i++) {
    int colorPresionado = esperarTecla();
    
    if (colorPresionado != secuencia[i]) {
      gameOver();
      return;
    }
    
    // Feedback visual y sonoro correcto
    activarLedYTono(obtenerLed(colorPresionado), obtenerTono(colorPresionado), 150);
  }
  
  // Nivel completado
  nivelCompletado();
}

int esperarTecla() {
  while (true) {
    if (Serial.available() > 0) {
      char tecla = Serial.read();
      
      switch(tecla) {
        case '1':
          activarLedYTono(ledVerde, tonoVerde, 200);
          Serial.print("✅ Verde ");
          return 1;
        case '2':
          activarLedYTono(ledAmarillo, tonoAmarillo, 200);
          Serial.print("✅ Amarillo ");
          return 2;
        case '3':
          activarLedYTono(ledRojo, tonoRojo, 200);
          Serial.print("✅ Rojo ");
          return 3;
        case '4':
          activarLedYTono(ledAzul, tonoAzul, 200);
          Serial.print("✅ Azul ");
          return 4;
        default:
          Serial.println("❌ Tecla inválida! Usa 1,2,3,4");
          break;
      }
    }
    delay(10);
  }
}

void mostrarColor(int color) {
  switch (color) {
    case 1: // Verde
      activarLedYTono(ledVerde, tonoVerde, velocidad);
      break;
    case 2: // Amarillo
      activarLedYTono(ledAmarillo, tonoAmarillo, velocidad);
      break;
    case 3: // Rojo
      activarLedYTono(ledRojo, tonoRojo, velocidad);
      break;
    case 4: // Azul
      activarLedYTono(ledAzul, tonoAzul, velocidad);
      break;
  }
}

void activarLedYTono(int led, int frecuencia, int duracion) {
  digitalWrite(led, HIGH);
  tone(buzzer, frecuencia, duracion);
  delay(duracion);
  digitalWrite(led, LOW);
  delay(50);
}

int obtenerLed(int color) {
  switch (color) {
    case 1: return ledVerde;
    case 2: return ledAmarillo;
    case 3: return ledRojo;
    case 4: return ledAzul;
    default: return ledVerde;
  }
}

int obtenerTono(int color) {
  switch (color) {
    case 1: return tonoVerde;
    case 2: return tonoAmarillo;
    case 3: return tonoRojo;
    case 4: return tonoAzul;
    default: return tonoVerde;
  }
}

void nivelCompletado() {
  // Aumentar dificultad
  nivel++;
  if (velocidad > 200) {
    velocidad -= 20;
  }
  
  // Celebrar nivel completado
  Serial.println();
  Serial.println("🎉 ¡NIVEL COMPLETADO!");
  Serial.print("🔜 Siguiente nivel: ");
  Serial.println(nivel);
  Serial.print("⚡ Velocidad: ");
  Serial.println(velocidad);
  
  for (int i = 0; i < 3; i++) {
    digitalWrite(ledEstado, HIGH);
    tone(buzzer, 659, 100); // MI agudo
    delay(120);
    digitalWrite(ledEstado, LOW);
    delay(120);
  }
  
  delay(1000);
}

void gameOver() {
  juegoActivo = false;
  
  Serial.println();
  Serial.println("💀 💀 💀 GAME OVER 💀 💀 💀");
  Serial.print("🏆 Puntuación final: NIVEL ");
  Serial.println(nivel - 1);
  Serial.println("================================");
  
  // Secuencia de game over
  for (int i = 0; i < 5; i++) {
    digitalWrite(ledVerde, HIGH);
    digitalWrite(ledAmarillo, HIGH);
    digitalWrite(ledRojo, HIGH);
    digitalWrite(ledAzul, HIGH);
    tone(buzzer, 196, 300); // SOL grave
    delay(300);
    digitalWrite(ledVerde, LOW);
    digitalWrite(ledAmarillo, LOW);
    digitalWrite(ledRojo, LOW);
    digitalWrite(ledAzul, LOW);
    delay(200);
  }
  
  // Mostrar puntuación final con parpadeos
  Serial.print("⭐ Puntuación (parpadeos): ");
  Serial.println(nivel - 1);
  
  for (int i = 0; i < nivel - 1; i++) {
    digitalWrite(ledEstado, HIGH);
    delay(400);
    digitalWrite(ledEstado, LOW);
    delay(400);
  }
  
  Serial.println();
  Serial.println("🔄 Presiona 's' para jugar otra vez");
  Serial.println("====================================");
  
  delay(2000);
}
```
<img width="752" height="731" alt="image" src="https://github.com/user-attachments/assets/418429b1-4b1d-4de0-96dd-dbe23453ee47" />
