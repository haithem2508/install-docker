# install-docker

Simple scripts to install Docker Engine and the Docker Compose plugin on Debian and Ubuntu VMs, straight from Docker's official repositories.

## Scripts

- `install-docker-debian.sh` - for Debian
- `install-docker-ubuntu.sh` - for Ubuntu

Each script:

1. Removes conflicting distro packages (`docker.io`, `podman-docker`, old `containerd`, etc.)
2. Adds Docker's official GPG key and apt repository
3. Installs `docker-ce`, `docker-ce-cli`, `containerd.io`, `docker-buildx-plugin` and `docker-compose-plugin`
4. Starts and enables the Docker service

## Usage

install the appropriate script for each OS flavor:

```sh
wget https://raw.githubusercontent.com/haithem2508/install-docker/refs/heads/main/install-docker-<name>.sh
chmod +x install-docker-<name>.sh
```

Run the script for your distribution:

```sh
# Debian
sh install-docker-debian.sh

# Ubuntu
sh install-docker-ubuntu.sh
```

The scripts use `sudo`, so run them as a user with sudo privileges.

## Verify

```sh
docker --version
docker compose version
docker run hello-world
```

## Run Docker without sudo (optional)

```sh
sudo usermod -aG docker $USER
```

Log out and back in for the group change to take effect.

## Notes

- Docker Compose is installed as the `docker compose` plugin (v2), not the standalone `docker-compose` binary.
- Tested on current Debian and Ubuntu releases. The repository suite is detected automatically from `/etc/os-release`.
