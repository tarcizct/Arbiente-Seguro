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
