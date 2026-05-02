# Circuito Real — L298N com motor de passo bipolar e OLED SH1106

Esta versão corresponde à adaptação do projeto para a montagem real, utilizando um driver L298N para comandar um motor de passo bipolar, do tipo NEMA 17 ou equivalente.

A lógica principal do elevador foi transportada da simulação para uma versão mais próxima da implementação física, mantendo a estrutura de pedidos exteriores e interiores, sensores Hall, permissiva de porta, LEDs, buzzer, reset, emergência, rearme e quatro displays OLED.

---

## Objetivo desta versão

O objetivo desta versão foi adaptar o sistema, anteriormente simulado com o driver A4988, para uma solução real com módulo L298N.

Nesta fase, pretendeu-se:

- adaptar o controlo do motor para o L298N;
- utilizar um motor de passo bipolar;
- manter a lógica de pedidos interiores e exteriores;
- manter a permissiva de porta;
- manter os sensores Hall de piso;
- utilizar quatro OLEDs SH1106 de 1,3";
- reduzir a carga de atualização dos displays;
- aproximar o código da montagem física real.

---

## Componentes principais

- Arduino Mega;
- módulo L298N;
- motor de passo bipolar, do tipo NEMA 17 ou equivalente;
- fonte de alimentação de 12 VDC para o motor;
- 4 sensores Hall para deteção dos pisos;
- 1 sensor Hall ou contacto equivalente para permissiva de porta;
- 4 botões exteriores;
- 4 botões interiores;
- 4 LEDs exteriores;
- 4 LEDs interiores;
- 1 botão de reset;
- 1 buzzer;
- 4 displays OLED SH1106 de 1,3";
- multiplexador I2C TCA9548A;
- resistências;
- cablagem;
- estrutura mecânica do elevador.

---

## Diferença principal em relação à simulação

Nas versões anteriores em Wokwi, o motor era controlado por um driver A4988, usando os sinais:

- `STEP`;
- `DIR`.

Nesta versão real, o controlo passa a ser feito através do módulo L298N, usando quatro sinais de comando para as bobinas do motor:

```cpp
#define pinMotorIN1 9
#define pinMotorIN2 33
#define pinMotorIN3 31
#define pinMotorIN4 32
