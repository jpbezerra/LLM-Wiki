# E1 - Design Físico e Topologia

**Data de Entrega:** 31/10 (sexta-feira)

**Critério Principal:** **Racionalidade** — seu design deve ser lógico, organizado e baseado em princípios sólidos de engenharia de redes.

---

## Equipamentos do Projeto

### Roteador Cisco 2911 (R-CIN)

**Quantidade:** 1 obrigatório

**Função:**

- Roteador de borda (conecta a rede interna à RNP/Internet).
- Realiza roteamento Inter-VLAN usando a técnica Router-on-a-Stick.
- Hospeda o serviço DHCP.

**Por que este modelo?**

- Suporta sub-interfaces lógicas (essencial para ROAS).
- Portas Gigabit Ethernet (evita gargalos).
- Desempenho adequado para o cenário.

### Switch Cisco 3560-24PS (Switch Core)

**Quantidade:** 1 obrigatório

**Função:**

- Ponto central de agregação de todos os switches de acesso.
- Distribui tráfego entre as VLANs.
- Configura portas trunk para transportar múltiplas VLANs.

**Por que este modelo?**

- Switch **multicamada (Layer 3)** — pode rotear entre VLANs.
- Capacidade de processar tráfego em alta velocidade.
- Portas PoE (Power over Ethernet) para expansão futura.

### Switch Cisco 2960-24TT (Switches de Acesso)

**Quantidade:** 7

**Função:**

- Conectar os PCs de cada laboratório.
- Definir portas de acesso para cada VLAN específica.
- Encaminhar tráfego para o Switch Core via trunk.

**Por que este modelo?**

- Switch **Camada 2** otimizado para acesso.
- Suporta VLANs e segurança por porta.
- Custo-efetivo para a densidade de portas necessária.

---

## Documentação para o Relatório

Tabela com os equipamentos:

| Equipamento | Modelo | Qtd | Função na Topologia | Conexões |
| --- | --- | --- | --- | --- |
| Roteador de Borda | 2911 | 1 | ?? | Ex: N (tipo entrada) → Dispositivo alvo, (tipo entrada) |
| Switch Core | 3560-24PS | 1 | ?? | Ex: N (Tipo entrada) → Dispositivo alvo (Tipo entrada) |
| Switch de Acesso | 2960-24TT | 7 | ?? | Ex: N (Tipo entrada) → Dispositivo alvo (Tipo entrada) |
| PCs | PC | 120 | End device | Ex: N (Tipo entrada) → Dispositivo alvo (Tipo entrada) |

Envie também uma captura de tela de como ficou o diagrama final.

Exemplo de captura de tela (lembrando que a rede será bem mais complexa que esse exemplo): um laboratório com 2 switches de acesso (2960-24TT) atendendo 12 PCs cada, ambos ligados por trunk a um Switch Core (3560-24PS), que por sua vez se conecta ao roteador de borda (2911, R-CIN).

??? note "Exemplo de topologia no Packet Tracer"
    ![image.png](../../../../assets/faculdade/periodo5/introducao-a-sistemas-distribuidos-e-redes-de-computadores/projeto-packet-tracer/e1-design-fisico-e-topologia/image.png)

---

## Fundamentos Teóricos

### Modelo Hierárquico da Cisco

Para projetar redes escaláveis e eficientes, a Cisco propõe um modelo hierárquico de **três camadas**:

**1. Camada de Acesso (Access Layer)**

- Onde os dispositivos finais (PCs, impressoras) se conectam à rede.
- Foco: segurança por porta, VLANs, alta densidade de conexões.
- **No seu projeto:** os 7 switches Cisco 2960-24TT (como cada switch tem 24 portas, os labs 1 e 2 precisarão de dois switches).

**2. Camada de Distribuição (Distribution Layer)**

- Agrega tráfego da camada de acesso.
- Aplica políticas de rede e controle de acesso.
- Realiza roteamento e filtragem de pacotes.
- **No seu projeto:** função combinada no Switch Core.

**3. Camada Core**

- Backbone da rede.
- Transporta grandes volumes de dados rapidamente.
- Foco: velocidade e confiabilidade.
- **No seu projeto:** função combinada no Switch Core.

### Core Colapsado (Collapsed Core)

Para redes de pequeno a médio porte, é comum **combinar** as camadas de Distribuição e Core em um único dispositivo. Isso reduz custos, simplifica a gestão e mantém a funcionalidade necessária.

**No projeto do CIn:** o Switch 3560-24PS atua como Core Colapsado.

---

## Dicas Finais

- **Organize visualmente:** uma topologia limpa facilita o troubleshooting futuro.
- **Documente tudo:** adicione anotações e use nomenclaturas claras para cada item.
- **Lembre-se:** este design será a base para todas as entregas seguintes.

**Próxima etapa:** com a topologia física pronta, você partirá para o planejamento de endereçamento IP usando VLSM (E2).
