# Practica-3-DHT11--CON--LCD
Este repositorio muestra la tercera practica practica del diplomado de como podemos programar una ESP32 con el sensor DHT22 y mostrando el resutado en la LCD.
## INTRODUCCION
### DESCRIPCION
La Esp32 la utilizamos en un entorno de adquision de datos, lo cual en esta practica ocuparemos un sensor (DTH11) para adquirir temperatura y humedad del entorno; Esta practica se desarrollara en el simulador llamado Wokwi (https://wokwi.com/projects/new/esp32).
#### Material Necesario 
WOKWI

Tarjeta ESP 32

Sensor DHT22

LCD 16X2 I2C

##### Instrucciones
Requisitos previos Para realizar la practica de este repositorio se necesita entrar a la plataforma WOKWI.

Instrucciones de preparación de entorno Abrir la terminal de programación y colocar la siguente codigo:

#include "DHTesp.h" #include <LiquidCrystal_I2C.h> #define I2C_ADDR 0x27 #define LCD_COLUMNS 20 #define LCD_LINES 4

const int DHT_PIN = 15;

DHTesp dhtSensor;

LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);

void setup() {

Serial.begin(115200); dhtSensor.setup(DHT_PIN, DHTesp::DHT22); lcd.init(); lcd.backlight();

}

void loop() {

TempAndHumidity data = dhtSensor.getTempAndHumidity(); Serial.println("Temp: " + String(data.temperature, 1) + "°C"); Serial.println("Humidity: " + String(data.humidity, 1) + "%"); Serial.println("---");

lcd.setCursor(0, 0); lcd.print(" Temp: " + String(data.temperature, 1) + "\xDF"+"C "); lcd.setCursor(0, 1); lcd.print(" Humidity: " + String(data.humidity, 1) + "% "); lcd.print("Wokwi Online IoT");

delay(1000); }

*Instalar la libreria de DHT sensor library for ESPx como se muestra en la siguente imagen.
![](https://github.com/ArmandoGl98/Practica-3-DHT11--CON--LCD/blob/main/Captura%20de%20pantalla%202023-12-21%20195253.png) 
*Realizar la conexion de DHT22 con la ESP32 y de la LCD de la siguiente manera
![](https://github.com/ArmandoGl98/Practica-3-DHT11--CON--LCD/blob/main/Captura%20de%20pantalla%202023-12-16%20093427.png)
###### INTRUCCIONES DE OPERACION
Iniciar simulador.
Visualizar los datos en el monitor serial.
Colocar la temperatura y humedad dando doble click al sensor DHT11
 ###### RESULTADOS
 Se veran los datos en la pantalla LCD
 
![](https://github.com/ArmandoGl98/Practica-3-DHT11--CON--LCD/blob/main/Captura%20de%20pantalla%202023-12-21%20195320.png)
