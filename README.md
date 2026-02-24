# 🏠 Sistema de Automação Residencial com ESP8266

Projeto de automação residencial utilizando **ESP8266** com servidor web embarcado, permitindo controle remoto de dispositivos através de uma interface web responsiva.

O próprio microcontrolador cria um **Access Point (AP)**, eliminando a necessidade de roteador externo e tornando o sistema totalmente independente.

---

## 🎯 Objetivo do Projeto

Demonstrar:

- Implementação de servidor HTTP embarcado
- Controle PWM em microcontroladores
- Manipulação de rotas REST-like
- Interface web embarcada em PROGMEM
- Comunicação assíncrona com Fetch API
- Estrutura organizada e escalável para IoT

---

## 🧰 Tecnologias Utilizadas

- ESP8266 (Arduino Core)
- C++
- HTML5
- CSS3
- JavaScript (Fetch API)
- PROGMEM (armazenamento em memória flash)

---

## 🏗️ Arquitetura do Sistema

Dispositivo (Celular/PC)
↓
Wi-Fi Access Point (ESP8266)
↓
Servidor HTTP embarcado
↓
Controle de GPIO (PWM e Digital)


O ESP8266 atua simultaneamente como:

- Access Point Wi-Fi
- Servidor Web
- Controlador de Hardware

---

## ⚙️ Funcionalidades

- 🔌 Criação automática de rede Wi-Fi
- 🌐 Servidor Web embarcado
- 💧 Controle de bomba com 5 níveis PWM
- 💡 Controle digital de luzes
- 🌫️ Controle digital de módulo de fumaça
- 📡 Rotas dedicadas para cada dispositivo
- 🧠 Armazenamento eficiente de página HTML em PROGMEM

---

## 🔌 Mapeamento de Pinos

cpp
const int PUMP_PIN   = 4;  // D2
const int SMOKE_PIN  = 5;  // D1
const int LIGHTS_PIN = 0;  // D3

Referência oficial do core ESP8266:
https://esp8266.github.io

🌐 Endpoints Disponíveis
Método	Rota	Descrição
GET	/	Interface principal
GET	/pump?level=X	Define nível PWM da bomba
GET	/lights?state=1	Liga/Desliga luz
GET	/smoke?state=1	Liga/Desliga fumaça
🔄 PWM no ESP8266

Faixa padrão: 0 – 1023

Frequência padrão: 1 kHz

Ajustável via:

analogWriteRange()

analogWriteFreq()

Níveis utilizados no projeto:
0
100
120
140
160
🚀 Como Executar

Faça upload do código para o ESP8266.

Conecte os dispositivos aos pinos indicados (utilize driver ou relé quando necessário).

Abra o Monitor Serial para visualizar o IP.

Conecte-se à rede Wi-Fi criada pelo ESP.

Acesse o IP pelo navegador.


https://github.com/user-attachments/assets/09024504-e4ec-4642-b7fc-829a5894c2d6

![espFoto](https://github.com/user-attachments/assets/b43325ac-aa0f-4691-9f56-aeb72e87ce33)

📌 Sobre o Autor

Projeto desenvolvido para estudo e prática em sistemas embarcados e IoT.

🔗 Repositório:
https://github.com/eduzimmartins22/Casa-Inteligente-
