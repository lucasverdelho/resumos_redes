# Sheet No. 2 - Group Communication Models in TCP/IP Networks

### 1. Objectives

Carry out self-assessment of knowledge by solving typical questions.

### 2. Questions

#### 2.1 The multicast service, whether at the application level or the network level, relies on virtual delivery infrastructures designated as distribution trees. Typically, these trees can be: (i) built by an active source or (ii) shared.

a. **Explain how both models differ, highlighting the role of the main entities involved.**

- **Source-Based Tree:** This model is centered around the data source, with a unique tree constructed for each source in the multicast group. The tree's paths are optimized specifically for that source's route to the receivers, potentially providing the most efficient delivery. The data source serves as the root, with the tree branching out to include all receivers of the multicast group.

- **Shared Tree:** Unlike the Source-Based Tree, the Shared Tree model involves one common distribution tree used by all sources for a multicast group. This tree isn't tailored to a specific source but offers a general approach that simplifies management and reduces resource consumption. The key entity here is the Rendezvous Point (RP), which acts as the tree's root, coordinating the distribution of data from sources to receivers.

b. **Explain the process of building type (i) and type (ii) trees.**

- **Type (i) Source-Based Tree:** The construction of a Source-Based Tree starts with the multicast source. As the source begins transmitting data, multicast routing protocols (like DVMRP or PIM-SM) help in building the tree. Each router in the network decides whether to join the tree based on whether it has members of the multicast group in its vicinity. The process involves creating a path from the source to all receivers, optimizing for the shortest or otherwise most efficient route.

- **Type (ii) Shared Tree:** The building of a Shared Tree begins with the establishment of a Rendezvous Point (RP). Sources send their data to the RP, which then forwards the data along the tree to the receivers. Both sources and receivers must register with the RP. As with the Source-Based Tree, routers use multicast routing protocols to construct the shared tree, ensuring that all group members receive the multicast data.

c. **List advantages and disadvantages of each model in terms of performance.**

- **Source-Based Tree:**
  - Advantages: Optimized routing for each source, potentially leading to lower latency and better use of bandwidth.
  - Disadvantages: Higher complexity and overhead due to the need for maintaining a separate tree for each source, leading to more intensive resource usage.
  
- **Shared Tree:**
  - Advantages: Simplicity in management and lower overhead, as only one tree per group is maintained, regardless of the number of sources.
  - Disadvantages: Potential inefficiency in data delivery paths, as the tree isn't optimized for any particular source, possibly leading to higher latency or increased bandwidth usage.

#### 2.2 The PIM (Protocol Independent Multicast) protocol allows creating support for multicast forwarding at the network level. Why does the PIM protocol contemplate (and implement) two distinct modes of operation, PIM-SM (Sparse Mode) and PIM-DM (Dense Mode)? Give practical examples where the use of one or the other protocol version is justified.

PIM-SM is designed for networks where multicast group members are sparsely distributed across a large area, which makes it inefficient to send multicast traffic everywhere. It's ideal for wide-area networks where bandwidth is precious. For instance, Internet TV broadcasting to a dispersed global audience would use PIM-SM. On the other hand, PIM-DM is suited for situations where group members are densely packed, like in a corporate LAN environment where many users might need to receive a video conference broadcast.

#### 2.3 The PIM-SM (Protocol Independent Multicast Sparse Mode) protocol generally uses a shared tree (shared tree) to create support for multicast forwarding at the network level and for this, it uses an overlay network. Is this statement true? Answer and justify your response.

Yes, the statement is true. PIM-SM generally utilizes a shared tree, or Rendezvous Point Tree (RPT), to manage multicast data distribution. This approach is particularly effective in sparse networks where members are widely distributed because it avoids flooding the network with multicast traffic. The use of an overlay network, in this case, allows PIM-SM to overlay the multicast distribution structure on top of the existing network infrastructure, enhancing efficiency and adaptability to the network's changing conditions.

## Sheet No. 3 - Multimedia Networking

### 1. Objectives

Carry out self-assessment of knowledge by solving typical questions.

### 2. Questions

#### Audio and Video

1. **Assume that the Monster is watching a video encoded at 4 Mbps and Bella is listening to an audio encoded at 200 kbps and that both sessions last one hour. Compare the sessions in terms of the volume of data transferred (in MBytes) and sensitivity to delays and losses.**

   **Data Volume:**
   - Video (Monster): At 4 Mbps for 3600 seconds, the total data is 4 Mbps * 3600 s = 14,400 Mbits, or 1,800 MBytes.
   - Audio (Bella): At 200 kbps for 3600 seconds, the total data is 200 kbps * 3600 s = 720 Mbits, or 90 MBytes.

   **Sensitivity:**
   - Video: Generally more sensitive to delays and losses due to the higher data rate and the need for continuous data flow to ensure smooth playback.
   - Audio: While also sensitive to delays and losses, audio streams typically require lower bandwidth and may employ various techniques (like buffering and error concealment) to mitigate the impacts of network variability.

2. **There are two types of redundancy in video. Describe them and discuss how they can be exploited for efficient video compression. What is the cost/benefit of the compression process?**

   - **Spatial Redundancy:** This refers to the similarity or repetition of pixel blocks within a single frame. By identifying and encoding these repeating patterns only once, significant compression can be achieved. Techniques like Discrete Cosine Transform (DCT) are often used to reduce spatial redundancy.
   - **Temporal Redundancy:** This refers to the similarity between successive frames. By only encoding the differences or changes between frames (often using motion vectors), data can be significantly compressed. 
   - **Cost/Benefit:** The main benefit of exploiting these redundancies is the reduction of required storage and bandwidth. However, the cost includes the computational complexity and time required for encoding and decoding, as well as potential quality loss due to compression.

3. **Suppose an analog audio signal is sampled 16,000 times per second and each sample is quantized into one of 1,024 levels. What would be the resulting bit rate of the digital PCM audio signal?**

   The bit rate can be calculated as follows: 
   - Sampling rate: 16,000 samples/second
   - Levels of quantization: 1,024 levels, which equals 10 bits (2^10)
   - Bit rate = 16,000 samples/second * 10 bits/sample = 160,000 bits/second or 160 kbps

4. **Multimedia applications can be classified into three main categories. Identify and describe each category. Give concrete examples of applications or services in each category.**

   - **Entertainment:** These applications provide content for enjoyment and leisure. Examples include video streaming services like Netflix and YouTube, online gaming, and virtual reality experiences.
   - **Communication:** These applications facilitate interactive communication between users. Examples include video conferencing tools like Zoom and Skype, and VoIP services.
   - **Education and Training:** These applications are used for learning and skill development. Examples include e-learning platforms like Coursera, Udemy, and various virtual training simulators.

#### Video Streaming

1. **Identify and describe two protocol solutions for supporting video streaming over HTTP. Compare these solutions in terms of performance.**

   - **HLS (HTTP Live Streaming):** A protocol developed by Apple that segments the streaming media into a sequence of small HTTP-based file downloads. Each segment contains a short interval of playback time, allowing the player to adjust quality on the fly as network conditions change.
   - **DASH (Dynamic Adaptive Streaming over HTTP):** An adaptive bitrate streaming technique that enables high quality streaming of media content over the Internet delivered from conventional HTTP web servers. Similar to HLS, it works by breaking the content into a sequence of small HTTP-based file segments.
   - **Comparison:** Both protocols are quite similar in performance, offering adaptive bitrate streaming. However, DASH is an international standard and provides more flexibility and control over the streaming experience, while HLS is widely supported, particularly in Apple environments.

2. **Identify and explain potential drawbacks that can affect a video streaming service over UDP.**

   - **Lack of reliability:** UDP doesn't guarantee packet delivery, order, or error checking, which might lead to data loss and impact the quality of the video stream.
   - **Jitter:** Variability in packet arrival times can cause uneven playback, affecting the viewing experience.
   - **No congestion control:** UDP doesn't adjust its sending rate based on network congestion, potentially leading to packet loss and further reducing video quality.

3. **Consider the non-adaptive HTTP video streaming model. Suppose the server sends at a constant rate of 2 Mbps and playback begins when 8 Mbits are received. Under these conditions, what is the expected initial delay (buffering delay) or when will playback occur?**

   - The initial buffering delay can be calculated by dividing the total initial buffer size by the constant sending rate.
   - Initial buffer: 8 Mbits
   - Sending rate: 2 Mbps
   - Buffering delay = 8 Mbits / 2 Mbps = 4 seconds
   - Playback will start after a buffering delay of 4 seconds.

#### Voice over IP Service

1. **Characterize the voice over IP service in terms of quality and service sensitivity to variations in the performance of the underlying IP network.**

   - **Quality:** VoIP quality is affected by factors like latency, jitter, and packet loss. High latency can cause noticeable delays, jitter can lead to garbled audio, and packet loss can result in missing sound fragments.
   - **Sensitivity:** VoIP is highly sensitive to network performance variations. Since it's a real-time service, even small issues can significantly affect the quality of the call. Techniques such as QoS prioritization and jitter buffers are often employed to mitigate these effects.

2. **Explain one of the studied methods that allows the receiver to recover from eventual voice packet losses.**

   - **Packet repetition or error concealment:** When packet loss is detected, the receiver can use the last successfully received packet to fill in the gap. This method doesn't truly recover the lost data but provides a way to smooth out the audio and maintain a consistent sound for the listener.

#### SIP Signaling Protocol

1. **What objectives does the SIP protocol aim to address?**

   SIP is designed to establish, maintain, and terminate multimedia sessions such as voice, video calls, and messaging over IP networks. It supports user mobility by providing a way to map permanent user identifiers to their current location and is designed to be independent of the underlying transport protocol.

2. **Identify and describe the main entities that support the operation of the SIP protocol.**

   - **User Agents:** Endpoints that initiate and terminate communication sessions, acting either as clients sending SIP requests or as servers responding to requests.
   - **Proxy Servers:** Intermediate servers that route SIP requests to the user agent server of the recipient or further proxies.
   - **Registrar Servers:** Servers that accept REGISTER requests and place the information it contains in a location service for the domain it handles.

3. **Illustrate through an example the establishment of a session between two SIP users located: (i) in the same SIP domain; and (ii) in different SIP domains.**

   - **Same Domain:** User A sends a SIP INVITE request to User B through their domain's proxy server. The proxy server forwards the INVITE to User B's user agent. Once User B accepts, the proxy facilitates the negotiation and setup of the session parameters.
   - **Different Domains:** User A sends a SIP INVITE to User B, which is routed through User A's proxy server to the appropriate proxy server in User B's domain. This server then routes the INVITE to User B. If User B accepts, the session is established, typically involving a series of response messages traversing back through the domain proxies.



## Sheet No. 4 - Multimedia Networking: Transport Protocols

### 1. Objectives

Carry out self-assessment of knowledge by solving typical questions.

### 2. Questions

#### Real-Time Support: RTP/RTCP

1. **In the design of various network services, the Real-Time Protocol (RTP) and Real-Time Control Protocol (RTCP) play an important role.**

   a. **State the purpose of these protocols and how they are articulated in the same session.**
      - **RTP (Real-Time Protocol):** Used for delivering data that has real-time requirements such as audio and video. It ensures that multimedia data packets are delivered in a sequence and timely manner, which is crucial for maintaining the quality of real-time audio and video streams. It carries the payload format, timestamping, and sequence number information necessary for proper sequence and timing reconstruction at the receiver end.
      - **RTCP (Real-Time Control Protocol):** Works alongside RTP, providing out-of-band control and monitoring of the RTP data delivery. It is used for session control and carries statistics and control information. RTCP reports are used to convey feedback on the quality of the data distribution, including packet loss, packet count, jitter, the last sequence number received, and more. This feedback can be used to adapt streaming media quality dynamically. Together, RTP and RTCP provide a framework for real-time communication over IP networks.

   b. **If RTP does not guarantee the delivery of real-time data why is it designated as “real-time”?**
      - The term "real-time" in RTP refers to its capacity to handle data that is time-sensitive and needs to be processed or experienced by the user as it is received, such as audio and video streams. It prioritizes timely delivery over reliability, which is suitable for applications like voice and video conferencing where late data is less useful than no data at all. It's designed to work with lower-level protocols that provide some level of reliability. RTP allows for the continuous transmission of data despite some packet loss, maintaining the real-time aspect of the communication.

   c. **Briefly describe the type of reports RTCP encompasses and their purpose.**
      - **RTCP Reports:** There are primarily four types of RTCP reports: Sender Report (SR), Receiver Report (RR), Source Description (SDES), and Goodbye (BYE).
        - **Sender Report (SR):** Sent by active senders in an RTP session, providing information about the total number of packets sent, total number of bytes sent, and the timestamp of the most recent RTP packet.
        - **Receiver Report (RR):** Sent by receivers if they are not sending any RTP packets. They provide feedback on the quality of the received RTP stream, including packet loss, delay, jitter, and the last sender report received.
        - **Source Description (SDES):** Carries metadata about the session participants, such as the CNAME (Canonical END-Name) which uniquely identifies a source.
        - **Goodbye (BYE):** Used to indicate the end of participation in an RTP session.
      - These reports are essential for participants to adapt to network conditions, diagnose issues, and manage session dynamics.

#### New Protocol Options: SCTP and QUIC

1. **Despite TCP being one of the most used transport protocols on the Internet, it has characteristics that can be inconvenient for certain applications.**

   a. **Explain the motivation behind the emergence of protocols like SCTP and QUIC.**
      - SCTP and QUIC emerged due to the need for more efficient, reliable, and versatile transport protocols, especially in the context of modern internet applications that demand high-speed, secure, and reliable communication. TCP, while robust and widely used, has several limitations, including its susceptibility to head-of-line blocking, lack of support for multi-homing and multi-streaming, and its relatively slow start-up time due to its handshake and congestion control mechanisms. SCTP addresses these issues by providing features like multi-homing for better network resilience and multi-streaming to reduce head-of-line blocking. QUIC further advances these improvements by reducing connection and transport latency, integrating security (TLS) by default, and improving loss recovery mechanisms.

   b. **Describe the features of the SCTP protocol emphasizing the functionalities offered at the application level. Give examples of applications or services that can benefit from its use.**
      - **SCTP Features:**
        - **Multi-streaming:** Allows multiple streams of data to be sent within the same SCTP connection, preventing a single lost or delayed packet from blocking the entire transmission (reducing head-of-line blocking).
        - **Multi-homing:** Supports multiple IP addresses in each endpoint, providing redundancy and failover capabilities in network connections.
        - **Path Selection and User Message Orientation:** Facilitates efficient network usage and supports message-based communication rather than byte stream.
      - **Benefited Applications:**
        - **Telecommunication Networks:** SCTP is used as a transport layer for signaling in IP telephony and 4G/LTE networks due to its robustness and performance characteristics.
        - **High Availability Services:** Systems that require high reliability and network failover mechanisms can benefit from SCTP's multi-homing feature.
        - **Real-time Applications:** Such as video and voice over IP that can benefit from the reduced head-of-line blocking and more efficient message handling.

2. **Provide a comparative assessment of the SCTP, TCP, and UDP protocols in relation to their services considering: “Reliable data transfer”; “Unordered data delivery” “Selective acks” “Multistreaming” and “Multihoming. Explain the function of each service and for each give examples of applications based on them.**

   - **Reliable Data Transfer:**
     - TCP and SCTP offer reliable data transfer, ensuring that all data sent is received and in the order sent. This is critical for applications like web browsing (HTTP), email (SMTP), and file transfers (FTP).
     - UDP does not guarantee delivery, but is suitable for applications where speed is more critical than reliability, such as live video streaming or online gaming.
   - **Unordered Data Delivery:**
     - UDP inherently supports unordered data delivery since it's a datagram service without built-in sequencing. This is useful for real-time applications like VoIP or live broadcasts where late data is less useful.
     - SCTP allows selective reception of unordered data, benefiting applications that can process parts of the message independently.
   - **Selective Acks:**
     - SCTP and TCP (with extensions like SACK) support selective acknowledgments, allowing the receiver to inform the sender of all segments that have arrived successfully, leading to more efficient retransmission strategies. This is useful in any application over a lossy network where efficiency and speed are critical.
   - **Multistreaming:**
     - SCTP uniquely offers multistreaming within a single connection, allowing multiple streams of data to be interleaved. This is particularly useful for complex applications like web browsers that handle different types of data simultaneously (e.g., text, images, video).
   - **Multihoming:**
     - SCTP's multihoming allows a connection to span multiple IP addresses for each endpoint, providing redundancy and reliability for critical applications such as data center operations, distributed databases, or any service requiring high availability and resilience.

3. **Make a comparative analysis between the connection establishment times among TCP, TCP+TLS, and QUIC protocols. In each situation describe how the connection establishment process takes place considering the scenario of a new connection.**

   - **TCP:** Requires a three-way handshake for connection establishment, consisting of SYN, SYN-ACK, and ACK messages. This can introduce a significant delay, especially over long distances.
   - **TCP+TLS:** After completing the TCP handshake, an additional handshake is required for TLS to negotiate encryption parameters. This adds another round of delay, making it even slower than plain TCP.
   - **QUIC:** Combines the transport layer and cryptographic handshake into a single process, allowing for immediate data transmission after the initial handshake. This significantly reduces the connection establishment time, particularly for new connections or when resuming connections with known servers.
   - In a new connection scenario, QUIC is notably faster due to its efficient handshake mechanism and built-in encryption, which eliminates the need for multiple sequential negotiations found in TCP and TCP+TLS.

4. **In HTTP/3, TCP is not used at the transport layer. Provide a comparative assessment between HTTP/1.1, HTTP/2, and HTTP/3 considering the differences related to the transport layer and security aspects. Comment on the advantages and disadvantages associated.**

   - **HTTP/1.1 (over TCP):** Each TCP connection allows for one request/response at a time, leading to inefficient use of network resources and latency issues due to the need for multiple connections. It is simple and widely supported but lacks the efficiency needed for modern web applications.
   - **HTTP/2 (over TCP):** Introduces multiplexing, allowing multiple requests and responses to be sent over a single TCP connection, significantly improving performance and reducing latency. It also introduces header compression and prioritization. However, it still suffers from TCP-related issues like head-of-line blocking at the TCP layer.
   - **HTTP/3 (over QUIC):** Leverages the benefits of QUIC, including reduced connection establishment time, improved security with TLS 1.3 integration, and resistance to head-of-line blocking due to packet-level multiplexing. It is designed for the modern internet, offering better performance and reliability, particularly on unstable networks. However, its deployment complexity and the need for widespread support are challenges.
   - **Advantages of HTTP/3:**
     - Reduced latency due to faster connection establishment and multiplexing.
     - Improved performance on lossy or unstable networks.
     - Integrated and improved security model with TLS 1.3.
   - **Disadvantages of HTTP/3:**
     - Increased complexity in implementation and deployment.
     - Requires support from both client and server sides, which is still in the process of being widely adopted.
