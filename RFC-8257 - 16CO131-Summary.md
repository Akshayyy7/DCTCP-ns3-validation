# RFC 8257 Data Center TCP (DCTCP) Summary:

* RFC 8257 DCTCP achieves high-burst tolerance, low latency, and high throughput with shallow-buffered switches. 
* DCTCP is a modification to the processing
   of ECN by a conventional TCP and requires that standard TCP
   congestion control be used for handling packet loss.

### DCTCP Algorithm

   There are three components involved in the DCTCP algorithm:

   *  The switches detect
      congestion and set the Congestion Encountered (CE) codepoint in
      the IP header and also mark the packets as ECN enabled.

   *  The receiver sends the congestion information back to the sender,
      using the ECN-Echo (ECE) flag in the TCP header.

   * The sender computes a congestion estimate and reacts by reducing
      the TCP congestion window (cwnd) accordingly.

### Important Points

* During such periods of
   congestion, conventional TCP will suffer packet loss and quickly and
   drastically reduce cwnd.  DCTCP, on the other hand, will use the
   fraction of marked packets to reduce cwnd more gradually.


* DCTCP's
   potential can only be realized in data centers where the entire
   network infrastructure supports ECN.
