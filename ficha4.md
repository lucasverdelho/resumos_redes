# Universidade do Minho MEI/MIEI Eng. De Serviços em Rede 2022/2023

## Ficha de auto-avaliação Nº4 – Multimedia Networking: Protocolos de Transporte

### 1. Objetivos

Efetuar a auto-avaliação de conhecimentos através da resolução de questões tipo.

### 2. Questões

#### Suporte a Tempo-Real: RTP/RTCP

1. **Na conceção de diversos serviços em rede os protocolos Real-Time Protocol (RTP) e Real-Time Control Protocol (RTCP) têm um papel importante.**

   a. **Diga qual o propósito destes protocolos e a forma como estão articulados numa mesma sessão.**
      - **RTP (Real-Time Protocol):** Utilizado para a entrega de dados que têm requisitos de tempo real como áudio e vídeo. Permite a entrega sequencial e no tempo certo de multimídia.
      - **RTCP (Real-Time Control Protocol):** Funciona juntamente com o RTP, fornecendo feedback sobre a qualidade da distribuição dos dados, permitindo monitorizar e controlar a sessão. Juntos, facilitam a sincronização e a identificação dos participantes numa sessão de comunicação multimídia.

   b. **Se o protocolo RTP não garante a entrega de dados em tempo-real porque razão é designado de “tempo-real”?**
      - O termo "tempo-real" refere-se à intenção de entrega de dados para processamento ou reprodução em um tempo tão próximo quanto possível ao momento em que os dados são capturados. Mesmo sem garantir a entrega, o RTP é otimizado para reduzir atrasos, mantendo a sequência e permitindo a reprodução fluente de conteúdo multimídia.

   c. **Descreva resumidamente que tipo de reports o RTCP contempla e a sua finalidade.**
      - **Reports do RTCP:** Incluem relatórios de remetente (sender reports) que fornecem informações sobre a quantidade de dados enviados e a taxa de perda de pacotes, relatórios de recepção (receiver reports) que dão feedback sobre a qualidade da receção, e relatórios de SDES (Source Description) que fornecem informações sobre a identidade dos participantes. A finalidade é melhorar a qualidade da comunicação ajustando parâmetros de transmissão e diagnóstico de problemas.

#### Novas opções protocolares: SCTP e QUIC

1. **Apesar do TCP ser dos protocolos de transporte mais usado na Internet apresenta características que podem ser um inconveniente para certas aplicações.**

   a. **Explique a motivação subjacente ao aparecimento de protocolos como o SCTP e o QUIC.**
      - SCTP e QUIC foram desenvolvidos para superar limitações do TCP como a sensibilidade a latência, falta de multistreaming, e lentidão no início da conexão. Eles oferecem melhorias como multiplexação de fluxos, entrega fora de ordem, recuperação de erro mais eficiente, e menor latência na inicialização de conexão, tornando-os mais adequados para aplicações que exigem desempenho e confiabilidade melhorados, como comunicações multimídia.

   b. **Descreva as características do protocolo SCTP salientando as funcionalidades oferecidas ao nível aplicacional. Dê exemplos de aplicações ou serviços que podem beneficiar do seu uso.**
      - **Características do SCTP:** Inclui multihoming (suporte para múltiplas interfaces de rede), multistreaming (permite múltiplos fluxos independentes de dados dentro de uma única conexão), e entrega de dados fora de ordem. Oferece confiabilidade sem bloqueio no nível de transporte.
      - **Aplicações Beneficiadas:** VoIP, transmissão de vídeo ao vivo, sistemas de mensagens instantâneas, onde a ordem e a integridade dos dados são críticas.

2. **Faça uma Avaliação comparativa dos protocolos SCTP, TCP e UDP em relação aos seus serviços levando em conta: “Reliable data transfer”; “Unordered data delivery” “Selective acks” “Multistreaming” e “Multihoming. Explique o funcionamento de cada serviço e para cada um dê exemplos de aplicações que baseadas em cada um deles.**

   - **Reliable Data Transfer:**
     - TCP e SCTP oferecem transferência de dados confiável, enquanto UDP não.
     - Aplicações como transferência de arquivo e e-mail beneficiam-se da confiabilidade do TCP/SCTP.
   - **Unordered Data Delivery:**
     - UDP e SCTP permitem entrega de dados fora de ordem; TCP não.
     - Jogos online e streaming de vídeo podem se beneficiar da entrega de dados fora de ordem para manter a fluidez.
   - **Selective Acks:**
     - SCTP e TCP (com extensões) suportam ACKs seletivos para uma recuperação de erro mais eficiente.
     - Útil em aplicações que requerem uma recuperação rápida de pacotes perdidos como videoconferência.
   - **Multistreaming:**
     - SCTP permite múltiplos fluxos dentro de uma conexão; TCP e UDP não.
     - Beneficia aplicações que lidam com múltiplos tipos de dados simultaneamente, como alguns protocolos de comunicação.
   - **Multihoming:**
     - SCTP suporta multihoming; TCP e UDP não.
     - Aplicações que necessitam de alta disponibilidade e resistência a falhas, como servidores de banco de dados, podem se beneficiar do multihoming.

3. **Faça uma análise comparativa entre os tempos para estabelecimento de conexão entre os protocolos TCP, TCP+TLS e QUIC. Em cada situação descreva como é o processo de estabelecimento de conexão levando em conta o cenário de uma nova conexão.**

   - **TCP:** Requer um handshake de três vias para estabelecer uma conexão, o que pode introduzir latência.
   - **TCP+TLS:** Além do handshake do TCP, requer um handshake adicional para o TLS, aumentando a latência.
   - **QUIC:** Combina transporte e negociação de segurança em um único handshake, reduzindo a latência em comparação ao TCP+TLS.
   - Em uma nova conexão, QUIC é mais rápido devido à sua eficiente negociação de parâmetros e suporte embutido para segurança.

4. **No HTTP/3 não utiliza TCP na camada de transporte. Faça uma avaliação comparativa entre HTTP/1.1, HTTP/2 e HTTP/3 levando em conta as diferenças relacionadas à camada de transporte e ainda relacionadas aos aspetos de segurança. Comente as vantagens e desvantagens associadas.**

   - **HTTP/1.1:** Usa TCP. Cada requisição/resposta requer uma conexão TCP separada, causando latência.
   - **HTTP/2:** Também usa TCP, mas permite múltiplas requisições e respostas em paralelo sobre uma única conexão (multiplexação).
   - **HTTP/3:** Usa QUIC em vez de TCP, proporcionando uma inicialização de conexão mais rápida, multiplexação e recuperação de erro melhorada. Oferece segurança embutida similar ao TLS.
   - **Vantagens de HTTP/3:** Menor latência, melhor desempenho em conexões instáveis, segurança integrada.
   - **Desvantagens de HTTP/3:** Implementação e suporte mais complexos em comparação com as versões anteriores.
