
  ## Conclusão
A fim de otimizar o projeto em sua operação, optou-se por fazer uma mudança no sensor que anteriormente estava sendo usado, o MQ-135 e então o novo escolhido foi o ZP07-MP503. A troca ocorreu em busca de ter uma maior precisão nos valores obtidos pelo sensor, além disso, segundo o datasheet do ZP07-MP503, está informado que a partir dos pinos A e B obtém-se a informação para sem poluição, pouca poluição, poluição e muita poluição, facilitando assim a troca de informação com o sistema para avisar ao usuário.
O aplicativo Blynk também foi alterado, pois era um sistema que possuia um limite de envio de dados para o aplicativo do celular, e também visando uma integração com o sistema [Dashboard ThinkBoard](https://github.com/sooarees/Dashboard-ThingsBoard) no LPAE, foi adicionado o protocolo MQTT de troca de mensagens. 

<p align="center">
  <img src="https://github.com/user-attachments/assets/12b0a7a8-a558-426e-a0ba-ec3365c0448f">
</p>
<p align="center">(Sensor em Alarme através do Dashboard do LPAE).</p>


## Andendo
Foi tentado integração com o sistema LORA (https://github.com/LaporteEng/LoRa_Sensors), entretanto pela falta de tempo, optamos com a equipe não seguir em frente, visto que haveria problemas de integração entre a ESP32 e a comunicação LORA. Insistimos para que futuramente haja tentativa de integração.
