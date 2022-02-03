# wifiupload

```
#include <Arduino.h>
#include <lionbit.h>
#include <WiFi.h>
#include <ota.h>


const char* ssid = "King-knight";
const char* password = "nrl1633n";


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
  ota_start();
  Serial.print("IP address: ");
  Serial.println(WiFi.localIP());

}

void loop() {
  ota_run();
 
}

```
