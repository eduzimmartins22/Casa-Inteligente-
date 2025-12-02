Projeto Casa inteligente com ESP8266

O que o sketch faz

Cria ponto de acesso Wi‑Fi e servidor web no ESP8266.

Controla três saídas:

Bomba com 5 níveis PWM.

Saída de fumaça digital.

Saída de luzes digital.

Interface web embutida para ajustar nível da bomba e ligar/desligar fumaça e luzes.

Pinos usados
const int PUMP_PIN   = 4;  // D2
const int SMOKE_PIN  = 5;  // D1
const int LIGHTS_PIN = 0;  // D3


Usa GPIOs diretamente, conforme a referência do core ESP8266 para Arduino, que mapeia números de pino Arduino para GPIOs. 
esp8266.github.io

Como usar rapidamente

Carregue o sketch no ESP8266.

Conecte as cargas aos pinos definidos, usando driver adequado se necessário.

No monitor serial, verifique o IP do ponto de acesso gerado.

Conecte um dispositivo ao Wi‑Fi com SSID e senha definidos.

Acesse o IP pelo navegador para ver a página de controle.

Resumo da estrutura do código

Variáveis principais: níveis PWM no array PWM_LEVELS[], estado atual da bomba e das saídas digitais.

HTML: página inteira em PROGMEM inclui estilo e script; usa fetch para /pump, /smoke, /lights.

Handlers:

/ serve a página.

/pump recebe level, ajusta analogWrite() com valor do array.

/smoke e /lights recebem state e atualizam a saída digital.

Setup: configura pinos, inicía AP, define rotas e inicia o servidor.

Loop: chama server.handleClient() para responder requisições.

Nota rápida sobre PWM

O ESP8266 permite PWM em pinos 0–16; valor padrão de alcance é 1023, frequência padrão 1 kHz; pode ser alterada por analogWriteRange() e analogWriteFreq(). 
esp8266.github.io

No sketch, os níveis usados são 0, 100, 120, 140, 160. Você pode ajustar para qualquer esquema desejado.

Pontos de atenção

Verifique compatibilidade dos pinos usados e necessidade de driver para cargas.

Alimentação adequada e proteção contra picos ou sobrecorrente.

A interface não reflete estado real após reset; se desejar, implemente endpoint de status e leitura inicial ao carregar a página.

Para páginas maiores, considere armazenar em SPIFFS/LittleFS em vez de somente PROGMEM.

https://github.com/user-attachments/assets/09024504-e4ec-4642-b7fc-829a5894c2d6

![espFoto](https://github.com/user-attachments/assets/b43325ac-aa0f-4691-9f56-aeb72e87ce33)
