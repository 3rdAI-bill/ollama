# Ollama Docker

Minimal Docker Compose setup for [Ollama](https://ollama.com) with optional NVIDIA GPU support.

## Quick start (CPU)

```bash
docker compose up -d
```

API: `http://localhost:11434`. Pull models with `docker exec ollama ollama pull <model>`.

## GPU (NVIDIA)

**Prerequisites:** Linux host with NVIDIA drivers (`nvidia-smi` works) and [NVIDIA Container Toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html). One-time setup on the GPU host:

```bash
sudo bash scripts/install-nvidia-container-toolkit.sh
```

Then start Ollama with GPU:

```bash
docker compose -f docker-compose.yml -f docker-compose.gpu.yml up -d
```

Or set `COMPOSE_FILE=docker-compose.yml:docker-compose.gpu.yml` and run `docker compose up -d`.

## Files

| File | Purpose |
|------|---------|
| `docker-compose.yml` | Ollama service, CPU-only (works on any host). |
| `docker-compose.gpu.yml` | Override that gives the container NVIDIA GPU access. |
| `scripts/install-nvidia-container-toolkit.sh` | Install and configure the toolkit on the GPU host. |

## Usage from another stack

To use this Ollama instance from another Docker stack (e.g. Agent Zero), attach that stack to the same network and set the LLM API base to `http://ollama:11434`, or use the host's IP and port `11434` if the port is published.
