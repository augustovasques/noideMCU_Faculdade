# noideMCU_Faculdade

#include <ESP8266WiFi.h> // Importa a Biblioteca ESP8266WiFi
#include <PubSubClient.h> // Importa a Biblioteca PubSubClient
#define TOPICO_SUBSCRIBE "MQTT"     //tópico MQTT de escuta
#define TOPICO_PUBLISH   "MQTT"    //tópico MQTT de envio de informações para Broker
#define TRIGGERPIN D1
#define ECHOPIN    D2

char auth[] = "TXw5yPRCV-QVfWXrqmEXB8YoocXTOhQw";//Autenticação MTTq Cassananda


char ssid[] = "nome de rede";
char pass[] = "senha de rede";


const char* BROKER_MQTT = "https://dashboard.heroku.com/apps"; //URL do broker MQTT que se deseja utilizar
int BROKER_PORT = 8081; // Porta do Broker MQTT Envio de Informações Para o Broker
 
 
//Variáveis e objetos globais
WiFiClient espClient; // Cria o objeto espClient
PubSubClient MQTT(espClient); // Instancia o Cliente MQTT passando o objeto espClient
char EstadoSaida = '0';  //variável que armazena o estado atual da saída
  
//Prototypes
void initSerial();
void initWiFi();
void initMQTT();
void reconectWiFi(); 
void mqtt_callback(char* topic, byte* payload, unsigned int length);
void VerificaConexoesWiFIEMQTT(void);
void InitOutput(void);

void loop()
{
  lcd.clear();
  lcd.print(0, 0, "Distance in cm"); //  ( X: 0-15,  Y: 0-1)
  long duracao, distancia; 
  delayMicroseconds(3); 
  
  digitalWrite(TRIGGERPIN, HIGH);
  delayMicroseconds(12); 
  
  digitalWrite(TRIGGERPIN, LOW);
  duracao = pulseIn(ECHOPIN, HIGH);
  distancia = (duracxao/2) / 29.1;
  Serial.print(distancia);
  Serial.println("Cm");
  BROKER_PORT.run();

  delay(3500);

}
