#include <PubSubClient.h>
#include <ESP8266WiFi.h>

const char* ssid = "SSID";      //SSID HERE
const char* password = "pass";  //PASS HERE
char* topic = "topic";          //TOPIC HERE
char* server = "ServerIP";      //BROKER IP HERE
char* message = "";

WiFiClient wifiClient;


void callback(char* topic, byte* message, unsigned int length)
{
  Serial.println((char*) message);
  //Serial.println();   
}
PubSubClient client(server, 1883, callback, wifiClient);


void setup() 
{
  String clientName;
  clientName += "esp8266";
  
  Serial.begin(9600);
  delay(10);  
  WiFi.begin(ssid, password);
  
  while (WiFi.status() != WL_CONNECTED)
  {
    delay(500);
  }
   
  if (client.connect((char*) clientName.c_str()))
  {
    Serial.println("Connected to broker");
  }
  else 
  {
    abort();
  }
  
  client.subscribe(topic); 
 
  if (client.subscribe(topic))
  {
    Serial.println("Subscribed");
  }
}


void loop() 
{
  client.loop();
}
