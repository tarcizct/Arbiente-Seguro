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
fechado com presença de gases nocivos à saúde.


<p align="center">
  <img src="https://github.com/user-attachments/assets/f3a6f94a-fe15-46d0-91bb-25d809eb9a3f">
</p>


# Design

  Abaixo destaca-se os componentes e os esboços esquemáticos necessários para a montagem do projeto.

## Esp32 

  Microcontrolador com processador  Xtensa LX6 dual-core de 32 bits, que possui entradas e saídas digitais e analógicas para integração de sensores e módulos e Wifi incluído. Além de sua fácil programação e facilidade de uso, possui um preço acessível, o que torna extremamente poderoso e ideal para projetar.

<p align="center">
  <img src="https://github.com/user-attachments/assets/cd6c5048-c17f-4a36-8223-771e3f3ad8f3">
</p>
<p align="center">(Figura do ESP32).</p>


## Sensor MQ-135

Sensor compatível com o ESP32, o qual é capaz de detectar a presença e/ou concentração de certos gases, tais como amônia, dióxido de carbono, benzeno, óxido nítrico, fumaça ou álcool. Após a detecção de um dos gases anteriores, envia um sinal HIGH para a entrada analógica do Arduino. 

<p align="center">
  <img src="https://github.com/user-attachments/assets/d1641f76-6be4-4ef6-9b02-4e36e0524786">
</p>
<p align="center">(Figura do sensor MQ-135).</p>


Modelo de montagem do sistema com o sensor MQ-135:

<p align="center">
  <img src="https://github.com/user-attachments/assets/4f3f6d0d-f6e4-4502-939a-3d06c305dfb6">
</p>
<p align="center">(Figura do modelo de funcionamento do sensor MQ-135).</p>


## MQTT

<p align="center">
  <img src="">
</p>
<p align="center">(Figura de exemplo genérico).</p>




<p align="center">
  <img src="">
</p>
<p align="center">(F).</p>



# Planta Resultante

<p align="center">
  <img width=462 height=334 src="">
</p>
<p align="center"> </p>


# Referências
* (https://victorvision.com.br/blog/placa-esp32/)
* https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://blog.asksensors.com/air-quality-sensor-mq135-cloud-mqtt/
* https://mqtt.org/
* https://www.youtube.com/@brino_edu
