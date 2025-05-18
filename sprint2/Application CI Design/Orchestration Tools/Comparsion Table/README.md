# CI/CD Tooling: Jenkins vs GitLab vs BuildPiper

## Author Details

| **Author**      | **Created on** | **Version** | **Last updated by** | **Internal Reviewer** | **L0 Reviewer** | **L1 Reviewer** | **L2 Reviewer** |
| --------------- | -------------- | ----------- | ------------------- | --------------------- | --------------- | --------------- | --------------- |
| Aditya Tripathi | 15-05-25       | 1           | Aditya Tripathi     | Priyansh              | Priyanka        | Rishabh         | Piyush          |

---

## Table of Contents

1. [Introduction](#introduction)
2. [What is Jenkins, GitLab, and BuildPiper?](#what-is-jenkins-gitlab-and-buildpiper)
3. [Why Choose These Tools?](#why-choose-these-tools)
4. [Workflow Diagrams](#workflow-diagrams)
5. [Comparison Table](#comparison-table)
6. [Best Practices](#best-practices)
7. [Recommendation & Conclusion](#recommendation--conclusion)
8. [Contact Information](#contact-information)
9. [References & Documentation Links](#references--documentation-links)

---

## Introduction

Choosing the right CI/CD tool is critical to automating and accelerating software delivery. Jenkins, GitLab, and BuildPiper are leading tools offering diverse capabilities across the DevOps lifecycle. This document explores each tool in detail to help engineering teams select the most suitable solution.

---

## What is Jenkins, GitLab, and BuildPiper?

### Jenkins

Jenkins is a widely adopted open-source automation server, facilitating CI/CD through an extensive plugin ecosystem. It supports pipeline-as-code, distributed builds, and broad integrations.To Read more on this follow this link [Jenkins](https://github.com/Cloud-NInja-snaatak/Documentation/tree/SHREY-SCRUM-170/application_ci/tools/orchestration/jenkins)

### GitLab

GitLab is a complete DevOps platform that unifies source code management (SCM), CI/CD, security scans, and collaboration under one interface. It simplifies workflows by centralizing all stages of development.To Read more on this follow this link [Gitlab](https://github.com/Cloud-NInja-snaatak/Documentation/tree/Shubham_SCRUM-171/application_ci/tools/orchestration/gitlab)

### BuildPiper

BuildPiper is a CI orchestration and microservices delivery platform designed to enable secure, scalable DevSecOps pipelines. It provides tight integrations with vulnerability scanning, quality gates, and artifact lifecycle management.To Read more on this follow this link [BuildPiper](https://github.com/Cloud-NInja-snaatak/Documentation/tree/Tharik_SCRUM-172/application_ci/tools/orchestration/buildpiper)

---

## Why Choose These Tools?

| Tool       | Why Use It?                                                           |
| ---------- | --------------------------------------------------------------------- |
| Jenkins    | Open-source, highly customizable, massive plugin ecosystem.           |
| GitLab     | All-in-one DevOps tool, integrated security, collaboration, scalable. |
| BuildPiper | Built for microservices, DevSecOps focused, powerful dashboarding.    |

---

## Workflow Diagrams

### Jenkins Workflow

[Jenkins Workflow](https://github.com/Cloud-NInja-snaatak/Documentation/blob/SHREY-SCRUM-170/application_ci/tools/orchestration/jenkins/README.md#jenkins-workflow-diagram)

### GitLab Workflow

[GitLab Workflow](https://github.com/Cloud-NInja-snaatak/Documentation/blob/Shubham_SCRUM-171/application_ci/tools/orchestration/gitlab/README.md#Workflow-Diagram)

### BuildPiper Workflow

[BuildPiper Workflow](https://github.com/Cloud-NInja-snaatak/Documentation/blob/Tharik_SCRUM-172/application_ci/tools/orchestration/buildpiper/README.md#workflow-diagram)

---

## Comparison Table

| Feature              | Jenkins                   | GitLab                        | BuildPiper                   |
| -------------------- | ------------------------- | ----------------------------- | ---------------------------- |
| Type                 | Open Source               | Open Core (Free + Enterprise) | Proprietary                  |
| Plugin Ecosystem     | 1800+ Plugins             | Native Features               | Pre-integrated Modules       |
| Pipeline as Code     | Jenkinsfile               | `.gitlab-ci.yml`              | Customizable GUI/YAML        |
| SCM Integration      | Git, SVN, Bitbucket, etc. | GitLab Native                 | Git, GitHub                  |
| Security Integration | Plugins (Snyk, SonarQube) | Built-in SAST/DAST            | Built-in                     |
| Dashboard/UX         | Moderate                  | Modern, Unified               | Intuitive, Visual Dashboards |
| Kubernetes Support   | Via Plugins               | Native                        | Native                       |
| Learning Curve       | Moderate to High          | Moderate                      | Low to Moderate              |
| Use Case             | General Purpose CI/CD     | Unified DevOps Lifecycle      | Microservices DevSecOps      |

---

## Best Practices

| Tool       | Best Practices                                                            |
| ---------- | ------------------------------------------------------------------------- |
| Jenkins    | Use declarative pipelines, secure credentials, monitor agent health.      |
| GitLab     | Use groups/subgroups, security scans, caching, reusable `.gitlab-ci.yml`. |
| BuildPiper | Use version-controlled configs, integrate scans, and leverage dashboards. |

---

## Recommendation & Conclusion

All three tools provide robust CI/CD capabilities. However, **Jenkins** stands out for the following reasons:

* Open-source flexibility.
* Largest plugin marketplace.
* Deep customization for any DevOps stack.
* Rich support for community-driven features.

While GitLab and BuildPiper offer end-to-end lifecycle support, **Jenkins** remains the best fit for teams who want modular control and open innovation.

**Chosen Tool: Jenkins**

---

## Contact Information

| Name           | Email Address                                                                         |
| -------------- | ------------------------------------------------------------------------------------- |
| Aditya Tripathi | aditya.tripathi.snaatak@mygurukulam.co |

---

## References & Documentation Links

| Tool       | Documentation Link                                                                                 |
| ---------- | -------------------------------------------------------------------------------------------------- |
| Jenkins    | [Jenkins Docs](https://github.com/Cloud-NInja-snaatak/Documentation/tree/SHREY-SCRUM-170/application_ci/tools/orchestration/jenkins)                                                         |
| GitLab     | [GitLab Docs](https://github.com/Cloud-NInja-snaatak/Documentation/tree/Shubham_SCRUM-171/application_ci/tools/orchestration/gitlab)                                                            |
| BuildPiper | [BuildPiper Docs](https://github.com/Cloud-NInja-snaatak/Documentation/tree/Tharik_SCRUM-172/application_ci/tools/orchestration/buildpiper) |

> For in-depth reading, refer to the individual documents:
>
> * [Jenkins Documentation](https://www.jenkins.io/doc)
> * [GitLab Documentation](https://docs.gitlab.com/)
> * [BuildPiper Documentation](https://github.com/user-attachments/assets/9ed09a96-a6f0-4b75-9ab9-25ac6b9d9e4b)
