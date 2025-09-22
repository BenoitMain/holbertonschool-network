# Diagram: What happens when you type https://www.google.com and press Enter

```mermaid
flowchart LR
  Browser["Browser\nhttps://www.google.com"]
  DNS["DNS resolver\n(UDP 53)"]
  Router["Internet / Routing"]
  FW["Firewall / Proxy"]
  LB["Load Balancer\n(L4/L7)"]
  Web["Web Server\n(nginx / reverse proxy)"]
  App["Application Server\n(business logic)"]
  DB["Database / Cache\n(SQL/NoSQL, Redis)"]

  Browser -->|DNS lookup (UDP 53)| DNS
  DNS -->|return IP (A/AAAA)| Browser

  Browser -->|TCP 443 (SYN) — TLS encrypted| Router
  Router --> FW
  FW -->|allow TCP 443| LB

  LB -->|forward (TLS passthrough or terminate)| Web
  Web -->|proxy request| App
  App -->|query| DB

  DB -->|result| App
  App -->|generate response (HTML/JSON)| Web
  Web -->|response (HTTP over TLS)| LB
  LB -->|TLS encrypted response| Browser
```

Short description / alt text: Diagram flow — Browser → DNS resolution → TCP/TLS to server IP (port 443) → Firewall → Load Balancer → Web Server → Application Server → Database.  
Render note: GitHub peut afficher mermaid nativement selon le repo/paramètres ; sinon ouvrez le fichier en preview VS Code ou exportez en PNG.