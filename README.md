# PAP — Elevador de 4 Pisos com Arduino Mega

## Descrição do Projeto

Este projeto foi desenvolvido no âmbito da Prova de Aptidão Profissional do Curso Profissional de Técnico de Eletrónica, Automação e Comando.

O sistema consiste num protótipo funcional de um elevador de quatro pisos, controlado por um Arduino Mega. O elevador recebe pedidos exteriores e interiores, memoriza os pedidos numa fila lógica, controla o movimento da cabine, identifica o piso atual através de sensores, apresenta informação em quatro displays OLED e possui lógica de segurança para situações de erro.

A simulação virtual foi desenvolvida em Wokwi, utilizando um driver A4988 para controlo do motor de passo. A implementação real será adaptada para uma estrutura física com motor de passo, módulo L298N, sensores Hall, cabine impressa em 3D, cabo de aço e tambor.

---

## Objetivos

- Desenvolver um elevador didático de quatro pisos.
- Controlar o movimento da cabine através de Arduino Mega.
- Registar pedidos exteriores e interiores.
- Memorizar vários pedidos em simultâneo.
- Atender os pedidos por prioridade de sentido.
- Indicar visualmente os pedidos através de LEDs.
- Apresentar estado, piso atual, fila de pedidos e sentido nos displays OLED.
- Bloquear o movimento se a porta não estiver fechada.
- Detetar falhas de movimento através de timeout.
- Entrar em emergência em caso de erro.
- Executar uma sequência de rearme segura.

---

## Funcionalidades Implementadas

- Controlo de motor de passo com A4988 na simulação.
- Botões exteriores para chamada dos quatro pisos.
- Botões interiores da cabine.
- LEDs exteriores e interiores associados aos pedidos.
- Sistema de fila de pedidos.
- Priorização de pedidos por sentido de deslocação.
- Sensores de piso simulados por interruptores.
- Buzzer com bip curto em chegada a piso pedido.
- Alarme contínuo em situação de emergência.
- Botão de reset.
- Lógica de rearme.
- Permissiva de porta.
- Quatro displays OLED ligados através de multiplexador TCA9548A.

---

## Imagem da Simulação

![Circuito completo no Wokwi](imagens/circuito_completo.png)

---

## Componentes Utilizados na Simulação

- Arduino Mega
- Driver A4988
- Motor de passo
- 4 displays OLED SSD1306
- Multiplexador I2C TCA9548A
- 4 botões exteriores
- 4 botões interiores
- 8 LEDs de pedidos
- 4 sensores de piso simulados
- 1 botão de reset
- 1 buzzer
- Breadboards e cablagem

---

## Componentes Previstos para a Implementação Real

- Arduino Mega
- Motor de passo NEMA 17 ou equivalente
- Módulo L298N
- Fonte industrial 12 VDC / 5 A / 60 W
- 4 sensores Hall
- 4 displays OLED de 1,3"
- 4 botões exteriores
- 4 botões interiores
- 8 LEDs
- Buzzer
- Botão de reset
- Cabine impressa em 3D
- Cabo de aço
- Tambor no eixo do motor
- Sistema de porta manual
- Fins de curso, futuramente

---

## Pinagem Principal

| Função | Pino Arduino Mega |
|---|---|
| Botão exterior piso 1 | D2 |
| Botão exterior piso 2 | D3 |
| Botão exterior piso 3 | D4 |
| Botão exterior piso 4 | D5 |
| Buzzer | D6 |
| Reset | D7 |
| Sensor piso 1 | D8 |
| STEP A4988 | D9 |
| DIR A4988 | D10 |
| Sensor piso 2 | D11 |
| Sensor piso 3 | D12 |
| Sensor piso 4 | D13 |
| Permissiva da porta | D22 |
| Botão interior piso 1 | D23 |
| Botão interior piso 2 | D24 |
| Botão interior piso 3 | D25 |
| Botão interior piso 4 | D26 |
| LED interior piso 1 | D27 |
| LED interior piso 2 | D28 |
| LED interior piso 3 | D29 |
| LED interior piso 4 | D30 |
| LED exterior piso 1 | A0 |
| LED exterior piso 2 | A1 |
| LED exterior piso 3 | A2 |
| LED exterior piso 4 | A3 |
| SDA I2C | D20 |
| SCL I2C | D21 |

---

## Lógica de Funcionamento

Os pedidos exteriores e interiores atuam sobre a mesma fila lógica. Quando um botão é pressionado, o pedido correspondente ao piso fica memorizado. O LED exterior e o LED interior desse piso acendem, indicando que o pedido está pendente.

O elevador analisa a posição atual e o sentido de deslocação. Se estiver a subir, dá prioridade aos pedidos acima do piso atual. Se estiver a descer, dá prioridade aos pedidos abaixo. A mudança de sentido só ocorre quando já não existem pedidos compatíveis com o sentido atual.

Quando o elevador chega a um piso pedido, o sistema remove esse pedido da fila, apaga os LEDs correspondentes, emite um bip curto e inicia uma paragem temporizada.

---

## Estados do Sistema

| Estado | Descrição |
|---|---|
| NORMAL | Funcionamento normal do elevador |
| PORTA | Movimento bloqueado por porta aberta |
| PARAGEM | Paragem temporizada num piso pedido |
| ESTAB | Estabilização após deteção de piso |
| ERRO_MOV | Erro durante movimento |
| ERRO_PAR | Erro consolidado com o elevador parado |
| REARME | Processo de recuperação após erro |

---

## Segurança e Emergência

O sistema possui uma lógica de segurança baseada em timeout. Se o elevador estiver em movimento durante demasiado tempo sem detetar um piso válido, entra em modo de emergência.

Em emergência:
- o motor é parado;
- os pedidos são limpos;
- os LEDs são desligados;
- o buzzer emite alarme contínuo;
- o funcionamento normal fica bloqueado até ser pressionado o botão de reset.

Após o reset, o sistema executa uma sequência de rearme, deslocando-se para uma posição segura e regressando depois ao funcionamento normal.

---

## Estrutura do Repositório

```text
codigo/
  Código Arduino da simulação e da implementação real.

simulacao/
  Ficheiros relacionados com o Wokwi e imagens do circuito virtual.

documentacao/
  Relatório técnico, tabelas, esquemas e explicações.

imagens/
  Imagens da simulação, montagem real e componentes.

extras/
  Histórico de versões, ideias futuras e problemas encontrados.
