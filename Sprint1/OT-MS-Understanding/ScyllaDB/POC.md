![image](https://github.com/user-attachments/assets/aa906a09-a286-4976-8907-ca2720b8d3b3)

| Author          | Created on | Version   | Last updated by |  Internal Reviewer | L0  | L1  | L2  |
|-----------------|------------|-----------|------------------|--------------------|-----|-----|-----|
| Aditya Tripathi | 28-04-25   | version 1 | N/A              | Priyanshu        | Khushi | Rishabh | Piyush |

## Table Of Content

1. [Introduction](#introduction)  
2. [Pre-requisites](#pre-requisites)  
3. [Software Overview](#software-overview)  
4. [System Requirements](#system-requirements)  
5. [ScyllaDB Installation and Configuration](#scylladb-installation-and-configuration)  
   - [Method 1: Installation of ScyllaDB with script](#method-1-installation-of-scylladb-with-script)  
   - [Method 2: Manual Installation using APT](#method-2-manual-installation-method-using-apt-repository-for-setting-up-scylladb-on-ubuntu)   
6. [Conclusion](#conclusion)  
7. [Contacts](#contacts)  
8. [References](#references)


## Introduction
This guide explains how to set up ScyllaDB on a local machine. ScyllaDB is a fast NoSQL database that works with Cassandra tools and supports easy integration. In this project, it's used in the Employee API to handle employee data efficiently.

## Pre-requisites

Before diving into the Installation of scyllaDB, let’s ensure the following prerequisites meet as its requirements.

## Software Overview
|                  |         |
|:----------------:|:-------:|
| **Software Name:**| ScyllaDB|
|**Version:**| 6.2 |

## System Requirements
| **Requirements** | **Details** |
|---------|---------|
| OS |  Ubuntu 22.4 |
| Vm type | t2 medium |
| Disk space | 30 GB |



# Scylladb Installation and configuration
### Two Methods to Install ScyllaDB on a Linux Machine

# Method 1. Installation of ScyllaDB with script

![_- visual selection (1)](https://github.com/user-attachments/assets/3823f0a2-8aca-49df-b84d-502454c421e7)


### The quickest way to install ScyllaDB is by using the provided script.

## 1. Run the installation script:
```
curl -sSf https://get.scylladb.com/server | sudo bash
sudo scylla_io_setup
```
![Screenshot 2025-05-01 101338](https://github.com/user-attachments/assets/2c46ffe2-f5f0-47e0-98a2-7754d3a46971)

## 2. Start the ScyllaDB server and check its status:
```
sudo systemctl start scylla-server
sudo systemctl status scylla-server
```
![Screenshot 2025-05-01 101414](https://github.com/user-attachments/assets/b1f49946-6324-4e72-9577-8f6133baee31)

## 3. Access ScyllaDB using cqlsh:
```
cqlsh
```
![Screenshot 2025-05-01 111345](https://github.com/user-attachments/assets/cff503de-aab4-4d94-ae1e-1e087a40e738)

# Method 2. Manual installation method using APT repository for setting up ScyllaDB on Ubuntu

![_- visual selection](https://github.com/user-attachments/assets/57363f9c-dcae-482e-984b-e66bf2b7d242)

## 1. Install a repo file and add the ScyllaDB APT repository to your system:

```bash
sudo mkdir -p /etc/apt/keyrings

sudo gpg --homedir /tmp --no-default-keyring --keyring /etc/apt/keyrings/scylladb.gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys A43E06657BAC99E3
```

## 2. Add ScyllaDB repository:
  
```bash
sudo wget -O /etc/apt/sources.list.d/scylla.list http://downloads.scylladb.com/deb/debian/scylla-6.2.list
```

### 3. Install ScyllaDB packages.

```bash
sudo apt-get update`
sudo apt-get install -y scylla
```

## **Start ScyllaDB**:

### 1. Check if ScyllaDB is running:

```bash 
sudo systemctl status scylla-server
```

### 2. If ScyllaDB is not running, update the configuration file:

```bash
sudo vi /etc/scylla/scylla.yaml
```

### 3. Update configuration file of scylla
```bash
Add these configurations:
rpc_address <private-ip>`
```

### 4. Configure I/O settings for ScyllaDB on your VM

```bash
sudo /opt/scylladb/scripts/scylla_io_setup
```

### 5. Restart ScyllaDB

```bash 
sudo systemctl start scylla-server
```

### 6. Verify ScyllaDB status:

```bash
sudo systemctl status scylla-server
```
![Screenshot 2025-05-01 101414](https://github.com/user-attachments/assets/36c37e1b-35a6-4c81-916e-6f8ee7b91294)


### 7. Access ScyllaDB and make a table:

```bash
cqlsh 10.0.26.146 9042 -u scylladb -p password

CREATE KEYSPACE IF NOT EXISTS employee_db 
WITH replication = {
  'class': 'SimpleStrategy', 
  'replication_factor': 1
};
```

![Screenshot 2025-05-01 105727](https://github.com/user-attachments/assets/a8a681b4-9703-43ee-8003-b5605b21c13b)

## Conclusion
ScyllaDB is a high-performance NoSQL database built for speed and low-latency access. It works well with tools made for Cassandra and is designed for scalability and fault tolerance. In the Employee API, ScyllaDB helps store and query employee data quickly and reliably, even as the data grows.

## Contacts

| Name| Email Address      | GitHub | URL |
|-----|--------------------------|----------|---------|
| Aditya Tripathi | aditya.tripathi.snaatak@mygurukulam.co | 


## References

| Source                                                                                     | Description                                |
| ------------------------------------------------------------------------------------------ | ------------------------------------------ |
| [ScyllaDB Installation Guide](https://opensource.docs.scylladb.com/stable/getting-started/install-scylla/index.html) | Step by Step installation guide ScyllaDB. |
| [Dcumentation of ScyllaDB](https://github.com/avengers-p11/Documentation/blob/main/OT%20MS%20Understanding/ScyllaDB/ScyllaDB%20Documentation/README.md) | What is scyllaDB a detailed documentation. |
