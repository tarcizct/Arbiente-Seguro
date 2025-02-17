## Teste Individual modelo LT 1:

O primeiro passo da implementação do projeto se deu por testar individualmente cada um dos componentes necessários, sendo eles o Buzzer, MQ-135, Aplicativo Blinky em conexão com a ESP32, entretanto durante a fase de Operação, tivemopas algumas alterações como do sensor para o ZP07-MP503 e devido a uma melhor otimização, a mudança para o MQTT do Blynk.

## Buzzer (Descontinuado)

A conexão feita está abaixo, com um resistor de 1.2kΩ:
<p align="center">
  <img src="https://github.com/user-attachments/assets/fd919fd7-ff90-482f-af44-bba58c5fedf3">
</p>
<p align="center">(Figura do ESP32 montado com o Buzzer).</p>

## MQ-135 (Descontinuado)

A montagem se deu pela seguinte lógica:

<p align="center">
  <img src="https://github.com/user-attachments/assets/cc2a7bd8-fdc7-4a49-b214-908aaede3f9c">
</p>
<p align="center">(Figura do ESP32 montado com o sensor MQ-135).</p>

## Blynk (Descontinuado)

Seguiu-se o passo a passo do blog (hackster.io) para realizar esse teste. A montagem do circuito foi exatamente a mesma que no teste do MQ-135, a diferença se dá somente no código.

E o resultado no aplicativo web/celular foi: 

<p align="center">
  <img src="https://github.com/user-attachments/assets/2374f311-c74b-4bfc-b227-c5c5c983491d">
</p>

Apenas desconsiderando os valores extremamente altos por conta dos cálculos, que foram ajustados posteriormente, houve um resultado satisfatório para o funcionamento de todo o sistema.

Segundo a Vaisala, quando o ppm de co2 chegar a 5000, há um risco para o ser humano, logo a sirene começará a soar e ao mesmo tempo irá encaminhar um popup no aplicativo de celular e/ou pelo aplicativo web, irá indicar o perigo na tela.

<p align="center">
  <img src="https://github.com/user-attachments/assets/d913e7e0-1cb5-4356-9605-fbee8db292f6">
</p>

## Modelo LT 1 do Projeto:

Primeiro protótipo do projeto, com integração entre Blynk, MQ-135 e o Buzzer, para que em detecção de gases tóxicos, seja ativado a sirene e também apareça um sinal visual no aplicativo. 

<p align="center">
  <img src="https://github.com/user-attachments/assets/caf0b862-d945-4e26-bb9d-c31c9414778d">
</p>

## Modelo LT 2 do Projeto (Final)

Após os testes durante a fase de Operação, fizemos a substituição para o sensor ZP07-MP503, utilizando o protocolo MQTT invés do aplicativo web Blynk e retirando o Buzzer, para um designe mais cleam e melhor integração com o sistema [Dashboard ThinkBoard](https://github.com/sooarees/Dashboard-ThingsBoard) do LPAE.

<p align="center">
  <img src="https://github.com/user-attachments/assets/1a404b50-5a50-4cd2-943c-09c6a6bade1f">
</p>
<p align="center">(Exemplo de funcionamento pelo Arduino).</p>

## Teste Final LT 2

<p align="center">
  <img src="https://github.com/user-attachments/assets/089b33c4-ac8b-464b-9f20-5f48d125534e">
</p>
<p align="center">(ESP32 montado com o sensor ZP07-MP503 em teste).</p>


## Código
https://github.com/tarcizct/Arbiente-Seguro/blob/main/Codigo.md

## Referências

*https://blog-asksensors-com.translate.goog/air-quality-sensor-mq135-cloud-mqtt/?_x_tr_sl=en&_x_tr_tl=pt&_x_tr_hl=pt&_x_tr_pto=tc

*https://forum.arduino.cc/t/how-to-calibrate-an-mq-135-gas-sensor-co2/402038/3

*https://mischianti.org/doit-esp32-dev-kit-v1-high-resolution-pinout-and-specs/

*https://components101-com.translate.goog/sensors/mq135-gas-sensor-for-air-quality?_x_tr_sl=en&_x_tr_tl=pt&_x_tr_hl=pt&_x_tr_pto=tc

*https://www.upesy.com/blogs/tutorials/measure-voltage-on-esp32-with-adc-with-arduino-code?srsltid=AfmBOorrGuhgN4d4wQx16BU-Zwh6bmrTmLYiBWLAlySbDQdTJpkhU0dB#

*https://www.futurlec.com/Datasheet/Sensor/MQ-135.pdf

*https://www.hackster.io/512389/esp32-monitoring-air-quality-with-mq-135-integrated-blynk-77d18b

*https://github.com/GeorgK/MQ135?tab=readme-ov-file#readme

*https://blog.asksensors.com/air-quality-sensor-mq135-cloud-mqtt/

*https://www.winsen-sensor.com/d/files/ZP07-MP503-4.pdf
