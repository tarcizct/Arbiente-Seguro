##Código modelo LT1:

#define BLYNK_TEMPLATE_ID "TMPL2Ie612Qwl"
#define BLYNK_TEMPLATE_NAME "Arbiente"
#define BLYNK_AUTH_TOKEN "2z_szXtUV4TA2BOkFwxElFVVmNws8u00"

#include <MQ135.h>
#include <WiFi.h>
#include <BlynkSimpleEsp32.h>

const int PINO_BUZZER = 5; // Pino 5 conectado ao buzzer
const int MQ135pin = A0;        // Define the pin for MQ135 sensor
const int ledBadQuality = 25;
const int SMOKE_THRESHOLD = 10; // Adjust this threshold based on your application
char ssid[] = "AndroidAP_3780"; // Replace with your WiFi SSID
char pass[] = "12345678";    // Replace with your WiFi password
bool isRunning = false; // Flag to track if the system is running

void setup() {
  Serial.begin(115200);
  Blynk.begin(BLYNK_AUTH_TOKEN, ssid, pass);
  pinMode(PINO_BUZZER, OUTPUT); // Define o PINO do buzzer como saída
  // Initialize Blynk chart
  Blynk.virtualWrite(V0, "CLEARDATA");
  Blynk.virtualWrite(V1, "CLEARDATA");
  Blynk.virtualWrite(V2, "CLEARDATA");
  Blynk.virtualWrite(V3, "CLEARDATA");
  Blynk.virtualWrite(V4, "CLEARDATA");
  Blynk.virtualWrite(V5, "CLEARDATA");
  Blynk.virtualWrite(V6, "CLEARDATA");
  Blynk.virtualWrite(V7, "CLEARDATA");
  analogReadResolution(10); 
}

void loop() {
  Blynk.run();

  if (isRunning) {
    /*MQ135 Gas_Sensor = MQ135(MQ135pin);
   // float V_out = rawValue *(V_Ref/1024);
    //float Rs = Rl*((V_Ref - V_out) / V_out);
    float ppm = Gas_Sensor.getPPM();
    float rzero = Gas_Sensor.getRZero();
    Serial.println(rzero);
    // Calculate CO2, CO, and other gases
    float ppm = 1.0 / (0.03588 * pow(resistance, 1.336));
    float co = ppm / 2.2;        // Approximate conversion from PPM to CO
    float methane = ppm / 2.7;    // Approximate conversion from PPM to CH4
    float ammonia = ppm / 3.6;    // Approximate conversion from PPM to NH3
    */

    float rs=(3.3/(analogRead(A0)*(3.3/1023))-1)*10000;
    float rzero = 67.0;
    float ppm = rs/rzero;
    float co = ppm / 2.2;        // Approximate conversion from PPM to CO
    float methane = ppm / 2.7;    // Approximate conversion from PPM to CH4
    float ammonia = ppm / 3.6;    // Approximate conversion from PPM to NH3
    
    //em caso de concentração de CO2 maior que 5000, ou CO maior que 50 ou metano maior que 50 ligar sirene de alerta.
    if(ppm<150||co>400||methane>400){
      digitalWrite(PINO_BUZZER, HIGH); // Ligar o buzzer
      Blynk.virtualWrite(V7, 1);
    }else{
    delay(1000);
      digitalWrite(PINO_BUZZER, LOW); // Desligar o buzzer
      Blynk.virtualWrite(V7, 0);
    }
    // Debugging: Print values to Serial Monitor
    //Serial.print("Raw Analog Value: ");
    //Serial.println(rawValue);
    //Serial.print("Voltage: ");
   // Serial.println(voltage, 2);    // Print with 2 decimal places
   // Serial.print("Sensor Resistance: ");
   // Serial.println(resistance, 2); // Print with 2 decimal places
    Serial.print("CO2 PPM: ");
    Serial.print(ppm, 2);        // Print with 2 decimal places
    Serial.print("\t CO: ");
    Serial.print(co, 2);         // Print with 2 decimal places
    Serial.print("\t Methane (CH4) PPM: ");
    Serial.print(methane, 2);    // Print with 2 decimal places
    Serial.print("\t Ammonia (NH3) PPM: ");
    Serial.println(ammonia, 2);    // Print with 2 decimal places

    // Display CO2, CO, and other gases on Blynk app
    Blynk.virtualWrite(V0, ppm);
    Blynk.virtualWrite(V1, co);
    Blynk.virtualWrite(V2, methane);
    Blynk.virtualWrite(V3, ammonia);
   // Blynk.virtualWrite(V4, voltage);
   // Blynk.virtualWrite(V5, resistance);

    // Add CO2 value to Blynk chart

   /* // Check CO2 levels and control LED
    if (co > SMOKE_THRESHOLD) {
      Blynk.virtualWrite(V10, 1);
      digitalWrite(ledBadQuality, HIGH);
    } else {
      Blynk.virtualWrite(V10, 0);
      digitalWrite(ledBadQuality, LOW);
    }
*/
    delay(6000); // Adjust the delay based on your application needs
  }
}

BLYNK_CONNECTED() {
  // Your existing code for BLYNK_CONNECTED
  // ...
}

BLYNK_WRITE(V6) {
  int startStopButton = param.asInt();
  if (startStopButton == 1) { // Button is pressed (Start)
    isRunning = true;
  } else { // Button is not pressed (Stop)
    isRunning = false;
    // Reset values or perform any other stop-related actions
    Blynk.virtualWrite(V0, 0); // Reset CO2 value
    Blynk.virtualWrite(V1, 0); // Reset CO value
    Blynk.virtualWrite(V2, 0); // Reset Methane value
    Blynk.virtualWrite(V3, 0); // Reset Ammonia value
    Blynk.virtualWrite(V7, 0); // Reset Ammonia value
   // Blynk.virtualWrite(V4, 0); // Reset another V9 value (adjust as needed)
   // Blynk.virtualWrite(V5, 0); // Turn off LED
    //digitalWrite(ledBadQuality, LOW);
  }
}

##Código modelo LT2:

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
