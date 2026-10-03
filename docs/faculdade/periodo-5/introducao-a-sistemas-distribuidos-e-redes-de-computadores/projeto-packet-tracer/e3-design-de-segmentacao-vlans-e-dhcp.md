# E3 - Design de Segmentação (VLANs e DHCP)

**Data de Entrega:** 07/11 (Sexta-feira)

**Critério Principal:** **Lógica e Funcionalidade** — a estratégia de DHCP deve ser funcional e as portas trunk devem suportar todas as VLANs.

---

## Prática no Packet Tracer

### Parte 0: Ativar a conexão do roteador

Por padrão, as portas de um roteador Cisco vêm administrativamente desligadas (`shutdown`). É preciso ligá-las manualmente.

Clique no `R-CIN` → aba `CLI`.

```text
Router# configure terminal

# Entre na interface física PRINCIPAL (não na sub-interface)
Router(config)# interface GigabitEthernet0/0

# Execute o comando para LIGAR a porta
Router(config-if)# no shutdown

# Saia e salve
Router(config-if)# end
Router# copy running-config startup-config
```

---

## Parte 1 e 2: Criação e Nomeação de VLANs

O objetivo aqui é criar as "redes virtuais" que irão segmentar os laboratórios. Essa configuração deve ser feita tanto no **Switch Core** quanto nos **Switches de Acesso**.

### Comandos Úteis

- `vlan <ID>` — cria uma VLAN com o número de identificação (ID) especificado, ou entra no modo de configuração dessa VLAN se ela já existir.
- `name <NOME_DA_VLAN>` — atribui um nome descritivo à VLAN em configuração. É boa prática usar nomes que identifiquem sua finalidade (ex: `LAB_ENGENHARIA` ou `VLAN10_LAB1`).

!!! tip "Dica Importante"
    A organização é fundamental. Certifique-se de que os IDs e nomes das VLANs sejam consistentes em todos os switches, para facilitar o gerenciamento.

### Comando de Verificação

- `show vlan brief` — exibe uma tabela com todas as VLANs criadas no switch, seus nomes e quais portas estão associadas a elas. Use para confirmar que as VLANs foram criadas corretamente.

---

## Parte 3: Configuração de Portas Trunk

### Comandos Úteis (Switch Core — Layer 3)

- `interface <tipo_e_numero>` ou `interface range <tipo_e_intervalo>` — entra no modo de configuração de uma porta específica (ex: `GigabitEthernet0/1`) ou de um intervalo de portas (ex: `FastEthernet0/1 - 7`).
- `switchport trunk encapsulation dot1q` — define o protocolo de encapsulamento usado para "etiquetar" o tráfego das VLANs. Obrigatório em switches Layer 3, como o 3560, antes de ativar o modo trunk.
- `switchport mode trunk` — ativa o modo de operação *trunk* na porta selecionada.

### Comandos Úteis (Switches de Acesso — Layer 2)

Nos switches de acesso (modelo 2960), geralmente o comando `switchport trunk encapsulation dot1q` não é necessário, pois eles só suportam esse protocolo. Pode-se usar diretamente `switchport mode trunk`.

### Comando de Verificação

- `show interfaces trunk` — mostra a lista de todas as portas operando em modo trunk, seu status e quais VLANs estão autorizadas a passar por elas. Essencial para verificar se as "autoestradas" estão funcionando.

---

## Parte 4: Configuração de Portas de Acesso

### Comandos Úteis

- `switchport mode access` — configura a porta para operar em modo de acesso.
- `switchport access vlan <ID>` — associa a porta de acesso à VLAN especificada. Todo o tráfego que entrar ou sair por essa porta pertencerá a essa VLAN.

---

## Parte 5: Configuração de DHCP e Roteamento no Roteador

O objetivo é fazer com que o roteador (`R-CIN`) gerencie a comunicação entre as diferentes VLANs (roteamento Inter-VLAN) e distribua endereços IP automaticamente para os PCs (serviço DHCP).

### Etapa A: Criar os Gateways (Router-on-a-Stick)

O roteador precisa de uma "porta" virtual para cada VLAN — essas são as sub-interfaces.

- `interface <tipo_e_numero>.<ID_DA_VLAN>` — cria uma sub-interface virtual. O número após o ponto deve corresponder ao ID da VLAN, para manter a organização (ex: `interface GigabitEthernet0/0.10` para a VLAN 10).
- `encapsulation dot1Q <ID_DA_VLAN>` — vincula a sub-interface à VLAN correspondente. É assim que o roteador sabe qual tráfego pertence a qual sub-interface.
- `ip address <IP_DO_GATEWAY> <MASCARA>` — atribui o endereço IP de gateway para aquela sub-rede/VLAN. Esse é o endereço que os PCs usarão para se comunicar com outras redes.

### Etapa B: Configurar o Serviço DHCP

- `ip dhcp excluded-address <IP_A_EXCLUIR>` — impede que o servidor DHCP distribua um endereço específico. Use para reservar os endereços dos gateways configurados na Etapa A.
- `ip dhcp pool <NOME_DO_POOL>` — cria um "conjunto" de configurações DHCP com um nome descritivo (ex: `POOL_LAB1`).
- `network <ENDERECO_DA_REDE> <MASCARA>` — define a faixa de endereços IP que esse pool pode distribuir.
- `default-router <IP_DO_GATEWAY>` — informa aos clientes DHCP qual é o endereço do gateway padrão da rede.
- `dns-server <IP_DO_DNS>` — informa aos clientes qual servidor DNS devem usar. Conforme solicitado, utilize o endereço **`8.8.8.8`** (DNS público do Google).

---

## Documentação para o Relatório

| VLAN ID | Nome da VLAN | Sub-rede IP | Gateway (R-CIN) | Switch(es) de Acesso | Portas de Acesso |
| --- | --- | --- | --- | --- | --- |
| VLAN 10 | LAB01 | 172.20.3.0 /26 | 172.20.3.1 | Sw-Acesso-Lab1-A / Sw-Acesso-Lab1-B | Fa0/1 - Fa0/24 (em ambos os switches) |
| VLAN 20 | LAB02 | 172.20.3.64 /27 | 172.20.3.65 | Sw-Acesso-Lab2-A / Sw-Acesso-Lab2-B | Fa0/1 - Fa0/24 (em ambos os switches) |
| VLAN 30 | LAB03 | 172.20.3.96 /27 | 172.20.3.97 | Sw-Acesso-Lab3 | Fa0/1 - Fa0/20 |
| VLAN 40 | LAB04 | 172.20.3.128 /27 | 172.20.3.129 | Sw-Acesso-Lab4 | Fa0/1 - Fa0/20 |
| VLAN 50 | LAB05 | 172.20.3.160 /27 | 172.20.3.161 | Sw-Acesso-Lab5 | Fa0/1 - Fa0/15 |

**Portas Trunk configuradas:**

- Switch Core: Fa0/1-5 (→ Switches de Acesso) + Gi0/1 (→ Roteador)
- Cada Switch de Acesso: Gi0/1 (→ Switch Core)

---

### Comandos de Verificação (devem estar presentes no relatório)

Use estes comandos para validar as configurações:

**Ver VLANs criadas (switch):**

```text
Switch# show vlan brief
```

**Ver portas trunk (switch):**

```text
Switch# show interfaces trunk
```

**Ver pools de DHCP no roteador (R-CIN):**

```text
R-CIN# show ip dhcp pool
```

### Passo Final: Testando a Configuração (deve estar presente no relatório)

1. Vá para qualquer PC em qualquer laboratório (ex: `PC-Lab1-01`).
2. Clique no PC.
3. Vá para a aba **Desktop**.
4. Clique em **IP Configuration**.
5. Selecione a opção **DHCP**.

Aguarde alguns segundos. Se tudo foi configurado corretamente, aparecerá "DHCP request successful" e o PC receberá endereço IP, máscara de sub-rede, gateway e servidor DNS da sua respectiva sub-rede.

- Um PC no Lab 1 deve receber um IP como `172.20.X.2`.
- Um PC no Lab 2 deve receber um IP como `172.20.X.66`.
- E assim por diante.

Depois de verificar que os PCs estão recebendo IPs, tente pingar de um PC em uma VLAN para um PC em outra VLAN, confirmando que o roteamento Inter-VLAN está funcionando. Por exemplo, do PC no Lab 1, abra o **Command Prompt** e digite `ping 172.20.X.5`. O primeiro ping pode falhar (devido ao processo ARP), mas os seguintes devem funcionar.

---

## Conceitos Essenciais: Portas de Acesso vs. Trunk

### Portas de Acesso (Access Ports)

- Pertencem a **uma única VLAN**.
- Conectam **dispositivos finais** (PCs, servidores).
- Tráfego **não etiquetado** (*untagged*).
- **No projeto:** portas onde os PCs dos laboratórios se conectam.

**Exemplo:** um PC conectado à porta Fa0/5 de um switch configurado para VLAN 10 só enxerga a VLAN 10.

### Portas Trunk (Trunk Ports)

- Transportam tráfego de **múltiplas VLANs** simultaneamente.
- Conectam **switches a switches** ou **switches a roteadores**.
- Tráfego **etiquetado**, usando o protocolo **IEEE 802.1Q**.
- **No projeto:** conexões entre switches de acesso e switch core, e entre switch core e roteador.

**Exemplo:** a conexão entre Switch-Acesso-Lab1 e Switch-Core transporta tráfego das VLANs 10, 20, 30, 40 e 50.

---

## Fundamentos Teóricos

### O que são VLANs?

**VLAN (Virtual Local Area Network)** é uma tecnologia que permite criar redes lógicas separadas dentro da mesma infraestrutura física.

!!! note "Analogia"
    Imagine um prédio com vários apartamentos. Embora compartilhem a mesma estrutura física, cada apartamento é privado e isolado — VLANs funcionam assim na rede.

**Benefícios das VLANs:**

- **Segurança:** isola o tráfego entre departamentos/grupos.
- **Performance:** reduz domínios de broadcast (menos tráfego desnecessário).
- **Organização:** agrupa logicamente dispositivos, independentemente da localização física.
- **Economia:** não é preciso usar switches separados para cada grupo.

**No projeto do CIn:** cada laboratório é uma VLAN separada — Lab 1 → VLAN 10, Lab 2 → VLAN 20, Lab 3 → VLAN 30, Lab 4 → VLAN 40, Lab 5 → VLAN 50.

### O que é DHCP?

**DHCP (Dynamic Host Configuration Protocol)** automatiza a configuração de rede dos dispositivos.

Sem DHCP, seria preciso configurar manualmente IP, máscara, gateway e DNS em cada PC — com alto risco de erros e conflitos de IP, e muito trabalho em redes grandes. Com DHCP, o PC liga, solicita a configuração, o servidor responde com todas as informações, e a configuração acontece automaticamente, sem erros.

**Funcionamento (processo DORA):**

1. **D**iscover: o PC envia um broadcast — "preciso de um IP!".
2. **O**ffer: o servidor DHCP oferece um IP disponível.
3. **R**equest: o PC aceita a oferta.
4. **A**ck: o servidor confirma e reserva o IP.

### Relação entre VLANs, Sub-redes e DHCP

É crucial entender como esses três conceitos se conectam:

1. **VLAN** (Camada 2 — Enlace): cria isolamento lógico usando tags em quadros Ethernet.
2. **Sub-rede IP** (Camada 3 — Rede): define o espaço de endereçamento (calculado na E2).
3. **Gateway** (Camada 3): porta de saída da VLAN/sub-rede para outras redes.
4. **DHCP**: serviço que automatiza a entrega das configurações (IP, máscara, gateway).

**Exemplo integrado:**

- O PC está na VLAN 10 (tag 802.1Q).
- A VLAN 10 usa a sub-rede `172.20.X.0/24`.
- O gateway da VLAN 10 é `172.20.X.1`.
- O pool DHCP para a VLAN 10 vai de `172.20.X.2` até `172.20.X.62`.
- O PC recebe automaticamente: IP do pool, máscara /24, gateway `.1`.

---

## Dicas e Erros Comuns

| Erro comum | Solução |
| --- | --- |
| VLAN não aparece no switch de acesso | Certifique-se de criar a VLAN em **todos** os switches |
| Trunk não funciona | Verifique se ambas as pontas da conexão estão configuradas como trunk |
| DHCP ainda não funciona | Normal nesta etapa — o DHCP só funcionará por completo após criar as sub-interfaces na E4 |
| Esqueceu de excluir o IP de gateway | O gateway não pode ser distribuído pelo pool; sempre exclua antes de criar o pool |

!!! tip "Dicas"
    - Use nomes descritivos para VLANs — ajuda na documentação e no troubleshooting.
    - Documente todas as portas trunk e access — você precisará disso na apresentação final.
    - O comando `interface range` economiza tempo ao configurar múltiplas portas de uma vez.

**Próxima etapa:** com VLANs e DHCP configurados, você implementará o roteamento Inter-VLAN para permitir comunicação entre os laboratórios (E4).
