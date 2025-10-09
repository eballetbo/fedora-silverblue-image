# WeeChat container for Fedora Silverblue

This repository contains the necessary files to run WeeChat as a Podman container on Fedora Silverblue.

## Overview

WeeChat is a fast, light, and extensible chat client. Running it as a container on Fedora Silverblue provides isolation and easy management.

## Setup Instructions

### 1. Build the Podman Image

Build the WeeChat container image using the provided `Containerfile`:

```bash
podman build -t weechat .
```

#### Option A: Run as a Container

1.**Run the container:**

```bash
mkdir -p ~/.local/podman/weechat/config ~/.local/podman/weechat/data ~/.local/podman/.weechat/cache
podman run -it -d --name weechat -v $HOME/.local/podman/weechat:/home/user/.weechat:Z weechat
```

2.**Attach to the WeeChat container:**

To interact with WeeChat, you need to attach to its console.

```bash
podman attach weechat
```

To detach without stopping WeeChat, press `Ctrl-a d`.

3.**Stop the container:**

```bash
podman stop weechat
```

4.**Start the container again:**

```bash
podman start weechat
```

#### Option B: Run as a System Service (Recommended for persistent use)

1.**Generate a systemd service file:**

Podman can generate a systemd unit file for your container. This allows `systemd` to manage the container's lifecycle.

```bash
podman generate systemd --name weechat > ~/.config/systemd/user/weechat.service
```

2.**Reload systemd and enable the service:**

```bash
systemctl --user daemon-reload
systemctl --user enable --now weechat.service
```

Now, WeeChat will start automatically when you log in.

3.**Attach to the WeeChat session:**

Since WeeChat is running in the background, you can attach to its session using `podman attach`.

```bash
podman attach weechat
```

To detach without stopping WeeChat, press `Ctrl-a d`.

4.**Stop the service:**

```bash
systemctl --user stop weechat.service
```

5.**Start the service:**

```bash
systemctl --user start weechat.service
```




