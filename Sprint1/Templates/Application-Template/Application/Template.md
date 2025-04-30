# Application Template

**Revision History**

| Author | Created on | Version   | Last updated by | Last edited on |  Internal Reviewer | L0  | L1  | L2  |
| :----- | :--------- | :-------- | :-------------- | :------------- | -------------------|-----|-----|-----|
| ABC    | 26-04-25   | version 1 | ABC             | 26-04-25       |                    |     |     |     |
| ...    | ...        | ...       | ...             | ...            | ...                | ... | ... | ... |    

## What & Why/Purpose

Explain the What,why of this application here. Describe why there was a need for this application and detail the specific problems it aims to solve.

## Pre-requisites

Before diving into application deployment, ensure the following Hardware, Software, and Security requirements are met.

### System Requirements

| Hardware Specifications | Minimum Recommendation |
| :-------------------- | :--------------------- |
| Processor             | dual-core              |
| RAM                   | 4GB                    |
| Disk                  | 20GB                   |
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

#### Inbound Traffic

| Port | Description      |
| :--- | :--------------- |
| 9042 | Used by ScyllaDB |

#### Outbound Traffic

| Port | Description           |
| :--- | :-------------------- |
| 8080 | Used by Tomcat-server |

### Others

| Others                 | Description   |
| :--------------------- | :------------ |
| Additional requirement | Description   |

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

## Monitoring

Monitoring in DevOps refers to the practice of continuously observing and collecting data from various components of an application or system to ensure its health, performance, and availability. It involves tracking various metrics, events, and logs to identify issues, anomalies, and opportunities for improvement. Monitoring is a crucial aspect of the DevOps lifecycle as it helps teams proactively manage and maintain their applications, enabling faster response to problems and better overall system performance.

### Metrics

| Parameter          | Description                                                        | Priority | Threshold               |
| :----------------- | :----------------------------------------------------------------- | :------- | :---------------------- |
| Disk Utilization   | The percentage of disk space used by the application.              | High     | >90%                    |
| Availability       | The percentage of time the application is available.               | ...      |  ...                    |
| Memory Utilization | The percentage of memory used by the application.                  | Medium   | >80%                    |
| CPU Utilization    | ...                                                                | ...      | ...                     |
| Network Traffic    | ...                                                                | ...      | ...                     |
| Latency            | ...                                                                | High     | < 300ms                 |
| Errors             | ...                                                                | ...      | ...                     |
| Throughput         | ...                                                                | ...      | ...                     |
| Security           | ...                                                                | ...      | ...                     |

### Health check

| Name      | Type           | InitialDelaySeconds | PeriodSeconds | TimeoutSeconds | SuccessThreshold | FailureThreshold |
| :-------- | :------------- | :------------------ | :------------ | :------------- | :--------------- | :--------------- |
| App name  | ReadinessProbe | 10                  | 10            | 5              | 1                | 3                |
| App name  | LivenessProbe  | 10                  | 10            | -              | 5                | 1                |

**Explanation of parameters used in above table:**

| Parameter           | Description                                                                                                   |
| :------------------ | :------------------------------------------------------------------------------------------------------------ |
| ReadinessProbe      | This probe checks if the application is ready to receive traffic.                                             |
| LivenessProbe       | This probe checks if the application is still running and responding to requests.                             |
| InitialDelaySeconds | ...                                                                                                           |
| PeriodSeconds       | ...                                                                                                           |
| TimeoutSeconds      | ...                                                                                                           |
| SuccessThreshold    | ...                                                                                                           |
| FailureThreshold    | ...                                                                                                           |

### Logging

This section offers details on various types of logs related to the application, such as Event Logs, Server Logs, System Logs, Authorization and Access Logs, Change Logs, Availability Logs, Resource Logs, and Threat Logs.

| Log Type                           | Location / Example Path    | Description                                                                                                                        |
| :--------------------------------- | :------------------------- | :--------------------------------------------------------------------------------------------------------------------------------- |
| **Event Logs**                     | `location/to/event.log`    | An event log is a high-level log recording network traffic and usage data like incorrect password attempts, login attempts, app events. |
| **Authentication & Access Logs** | `location/to/access.log`   | Contains a list of persons or bots who have accessed specific programs or files.                                                     |
| **Server Logs**                    | ...   | ...                                                                |
| **System Logs**                    | ...         | ...                                                                           |
| **Change Logs**                    | ...  | ...                                   |
| **Availability Logs**              | ...   | ...                                                                   |
| **Resource Logs**                  | ... | ...                                                            |
| **Threat Logs**                    | ...   |  ...                                    |

## Disaster Recovery (DR)

In the event of a disaster affecting the application's functionality, it's important to have a robust disaster recovery plan in place. It typically ensures that critical systems and data can be restored after a disaster.

A disaster could be caused by a natural disaster, a cyberattack, or other event that takes down your IT infrastructure.

*(Describe the specific DR strategy for this application here, e.g., backup frequency, RTO/RPO targets, failover procedures).*

## High Availability (HA)

Ensuring high availability of the application is crucial to minimize downtime and provide seamless service to users. High Availability is a design approach that minimizes downtime for critical systems and services. This is achieved by deploying redundant components and systems, so that if one component fails, another can take over.

*(Describe the HA mechanisms in place here, e.g., load balancing, clustering, redundant servers/database).*

> **Note:** In other words, DR is focused on *recovering from* a disaster, while HA is focused on *preventing* downtime.

## Troubleshooting

Mention all the common issues that you encountered while performing setup of the Application. If you think there are some specific errors that are seen, you can add their screenshots or give a brief explanation of issue and offer solution to resolve it or guide the user to troubleshoot easily.

*   **Issue 1:** Brief description of the common issue.
    *   **Error Message (if applicable):** `Paste relevant error message here`
    *   **Screenshot (Optional):** `![Error Screenshot](path/to/screenshot.png)`
    *   **Solution:** Steps to resolve the issue or guide troubleshooting.
*   **Issue 2:** Another common issue description.
    *   **Solution:** Steps to resolve this issue.
*   *Add more common issues as needed*

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
