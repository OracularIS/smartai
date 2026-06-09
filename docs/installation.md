# Installation (AI Apps Platform)

This page covers:

- First-time install (prereqs + `.env`)
- Running on `localhost` or a server IP (no domain required)
- SSL certificate setup (local dev or real domain)
- Updating the platform (new images)

---

## Prerequisites

- **Docker Desktop installed (recommended)**  
  Install guides:
  - Windows: https://docs.docker.com/desktop/setup/install/windows-install/
  - macOS: https://docs.docker.com/desktop/setup/install/mac-install/
  - Linux: https://docs.docker.com/desktop/setup/install/linux/
- **Docker Compose** (included with Docker Desktop)
- **Optional alternative**: Podman + Podman Compose
- **Registry access** to pull container images
- **SSL certificate files present** (required):
  - `nginx/certs/server.crt`
  - `nginx/certs/server.key`
- **Environment config updated**: project root `.env` (everything is configured in `.env`)

> Required container images are pulled automatically the first time you start the platform.

---

## 1) Configure `.env`

Edit `.env` in the project root.

Example (no domain, local machine):

```env
SERVER_NAME=localhost
SSL_CERT=./nginx/certs/server.crt
SSL_KEY=./nginx/certs/server.key
```

| Variable    | Description                         |
| ----------- | ----------------------------------- |
| SERVER_NAME | Hostname or IP used by the platform |
| SSL_CERT    | Path to SSL certificate             |
| SSL_KEY     | Path to SSL private key             |

---

## 2) Run on localhost (no domain)

### Same machine

Set `SERVER_NAME=localhost`, start the platform, then open:

```text
https://localhost
```

### Other machines on your network (server IP)

1) Find your work machine IP address:

- **Windows (domain-joined work machine)**: `ipconfig` (use the `IPv4 Address`)
- **macOS**: `ipconfig getifaddr en0`
- **Linux**: `hostname -I`

2) Set:

```env
SERVER_NAME=<YOUR_SERVER_IP>
```

3) Start the platform and open:

```text
https://<YOUR_SERVER_IP>
```

> Ensure port `443` is reachable (firewall/VPN/network rules may apply).

---

## 3) SSL certificates (required)

You have two common options. Pick one:

### Option A: Local development (no domain) - mkcert (recommended)

Walkthrough: https://github.com/FiloSottile/mkcert

Generate certs into the expected paths:

```bash
mkcert -install
mkcert -key-file nginx/certs/server.key -cert-file nginx/certs/server.crt localhost 127.0.0.1
```

If you use `SERVER_NAME=<YOUR_SERVER_IP>`, include the IP too:

```bash
mkcert -key-file nginx/certs/server.key -cert-file nginx/certs/server.crt localhost 127.0.0.1 <YOUR_SERVER_IP>
```

### Option B: You own a real domain - Let's Encrypt

This requires a public domain pointing to your server and inbound access to ports **80** and **443**.

- Linux (Certbot): https://certbot.eff.org/
- Windows (win-acme): https://www.win-acme.com/

After generating the certificate, configure `SSL_CERT`/`SSL_KEY` to point to it (or copy the files into `nginx/certs/` as `server.crt` and `server.key`).

---

## 4) Start / stop / update

### First-time start (pulls images)

**macOS / Linux**

```bash
./ai-apps.sh start
```

**Windows (PowerShell)**

```powershell
.\ai-apps.ps1 start
```

Typically starts:

- `oogy-api`
- `chat-api`
- `enterprise-mesh-api`
- `smart-functions-ui`

### Stop

**macOS / Linux**

```bash
./ai-apps.sh stop
```

**Windows (PowerShell)**

```powershell
.\ai-apps.ps1 stop
```

### Update the platform (pull newer images)

If you also track this repo with Git:

```bash
git pull
```

Then:

**macOS / Linux**

```bash
./ai-apps.sh update
```

**Windows (PowerShell)**

```powershell
.\ai-apps.ps1 update
```

Restart after an update:

```text
stop -> start
```

---

## Commands (cheatsheet)

**Windows (PowerShell)**

```powershell
.\ai-apps.ps1 start
.\ai-apps.ps1 stop
.\ai-apps.ps1 status
.\ai-apps.ps1 logs
.\ai-apps.ps1 update
```

**macOS / Linux**

```bash
./ai-apps.sh start
./ai-apps.sh stop
./ai-apps.sh status
./ai-apps.sh logs
./ai-apps.sh update
```

---

## Notes

- If you change `.env`, restart the containers.
- Certificates must match `SERVER_NAME` (localhost vs IP vs domain).
