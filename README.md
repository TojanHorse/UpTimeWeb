<div align="center" width="100%"> <img src="https://imgs.search.brave.com/ny5ikV8C3-hXyJACBXB2lcfOw2sIRJjQRrUv-G9ijBw/rs:fit:860:0:0:0/g:ce/aHR0cHM6Ly9pbWFn/ZXMtcGxhdGZvcm0u/OTlzdGF0aWMuY29t/Ly9DU3NyR3J6ME00/YWZCR1lrMWUzVzFp/TUVhNmM9LzE3NTl4/MTEzMjoyODAweDIx/NzMvZml0LWluLzUw/MHg1MDAvcHJvamVj/dHMtZmlsZXMvMTYw/LzE2MDc1LzE2MDc1/MTEvMzdjZmJkYWUt/MTY0Yy00ZDcwLTg4/NGYtYzNkNjI5ZGI3/MmMwLnBuZw" width="128" alt="UpTimeWeb Logo" /> </div> <div align="center"> <img src="https://placeholder.com/30x30" width="30" height="30" alt="Team Bytes Logo" /> <h3>Team Bytes</h3> </div>
UpTimeWeb
A powerful self-hosted monitoring tool developed by TojanHorse.

🚀 How to Run This Project
Development Mode
Install Node.js (version 18 or higher recommended) and npm if you haven't already.
Clone the repository:
sh
git clone https://github.com/TojanHorse/UpTimeWeb.git
cd UpTimeWeb
Install dependencies:
sh
npm install
Start the development server:
sh
npm run dev
Open your browser and go to:
http://localhost:3001
Production Mode
Install dependencies:
sh
npm install
Build the frontend:
sh
npm run build
Start the server:
sh
node server/server.js
Open your browser and go to:
http://localhost:3001
You should now see the UpTimeWeb interface running locally!

🐳 Docker Installation
Use the official TojanHorse UpTimeWeb Docker image:

bash
docker run -d --restart=always -p 3001:3001 -v uptime-web:/app/data --name uptime-web tojanforce/uptimeweb:latest
UpTimeWeb is now running on http://0.0.0.0:3001.

[!NOTE] To limit exposure to localhost only, use:

bash
docker run -d --restart=always -p 127.0.0.1:3001:3001 -v uptime-web:/app/data --name uptime-web tojanforce/uptimeweb:latest
🆙 How to Update
Docker Update
Simply pull the latest image and restart your container:

bash
docker pull tojanforce/uptimeweb:latest
docker stop uptime-web
docker rm uptime-web
docker run -d --restart=always -p 3001:3001 -v uptime-web:/app/data --name uptime-web tojanforce/uptimeweb:latest
Manual Update
bash
cd UpTimeWeb
git pull
npm install
npm run build
pm2 restart uptime-web # If using PM2
# OR
node server/server.js # If running directly
💪🏻 Production Deployment with PM2
For running UpTimeWeb in the background:

bash
# Install PM2 if you don't have it:
npm install pm2 -g && pm2 install pm2-logrotate

# Start Server
pm2 start server/server.js --name uptime-web

# Add to startup
pm2 save && pm2 startup
Useful PM2 Commands:

bash
# Monitor the application
pm2 monit

# View logs
pm2 logs uptime-web

# Restart the application
pm2 restart uptime-web
🛠️ Useful Commands
Here are some handy commands for managing your UpTimeWeb installation:

Reset Password
If you forgot your password, you can reset it using the command line:

bash
# For Docker installation
docker exec -it uptime-web node extra/reset-password.js

# For non-Docker installation
node extra/reset-password.js
Backup and Restore
bash
# Backup (Docker)
docker exec -it uptime-web node extra/backup-db.js

# Backup (Non-Docker)
node extra/backup-db.js

# The backup file will be saved in the data directory
Database Maintenance
bash
# Check DB integrity
node extra/check-db-integrity.js

# Cleanup old notification data
node extra/cleanup-old-notification.js

# Purge stale data (entries older than X days)
node extra/purge-stale-data.js --days=30
Advanced Commands
bash
# View current settings
node extra/get-config.js

# Import data from JSON
node extra/import-data.js --file=/path/to/data.json

# Export data to JSON
node extra/export-data.js --output=/path/to/output.json

# Run in maintenance mode
node server/server.js --maintenance
Docker Commands
bash
# View logs
docker logs uptime-web

# Run a shell in the container
docker exec -it uptime-web sh

# Restart service
docker restart uptime-web

# Backup volume data
docker run --rm -v uptime-web:/source -v $(pwd):/backup alpine tar -czf /backup/uptime-web-backup.tar.gz -C /source .
⭐ Features
Monitoring uptime for HTTP(s) / TCP / HTTP(s) Keyword / HTTP(s) Json Query / Ping / DNS Record / Push / Steam Game Server / Docker Containers
Fancy, Reactive, Fast UI/UX
Notifications via Telegram, Discord, Gotify, Slack, Pushover, Email (SMTP), and 90+ notification services
20-second intervals
Multiple languages
Multiple status pages
Map status pages to specific domains
Ping chart
Certificate info
Proxy support
2FA support
<<<<<<< HEAD
=======
🖼 Screenshots
Light Mode:

<img src="https://uptime.kuma.pet/img/light.jpg" width="512" alt="" />
Status Page:

<img src="https://user-images.githubusercontent.com/1336778/134628766-a3fe0981-0926-4285-ab46-891a21c3e4cb.png" width="512" alt="" />
Settings Page:

<img src="https://louislam.net/uptimekuma/2.jpg" width="400" alt="" />
Telegram Notification Sample:

<img src="https://louislam.net/uptimekuma/3.jpg" width="400" alt="" />
>>>>>>> 9e66d0d7619536537969ff48feea0c6ec1ba14d9
System Requirements
Platform
✅ Major Linux distros such as Debian, Ubuntu, CentOS, Fedora and ArchLinux etc.
✅ Windows 10 (x64), Windows Server 2012 R2 (x64) or higher
❌ FreeBSD / OpenBSD / NetBSD
❌ Replit / Heroku
Node.js 18 / 20.4
npm 9
Advanced Configuration
For reverse proxy configuration and advanced deployment options, check the GitHub repository wiki or reach out to the maintainer.

ℹ️ About
UpTimeWeb is a powerful monitoring tool developed and maintained by Team Bytes under TojanHorse leadership. All rights to the codebase belong to TojanHorse and Team Bytes.

This project aims to provide an easy-to-use self-hosted monitoring tool with advanced features and regular improvements.

If you encounter any issues or have questions, please open an issue on the GitHub repository at https://github.com/TojanHorse/UpTimeWeb.git.

