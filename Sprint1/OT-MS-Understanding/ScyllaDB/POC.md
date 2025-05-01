## Table Of Content

- [Introduction](#introduction)
- [Pre-requisites](#pre-requisites)
- [System Requirements](#system-requirements)
- [Scylladb Installation and configuration](#scylladb-installation-and-configuration)
- [Contacts](#contacts)
- [References](#references)


## Introduction
This documentation provides a simple guide to setting up ScyllaDB locally. ScyllaDB is a high-performance, distributed NoSQL database compatible with Apache Cassandra, making it easy to integrate and migrate. In our project, ScyllaDB is used in the Employee API microservice to efficiently manage distributed data.

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
| Disk space | 20 GB |



# Scylladb Installation and configuration
### Two Methods to Install ScyllaDB on a Linux Machine
![Screenshot 2024-11-18 170054](https://github.com/user-attachments/assets/25da80d4-4f36-41c4-bc0a-0a8374e91ff3)

# Installation of ScyllaDB with basic Method
### The quickest way to install ScyllaDB is by using the provided script.

## 1. Run the installation script:
```
curl -sSf https://get.scylladb.com/server | sudo bash
sudo scylla_io_setup
```
![Screenshot 2024-11-18 161722](https://github.com/user-attachments/assets/3be1e5c9-76dc-42a1-85ba-27e17721ed84)


## 2. Start the ScyllaDB server and check its status:
```
sudo systemctl start scylla-server
sudo systemctl status scylla-server
```
![Screenshot 2024-11-18 161831](https://github.com/user-attachments/assets/9c6a0d24-22a6-44d9-ae19-79b1757f9dd7)

## 3. Access ScyllaDB using cqlsh:
```
cqlsh
```
![Screenshot 2024-11-18 161912](https://github.com/user-attachments/assets/3654db11-4887-4fce-895b-45d8211ac164)

# Method 2. Manual installation method using APT repository for setting up ScyllaDB on Ubuntu

## 1. Install a repo file and add the ScyllaDB APT repository to your system:

```bash
sudo mkdir -p /etc/apt/keyrings

sudo gpg --homedir /tmp --no-default-keyring --keyring /etc/apt/keyrings/scylladb.gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys A43E06657BAC99E3
```

## 2. Add ScyllaDB repository:
  
```bash
sudo wget -O /etc/apt/sources.list.d/scylla.list http://downloads.scylladb.com/deb/debian/scylla-6.2.list
```

![Screenshot 2024-11-12 141116](https://github.com/user-attachments/assets/ab1d7faf-e3ef-41e9-8d84-9a830bd85777)

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
  
authenticator: PasswordAuthenticator
authorizer: CassandraAuthorizer
```

### 4. Configure I/O settings for ScyllaDB on your VM

```bash
sudo /opt/scylladb/scripts/scylla_io_setup
```

![Screenshot 2024-11-12 175205](https://github.com/user-attachments/assets/c6e9883b-1e08-4159-a7b5-a486db9fe076)



### 5. Restart ScyllaDB

```bash 
sudo systemctl start scylla-server
```

### 6. Verify ScyllaDB status:

```bash
sudo systemctl status scylla-server
```

![Screenshot 2024-11-12 142659](https://github.com/user-attachments/assets/11a54d9e-9783-466f-831f-260cdc9e0e3f)

## Conclusion


ScyllaDB is a fast, scalable NoSQL database designed for low-latency operations and efficient resource use, making it ideal for microservices like the Employee API. Its distributed design ensures high availability, fault tolerance, and seamless integration with Cassandra tools. In the Employee API, ScyllaDB efficiently handles large datasets, providing fast queries, scalability, and reliability for managing employee data.



## Contacts

| Name| Email Address      | GitHub | URL |
|-----|--------------------------|----------|---------|
| Aditya Tripathi | aditya.tripathi.snaatak@mygurukulam.co | 


## References

| Source                                                                                     | Description                                |
| ------------------------------------------------------------------------------------------ | ------------------------------------------ |
| [ScyllaDB Installation Guide](https://opensource.docs.scylladb.com/stable/getting-started/install-scylla/index.html) | Comprehensive guide for installing ScyllaDB on Linux. |
| [Dcumentation of ScyllaDB](https://github.com/avengers-p11/Documentation/blob/main/OT%20MS%20Understanding/ScyllaDB/ScyllaDB%20Documentation/README.md) | Information about scyllaDB . |
| [Application Template ](https://github.com/OT-MICROSERVICES/documentation-template/wiki/Application-Template) | Document format followed from this link   |
