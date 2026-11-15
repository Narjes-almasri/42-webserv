# Webserv

**A lightweight HTTP/1.1 server in C++98, built as a 42 team project.**

This educational systems-programming project explores how an HTTP server receives requests, routes them, and responds using low-level networking and non-blocking I/O.

## Project scope

- Non-blocking client and server sockets managed with `poll()`
- Multiple server configurations and listening ports
- `GET`, `POST`, and `DELETE` request handling
- Static-file serving, index pages, and directory listings
- Redirects and configurable error pages
- File uploads and request-body limits
- CGI execution configured by file extension
- Chunked request-body decoding

## Build and run

```bash
make
./webserv configs/webserv.conf
```

The example configuration listens on `127.0.0.1:8080` and demonstrates routes for static files, CGI, uploads, and redirects. A second configuration is available at `configs/test.config`.

## Try it

```bash
curl -i http://127.0.0.1:8080/
python3 tests/raw_requests.py
bash tests/stress_static.sh
```

The repository also includes CGI and upload test scripts. Ensure the configured interpreter paths and test prerequisites exist on your machine before running them.

## Team

Built with **Narjes Almasri**, **Leen**, and **Sara Kteifan**. This fork keeps the team project’s original history and attribution.

## Note

This is a 42 coursework project, not a production web server. The listed features describe project scope; validate behavior against your campus subject and evaluation tests before presenting it as fully compliant.
