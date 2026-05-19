Network traffic can provide valuable insights into potential breaches. Network traffic is typically analyzed in detail at the level of individual frames or using summary statistics of traffic flows and protocol usage.

A SIEM will store selected information from sensors installed to different points on the network. Information captured from network packets can be aggregated and summarized to show overall protocol usage and endpoint activity. On a typical network, sensors are not configured to record all network traffic, as this would generate a very considerable amount of data. More typically, only packets that triggered a given firewall or IDS rule are recorded. SIEM software will usually provide the ability to pivot from an event or alert summary to opening the underlying packets in an analyzer.

On the other hand, given sufficient resources, a retrospective network analysis (RNA) solution provides the means to record the totality of network events at either a packet header or payload level.

Packet analysis refers to deep-down, frame-by-frame scrutiny of captured traffic using a tool such as Wireshark. The analyzer decodes the packet to show the header fields at data link/MAC, network/IP, and transport (TCP/UDP) layers. At the application layer, it shows both header data and payload contents.

Packet analysis can identify whether packets passing over a standard port have been manipulated in some nonstandard way, to work as a mechanism for a botnet server, for instance. It allows inspection of protocol payloads to try to identify data exfiltration attempts or attempts to contact suspicious domains and URLs. Detailed analysis of the packet contents can help to reveal the tools used in an attack. It is also possible to extract binary files such as potential malware for analysis.

![A Screengrab shows the results of the Wireshark packet analyzer.](https://s3.amazonaws.com/wmx-api-production/courses/54332/images/2193-1692974873699.png) Description

The table on the top lists the number, time, source, destination, protocol, length, and info. The S M B protocol is highlighted. The table is followed by the information along with few lines of code. The tab reassembled TCP (4160 bytes) is selected at the bottom.

Using the Wireshark packet analyzer to identify malicious executables being transferred over the Windows file-sharing protocol. (Screenshot Wireshark [wireshark.org](https://www.wireshark.org/).)