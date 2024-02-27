# Networking Protocols

## 1. Packets with Headers

- **Paper Communication**:
  - Envelope contains routing information.
  - Letter contains the contents.
  - Pages of a book can be sent in envelopes, facilitating reassembly if numbered.

- **Digital Communication**:
  - **Data**: Message or data to be sent.
  - **Packet / Segment / Frame**: Data divided into packets for transmission.
  - **Header / Footer**: Contains routing information and marks the start/end of the packet.

- **Layers**:
  - Digital communication uses layered containers, like OSI model or Internet Protocol Suite.
  - Each layer adds routing information.
  - Data can be sliced into smaller pieces at each layer.

## 2. TCP/IP and Friends

- **TCP/IP**:
  - **TCP, IP, and UDP** are pervasive protocols.
  - Sit in the middle of the network layer stack.
  - Transmit higher-level protocols (HTTP, SMTP, SSH) and are transmitted by lower-level protocols (Wi-Fi, Ethernet).

- **TCP (Transmission Control Protocol)**:
  - Reliable, ordered, connection-oriented transport protocol.
  - Uses acknowledgments and retransmissions for reliability.
  - Slower but provides reliable delivery over IP.

- **UDP (User Datagram Protocol)**:
  - Lightweight transport protocol.
  - Adds source/destination port numbers and checksum for error detection.
  - No guaranteed delivery or order.

- **IP (Internet Protocol)**:
  - Two versions: IPv4 and IPv6.
  - Every computer has a unique IP address.
  - Best-effort delivery with no guarantee of arrival.

## 3. URLs

- **Components**:
  - Scheme (e.g., HTTP, HTTPS).
  - Hostname (identifies a computer).
  - Path (identifies a specific resource).

- **Mapping URL Hostname to IP Address**:
  - Browsers convert hostname to IP address using DNS.
  - DNS allows convenient mapping between user-readable hostnames and IP addresses.

## 4. DHCP

- **Dynamic Host Control Protocol (DHCP)**:
  - Assigns IP addresses dynamically.
  - Involves a negotiation process between the client and server.
  - Uses UDP packets for communication.
  - Offers flexibility and efficiency in IP address allocation.
