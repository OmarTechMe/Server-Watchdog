⚡ SERVER WATCHDOG ⚡
SERVER WATCHDOG is a lightweight, cross-platform telemetry and network monitoring tool. It continuously monitors your local servers, specific service ports, and public network health, sending instant real-time alerts directly to your Discord server if anything goes offline.

It features a beautiful "Matrix-style" visual dashboard, hardware polling, and the ability to trigger automated recovery scripts when a server crashes.

🌟 Key Features
Dual Monitoring: Tracks Local IPs (every 60 seconds) and Public Domains (every 15 minutes).

Port-Specific Tracking: Check specific services (like 192.168.1.10:8006 for Proxmox or port 80 for web servers) instead of just checking if the machine is powered on.

Instant Discord Alerts: Get notified the second a connection drops, and again when it is restored.

Smart Cooldowns: Never spams your Discord. It alerts you once when a server drops, backs off for 15 minutes, and waits for it to come back online.

Auto-Recovery: Automatically runs local .bat or .sh scripts to attempt to fix crashed servers.

Portable: Runs entirely from a single .exe file. No installation required.

🚀 Step 1: Download the Software
Go to the Releases Page.

Look for the latest version (e.g., v20) and click on ServerWatchdog.exe to download it.

Place the .exe file in a dedicated folder on your computer (it will create a small config file and a log file in the same folder when you run it).

💬 Step 2: How to Get Your Discord Webhook URLs
To get alerts on your phone or computer, you need to connect the software to a Discord server.

1. Create a Discord Server (If you don't have one):

Open Discord, scroll to the bottom of your server list on the left, and click the "+" button to "Add a Server".

Choose "Create My Own" and give it a name.

2. Create a Text Channel:

It is recommended to make two specific channels for your alerts: one named #local-alerts and one named #domain-alerts.

3. Generate the Webhook URL:

Hover your mouse over your #local-alerts channel and click the Gear Icon (Edit Channel).

On the left menu, click Integrations.

Click on Webhooks and then click New Webhook.

Give the webhook a cool name (like "Local Watchdog").

Click the Copy Webhook URL button.

Save this URL somewhere safe!

Repeat step 3 for your #domain-alerts channel to get your second URL.

⚙️ Step 3: How to Use the Software
Open the Software: Double-click the ServerWatchdog.exe file.

Paste Your Webhooks: Paste the URLs you got from Discord into the two text boxes at the top of the app.

Add Your Local IPs: * In the bottom left box, type the IP addresses of the servers you want to monitor.

Put one IP per line.

Advanced: If you want to monitor a specific port, add it to the end with a colon (example: 192.168.1.10:80).

Add Public Domains: * In the bottom right box, keep the default health domains (like google.com or 1.1.1.1), or add your own public websites to monitor your internet connection health.

Start Scanning: Click the big green ▶ INITIATE UPLINK button.

The software will now display its boot sequence and begin monitoring your network! It will automatically save your IP lists and Webhooks so you never have to type them again.

🔧 Advanced: Auto-Recovery Scripts
If you check the Enable Auto-Recovery Scripts box, the Watchdog can try to fix your servers for you.

If the IP 192.168.1.13 goes offline, the software will look in its folder for a script named:

recover_192_168_1_13.bat (if running on Windows)

recover_192_168_1_13.sh (if running on Linux)

If you are tracking a specific port, like 192.168.1.10:8006, it will look for:

recover_192_168_1_10_8006.bat

You can put whatever commands you want inside these scripts, such as sending a Wake-On-LAN magic packet to turn a computer on, or using SSH to restart a crashed web service. If the script exists, the Watchdog will run it the moment the server drops.

👨‍💻 Developer & Support
Architect: Omar BOUZID

Contact: omarbouzid1337@proton.me

Built for stability, precision, and cybernetic network oversight.
