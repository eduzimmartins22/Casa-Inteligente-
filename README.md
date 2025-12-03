Descrição do Projeto

Sistema simples de automação residencial utilizando ESP8266, permitindo controle de bomba, fumaça e luzes através de uma interface web embutida.
O próprio ESP cria um ponto de acesso Wi-Fi para que qualquer dispositivo possa se conectar e controlar o sistema.

Recursos Implementados

Criação de Access Point (AP) Wi-Fi diretamente no ESP8266.

Servidor web embarcado para controle das saídas.

Ajuste de potência da bomba via PWM com 5 níveis.

Controle digital de fumaça e luzes.

Página HTML completa armazenada em PROGMEM com JavaScript e fetch API.

Rotas próprias para cada controle (/pump, /smoke, /lights).

Pinos Utilizados
const int PUMP_PIN   = 4;  // D2
const int SMOKE_PIN  = 5;  // D1
const int LIGHTS_PIN = 0;  // D3


O código utiliza a referência oficial de mapeamento do core ESP8266 para Arduino.
Documentação: esp8266.github.io

Como Usar

Carregue o sketch no ESP8266.

Conecte bomba, módulo de fumaça e luzes aos pinos indicados (com driver se necessário).

Abra o monitor serial e copie o IP gerado pelo ponto de acesso.

Conecte-se ao Wi-Fi criado pelo ESP.

Acesse o IP no navegador do celular ou PC.

Utilize a interface para:

Definir nível da bomba

Ligar/desligar fumaça

Ligar/desligar luzes

Resumo da Estrutura do Código

Variáveis principais: níveis de PWM, estados digitais e armazenamento do nível atual.

Página HTML: inserida em PROGMEM com CSS e JavaScript.

Rotas:

/ → página de controle

/pump?level=X → ajusta PWM

/lights?state=1 → liga/desliga luz

/smoke?state=1 → liga/desliga fumaça

Setup: configura pinos, inicia AP, define rotas e inicia servidor.

Loop: server.handleClient() processa as requisições.

Nota sobre PWM no ESP8266

PWM disponível nos pinos 0–16

Alcance padrão: 0–1023

Frequência padrão: 1 kHz

Ajustável com analogWriteRange() e analogWriteFreq()

Níveis usados no projeto:
0, 100, 120, 140, 160
(podendo ser alterados livremente)

https://github.com/user-attachments/assets/09024504-e4ec-4642-b7fc-829a5894c2d6

![espFoto](https://github.com/user-attachments/assets/b43325ac-aa0f-4691-9f56-aeb72e87ce33)
