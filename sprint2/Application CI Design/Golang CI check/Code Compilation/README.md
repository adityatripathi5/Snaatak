

---

# **Documentation and POC of Code Compilation in Golang CI Checks**

| **Author**      | **Created on** | **Version** | **Last updated by** | **Internal Reviewer** | **L0 Reviewer** | **L1 Reviewer** | **L2 Reviewer** |
| --------------- | -------------- | ----------- | ------------------- | --------------------- | --------------- | --------------- | --------------- |
| Aditya Tripathi | 18-05-25       | 1           | Aditya Tripathi     | Priyansh              | Priyanka        | Rishabh         | Piyush          |

---

# Table of Contents

1. [**Introduction**](#introduction)
2. [**Why Compile Golang Code?**](#why-compile-golang-code)
3. [**Golang Compilation Process**](#golang-compilation-process)
4. [**Tools Used in Golang Compilation**](#tools-used-in-golang-compilation)
5. [**Comparison with Other Backends**](#comparison-with-other-backends)
6. [**Workflow Diagram**](#workflow-diagram)
7. [**Advantages**](#advantages)
8. [**POC - Golang Code Compilation via CI**](#poc---golang-code-compilation-via-ci)
9. [**Best Practices**](#best-practices)
10. [**Recommendations & Conclusion**](#recommendations--conclusion)
11. [**Contact Information**](#contact-information)
12. [**References**](#references)

---

## Introduction

This document outlines the Continuous Integration (CI) design for Golang code compilation in the **Backend** module of the [OT-MICROSERVICES](https://github.com/OT-MICROSERVICES/) ecosystem. The goal is to ensure that each Go microservice is compiled, tested, and validated as part of the CI process, leading to reliable and production-ready binaries.

Go code is statically compiled into a single executable binary, making it highly efficient for CI pipelines and cloud-native deployment.

---

## Why Compile Golang Code?

| **Reason**                | **Description**                                              |
| ------------------------- | ------------------------------------------------------------ |
| **Binary Generation**     | Compiles directly into native binary, no interpreter needed. |
| **Error Detection**       | Syntax and type errors caught early in build stage.          |
| **Dependency Management** | Ensures all modules are downloaded and validated.            |

---

## Golang Compilation Process

| **Step**                | **Description**                                        |
| ----------------------- | ------------------------------------------------------ |
| `go mod tidy`           | Cleans and validates `go.mod` and dependencies.        |
| `go build`              | Compiles `.go` source files into an executable binary. |
| `go test`               | Runs all unit tests to ensure code correctness.        |
| `go install` (optional) | Installs the binary in the system path.                |

---

## Tools Used in Golang Compilation

| **Tool**           | **Purpose**                          | **Why Used**                                      |
| ------------------ | ------------------------------------ | ------------------------------------------------- |
| **Go**             | Core compiler and toolchain          | Official build system for all Golang applications |
| **Makefile**       | (Optional) Structured build commands | Simplifies repetitive build/test tasks            |
| **go mod**         | Dependency management                | Manages module versions and reproducibility       |
| **GitHub Actions** | CI Automation                        | Automates Go builds and tests per push/PR         |

---

## Comparison with Other Backends

| **Feature**        | **Golang**    | **Java (Spring Boot)** | **Node.js** |
| ------------------ | ------------- | ---------------------- | ----------- |
| Compilation Output | Native Binary | JAR/WAR                | JS Code     |
| CI Speed           | Very Fast     | Medium                 | Fast        |
| Runtime Overhead   | Low           | High                   | Medium      |
| Docker Friendly    | Yes           | Yes                    | Yes         |

---

## Workflow Diagram

![image](https://github.com/user-attachments/assets/b5c04e14-45e1-4a82-b2b4-15c1d8dc05a6)

---

## Advantages

| **Advantage**                 | **Benefit**                                                         |
| ----------------------------- | ------------------------------------------------------------------- |
| **Single Binary Output**      | Easy deployment and portability                                     |
| **CI Integration Simplicity** | Few moving parts, no need for separate compilers or runtimes        |
| **Faster Feedback Loop**      | Compile and test cycles are fast, suitable for microservices        |
| **Minimal Dependencies**      | Reduced external package reliance enhances security and reliability |

---

# POC - Golang Code Compilation via CI

Please Refer Here for Code Compilation [POC](https://github.com/adityatripathi5/Snaatak/blob/main/sprint2/Application%20CI%20Design/Go%20CI%20Checks/Code%20Compilation/POC.md)

---

## Best Practices

* Always run `go mod tidy` before commit to clean unused dependencies.
* Use `go build -v ./...` to compile all packages with verbose output.
* Include unit tests in your pipeline using `go test ./... -v`.
* Add a `Makefile` to standardize build/test/lint commands.
* Use `CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -o app` for cross-compilation in CI.
* Lint the code using tools like `golangci-lint`.

---

## Recommendations & Conclusion

Compiling Golang code in CI ensures that only valid, working, and tested code gets promoted across environments. The compiled binaries are easy to deploy, version, and roll back. By integrating build, test, and linting in the CI workflow, we improve confidence, reduce bugs, and maintain consistent quality across services.

---

## Contact Information

| **Name**        | **Email**                                                                                 |
| --------------- | ----------------------------------------------------------------------------------------- |
| Aditya Tripathi | [aditya.tripathi.snaatak@mygrurukulam.co](mailto:aditya.tripathi.snaatak@mygrurukulam.co) |

---

## References

| **Link**                                             | **Description**        |
| ---------------------------------------------------- | ---------------------- |
| [golang.org doc](https://golang.org/doc/)            | Official Go Docs       |
| [go.dev modules](https://go.dev/doc/modules)         | Go Modules Guide       |
| [github actions](https://docs.github.com/en/actions) | GitHub Actions Docs    |
| [golangci-lint](https://golangci-lint.run/)          | Linting Tool for Go    |
| [effective go](https://go.dev/doc/effective_go)      | Style & Best Practices |

---


