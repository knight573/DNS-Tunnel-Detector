# DNS Tunneling & Heuristic-Based Exfiltration Detector



## 🛡️ About the Project

This project was devaeloped to explore the mechanics of DNS tunneling—a sophisticated method used to bypass firewalls by "hiding" data inside standard DNS queries. My goal was to move beyond simple packet capture and build a system capable of identifying these hidden channels using statistical analysis.



## 🚀 Technical Implementation & Detection Logic

To differentiate between legitimate web traffic and malicious data exfiltration, I focused on three specific detection heuristics:



1. **Statistical Entropy Analysis**: 

   - I used **Shannon Entropy** to measure the randomness of incoming DNS subdomains. 

   - Standard domain names (like `google.com`) have low entropy, whereas encoded data (like Base64 or Hexadecimal strings used in tunneling) shows significantly higher randomness.



2. **Structural Heuristics**: 

   - The system flags queries that exceed standard length thresholds (e.g., 50-60 characters), which is a common characteristic of data-heavy DNS packets.

   - I also implemented monitoring for high-frequency **TXT** and **CNAME** records, which are frequently exploited for their ability to carry larger payloads.



3. **Protocol Analysis**: 

   - Using the **Scapy** library, I performed real-time inspection of DNS Resource Records (RR) to identify anomalies at the Application Layer (Layer 7).
