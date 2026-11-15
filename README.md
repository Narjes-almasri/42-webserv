<p align="center">
  <img src="assets/webserv-banner.jpg" alt="A stream of HTTP requests flowing into a server" width="100%" />
</p>

<h1 align="center">⚡ Webserv</h1>
<p align="center"><strong>From socket to response.</strong><br />A lightweight HTTP/1.1 server in C++98, built as a 42 team project.</p>

<p align="center">
  <img alt="C++98" src="https://img.shields.io/badge/C%2B%2B-98-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white" />
  <img alt="HTTP 1.1" src="https://img.shields.io/badge/HTTP-1.1-00A7A7?style=for-the-badge" />
  <img alt="42 Webserv" src="https://img.shields.io/badge/42-Webserv-00BABC?style=for-the-badge" />
  <img alt="Event-driven I/O" src="https://img.shields.io/badge/I%2FO-poll()-5B55D9?style=for-the-badge" />
</p>

---

## 🌐 What is Webserv?

Webserv is an educational systems-programming project about the machinery behind a web request: accepting a connection, parsing HTTP, choosing a route, and sending the right response. The implementation uses low-level networking and a non-blocking event loop.

> This is a personal fork of the original team repository. The original project and commit history are preserved: [LeenAlmahthi/webserv-](https://github.com/LeenAlmahthi/webserv-).

## 🔄 Request flow

```mermaid
flowchart LR
    B["Browser / client"] --> P["poll() event loop"]
    P --> H["Parse HTTP request"]
    H --> R{"Route"}
    R --> S["Static file"]
    R --> U["Upload"]
    R --> C["CGI"]
    S --> O["HTTP response"]
    U --> O
    C --> O
    classDef client fill:#e8f7ff,stroke:#16a6cc,color:#102a43,stroke-width:2px
    classDef event fill:#e9e7ff,stroke:#6f63e8,color:#201a52,stroke-width:2px
    classDef route fill:#fff3dc,stroke:#e89b2c,color:#402b09,stroke-width:2px
    classDef output fill:#e6fbf2,stroke:#25a878,color:#103b2c,stroke-width:2px
    class B client
    class P,H event
    class R,S,U,C route
    class O output
```

## ✨ Project scope

| Area | What it covers |
| --- | --- |
| ⚡ **Networking** | Non-blocking client/server sockets managed with `poll()` |
| 🧭 **Routing** | Multiple server configurations, listening ports, methods, and redirects |
| 📄 **Static content** | Files, index pages, and directory listings |
| 📤 **Uploads** | File upload handling and request-body limits |
| 🧩 **CGI** | Script execution configured by file extension |
| 🛠️ **HTTP details** | Error pages and chunked request-body decoding |

## 🚀 Build and run

```bash
make
./webserv configs/webserv.conf
```

The example configuration listens on `127.0.0.1:8080` and demonstrates static files, CGI, uploads, and redirects. A second example is available at `configs/test.config`.

## 🧪 Try it

Start the server in one terminal, then try:

```bash
curl -i http://127.0.0.1:8080/
python3 tests/raw_requests.py
bash tests/stress_static.sh
```

The repository also includes CGI and upload test scripts. Make sure the configured interpreter paths and test prerequisites exist on your machine before running them.

## 🤝 Team

Built with **[Narjes Almasri](https://github.com/Narjes-almasri)**, **[Leen](https://github.com/LeenAlmahthi)**, and **[Sara Kteifan](https://github.com/SaraKteifan)**. This fork keeps the team project's original history and attribution.

## 📌 Project note

This is a 42 coursework project, not a production web server. The features above describe project scope; validate behavior against your campus subject and evaluation tests before presenting it as fully compliant.
