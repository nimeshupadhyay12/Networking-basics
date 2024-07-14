**THE OSI REFERENCE MODEL**

### 1. Physical Layer (Layer 1)

**Function:**

- The Physical Layer is responsible for the transmission and reception of raw data bits over a physical medium. This includes the hardware aspects such as cables, switches, and network interface cards.
- The physical layer is right down to the hardware of the computer. This is where the electrical pulses that make up data transfer over a network are sent and received. It's the job of the physical layer to convert the binary data of the transmission into signals and transmit them across the network, as well as receiving incoming signals and converting them back into binary data.

**Details:**

- **Transmission Medium:** Specifies the medium through which data is transmitted (copper wire, fiber optics, wireless).
- **Bit Transmission:** Deals with the conversion of data into electrical, optical, or radio signals.
- **Standards and Interfaces:** Defines the physical and electrical characteristics of the hardware (e.g., voltages, timing, data rates).

**Devices:**

- Hubs, Repeaters, Network Interface Cards (NICs), Cables (Ethernet, Fiber Optic).

**Examples:**

- Ethernet (IEEE 802.3), USB.

### 2. Data Link Layer (Layer 2)

**Function:**

- Ensures reliable transmission of data across a physical network link by handling error detection and correction, as well as flow control.
- The data link layer focuses on the _physical_ addressing of the transmission. It receives a packet from the network layer (that includes the IP address for the remote computer) and adds in the physical (MAC) address of the receiving endpoint. Inside every network enabled computer is a Network Interface Card (NIC) which comes with a unique MAC (Media Access Control) address to identify it.

  MAC addresses are set by the manufacturer and literally burnt into the card; they can't be changed -- although they _can_ be spoofed. When information is sent across a network, it's actually the physical address that is used to identify where exactly to send the information.

  Additionally, it's also the job of the data link layer to present the data in a format suitable for transmission.

  The data link layer also serves an important function when it receives data, as it checks the received information to make sure that it hasn't been corrupted during transmission, which could well happen when the data is transmitted by layer 1: the physical layer.

**Details:**

- **MAC (Media Access Control) Sub-layer:** Manages protocol access to the physical network medium.
- **LLC (Logical Link Control) Sub-layer:** Manages frame synchronization, error checking, and flow control.

**Devices:**

- Switches, Bridges.

**Examples:**

- Ethernet, PPP (Point-to-Point Protocol), MAC addresses, VLANs.

### 3. Network Layer (Layer 3)

**Function:**

- Responsible for data routing, packet forwarding, and logical addressing to determine the best path for data to travel across networks.
- The network layer is responsible for locating the destination of your request. For example, the Internet is a huge network; when you want to request information from a webpage, it's the network layer that takes the IP address for the page and figures out the best route to take. At this stage we're working with what is referred to as _Logical_ addressing (i.e. IP addresses) which are still software controlled. Logical addresses are used to provide order to networks, categorising them and allowing us to properly sort them. Currently the most common form of logical addressing is the IPV4 format, which you'll likely already be familiar with (i.e 192.168.1.1 is a common address for a home router).

**Details:**

- **Routing:** Determines the best route for data from source to destination.
- **Logical Addressing:** Uses IP addresses to identify devices on the network.
- **Fragmentation and Reassembly:** Breaks down large packets into smaller ones and reassembles them at the destination.

**Devices:**

- Routers, Layer 3 Switches.

**Examples:**

- IP (Internet Protocol), ICMP (Internet Control Message Protocol), ARP (Address Resolution Protocol).

### 4. Transport Layer (Layer 4)

**Function:**

- Ensures complete data transfer and manages end-to-end communication. It provides error recovery, data flow control, and data segmentation.
- The transport layer is a very interesting layer that serves numerous important functions. Its first purpose is to choose the protocol over which the data is to be transmitted. The two most common protocols in the transport layer are TCP (**T**ransmission **C**ontrol **P**rotocol) and UDP (**U**ser **D**atagram **P**rotocol); with TCP the transmission is _connection-based_ which means that a connection between the computers is established and maintained for the duration of the request. This allows for a reliable transmission, as the connection can be used to ensure that the packets _all_ get to the right place. A TCP connection allows the two computers to remain in constant communication to ensure that the data is sent at an acceptable speed, and that any lost data is re-sent. With UDP, the opposite is true; packets of data are essentially thrown at the receiving computer -- if it can't keep up then that's _its_ problem (this is why a video transmission over something like Skype can be pixelated if the connection is bad). What this means is that TCP would usually be chosen for situations where accuracy is favoured over speed (e.g. file transfer, or loading a webpage), and UDP would be used in situations where speed is more important (e.g. video streaming).

With a protocol selected, the transport layer then divides the transmission up into bite-sized pieces (over TCP these are called _segments_, over UDP they're called _datagrams_), which makes it easier to transmit the message successfully.

**Details:**

- **Segmentation and Reassembly:** Divides large messages into segments and reassembles them.
- **Connection Management:** Establishes, maintains, and terminates connections (TCP).
- **Flow Control and Error Control:** Manages data flow and corrects errors in data transmission.

**Devices:**

- Gateways, Firewalls (operating at Layer 4).

**Examples:**

- TCP (Transmission Control Protocol), UDP (User Datagram Protocol), port numbers.

### 5. Session Layer (Layer 5)

**Function:**

- Manages sessions between applications, including the setup, maintenance, and teardown of communication sessions.
- When the session layer receives the correctly formatted data from the presentation layer, it looks to see if it can set up a connection with the other computer across the network. If it can't then it sends back an error and the process goes no further. If a session _can_ be established then it's the job of the session layer to maintain it, as well as co-operate with the session layer of the remote computer in order to synchronise communications. The session layer is particularly important as the session that it creates is unique to the communication in question. This is what allows you to make multiple requests to different endpoints simultaneously without all the data getting mixed up (think about opening two tabs in a web browser at the same time)! When the session layer has successfully logged a connection between the host and remote computer the data is passed down to Layer 4: the transport Layer.

**Details:**

- **Session Establishment:** Initiates and manages the dialog between two communicating devices.
- **Session Maintenance:** Keeps the session alive and manages data exchange.
- **Session Termination:** Properly closes the session to end communication.

**Devices:**

- Session Layer does not involve specific hardware devices but rather protocols and software.

**Examples:**

- NetBIOS, PPTP (Point-to-Point Tunneling Protocol), RPC (Remote Procedure Call).

### 6. Presentation Layer (Layer 6)

**Function:**

- Translates data between the application layer and the network format, ensuring data is in a readable format. It also handles data encryption, compression, and translation.
- The presentation layer receives data from the application layer. This data tends to be in a format that the application understands, but it's not necessarily in a standardised format that could be understood by the application layer in the _receiving_ computer. The presentation layer translates the data into a standardised format, as well as handling any encryption, compression or other transformations to the data. With this complete, the data is passed down to the session layer.

**Details:**

- **Data Translation:** Converts data formats (e.g., character encoding, encryption, and decryption).
- **Data Compression:** Reduces the size of data to be transmitted.
- **Data Encryption:** Secures data by transforming it into an unreadable format for unauthorized users.

**Devices:**

- Encryption devices and software tools.

**Examples:**

- SSL/TLS (Secure Sockets Layer/Transport Layer Security), JPEG, ASCII, EBCDIC.

### 7. Application Layer (Layer 7)

**Function:**

- Provides network services directly to end-users and applications. It serves as the interface between the user and the network.
- The application layer of the OSI model essentially provides networking options to programs running on a computer. It works almost exclusively with applications, providing an interface for them to use in order to transmit data. When data is given to the application layer, it is passed down into the presentation layer.

**Details:**

- **Network Services:** Provides services such as file transfer, email, remote login, and network management.
- **High-Level APIs:** Interfaces and protocols that applications use to communicate over the network.

**Devices:**

- End-user devices, application servers.

**Examples:**

- HTTP (Hypertext Transfer Protocol), FTP (File Transfer Protocol), SMTP (Simple Mail Transfer Protocol), DNS (Domain Name System), Telnet.

### Mnemonic for Remembering OSI Layers:

- **All People Seem To Need Data Processing:** (Application, Presentation, Session, Transport, Network, Data Link, Physical)

Understanding the OSI model helps in diagnosing network issues, designing network solutions, and understanding how different networking protocols interact with each other. This layered approach allows network administrators and cybersecurity professionals to isolate problems and work on specific network components effectively.
