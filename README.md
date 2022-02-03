# WiFi Upload without Serial COM port 

```
#include <Arduino.h>
#include <lionbit.h>
#include <WiFi.h>
#include <ota.h>


const char* ssid = "..........."; /* WiFi SSID */
const char* password = "........."; /* WiFi password */


void setup() {
 
  Serial.begin(9600);
  Serial.println("Booting");
  WiFi.mode(WIFI_STA);
  WiFi.begin(ssid, password);
  while (WiFi.waitForConnectResult() != WL_CONNECTED) {
    Serial.println("Connection Failed! Rebooting...");
    delay(5000);
    ESP.restart();
  }
  ota_start(); /* WiFi upload setup */
  Serial.print("IP address: ");
  Serial.println(WiFi.localIP());

}

void loop() {
  ota_run(); /* Always need to run in main looop */
 
}

```
