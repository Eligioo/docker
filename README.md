
# Install with composer
```json
  // add the following repository:
  // we are misusing the silverstripe-module since it installs in the root folder
  // the reference is the branchname

 "repositories"[
    {
      "type": "package",
      "package": {
        "name": "eligioo/docker",
        "version": "1.0",
        "type": "silverstripe-module",
        "source": {
          "type": "git",
          "url": "git@github.com:Eligioo/docker.git",
          "reference": "laravel"
        }
      }
    }
 ]
```

```bash
composer require eligioo/docker
```


# Install Docker on Ubuntu

Update the `apt` package index:

```
sudo apt-get update
```

Install packages to allow `apt` to use a repository over HTTPS:
```
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
```

Add Docker’s official GPG key:

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

```
sudo add-apt-repository \
  "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) \
  stable"
```
Update the `apt` package index.
```
sudo apt-get update
```

Install the latest version of Docker Engine - Community and containerd:
```
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

Verify that Docker Engine - Community is installed correctly by running the hello-world image.
```
sudo docker run hello-world
```

# Install Docker Compose on Ubuntu

Run this command to download the current stable release of Docker Compose:
```
sudo curl -L "https://github.com/docker/compose/releases/download/1.25.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

Apply executable permissions to the binary:
```
sudo chmod +x /usr/local/bin/docker-compose
```

Test installation:
```
sudo docker-compose --version
```

# Manage Docker as a non-root user
The Docker daemon binds to a Unix socket instead of a TCP port. By default that Unix socket is owned by the user `root` and other users can only access it using `sudo`. The Docker daemon always runs as the `root` user.

If you don’t want to preface the `docker` command with `sudo`, create a Unix group called `docker` and add users to it. When the Docker daemon starts, it creates a Unix socket accessible by members of the `docker` group.

#### The docker group grants privileges equivalent to the root user. For details on how this impacts security in your system, see [Docker Daemon Attack Surface](https://docs.docker.com/engine/security/security/#docker-daemon-attack-surface).

Create the docker group.
```
sudo groupadd docker
```

Add your user to the docker group.
```
sudo usermod -aG docker $USER
```

Log out and log back in so that your group membership is re-evaluated.

On Linux, you can also run the following command to activate the changes to groups:
```
newgrp docker 
```

Verify that you can run docker commands without sudo.
```
docker run hello-world
```