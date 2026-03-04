# Self-Hosted Media Player

## Overview
This project is a self-hosted media infrastructure deployed on Ubuntu Server using Docker.

It enables secure remote media streaming without traditional port forwarding by leveraging Cloudflare Tunnel. The system is designed with clear separation between service definitions and persistent data, following production-style container orchestration principles.

The primary objective of this project is to design a secure, maintainable, and scalable self-hosted environment.

---

## Architecture Overview

                            Internet  
                                ↓  
                        Cloudflare Tunnel  
                                ↓  
                        Ubuntu Homeserver
                                │    
                      ┌─────────┴─────────┐  
                      │                   │    
             Persistent Storage        Jellyfin   

All services are containerized and bound to localhost. Only selected services are exposed via Cloudflare Tunnel.

---

## Tech Stack

![Ubuntu](https://img.shields.io/badge/Ubuntu-E95420?logo=ubuntu&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white)
![Jellyfin](https://img.shields.io/badge/Jellyfin-00A4DC?logo=jellyfin&logoColor=white)
![Cloudflare](https://img.shields.io/badge/Cloudflare-F38020?logo=cloudflare&logoColor=white)

### Infrastructure
- Ubuntu Server (Linux)
- SSH Remote Access

### Containerization
- Docker
- Docker Compose
- Docker Networking & Volume Management

### Media Platform
- Jellyfin (Self-hosted media streaming)

### Networking & Security
- Cloudflare Tunnel (Zero Trust exposure)
- Localhost Service Binding
- No public port forwarding

---

## System Design Principles

- Strict separation of services and persistent data
- Infrastructure organized under `/srv`
- Containerized deployment for portability
- No direct public port exposure
- Secure remote access through reverse tunneling

---

## Operational Practices

- Linux file permission management
- Structured media directory naming conventions
- Service isolation via Docker networking
- Centralized service configuration using Docker Compose

---

## Directory Structure

```text
/srv
├── services                # Docker Compose definitions
│   └── jellyfin
│       └── docker-compose.yml
│
├── data                    # Persistent volumes
│   ├── jellyfin
│   │   ├── cache
│   │   └── config
│   │
│   └── media
│       ├── movies
│       └── tv
│
└── infra                   # Infrastructure components
    └── tunnel
        ├── cloudflared
        └── docker-compose.yml