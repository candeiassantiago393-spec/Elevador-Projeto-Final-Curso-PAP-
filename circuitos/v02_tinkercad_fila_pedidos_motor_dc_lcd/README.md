# Circuito v02 — Tinkercad com fila de pedidos

Esta versão corresponde à segunda fase de desenvolvimento do projeto do elevador de 4 pisos em Tinkercad.

O circuito mantém a base da primeira versão, utilizando Arduino Uno, motor DC, ponte H, LCD I2C, botões exteriores, LEDs, buzzer e sensores simulados por interruptores. A principal evolução desta fase ocorreu no código, com a introdução de uma lógica de pedidos pendentes.

## Objetivo desta versão

O objetivo principal desta versão foi melhorar a lógica de funcionamento do elevador, permitindo memorizar vários pedidos de andares em simultâneo.

Na versão anterior, o sistema trabalhava essencialmente com uma variável de destino, o que fazia com que o último botão pressionado substituísse o destino anterior. Nesta versão foi introduzido um array de pedidos, permitindo que cada andar tivesse o seu próprio estado de pedido ativo.

## Principal alteração implementada

Foi introduzido o array:

```cpp
bool pedidos[4] = { false, false, false, false };
