# Universidade do Minho MEI/MIEI Eng. De Serviços em Rede 2023/2024

## Ficha de auto-avaliação Nº3 – Multimedia Networking

### 1. Objetivos

Efetuar a auto-avaliação de conhecimentos através da resolução de questões tipo.

### 2. Questões

#### Áudio e Vídeo

1. **Assuma que o Monstro está a assistir a um vídeo codificado a 4 Mbps e a Bela a ouvir um áudio codificado a 200 kbps e que ambas as sessões têm a duração de uma hora. Compare as sessões em termos do volume de dados transferido (em MBytes) e sensibilidade a atrasos e perdas.**

   **Volume de Dados:**
   - Vídeo: 4 Mbps * 3600s = 14,400 Mbits = 1800 MBytes
   - Áudio: 200 kbps * 3600s = 720 Mbits = 90 MBytes
   
   **Sensibilidade:**
   - Vídeo: Mais sensível a atrasos e perdas, pois afetam a qualidade percebida e continuidade.
   - Áudio: Sensível a atrasos e perdas, mas geralmente tem mecanismos de correção mais eficazes e pode tolerar perdas menores sem afetar significativamente a compreensão.

2. **Existem dois tipos de redundância em vídeo. Descreva-os e discuta como podem ser explorados para obter uma compactação eficiente do vídeo. Qual o custo/benefício do processo de compactação?**

   - **Redundância Espacial:** Refere-se à semelhança entre regiões adjacentes dentro do mesmo quadro de vídeo. Pode ser explorada por técnicas como a transformação e quantização para reduzir o tamanho dos dados.
   - **Redundância Temporal:** Refere-se à semelhança entre quadros consecutivos. Pode ser explorada por técnicas de previsão de movimento e compensação de movimento.
   
   **Custo/Benefício:**
   - **Custo:** Maior complexidade computacional e possíveis atrasos devido ao processamento.
   - **Benefício:** Redução significativa no volume de dados, facilitando armazenamento e transmissão.

3. **Suponha que um sinal de áudio analógico é amostrado 16000 vezes por segundo e cada amostra é quantizada num de 1024 níveis. Qual seria a taxa de bits resultante do sinal áudio digital PCM?**

   - Taxa de amostragem: 16000 amostras/segundo
   - Níveis de quantização: 1024 níveis = 10 bits por amostra (2^10 = 1024)
   - Taxa de bits = 16000 * 10 = 160 kbps

4. **As aplicações multimédia podem ser classificadas em três categorias principais. Identifique e descreva cada categoria. Dê exemplos concretos de aplicações ou serviços em cada categoria.**

   - **Entretenimento:** Aplicações focadas no lazer e entretenimento. Ex: Streaming de vídeo (Netflix, YouTube), jogos online.
   - **Comunicação:** Aplicações focadas em facilitar a comunicação interpessoal. Ex: Videoconferência (Zoom, Skype), VoIP.
   - **Educação e Formação:** Aplicações focadas em ensino e aprendizagem. Ex: Plataformas de e-learning (Coursera, Udemy).

#### Vídeo Streaming

1. **Identifique e descreva duas soluções protocolares para o suporte do serviço de vídeo streaming sobre HTTP. Compare essas soluções em termos de desempenho.**

   - **HLS (HTTP Live Streaming):** Divisão do conteúdo em pequenos segmentos de arquivo, permitindo a adaptação da qualidade do vídeo às condições de rede. Oferece boa eficiência e ampla compatibilidade.
   - **DASH (Dynamic Adaptive Streaming over HTTP):** Padrão aberto que permite a adaptação de conteúdo multimídia em tempo real. Suporta mais personalização e é altamente adaptável.
   
   **Comparação:**
   - HLS é mais amplamente suportado e mais fácil de implementar, mas DASH oferece maior flexibilidade e eficiência em redes variáveis.

2. **Identifique e explique potenciais inconvenientes que podem afetar um serviço de vídeo streaming sobre UDP.**

   - **Falta de confiabilidade:** UDP não garante a entrega de pacotes, podendo resultar em perda de dados e degradação da qualidade do vídeo.
   - **Variação de latência (Jitter):** Pode causar variação no tempo de entrega dos pacotes, afetando a reprodução suave do vídeo.

3. **Considere o modelo de vídeo streaming sobre HTTP (não adaptativo). Suponha que o servidor envia a uma taxa constante de 2Mbps e a reprodução começa quando forem recebidos 8Mbits. Nestas condições qual é o atraso inicial expectável (buffering delay) ou seja quando ocorrerá o playout?**

   - Taxa de transmissão: 2Mbps
   - Buffer inicial: 8Mbits
   - Atraso inicial (buffering delay) = 8Mbits / 2Mbps = 4 segundos

#### Serviço de Voz sobre IP

1. **Caracterize o serviço de voz sobre IP em termos de qualidade e sensibilidade do serviço face a variações no desempenho da rede IP subjacente.**

   - **Qualidade:** Pode variar dependendo da latência, jitter e perda de pacotes na rede. Técnicas como QoS podem ser usadas para garantir a qualidade.
   - **Sensibilidade:** Altamente sensível a variações, especialmente a latência e jitter, que podem causar atrasos ou perda de qualidade na voz.

2. **Explique um dos métodos estudados que permita ao recetor recuperar eventual perda de pacotes de voz.**

   - **Repetição de pacotes:** O recetor pode solicitar a retransmissão de pacotes perdidos ou usar pacotes recebidos anteriormente para preencher as lacunas.

#### Protocolo de Sinalização SIP

1. **Diga quais os objetivos a que o protocolo SIP pretende dar resposta?**

   - Estabelecimento, modificação e término de sessões de comunicação multimídia.
   - Suporte para mobilidade do usuário e interoperabilidade entre diferentes dispositivos e redes.

2. **Identifique e descreva as principais entidades que sustentam a operação do protocolo SIP.**

   - **User Agent:** Cliente que inicia e termina as sessões de comunicação.
   - **Proxy Server:** Encaminha pedidos e respostas entre user agents e outros servidores.
   - **Registrar Server:** Registra as localizações dos user agents.

3. **Ilustre através de um exemplo o estabelecimento de uma sessão entre dois utilizadores SIP localizados: (i) no mesmo domínio SIP; e (ii) em domínios SIP diferentes.**

   - **Mesmo Domínio:** O User Agent A envia um convite SIP ao Proxy Server que, por sua vez, encaminha ao User Agent B no mesmo domínio. A comunicação é estabelecida diretamente após a resposta de B.
   - **Domínios Diferentes:** O User Agent A envia um convite que é encaminhado através de múltiplos proxies até alcançar o User Agent B em outro domínio. Após a negociação dos parâmetros, a sessão é estabelecida entre os dois domínios.
