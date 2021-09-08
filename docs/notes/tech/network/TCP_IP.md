# [TCP/IP](https://intronetworks.cs.luc.edu/current/html/tcpA.html)

- **Sliding windows algorithm** 

!!! Abstract
    
    === "TCP Header"
        - ![TCP Header](https://intronetworks.cs.luc.edu/current/html/_images/tcp_header.svg)
        - SYN: for SYNchronize; marks packets that are part of the new-connection handshake
        - ACK: indicates that the header Acknowledgment field is valid; that is, all but the first packet
        - FIN: for FINish; marks packets involved in the connection closing
        - PSH: for PuSH; marks “non-full” packets that should be delivered promptly at the far end
        - RST: for ReSeT; indicates various error conditions
        - URG: for URGent; part of a now-seldom-used mechanism for high-priority data
        - CWR and ECE: part of the Explicit Congestion Notification mechanism,

    === "TCP Connection Establishment"
        - If A is the client and B is the listening server, then the handshake proceeds as follows:
        - A sends B a packet with the SYN bit set (a SYN packet)
        - B responds with a SYN packet of its own; the ACK bit is now also set
        - A responds to B’s SYN with its own ACK
        - ![three way handshake](https://intronetworks.cs.luc.edu/current/html/_images/tcp_3wh.svg)
        - The three-way handshake is vulnerable to an attack known as SYN flooding

    === "Closing a connection"
        - To close the connection, a superficially similar exchange involving FIN packets may occur:
        - A sends B a packet with the FIN bit set (a FIN packet), announcing that it has finished sending data
        - B sends A an ACK of the FIN
        - B may continue to send additional data to A When B is also ready to cease sending, it sends its own FIN to A
        - A sends B an ACK of the FIN; this is the final packet in the exchange
        ![close connection](https://intronetworks.cs.luc.edu/current/html/_images/tcp_close2.svg)
      