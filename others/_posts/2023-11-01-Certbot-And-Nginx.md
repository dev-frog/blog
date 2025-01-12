layout: post
title: Hono REST API
description: >

---


## Introduction

Let’s Encrypt is a Certificate Authority (CA) that provides an easy way to obtain and install free TLS/SSL certificates, 
thereby enabling encrypted HTTPS on web servers. It simplifies the process by providing a software client, Certbot, 
that attempts to automate most (if not all) of the required steps. Currently, the entire process of obtaining and 
installing a certificate is fully automated on both Apache and Nginx.


## Command

> Install Certbot and it’s Nginx plugin with

```bash
sudo apt install certbot python3-certbot-nginx

```

> Step 2 — Confirming Nginx’s Configuration

```bash
sudo ufw status

sudo ufw allow 'Nginx Full'
sudo ufw delete allow 'Nginx HTTP'

sudo ufw status

``

> Step 4 — Obtaining an SSL Certificate 

```bash
sudo certbot --nginx -d example.com -d www.example.com
```

> Step 5 — Verifying Certbot Auto-Renewal

```bash
sudo systemctl status certbot-renew.timer
```

> To test the renewal process, you can do a dry run with

```bash

sudo certbot renew --dry-run

```
