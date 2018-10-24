
# RFC 8257 Data Center TCP (DCTCP) Summary:

### Keywords:
* ECN   : Explicit Congestion Notification
* DCTCP :  Data Center TCP  

## Notes:

*  [RFC3168] describes a mechanism of using ECN from the switches for detection of congestion. However, this method only detects the presence of congestion, not its
   extent.
*  DCTCP estimates the fraction of bytes that encounter congestion rather than simply detecting that some congestion has occurred.
*  achieves high-burst tolerance, low latency, and high throughput with shallow-buffered switches. 
*  DCTCP is a modification to the processing of ECN by a conventional TCP. Standard TCP congestion control be used for handling packet loss.
*  ### DCTCP Algorithm

   There are three components involved in the DCTCP algorithm:

   o  The switches (or other intermediate devices in the network) detect
      congestion and set the Congestion Encountered (CE) codepoint in
      the IP header.

   o  The receiver echoes the congestion information back to the sender,
      using the ECN-Echo (ECE) flag in the TCP header.

   o  The sender computes a congestion estimate and reacts by reducing
      the TCP congestion window (cwnd) accordingly.

* The Layer 3 (L3) switches and routers in a data-center fabric
  indicate congestion to the end nodes by setting the CE codepoint in
  the IP header   
  
* DCTCP introduces a new Boolean TCP state variable, DCTCP
  Congestion Encountered (DCTCP.CE), which is initialized to false and
  stored in the Transmission Control Block (TCB).  When sending an ACK,
  the ECE flag MUST be set if and only if DCTCP.CE is true.  When
  receiving packets, the CE codepoint MUST be processed as follows:

  1.If the CE codepoint is set and DCTCP.CE is false, set DCTCP.CE to
     true and send an immediate ACK.
     
  2.If the CE codepoint is not set and DCTCP.CE is true, set DCTCP.CE
     to false and send an immediate ACK.
     
  3.Otherwise, ignore the CE codepoint.
