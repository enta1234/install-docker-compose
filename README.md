# Installing Docker and Docker Compose
on CentOS 7 is a straightforward process. Here's a step-by-step guide:

**Prerequisites:**

- A CentOS 7 system with sudo access
- An internet connection

**Step 0: Uninstall old versions**

Older versions of Docker went by docker or docker-engine. Uninstall any such older versions before attempting to install a new version, along with associated dependencies.

```bash
sudo yum remove docker \
                docker-client \
                docker-client-latest \
                docker-common \
                docker-latest \
                docker-latest-logrotate \
                docker-logrotate \
                docker-engine
```

**Step 1: Install the required packages**

Before installing Docker, ensure you have the necessary packages installed. Update the system's package repository:

```bash
sudo yum update -y
```

Install the required packages for Docker installation:

```bash
sudo yum install -y yum-utils
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```

**Step 2: Install Docker**

Enable the Docker repository:

```bash
sudo yum install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
```

**Step 3: Start and verify Docker service**

Start the Docker service:

```bash
sudo systemctl start docker
```

Enable Docker to start automatically at system boot:

Verify that Docker is running:

```bash
sudo systemctl status docker
```

You should see an output indicating that Docker is active (running).

**Step 4: Install Docker Compose**

Download the latest Docker Compose release:

```bash
wget https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)
```

Move the downloaded file to the /usr/local/bin directory:

```bash
sudo mv docker-compose-$(uname -s)-$(uname -m) /usr/local/bin/docker-compose
```

Make the docker-compose executable:

```bash
sudo chmod +x /usr/local/bin/docker-compose
```

Verify that Docker Compose is installed:

```bash
docker-compose version
```

You should see the installed Docker Compose version number.

**Step 5: Verify Docker Compose installation**

To verify that Docker Compose is installed correctly, create a simple Docker Compose file named docker-compose.yml with the following content:

```yaml
version: "3.9"

services:
  hello:
    image: hello-world
```

Save the file and run the following command:

```bash
docker-compose up -d
```

This will create and run a Docker container based on the hello-world image. You can verify that the container is running using the following command:

```bash
docker-compose ps
```

You should see an output indicating that the hello container is running.

Congratulations! You have successfully installed Docker and Docker Compose on CentOS 7.
