

---

# POC - Java Unit Testing using JUnit

---

## Table of Contents

1. [Objective](#objective)
2. [Pre-requisites](#pre-requisites)
3. [Step-by-Step Guide](#step-by-step-guide)
4. [Contact Information](#contact-information)
5. [References](#references)

---

## Objective: Execute Unit Tests for a Java Project Using JUnit

The objective of this POC is to demonstrate how to execute unit tests for a Java project using JUnit with Maven, and generate a test report for verification.

---

## Pre-requisites:

| **Specification** | **Details**              |
| ----------------- | ------------------------ |
| OS                | Ubuntu 22.04* |
| Java Version      | >= 17                    |
| Maven             | Installed (`mvn` CLI)    |
| Testing Framework | JUnit                    |

---

## Step-by-Step Guide:

**Step 1**: Navigate to the Java app directory

```bash
cd salary-api
```

![Step 1 Screenshot](https://github.com/user-attachments/assets/9c573b49-aa23-4b8f-b6bb-796a6564d1be)

---

**Step 2**: Run unit tests using Maven

```bash
mvn test
```

![Step 2 Screenshot](https://github.com/user-attachments/assets/fe1ebf4c-509c-4edd-bf31-702398c2e206)

---

**Step 3**: View test results

JUnit test results will be displayed in the terminal and stored in the `target/surefire-reports` directory.

![Step 3 Screenshot](https://github.com/user-attachments/assets/a11d9a01-6369-436c-abfe-28080f641229)

---

**Step 4**: Access reports or artifacts

| **Artifact**                                                                                                                                                       | **Description**   |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------- |
| [Test Report](https://github.com/avengers-p11/Documentation/blob/main/Application%20CI%20Design/Java%20CI%20Checks/Unit%20Testing%20/report)                       | JUnit Test Report |
| [Jar File](https://github.com/avengers-p11/Documentation/blob/main/Application%20CI%20Design/Java%20CI%20Checks/Bugs%20Analysis/salary-0.1.0-RELEASE.jar.original) | Build Artifact    |

---

## Contact Information

| **Name**        | **Email**                                                                                 |
| --------------- | ----------------------------------------------------------------------------------------- |
| Aditya Tripathi | [aditya.tripathi.snaatak@mygrurukulam.co](mailto:aditya.tripathi.snaatak@mygrurukulam.co) |

---

## References

| **Link**                                                                                                                                                              | **Description**       |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------- |
| [JUnit 5 Docs](https://junit.org/junit5/docs/current/user-guide/)                                                                                                     | Official JUnit Guide  |
| [Apache Maven](https://maven.apache.org/guides/)                                                                                                                      | Maven Build Tool Docs |
| [Surefire Plugin](https://maven.apache.org/surefire/maven-surefire-plugin/)                                                                                           | Test Execution Plugin |
| [CI Tool Reference](https://github.com/avengers-p11/Documentation/tree/main/Application%20CI%20Design/Java%20CI%20Checks/Static%20Code%20Analysis#tool-poc-sonarqube) | Related CI Tools      |

---


