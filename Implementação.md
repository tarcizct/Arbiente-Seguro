## Teste Individual

O primeiro passo da implementação do projeto se deu por testar individualmente cada um dos componentes necessários, sendo eles o Buzzer, MQ-135, Aplicativo Blinky em conexão com a ESP32.

## Buzzer

A conexão feita está abaixo, com um resistor de 1.5kΩ:
<p align="center">
  <img src="https://github.com/user-attachments/assets/fd919fd7-ff90-482f-af44-bba58c5fedf3">
</p>
<p align="center">(Figura do ESP32 montado com o Buzzer).</p>

Código de Teste:
<p align="center">
  <img src="https://github.com/user-attachments/assets/c30e43ef-11ce-428a-9df8-f7bbdf282f50">
</p>
<p align="center">(Figura do código para o teste do Buzzer).</p>

O resultado nos forneceu um som extremamente baixo, logo foi realizado a troca por um resistor de 600Ω para a melhora no som de alarme.


## MQ-135

A montagem se deu pela seguinte lógica:

<p align="center">
  <img src="https://github.com/user-attachments/assets/cc2a7bd8-fdc7-4a49-b214-908aaede3f9c">
</p>
<p align="center">(Figura do ESP32 montado com o sensor MQ-135).</p>

Código de Teste:

<p align="center">
  <img src="https://github.com/user-attachments/assets/88c837b2-d2ec-4b46-a7d4-88b45fa2e156">
</p>
<p align="center">
  <img src="https://github.com/user-attachments/assets/65f0db86-2164-4efc-b575-b66555682046">
</p>
<p align="center">(Figura do Código do Sensor MQ-135).</p>

E o resultado serial foi: 

<p align="center">
  <img src="https://github.com/user-attachments/assets/38839b0e-5e6c-4cc9-9860-e93af85b6ed7">
</p>
<p align="center">(Figura resultado serial lido pelo sensor MQ-135).</p>

O funcionamento do sensor se deu corretamente, foi testado em um ambiente controlado com um pouco de fumaça (CO2) possibilitando ver os valores analógicos sendo alterados.

## Blynk

Seguiu-se o passo a passo do blog (hackster.io) para realizar esse teste. A montagem do circuito foi exatamente a mesma que no teste do MQ-135, a diferença se dá somente no código: 

<p align="center">
  <img src="https://github.com/user-attachments/assets/acfbed2d-520a-41e6-bbec-a96d40b02877">
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/894375a4-ad77-4c3f-a2e9-5646c2c6e253">
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/aa74296a-bfd1-43ff-ae91-e6b8c917e27d">
</p>

E o resultado no aplicativo web/celularde foi: 

<p align="center">
  <img src="https://github.com/user-attachments/assets/2374f311-c74b-4bfc-b227-c5c5c983491d">
</p>

Apenas desconsiderando os valores extremamente altos por conta dos cálculos, que foram ajustados posteriormente, houve um resultado satisfatório para o funcionamento de todo o sistema.

Segundo a Vaisala, quando o ppm de co2 chegar a 5000, há um risco para o ser humano, logo a sirene começará a soar e ao mesmo tempo irá encaminhar um popup no aplicativo de celular e/ou pelo aplicativo web, irá indicar o perigo na tela.

<p align="center">
  <img src="https://github.com/user-attachments/assets/d913e7e0-1cb5-4356-9605-fbee8db292f6">
</p>

## Projeto Resultante

Após correções, foi montado o projeto resultante, com integração entre Blynk, MQ-135 e Buzzer, para que em detecção de gases tóxicos, seja ativado a sirene do buzzer e também apareça um sinal visual no aplicativo. 

<p align="center">
  <img src="https://github.com/user-attachments/assets/cc36eb5b-ad3a-4f69-a236-0e5272c9884b">
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/caf0b862-d945-4e26-bb9d-c31c9414778d">
</p>

## Codigo
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
