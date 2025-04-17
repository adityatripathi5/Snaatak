![image](https://github.com/user-attachments/assets/847021e6-20cd-420c-8aca-e8f91eb72295)

| Author          | Created on | Version   | Last updated by | Last edited on | Internal Reviewer | L0  | L1  | L2  |
|-----------------|------------|-----------|------------------|----------------|--------------------|-----|-----|-----|
| Aditya Tripathi | 15-04-25   | version 1 | N/A              | N/A            | Priyanshu                | Khushi | Rishabh | Piyush |

# Golang Installation Guide

This document provides a step-by-step guide to installing Golang, covering various scenarios, including installation for OT/Microservice development and handling legacy applications.

## Table of Contents

1.  [Introduction](#introduction)
2.  [What is Golang?](#what-is-golang)
3.  [Pre-Checks](#pre-checks)
4.  [Installation](#installation)
    * [Most Widely Used Golang Version](#most-widely-used-golang-version)
    * [Latest Golang Version](#latest-golang-version)
    * [Legacy Applications (Older Golang Versions)](#legacy-applications-older-golang-versions)
    * [OT/Microservices](#otmicroservices)
5.  [Post-Checks](#post-checks)
6.  [Best Practices](#best-practices)
7.  [Conclusion](#conclusion)

## 1. Introduction

This guide will walk you through the process of installing Golang (also known as Go) on your system.  It covers the installation of the latest version, a widely used version, and how to handle older versions for legacy applications.  It also includes specific instructions for setting up Golang for OT (Observability Tools) and microservice development.
You can Refer the link to read about detailed introduction guide [Link](https://github.com/Cloud-NInja-snaatak/Documentation/blob/tharik_scrum30/commonstack/applications/golang/introduction/intro.md)

## 2. What is Golang?

Golang is a statically typed, compiled programming language designed at Google. It is known for its simplicity, efficiency, and performance.  Golang is well-suited for building a variety of applications, including:

* Web servers and APIs
* Microservices
* System programming
* Cloud-native applications

## 3. Pre-Checks

Before installing Golang, ensure the following:

* **Operating System Compatibility:** Verify that the Golang version you intend to install is compatible with your operating system (Windows, macOS, Linux).
* **Administrative Privileges:** You may need administrator or superuser privileges for certain installation steps, especially for system-wide installation.
* **Internet Access:** An active internet connection is required to download the Golang distribution.
* **Sufficient Disk Space:** Ensure you have enough free disk space to download and extract the Golang archive.

## 4. Installation

This section provides step-by-step installation instructions for different Golang versions and use cases.

### Most Widely Used Golang Version

While the "most widely used" version can change, it's often a recent stable release that has had time to mature.  As of late 2024, Go 1.20 and 1.21 are good choices.  Here's how to install (using Go 1.21 as an example):

* **Download:** Download the appropriate binary distribution from the official Golang website: [Link](https://go.dev/dl/)
* **Installation:**
    * **Linux/macOS:**

        ```bash
        wget [https://go.dev/dl/go1.21.0.linux-amd64.tar.gz](https://go.dev/dl/go1.21.0.linux-amd64.tar.gz)  
        sudo tar -C /usr/local -xzf go1.21.0.linux-amd64.tar.gz
        echo 'export PATH=$PATH:/usr/local/go/bin' >> ~/.bashrc  # Or ~/.zshrc
        source ~/.bashrc  # Or source ~/.zshrc
        ```
    * **Windows:**
        1.  Download the MSI installer from [Link](https://go.dev/dl/)
        2.  Run the installer and follow the prompts. The installer typically sets up the necessary environment variables.

### Latest Golang Version

To install the latest stable Golang version:

* Follow the same steps as above, but download the latest version available on the [Link](https://go.dev/dl/).  Always get the latest stable release.

### Legacy Applications (Older Golang Versions)

For legacy applications that require a specific older Golang version, follow these steps:

* **Download:** Download the appropriate archive from the Golang download archive: [Link](https://go.dev/dl/)
* **Installation:**
    * **Linux/macOS:**

        ```bash
        wget [https://go.dev/dl/go1.16.15.linux-amd64.tar.gz](https://go.dev/dl/go1.16.15.linux-amd64.tar.gz) 
        sudo tar -C /opt -xzf go1.16.15.linux-amd64.tar.gz  
        echo 'export PATH=$PATH:/opt/go1.16.15/bin' >> ~/.bashrc 
        source ~/.bashrc
        ```

### OT/Microservices

For setting up Golang for Observability Tools (OT) and microservice development, the standard installation is usually sufficient.  Here's a specific example (using Go 1.22.1, as you provided):

* **Linux:**

    ```bash
    wget [https://go.dev/dl/go1.22.1.linux-amd64.tar.gz](https://go.dev/dl/go1.22.1.linux-amd64.tar.gz)
    sudo tar -C /usr/local -xzf go1.22.1.linux-amd64.tar.gz
    echo 'export PATH=$PATH:/usr/local/go/bin' >> ~/.bashrc # Or ~/.zshrc
    source ~/.bashrc # Or source ~/.zshrc
    go mod tidy 
    ```
* **Explanation of `go mod tidy`**:  This command is crucial for microservices.  It cleans up your project's `go.mod` file, removing unused dependencies and ensuring that all necessary dependencies are correctly listed.  Run this in your project directory.

## 5. Post-Checks

After installation, verify that Golang is installed correctly:

* **Check Golang Version:** Open a terminal or command prompt and run:

    ```bash
    go version
    ```

    This should display the installed Golang version.
* **Check Go Environment:** Run:

    ```bash
    go env
    ```

    This will display the Golang environment settings, including `GOROOT` (the installation directory) and `GOPATH` (your workspace).
* **Run a Simple Program:**
    1.  Create a file named `hello.go` with the following content:

        ```go
        package main

        import "fmt"

        func main() {
            fmt.Println("Hello, Golang!")
        }
        ```
    2.  Open a terminal, navigate to the directory where you saved `hello.go`, and run:

        ```bash
        go run hello.go
        ```

        This should print "Hello, Golang!" to the console.

## 6. Best Practices

* **Use the Latest Stable Version:** For new projects, it's generally recommended to use the latest stable Golang version.
* **Manage Dependencies with Go Modules:** Use Go modules ( `go.mod`) to manage project dependencies. This is the standard and recommended approach.
* **Set `GOPATH` (If Necessary):** For older projects, you might need to set the `GOPATH` environment variable.  For modern Go with modules, this is often not required.
* **Update Go Regularly:** Keep your Go installation updated to benefit from the latest features, performance improvements, and security patches.
* **Organize Your Workspace:** If you are working with Go Modules, you don't need to create your projects inside the GOPATH.
* **Use `go mod tidy`:** In your projects, especially microservices, use `go mod tidy` to keep your dependencies clean and accurate.

## 7. Conclusion

This guide provides a comprehensive approach to installing Golang for various use cases. By following these steps, you can set up Golang for general development, legacy applications, and modern microservices.

## Contact Information
| Name         | Email address          |
|--------------|------------------------|
| Aditya Tripathi          | aditya.tripathi.snaatak@mygurukulam.co     |

## Reference Links
| Links        | Descriptions         |
|--------------|------------------------|
|    [Link](https://medium.com/@julienetienne/why-go-the-benefits-of-golang-6c39ea6cff7e) | Why Go - Advantages of go over other languages |
[Link](https://splitunknown.medium.com/installing-go-golang-on-linux-macos-and-windows-a-step-by-step-guide-7efe0643123b)     |  A detailed Golang Installation Guide for Linux/Mac    |
