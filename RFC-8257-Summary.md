# RFC 8257: Data Center TCP (DCTCP): TCP Congestion Control for Data Centers [Plain Summary]

## What does RFC 8257 discuss/entail/convey?
* Documentation of DCTCP as currently implemented by major OS (Microsoft Windows, Linux, FreeBSD)
* Deployment issues related to coexistence of DCTCP and conventional TCP
* Lack of negotiating mechanism between sender and receiver and possible mitigations

## What does DCTCP do?
* Extends ECN (Explicit Congestion Notification) processing to estimate fraction of bytes that encounter congestion rather than simply detecting that congestion occurred.
* It then scales the TCP congestion window on the basis of this estimate.
    ### What is ECN?
    Conventionally, TCP/IP networks signal congestion by dropping packets. ECN is an extension to TCP and IP which allows end-to-end notification of network congestion withoout dropping packets.


## What does DCTCP achieve?
* High-burst tolerance
* Low latency
* High throughput with shallow-buffered switches

> Note: DCTCP must not be deployed over public Internet without additional measures.






