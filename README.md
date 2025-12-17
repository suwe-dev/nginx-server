# Docker NGINX Static Web Server

This project provides a lightweight Docker-based setup for serving static web content using **NGINX**. It is suitable for local development, testing, or simple production use cases where a static website or HTML assets need to be served reliably.

---

## Project Structure

```text
.
├── docker-compose.yml
├── nginx/
│   └── nginx.conf
└── html/
    ├── index.html
    └── about.html
```

* **docker-compose.yml** – Defines the NGINX service and runtime configuration
* **nginx/nginx.conf** – Custom NGINX configuration
* **html/** – Static website files served by NGINX

---

## Prerequisites

* Docker (v20+ recommended)
* Docker Compose (v2+ recommended)

Verify installation:

```bash
docker --version
docker compose version
```

---

## Docker Compose Configuration

The project uses the following Docker Compose service definition:

* **Image**: `nginx:latest`
* **Container name**: `nginx-web-server`
* **Port mapping**: `80:80`
* **Volumes**:

  * Custom NGINX configuration mounted read-only
  * Static HTML files mounted read-only
* **Restart policy**: `unless-stopped`

---

## Usage

### 1. Start the Server

From the project root directory:

```bash
docker compose up -d
```

This will:

* Pull the NGINX image if not present
* Start the container in detached mode
* Serve content from the `html/` directory

---

### 2. Access the Application

Open a browser and navigate to:

* [http://localhost](http://localhost)
* [http://localhost/about.html](http://localhost/about.html)

Or use curl in terminal to verify the installation in servers

```bash
curl http://localhost
curl http://localhost/about.html
```

---

### 3. Stop the Server

```bash
docker compose down
```

---

## Customization

### Modify HTML Content

Edit or add files in the `html/` directory:

```text
html/
├── index.html
├── about.html
└── contact.html
```

Changes are reflected immediately (no container rebuild required).

---

### Modify NGINX Configuration

Edit:

```text
nginx/nginx.conf
```

After making changes, reload the container:

```bash
docker compose restart nginx
```

---

## Common Commands

```bash
# View running containers
docker ps

# View logs
docker logs nginx-web-server

# Restart the service
docker compose restart
```

---

## Notes

* All mounted volumes are **read-only** for improved safety
* This setup is intended for **static content** only
* For HTTPS, reverse proxying, or dynamic backends, additional configuration is required

---

## License

This project is licensed under MIT License

Copyright (c) 2025 Suwethan

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.