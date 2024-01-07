# Sheet No. 2 - Group Communication Models in TCP/IP Networks

### 1. Objectives

Carry out self-assessment of knowledge by solving typical questions.

### 2. Questions

#### 2.1 The multicast service, whether at the application level or the network level, relies on virtual delivery infrastructures designated as distribution trees. Typically, these trees can be: (i) built by an active source or (ii) shared.

a. **Explain how both models differ, highlighting the role of the main entities involved.**

   - **Source-Based Tree:** In this model, each multicast source has a unique distribution tree for the multicast group. The tree is optimized for the source and the receivers of that specific group, ensuring the best possible route from each source to all receivers. The main entity involved is the data source that acts as the root of the tree.

   - **Shared Tree:** In this model, all members of a multicast group share a single distribution tree. The tree is not optimized for any specific source but allows for simpler configuration and less routing overhead. The designated rendezvous point (RP) is the main entity, acting as the root of the tree for all group members.

b. **Explain the process of building type (i) and type (ii) trees.**

   - **Type (i) Source-Based Tree:** The tree is built through the specific routing protocol, where each router on the path from the source to the receiver joins the tree, forwarding packets to additional branches as needed to reach all group members.

   - **Type (ii) Shared Tree:** First, the RP must be identified. Then, both the sources and receivers register with the RP. Data is initially sent to the RP, which then distributes the data along the shared tree to all receivers.

c. **List advantages and disadvantages of each model in terms of performance.**

   - **Source-Based Tree:**
     - Advantages: Optimized paths for each source, efficiency in data delivery.
     - Disadvantages: Requires more resources and greater overhead due to the maintenance of multiple trees.

   - **Shared Tree:**
     - Advantages: Lower routing overhead, easier to manage.
     - Disadvantages: Data delivery path may not be ideal (greater latency).

#### 2.2 The PIM (Protocol Independent Multicast) protocol allows creating support for multicast forwarding at the network level. Why does the PIM protocol contemplate (and implement) two distinct modes of operation, PIM-SM (Sparse Mode) and PIM-DM (Dense Mode)? Give practical examples where the use of one or the other protocol version is justified.

PIM-SM (Sparse Mode) is used in networks where group members are dispersed and PIM-DM (Dense Mode) is more suitable for dense groups. For example, PIM-SM is ideal for applications such as Internet TV where users are spread out, while PIM-DM could be used in internal networks of an organization where there are many users interested in a broadcast.

#### 2.3 The PIM-SM (Protocol Independent Multicast Sparse Mode) protocol generally uses a shared tree (shared tree) to create support for multicast forwarding at the network level and for this, it uses an overlay network. Is this statement true? Answer and justify your response.

The statement is true. PIM-SM uses a shared tree centered on an RP to facilitate the construction of an efficient multicast distribution network. The use of an overlay network allows PIM-SM to flexibly adapt to various network topologies and dynamic conditions, facilitating scalability and multicast routing management.



# Sheet No. 3 - Multimedia Networking

### 1. Objectives

Carry out self-assessment of knowledge by solving typical questions.

### 2. Questions

#### Audio and Video

1. **Assume that the Monster is watching a video encoded at 4 Mbps and Bella is listening to an audio encoded at 200 kbps and that both sessions last one hour. Compare the sessions in terms of the volume of data transferred (in MBytes) and sensitivity to delays and losses.**

   **Data Volume:**
   - Video: 4 Mbps * 3600s = 14,400 Mbits = 1800 MBytes
   - Audio: 200 kbps * 3600s = 720 Mbits = 90 MBytes
   
   **Sensitivity:**
   - Video: More sensitive to delays and losses as they affect perceived quality and continuity.
   - Audio: Sensitive to delays and losses, but generally has more effective correction mechanisms and can tolerate minor losses without significantly affecting comprehension.

2. **There are two types of redundancy in video. Describe them and discuss how they can be exploited for efficient video compression. What is the cost/benefit of the compression process?**

   - **Spatial Redundancy:** Refers to the similarity between adjacent regions within the same video frame. Can be exploited by techniques such as transformation and quantization to reduce data size.
   - **Temporal Redundancy:** Refers to the similarity between consecutive frames. Can be exploited by motion prediction and motion compensation techniques.
   
   **Cost/Benefit:**
   - **Cost:** Greater computational complexity and possible delays due to processing.
   - **Benefit:** Significant reduction in data volume, facilitating storage and transmission.

3. **Suppose an analog audio signal is sampled 16,000 times per second and each sample is quantized into one of 1,024 levels. What would be the resulting bit rate of the digital PCM audio signal?**

   - Sampling rate: 16,000 samples/second
   - Quantization levels: 1,024 levels = 10 bits per sample (2^10 = 1,024)
   - Bit rate = 16,000 * 10 = 160 kbps

4. **Multimedia applications can be classified into three main categories. Identify and describe each category. Give concrete examples of applications or services in each category.**

   - **Entertainment:** Applications focused on leisure and entertainment. Ex: Video streaming (Netflix, YouTube), online gaming.
   - **Communication:** Applications focused on facilitating interpersonal communication. Ex: Video conferencing (Zoom, Skype), VoIP.
   - **Education and Training:** Applications focused on teaching and learning. Ex: E-learning platforms (Coursera, Udemy).

#### Video Streaming

1. **Identify and describe two protocol solutions for supporting video streaming over HTTP. Compare these solutions in terms of performance.**

   - **HLS (HTTP Live Streaming):** Splits content into small file segments, allowing for quality adaptation of video to network conditions. Offers good efficiency and broad compatibility.
   - **DASH (Dynamic Adaptive Streaming over HTTP):** An open standard that allows real-time multimedia content adaptation. Supports more customization and is highly adaptable.
   
   **Comparison:**
   - HLS is more widely supported and easier to implement, but DASH offers greater flexibility and efficiency on variable networks.

2. **Identify and explain potential drawbacks that can affect a video streaming service over UDP.**

   - **Lack of reliability:** UDP does not guarantee packet delivery, which can result in data loss and degraded video quality.
   - **Latency variation (Jitter):** Can cause variation in packet delivery time, affecting smooth video playback.

3. **Consider the non-adaptive HTTP video streaming model. Suppose the server sends at a constant rate of 2 Mbps and playback begins when 8 Mbits are received. Under these conditions, what is the expected initial delay (buffering delay) or when will playback occur?**

   - Transmission rate: 2 Mbps
   - Initial buffer: 8 Mbits
   - Initial delay (buffering delay) = 8 Mbits / 2 Mbps = 4 seconds

#### Voice over IP Service

1. **Characterize the voice over IP service in terms of quality and service sensitivity to variations in the performance of the underlying IP network.**

   - **Quality:** Can vary depending on latency, jitter, and packet loss in the network. Techniques like QoS can be used to ensure quality.
   - **Sensitivity:** Highly sensitive to variations, especially latency and jitter, which can cause delays or loss of voice quality.

2. **Explain one of the studied methods that allows the receiver to recover from eventual voice packet losses.**

   - **Packet repetition:** The receiver may request retransmission of lost packets or use previously received packets to fill in gaps.

#### SIP Signaling Protocol

1. **What objectives does the SIP protocol aim to address?**

   - Establishing, modifying, and terminating multimedia communication sessions.
   - Supporting user mobility and interoperability between different devices and networks.

2. **Identify and describe the main entities that support the operation of the SIP protocol.**

   - **User Agent:** Client that initiates and terminates communication sessions.
   - **Proxy Server:** Forwards requests and responses between user agents and other servers.
   - **Registrar Server:** Registers the locations of user agents.

3. **Illustrate through an example the establishment of a session between two SIP users located: (i) in the same SIP domain; and (ii) in different SIP domains.**

   - **Same Domain:** User Agent A sends a SIP invitation to the Proxy Server which then forwards it to User Agent B in the same domain. Communication is established directly after B's response.
   - **Different Domains:** User Agent A sends an invitation that is forwarded through multiple proxies until reaching User Agent B in another domain. After negotiating the parameters, the session is established between the two domains.


## Sheet No. 4 - Multimedia Networking: Transport Protocols

### 1. Objectives

Carry out self-assessment of knowledge by solving typical questions.

### 2. Questions

#### Real-Time Support: RTP/RTCP

1. **In the design of various network services, the Real-Time Protocol (RTP) and Real-Time Control Protocol (RTCP) play an important role.**

   a. **State the purpose of these protocols and how they are articulated in the same session.**
      - **RTP (Real-Time Protocol):** Used for delivering data that has real-time requirements such as audio and video. Allows for sequential and timely delivery of multimedia.
      - **RTCP (Real-Time Control Protocol):** Works alongside RTP, providing feedback about the quality of data distribution, allowing for monitoring and controlling the session. Together, they facilitate synchronization and identification of participants in a multimedia communication session.

   b. **If RTP does not guarantee the delivery of real-time data why is it designated as “real-time”?**
      - The term "real-time" refers to the intent of delivering data for processing or playback as close as possible to the moment the data is captured. Even without guaranteeing delivery, RTP is optimized to reduce delays, maintaining sequence, and enabling smooth playback of multimedia content.

   c. **Briefly describe the type of reports RTCP encompasses and their purpose.**
      - **RTCP Reports:** Include sender reports providing information about the amount of data sent and packet loss rate, receiver reports giving feedback on the quality of reception, and SDES (Source Description) reports providing information about the participants' identity. The purpose is to improve the quality of communication by adjusting transmission parameters and diagnosing issues.

#### New Protocol Options: SCTP and QUIC

1. **Despite TCP being one of the most used transport protocols on the Internet, it has characteristics that can be inconvenient for certain applications.**

   a. **Explain the motivation behind the emergence of protocols like SCTP and QUIC.**
      - SCTP and QUIC were developed to overcome TCP limitations such as latency sensitivity, lack of multi-streaming, and slow connection startup. They offer improvements like multiplexing of streams, out-of-order delivery, more efficient error recovery, and reduced latency in connection initiation, making them more suitable for applications that demand improved performance and reliability, like multimedia communications.

   b. **Describe the features of the SCTP protocol emphasizing the functionalities offered at the application level. Give examples of applications or services that can benefit from its use.**
      - **SCTP Features:** Includes multihoming (support for multiple network interfaces), multi-streaming (allows multiple independent streams of data within a single connection), and out-of-order data delivery. Offers non-blocking reliability at the transport level.
      - **Benefited Applications:** VoIP, live video broadcasting, instant messaging systems, where order and data integrity are critical.

2. **Provide a comparative assessment of the SCTP, TCP, and UDP protocols in relation to their services considering: “Reliable data transfer”; “Unordered data delivery” “Selective acks” “Multistreaming” and “Multihoming. Explain the function of each service and for each give examples of applications based on them.**

   - **Reliable Data Transfer:**
     - TCP and SCTP offer reliable data transfer, while UDP does not.
     - Applications such as file transfer and email benefit from the reliability of TCP/SCTP.
   - **Unordered Data Delivery:**
     - UDP and SCTP allow out-of-order data delivery; TCP does not.
     - Online games and video streaming can benefit from out-of-order data delivery to maintain fluidity.
   - **Selective Acks:**
     - SCTP and TCP (with extensions) support selective acknowledgments for more efficient error recovery.
     - Useful in applications requiring quick recovery of lost packets like video conferencing.
   - **Multistreaming:**
     - SCTP allows multiple streams within a connection; TCP and UDP do not.
     - Benefits applications that deal with multiple types of data simultaneously, like some communication protocols.
   - **Multihoming:**
     - SCTP supports multihoming; TCP and UDP do not.
     - Applications requiring high availability and fault resilience, like database servers, can benefit from multihoming.

3. **Make a comparative analysis between the connection establishment times among TCP, TCP+TLS, and QUIC protocols. In each situation describe how the connection establishment process takes place considering the scenario of a new connection.**

   - **TCP:** Requires a three-way handshake to establish a connection, which can introduce latency.
   - **TCP+TLS:** In addition to TCP's handshake, requires an additional handshake for TLS, increasing latency.
   - **QUIC:** Combines transport and security negotiation in a single handshake, reducing latency compared to TCP+TLS.
   - In a new connection, QUIC is faster due to its efficient parameter negotiation and built-in support for security.

4. **In HTTP/3, TCP is not used at the transport layer. Provide a comparative assessment between HTTP/1.1, HTTP/2, and HTTP/3 considering the differences related to the transport layer and security aspects. Comment on the advantages and disadvantages associated.**

   - **HTTP/1.1:** Uses TCP. Each request/response requires a separate TCP connection, causing latency.
   - **HTTP/2:** Also uses TCP, but allows multiple requests and responses in parallel over a single connection (multiplexing).
   - **HTTP/3:** Uses QUIC instead of TCP, providing faster connection startup, multiplexing, and improved error recovery. Offers built-in security similar to TLS.
   - **Advantages of HTTP/3:** Lower latency, improved performance on unstable connections, integrated security.
   - **Disadvantages of HTTP/3:** More complex implementation and support compared to previous versions.






   