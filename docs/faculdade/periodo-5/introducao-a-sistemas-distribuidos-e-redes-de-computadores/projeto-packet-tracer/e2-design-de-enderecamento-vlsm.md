# E2 - Design de Endereçamento VLSM

**Data de Entrega:** 05/11 (Quarta-feira)

**Critério Principal:** **Minimização do Desperdício** — o uso do bloco /24 deve ser o mais eficiente possível.

---

## Fundamentos Teóricos

### O que é VLSM?

**VLSM (Variable Length Subnet Mask)** é uma técnica de subnetting que permite criar sub-redes de **tamanhos diferentes** dentro do mesmo bloco de rede.

**Problema resolvido:** antes do VLSM, usava-se FLSM (Fixed Length Subnet Mask), onde todas as sub-redes tinham o mesmo tamanho. Isso desperdiçava muitos endereços IP.

**Exemplo de desperdício com FLSM:**

- Preciso de 1 sub-rede para 100 hosts e outra para 2 hosts.
- Com FLSM, ambas teriam 128 endereços (a próxima potência de 2 que cobre o maior requisito).
- Desperdício: 126 IPs na segunda sub-rede.

**Solução com VLSM:**

- Sub-rede 1: /25 (128 endereços) para 100 hosts.
- Sub-rede 2: /30 (4 endereços) para 2 hosts.
- Desperdício minimizado.

### Por que VLSM é obrigatório neste projeto?

**Requisitos do projeto:**

- 5 sub-redes: 35, 30, 20, 20, 15 hosts.
- Bloco disponível: /24 (256 endereços, 254 utilizáveis).

**Se usássemos FLSM:**

- Maior necessidade: 35 hosts → requer bloco de 64 endereços (/26).
- 5 sub-redes × 64 = **320 endereços necessários**.
- O bloco /24 tem apenas 256 endereços.
- **Impossível.**

**Com VLSM:** possível alocar eficientemente dentro dos 256 endereços disponíveis.

---

## Matemática do Subnetting

### Fórmulas Essenciais

**1. Número de hosts utilizáveis por sub-rede:**

$$\text{Hosts utilizáveis} = 2^H - 2$$

Onde $H$ é o número de bits reservados para hosts. O $-2$ é porque 1 endereço é reservado para a rede e 1 para o broadcast.

**2. Número de bits necessários:**

$$2^H \geq (\text{hosts requeridos} + 2)$$

**3. Máscara de sub-rede:**

$$\text{Bits de rede} = 32 - H$$

### Exemplos Práticos

**Exemplo 1 — preciso de 50 hosts:**

- $2^5 = 32$ (insuficiente).
- $2^6 = 64$ (suficiente).
- $H = 6$ bits para hosts.
- Máscara: $32 - 6 = /26$.
- Hosts utilizáveis: $64 - 2 = 62$.

**Exemplo 2 — preciso de 10 hosts:**

- $2^3 = 8$ (insuficiente).
- $2^4 = 16$ (suficiente).
- $H = 4$ bits para hosts.
- Máscara: $32 - 4 = /28$.
- Hosts utilizáveis: $16 - 2 = 14$.

---

## Aplicando VLSM ao Projeto

### Bloco de IP Atribuído

Cada grupo recebe um bloco **172.20.X.0/24**, onde X é o número do grupo (consulte o documento do projeto). Exemplo, para o grupo 1: **172.20.1.0/24**.

**Informações do bloco /24:**

- Endereço de rede: `172.20.1.0`
- Máscara: `255.255.255.0`
- Total de endereços: 256
- Endereços utilizáveis: 254 (de `.1` a `.254`)
- Broadcast: `172.20.1.255`

### Requisitos de Sub-redes

| Lab | Hosts Necessários |
| --- | --- |
| Lab 1 | 35 hosts |
| Lab 2 | 30 hosts |
| Lab 3 | 20 hosts |
| Lab 4 | 20 hosts |
| Lab 5 | 15 hosts |

!!! warning "Regra de Ouro"
    **Sempre comece pela maior sub-rede e siga em ordem decrescente.** Isso garante que as sub-redes fiquem contíguas (sem buracos no espaço de endereços) e que haja espaço suficiente para todas elas.

---

## Documentação para o Relatório

**Esta tabela deve estar preenchida no seu relatório da E2:**

| Laboratório / VLAN | ID da VLAN (Sugestão) | Hosts Necessários | Hosts Alocados (Tamanho do Bloco) | Endereço da Rede | Máscara / CIDR | Faixa de IPs Usáveis | Gateway (R-CIN) | Endereço de Broadcast |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Lab 1 (A+B) | VLAN 10 | 35 | 62 ($2^6 - 2$) | 172.20.3.0 | 255.255.255.192 (/26) | 172.20.3.2 - 172.20.3.62 | 172.20.3.1 | 172.20.3.63 |
| Lab 2 (A+B) | VLAN 20 | 30 | 30 ($2^5 - 2$) | 172.20.3.64 | 255.255.255.224 (/27) | 172.20.3.66 - 172.20.3.94 | 172.20.3.65 | 172.20.3.95 |
| Lab 3 | VLAN 30 | 20 | 30 ($2^5 - 2$) | 172.20.3.96 | 255.255.255.224 (/27) | 172.20.3.98 - 172.20.3.126 | 172.20.3.97 | 172.20.3.127 |
| Lab 4 | VLAN 40 | 20 | 30 ($2^5 - 2$) | 172.20.3.128 | 255.255.255.224 (/27) | 172.20.3.130 - 172.20.3.158 | 172.20.3.129 | 172.20.3.159 |
| Lab 5 | VLAN 50 | 15 | 30 ($2^5 - 2$) | 172.20.3.160 | 255.255.255.224 (/27) | 172.20.3.162 - 172.20.3.190 | 172.20.3.161 | 172.20.3.191 |

---

### Análise de Eficiência

Exemplo:

- **Endereços alocados:** 172.20.1.0 até 172.20.1.32 (31 endereços)
- **Endereços disponíveis para expansão:** 172.20.1.32 até 172.20.1.64 (31 endereços)
- **Taxa de utilização:** $31/64 = 48\%$ de eficiência
- **Espaço livre suficiente para:** um novo laboratório com até 31 hosts (bloco /26)

---

## Dicas e Erros Comuns

| Erro comum | Como evitar |
| --- | --- |
| Esquecer de somar +2 ao calcular hosts necessários | Lembre-se: o endereço de rede e o de broadcast não são utilizáveis |
| Não seguir a ordem decrescente ao alocar sub-redes | Sempre comece pela maior sub-rede |
| Confundir máscara decimal com CIDR | `/26` = `255.255.255.192`; `/27` = `255.255.255.224`; `/28` = `255.255.255.240` |

!!! tip "Dica"
    Anote os endereços de gateway — você vai usá-los na configuração do DHCP (E3) e nas sub-interfaces (E4).

**Próxima etapa:** com o plano de endereçamento pronto, você implementará a segmentação com VLANs e DHCP (E3).
