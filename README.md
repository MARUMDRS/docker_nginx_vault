# Vaultwarden with Nginx Reverse Proxy

This repository contains a Docker Compose setup for running Vaultwarden (Bitwarden) server with Nginx as a reverse proxy.

## Table of Contents

- [About the Project](#about-the-project)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Contact](#contact)

## About the Project

This project sets up a self-hosted Vaultwarden server (an unofficial Bitwarden server) using Docker Compose. Nginx is used as a reverse proxy to handle HTTPS and direct traffic to the Vaultwarden server.

## Getting Started

To get a local copy up and running follow these steps.

### Prerequisites

Ensure you have the following installed on your system:
- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)
- [htpasswd](https://httpd.apache.org/docs/2.4/programs/htpasswd.html)
- [SelfSigned SSL Certificates](https://www.digitalocean.com/community/tutorials/how-to-create-a-self-signed-ssl-certificate-for-nginx-in-ubuntu-16-04) *if needed*
- [LetsEncryptCerts](https://macdonaldchika.medium.com/how-to-install-tls-ssl-on-docker-nginx-container-with-lets-encrypt-5bd3bad1fd48)

Other places for further study:
-[Docker Volumes](https://docs.docker.com/storage/volumes/)
-[Docker Mounts](https://docs.docker.com/storage/bind-mounts/)
-[Nginx in Docker](https://www.docker.com/blog/how-to-use-the-official-nginx-docker-image/)
### Installation

1. Clone the repository:
   ```sh
   git clone https://github.com/your_username/vaultwarden-nginx.git
   cd vaultwarden-nginx

2. Customize the configuration files as needed.

3. Run the Docker Compose setup:
   ```sh
   docker-compose up -d

## Configuration
If you want to access the /admin page, an htpasswd file is neeeded.
1. The htpasswd File
   ```sh
   sudo apt-get install apache2-utils
   htpasswd -c ./adminpage/.htpasswd your_username

*If you do not need the /admin page,then you should go to the nginx configuration file (nginx.conf) and comment this part:

    location /admin {
        ...
    }

2. Docker Compose File

The docker-compose.yml file includes two services: vaultwarden and nginx. You can tweak them as you like.

3.  Nginx Configuration

The nginx.conf file contains the configuration of the nginx server.

## Usage
Once the containers are up and running, you can access Vaultwarden at https://your-domain.com (replace with your actual domain).

