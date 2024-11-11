# Arbiente-Seguro
Projeto de sensor de qualidade do ar PI2-IFSC

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

# Design
Componentes:
## Arduino Uno R3
Microcontrolador com chip ATmega328p, que possui entradas e saídas digitais e analógicas para integração de sensores e módulos. Além de sua fácil programação e facilidade de uso, possui um preço acessível, o que torna extremamente poderoso e ideal para projetar.

(Figura do Arduino Uno R3)
##Módulo Bluetooth HC-05
Módulo para o Arduino que o permite enviar e receber sinais via bluetooth. Possui uma configuração simples e com um preço baixo. Com alcance de 10 metros, tornando assim útil para pequenos ambientes a serem monitorados.

(Figura ilustrativa do Módulo Bluetooth HC-05)
Modelo de montagem do módulo Bluetooth para envio de dados para o App no celular disponibilizado pelo site MakerHero:

(Figura do modelo de funcionamento do HC-05 como modo Mestre)
## Sensor MQ-135
Sensor compatível com o Arduino, o qual é capaz de detectar a presença e/ou concentração de certos gases, tais como amônia, dióxido de carbono, benzeno, óxido nítrico, fumaça ou álcool. Após a detecção de um dos gases anteriores, envia um sinal HIGH para a entrada analógica do Arduino. 

(Figura do sensor MQ-135)
Modelo de montagem do sistema com o sensor MQ-135 disponível no tinkercad:

(Figura do modelo de funcionamento do sensor MQ-135)

## MIT AppInventor
Site para criação de aplicativos de celular que possui uma integração facilitada com o microcontrolador Arduino e para o módulo HC-05.


(Figura de exemplo genérico do app)

(Figura de exemplo de programação do app conectar ao bluetooth do módulo HC-05 disponível pelo canal no youtube Brino Robótica Educacional)


https://docs.google.com/document/d/1-M7JsuPMnNRBw-6t0dHKmxgBMf4rZE9k/edit?usp=drivesdk&ouid=102812544872728031002&rtpof=true&sd=true

![Sem título](https://github.com/user-attachments/assets/4fa16424-ec9c-40f0-8e05-63f5aa7ada2d)


![image](https://github.com/user-attachments/assets/b1e0c797-3024-4e38-9362-ce7e15af6e52)
Esquemático Arbiente-Seguro.



REFERENCIAS

https://www.makerhero.com/blog/tutorial-modulo-bluetooth-com-arduino/
https://www.usinainfo.com.br/sensor-de-gas-arduino/sensor-de-co2-mh-z14a-infravermelho-cabo-8348.html
