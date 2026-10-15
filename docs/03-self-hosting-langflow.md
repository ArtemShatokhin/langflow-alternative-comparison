# Self-hosting Langflow, and self-hosting the system around it

Self-hosting Langflow means running one service on your own infrastructure: the builder and the flows it serves. Self-hosting Kortix means running the whole company layer, the web app, the API and the database, as one stack, while each session still runs on its own cloud computer. Both paths are documented by the projects themselves.

## Self-hosting Langflow with pip

Langflow installs as a Python package. Its repository recommends Python 3.10 to 3.14 and `uv`, then:

```sh
uv pip install langflow -U
uv run langflow run
```

The server starts at http://127.0.0.1:7860. Official release packages disable automatic login by default, so you set `LANGFLOW_SUPERUSER_PASSWORD` before starting and sign in with the username `langflow` ([langflow-ai/langflow](https://github.com/langflow-ai/langflow)).

## Self-hosting Langflow with Docker

The official image runs in one command:

```sh
docker run -p 7860:7860 \
  -e LANGFLOW_SUPERUSER_PASSWORD=CHANGE_ME \
  langflowai/langflow:latest
```

Official Docker images require authentication by default, and the app is then available at http://localhost:7860 ([Langflow documentation](https://docs.langflow.org/deployment-docker)).

## Self-hosting Langflow with Docker Compose

For a persistent database instead of the default SQLite file, Langflow ships a Compose file that includes PostgreSQL and a persistent volume:

```sh
git clone https://github.com/langflow-ai/langflow.git
cd langflow/docker_example
docker compose up
```

You configure database credentials and the superuser password through a `.env` file beside the Compose file ([Langflow documentation](https://docs.langflow.org/deployment-docker)). Langflow also documents a remote server with Docker and Caddy, Nginx with automatic certificates, and Kubernetes ([deployment overview](https://docs.langflow.org/deployment-overview)).

## What changes when the whole layer is one repo

Self-hosting Langflow gives a team its flows on its own hardware. The team still runs the surrounding application, and the flows, projects and served endpoints are state inside the Langflow instance. Self-hosting Kortix changes the unit you operate. Kortix is open source, and the thing you run is the company repo: your agents, their skills, your company memory, and every connector live in one git repo you own, and the instance serves the web app, the API and the database from a single stack.

## Self-hosting Kortix

Kortix self-host is one Docker Compose stack that the `kortix self-host` CLI installs, configures and updates. On a server that already has Docker and the Compose plugin:

```sh
curl -fsSL https://kortix.com/install | bash
kortix self-host init --domain kortix.example.com --admin-email you@example.com
kortix self-host start
```

A bare Linux server can run a bootstrap script instead, which installs Docker and the CLI, then starts the stack with a TLS certificate. Afterwards, `kortix self-host configure` reviews the setup answers and `kortix self-host doctor` checks the instance. Both the bootstrap and the manual path are on the [Kortix self-hosting docs](https://kortix.com/docs/host).

## What a self-hosted Kortix needs

- A Linux server with a public IP, plus DNS records for the domain and its API subdomain before the first start.
- Ports 80 and 443 open inbound.
- A sandbox provider key, so sessions can start. Sessions run on a cloud sandbox provider, and the instance has to be reachable from the internet so those sandboxes can call back.
- A model provider key, which you add in the web app after the first sign-in.

Self-host is free. The stack pulls its images from Docker Hub, so the server needs outbound access ([Kortix self-hosting docs](https://kortix.com/docs/host)).
