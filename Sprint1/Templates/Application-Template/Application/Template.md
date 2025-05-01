# Application Template

| Author | Created on | Version   | Last updated by | Last edited on |  Internal Reviewer | L0  | L1  | L2  |
| :----- | :--------- | :-------- | :-------------- | :------------- | -------------------|-----|-----|-----|
| Aditya    | 26-04-25   | version 1 | Aditya       | 26-04-25       | Priyanshu          | Priyanka     | Rishabh    | Piyush    |
| ...    | ...        | ...       | ...             | ...            | ...                | ... | ... | ... |   

## Table of Contents

- [What & Why / Purpose](#what--whypurpose)
- [Pre-requisites](#pre-requisites)
- [Architecture](#architecture)
- [Step-by-step installation of `<Your Application Name>`](#step-by-step-installation-of-your-application-name)
  - [Step 1: Installation of Software Dependencies](#step-1-installation-of-software-dependencies)
  - [Step 2: Build/Artifact Generation](#step-2-buildartifact-generation)
  - [Step 3: Application Deployment](#step-3-application-deployment)
- [Troubleshooting](#troubleshooting)
- [FAQs](#faqs)
- [Contact Information](#contact-information)
- [References](#references) 

## What & Why/Purpose

Explain the What,why of this application here. Describe why there was a need for this application and detail the specific problems it aims to solve.

## Pre-requisites

Before diving into application deployment, ensure the following Hardware, Software, and Security requirements are met.

### System Requirements

| Hardware Specifications | Minimum Recommendation |
| :-------------------- | :--------------------- |
| Processor             | dual-core              |
| RAM                   | 4GB                    |
| Disk                  | 30GB                   |
| OS                    | Ubuntu (22.04)         |

### Dependencies

#### Build time Dependency

| Name          | Version   | Description   |
| :------------ | :-------- | :------------ |
| `<application>` | `<version>` | `<Description>` |
| `<application>` | `<version>` | `<Description>` |

#### Run time Dependency

| Name          | Version   | Description   |
| :------------ | :-------- | :------------ |
| `<application>` | `<version>` | `<Description>` |
| `<application>` | `<version>` | `<Description>` |

### Important Ports

| Port | Description      |
| :--- | :--------------- |
| 9042 | Used by ScyllaDB |
| 8080 | Used by Tomcat-server |

## Architecture

![image](https://github.com/user-attachments/assets/40b6cf42-395b-4e7c-bfa7-0a53d0d608fe)

**Dataflow Diagram**

Explain the flow of the data in the architecture diagram above. Describe how data travels and is processed within this application.

## Step-by-step installation of `<Your Application Name>`

### Step 1: Installation of software Dependencies

#### Build Dependency

Add the command used to install the build dependencies below:
```bash
# Example: apt-get update && apt-get install -y <build-dependency-1> <build-dependency-2>
[command]
```
#### Run time Dependency

Add the command used to install the run time dependencies below:
```bash
# Example: pip install -r requirements.txt
[command]
```

#### Other Dependency

Add commands used to install any other dependencies (e.g., for 3rd party integrations) below:
```bash
# Example: install_integration_tool.sh
[command]
```
### Step 2: Build/Artifact Generation

Clone the git repository:
```bash
# Example: git clone <your-repo-url>
# Example: cd <your-repo-directory>
[commands]
```

Run the following command inside the directory to build your software artifact:
```bash
# Example: mvn clean package
# Example: make build
[commands]
```

### Step 3: Application Deployment

Perform the following steps to deploy the software artifact:
```bash
# Example: cp target/app.jar /opt/app/
# Example: systemctl start your-app-service
# Example: kubectl apply -f deployment.yaml
[command]
```

Ensure the application deployed is in working state:
```bash
# Example: curl http://localhost:8080/health
# Example: systemctl status your-app-service
# Example: kubectl get pods -l app=<your-app-label>
[command]
```

## Troubleshooting

Below are common issues you might encounter while setting up the application, along with possible solutions or guidance.

| **Issue**                          | **Error Message (if any)**          | **Screenshot (Optional)**                         | **Solution / Troubleshooting Steps**                                  |
|------------------------------------|-------------------------------------|---------------------------------------------------|----------------------------------------------------------------------|
| Issue 1: Brief description of the common issue | `Paste relevant error message here` | ![Error Screenshot](path/to/screenshot.png)       | Steps to resolve the issue or helpful tips for debugging.           |
| Issue 2: Another common issue description     | –                                   | –                                                 |  –      |
| *Add more issues as needed*       | –                                   | –                                                 | –                                                                    |

## FAQs

*   **Is this application free?**
    Yes, it is an open-source application. *(Adjust if not applicable)*

*   **Can I deploy this application on all Cloud platforms?**
    Yes, it can be deployed on any cloud platform supporting its prerequisites (like Ubuntu 22.04 and required dependencies). *(Adjust based on actual compatibility)*

*   **Do you offer an enterprise version of this application?**
    No, this is an open-source contribution. No enterprise version is available. *(Adjust if applicable)*

## Contact Information

| Name | Email address       |
| :--- | :------------------ |
| abc  | abc@mygurukulam.co  |
| xyz  | xyz@mygurukulam.co  |

## References

| Links                                                                       | Descriptions                                                      |
| :-------------------------------------------------------------------------- | :---------------------------------------------------------------- |
| [CICD Docs - Installation on Ubuntu](https://www.jenkins.io/doc/book/installing/linux/#debianubuntu) | ...                         |
| [User Guide](https://amplifi.com/user-guide/FAQs.html)       | ...                                          |
| [Intro and Overview](https://thecontentauthority.com/blog/introduction-vs-overview) | ...                    |
