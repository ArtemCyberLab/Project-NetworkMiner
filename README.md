 Project Goal

The goal of this project was to gain practical skills in network forensics using NetworkMiner — an open-source tool for passive network traffic analysis.
I analyzed pre-captured network traffic (PCAP files), extracted digital artefacts such as files, credentials, images, and server banners, investigated host activities and protocols, and compared the results between different NetworkMiner versions.

Tools and Environment

Tool: NetworkMiner by Netresec

Version 2.7.2 — used for main analysis, metadata, and artefact extraction.

Version 1.6.1 — used for frame-level inspection (sequence numbers, packet details).

Operating System: Windows (though NetworkMiner also supports Linux and macOS).

Data Samples:
mx-3.pcap, mx-4.pcap, mx-7.pcap, mx-9.pcap, case1.pcap, case2.pcap

Skills required: Networking fundamentals (ports, protocols, sessions) and basic Linux familiarity.

 Methodology

Loaded PCAP files into NetworkMiner through Case Panel → Load PCAP.
When multiple captures were open, I removed unrelated ones using
“Remove selected files and Reload Case Files.”

Examined different views and tabs for analysis:

Hosts — viewed IPs, MACs, OS fingerprints, open ports, and banners.

Files / Images — extracted transmitted files and images.

Credentials — analyzed captured usernames and passwords.

Parameters — filtered HTTP headers such as content-type.

DNS — reviewed DNS queries and responses.

Anomalies — checked for TLS or protocol anomalies.

Frames (v1.6.1) — viewed low-level frame fields such as sequence numbers.

Filtered results using keywords (frame numbers, filenames, etc.) for each task.

Recorded all findings and compared how results differed between NetworkMiner versions.

 Results and Findings
 Task 4 — mx-3.pcap / mx-4.pcap

Total frames: 460

IPs sharing the same MAC as 145.253.2.203: 2

Packets sent from 65.208.228.223: 72

Web server banner: Apache

Extracted username: #B\Administrator

Extracted password: NTLMv2 hash (long blob)

Only NetworkMiner v2.7.2 extracted credentials; v1.6.1 did not.

 Task 5 — mx-7.pcap / mx-9.pcap

Linux distribution in frame 63075: CentOS

Page header in frame 75942: Password-Ned AB

Source IP of image ads.bmp.2E5F0FD9.bmp: 80.239.178.187

Possible TLS anomaly frame: 36255

Platform sending password reset email: Facebook

Email of Branson Matheson: branson@sandsite.org

Task 6 — Version Differences

Detect duplicate MAC addresses: 2.7

Handle frame details: 1.6

More detailed packet info: 1.6

 Task 7 — case1.pcap / case2.pcap

OS of host 131.151.37.122: Windows NT 4

Bytes received 131.151.32.91 → 131.151.37.122 (port 1065): 192 bytes

Bytes received 131.151.37.122 → 131.151.32.21 (port 143): 20769 bytes

Sequence number of frame 9: 2AD77400

Detected content-type parameters: 2

USB product brand: asix

Phone model: Lumia 535

Source IP of “fish” image: 50.22.95.9

Password for homer.pwned.se@gmx.com
: spring2015

DNS query for frame 62001: pop.gmx.com

Conclusions

Throughout this project, I:

Learned to use NetworkMiner for passive traffic analysis and artefact reconstruction.

Successfully extracted credentials, images, files, web server banners, and DNS queries.

Compared how older and newer versions of NetworkMiner handle data — version 1.6.1 is better for frame-level analysis, while version 2.7.2 excels in artefact extraction and UI usability.

Practiced core digital forensics and incident response skills by investigating real PCAP samples.

 Future Improvements

Automate analysis with tshark/Wireshark integration for deeper inspection.

Develop scripts for batch PCAP metadata extraction and indexing before loading into NetworkMiner.

Create additional custom PCAPs for practice (SMTP attachments, NTLM handshakes, FTP sessions, etc.).

In summary:
This project allowed me to strengthen my understanding of network protocols and digital forensics workflow. I gained hands-on experience investigating real network captures, interpreting artefacts, and correlating network events — essential skills for cybersecurity and incident response roles.
