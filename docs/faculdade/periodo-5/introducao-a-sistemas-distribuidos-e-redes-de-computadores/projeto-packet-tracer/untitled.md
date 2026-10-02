# Untitled

### **1. Descrição**
Vocês são a Equipe de Elite de Analistas de Redes e foram convocados para um desafio de vida ou morte no mundo da conectividade: acabar de uma vez por todas com o caótico problema de lentidão, configuração errada e desperdício de IPs e equipamentos nos laboratórios do Centro de Informática da UFPE.
A missão é clara: a rede está um “caótica” de configurações antigas e endereçamento ineficiente. A única solução é estruturar a rede do zero.
A alta gerência decidiu que cada grupo de analistas criará um projeto-piloto completo. A rede de produção será montada com base naquele que apresentar a melhor solução técnica e o uso mais eficiente de recursos.
Para guiar seu trabalho, os seguintes critérios listados neste documento são invioláveis.
### **2. Objetivo**
O objetivo é planejar e documentar a reestruturação completa de uma instância virtual da rede do CIn, demonstrando domínio em VLSM, VLANs, e Roteamento (Inter-VLAN e Externo).
### **Requisitos e Cenário**
- **Bloco IP Único:** Cada grupo pode encontrar o seu bloco IP na planilha de grupos do Classroom.
- **VLSM Obrigatório:** Seu grupo deve usar o bloco ‘/24‘ para criar cinco sub-redes com os tamanhos apropriados dos laboratórios simulados, aplicando VLSM para minimizar o desperdício de IP:
	1. Sub-rede para 35 hosts (precisará de 2 switches)
	2. Sub-rede para 30 hosts (precisará de 2 switches)
	3. Sub-rede para 20 hosts
	4. Sub-rede para 20 hosts
	5. Sub-rede para 15 hosts
- **Conectividade Externa (Provedor Pronto):** O Roteador do CIn (R-CIN) conecta-se à RNP em ‘2.2.2.2 /30‘.
### **Equipamentos Disponíveis por Grupo (Uso Mínimo/Máximo)**
O grupo deve planejar o uso eficiente dos seguintes recursos:
<table>
<tr>
<td>**Equipamento**</td>
<td>**Tipo**</td>
<td>**Quantidade.**</td>
<td>**Função Primária**</td>
</tr>
<tr>
<td>Roteador (R-CIN)</td>
<td>2911</td>
<td>1</td>
<td>Roteamento Inter-VLAN e Conexão WAN.</td>
</tr>
<tr>
<td>Switch Core</td>
<td>3560-24PS</td>
<td>1</td>
<td>Ponto central de distribuição, Trunks e DHCP.</td>
</tr>
<tr>
<td>Switch de Acesso</td>
<td>2960-24TT</td>
<td>7</td>
<td>Conexão dos hosts e definição das portas de acesso.</td>
</tr>
<tr>
<td>Máquinas/Hosts</td>
<td>PCs</td>
<td>Tamanho do Lab</td>
<td>PCs ou Laptops para testes (DHCP e conectividade).</td>
</tr>
</table>
### **3. Estrutura de Entregas e Cronograma (Valor Total: 10,0)**
A avaliação será feita através de Relatórios Concisos e Técnicos que detalham o design e a conclusão de cada etapa.
<table>
<tr>
<td>**E**</td>
<td>**Tópico Principal**</td>
<td>**Conteúdo (Foco do Relatório)**</td>
<td>**Data de Entrega**</td>
<td>**Valor**</td>
</tr>
<tr>
<td>**E1**</td>
<td>Design Físico e Topologia</td>
<td>Diagrama, alocação de equipamentos e justificativas.</td>
<td>31/10/2025</td>
<td>2,0</td>
</tr>
<tr>
<td>**E2**</td>
<td>Design de Endereçamento VLSM</td>
<td>Tabela de VLSM (cálculos e IPs) e eficiência da alocação.</td>
<td>05/11/2025</td>
<td>2,0</td>
</tr>
<tr>
<td>**E3**</td>
<td>Design de Segmentação (VLANs/DHCP)</td>
<td>Lista de VLANs, estratégia de DHCP e mapeamento de portas.</td>
<td>07/11/2025</td>
<td>2,0</td>
</tr>
<tr>
<td>**E4**</td>
<td>Roteamento InterVLAN e Conectividade</td>
<td>Comandos de subinterfaces, rota padrão e evidência de conectividade.</td>
<td>12/11/2025</td>
<td>2,0</td>
</tr>
<tr>
<td>E5</td>
<td>Apresentação Final do Projeto</td>
<td>(Demonstração e Desafios)</td>
<td>19/11/2025</td>
<td>2,0</td>
</tr>
</table>
### **4. Entregas**
Em cada guia do projeto, há uma seção chamada **"Documentação para o Relatório"** com a documentação necessária para cada entrega.
### **4.1 E1: Design Físico e Topologia (2,0 Pontos)**
- **Documento (Relatório):** Diagrama de Topologia, justificativa do número de Switches de Acesso e identificação clara das portas Trunk e Access.
- **Critério Principal:** Racionalidade. O design deve ser lógico, organizado e capaz de suportar as 5 VLANs.
### **4.2 E2: Design de Endereçamento VLSM (2,0 Pontos)**
- **Documento (Relatório):** Tabela IP de VLSM Completa, mostrando a ordem de alocação (da maior para a menor), Máscara (/X) e Endereço do Gateway.
- **Critério Principal:** Minimização do Desperdício. O uso do bloco /24 deve ser o mais eficiente possível.
### **4.3 E3: Design de Segmentação (VLANs/DHCP) (2,0 Pontos)**
- **Documento (Relatório):** Lista de VLANs, Configuração IP estática ou Estratégia DHCP (escolha e comandos-chave dos pools), que pode ser no roteador, no switch core ou um Server-PT (DHCP Service) e Tabela resumindo as configurações de portas Trunk e Access.
- **Critério Principal:** Lógica e Funcionalidade. A estratégia de DHCP deve ser funcional e as portas de tronco devem suportar todas as VLANs.
### **4.4 E4: Roteamento Inter-VLAN e Conectividade (2,0 Pontos)**
- **Documento (Relatório):** Comandos das Subinterfaces, se usou algum protocolo (ex.: OSPF) e da Rota Padrão para o RNP.
- **Teste de Conectividade:** Evidências (logs ou capturas de tela) do teste de comunicação entre dois hosts em VLANs diferentes e de um host para a RNP.
- **Critério Principal:** Conectividade Total. O roteamento deve ser transparente da LAN para o backbone.
### **4.5 E5: Apresentação Final do Projeto (2,0 Pontos)**
- **Documento (Relatório):** Relatório final, juntando todas as etapas e a conclusão com desafios e lições aprendidas.
- **Apresentação de Funcionamento:** Realização de testes e demonstrações dos comandos usados durante a construção do projeto.
- **Critério Principal:** Conectividade Total. Os PCs devem conversar entre si e navegar na Internet.
