<div align="center" width="100%">
    <img src="./frontend/public/icon.svg" width="128" alt="" />
</div>

# Dockge

A fancy, easy-to-use and reactive docker `compose.yaml` stack oriented manager.

<img src="https://github.com/louislam/dockge/assets/1336778/26a583e1-ecb1-4a8d-aedf-76157d714ad7" width="900" alt="" />

## ⭐ Features

- Manage `compose.yaml`
- Interactive Editor for `compose.yaml`
- Interactive Web Terminal
- Reactive
   - Everything is just responsive. Progress (Pull/Up/Down) and terminal output are in real-time
- Easy-to-use & fancy UI
   - If you love Uptime Kuma's UI/UX, you will love this too
- Convert `docker run ...` commands into `compose.yaml`

## 🔧 How to Install

### Basic

Default stacks directory is `/opt/stacks`.

```
# Create a directory that stores your stacks
mkdir -p /opt/stacks

# Create a directory that stores dockge's compose.yaml
mkdir -p /opt/dockge
cd /opt/dockge

# Download the compose.yaml
wget https://raw.githubusercontent.com/louislam/dockge/master/compose.yaml

# Start Server
docker-compose up -d
```

### Advanced

If you want to store your stacks in another directory, you can change the `DOCKGE_STACKS_DIR` environment variable and volumes.

For exmaples, if you want to store your stacks in `/my-stacks`:

```yaml
version: "3.8"
services:
  dockge:
    image: louislam/dockge:1
    restart: unless-stopped
    ports:
      - 5001:5001
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
      - ./data:/app/data

      # Your stacks directory in the host
      # (The paths inside container must be the same as the host)
      - /my-stacks:/my-stacks
    environment:
      # Tell Dockge where is your stacks directory
      - DOCKGE_STACKS_DIR=/my-stacks
```


## Motivations

- I have been using Portainer for some time, but for the stack management, I am sometimes not satisfied with it. For example, sometimes when I try to deploy a stack, the loading icon keeps spinning for a few minutes without progress. And sometimes error messages are not clear.
- Try to develop with ES Module + TypeScript (Originally, I planned to use Deno or Bun.js, but they do not support for arm64, so I stepped back to Node.js)

If you love this project, please consider giving this project a ⭐.


## FAQ

#### "Dockge"?

"Dockge" is a coinage word which is created by myself. I hope it sounds like `Badge` but replacing with `Dock` - `Dock-ge`.

The naming idea was coming from Twitch emotes like `sadge`, `bedge` or `wokege`. They are all ending with `-ge`.

If you are not comfortable with the pronunciation, you can call it `Dockage`

#### Can I manage a single container without `compose.yaml`?

The main objective of Dockge is that try to use docker `compose.yaml` for everything. If you want to manage a single container, you can just use Portainer or Docker CLI.

## More Ideas?

- Stats
- File manager
- App store for yaml templates
- Get app icons
- Switch Docker context
- Support Dockerfile and build
- Support Docker swarm


# Others

Dockge is built on top of [Compose V2](https://docs.docker.com/compose/migrate/). `compose.yaml`  is also known as `docker-compose.yml`.


