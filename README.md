<div align="center">

```
██████╗  ██████╗ ██████╗ ██╗  ██╗███████╗██████╗
██╔══██╗██╔═══██╗██╔══██╗██║ ██╔╝██╔════╝██╔══██╗
██║  ██║██║   ██║██████╔╝█████╔╝ █████╗  ██████╔╝
██║  ██║██║   ██║██╔══██╗██╔═██╗ ██╔══╝  ██╔══██╗
██████╔╝╚██████╔╝██║  ██║██║  ██╗███████╗██║  ██║
╚═════╝  ╚═════╝ ╚═╝  ╚═╝╚═╝  ╚═╝╚══════╝╚═╝  ╚═╝
```

**A clean, offline-first Google Dorking tool for security researchers and bug bounty hunters.**

![HTML](https://img.shields.io/badge/HTML-single%20file-orange?style=flat-square&logo=html5)
![Zero Dependencies](https://img.shields.io/badge/dependencies-zero-brightgreen?style=flat-square)
![Offline](https://img.shields.io/badge/works-offline-blue?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-purple?style=flat-square)

</div>

---

## What is this?

**Dorker** is a single HTML file that turns raw Google Dork patterns into one-click search links — no backend, no API keys, no install. Just open it in your browser and start recon.

Designed for **bug bounty hunters**, **pentesters**, and **security researchers** who want a fast, organized interface for passive reconnaissance without juggling bookmarks or remembering dork syntax by heart.

---

## Features

| Feature | Description |
|---|---|
| 🔍 **Multi-Engine** | Google · Bing · DuckDuckGo · Brave Search · Yandex |
| 🗂️ **Categories** | Dorks organized by type — Recon, Files, Redirect, Secrets, Vulns |
| ✏️ **Custom Dorks** | Add your own dork patterns to any category |
| 📁 **Custom Categories** | Create new categories to match your workflow |
| ⎘ **Quick Copy** | Copy any dork to clipboard in one click |
| 💾 **Persistent Storage** | Everything saved in localStorage — survives browser restarts |
| 🎨 **Theme per Engine** | Each search engine has its own color theme |
| 📦 **Zero Dependencies** | Pure HTML + CSS + JS, no frameworks, no npm, no build step |
| ✈️ **Offline Ready** | Works completely offline after the first open |

---

## Preview

```
┌─────────────────────────────────────────────────────────┐
│  ● Google                              🟠 Google ▼      │
│                                                          │
│           D O R K E R                                    │
│                                                          │
│         [ example.com                 ]                  │
│                                                          │
│  All  Reconnaissance  Sensitive Files  +New Category     │
│  ┌──────────────────────────────────────────────────┐   │
│  │ site:example.com inurl:&                    ⎘  ✕ │   │
│  ├──────────────────────────────────────────────────┤   │
│  │ site:example.com ext:php | ext:aspx | ...   ⎘  ✕ │   │
│  └──────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────┘
```

---

## Quick Start

```bash
git clone https://github.com/yourusername/dorker.git
cd dorker
open dorker.html   # macOS
xdg-open dorker.html  # Linux
start dorker.html  # Windows
```

Or just **[download the file](./dorker.html)** and open it. That's it.

---

## Built-in Dork Categories

### 🔭 Reconnaissance
General footprinting — exposed pages, CMS fingerprinting, Nginx defaults, public endpoints.

```
site:{domain} inurl:&
site:{domain} inurl:wp-content | inurl:wp-admin | inurl:wp-login
site:{domain} intitle:"welcome to Nginx"
```

### 📂 Sensitive Files
Exposed configs, backups, environment files, source control artifacts.

```
site:{domain} ext:env | ext:bak | ext:log | ext:conf | ext:git | ext:htpasswd
site:{domain} filetype:pdf | filetype:doc | filetype:xls
site:{domain} intext:"index of" (passwd|shadow|htpasswd)
```

### 🔀 Open Redirect
URL parameters that may redirect to external hosts.

```
site:{domain} inurl:url= | inurl:return= | inurl:next= | inurl:redir= inurl:http
```

### 🔑 Secrets & Tokens
API explorers, swagger docs, exposed credentials in query strings.

```
site:{domain} inurl:swagger | inurl:api-docs | inurl:api-explorer
site:{domain} inurl:password= | inurl:secret= | inurl:token= inurl:&
```

### 🐛 Vulnerabilities
SQL error messages, LFI-prone paths, CGI scripts.

```
site:{domain} "SQL syntax" | "mysql_fetch" | "ORA-" | "Warning: pg_"
site:{domain} inurl:".php?id=" | inurl:".asp?id="
site:{domain} inurl:"/cgi-bin/" ext:cgi | ext:pl | ext:sh
```

---

## Adding Custom Dorks

Use `{domain}` as a placeholder — it gets replaced with whatever target you type.

```
site:{domain} inurl:graphql
site:{domain} ext:yaml | ext:yml inurl:docker
site:{domain} "internal use only" | "confidential"
```

All custom dorks and categories persist in `localStorage` automatically.

---

## Engine Themes

| Engine | Color | URL |
|---|---|---|
| Google | 🟠 Orange | `google.com/search` |
| Bing | 🔵 Blue | `bing.com/search` |
| DuckDuckGo | 🔴 Red | `duckduckgo.com` |
| Brave Search | 🟣 Purple | `search.brave.com` |
| Yandex | 🟡 Yellow | `yandex.com/search` |

---

## Disclaimer

> This tool is intended for **authorized security testing and research only**.  
> Running dorks against targets you do not have permission to test may violate laws including the Computer Fraud and Abuse Act (CFAA) and equivalent legislation in your jurisdiction.  
> The author assumes no responsibility for misuse.  
> **Always get written permission before testing.**

---

## Contributing

PRs are welcome. Ideas worth contributing:

- New dork patterns (with category and description)
- Additional search engines
- Export to `.txt` / `.csv`
- Dark/light mode toggle
- Dork scoring or severity tagging

```bash
git checkout -b feature/my-dorks
# add your dorks or feature
git commit -m "feat: add GraphQL dork patterns"
git push origin feature/my-dorks
```

---

## License

MIT — do whatever you want, just don't be evil.

---


