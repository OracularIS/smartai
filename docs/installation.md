# AI Apps - Installation & Running the Platform

This guide explains how to install prerequisites and run the **AI Apps** platform using the provided startup scripts.

---

## Prerequisites

Before starting the platform, ensure the following are available:

- **Operating System Requirements**
  - Windows: Win10 or Win11
  - Linux: Ubuntu, Redhat, MacOS

- **Resources**:
  - vCPU    4 Core
  - RAM   8 GB
  - Storage   50 GB SSD
  - OS    Ubuntu 22.04 LTS or Above
  - Docker    Docker CE + Compose
  - Network   Public IP + DNS

These are the minimum requirements. The optimal number would depend on number of concurrent users. The API traffic based on AI usage, and the number of requests sent through the system

- **Docker Desktop installed (recommended)**
  - Windows: https://docs.docker.com/desktop/setup/install/windows-install/
  - macOS: https://docs.docker.com/desktop/setup/install/mac-install/
  - Linux: https://docs.docker.com/desktop/setup/install/linux/
- **Docker Compose** (included with Docker Desktop)
- **Domain name / ServerName** configured and resolvable (e.g., `ai-apps.yourcompanyname.com`)
- **AI Apps package** (Installation script provided on request) containing `downloadscript.sh` and `downloadscript.ps1`
- **SSL certificate files present**
  - `nginx/certs/server.crt`
  - `nginx/certs/server.key`
- **Environment config updated**: project root `.env`

> Required container images are pulled automatically when you start the platform for the first time.

Images typically included:

- `oogy-api`
- `chat-api`
- `enterprise-mesh-api`
- `smart-functions-ui`

---

## 1) Configure environment

Edit the `.env` file in the project root.

Example:

```env
SERVER_NAME=ai-apps.domain-name.com
SSL_CERT=./nginx/certs/server.crt
SSL_KEY=./nginx/certs/server.key
```

### Environment variables

| Variable    | Description                         |
| ----------- | ----------------------------------- |
| SERVER_NAME | Domain name used by the application |
| SSL_CERT    | Path to SSL certificate             |
| SSL_KEY     | Path to SSL private key             |

---

## 2) DNS / hosts setup

Choose one approach based on how you will access the platform.

### Option A) Local testing (hosts file)

If you are running the stack locally and want your browser to reach the containers, map the same hostname as `SERVER_NAME` (and `NEXTAUTH_URL`, if used) to `127.0.0.1`.

**Windows**

- Hosts file: `C:\Windows\System32\drivers\etc\hosts`
- Add:

```text
127.0.0.1 ai-apps.domain-name.com
```

**macOS / Linux**

- Hosts file: `/etc/hosts`
- Add:

```text
127.0.0.1 ai-apps.domain-name.com
```

> You typically need Administrator (Windows) / sudo (macOS/Linux) to edit the hosts file.

### Option B) Public IP + public DNS

If you are using a public IP and public DNS, add the public IP of your device/VM in your DNS provider.

Example:

- IP of VM or device: `192.168.1.2`
- DNS provider record:
  - Record Type: `A`
  - Host: `ai-apps`
  - Value: `192.168.1.2`

---

## 3) Start the AI Apps

Run the startup script from the project root.

### macOS / Linux

```bash
./ai-apps.sh start
```

### Windows (PowerShell)

```powershell
.\ai-apps.ps1 start
```

The script will:

- Load environment variables
- Validate SSL configuration
- Pull latest images (first time)
- Start all containers

---

## 4) Access the application

Open:

```text
https://<SERVER_NAME>
```

Example:

```text
https://ai-apps.domain-name.com
```

---

## 5) Stop the application

### macOS / Linux

```bash
./ai-apps.sh stop
```

### Windows (PowerShell)

```powershell
.\ai-apps.ps1 stop
```

---

## 6) Update the platform

Use this when you want to pull newer images.

### Update images

**Windows (PowerShell)**

```powershell
.\ai-apps.ps1 update
```

**macOS / Linux**

```bash
./ai-apps.sh update
```

Restart after an update:

```text
stop -> start
```

---

## Commands (cheatsheet)

### Windows (PowerShell)

```powershell
.\ai-apps.ps1 --help
.\ai-apps.ps1 start
.\ai-apps.ps1 stop
.\ai-apps.ps1 status
.\ai-apps.ps1 logs
.\ai-apps.ps1 update
```

### macOS / Linux

```bash
./ai-apps.sh --help
./ai-apps.sh start
./ai-apps.sh stop
./ai-apps.sh status
./ai-apps.sh logs
./ai-apps.sh update
```

---

## How to generate SSL certificates

To enable HTTPS without browser security warnings, a valid SSL certificate is required.

### Option 1) Use an existing SSL certificate

If you already have an SSL certificate for your domain, provide:

- Certificate file (`.crt` or full chain certificate)
- Private key file (`.key`)

Place them at:

- `nginx/certs/server.crt`
- `nginx/certs/server.key`

Or update `.env` to point `SSL_CERT`/`SSL_KEY` to the correct paths.

### Option 2) Generate a free Let's Encrypt certificate

#### Prerequisites

- You own the domain name.
- The domain's DNS records point to your server.
- Ports **80** and **443** are accessible from the internet.

#### Linux: Certbot

Walkthrough: https://certbot.eff.org/

Ubuntu/Debian:

```bash
sudo apt update
sudo apt install certbot
```

Generate the certificate:

```bash
sudo certbot certonly --standalone -d yourdomain.com -d www.yourdomain.com
```

Certificate location:

```text
/etc/letsencrypt/live/yourdomain.com/fullchain.pem
/etc/letsencrypt/live/yourdomain.com/privkey.pem
```

Renewal:

```bash
sudo certbot renew
```

#### Windows: win-acme

Walkthrough: https://www.win-acme.com/

1. Download and extract win-acme.
2. Run `wacs.exe` as Administrator.
3. Create a new certificate and enter your domain name(s) (for example `example.com`, `www.example.com`).
4. Export or copy the resulting certificate/key to the locations used by your `.env`.

---

## Notes

- Ensure SSL certificate files exist at the paths configured in `.env`.
- Changes to `.env` require restarting the containers.
