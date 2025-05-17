<div align="center">
  <img src="https://imgs.search.brave.com/ny5ikV8C3-hXyJACBXB2lcfOw2sIRJjQRrUv-G9ijBw/rs:fit:860:0:0:0/g:ce/aHR0cHM6Ly9pbWFn/ZXMtcGxhdGZvcm0u/OTlzdGF0aWMuY29t/Ly9DU3NyR3J6ME00/YWZCR1lrMWUzVzFp/TUVhNmM9LzE3NTl4/MTEzMjoyODAweDIx/NzMvZml0LWluLzUw/MHg1MDAvcHJvamVj/dHMtZmlsZXMvMTYw/LzE2MDc1LzE2MDc1/MTEvMzdjZmJkYWUt/MTY0Yy00ZDcwLTg4/NGYtYzNkNjI5ZGI3/MmMwLnBuZw" width="150" alt="UpTimeWeb Logo" />
  
  <h1>UpTimeWeb</h1>
  <p align="center">
    <b>Enterprise-grade monitoring solution with unparalleled reliability</b>
  </p>
  
  <p align="center">
    <img src="https://img.shields.io/github/license/TojanHorse/UpTimeWeb?style=flat-square" alt="License" />
    <img src="https://img.shields.io/github/v/release/TojanHorse/UpTimeWeb?style=flat-square" alt="Latest Release" />
    <img src="https://img.shields.io/docker/pulls/tojanforce/uptimeweb?style=flat-square" alt="Docker Pulls" />
  </p>
  
  <br />
  
  <div>
    <img src="https://placeholder.com/30x30" width="30" height="30" alt="Team Bytes Logo" />
    <h3>Team Bytes</h3>
  </div>
</div>

---

## 📖 Overview

**UpTimeWeb** is a robust, self-hosted monitoring solution designed for modern infrastructure. Built from the ground up by TojanHorse, it offers comprehensive uptime monitoring with an intuitive interface and powerful notification system.

## ✨ Key Features

- **Versatile Monitoring**: Track HTTP(s), TCP, HTTP(s) Keyword, JSON queries, Ping, DNS records, and Docker containers
- **Real-time Alerts**: Receive instant notifications through 90+ services including Telegram, Discord, Slack, and Email
- **Responsive Dashboard**: Clean, modern UI that works flawlessly on all devices
- **Comprehensive Reporting**: Detailed analytics and historical data visualization
- **High Performance**: 20-second monitoring intervals with minimal resource usage
- **Enterprise Security**: Full 2FA support and secure credential management
- **Status Pages**: Create public or private status pages with custom domains

## 🚀 Quick Start

### Docker Installation (Recommended)

Deploy in seconds with our official Docker image:

```bash
docker run -d --restart=always \
  -p 3001:3001 \
  -v uptime-web:/app/data \
  --name uptime-web \
  tojanforce/uptimeweb:latest
```

Access the dashboard at: `http://localhost:3001`

### Manual Installation

#### Prerequisites

- Node.js 18+ and npm 9+
- Git (for cloning the repository)

#### Development Setup

```bash
# Clone the repository
git clone https://github.com/TojanHorse/UpTimeWeb.git
cd UpTimeWeb

# Install dependencies
npm install

# Start development server
npm run dev
```

#### Production Deployment

```bash
# Install dependencies
npm install

# Build the frontend
npm run build

# Start the production server
node server/server.js
```

## 🛡️ System Requirements

| Component | Requirement |
|-----------|-------------|
| CPU       | 1+ cores    |
| Memory    | 512MB+ RAM  |
| Disk      | 1GB+ space  |
| OS        | ✅ Linux (Debian, Ubuntu, CentOS, etc.)<br>✅ Windows 10/Server 2012 R2 (x64) or higher<br>❌ FreeBSD/OpenBSD/NetBSD<br>❌ Replit/Heroku |
| Software  | Node.js 18+ / npm 9+ |

## 🔒 Secure Deployment

For enhanced security, restrict access to localhost only:

```bash
docker run -d --restart=always \
  -p 127.0.0.1:3001:3001 \
  -v uptime-web:/app/data \
  --name uptime-web \
  tojanforce/uptimeweb:latest
```

## 🔄 Update Procedures

### Docker Update

```bash
# Pull the latest image
docker pull tojanforce/uptimeweb:latest

# Stop and remove the existing container
docker stop uptime-web
docker rm uptime-web

# Create a new container with the latest image
docker run -d --restart=always \
  -p 3001:3001 \
  -v uptime-web:/app/data \
  --name uptime-web \
  tojanforce/uptimeweb:latest
```

### Manual Update

```bash
cd UpTimeWeb
git pull
npm install
npm run build

# If using PM2
pm2 restart uptime-web

# OR if running directly
node server/server.js
```

## 💼 Production Deployment with PM2

```bash
# Install PM2
npm install pm2 -g && pm2 install pm2-logrotate

# Start server with PM2
pm2 start server/server.js --name uptime-web

# Configure startup persistence
pm2 save && pm2 startup
```

**PM2 Management Commands:**

```bash
pm2 monit                # Live monitoring dashboard
pm2 logs uptime-web      # View application logs
pm2 restart uptime-web   # Restart application
```

## 🛠️ Administration

### Account Management

```bash
# Reset password (Docker)
docker exec -it uptime-web node extra/reset-password.js

# Reset password (Non-Docker)
node extra/reset-password.js
```

### Backup & Recovery

```bash
# Create backup (Docker)
docker exec -it uptime-web node extra/backup-db.js

# Create backup (Non-Docker)
node extra/backup-db.js

# Backup Docker volume
docker run --rm \
  -v uptime-web:/source \
  -v $(pwd):/backup \
  alpine tar -czf /backup/uptime-web-backup.tar.gz -C /source .
```

### Database Maintenance

```bash
# Verify database integrity
node extra/check-db-integrity.js

# Remove old notifications
node extra/cleanup-old-notification.js

# Purge historical data
node extra/purge-stale-data.js --days=30
```

### Advanced Configuration

```bash
# View current settings
node extra/get-config.js

# Import data
node extra/import-data.js --file=/path/to/data.json

# Export data
node extra/export-data.js --output=/path/to/output.json

# Maintenance mode
node server/server.js --maintenance
```

### Docker Management

```bash
docker logs uptime-web           # View logs
docker exec -it uptime-web sh    # Access shell
docker restart uptime-web        # Restart service
```

## 🖼️ Screenshots

<div align="center">
  <img src="https://uptime.kuma.pet/img/light.jpg" width="80%" alt="Dashboard" />
  <p><i>Main dashboard interface</i></p>
  
  <br />
  
  <img src="https://user-images.githubusercontent.com/1336778/134628766-a3fe0981-0926-4285-ab46-891a21c3e4cb.png" width="80%" alt="Status Page" />
  <p><i>Public status page</i></p>
</div>

## 🌐 Advanced Configuration

For enterprise deployments, reverse proxy configuration, and advanced deployment options, please refer to our comprehensive documentation or contact the development team.

## 🤝 About Team Bytes

Team Bytes, led by TojanHorse, is dedicated to developing enterprise-grade monitoring solutions with a focus on reliability, security, and user experience. UpTimeWeb represents our commitment to providing robust infrastructure monitoring tools for businesses of all sizes.

## 📄 License & Legal

UpTimeWeb is developed and maintained by Team Bytes under TojanHorse leadership. All rights to the codebase belong to TojanHorse and Team Bytes.

## 📞 Support

For technical support, feature requests, or to report bugs, please open an issue on our GitHub repository:

[https://github.com/TojanHorse/UpTimeWeb](https://github.com/TojanHorse/UpTimeWeb.git)
