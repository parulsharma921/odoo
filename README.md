# Odoo on EC2 with Docker

This guide will help you install Odoo on an AWS EC2 instance running Ubuntu using Docker.

## Prerequisites
1. AWS EC2 instance with Ubuntu (e.g., Ubuntu 20.04).
2. Docker installed on the EC2 instance.

## Steps

### 1. Launch an EC2 Instance
- Go to the [AWS Console](https://aws.amazon.com/console/).
- Launch an EC2 instance with Ubuntu (choose `Ubuntu 20.04` or later).
- Allow SSH access to the EC2 instance from your local machine's IP.

### 2. Connect to the EC2 Instance

ssh -i /path/to/your-key.pem ubuntu@<EC2-IP-ADDRESS>


 ## Install Docker on EC2

sudo apt update
sudo apt install -y docker.io
sudo systemctl enable --now docker

## Pull the Odoo Docker Image
sudo docker pull odoo

## Start a PostgreSQL server
$ docker run -d -e POSTGRES_USER=odoo -e POSTGRES_PASSWORD=odoo -e POSTGRES_DB=postgres --name db postgres:15

## Run Odoo in Docker
$ docker run -p 8069:8069 --name odoo --link db:db -t odoo

## Access Odoo
Open your browser and visit http://<EC2-IP-ADDRESS>:8069 to access Odoo.


![image](https://github.com/user-attachments/assets/04d9a76f-2a60-4c4d-8e3b-c9aa1d813db8)

![image](https://github.com/user-attachments/assets/69f54dab-7ab0-4dc4-b9d6-e41cac5fcd63)


![image](https://github.com/user-attachments/assets/aeded8a6-5100-4740-8c14-8977d99a17b1)





