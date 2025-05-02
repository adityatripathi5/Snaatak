![image](https://github.com/user-attachments/assets/09ddd0a4-3ab4-4f86-9784-df29f4a0890c)

# DNS Implementation

| Author          | Created on | Version   | Last updated by |  Internal Reviewer | L0  | L1  | L2  |
|-----------------|------------|-----------|------------------|--------------------|-----|-----|-----|
| Aditya Tripathi | 01-05-25   | version 1 | N/A              | Priyanshu        | Khushi | Rishabh | Piyush |

## Table of Content

- [Introduction](#introduction)
- [Pre-requisites](#pre-requisites)
- [Implementation Steps](#implementation-steps)
- [Conclusion](#conclusion)
- [Contact Information](#contact-information)
- [Reference](#reference)


## Introduction

This document explains the implementation of DNS (Domain Name System) configuration for a domain as per the POC. DNS is responsible for translating human-readable domain names into IP addresses. In this setup, we configure DNS records using a domain registrar or DNS provider, ensuring proper routing of traffic to the server hosting the application or services.

## Pre-requisites

- **Domain Name**: Domain DNS configured to point to the server (A/AAAA records).
- **Web server**: Install **Nginx** server on your VM.

## Implementation Steps

### 1. Install Nginx

Update system packages and install Nginx.

![Screenshot 2025-05-02 174134](https://github.com/user-attachments/assets/7cfdb51d-1534-4bb3-9ceb-321d30c66f6f)

### 2. Verify Server Configuration

Check Nginx to ensure your domain is being served correctly.

```sh
sudo nano /etc/nginx/sites-available/default
```
### Now Adding this Content as given below:

```sh
server {
    listen 80;
    server_name cloudninjahp.publicvm.com;
    client_max_body_size 100M;

    index index.html index.php;
    root /var/www/html/cloudninjahp.publicvm.com/;

    access_log  /var/log/nginx/cloudninjahp.publicvm.com/access.log;
    error_log   /var/log/nginx/cloudninjahp.publicvm.com/error.log;
}
```
### Create web root dir
```sh
sudo mkdir -p /var/www/html/cloudninjahp.publicvm.com
```

### Place your HTML file
```sh
sudo nano /var/www/html/cloudninjahp.publicvm.com/index.html
```
### Now Paste the HTML code
```sh
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Welcome to CloudNinja</title>
  <style>
    body {
      background: linear-gradient(to right, #00c6ff, #0072ff);
      color: white;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      text-align: center;
      padding-top: 15%;
    }
    h1 {
      font-size: 3em;
      font-weight: bold;
      margin-bottom: 0.3em;
      text-shadow: 2px 2px 4px #000000;
    }
    p {
      font-size: 1.5em;
      font-weight: bold;
      text-shadow: 1px 1px 2px #000000;
    }
  </style>
</head>
<body>
  <h1>WELCOME TO CLOUDNINJA PAGE</h1>
  <p>Maintained by Aditya Tripathi</p>
</body>
</html>
```
### Create log directories
```sh
sudo mkdir -p /var/log/nginx/cloudninjahp.publicvm.com
```
### Test configuration
```sh
sudo nginx -t
```
![Screenshot 2025-05-02 174923](https://github.com/user-attachments/assets/802386eb-6dac-43c2-b90f-37c69fccfc3e)

### 3. Setup Your DNS A records

![image](https://github.com/user-attachments/assets/30a6a71f-6ffa-467d-8bd4-b84f251ecdeb)

### 4. Restart Web Server

Reload the server to apply the changes:
```bash
sudo systemctl reload nginx
```
![Screenshot 2025-05-02 190205](https://github.com/user-attachments/assets/33ce0659-fa7c-4dec-817c-de00c03b2455)


### 6. Validate DNS

Open `http://cloudninjahp.publicvm.com/` in a browser and ensure it shows a unsecure lock icon.

![Screenshot from 2025-05-02 17-54-08](https://github.com/user-attachments/assets/a96cd198-9859-489e-9906-85f532380161)

## Conclusion

The domain has been successfully configured with the correct DNS settings, allowing it to resolve to the target server. With proper A records and Nginx configuration in place, the domain now points to the intended web content, completing the DNS setup as per the POC. Also to configure SSL onto the same DNS you can refer this documentation [SSL Implementation](https://github.com/Cloud-NInja-snaatak/Documentation/blob/himanshu-SCRUM-123/domain_security/ssl/implementation_of_ssl/README.md)

##  **Contact Information**

| Name              | Email Address                                   |
|-------------------|--------------------------------------------------|
| Aditya Tripathi | aditya.tripathi.snaatak@mygurukulam.co         |

## Reference

| **Reference Name**  | **Description**                            | **Link**                |
|---------------------|--------------------------------------------|-------------------------|
| DNS POC             | POC on how you can set up DNS for your application     | [DNS POC](https://github.com/Cloud-NInja-snaatak/Documentation/blob/Tharik_SCRUM-119/domain_security/dns/dns_poc/README.md) |
| DNS Documentation   | Detailed documentation on DNS              | [DNS Documentation](https://github.com/Cloud-NInja-snaatak/Documentation/blob/Shubham_SCRUM-118/domain_security/dns/dns_document/README.md) |
