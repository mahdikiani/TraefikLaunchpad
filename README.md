# Traefik Docker Compose Launchpad
This repository contains a simple and reusable Docker Compose configuration for [Traefik](https://traefik.io/), a modern HTTP reverse proxy and load balancer. It is designed to be included as a Git submodule in other projects to easily set up Traefik as a reverse proxy.

## Features

- **Automated HTTPS**: Automatically issue and renew SSL certificates using Let's Encrypt.
- **Easy Configuration**: Uses Docker labels for easy service configuration.
- **Modularity**: Can be included as a submodule in any Docker-based project.

## Prerequisites

- Docker
- Docker Compose

## Installation

To use this project as a submodule in your project, run the following command in the root of your project's repository:

```bash
git submodule add https://github.com/mahdikiani/TraefikLaunchpad.git path/to/submodule
```

## Usage

1. Navigate to the submodule directory:

```bash
cd path/to/submodules
```

2. Start Traefik by running:
```bash
touch acme.json
chmod 600 acme.json
docker-compose -f traefik.yml up -d
```

3. Configure your other services in Docker Compose to use Traefik by setting appropriate labels. Here's an example for a service:
```yaml
services:
  web:
    image: nginx
    labels:
      - "traefik.http.routers.web.rule=Host(`yourdomain.com`)"
      - "traefik.http.routers.web.tls.certresolver=letsencrypt"
```

## Configuration

This module comes with a default configuration for Traefik, which you can modify as needed. The traefik docker configuration file is `traefik.yml`.


## License

This project is open source and available under the [MIT License](https://github.com/mahdikiani/TraefikLaunchpad/blob/main/LICENSE).

## Authors
- [Mahdi Kiani](https://github.com/mahdikiani)

For more information on Traefik, visit the [official Traefik documentation](https://traefik.io/).