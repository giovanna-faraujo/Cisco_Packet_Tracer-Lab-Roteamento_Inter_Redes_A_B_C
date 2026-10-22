# Roteamento entre três redes IPv4

## Visão geral

Neste laboratório do **Programa Mulher Digital**, utilizei o **Cisco Packet Tracer** para praticar a configuração e a comunicação entre três redes IPv4 diferentes.

A atividade envolveu um roteador Cisco 2911, três switches Cisco 2960 e seis computadores, organizados em três redes.

O objetivo foi entender como os **endereços IP, máscaras de rede e gateways** permitem que computadores de redes diferentes se comuniquem por meio de um roteador.

---

## Topologia da rede

![Topologia do laboratório](https://github.com/user-attachments/assets/c87e1dee-1aa0-4135-86e2-e418ee63704c)

Cada rede possui dois computadores conectados a um switch. Os três switches estão ligados ao roteador central, responsável pela comunicação entre as redes.

---

## O que pratiquei

* Montagem de uma topologia com três redes IPv4.
* Conexão de computadores, switches e roteador.
* Configuração de endereços IPv4 estáticos, máscaras e gateways.
* Configuração das interfaces do roteador.
* Comunicação entre computadores de redes diferentes.
* Verificação de conectividade utilizando ICMP.

---

## Como o laboratório foi desenvolvido

1. **Montagem:** adição de um roteador Cisco 2911, três switches Cisco 2960 e seis computadores.
2. **Conexões:** ligação dos computadores aos switches e dos switches ao roteador.
3. **Endereçamento:** definição dos endereços IPv4, máscaras e gateways dos computadores.
4. **Roteador:** configuração e habilitação das três interfaces de rede.
5. **Verificação:** utilização de testes ICMP para observar a comunicação entre redes diferentes.

---

## Configurações dos dispositivos

### 1. Endereçamento das redes

Cada rede recebeu uma faixa de endereços IPv4 e um gateway próprio.

| Rede       | Endereço de rede | Máscara         | CIDR  | Gateway       |
| ---------- | ---------------- | --------------- | ----- | ------------- |
| **Rede A** | `10.0.0.0`       | `255.0.0.0`     | `/8`  | `10.0.0.1`    |
| **Rede B** | `172.16.0.0`     | `255.255.0.0`   | `/16` | `172.16.0.1`  |
| **Rede C** | `192.168.1.0`    | `255.255.255.0` | `/24` | `192.168.1.1` |

### 2. Configurações do roteador e computadores

As interfaces do roteador foram definidas como gateways das respectivas redes. Cada computador recebeu um endereço IPv4 estático.

| Dispositivo           | Interface | Endereço IPv4 | Máscara | Gateway       |
| --------------------- | --------- | ------------- | ------- | ------------- |
| **Roteador — Rede A** | G0/0      | `10.0.0.1`    | `/8`    | —             |
| PC A1                 | Fa0       | `10.0.0.2`    | `/8`    | `10.0.0.1`    |
| PC A2                 | Fa0       | `10.0.0.3`    | `/8`    | `10.0.0.1`    |
| **Roteador — Rede B** | G0/1      | `172.16.0.1`  | `/16`   | —             |
| PC B1                 | Fa0       | `172.16.0.2`  | `/16`   | `172.16.0.1`  |
| PC B2                 | Fa0       | `172.16.0.3`  | `/16`   | `172.16.0.1`  |
| **Roteador — Rede C** | G0/2      | `192.168.1.1` | `/24`   | —             |
| PC C1                 | Fa0       | `192.168.1.2` | `/24`   | `192.168.1.1` |
| PC C2                 | Fa0       | `192.168.1.3` | `/24`   | `192.168.1.1` |

**Observações:**

* As interfaces G0/0, G0/1 e G0/2 do roteador devem estar habilitadas.
* Nos computadores, as configurações são realizadas em `Desktop > IP Configuration`.
* Na tabela, as máscaras estão representadas em CIDR para facilitar a leitura.

### 3. Conexões entre os dispositivos

As conexões foram definidas utilizando cabos **Copper Straight-Through**.

| Origem   | Porta de origem | Destino  | Porta de destino |
| -------- | --------------- | -------- | ---------------- |
| Roteador | G0/0            | Switch A | Fa0/1            |
| Roteador | G0/1            | Switch B | Fa0/1            |
| Roteador | G0/2            | Switch C | Fa0/1            |
| PC A1    | Fa0             | Switch A | Fa0/2            |
| PC A2    | Fa0             | Switch A | Fa0/3            |
| PC B1    | Fa0             | Switch B | Fa0/2            |
| PC B2    | Fa0             | Switch B | Fa0/3            |
| PC C1    | Fa0             | Switch C | Fa0/2            |
| PC C2    | Fa0             | Switch C | Fa0/3            |

---

## Testes de conectividade

A atividade apresenta um exemplo de comunicação entre o **PC A2 (Rede A)** e o **PC B2 (Rede B)**, utilizando um pacote ICMP no Cisco Packet Tracer.

No material de referência, o teste aparece com o status **Successful**, indicando que o pacote foi entregue na simulação ilustrada.

Esse exemplo demonstra como o roteador pode encaminhar informações entre redes diferentes.

**Observação:** o resultado apresentado pertence ao material da atividade e não representa uma validação independente de todos os dispositivos da topologia.

---

## Onde esse conhecimento pode ser aplicado?

**Cenário fictício: comunicação entre setores de uma empresa**

Imagine uma empresa com três setores:

* **Financeiro:** Rede A.
* **Comercial:** Rede B.
* **Operações:** Rede C.

Cada setor possui sua própria rede de computadores.

Um funcionário do Comercial precisa acessar um recurso do Financeiro, mas os computadores estão em redes diferentes.

O profissional de TI verifica os endereços IP, as máscaras e os gateways para garantir que os dispositivos estejam configurados corretamente.

Com o roteador interligando as redes, os computadores podem trocar informações entre os setores.

> **Resultado esperado:** permitir a comunicação entre as redes, desde que as configurações estejam corretas e não existam regras impedindo o acesso.

> **O que esse cenário ensina:** separar computadores em redes diferentes ajuda na organização do ambiente. Porém, essa separação não impede automaticamente o acesso entre setores. Para controlar quem pode acessar determinados recursos, são necessárias configurações adicionais de segurança.

---

## Principais aprendizados

Com este laboratório, pude praticar conceitos importantes para a configuração e o diagnóstico de redes de computadores.

* **Endereçamento IPv4:** configuração de endereços para identificar os dispositivos.
* **Máscaras de rede:** identificação dos endereços que pertencem à mesma rede.
* **Gateway padrão:** definição do caminho utilizado para acessar outras redes.
* **Switches e roteadores:** compreensão das funções de cada equipamento na comunicação.
* **Roteamento entre redes:** utilização de um roteador para conectar diferentes segmentos.
* **Testes ICMP:** verificação da comunicação e investigação de possíveis falhas.

**O principal aprendizado foi entender como os dispositivos de diferentes redes conseguem se comunicar e como essas configurações ajudam no diagnóstico de problemas de conectividade em ambientes corporativos.**

---

## Entendendo os termos técnicos

| Termo                       | Explicação simples                                                         |
| --------------------------- | -------------------------------------------------------------------------- |
| **IPv4**                    | Endereço utilizado para identificar um dispositivo em uma rede.            |
| **Switch**                  | Equipamento que conecta computadores dentro de uma rede local.             |
| **Roteador**                | Equipamento que permite a comunicação entre redes diferentes.              |
| **Gateway**                 | Endereço utilizado pelo computador para enviar informações a outras redes. |
| **Máscara de rede**         | Define quais endereços fazem parte da mesma rede.                          |
| **Interface**               | Porta de comunicação de um dispositivo.                                    |
| **ICMP**                    | Protocolo utilizado em testes de comunicação, como o `ping`.               |
| **CIDR**                    | Forma abreviada de representar uma máscara de rede, como `/8` ou `/24`.    |
| **Copper Straight-Through** | Cabo de rede direto utilizado para conectar equipamentos.                  |

