# 🛣️ Koocheh

**Koocheh** (کوچه) is a lightweight, rule-based proxy router written in Go, designed to serve multiple users in restricted network environments. It acts as a controlled gateway, deciding whether to forward traffic directly or route it through a secure tunnel like TUIC or V2Ray — per domain, user, or policy.

Built for high censorship contexts like Iran, Koocheh offers stealth, simplicity, and smart routing.

---

## ✨ Features

- 🔐 Multi-user SOCKS5 proxy with basic auth
- 🧠 Smart routing by domain, IP, or rule
- 🌍 Split traffic: Direct for `.ir`, proxy for `.com`
- 🔄 Supports tunnel backends like TUIC or V2Ray
- 🧩 Pluggable outbound handling (rotate, fallback, random)
- 🪶 Lightweight & fast – written in Go
- 📄 Simple config file (YAML or JSON)
- 📊 Optional access logging per user

---

## 🚀 Quick Start

### 1. Install

```bash
git clone https://github.com/yourname/koocheh.git
cd koocheh
go build -o koocheh
````

Or use prebuilt binary (coming soon).

---

### 2. Example Config (`config.yaml`)

```yaml
listen: 0.0.0.0:1080
users:
  - username: ali
    password: ali123
  - username: sara
    password: pass456

routes:
  - domain_suffix: ".ir"
    action: direct
  - domain_suffix: "telegram.org"
    action: proxy
  - ip_cidr: "10.0.0.0/8"
    action: direct
  - default: proxy

proxy:
  type: socks5
  address: 127.0.0.1:1081  # TUIC/V2Ray client
```

---

### 3. Run the server

```bash
./koocheh -config config.yaml
```

Users can now connect via SOCKS5 at `yourserver:1080` using their username/password.

---

## 🔧 Tunnel Setup (TUIC/V2Ray)

Use TUIC or V2Ray client on the same server, listening on `127.0.0.1:1081`, and pointing to your foreign VPS.

---

## 📦 Binary Options

Coming soon for:

* Linux (amd64, arm64)
* Windows
* macOS

---

## 🧠 Philosophy

> A **koocheh** is a side street — quiet, hidden, unnoticed.
> Koocheh routes only what needs to be hidden, and lets the rest flow freely.
> This means less overhead, faster browsing, and less risk.

---

## ✅ Roadmap

* [ ] SOCKS5 proxy with auth
* [ ] Domain/IP-based routing
* [ ] Stats per user
* [ ] Live config reload
* [ ] Web dashboard
* [ ] Multi-hop tunneling

---

## 💬 Credits

Created by users of the free web, for users behind firewalls.
Koocheh is open-source. Use it, fork it, build on it.

---

## 📄 License

MIT License

