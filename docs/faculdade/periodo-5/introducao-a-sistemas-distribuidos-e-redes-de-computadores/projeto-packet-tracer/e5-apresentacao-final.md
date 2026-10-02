# E5 - Apresentação Final

# 🎤 E5 - Apresentação Final do Projeto
**Data de Entrega:** 19/11 (Quarta-feira)
**Critério Principal:** **Conectividade Total** - os PCs devem conversar entre si e navegar na Internet. Demonstração oral de funcionamento.
---
## 📖 O que é esperado nesta entrega?
A E5 é a **culminação** do projeto. Você deverá:
1. **Consolidar toda a documentação** (E1 a E4) em um relatório final coeso
2. Apresentar o funcionamento da rede no Packet Tracer
3. **Explicar suas decisões de design** e justificar escolhas técnicas
Esta é sua oportunidade de mostrar que você não apenas seguiu instruções, mas **compreendeu** os fundamentos de redes!
---
### Demonstração 1: Tabela de Roteamento
```javascript
R-CIN# show ip route
```
### Demonstração 2: VLANs e Trunks
```javascript
Switch-Core# show vlan brief
Switch-Core# show interfaces trunk
```
### Demonstração 3: DHCP em Ação
- Abrir um PC
- Mostrar que está configurado para DHCP
- Executar `ipconfig` no Command Prompt
### Demonstração 4: Conectividade Intra-VLAN
```javascript
PC-Lab1-01> ping 172.20.1.10
```
### Demonstração 5: Conectividade Inter-VLAN 
```javascript
PC-Lab1-01> ping 172.20.1.70
```
### Demonstração 6: Traceroute
```javascript
PC-Lab1-01> tracert 172.20.1.70
```
### Demonstração 7: Conectividade Externa
```javascript
PC-Lab1-01> ping 2.2.2.2
```
---
## 🎯 Perguntas que serão feitas
Esteja preparado para responder:
### Sobre Design
- "Como escalaria esta rede para 10 laboratórios?"
### Sobre VLSM
- "Por que começar pela maior sub-rede?"
- "Quanto IP foi desperdiçado?"
### Sobre VLANs
- "O que acontece se não criar a VLAN em um switch?"
- "Trunk e Access são configurações de software ou hardware?"
### Sobre Roteamento
- "Por que a técnica se chama Router-on-a-Stick?"
- "Qual a principal desvantagem do ROAS?"
### Sobre Troubleshooting
- "Se o ping inter-VLAN falhasse, qual seria seu diagnóstico?"
---
**❌ Evite:**
- Ler slides ou relatório palavra por palavra
- Demonstrações muito longas sem explicação
- Jargão técnico excessivo sem contexto
- Culpar erros no software ("o Packet Tracer está bugado")
