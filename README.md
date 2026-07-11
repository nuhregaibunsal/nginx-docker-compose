# i2i Academy — Containerization

A minimal containerization exercise: a static web page served by **Nginx**, orchestrated
with **Docker Compose**. The same setup runs locally and on a cloud virtual machine.

## Contents

```
.
├── index.html            # Static page with the welcome message
├── nginx/default.conf    # Nginx server configuration
├── docker-compose.yml    # Nginx service definition
└── README.md
```

## Run locally

Requires Docker and Docker Compose.

```bash
docker compose up -d
```

Then open the page in a browser:

```
http://localhost:8080
```

Stop and remove the container:

```bash
docker compose down
```

## How it works

- The service uses the official `nginx:latest` image.
- `index.html` is mounted into the container at `/usr/share/nginx/html/index.html`.
- `nginx/default.conf` is mounted at `/etc/nginx/conf.d/default.conf` to configure the server.
- Host port `8080` is mapped to the container's port `80`.

## Cloud deployment

The exact same files run on a cloud virtual machine: install Docker and Docker Compose on
the VM, copy this project to it, run `docker compose up -d`, and open the port used
(`8080`) in the VM's firewall/security group. The page is then reachable at
`http://<vm-public-ip>:8080`.
