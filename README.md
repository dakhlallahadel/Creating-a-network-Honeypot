How to Build a Network Honeypot
By Adel Dakhlallah


Goal: Create a basic honeypot that mimics a vulnerable service to log and analyze attack behavior. Showcase your skills in cybersecurity, logging, networking, and scripting.
________________________________________
Step 1: Choose Your Honeypot Type
Decide what kind of honeypot you want to build:
•	Low-interaction honeypots (safer, easier):
o	Tools: Cowrie (SSH/Telnet), Honeyd, Dionaea, Glastopf (HTTP)
•	High-interaction honeypots (real services, more risk):
o	Tools: Build a vulnerable VM (e.g., Metasploitable or custom setup)
________________________________________
Step 2: Set Up Your Environment
Use a safe, isolated system or cloud VM (e.g., AWS, DigitalOcean, VirtualBox):
•	Install Ubuntu/Debian
•	Update system with following command:
o	sudo apt update && sudo apt upgrade
•	Install Git, Python, and dependencies
________________________________________
Step 3: Install the Honeypot
Example: Install Cowrie
•	Install dependencies:
o	sudo apt install git python3-venv python3-pip libssl-dev libffi-dev build-essential
•	Clone Cowrie repo
o	git clone https://github.com/cowrie/cowrie.git cd cowrie

•	Setup virtual environment
o	python3 -m venv cowrie-env
source cowrie-env/bin/activate

•	Install Python dependencies
o	pip install --upgrade pip
o	pip install -r requirements.txt

•	Copy config template
o	cp etc/cowrie.cfg.dist etc/cowrie.cfg
•	Configure as needed in etc/cowrie.cfg.
________________________________________
 Step 4: Run the Honeypot
•	Command:
o	bin/cowrie start
•	Cowrie simulates an SSH/Telnet service
•	It logs credentials, commands, and sessions attackers try
•	Logs are stored in var/log/cowrie
________________________________________
Step 5: Monitor and Analyze
•	Use Kibana/Elasticsearch or custom scripts to analyze logs
•	Look for:
o	Brute force attempts
o	Common malware payloads
o	Attacker IPs and behaviors
