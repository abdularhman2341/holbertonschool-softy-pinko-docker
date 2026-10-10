# Softy Pinko Docker

A step-by-step project that containerizes a web application with Docker. It starts with a single Ubuntu image and ends with three services, a front-end, a back-end API and a reverse proxy, run together by Docker Compose.

## Architecture (task5)

```
Browser ──► Proxy (Nginx :80) ──┬──► /      ──► Front-end (Nginx :9000)
                                 └──► /api   ──► Back-end (Flask :5252)
```

Only the proxy is reachable from outside. The front-end and back-end are reachable only inside the Docker network.

## Tasks

| Directory | Description |
|-----------|-------------|
| `task0` | Base Ubuntu image that updates APT and prints `Hello, World!` |
| `task1` | Back-end: Python 3, pip and Flask serving `/api/hello` on port 5252 |
| `task2` | Project split into `back-end/` and `front-end/`; static site served by Nginx on port 9000 |
| `task3` | Front-end fetches data from the back-end through AJAX; CORS enabled with `flask-cors` |
| `task4` | Both services orchestrated with `docker-compose.yml` |
| `task5` | Nginx reverse proxy on port 80 routes `/` to the front-end and `/api` to the back-end |

## Requirements

- Docker Desktop (or Docker Engine with the Compose plugin)

## Usage

### task0

```bash
cd task0
docker build -t softy-pinko:task0 .
docker run -it --rm softy-pinko:task0
```

### task1

```bash
cd task1
docker build -t softy-pinko:task1
