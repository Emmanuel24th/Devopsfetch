# devopsfetch

`devopsfetch` is a DevOps tool designed to collect and display system 
information. It provides insights into active ports, Docker containers, 
Nginx configurations, and user activities.

## Features

- **Ports:**
  - List all active ports and services.
  - Display detailed information for a specific port.
  
- **Docker:**
  - List all Docker images and containers.
  - Display detailed information for a specific Docker container.

- **Nginx:**
  - List all Nginx domains and their ports.
  - Display detailed configuration for a specific Nginx domain.

- **Users:**
  - List all users and their last login times.
  - Display detailed information about a specific user.

## Installation

### 1. Clone the Repository

Clone the repository

```bash

cd devopsfetch

2. Create and Activate a Python Virtual Environment (Optional)
Create a virtual environment and activate it:

bash
Copy code
python3 -m venv venv
source venv/bin/activate
3. Install Dependencies
Create a requirements.txt file and add the following (if you have 
additional dependencies later, add them here):

plaintext
Copy code
# requirements.txt
# Add your dependencies here
Install the dependencies:

bash
Copy code
pip install -r requirements.txt
4. Make Scripts Executable
Ensure all scripts are executable:

bash
Copy code
chmod +x src/devopsfetch.py
chmod +x install.sh
chmod +x logrotate.sh
5. Run the Installation Script
Run the installation script to set up the tool:

bash
Copy code
./install.sh
Usage

Basic Commands
Run devopsfetch with the following options:

List Ports:

bash
Copy code
devopsfetch -p
Port Details:

bash
Copy code
devopsfetch -p [port_number]
List Docker Images and Containers:

bash
Copy code
devopsfetch -d
Docker Container Details:

bash
Copy code
devopsfetch -d [container_name]
List Nginx Domains:

bash
Copy code
devopsfetch -n
Nginx Domain Details:

bash
Copy code
devopsfetch -n [domain]
List Users:

bash
Copy code
devopsfetch -u
User Details:

bash
Copy code
devopsfetch -u [username]
Example
To list all active ports and display details for port 80:

bash
Copy code
devopsfetch -p
devopsfetch -p 80
Logging and Log Rotation

Logs are stored in /var/log/devopsfetch.log.

Log Rotation Script
The logrotate.sh script rotates logs daily. You can manually run it or set 
it up in a cron job:

bash
Copy code
./logrotate.sh
To schedule log rotation (e.g., daily):

bash
Copy code
echo "0 0 * * * /path/to/logrotate.sh" | sudo tee -a /etc/crontab
Launch Daemon for Continuous Monitoring (macOS)

On macOS, launchd is used for continuous monitoring.

1. Create a Launch Daemon Configuration File
Create the configuration file:

bash
Copy code
sudo touch /Library/LaunchDaemons/com.example.devopsfetch.plist
2. Edit the Configuration File
Edit /Library/LaunchDaemons/com.example.devopsfetch.plist to include:

xml
Copy code
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" 
"http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>Label</key>
    <string>com.example.devopsfetch</string>
    <key>ProgramArguments</key>
    <array>
        <string>/usr/local/bin/devopsfetch</string>
    </array>
    <key>RunAtLoad</key>
    <true/>
    <key>KeepAlive</key>
    <true/>
    <key>StandardOutPath</key>
    <string>/var/log/devopsfetch.log</string>
    <key>StandardErrorPath</key>
    <string>/var/log/devopsfetch.err</string>
</dict>
</plist>

3. Load the Launch Daemon
Load the daemon:

bash
Copy code
sudo launchctl load /Library/LaunchDaemons/com.example.devopsfetch.plist
4. Verify Daemon Status
Check if the daemon is running:

bash
Copy code
sudo launchctl list | grep com.example.devopsfetch
Troubleshooting

If you encounter issues, check the logs:

Standard output: /var/log/devopsfetch.log
Standard error: /var/log/devopsfetch.err

# Devopsfetch
