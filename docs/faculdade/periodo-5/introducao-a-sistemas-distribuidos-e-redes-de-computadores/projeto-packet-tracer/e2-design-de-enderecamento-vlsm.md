# E2 - Design de Endereçamento VLSM

# 🔢 E2 - Design de Endereçamento VLSM
**Data de Entrega:** 05/11 (Quarta-feira)
**Critério Principal:** **Minimização do Desperdício** - o uso do bloco /24 deve ser o mais eficiente possível.
---
## 📖 Fundamentos Teóricos
### O que é VLSM?
**VLSM (Variable Length Subnet Mask)** é uma técnica de subnetting que permite criar sub-redes de **tamanhos diferentes** dentro do mesmo bloco de rede.
**Problema resolvido:** Antes do VLSM, usava-se FLSM (Fixed Length), onde todas as sub-redes tinham o mesmo tamanho. Isso desperdiçava muitos IPs.
**Exemplo de desperdício com FLSM:**
- Preciso de 1 sub-rede para 100 hosts e outra para 2 hosts
- Com FLSM: ambas teriam 128 endereços (próxima potência de 2)
- Desperdício: 126 IPs na segunda sub-rede!
**Solução com VLSM:**
- Sub-rede 1: /25 (128 endereços) para 100 hosts
- Sub-rede 2: /30 (4 endereços) para 2 hosts
- ✅ Desperdício minimizado!
### Por que VLSM é obrigatório neste projeto?
**Requisitos do projeto:**
- 5 sub-redes: 35, 30, 20, 20, 15 hosts
- Bloco disponível: /24 (256 endereços, 254 utilizáveis)
**Se usássemos FLSM:**
- Maior necessidade: 35 hosts → requer bloco de 64 (/26)
- 5 sub-redes × 64 = **320 endereços necessários**
- Bloco /24 tem apenas 256 endereços
- ❌ **Impossível!**
**Com VLSM:** ✅ Possível alocar eficientemente dentro dos 256 endereços disponíveis.
---
## 🧮 Matemática do Subnetting
### Fórmulas Essenciais
**1. Número de hosts por sub-rede:**
```javascript
Hosts utilizáveis = 2^H - 2
```
- H = número de bits para hosts
- -2 porque: 1 endereço de rede + 1 endereço de broadcast
**2. Número de bits necessários:**
```javascript
2^H ≥ (hosts_requeridos + 2)
```
**3. Máscara de sub-rede:**
```javascript
Bits de rede = 32 - H
```
### Exemplos Práticos
**Exemplo 1:** Preciso de 50 hosts
- 2\^5 = 32 (insuficiente)
- 2\^6 = 64 (suficiente!) ✅
- H = 6 bits para hosts
- Máscara: 32 - 6 = /26
- Hosts utilizáveis: 64 - 2 = 62
**Exemplo 2:** Preciso de 10 hosts
- 2\^3 = 8 (insuficiente)
- 2\^4 = 16 (suficiente!) ✅
- H = 4 bits para hosts
- Máscara: 32 - 4 = /28
- Hosts utilizáveis: 16 - 2 = 14
---
## 🎯 Aplicando VLSM ao Projeto
### Bloco de IP Atribuído
Cada grupo recebe um bloco: **172.20.X.0/24**
- X = número do seu grupo (consulte o documento do projeto)
- Exemplo para grupo 1: **172.20.1.0/24**
**Informações do bloco /24:**
- Endereço de rede: 172.20.1.0
- Máscara: 255.255.255.0
- Total de endereços: 256
- Endereços utilizáveis: 254 (de .1 a .254)
- Broadcast: 172.20.1.255
### Requisitos de Sub-redes
<table header-row="true">
<tr>
<td>Lab</td>
<td>Hosts Necessários</td>
</tr>
<tr>
<td>Lab 1</td>
<td>35 hosts</td>
</tr>
<tr>
<td>Lab 2</td>
<td>30 hosts</td>
</tr>
<tr>
<td>Lab 3</td>
<td>20 hosts</td>
</tr>
<tr>
<td>Lab 4</td>
<td>20 hosts</td>
</tr>
<tr>
<td>Lab 5</td>
<td>15 hosts</td>
</tr>
</table>
### **Regra de Ouro**
⚠️ **SEMPRE comece pela maior sub-rede e siga em ordem decrescente!**
Por quê? Porque as sub-redes devem ser contíguas (sem buracos). Começando pela maior, você garante espaço para todas.
---
## 📊 Documentação para o Relatório
### **Esta tabela deve estar preenchida no seu relatório da E2:**
<table header-row="true">
<tr>
<td>Laboratório / VLAN</td>
<td>ID da VLAN (Sugestão)</td>
<td>Hosts Necessários</td>
<td>Hosts Alocados (Tamanho do Bloco)</td>
<td>Endereço da Rede</td>
<td>Máscara / CIDR</td>
<td>Faixa de IPs Usáveis</td>
<td>Gateway (R-CIN)</td>
<td>Endereço de Broadcast</td>
</tr>
<tr>
<td>Lab 1 (A+B)</td>
<td>VLAN 10</td>
<td>35</td>
<td>62 (2\^6 - 2)</td>
<td>172.20.3.0</td>
<td>255.255.255.192 (/26)</td>
<td>172.20.3.2 - 172.20.3.62</td>
<td>172.20.3.1</td>
<td>172.20.3.63</td>
</tr>
<tr>
<td>Lab 2 (A+B)</td>
<td>VLAN 20</td>
<td>30</td>
<td>30 (2\^5 - 2)</td>
<td>172.20.3.64</td>
<td>255.255.255.224 (/27)</td>
<td>172.20.3.66 - 172.20.3.94</td>
<td>172.20.3.65</td>
<td>172.20.3.95</td>
</tr>
<tr>
<td>Lab 3</td>
<td>VLAN 30</td>
<td>20</td>
<td>30 (2\^5 - 2)</td>
<td>172.20.3.96</td>
<td>255.255.255.224 (/27)</td>
<td>172.20.3.98 - 172.20.3.126</td>
<td>172.20.3.97</td>
<td>172.20.3.127</td>
</tr>
<tr>
<td>Lab 4</td>
<td>VLAN 40</td>
<td>20</td>
<td>30 (2\^5 - 2)</td>
<td>172.20.3.128</td>
<td>255.255.255.224 (/27)</td>
<td>172.20.3.130 - 172.20.3.158</td>
<td>172.20.3.129</td>
<td>172.20.3.159</td>
</tr>
<tr>
<td>Lab 5</td>
<td>VLAN 50</td>
<td>15</td>
<td>30 (2\^5 - 2)</td>
<td>172.20.3.160</td>
<td>255.255.255.224 (/27)</td>
<td>172.20.3.162 - 172.20.3.190</td>
<td>172.20.3.161</td>
<td>172.20.3.191</td>
</tr>
</table>
---
### 📈 Análise de Eficiência
ex.:
**Endereços alocados:** 172.20.1.0 até 172.20.1.32 (31 endereços)
**Endereços disponíveis para expansão:** 172.20.1.32 até 172.20.1.64 (31 endereços)
**Taxa de utilização:** 31/64 = 48**% de eficiência** ✅
**Espaço livre suficiente para:** Um novo laboratório com até 31 hosts (bloco /26)
---
## 💡 Dicas e Erros Comuns
**❌ Erro 1:** Esquecer de somar +2 ao calcular hosts necessários
- Lembre-se: endereço de rede e broadcast não são utilizáveis!
**❌ Erro 2:** Não seguir a ordem decrescente
- Sempre comece pela maior sub-rede!
**❌ Erro 3:** Confundir máscara decimal com CIDR
- /26 = 255.255.255.192
- /27 = 255.255.255.224
- /28 = 255.255.255.240
**✅ Dica:** Anote os endereços de gateway - você usará na configuração do DHCP (E3) e nas sub-interfaces (E4)
**Próxima etapa:** Com o plano de endereçamento pronto, você implementará a segmentação com VLANs e DHCP (E3).
