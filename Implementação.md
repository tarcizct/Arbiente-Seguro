## Teste Individual

O primeiro passo da implementação do projeto se deu por individualmente fazer funcionar cada um dos componentes necessários, sendo eles Buzzer, MQ-135, Aplicativo Blinky.

## Buzzer

No primeiro teste foi feito com o Buzzer. A conexão feita está abaixo, com um resistor de 1.5kΩ:
<p align="center">
  <img src="https://github.com/user-attachments/assets/fd919fd7-ff90-482f-af44-bba58c5fedf3">
</p>
<p align="center">(Figura do ESP32 montado com o Buzzer).</p>

E o código para teste foi:
<p align="center">
  <img src="https://github.com/user-attachments/assets/c30e43ef-11ce-428a-9df8-f7bbdf282f50">
</p>
<p align="center">(Figura do código para o teste do Buzzer).</p>
O resultado se deu em um som extremamente baixo, utilizando um resistor de 300Ω se dará um som mais alto e suficiente para o projeto.


## MQ-135

O segundo teste foi para a leitura serial do sensor de gás MQ-135, a montagem se deu pela seguinte lógica:
<p align="center">
  <img src="https://github.com/user-attachments/assets/cc2a7bd8-fdc7-4a49-b214-908aaede3f9c">
</p>
<p align="center">(Figura do ESP32 montado com o sensor MQ-135).</p>

E o código para o teste foi:
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

Com isso o funcionamento do sensor se deu corretamente, foi testado com um pouco de fumaça controlada para ver os valores analógicos serem alterados.

## Blynk

O último teste individual foi do aplicativo Blynk. Seguiu-se o passo a passo do blog (hackster.io) para realizar esse teste. A montagem do circuito foi exatamente a mesma que no teste do MQ-135, a diferença se dá somente no código agora: 

<p align="center">
  <img src="https://github.com/user-attachments/assets/acfbed2d-520a-41e6-bbec-a96d40b02877">
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/891d565b-f135-4874-91e1-3631d09ff509)">
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/894375a4-ad77-4c3f-a2e9-5646c2c6e253">
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/aa74296a-bfd1-43ff-ae91-e6b8c917e27d">
</p>

E o resultado no aplicativo de celular da Blynk foi: 

<p align="center">
  <img src="https://github.com/user-attachments/assets/2374f311-c74b-4bfc-b227-c5c5c983491d">
</p>

Apenas desconsiderando os valores extremamente altos por conta dos cálculos, que serão ajustados em breve, houve um resultado satisfatório para o funcionamento de todo o sistema.

Segundo a Vaisala, quando o ppm de co2 chegar a 5000, há um risco para o ser humano, logo a sirene começará a soar.
<p align="center">
  <img src="https://github.com/user-attachments/assets/d913e7e0-1cb5-4356-9605-fbee8db292f6">
</p>

