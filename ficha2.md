# Universidade do Minho MEI/MIEI Eng. De Serviços em Rede 2023/2024

## Ficha de auto-avaliação Nº2 – Modelos de Comunicação em Grupo em Redes TCP/IP

### 1. Objetivos

Efetuar a auto-avaliação de conhecimentos através da resolução de questões tipo.

### 2. Questões

#### 2.1 O serviço multicast seja a nível aplicacional ou a nível de rede assenta em infraestruturas virtuais de entrega designadas por árvores de distribuição. Tipicamente estas árvores podem ser: (i) construídas por fonte ativa ou (ii) partilhadas.

a. **Explique em que se diferenciam ambos os modelos salientando o papel das principais entidades envolvidas.**

   - **Árvore construída por fonte ativa (Source-Based Tree):** Neste modelo, cada fonte de multicast tem uma árvore de distribuição única para o grupo de multicast. A árvore é otimizada para a fonte e os receptores desse grupo específico, garantindo a melhor rota possível de cada fonte para todos os receptores. A entidade principal envolvida é a fonte de dados que atua como a raiz da árvore.

   - **Árvore partilhada (Shared Tree):** Neste modelo, todos os membros de um grupo multicast compartilham uma única árvore de distribuição. A árvore não é otimizada para nenhuma fonte específica, mas permite uma configuração mais simples e menos sobrecarga de roteamento. O ponto de encontro designado (Rendezvous Point - RP) é a principal entidade, agindo como a raiz da árvore para todos os membros do grupo.

b. **Explique o processo de construção das árvores do tipo (i) e do tipo (ii).**

   - **Tipo (i) Source-Based Tree:** A árvore é construída através do protocolo de roteamento específico, onde cada roteador no caminho da fonte ao receptor se junta à árvore, encaminhando pacotes para ramos adicionais conforme necessário para alcançar todos os membros do grupo.

   - **Tipo (ii) Shared Tree:** Primeiro, é necessário identificar o RP. Depois, tanto as fontes quanto os receptores se registram no RP. Os dados são inicialmente enviados para o RP, que então distribui os dados ao longo da árvore partilhada para todos os receptores.

c. **Enuncie vantagens e desvantagens de cada modelo em termos de desempenho.**

   - **Source-Based Tree:**
     - Vantagens: Caminhos otimizados para cada fonte, eficiência na entrega de dados.
     - Desvantagens: Requer mais recursos e maior sobrecarga devido à manutenção de múltiplas árvores.

   - **Shared Tree:**
     - Vantagens: Menor sobrecarga de roteamento, mais fácil de gerir.
     - Desvantagens: Caminho de entrega de dados pode não ser o ideal (maior latência).

#### 2.2 O protocolo PIM (Protocol Independent Multicast) permite criar suporte para encaminhamento multicast ao nível de rede. Por que razão o protocolo PIM contempla (e implementa) dois modos de operação distintos o PIM-SM (Sparse Mode) e o PIM-DM (Dense Mode)? Dê exemplos práticos em que se justifica a utilização de uma ou outra versão do protocolo.

PIM-SM (Sparse Mode) é usado em redes onde membros de grupo são dispersos e PIM-DM (Dense Mode) é mais adequado para grupos densos. Por exemplo, PIM-SM é ideal para aplicações como TV via Internet onde os utilizadores estão espalhados, enquanto PIM-DM pode ser usado em redes internas de uma organização onde há muitos utilizadores interessados numa transmissão.

#### 2.3 O protocolo PIM-SM (Protocol Independent Multicast Sparse mode) geralmente utiliza uma árvore partilhada (shared tree) para criar suporte para encaminhamento multicast ao nível de rede e para isto utiliza uma rede overlay. Esta afirmação é verdadeira? Responda e justifique a sua resposta.

A afirmação é verdadeira. PIM-SM utiliza uma árvore partilhada centrada em um RP para facilitar a construção de uma rede de distribuição multicast eficiente. A utilização de uma rede overlay permite que o PIM-SM se adapte de forma flexível a várias topologias de rede e condições dinâmicas, facilitando a escalabilidade e a gestão do encaminhamento multicast.
