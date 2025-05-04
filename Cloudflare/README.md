# Cloudflare Cheat Sheet

## 📋 Table of Contents
- [Basic Configuration](#-basic-configuration)
- [Creating Subdomains](#-creating-subdomains)
- [Using Workers](#-using-workers)
- [Security Settings](#-security-settings)
- [Performance Optimization](#-performance-optimization)
- [Analytics & Monitoring](#-analytics--monitoring)
- [Cloudflare Tunnel](#-cloudflare-tunnel)

## 🔧 Basic Configuration

**Domain Settings:**
- Registered Domain: `pika-tech.com`
- Domain hosted on Cloudflare
- DNS managed by Cloudflare

## 🌐 Creating Subdomains

### Using Cloudflare Pages

**Steps to create `blog.pika-tech.com`:**

1. Navigate to **Cloudflare Dashboard → Pages → Create Project**
2. Connect your Git repository and deploy your site
3. After deployment, go to **Settings → Custom Domains**
4. Add custom domain: `blog.pika-tech.com`
5. DNS record (CNAME) will be automatically created

## 🚀 Using Workers

### Simple Redirect Example

**Create a redirect to Notion:**

1. Go to **Workers & Pages → Create Worker**
2. Name your worker (e.g., `notion-redirect`)
3. Add this code:

```js
export default {
  async fetch(request) {
    return Response.redirect(
      "https://www.notion.so/c7467a14a5334c81845ab252ea8ad694",
      301
    );
  },
};
```

4. Deploy and bind to custom domain: `notion.pika-tech.com`

### API Proxy Example

```js
addEventListener('fetch', event => {
  event.respondWith(handleRequest(event.request))
})

async function handleRequest(request) {
  const apiUrl = "https://api.example.com"
  const modifiedRequest = new Request(apiUrl, request)
  return fetch(modifiedRequest)
}
```

### Geolocation-based Redirect

```js
addEventListener('fetch', event => {
  event.respondWith(handleRequest(event.request))
})

async function handleRequest(request) {
  const country = request.headers.get('CF-IPCountry')
  
  if (country === 'TW') {
    return Response.redirect('https://tw.pika-tech.com', 302)
  }
  
  return fetch(request)
}
```

## 🔒 Security Settings

### SSL/TLS Configuration

1. Go to **SSL/TLS → Overview**
2. Choose encryption mode:
   - **Full**: Encrypts end-to-end (requires valid SSL on origin)
   - **Full (strict)**: Validates certificate authenticity (recommended)
3. Enable **"Always Use HTTPS"** in **SSL/TLS → Edge Certificates**

### Web Application Firewall (WAF)

1. Navigate to **Security → WAF**
2. Enable recommended ruleset for basic protection
3. Configure custom rules for specific threats

## ⚡ Performance Optimization

### Caching Settings

1. Go to **Caching → Configuration**
2. Configure Browser Cache TTL:
   - Recommended: 4 hours (14400 seconds)
3. Enable **Always Online** to serve cached content when origin is down

### Page Speed Improvements

1. Navigate to **Speed → Optimization**
2. Enable:
   - **Auto Minify** (HTML, CSS, and JavaScript)
   - **Brotli compression**
   - **Early Hints**
   - **HTTP/3 (QUIC)**

## 🔍 Analytics & Monitoring

### Traffic Analysis

1. Go to **Analytics → Web Analytics**
2. Add domains you want to track
3. Monitor:
   - Visitor statistics
   - Page performance
   - Bot traffic

### Alert Configuration

1. Navigate to **Notifications**
2. Set up alerts for:
   - Security incidents
   - Origin server errors
   - Traffic spikes

## 🔗 Cloudflare Tunnel

Securely connect your local services to Cloudflare without opening inbound ports.

### Installation

**For Linux:**
```bash
wget https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb
sudo dpkg -i cloudflared-linux-amd64.deb
```

### Setup Process

1. **Authenticate with Cloudflare:**
   ```bash
   cloudflared tunnel login
   ```

2. **Create a Tunnel:**
   ```bash
   cloudflared tunnel create <TUNNEL_NAME>
   ```

3. **Configure the Tunnel:**
   
   Create or edit the config file at `~/.cloudflared/config.yml`:
   ```yaml
   tunnel: <TUNNEL_ID>
   credentials-file: /path/to/.cloudflared/<TUNNEL_ID>.json
   
   ingress:
     - hostname: example.com
       service: http://localhost:8080
     - service: http_status:404
   ```

4. **Run the Tunnel:**
   ```bash
   cloudflared tunnel run <TUNNEL_NAME>
   ```

5. **Route Traffic:**
   ```bash
   cloudflared tunnel route dns <TUNNEL_NAME> subdomain.yourdomain.com
   ```

### Running as a Service

**For Linux systems:**
```bash
sudo cloudflared service install
sudo systemctl start cloudflared
```

