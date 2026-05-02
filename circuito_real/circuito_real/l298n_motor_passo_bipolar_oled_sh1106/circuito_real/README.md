# Circuito Real

Esta pasta contém os ficheiros relacionados com a adaptação do projeto para montagem real.

Ao contrário das versões anteriores, que correspondem a fases de simulação em Tinkercad e Wokwi, esta secção documenta a passagem do sistema para componentes físicos reais.

A implementação real utiliza Arduino Mega, driver L298N, motor de passo bipolar do tipo NEMA 17 ou equivalente, sensores Hall, displays OLED SH1106, botões, LEDs, buzzer, sistema de permissiva de porta e alimentação separada entre lógica e potência.

## Objetivo

O objetivo desta secção é documentar a evolução do projeto da simulação para a montagem real, registando:

- circuito real utilizado;
- código adaptado ao driver L298N;
- diferenças entre simulação e implementação física;
- componentes usados na montagem;
- cuidados de alimentação e cablagem;
- limitações e melhorias futuras.

## Versões disponíveis

- [`l298n_motor_passo_bipolar_oled_sh1106`](l298n_motor_passo_bipolar_oled_sh1106) — versão real com Arduino Mega, L298N, motor de passo bipolar/NEMA 17 e quatro OLEDs SH1106.
