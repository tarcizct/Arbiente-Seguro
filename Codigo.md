#include <Wire.h>
#include <WiFi.h>
#include <PubSubClient.h>

int state=0;
int a=0;
int b=0;

// Configurações Wi-Fi
const char *ssid = "lpae_wifi";
const char *password = "esp-8266";

// Configurações MQTT
const char *mqtt_broker = "192.168.1.2";
const char *topic = "v1/devices/me/telemetry";
const int mqtt_port = 1883;
const char *mqtt_user = "HPQZjD1z1oA5Ns6fO1jd";
const char *mqtt_password = "";

WiFiClient espClient;
PubSubClient client(espClient);

// Função para conectar ao WiFi
void setup_wifi() {
    Serial.println("Conectando ao WiFi...");
    WiFi.begin(ssid, password);
    while (WiFi.status() != WL_CONNECTED) {
        delay(500);
        Serial.print(".");
    }
    Serial.println("\nWiFi conectado!");
}

// Função para conectar ao MQTT
void reconnect() {
    while (!client.connected()) {
        Serial.print("Conectando ao MQTT...");
        if (client.connect("ESP32Client", mqtt_user, mqtt_password)) {
            Serial.println("Conectado ao MQTT!");
            client.subscribe(topic);
        } else {
            Serial.print("Falha na conexão, rc=");
            Serial.println(client.state());
            delay(2000);
        }
    }
}


// Função para enviar mensagens JSON ao MQTT
void sendMessage(const char *sensor, const char *assunto, const char *valor) {
    char buffer[256];
    snprintf(buffer, sizeof(buffer), "{\"sensor\": \"%s\", \"assunto\": \"%s\", \"valor\": \"%s\"}", sensor, assunto, valor);
    client.publish(topic,buffer);
}

void setup() {
  // put your setup code here, to run once:
  pinMode(35,INPUT);
  pinMode(34,INPUT);
      // Configura WiFi e MQTT
    setup_wifi();
    client.setServer(mqtt_broker, mqtt_port);
    client.setCallback([](char *topic, byte *payload, unsigned int length) {
        Serial.print("Mensagem recebida no tópico: ");
        Serial.println(topic);
    });

}

void loop() {

   // Mantém a conexão MQTT
    if (!client.connected()) {
        reconnect();
    }
    client.loop();

  Serial.begin(115200);  
  // put your main code here, to run repeatedly:
  b=digitalRead(35);
  a=digitalRead(34);
  Serial.print("A: ");
  Serial.println(a);
  Serial.print("B: ");
  Serial.println(b);
  delay(5000);

  if(a==0&&b==0){
    state=0;
    Serial.println("Ar sem poluicao");
  }else if(a==0&&b==1){
    state=1;
    Serial.println("Ar com pouca poluicao");
  }else if(a==1&&b==0){
    state=2;
    Serial.println("Ar com poluicao");
  }else if(a==1&&b==1){
    state=3;
    Serial.println("Ar com muita poluicao");
  }
  char stateValue[8];
  snprintf(stateValue, sizeof(stateValue),"%d",state);
   // Publica a poluição detectada no tópico MQTT
        Serial.printf("State: %s\n", stateValue);
        sendMessage("sensor_de_cor", "temperature", stateValue);
}
