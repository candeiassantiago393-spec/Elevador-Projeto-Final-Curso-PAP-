
---

## Versão em português

```md
# Test Bench PAP — Pedidos Exteriores

Esta pasta contém os ficheiros de teste para o **sistema de pedidos exteriores** do projeto PAP do elevador.

O objetivo é testar, de forma independente e segura, o hardware relacionado com as **chamadas exteriores dos pisos**, antes de integrar esta parte no código completo de controlo do elevador.

---

## Contexto do projeto

Este test bench pertence à implementação real de um **protótipo de elevador de 4 pisos**, desenvolvido com um **Arduino Mega**.

Nesta fase, são testados apenas os componentes dos pedidos exteriores:

- Botões exteriores de chamada
- LEDs exteriores de indicação
- Lógica de memória entre botão e LED

Neste teste não existe lógica do motor, OLEDs, sensores dos pisos, permissiva da porta, emergência ou rearme.

---

## Ficheiro principal de teste

### `Test_01_External_Requests_LED_Latched.ino`

Este ficheiro testa o comportamento completo dos pedidos exteriores:

| Ação | Resultado |
|---|---|
| Carregar no botão exterior do piso 1 | LED do piso 1 fica ligado |
| Carregar no botão exterior do piso 2 | LED do piso 2 fica ligado |
| Carregar no botão exterior do piso 3 | LED do piso 3 fica ligado |
| Carregar no botão exterior do piso 4 | LED do piso 4 fica ligado |

Os LEDs permanecem ligados depois de carregar nos botões. Isto permite testar vários pedidos de piso ao mesmo tempo, de forma semelhante à memória de pedidos de um elevador real.

---

## Ficheiros de teste previstos

Esta pasta também irá incluir testes mais simples e isolados:

| Ficheiro | Objetivo |
|---|---|
| `Test_01_External_Requests_LED_Latched.ino` | Testa botões e LEDs em conjunto com memória de pedido |
| `Test_02_External_Buttons_Only.ino` | Testa apenas os botões exteriores através do Serial Monitor |
| `Test_03_External_LEDs_Only.ino` | Testa apenas os LEDs exteriores sem botões |

---

## Hardware utilizado

- Arduino Mega
- 4 botões de pressão exteriores
- 4 LEDs exteriores
- 4 resistências para os LEDs
- Cabos de ligação ou cablagem do projeto
- Breadboard, bornes ou ligações soldadas

---

## Pinagem

### Botões exteriores

| Piso | Função | Pino Arduino Mega |
|---|---|---:|
| Piso 1 | Botão exterior 1 | D2 |
| Piso 2 | Botão exterior 2 | D3 |
| Piso 3 | Botão exterior 3 | D4 |
| Piso 4 | Botão exterior 4 | D5 |

### LEDs exteriores

| Piso | Função | Pino Arduino Mega |
|---|---|---:|
| Piso 1 | LED exterior 1 | A0 |
| Piso 2 | LED exterior 2 | A1 |
| Piso 3 | LED exterior 3 | A2 |
| Piso 4 | LED exterior 4 | A3 |

Os pinos analógicos A0, A1, A2 e A3 são usados como saídas digitais.

---

## Ligação dos botões

Os botões usam as resistências internas de pull-up do Arduino.

Cada botão deve ser ligado entre o pino de entrada do Arduino e o GND.

Exemplo:

```text
Pino de entrada do Arduino ── Botão ── GND
