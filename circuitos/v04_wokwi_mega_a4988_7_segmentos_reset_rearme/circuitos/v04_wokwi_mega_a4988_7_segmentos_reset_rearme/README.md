# Circuito v04 — Wokwi com Arduino Mega, A4988 e displays de 7 segmentos

Esta versão corresponde a uma fase experimental e importante do desenvolvimento da PAP.  
Depois da transição para o Wokwi com Arduino Mega e driver A4988, surgiu a ideia de adicionar displays de 7 segmentos para indicar visualmente o piso atual do elevador.

Nesta fase, o projeto já utiliza Arduino Mega, motor de passo com driver A4988, sensores simulados, botões de chamada, LEDs de pedidos, buzzer, LCD I2C e uma nova interface visual composta por quatro displays de 7 segmentos.

Além da parte visual, esta versão também introduz melhorias importantes na lógica do sistema, como botão de reset, deteção de timeout, estados de erro e processo de rearme.

---

## Objetivo desta versão

O principal objetivo desta versão foi testar a possibilidade de utilizar displays de 7 segmentos para indicar o andar atual do elevador.

Esta fase também serviu para começar a aproximar o sistema de uma lógica de segurança mais completa, através da introdução de:

- botão de reset;
- estados de funcionamento;
- timeout de movimento;
- alarme contínuo em erro;
- processo de rearme;
- estabilização após deteção de piso;
- debounce dos botões.

---

## Componentes utilizados

- Arduino Mega;
- motor de passo;
- driver A4988;
- 4 botões de chamada exteriores;
- 4 LEDs indicadores de pedidos;
- 4 sensores de piso simulados por interruptores;
- buzzer;
- botão de reset;
- LCD 20x4 com comunicação I2C;
- 4 displays de 7 segmentos;
- resistências;
- breadboards e cablagem.

---

## Principal novidade: displays de 7 segmentos

Nesta versão foi testada a utilização de quatro displays de 7 segmentos para mostrar o piso atual do elevador.

A ideia era ter uma indicação visual direta do andar onde a cabine se encontrava.  
Para isso, foi implementada uma lógica de multiplexagem dos displays.

Os pinos dos segmentos foram definidos no código através do array:

```cpp
const int segmentPins[7] = { 22, 23, 24, 25, 26, 27, 28 };
