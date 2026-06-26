# ACUITY Deployment Script

Deploy the ACUITY platform in minutes using a single installation command. The installer automatically downloads, configures, and starts the required Docker services with minimal user interaction.

---

## Features

* 🚀 One-command installation
* 🐳 Docker-based deployment
* 🔧 Automatic dependency installation
* 📦 Automatic application setup
* 🔄 Easy updates
* 📝 Simple configuration
* 🖥️ Ubuntu server support
* ⚡ Fast deployment


# Quick Start

Install ACUITY using a single command:

```bash
wget -qO- https://raw.githubusercontent.com/digital-ECMT/acuity-docker/refs/heads/main/install.sh | bash
```

The installer is streamed directly from GitHub and executed immediately using **Bash**. No local copy of `install.sh` is saved.

---

# What the Installer Does

The installation script automatically performs the following tasks:

* Checks system requirements
* Installs required dependencies
* Installs Docker (if necessary)
* Downloads the latest application files
* Configures the environment
* Creates required directories
* Starts Docker containers
* Completes the installation

---

# Verify Installation

Check that the containers are running:

```bash
docker ps
```

View running services:

```bash
docker compose ps
```

---

# Useful Commands

Start services

```bash
docker compose up -d
```

Stop services

```bash
docker compose down
```

Restart services

```bash
docker compose restart
```

View logs

```bash
docker compose logs -f
```

---

## Linux Startup & Shutdown

After completing the installation, ACUITY can be managed using the provided startup and shutdown helper scripts. These scripts simplify starting and stopping the complete Docker environment without requiring manual Docker commands.

### Startup Script

Start the complete ACUITY environment:

```bash
wget -qO- https://raw.githubusercontent.com/digital-ECMT/acuity-docker/refs/heads/main/acuity-start-unix.sh | bash
```

or download it for repeated use:

```bash
wget https://raw.githubusercontent.com/digital-ECMT/acuity-docker/refs/heads/main/acuity-start-unix.sh

chmod +x acuity-start-unix.sh

./acuity-start-unix.sh
```

The startup script typically performs the following tasks:

* Starts all required Docker containers
* Verifies Docker is running
* Loads the appropriate Docker Compose configuration
* Starts application services in the correct order
* Displays the current container status

---

### Shutdown Script

Gracefully stop the ACUITY environment:

```bash
wget -qO- https://raw.githubusercontent.com/digital-ECMT/acuity-docker/refs/heads/main/acuity-stop-unix.sh | bash
```

or download it locally:

```bash
wget https://raw.githubusercontent.com/digital-ECMT/acuity-docker/refs/heads/main/acuity-stop-unix.sh

chmod +x acuity-stop-unix.sh

./acuity-stop-unix.sh
```

The shutdown script safely:

* Stops all running Docker containers
* Preserves application data and volumes
* Performs an orderly shutdown of services

---


# Updating

To update the application:

```bash
cd acuity-docker

git pull

docker compose pull

docker compose up -d
```

---

# Uninstall

Stop the application:

```bash
docker compose down
```

Remove the installation:

```bash
rm -rf acuity-docker
```

Optionally clean unused Docker resources:

```bash
docker system prune -a
```

---

# Documentation

Additional documentation is available in the project's GitHub Wiki.

---

# Troubleshooting

### Docker is not installed

The installer attempts to install Docker automatically. If installation fails, install Docker manually and rerun the installer.

### Permission Denied

Run the installer with elevated privileges if required:

```bash
wget -qO- https://raw.githubusercontent.com/digital-ECMT/acuity-docker/refs/heads/main/install.sh | sudo bash
```

### Port Already in Use

Check which process is using the port:

```bash
sudo lsof -i :80
```

or

```bash
sudo lsof -i :443
```

---

# Contributing

Contributions are welcome. Feel free to submit issues, feature requests, or pull requests.

---

# License

This project is licensed under the license included in this repository.
