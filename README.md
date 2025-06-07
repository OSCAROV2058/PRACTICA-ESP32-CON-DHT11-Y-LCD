# PRACTICA-ESP32-CON-DHT11-Y-LCD

## Introduccion

### Descripcion

Este repositorio muestra como podemos programar una ESP32 con el sensor DHT11 y una pantalla LCD

## Material necesario

-WOKWI

-Tarjeta ESP32

-Sensor DHT11

-Pantalla LCD (16x2)

## Instrucciones de preparación de entorno

1. Abrir la terminal de programación y colocar la siguente programación:

```
#include "DHTesp.h"
#include <LiquidCrystal_I2C.h>
#define I2C_ADDR    0x27
#define LCD_COLUMNS 20
#define LCD_LINES   4

const int DHT_PIN = 15;

DHTesp dhtSensor;

LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);

void setup() {

  Serial.begin(115200);
  dhtSensor.setup(DHT_PIN, DHTesp::DHT22);
  lcd.init();
  lcd.backlight();

}

void loop() {

 lcd.setCursor(0, 0);
  lcd.print(" DIPLOMADO 5 ");
  lcd.setCursor(0, 1);
  lcd.print(" AUTOMATIZACION ");
delay(2000);
lcd.clear();
 
 lcd.setCursor(0, 0);
  lcd.print(" OSCAR OCAMPO ");
  lcd.setCursor(0, 1);
  lcd.print(" ING. MECANICO ");
delay(2000);
lcd.clear();

lcd.setCursor(0, 0);
  lcd.print(" 07 JUNIO 2025 ");
delay(2000);
lcd.clear();

  TempAndHumidity  data = dhtSensor.getTempAndHumidity();
  Serial.println("Temp: " + String(data.temperature, 1) + "°C");
  Serial.println("Humidity: " + String(data.humidity, 1) + "%");
  Serial.println("---");
  
  lcd.setCursor(0, 0);
  lcd.print("  Temp: " + String(data.temperature, 1) + "\xDF"+"C  ");
  lcd.setCursor(0, 1);
  lcd.print(" Humidity: " + String(data.humidity, 1) + "% ");
  delay(2000);
  lcd.clear();

}
```

2. Instalar la libreria de DHT sensor library for ESPx y LiquidCrystal I2C como se muestra en la siguente imagen.

![](https://github.com/OSCAROV2058/PRACTICA-ESP32-CON-DHT11-Y-LCD/blob/main/image.png?raw=true)

3. Hacer la conexion de DHT11 y LCD con la ESP32 como se muestra en la siguente imagen.

![](https://github.com/OSCAROV2058/PRACTICA-ESP32-CON-DHT11-Y-LCD/blob/main/image%20(1).png?raw=true)


## Instrucciónes de operación

1. Iniciar simulador.

2. Visualizar los datos en el monitor serial. (CURSO, NOMBRE Y CARRERA, FECHA).

3. Colocar la temperatura y humedad dando doble click al sensor DHT11.

## Resultados

Cuando haya funcionado, verás los valores dentro del monitor serial como se muestra en las siguentes imagenes.

![](https://github.com/OSCAROV2058/PRACTICA-ESP32-CON-DHT11-Y-LCD/blob/main/image%20(2).png?raw=true)

![](https://github.com/OSCAROV2058/PRACTICA-ESP32-CON-DHT11-Y-LCD/blob/main/image%20(3).png?raw=true)

![](https://github.com/OSCAROV2058/PRACTICA-ESP32-CON-DHT11-Y-LCD/blob/main/image%20(4).png?raw=true)

![](https://github.com/OSCAROV2058/PRACTICA-ESP32-CON-DHT11-Y-LCD/blob/main/image%20(5).png?raw=true)

## Creditos

Desarrollado por Ing. Oscar Jair Ocampo Villarreal
- ([github](https://github.com/OSCAROV2058))
