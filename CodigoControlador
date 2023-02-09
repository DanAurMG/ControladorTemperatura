//Declaración e inicialización de variables a utilizar
float previousX = 186.0;
float x = 0.0;
int ledPinC = 2;
int ledPinF = 0;
int ledPinT = 4;
int sensorPin = A0;
float controlador = 0.0

// Esta función se ejecuta cuando se ejecuta por primera vez el programa y cuando se resetea la placa
void setup() {
  // initialize serial communication at 9600 bits per second:
  Serial.begin(9600);
  pinMode(ledPinC, OUTPUT);
  pinMode(ledPinF, OUTPUT);
  pinMode(ledPinT, OUTPUT);
}

//Función que se ejecutará en loop hasta que se reinicie la placa
void loop() {

  // Leemos e imprimimos en consola la entrada analógica que nos da el PT100
  x = analogRead(sensorPin);
  Serial.println("Lectura analogica");
  Serial.println(x);
  
  //El PT100 es un sensor algo inestable, esta parte es para evitar valores de cero
  if(x < 1.0){
    x = previousX;
  }  else if(x > 1.1){
    previousX = x;
  }
    
  //Condicional para actuar cuando el termistor detecte más de 25 grados  
  if(x > 180.00){    
    digitalWrite(ledPinC, HIGH);
    digitalWrite(ledPinF, LOW);
    digitalWrite(ledPinT, LOW);
    Serial.println("Se encendera el ventilador");      
    
  //Condicional para actuar cuando el termistor detecte más de 13 grados y menos de 24.9
  }else if(x>91.0 && x <  179.0){
    Serial.println("Templado");
    digitalWrite(ledPinF, LOW);
    digitalWrite(ledPinC, LOW);
    digitalWrite(ledPinT, HIGH);
    
    //Condicional para actuar cuando el termistor detecte más de 12.9 grados
  }else if(x < 90.00){
    digitalWrite(ledPinC, LOW);
    digitalWrite(ledPinT, LOW);
    digitalWrite(ledPinF, HIGH);
    Serial.println("Se calentaran los leds");       
  }
  
  //Se procesa la lectura cada 3 segundos
  delay(3000);
}
