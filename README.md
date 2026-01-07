🚨 DDoS Attack Detection in SDN using Entropy</br>
📌 Overview

This project implements an entropy-based DDoS attack detection mechanism in a Software-Defined Networking (SDN) environment. The system leverages traffic randomness analysis to distinguish between normal network behavior and coordinated attack traffic, enabling early and accurate detection of Distributed Denial of Service (DDoS) attacks.

The solution is developed and evaluated using Mininet, POX Controller, Open vSwitch (OVS), and Python (Scapy), demonstrating effective detection of multiple DDoS attack types with low false positives.

🎯 Objectives

Understand the fundamentals of SDN, entropy, and DDoS attacks

Detect network host attacks using entropy-based anomaly detection

Implement real-time mitigation using OpenFlow rules via SDN controller

Evaluate detection accuracy and response time under attack scenarios

🧠 Key Concept: Entropy-Based Detection

Entropy, derived from information theory, measures the randomness or unpredictability of network traffic.

High entropy → Normal, legitimate traffic (diverse & unpredictable)

Low entropy → DDoS traffic (repetitive & coordinated)

By continuously monitoring entropy values of traffic features (e.g., source IPs, packet distribution), the system flags anomalies when entropy drops below a dynamic threshold.

🏗️ System Architecture

SDN Controller: POX (Python-based)

Network Emulator: Mininet

Switches: Open Virtual Switch (OVS)

Traffic Generator: Python Scapy

Operating System: Ubuntu 24.04 (VM-based)

Topology:

Tree topology

4 switches

9 hosts

1 remote controller

⚙️ Project Modules
🔹 Module I: Model Creation

SDN setup using Mininet

Tree topology configuration

Traffic generation scripts

🔹 Module II: Simulation

Normal traffic simulation

DDoS attack traffic simulation

Traffic data analysis

🔹 Module III: Observation & Results

Entropy computation

Threshold-based attack detection

Mitigation via OpenFlow rules

🧪 Attack Types Detected

SYN Flood Attacks

UDP Flood Attacks

HTTP-based Flood Attacks

🛠️ Installation & Setup
1️⃣ Install Python
sudo apt-get install python

2️⃣ Install Scapy
sudo apt-get install python-scapy

3️⃣ Install Mininet & POX Controller

Mininet: http://mininet.org/download/

POX:

git clone https://github.com/noxrepo/pox

📂 Project Structure
DDoS-Entropy-SDN/
├── mininet/
│   └── custom/
│       ├── traffic.py
│       └── attack.py
├── pox/
│   └── pox/
│       └── forwarding/
│           ├── detectionUsingEntropy.py
│           └── l3_detectionEntropy.py
├── README.md

▶️ Running the Project
1️⃣ Start POX Controller
cd pox
python ./pox.py forwarding.l3_detectionEntropy.py

2️⃣ Launch Mininet Topology
sudo mn --switch ovsk --topo tree,depth=2,fanout=3 \
--controller=remote,ip=127.0.0.1,port=6633

3️⃣ Open Host Terminals
mininet>xterm h1 h2 h3 h9

4️⃣ Generate Normal Traffic (h1)
cd ../mininet/custom
python traffic.py -s 2 -e 65

5️⃣ Launch DDoS Attack (h2 & h3)
cd ../mininet/custom
python attack.py 10.0.0.64

📊 Results & Analysis

Entropy values are continuously monitored at the controller

Threshold entropy is derived from minimum normal traffic entropy

DDoS attack detected when entropy drops below threshold (≈ 0.5)

Attacks detected within first 250 malicious packets

Switches are dynamically shut down and restored post-attack

✔ High detection accuracy
✔ Low false positives
✔ Fast response time

🚀 Future Improvements

Adaptive ML-based threshold learning

Detection of low-rate and stealth DDoS attacks

Integration with real-time alerting systems

Scalability testing with larger topologies

🙏 Acknowledgment

I sincerely thank Exposys Data Labs for providing the opportunity to work on this project during my internship. Their guidance, support, and collaborative environment played a crucial role in enhancing my technical and professional skills.

👤 Author

Ayush Kumar Yadav
B.Tech Student | Networking & Security Enthusiast
Project: DDoS Attack Detection in SDN using Entropy
