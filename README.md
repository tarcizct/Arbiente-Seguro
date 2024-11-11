# Arbiente-Seguro

Instituto Federal de Santa Catarina - *Campus* Florianópolis
Departamento Acadêmico de Eletrônica
Curso de Engenharia Eletrônica

Projetistas

* Leandro Luiz Schoninger Filho - <leandro.lsf@aluno.ifsc.edu.br>
* Tarcísio Zanchetta - <tarcisio.z@aluno.ifsc.edu.br>


Com o aumento da frequência do detrimento da qualidade do ar por
conta dos problemas ecológicos cada vez mais preocupantes, a saúde e o
bem-estar das pessoas estão cada vez mais avariadas, com falta de
informação sobre como lidar com cada problema, e principalmente, saber o que
exatamente está o afetando, a necessidade de um produto que possa auxiliar
acaba se tornando essencial.

O objetivo é desenvolver um aplicativo que se comunica com um Arduino
com sensor de qualidade do ar. O sensor captará todas as nuances e gases
tóxicos, para os seres vivos, e então no aplicativo apresentará os avisos e
como lidar com cada gás quando acima do aceitável. Um aplicativo
extremamente interativo, com informações para cada caso é o essencial para
que o usuário possa manter-se saudável em ambientes desafiadores.
O interesse com a aplicação desse sensor vai desde a aplicação numa
cozinha industrial, até na análise do ar externo ou mesmo laboratorial/ambiente
fechado com presença de gases nocivos à saúde


<p align="center">
  <img src="https://github.com/user-attachments/assets/f3a6f94a-fe15-46d0-91bb-25d809eb9a3f">
</p>


# Design

  Abaixo destaca-se os componentes e os esboços esquemáticos necessários para a montagem do projeto.

## Arduino Uno R3

  Microcontrolador com chip ATmega328p, que possui entradas e saídas digitais e analógicas para integração de sensores e módulos. Além de sua fácil programação e facilidade de uso, possui um preço acessível, o que torna extremamente poderoso e ideal para projetar.

<p align="center">
  <img src="https://github.com/user-attachments/assets/58e84fa7-da44-4f20-aa4a-aa0d4f614356">
</p>
<p align="center">(Figura do Arduino Uno R3).</p>


## Módulo Bluetooth HC-05

Módulo para o Arduino que o permite enviar e receber sinais via bluetooth. Possui uma configuração simples e com um preço baixo. Com alcance de 10 metros, tornando assim útil para pequenos ambientes a serem monitorados.

![image](https://github.com/user-attachments/assets/e5673005-e40a-4f9e-9864-4adf0303e5ab)

(Figura ilustrativa do Módulo Bluetooth HC-05)


Modelo de montagem do módulo Bluetooth para envio de dados para o App no celular disponibilizado pelo site MakerHero:

![image](https://github.com/user-attachments/assets/4f73ba83-8e0a-4c6d-9243-ca6956771557)

(Figura do modelo de funcionamento do HC-05 como modo Mestre)


## Sensor MQ-135

Sensor compatível com o Arduino, o qual é capaz de detectar a presença e/ou concentração de certos gases, tais como amônia, dióxido de carbono, benzeno, óxido nítrico, fumaça ou álcool. Após a detecção de um dos gases anteriores, envia um sinal HIGH para a entrada analógica do Arduino. 


![image](https://github.com/user-attachments/assets/d1641f76-6be4-4ef6-9b02-4e36e0524786)

(Figura do sensor MQ-135)


Modelo de montagem do sistema com o sensor MQ-135 disponível no tinkercad:

![image](https://github.com/user-attachments/assets/c5d18167-9eb6-4c59-a30e-511d01eaeacb)

(Figura do modelo de funcionamento do sensor MQ-135)


## MIT AppInventor

Site para criação de aplicativos de celular que possui uma integração facilitada com o microcontrolador Arduino e para o módulo HC-05.

![image](https://github.com/user-attachments/assets/373f85d0-1953-4447-ada9-faf233437bab)

(Figura de exemplo genérico do app)


![image](https://github.com/user-attachments/assets/e01d0f1d-46af-472e-aed8-f8e7cb80e46e)

(Figura de exemplo de programação do app conectar ao bluetooth do módulo HC-05 disponível pelo canal no youtube Brino Robótica Educacional)


# Planta Resultante

![image](https://github.com/user-attachments/assets/b1e0c797-3024-4e38-9362-ce7e15af6e52)
Esquemático Arbiente-Seguro.



# Referências
* https://www.makerhero.com/blog/tutorial-arduino-bluetooth-hc-05-mestre/
* https://www.usinainfo.com.br/sensor-de-gas-arduino/sensor-de-co2-mh-z14a-infravermelho-cabo-8348.html
* https://www.tinkercad.com/things/iQq2Xw76GUK-copy-of-detector-de-fumaca/editel?returnTo=https%3A%2F%2Fwww.tinkercad.com%2Fdashboard
* https://www.youtube.com/@brino_edu
